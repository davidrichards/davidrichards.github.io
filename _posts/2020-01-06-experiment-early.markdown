---
layout: post
title:  Experiment Early
summary: Lessons learned from using nbdev.
date:   2020-01-06-03:18:20
categories: opinion
---

Sometimes ideas get out of hand and a small improvement becomes a big project. Building systems bottom up can keep small things small and let important things grow up. My experience with nbdev over the holidays reinforced my confidence that incremental improvements matter.

Jeremy Howard and Sylvain Gugger [released nbdev](https://nbdev.fast.ai/tutorial/) last month, a few tools for creating tests, documentation, libraries, and Python packages from Jupyter Notebooks. I setup a hello world project while listening to them discuss the project and had something working by the end of the video. I then setup another project and began gathering tools from around my hard drive. It felt great to convert notebooks into libraries.

## Slow is Smooth

Many data people prefer working in interactive environments--Jupyter Notebook, the R console, Google Colab--whatever tool that makes it easy to test ideas, visualize the results, and keep things light. This is how I do it. Working this way, I take small steps. I think about one thing at a time. If I can't quite remember how a function works, the documentation is a few keystrokes away. If something isn't working out quite right, I run a few tests until I understand it. Pretty soon I have something that makes sense.

I've heard disparaging comments about this kind of work. The most confrontational went something like, "be a grown up and write code in an editor." I am a grown up. I've worked in plenty of editors. I prefer notebooks.

Jeremy Howard perfers notebooks too. He's reported that he gets a 2-3x productivity boost in writing software when working in a Jupyter notebook. Showing serious improvements seems grown up to me.

With my experiments with nbdev over the holiday I focused exclusively on the notebook. How does it feel to work on something large across many notebooks? It's a bit confusing until I start to think about the problem differently, then it gets easier. How hard is it to write tests and harden my code? It's incredibly easy. In fact, I rely on simpler tools, assert and a few functions that I wrote instead of anything heavy or complex. How hard is it to run tests across all of my work? It's a single line at a command prompt. How easy is it to create library code from notebooks? Another single line at a command prompt. How about documentation? Theoretically, that's a one-liner, but I have a few things not working with that right now. We'll see.

What all of this means for me is I'm doing one thing at a time. I'm focusing on completely engrossing myself in what I'm doing, getting it to work well, then integrating that with other things like tests, libraries, and documentation easily. This is smooth work.

## Smooth is Fast

Once I stopped trying to architect big things, I started to pick up speed in my work. What I tried to do was design a big system for managing data lab artifacts, incuding class interfaces and diagrams with lots of arrows on them.

The smoothness from working in a notebook comes from the bottom up. It comes from getting things working and making sure those things work later in a larger context. There's nothing wrong with writing classes to organize code, but I found that a few functions in a module are simpler and easier to use.

This reminds me of the many things I don't often do, because it takes a large shift in my thinking. This includes some articles I haven't written, some projects I haven't finished, and some areas of my projects I've ignored for too long. If it's going to take a large effort, I sometimes wait until I feel up to the challenge.

Incremental improvements doesn't require me to do massive things. If something's bugging me, I can run the code and play with it. If something's not quite working, I can focus on one little thing until I understand what is going on there.

This is just the mindset of finishing things. There are no tricks involved.

## nbdev is Nascent

This is a nascent project. It's quirky. I created a third project with it last night and one of the configuration files didn't transfer with the github template. My documentation is a bit quirky. Sometimes I have to update my library to get my code to work correctly on Github.

Part of the fun with this tool is it integrates with Github. Committing code means building a test environment, running tests, building the documentation, and ensuring my code is up to standards. So the newness of the library can be a bit disruptive in this integrated environment. I'm OK with that right now.

What I really gained from my experience was a joy of creating again. It feels like the earlier days in my career when I learned how to write small bits of code and test them. It feels like I dont' have to do great things all at once. I'm looking forward to doing small things well.
