---
layout: post
title:  Actor Model
summary: A few notes on the main advantages of the actor model for distributed computing.
date:   2019-09-22-18:29:04
categories: raw
---
## Thinking About Actors

I've been thinking about the actor model for a project I'm working on. My challenge is to build a simple prototype today, and come back with a much more robust system later. So, thinking about the eventual interface with a few notes.

### Threads Are Difficult

Threads are difficult to trace and debug. The actor model is another approach to distributed computation that has worked well with Erlang, Elixir, and Akka on the JVM. Celluloid is a Ruby implementation (though it is no longer maintained).

[Storti, 2015]

### Unit of Computation

An actor works as a unit of computation. It receives messages, has an address, and works in isolation. The state inside the actor is local only, and immutable. An actor can create more actors, send messages to other actors, and designate what to do with the next message. In this way, the internal state can be shared safely with other actors.

[Storti, 2015]

### Fault Tolerance

Fault tolerance with the actor model has traditionally been allowing things to crash. This reduces efforts to write defensive code. The system can heal itself by recovering from crashes. The most common strategy for recovery is to restart the actor in its initial state.

[Storti, 2015]

### Distributed

With a well-architected actor model system, it doesn't matter if the message is local or on another node in the system. As long as there is network connectivity, the system can be distributed.

[Storti, 2015]


## References:

Storti, B. (2015, July 9). The actor model in 10 minutes. Retrieved September 23, 2019, from https://www.brianstorti.com/the-actor-model/


