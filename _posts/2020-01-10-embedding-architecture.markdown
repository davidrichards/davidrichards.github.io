---
layout: post
title:  Embedding Architecture
summary: Thinking about data architecture
date:   2020-01-10-03:18:20
categories: opinion
---

There is a code challenge that I saw that asks the developer to create a friend of a friend network with arbitrary attributes attached to the people in the networks. The goal of the exercise is to demonstrate the developer understands a technology stack and a little about graphs. What I learned from thinking about the exercise was how machine learning and profit centers influence the data architecture of the system.

Normally, I would think about the problem in terms of pages in the application: there's going to be a list of people, a user profile, an attribute form, and a few similar pages. Given the flexibility of the people in the network and their attributes, the system would create abstractions around those unknowns. That's enough to figure out what database tables I need, and how to index those tables.

Then my imagination took over. What if I trained a model to learn the reachability of people in the network? Say I track a few things about the nature of that relationship and predict whether new connections are likely to be formed just because they're available. Not everyone I've met would want to meet each other. That has to do with them, me, how long it's been since we worked together, those kinds of things.

I would train the model using embeddings for the categorical information. Instead of 'boss of' as 1 or 'employed by' as 2, I learn 'boss of' as [0.1, 0.2, 0.15] or 'employed by' as [0.2, 0.1, 0.15]. These embeddings give the model a place to store the richness in that relationship and how they influence the behavior of people. The embeddings become an artifact I can extract from my model. I'll transfer them into other models when I'm doing similar work. I'll cluster the attributes with them to learn what those patterns mean in terms of things I can influence or understand.

So, reachability would involve how the network grows. I would also want to model how valuable the relationships are inside the network. Now that there's all this friendship, what good is it? I'd predict this value using the same methods, developing embedding matrices for each category in the network.

Imagine reachability and interaction are critical to profitability, so this question remains stable in everyone's minds as important. I learn quite a bit more about what's led to my success, but I also have really good tools to figure out what something new may mean.

As an example, say I decide to add college degrees into the attributes I track in my network. I get some data and update my models. Knowing about the education of each person, do I know more about reachability and interaction? Does education behave more like job title or more like hobbies?

From here I can experiment with ways to encourage more-profitable behavior in my network. I know the factors that drive people. I know if new factors are significant, and if so in what way they are significant. I can direct what features to put in the application, what approaches to try in marketing, and which reports to provide.

The algorithms I use to build models may change, but the outputs don't. The activities I use in the business to enhance behavior may change, but the outputs don't. The screens and user interaction may change, but the but the outputs don't.

I can imagine the next 100 changes proposed for this network and none of them disrupt the core data relationships. I need tables for people, friendships, attributes, and a few join tables. I need space for the embedding vectors mapped to categorical variables, probably in an object store. I need my models in an object store. I need indexes so graphs are easy to assemble and search.  I'll have the graph on people built by friendships and the graph on attributes built by clustering on the embedding vectors. I'll need cache on things that are slow to compute.

What I've just done is create a fairly stable data architecture by combining the user experience, business profit centers, and machine learning to understand the profit.