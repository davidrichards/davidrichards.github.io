---
layout: post
title:  Setup Kafka with Vagrant
summary: Evaluating Kafka for some upcoming projects, these are the resources I've produced that you can run in your own environment.
date:   2014-10-28 22:33:00
categories: software react
---
I recently had a problem with setting up Kafka in my development environment.  It had some dependencies that were older than the ones I was running locally.  No worries, that's what virtualization is for.

One way to create a virtual environment is to use [Vagrant][vagrant].  Setting up a Vagrant environment is fairly simple and it's portable.  You should be able to setup Kafka for evaluation with the tools I have here.

If you know what you are doing, you can just grab my [Vagrantfile][vagrantfile].

I started my work by following [Steve Connelly's][steve] [step-by-step example][steve_article].  Add notes about if it worked well, what I learned, etc.

Based on this, I wanted to setup the Vagrantfile using [Ansible][ansible].  Tell the story of anything important about using this work here.

Finally, I wanted to exercise Kafka a little.  I wrote a [producer] using Node.js and a few consumers:

* [R-based consumer]
* [Python-based consumer]
* [Node-based consumer]

In the future, I'll post about using this with Cassandra, Hadoop, and a few other tools.

[vagrant]: https://www.vagrantup.com/
[vagrantfile]: #
[steve]: http://www.objectpartners.com/author/sconnelly/
[steve_article]: http://www.objectpartners.com/2014/05/06/setting-up-your-own-apache-kafka-cluster-with-vagrant-step-by-step/
[ansible]: #

