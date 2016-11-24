---
layout: post
title:  Data Exploration with Elixir
summary: Exploring data using elixir-metrics
date:   2016-11-24-12:18:00
categories: development data
---
I put a lot of stock in data exploration. Why? It gives me the preview to the kinds of questions I need to be asking about my data.  

What is data exploration? It's the initial look over the data, to see what's there.  How many values are missing? Is it continuous, categorical, or time series data? What is the shape of the data? What correlations and limits might prompt my work?

Let's say I have some data:

    [...]

Now do a pandas-similar approach to the data I've seen.

This gives me univariate data.

Now do some bivariate exploration.

Now explore some time series

Make sure I have examples for:

* normalization
* scaling
* encoding


[histogram]: https://github.com/HdrHistogram/hdr_histogram_erl
[statistics]: https://github.com/msharp/elixir-statistics
[metrics]: TODO: Move to github


