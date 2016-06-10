---
layout: post
title:  The Paradox of Big Data
summary: Curious people find more questions to ask when the data is bigger.  This is a review of pragmatic principles for data analysis.
date:   2016-6-9-11:10:00
categories: development data
---

We had a great time at the [Utah County Data Science Meetup](http://www.meetup.com/Utah-County-Data-Science-Meetup/) recently.  We talked about data exploration and released a [toolkit](https://github.com/Utah-Data-Science/data_exploration_toolkit) for working through data problems using Pandas.  It's a work in progress.  We're collecting our best tips and tricks.  Already from this I've been collaborating with several of the people in our group and we've been having a great time exploring new data sets.

A lot of the strength is in the tools brought together with Pandas.  We work in [Jupyter notebooks](http://jupyter.org/) with [matplotlib](http://matplotlib.org/), [NumPy](http://www.numpy.org/), [scikit-learn](http://scikit-learn.org/stable/), whatever makes the job easier.  If this is your thing, [Learning the Pandas Library by Matt Harrison](https://www.amazon.com/gp/product/B01GIE03GW/ref=nav_timeline_asin?ie=UTF8&psc=1) is an under-appreciated resource for you.

**However, there's always data envy.**  Our work on data that fits in memory is shameful somehow.  I think there are a lot of really sexy projects out there that do interesting things on Big Data, though I don't tend to focus on that kind of data set.

Why?

When Big Data started hitting our radars, we had some basic concepts repeated:

* Cloud computing and storage makes more and more analysis affordable
* There are Internet-sized problems to solve
* These take different approaches
* MapReduce (and later other approaches) work well with data like this

This is good.  In fact, there's a [free course from UC Berkely](https://www.edx.org/xseries/data-science-engineering-apache-spark) that is just opening that will teach you to do this with Apache Spark.  **However, it takes a lot of work to get proficient in this completely different way of approaching a data problem.**

## The Paradox

With all that work looming, there's a paradox with Big Data that kind of lets the air out of that balloon for me.  [Andrew Gelman](http://andrewgelman.com/2005/07/31/n_is_never_larg/) said it this way:

> Sample sizes are never large. If N is too small to get a sufficiently-precise estimate, you need to get more data (or make more assumptions). But once N is "large enough," you can start subdividing the data to learn more (for example, in a public opinion poll, once you have a good estimate for the entire country, you can estimate among men and women, northerners and southerners, different age groups, etc etc). N is never enough because if it were "enough" you’d already be on to the next problem for which you need more data.

Since I'm always breaking it down, **the more-interesting problems actually fit in a modern laptop's memory.**  I may need a modern Big Data pipeline to get a sample of interesting data, but I still prefer to work on data with medium sized tools.

## What Do I Suggest?

With all this in mind, this is the approach I'm advocating (for starters at least):

* Build in the Small
* Apply in the Large
* Stay Curious
* Use Python
* Use Jupyter
* Avoid Fancy Data Stores
* Use a Data Pipeline

## Build in the Small

Try building models on a small amount of data.  I will sometimes sample my data set and work on tens of thousands of records instead of millions or billions.

Reviewing the [Pragmatic Programmer ideas](https://blog.codinghorror.com/a-pragmatic-quick-reference/), this seems to fit a lot of their ideas:

* Use Tracer Bullets to Find the Target
* Prototype to Learn
* Don't Assume It -- Prove It
* Finish What You Start
* Estimate the Order of Your Algorithms
* Refactor Early, Refactor Often

Some of these are a bit of a stretch, but they boil down to the same pragmatic aesthetic that works.  I find when I'm analyzing data especially, I need to have my pragmatic hat on.  There is a lot to remember, research and review.  It doesn't work if I'm trying to take on too much or work with unwieldy data.

## Apply in the Large

With good sense about data and the insights available, I can then try and apply these things at scale.  I can serialize a model and run it inside an application.  I can wrap my work in an API and make it accessible as a separate service.  I can even translate all that work into an optimized workflow that's meant for large or even Big Data.  **There are many ways to take this work to the people at scale, once I have insights to share.**

## Stay Curious

If I try a few unoptimized approaches at exploring or modeling my data, I can start to see the bigger picture.  Where are there likely relationships?  Where are there problems in the data?  What data doesn't look very normal?  How do the variables relate to one another?

If I'm asking a lot of questions, I don't have time to build up an infrastructure.  That leads me to my next point.

## Use Python

The analytic tools in Python are well tread.  I like working in Clojure, R, Ruby, and many other languages and environments.  Python is application ready.  There are tools there that are optimized for complex computation.  There are pipeline tools.  There are API-building tools.  There are great resources for gathering and transforming data.

Why reinvent this wheel?

Once upon a time, I tried to do that.  I found an old conference talk I had given in Texas in 2008 that made me cringe.  I was talking about data analysis with Ruby.  In that talk, I admitted that Python had better tools, but I preferred to work in Ruby.  That was hubris.  That was really a bone-headed perspective.  The people that make this work make this in Python.  It's not only Python, Java and Clojure and Spark and Scala and R and many many other great opportunities for solutions are out there.  Just don't start there.  Start with Python.

## Use Jupyter

It turns out that dialog and language are really important for software development.  It's not conclusive, but [evidence suggests](http://www.fastcompany.com/3029364/this-is-your-brain-on-code-according-to-functional-mri-imaging) that we use the language portions of our brains when writing software.  This makes sense to me.  It's not really very mathematical.  Yes, we need to be logical, but we also need to have logic when we write or speak.  It's more-logical than informal language, but that's just a detail.

So, how do we access these parts of our brains? I write blog articles.  I write in Evernote.  I walk around the office with hands waving in the air talking to myself like a lunatic.

I also write in [Jupyter](http://jupyter.org/).

Why?

I can mix dialog with code, data visualization and LaTeX markup very easily.  I can export this in many formats.  I can engage in my work.  I can try things first and clean them later.  I can describe to the next person that goes through my work what I've been able to accomplish.

When I talk about my data analysis, I can often see things I didn't consider the first few times around the data set.  This goes back to staying curious.

## Avoid Fancy Data Stores

I'm working on replacing a legacy application that wrote to MongoDB.  The application is only 5 years old.  It wasn't written in a way that scales well.  Mongo can scale, if you know what you're up against and [understand the drawbacks](http://www.sarahmei.com/blog/2013/11/11/why-you-should-never-use-mongodb/).  Mongo was chosen because it was popular at the time, and people thought they had a problem they didn't actually have.

I've heard of several similar projects going on in the businesses within a half mile of where I work.

**My advice is try and get simple things done first and get on with it.**

## Use a Data Pipeline

Provenance matters.  Once you've made a point with data, the next question is almost always, "Where did the data come from?"

More annoying is not being able to reproduce a data model on a second sample.  If I've forgotten a step or left a script in some corner of some hard drive somewhere, I'm toast.

Practically speaking, I just take notes on paper for this.  Sometimes I use my Jupyter and it works well.  If it gets rough, especially with the ETL portions of the project, I write and store scripts in a git repository.

[Another analyst (Jeff Potter)](https://github.com/jpotts18) in the area likes his experience with [Airflow](http://nerds.airbnb.com/airflow/) from Airbnb.  He likes it more than [Luigi](https://github.com/spotify/luigi) from Spotify because Airflow gets more love and maintenance from their corporate sponsors.

Whatever you choose, just remember to have a plan to explain and reproduce your results when you're finished.

<blockquote class="imgur-embed-pub" lang="en" data-id="kcUcGhK"><a href="//imgur.com/kcUcGhK">Crazy Disc Golf Throw</a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>

**Bottom line**, I think you get a lot more accomplished by first focusing on medium-sized data and getting high-quality models and insights rather than learning all the latest Big Data tools and perspectives.  With the Big Data Paradox, you're going to want to be asking those kinds of questions on mid-sized data eventually anyway.