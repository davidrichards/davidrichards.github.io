---
layout: post
title:  Github Pages Tutorial
date:   2016-06-16 09:20:00 -0600
categories: collaboration
---

A friend asked me for a good tutorial on blogging with Github Pages.  I hadn't thought of it, but a lot of the tools we use here aren't necessarily in the wheelhouse of all the developers I work with.  Also, I couldn't find a good one that gave him what I thought he needed.  When my Slack reply was over 30 lines long, I realized I should just make this available for anyone.

This article is for anyone wishing to make regular contributions as a writer to a Github Pages blog using Jekyll.

**TL;DR clone your git repo, create and edit pages in _posts using markdown, use git to manage what is published.**

If you are setting up the blog from scratch, there's a good tutorial for setting that up [from Github here](https://pages.github.com/) and there's a fun interactive version of the same [from Thinkful here](https://www.thinkful.com/learn/a-guide-to-using-github-pages/).  When you're done with that, you probably want to follow the [Blogging with Jekyll](https://help.github.com/articles/using-jekyll-with-pages) link at the bottom of the Github link.

I'll start from the moment that's setup and you want to write articles.  Here are the things you need to know:

* It's just a git repository, filled mostly with text and configuration files
* Write articles in the _posts directory
* Write using [Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

### Using Git
If you're not familiar with git, Github has the [best references to learning git](https://help.github.com/articles/good-resources-for-learning-git-and-github/).  They also have a [Desktop application](https://desktop.github.com/) that manages all the commits, pushes and pulls you'll want to do.

If I start an article locally and don't finish it right away, I like to create a topic branch just for that article. I can push it up to origin and nobody will read the article until you merge it in to master.

### Writing Articles

When you're ready to create or edit an article, you will work with the files in _posts.  Use a file with a `year-month-day-article-name.markdown` format.  For example `2016-6-16-github-pages-tutorial.markdown` is the name of this article.

The article has a header, that looks like:

    ---
    layout: post
    title:  Github Pages Tutorial
    date:   2016-06-16 09:20:00 -0600
    categories: collaboration
    ---

* The layout is post.
* The title is a human-readable title.
* The date is the article date.
* You can use spaces between category names if you'd like to do that.

Write your article under the second set of triple dashes using [markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).

### Preparing the Blog HTML

Github will automatically compile the HTML for you when you push your articles up to origin.  Sometimes I just write an article, edit it in my text editor, and then fine tune it in my browser in the live site.  Not a lot of people are reading the information right then anyway.  If you're happy with that, you're done.

If you want to actually have a refined article before you push it, you'll need a Ruby environment setup locally and Jekyll installed.  You can go to a command line and type:

    ruby --version

When I do that, I get this:

    ruby 2.2.2p95 (2015-04-13 revision 50295) [x86_64-darwin14]

If you're using [rbenv](https://github.com/rbenv/rbenv) or [rvm](https://rvm.io/), you'll probably want a gemset setup for your blog.  I like doing this so that my blog dependencies never conflict with any other project I'm running on the same machine.

Once you have an environment you can live with, go to your blog's root directory and type:

    gem install bundler

then

    bundle install

That will take a few minutes and will load all the software you need to run jekyll locally.  To serve your blog locally, type

    jekyll serve

That will listen for changes in your blog and create the HTML you need.  You can see your blog at http://localhost:4000.

### Wrapping Up

That should get you at least started with blogging with Github Pages.