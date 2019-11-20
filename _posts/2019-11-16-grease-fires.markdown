---
layout: post
title:  Grease Fires
summary: Rather than starting grease fires, build furnaces.
date:   2019-11-16-01:40:50
categories: opinion
---

When writing software, there are principles that make it easier to deliver something valuable. Just like I would rather have a working furnace in my basement than a grease fire on my stove, I would rather have a complicated but reliable software system than one that was quick to throw together.

It's better to build a furnace than start a grease fire. A grease fire usually comes up with cooking, the cooking grease is on fire. The problem with a grease fire is water and oil don't mix, so throwing water on a stove on fire spreads the fire. Soon the whole kitchen and later the house is burning because the energy of that fire isn't contained by throwing water on it, or letting it burn on horizontal surfaces.

An alternative way to have a fire is a furnace. A furnace has a thermostat, hot surface ignitor, burners, and a heat exchanger to turn a need for heat into heat safely. It also has a return duct, air filter, blower motor, supply plenum, and flue to handle cold air, hot air, and exhaust. It's a safe, known system that can distribute heat in a home.

In 1967, Melvin Conway introduced the concept that organizations produce designs that copy the organization. Everyone ships their org charts in their products (Wroblewski, 2019). This is sometimes called Conway's Law, though Stephen Sinofki from Microsoft made the concept more popular. When we ship our org chart, we are building a grease fire. The easiest way for us to think about and solve a problem is what our customers get from us, whether or not that is best for our customers.

When a software product is designed like a grease fire, it's horizontal. There are data structures over there that have a magical influence on logic over here. There are no clear interfaces that drive the core business logic. Things are allowed to spring up without documentation or a sense of overall constraint.

A new person joining the team building a grease fire doesn't know where to start. They see methods that are over 100 lines long. They hear terms at stand up meetings that aren't in the documentation or code, special ways the team has learned to keep this fire contained. See, if grease is burning on my stovetop, and I know that's what's happening, I'm not going to throw water on it, and I'll treat the situation with the care it deserves, but the new developer doesn't know that, and regular efforts to contain the situation could be disastrous.

Another hint that you have a grease fire can be found in how long it takes to setup a development environment. Ideally this works in minutes. With large systems, it may take hours or the better part of a day. If it takes a week and your developer still isn't sure they got it right, you have a grease fire.

How do you turn a grease fire into a furnace, chaotic energy into something productive? Drive the details deeper and ensure there are testable interfaces.

Driving details deeper means there is an understandable interface that requests or drives the program flow. It means I can reason when I request this, I get that. It means a reasonable call can be handled by default, and that special cases are well documented and handled at the same interface as the reasonable call.

It also means the structure of the code is testable. I can mock out whole subsystems like messaging, storing data in a database, or parsing an HTML request outside of the main flow of some code. It means the setup of a normal unit test is 1 or 2 lines, and special edge cases no more than a handful of lines.

This structure gives the code purpose. It makes it understandable. It keeps developers from increasing chaos when they make a contribution. It means someone knows what the code is used for and builds a reasonable flow for that purpose.

I have a special set of tools that work for me to create this kind of furnace. Typically, it's unit tests and service objects. You don't have to use my style of coding to get my style of results. You can design anything you want to design, but drive the details deeper and ensure there are testable interfaces.

And the bit about shipping the org chart? If I have independent and indolent developers, you can see it in the code. It looks like a grease fire. If I have several waves of developers that came and left the project and I can see this in the code, I have a grease fire. If I have aloof and demanding managers that just want results, that too can be seen in the code.

Think of thinking as a system, that feelings and thoughts become standards and systems that become the reality of the future. All of the small choices we make turn into hardened bits of logic in our software. Use principles to constrain those bits of logic and make them easier to manage as a project matures.

## References

Wroblewski, L. (2019). Mind the gap, user centered design in large organizations with Luke Wroblewski. Retrieved from https://www.youtube.com/watch?v=mAiNdU1go1A


