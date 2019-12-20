---
layout: post
title:  The Data Lab
summary: The kind of data lab I want.
date:   2019-12-20-03:18:20
categories: opinion
---

I work with data. I have worked with data for a long time. Some of those projects have gone really well. There are some things that make these projects valuable:

* Experiments can be shared and reproduced.
* Data can be applied to models.
* Models can be transformed into services.

## Automobile Analogy

Imagine it is 1900 and you have a passion for automobiles. They're already around. Verbiest may have made the first one 227  years ago. His was a steam powered contraption, but you're into the combustible engine—power is your thing. Time traveling us may have been clever if we pointed out Niépce's electric car in France, but you've got gasoline in your veins and Benz is your guy. 31 years ago, Benz has invented the modern automobile, and now Daimler, Peugeot, and many others have been building cars for a decade.

These are exciting times. What do you do?

Like many people, you find a garage somewhere and start tinkering. You get an engine working and maybe you sell a yet-to-be-released car to your cousin who inherited the family fortune. Cobbling together the technology of the day, you are able to get that fresh car over to your cousin only 1 year later than you promised. Congratulations, you're an automaker.

That took a lot of effort, so you gather people from the neighborhood, organize yourselves a little, and pretty soon you can get 5, maybe 10 cars built a year. These are expensive, but your sister has an eye for beauty and your buddy from school can talk a chicken out of its feathers. People are willing to keep you in business.

Because we know the story, we know exciting is about to get wild. Henry Ford will automate this whole process and give his factory workers raises so they can afford to buy his cars. Soon we're priced out of the market and the best we can do is say we were there when automobiles became a thing.

## State of Data Work

I think this is where we are with data work today. I think there are competent engines in traditional machine learning and deep learning. I think there is enough data, enough talent, and enough solvable problems to turn a profit peddling machine learning skills. This could go on for years, and it probably will.

What comes next though is an automation of our industry. Vendor services that have seen more data have been tweaked and optimized are often already better choices than the models we can build.

Our job changes from writing models and delivering them to comparing models with other services and choosing between those we do best and those others do best. All of it needs to be usable somewhere, probably in a cloud service.

## My Assembly Line

For me, the data service assembly starts with experiments. The [nbdev tools](http://nbdev.fast.ai/tutorial) [^nbdev] can turn a Jupyter notebook into a model-building pipeline. That tool adds testing, documentation, model versioning, and sanity to the process of learning from data.

Evaluating models against different datasets can be automated. By running a model in an experiment loop, I can evaluate how the model performs with different hyper parameters and against different data. Progress can be documented in the project. [MinIO](https://min.io/) [^minio] can store and share my models. 

Services can be built in Kubernetes and exposed as a service with Flask. With versioned, stored models, we can link the experiment documentation to the service so people can know about what to expect by using these models.

Cloud infrastructure can be built around all of this to monitor, secure, scale, backup, and maintain the lab. A Hydra engine can manage the agreements we have, tracking costs, expectations, time, and inventory. This final effort assists us in focusing our efforts in the most productive areas.

## Incomplete Work

This isn't complete work. A lot of what I'm talking about exists in various projects and experiments. I'll be gathering this into a single place and demonstrating how it works over the next few months.

[^nbdev]: [nbdev](http://nbdev.fast.ai/tutorial) FastAI develops in notebooks first. The nbdev tools are a smart way to extract that code into libraries.
[^minio]: [minio](https://min.io/) MinIO works as an abstraction layer for storing objects locally or in the cloud.
