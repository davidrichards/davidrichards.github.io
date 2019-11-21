---
layout: post
title:  Pipeline Patterns
summary: Things that will work in ten years are worth learning well today.
date:   2019-11-20-02:40:50
categories: opinion
---

As I move data between systems, I’ve noticed some patterns and principles that work well enough to share.

If I do one thing at a time, I am more efficient. This is true of me as a person, me as part of a team, and the tools I use. Be singular and benefit from simplicity.

If I create a simple interface, it’s easier to understand and use. Simple means the normal outcome works without configuration. It means I focus on what instead of how, what I want instead of how it will be handled.

Make systems configurable. If the normal use case isn’t what I need, make it easy to change. This is often done with dependency injection, pass in a piece of logic that can provide the different behavior or outcome.

React to the data rather than the configuration. If I have to configure a system, then I set the behavior in at least two places: in the configuration and in the code. Instead, look for keys, types, or patterns that inject the right behavior.

Write systems that can run in sequence. If I’m extracting data, have a few transformation steps, and load it somewhere, I’ll design the interfaces so the output of one step can be the input of the next step. I keep in mind that I may change the order of some of the steps, add some or remove some.

Address errors and back pressure directly. What happens when something goes wrong? Do we stop, raise, log, alert? What happens when there’s too much data? What happens when we need to run the same data more than once? What happens when we write bugs and need to fix them? Does order matter? The easier it is to make a mistake, the easier it is to handle things well because I can focus on the task at hand instead of worrying about what I would do when something goes wrong.

Consider writing service objects, classes that perform a single function. These are easier to test and replace. If you write these, don’t be afraid to memoize values. Trying to remember what side effects I may or may not have caused gives me a headache. It’s better to guarantee that things don’t change. This is especially useful when testing a new system or changing an old system.

Write unit tests. There are many kinds of tests that may be appropriate, but unit tests are almost always appropriate.

Create a productivity layer. Most libraries are designed to be useful to the greatest number of users, which means there are many low-level functions. Decide what works for your situation and write higher-level functions. For example, an upsert (find and insert or update data) can be implemented in code if you don’t want to use a database-level one. This is another way to say drive details deeper: make the steps you take simple and obvious rather than exposing how your dependencies work.

There are other good ideas, but all of these have been an important part of the last half dozen projects I’ve worked on.
