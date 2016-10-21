---
layout: post
title:  Ecto.Multi and Sane Code
summary: Keeping code sane and reasonable for non-trivial business logic using Elixir and Phoenix.
date:   2016-10-20-17:00:00
categories: development data
---
I'm using Phoenix and Elixir at work, loving my experience. If I can expose a few of my own mistakes along the way, it might be useful.

As with all frameworks, newbs tend to bloat things for a while. I did too. Writing our application, we started with a monolithic application: all the functionality in one big project.  I also had a strong Rails influence in my thinking.  That meant I tried to put a little too much in controllers and models (even though I tend to structure my Ruby code much simpler than that).

So, how did this break things?

I was missing things off the [happy path][happy].  I didn't have transactions wrapping co-dependent logic. I could create records in the database, have things fail, and have to deal with this new nonsense state.  Things were just hardly working, and I knew I needed to handle it better.

## Enter Ecto.Multi

Let me start with an [example from Wojtek Mach][multi_example]:

    defmodule Bank.CustomerRegistration do
      use Bank.Model

      def create(username, email, password) do
        Ecto.Multi.new
        |> Ecto.Multi.insert(:customer, Customer.build(%{username: username, email: email}))
        |> Ecto.Multi.run(:account, fn _ ->
          Auth.register(%{email: email, password: password})
        end)
        |> Ecto.Multi.run(:update, fn %{customer: customer, account: account} ->
          Ecto.Changeset.change(customer, auth_account_id: account.id)
          |> Repo.update
        end)
        |> Repo.transaction()
      end
    end

Before we break this down, let me say this. Ecto.Multi is an all-together-now proposal. In this case, the customer is written, authenticated remotely, and updated, all under a transaction.  If I weren't using this for transactional safety, I could still compose an object over many operations and have that work for me.

But that's not very useful if we don't know what's going on.  Let's break this down. We have a module. Some people (maybe just people I know), call this kind of module a context module. It's like a [Service Object][service_object] from the OO space and Uncle Bob Martin's thinking. It produces a context to get something handled simply and directly. This, rather than in models or controllers or some other over-used space in your work.

Inside the create function, we're creating a new Multi struct with `Ecto.Multi.new`.  The important thing here is we're creating a data type that stores a local log of every step along the way.  This is the all-together-now approach to the code.

![beatles][beatles]

Next, we write to the database.  We give it a label, `:customer` in this case.  [insert][insert] takes a changeset or struct.  In this example, there's a really good practice for setting that up, `Customer.build`:

    def build(%{username: username} = params) do
      changeset(%Customer{}, params)
      |> put_assoc(:wallet, Ledger.Account.build_wallet("Wallet: #{username}"))
    end

This is a nice way to setup a changeset, adding some defaults more simply.  A basic Customer changeset with whatever parameters I know about, and setting up the wallet association.  **A lot of power, and little fuss.  Win.**

Now we're on to some custom code with [run][run] (twice, actually).  We can write any function we'd like. We still label every step, we always label every step.  The key is to use the right return value: `{:ok, value}` or `{:error, value}`.  The more I build with Elixir, the more I love this interface. It makes it easier to manage error handling code with tuples like this.

Finally, we call [transaction][transaction].  This also uses the same tuple return code and the same labeling convention (surprise!).  This won't work for things like MongoDB, but does work for PostgreSQL or similar databases.

So, we have a few functions called in a chain. What's the big deal?  At least two things: it's all or nothing, and it gives us a log of every step if we need it later.  Knowing we've got all the steps, even the remote API calls, handled, reduces the complexity of our business logic.  And, if it doesn't go well, we can respond to that by knowing exactly what went wrong and what state we were in.

What does it look like when things go wrong?  We get a tuple that looks something like:

    {:error, failed_operation, failed_value, changes_so_far}

That is:

* :error, the easiest way to pattern match
* failed_operation: whatever label we gave the step that failed
* failed_value: the failing response
* changes_so_far: all the prior steps, stored and available for reasoning

