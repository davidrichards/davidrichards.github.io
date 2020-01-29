---
layout: post
title:  Shower Thoughts
summary: Two thoughts I've had lately that seem important days later.
date:   2020-01-29-03:18:20
categories: opinion
---

Two thoughts:

* There are more efficient ways to address healthcare costs in the United States.
* Knowledge bases in deep learning could start with small-scale toy problems.

## Health Care

<img src="https://i.imgur.com/hIZYj9O.jpg" width="600" />

So, health care in the United States is expensive. We pay a lot publicly, we pay a lot privately. There are reasons for this, involving emergent care, asymmetric bargaining, and preventative  care. There is also a very lucrative healthcare lobbying industry maintaining the status quo.

However, politics is for power. If people decide to address these problems competently, getting smart about expenses, bargaining power, and accountability, it would not only be more efficient, it would be incrementally achievable. Meaning, with better patient portals, I become my own healthcare advocate. With autonomous bargaining agents, many people can purchase things like insulin and Epipens at bulk prices. Relatively small efforts have relatively immediate effects.

It would take a systems intelligence to pull this off, keeping large concerns in balance, maintaining the integrity of agreements, and addressing core issues that should not be in our way.

Listening to [Mary Frances Berry talk](https://www.youtube.com/watch?v=qD7d1QS3y1c), these things seem tractable. However, I'm not convinced that the most efficient strategy is to reform the federal government, but to create consumer power with smart applications.

## Knowledge Bases

One of the things people want right now is an AI system that can address common sense. The blackbox combinatorial solver provides a common sense next-steps approach to many kinds of models. A knowledge base, however, is used for a different set of problems. Having common sense awareness of what we're talking about provides reasoning about elbows and knees because something is known about those parts of the body, not because they show up in certain ways in images or texts together.

People have imagined this would take a draconian effort, to train our networks how to recognize facts like this. They may be right. Some tractable tests would be interesting:

* Start with 10-100 facts.
* Train a network to use these facts in a toy problem.
* Import the embedding matrix, training event, and fact into a knowledge base.
* Incrementally choose harder tasks, adding facts and using old with new facts. Update the knowledge base.

What we end up with is a lot of artifacts, some of them developing deep and well-known uses for solving problems. Because we're keeping the embedding matrices, we're storing the patterns of how these facts relate to each other, how distinct they are in their ability to add knowledge when needed. We don't go for all the facts, we go for the useful ones and try and teach a system to curate what it needs to move forward.

Vaguely, I think an attention network using these facts in the attention vector could be a testing environment of what is or isn't useful, what supports and detracts from usability. A system can be balanced this way.

The end result would be a catalog of facts that can be used in other kinds of models. If it's a chat bot, the model would be a multi-modal one, with the fact embeddings alongside the language models, and layers that combine whether to use language model transformers or knowledge base facts. If it's a combinatorial solver, there would be layers that mix in these facts when it's more efficient to use them to learn the interface to the solver.

What we end up with is a mid-level system of working parts in networks, rather than pure types of networks. Nothing is built in one step. Nothing is thrown out once a model is discontinued. Everything is labeled. We learn how to assemble from many transfer learning tasks.