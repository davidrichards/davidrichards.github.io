---
layout: post
title:  Daily Post for September 10, 2019
summary: Rough draft ideas from things researched around September 10, 2019
date:   2019-09-10-07:46:56
categories: raw
---
## Distributed Systems

Reviewing a few ideas on distributed systems, I found this great summary by Orosz from his experiencing rebuilding the payment system at Uber. Most of his ideas come from Designing Data-Intensive Applications by Martin Kleppmann.

### Create an SLA

When designing a distributed architecture, decide what healthy looks like. How do I know a system is working? A service level agreement (SLA) defines how we measure a system's performance, and what the threshold level of problems can be. There are different types.

Availability measures how much downtime is allowed. Convert the percentage to minutes downtime per year, such as 99.99% availability provides for 50 minutes of downtime per year.

Accuracy addresses whether any data can be inaccurate or lost. Consider data systems that provide eventual consistency but users might get out of date information from time to time.

Capacity addresses how much load a system is designed to support. If we are nearing capacity, all other guarantees may be challenged. Report this in terms of requests per second.

Latency measures how much time until the system responds. Use a 95% and 99% response time so that truly irregular issues can be handled differently.

[Orosz, 2018]

### Scaling Strategy

As businesses grow, their system load increases. How will new capacity be added? Typically, this is vertical or horizontal scaling, or buying bigger/stronger machines vs adding more machines to the system. Horizontal scaling is almost always preferable to vertical scaling.

[Orosz, 2018]

### Clustering

A lot of systems have a higher availability than their nodes, such as a 99.999% availability (down about 5 minutes / year) on nodes that are available 99.9% of the time (down about 8 hours / year). This can be done by clustering the nodes.

[Orosz, 2018]

### Consistency

It is not trivial when nodes are going up and down to keep them consistent. A system must ensure the nodes have the save information, that they are communicating to each other, that they remain in sync. With messages between nodes, when they fail, means some data can get lost or nodes might become unavailable.  The three main consistency models are strong consistency, weak consistency, and eventual consistency. Typically, the weaker the consistency required, the faster the system can be. Some parts of a system might need to be strongly consistent whereas less mission-critical parts can use tradeoffs for performance.

[Orosz, 2018]

### Data Durability

Data durability means that once data is stored, it will be available later. This is true even when nodes go offline, crash, or have data corrupted. Some systems handle this at a node level, some at a cluster level, and some don't provide this. Replication is usually how durability is addressed. Many tools such as Cassandra, MongoDB, HDFS, and Dynamodb all support different levels of durability.

[Orosz, 2018]

### Message Durability

Message durability addresses whether messages will arrive. RabbitMQ, Kafka, and other systems are usually used for this. Message persistence means that when a failure happens on a node processing a message, the message will be there to process once the failure is resolved. Message durability means if a node or queue goes offline when a message is sent, it will still get the message when it comes back online. There is a difference in complexity between a message delivered exactly once and at least once.

[Orosz, 2018]

### Idempotency

Connections may drop or requests may time out. Clients often retry these. An idempotent system ensures the execution occurs only once. For an idempotent, distributed system, some sort of distributed locking system is required.

[Orosz, 2018]

### Sharding

When storing more data than can be held on a single node, we commonly shard the data, meaning the data is horizontally distributed with a hashing strategy to assign data to a partition. Resharding is an interesting challenge. Most distributed systems process across multiple nodes, using a voting based approach, meaning a certain number of nodes must get the same answer before the operation is successfully processed. This is a quorum.

[Orosz, 2018]

### Actor Model

The actor model addresses the code in terms of communication. With the actor model, an actor sends messages and reacts to messages. Each actor has a limited set of things it can do. With basic rules, a system can repair itself after an actor crashes. Another approach is CSP--communicating sequential processes.

[Orosz, 2018]

### Reactive Architecture

The goal is usually to make a system resilient, elastic, and scalable. Reactive Architecture is one way to do this. The Reactive Manifesto describes a consistent and complete way to address the full system, to test whether your solution is fully designed.

[external link](https://www.reactivemanifesto.org)

[Orosz, 2018]

## Uber is a Cautionary Tale

Uber, once valued at $76B, IPOed at $71.1B and currently has a market capitalization of $54.5B, just months into their experience with public market investors. 500,000 people removed the app from their phones with the #deleteuber Twitter campaign. Problems began with Susan Fowler's blog post about how the company ignored her sexual harassment complaint. There were also problems when reporters revealed Uber had programs to spy on competitors and deceive government officials. The efforts flattened Uber's growth and resulted in investors pushing the founder and CEO, Travis Kalanick, out of Uber.

[Kessler, 2019]

## Greyball

For four years, Uber had a worldwide program to deceive authorities with a tool called Greyball. This involved officials in Boston, Paris, Las Vegas, Australia, China, and South Korea. It was part of operation VTOS, violation of terms of service. Basically, if a rider is thought to be an enforcement officer, a fake app is served, that obstructs regulators' ability to gather evidence against Uber. The project was approved by Uber's legal team. They also used UberX to get drivers quickly approved before local regulators could stop them.

[Isaac, 2017]

## Cognitive Distortions

Our mind convinces us sometimes of things that aren't true. These are called cognitive distortions. Typically, they will reinforce negative thinking or emotions. We think we're rational and accurate, but really we're just feeling bad about ourselves. An example would be, "I always fail when I try to do something new; I therefore fail at everything I try." This is an example of polarized thinking, everything is black or white. If they went further and said, "I must be a complete loser and failure," then they're overgeneralizing.

[Grohol, 2019]

## References

Grohol, J. M., & read, P. D. L. updated: 24 J. 2019~ 7 min. (2016, May 17). 15 Common Cognitive Distortions. Retrieved September 9, 2019, from Psych Central website: https://psychcentral.com/lib/15-common-cognitive-distortions/

Isaac, M. (2017, March 3). How Uber Deceives the Authorities Worldwide. The New York Times. Retrieved from https://www.nytimes.com/2017/03/03/technology/uber-greyball-program-evade-authorities.html

Kessler, S. (2019, September 4). What Went Wrong at Uber. Retrieved September 9, 2019, from Medium website: https://onezero.medium.com/what-went-wrong-at-uber-b9e9ce0faa85

Orosz, G. (2018, April 16). Distributed architecture concepts I learned while building a large payments system. Retrieved September 9, 2019, from The Pragmatic Engineer website: https://blog.pragmaticengineer.com/distributed-architecture-concepts-i-have-learned-while-building-payments-systems/



