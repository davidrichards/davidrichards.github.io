---
layout: post
title:  Test Power to the People
summary: Getting comfortable with testing our code shouldn't be as hard as it is.
date:   2016-3-30-18:15:00
categories: development
---

Once upon a time, a long time ago, I was at a Ruby meetup with Andrew Shafer ([@litleidea](https://twitter.com/littleidea)) talking about testing.  He asked us all if we test our code.  A few hands went up.  "What, you never verify that your code runs before you ship it?"  All our hands went up.  His point was that writing an automated test is just an extension of the normal things we all do anyway.

Talking with BJ Nielsen ([@localshred](https://twitter.com/localshred)) tonight about testing, he reminded me of the same thing.  We all test all the time, just we feel like it's some kind of elite thing that we aspire to.

Back in the day of Engels and Marx, they talked a lot about the Bourgeoisie and Proletariat.  Marx invented this concept to give a name to a feeling.  The Bourgeoisie are the people that make the rules, own the land, disapprove of working-class ways.  The Proletariat are the rest of us.  Talking about the difference was enough to cause a revolution.  People wanted more power for people like them.  It's probably funny to hear a well-paid software developer talk about myself as the Proletariat, but I still like to get in the trenches and deliver pull requests on projects.

<img src="http://i.imgur.com/HC5Ydn4.jpg" alt="Power to the People" height="300">

All of us, with zero or more days on the job figure out how to ship a job well done.  Some of us write automated tests and some of us like writing those tests.  But all of us test.

I've done a lot of work in the Ruby community.  I was at an Agile conference a lot of years ago with all sorts of developers in the room.  We were practicing some test-driven development and [Brian Marick](http://www.exampler.com/testing-com/) wanted to make sure we all had a way to practice some examples.  He asked each table what language we would work in and which testing library.  When he came to the Rubyists in the room, he said something like, "Rubyists have more testing frameworks per capita than...."  I don't remember the punchline, but the whole room laughed.  We like our tests, but we can be pretty dogmatic about it too.

Over the years, the community's had a few online fights about how to test.  I don't remember all the fights, but here are a few:

* BDD vs TDD
* Mochs vs Fixtures
* Integration tests (or no)
* Framework A vs Framework B

It's kind of fun to hear someone passionately teaching how things work, and I'm not saying that the people that test differently than me are wrong.

**There is a feeling, however, that someone else owns the good ideas when it comes to testing.**  The Bourgeoisie are the testing experts and the rest of us just Proletariat commoners slinging code for a living.

**I think it's important to demystify testing and enjoy work well delivered again.**

At the [MWRC](http://mtnwestrubyconf.org/) last week, Ryan Davis ([@the_zenspider](https://twitter.com/the_zenspider)) built a [test framework from scratch.](http://www.zenspider.com/presentations/2016-mwrc.html)  Seeing the whole thing come together took the final scales from my eyes, and I've been testing with more and more confidence since.

The heart of any automated test is just an assertion.  We may have fancy ways to code it up, but something must be true to know that my code delivers on its promise.  If we're confident with that, that's a great thing.

I tend to do one more thing often, I mock out anything that I'm not testing directly (usually with [mocha](http://gofreerange.com/mocha/docs/)).  You might not like doing it that way, and that's OK too.  Maybe I should have finished with, it's all just an assertion, and end with that.  I probably should explain a little what everyone's been fighting about so that this thing feels more normal to you.

The 'mochist' approach to testing says that we prefer writing tests on code we're working on as opposed to testing anything else.  That seems like a strange thing to defend, but we all get comfortable in our own ways and some people feel more comfortable seeing the database respond.  After all, that's the thing that they're delivering.  I say if that makes it easier for you to ship code, then do it that way.

I was challenged on that not too long ago.  The person challenging me had more authority than me in the organization that was signing my checks.  No big deal.  I was non-plussed by the question. I think my calmness made my point better than anything else could.  I said something like, "I can write those kinds of tests too, whatever we need to do to be confident."  End of discussion.  We ship code working systems and don't get too worked up about things.

However, I still write most tests that don't use any other piece of code, database or API.  A test like this looks sort of like:

    def test_products
      products = mock
      products.expects(:is_active).returns(true)
      ::Product.expects(:is_accruing).returns(products)
      assert(@subject.products)
    end

What this says is when I call products on the piece of code I'm calling, it will use Product and ask it for 'is_accruing'.  That returns a mock object that is expecting 'is_active' and returns true.  The chain inside the code looks something like:

    Product.is_accruing.is_active

Some people argue that this is kind of hard to understand.  They may be right.  The point is I'm testing the plumbing of the method.  If that changes or needs to change, my test will fail, and I'll be working on purpose.  I'm testing that one piece of code relies on another piece of code consistently.  In recent months, we've asserted over 2,500 things on a project this way and missed two things.  That is, two things made it to production that didn't do what we thought we were supposed to be doing.  This approach may not be the end all, but I can live with those odds.

The whole point is that we should bring testing back to the people that write code.  We should be comfortable.  **Almost my whole testing philosophy can be demonstrated with one test.  There's no other secret sauce that I'm dying to show you.**

A nice side effect of writing tests (especially these kinds of tests) is that my methods get pretty short.  Short means it's easier to read and easier to fix later.  I had one of my two problems that made it to production happen today.  It was kind of messy, but it only took a few minutes to find where the code was breaking.  I had a one-line method that needed to be fixed.  We fixed it, wrote a test that made sure the problem never came back again and got production running again.

I worked with someone that's an incredibly gifted developer.  He has a mind for code and optimization better than the next 9 developers.  Somewhere along the line, something made testing seem overly complicated for him.  We paired for a few hours and he was testing like a pro.  He and I and one other person are head-to-head this month on the number of commits we've moved into production.  Together we have about 250 commits for the month.  We like to commit code every time we deliver one thing well.  That means our product does about 250 new things well this month.  That's a pretty good velocity for any three people.  It all works well because the style of delivering working systems that I'm talking about actually works for real problems.

Anyway, I probably shouldn't try and convince anyone that they should code like me.  Just do what you do so that you can be a confident coder.  Make sure some things happen because you meant them to happen.  Use mocks if they help you get things into production faster.  Enjoy being a creative human.