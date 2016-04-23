---
layout: post
title:  A Problem with JavaScript
summary: This is not a rant.  This is a moment to ask what can be done to be more productive with JavaScript.
date:   2016-4-21-22:49:00
categories: development
---

Let me be clear.  I am not about to rant about JavaScript, the community, developers, or anything else.  I'm just going to ask a few questions to figure out how I can be more productive with it.

What is wrong with JavaScript?

One thing I mean by that is, "why isn't it boring yet?"  It's been around in some form for over 20 years.  That usually means a technology kind of slows down and loses its exuberant changes.

Right now, JavaScript is the [third-most in demand language](http://www.codingdojo.com/blog/9-most-in-demand-programming-languages-of-2016/).  It's in demand.  It's running on billions of devices.  It's old.  It's not tired.  And it's not getting replaced, though many have tried.  Think Dart, VBScript, JScript (IE 3), Java Applets and many more.  Why isn't it tired?  Why can't it be replaced?

**Maybe because a lot of people are winning with JavaScript.**

However, "winning" means a lot of people are trying to "fix" JavaScript.  CoffeeScript, TypeScript, ClojureScript and Roy are all adding to the mix of ways to write JavaScript.  In case you think I'm hyperbolic when I say everyone is trying to fix JavaScript, there are 327 languages on [this list](https://github.com/jashkenas/coffeescript/wiki/list-of-languages-that-compile-to-js) that compile to JavaScript in some way.

But it isn't really a targeted standard.  I mean, ECMAScript **IS** a standard, but the standard is also growing up quite rapidly.  ES6 wasn't even finished before they started planning ES7 and beyond [3 years ago](https://esdiscuss.org/topic/es6-es7-es8-and-beyond-a-proposed-roadmap).  The idea is to quickly ship updated standards and then keep moving on other features that makes it easier to use JavaScript everywhere.

And this might be the reason why we're mushrooming in JavaScript technologies: **we're all trying to make the language easier for competing definitions of easy.**

For example, a lot of people get a lot of mileage out of strict typing.  They know that they can rely on other tool systems to optimize a statically-typed code base.  They also rely on type constraints to keep their code more consistent with their intentions.  On the other hand, many people have embraced duck typing and dynamic programming to extend systems without great formalities.  Others are figuring out concurrency and throughput.  Still others are trying to integrate JavaScript closer to their native languages.  And don't forget the functional programming benefits, my favorite standard of better.  Let's face it, JavaScript was raised in a rough neighborhood before there were browser standards and many ideas of discipline just couldn't apply to the language.

Beyond just language features, there are the explosions of modules, web frameworks and build tools that erupt in the community.  This makes large amounts of software quickly outdated.  It means dependency management is a nightmare.  Here is a great writeup about [How one developer just broke Node, Babel and thousands of projects with 11 lines of JavaScript](http://www.theregister.co.uk/2016/03/23/npm_left_pad_chaos/).

It's not just dependency management that we're battling, but there are many competing ideas on how to create and share modules within a single application.  Modularity seems to have been an afterthought.  [Here is a non-trivial writeup](https://addyosmani.com/writing-modular-js/) of many of the modular JS ideas that could help straighten this out.

Our build tools have also embraced the same kind of [Wild West discipline](http://walkercoderanger.com/blog/2015/06/state-of-js-build-tools-2015/) that most of the rest of the tools are experiencing.

**In a way, this is all great news.  A lot of very smart and dedicated people are applying themselves to solving real problems in their applications and sharing that with the community.**

It also means that we very quickly run out of mental capacity to really embrace all of it.  We each pick the bits we understand or like and remain a fractured community.

When DHH ranted regularly about his way of seeing the world, a lot of people showed up for the debate.  It was a lively conversation and many of use that were trying to push Ruby into our day jobs found ourselves apologizing for DHH to our traditionalist bosses. These weren't really apologies as much as they were sideways compliments.  He was doing so much for our work lives and community that we could point out the incredible good he was doing, even if he was highly opinionated.

That was really a strategy that worked well for the Ruby community, although they were [exciting times](http://martinfowler.com/bliki/EnterpriseRails.html).

Brandon Hayes recently did an [excellent job talking about these kinds of community trends](http://confreaks.tv/videos/mwrc2016-surviving-the-framework-hype-cycle).  There is a hype cycle that is fun and new and exciting, and then there is the boring bits where people stick with the things that work and make billions of dollars in their companies.

And this gets to the heart of the problem with JavaScript, as I see it.  It's a perpetually hyped community.  There is a new web framework every time I turn around.  [This list](https://en.wikipedia.org/wiki/List_of_JavaScript_libraries#Web-application_related_.28MVC.2C_MVVM.29) currently puts that at 29 web frameworks written in JavaScript.  That number will grow soon.

**When the problem is that there is too much of a good thing, the solution is to pick something and deliver working systems with it.**

That is hard to do if you haven't done that before.  It means that you're probably wrong, whatever you choose.  Or, you're not going to get that same warm-fuzzy feeling of completion that helps you sleep at night.

I recently had this problem in spades while setting up the build stack for a project.  I decided to use webpack and Babel because they are rich tools with a majority of the present-day mindshare, I think.  That means there are StackOverflow articles, blogs, tutorials, lists and lots and lots of JavaScript modules prepared for setting up a highly-customized build environment.

Let me stress that last part one more time.

**There are lots and lots of JavaScript modules prepared for setting up a highly customized build environment**

So, that's the context of a problem.  JavaScript is what it is.  It affects our projects.  It affects our study patterns.  It affects our productivity.  What is the context of a solution?

**With all things software, the winning strategy ships working systems.**

The solution for me to stop worrying about things I can't fix is to put code in an editor and see what I can do.  More to come as I work on solutions I can live (thrive?) with.