The more-complete instructions for Ecto.Multi are where [you'd expect them][multi_api].  You'll find instructions there for things like update and delete.  At work, we use Multi for things like creating a user.  In much the same way as the example above, we need an all-or-nothing approach to critical things like this.

## But Wait, There's More

So, Multi takes us a long way.  It can be overkill though if we just want to handle errors.  For that, I like to use [with][with].  Here is the example from the user docs:

    opts = %{width: 10}
    with {:ok, width} <- Map.fetch(opts, :width),
         {:ok, height} <- Map.fetch(opts, :height) do
      {:ok, width * height}
    else
      :error ->
        {:error, :wrong_data}
    end

What's going on here?

We start `with` using the `with` keyword and the first assignment **on the first line**.  I wanted to make that pretty and indent it underneath `with`, but that's not OK.

We are pattern matching {:ok, width} with Map.fetch(opts, :width). This uses a backwards arrow operator which is a little strange. There's probably a good explanation about why not pattern match on an `=`.  Whatever the reason, it helps me think about each step of my work because it's different.

Put another way, that first line fetches :width from the opts map.  It expects a tuple starting with :ok, and whatever width is in the map (10 in our case).  If that doesn't match, the else code is called. More on that in a moment.

Notice a comma at the end of the first pattern match/operation. We then go to the next operation, and keep going as long as we'd like, pattern matching and collecting values as we go.  These values are available to me in subsequent calls or my do block.  Did you notice that block?  In this case, it returns `{:ok, width * height}`.  If all went well, we get the area of a square.  If not, the else code is written.

Now, the else statement works like a case. Something didn't work, let's pattern match what that was. In this case, we expect :error only, so we use `:error -> {:error, :wrong_data}`.  If things could go wrong inconsistently, you could write many pattern matching entries here. The syntax for the else is like a case, meaning **no commas and forward arrows**.

`with` recapped:

* start the with operations on the same line as `with`
* use backward arrows (`<-`) for the operations
* use commas to separate operations
* pattern match the happy path from each operation
* create a `do` block to handle what happens when everything goes write
* create an `else` block to handle what happens when something goes wrong
* leave the `else` block out if you can handle the error response directly
* use `case` syntax for the else block (forward arrows (`->`) and no commas)

This is a tricky little [special form][special_form], but I tend to use it quite a bit.  Why? I can have the all-or-nothing benefits I got from Ecto.Multi, but for any code. Also, I have more-relaxed rules about return values.  So, if I don't take the time to wrap everything I touch to use the `{:ok, value}` or `{:error, value}` response, I can still manage the unhappy path.

![unhappy path][unhappy_path]

## Why? Why All This?

Let me tell you something important. There are always better ways to do things.  With `Multi.Ecto` and `with`, I can handle when things go wrong before I know what my final form is going to be. Not knowing all the things is the way we all develop, even those of us that have been around for a while. I don't always stop and wrap all the functions I use with a tuple response. I could work out some of the complicated transactional code with better-designed changesets, schemas, and helper functions. I could break down my applications into [umbrella applications][umbrella].  I do some of these, but these tools make my code sane in the meantime.

The other nice thing is using these tools encourage me to embrace good practices:

* have clear and consistent interfaces with other functions
* embrace helper functions around my changesets like build
* always handle the unhappy path (first, usually)

And, in case I wasn't being clear, all of this is important because I got it wrong quite a few times before I started to appreciate it.

[beatles]: http://i.imgur.com/VzTY0qf.jpg
[happy]: https://en.wikipedia.org/wiki/Happy_path
[multi_example]: https://github.com/wojtekmach/acme_bank/blob/master/apps/bank/lib/bank/customer_registration.ex
[service_object]: https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html
[multi_api]: https://hexdocs.pm/ecto/Ecto.Multi.html#insert_all/5
[insert]: https://hexdocs.pm/ecto/Ecto.Multi.html#insert/4
[run]: https://hexdocs.pm/ecto/Ecto.Multi.html#run/3
[transaction]: https://hexdocs.pm/ecto/Ecto.Repo.html#c:transaction/2
[with]: http://elixir-lang.org/docs/stable/elixir/Kernel.SpecialForms.html#with/1
[special_form]: http://elixir-lang.org/docs/stable/elixir/Kernel.SpecialForms.html
[unhappy_path]: http://i.imgur.com/1n3o816.jpg
[umbrella]: http://elixir-lang.org/getting-started/mix-otp/dependencies-and-umbrella-apps.html