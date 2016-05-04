---
layout: post
title:  Where Are We Going?
summary: An effective leader gets their people to ask "Where are we going and how can I help?"  These are lessons learned from effective and frustrating experiences delivering software systems for over 20 years in the business.
date:   2016-5-4-00:33:00
categories: development
---

"Are we there yet?"

This is the whine from the backseat of many road trips.  Maybe you've been on some of these?  I have, both as the driver and the impatient child.  It's hard for a child that doesn't have as strong a sense of time or patience to sit still and enjoy the journey.  Without having anything to do, it's even harder.

As a parent, I've learned to patiently set the context with my children as we prepare for a trip.  I then talk to them about what we're doing, how far along we've made it, and interesting things we're passing.  Well, they're interesting to a dad anyway.  With an ongoing conversation, at least the time passes quickly and I don't get asked that question.

Thinking about it today, I realize that "Are we there yet?" is a euphemism for, "I don't want to travel with you any longer."  The journey just doesn't seem worth it at those moments.

I think this is true in our business life as well.  **A leader needs to sell the team on where we are going and how we'll get there.  In fact, if they haven't done this, very little else really matters.**

It's even worse with software developers.  We are problem solvers by craft.  Until we're sold on where we're going, we naturally treat it as an unsolved puzzle and often get carried away trying to do the leader's job for them.  It's an advanced form of [nerd snipping](https://xkcd.com/356/).

<img src="https://imgs.xkcd.com/comics/nerd_sniping.png" height="400px" />

So, for software developers, they need to be assured (**often**) that the problem isn't the organization, the product or anything else.  The problem is a particular set of prioritized issues and features.  If that's not known, the problem is figuring those out.  Software developers can reason with product owners about whether a customer will notice a feature or whether a bug is critical or minor.  It's not really a negotiation, just a little bit of information needs to be shared.

This is important for productivity.  It's also important for cost management.  Engineering is usually one of the most expensive parts of a project, some of the riskiest components, so getting engineers to push along is critical.

### So, why is it so hard for most companies to figure this out?

It's rare, in my experience, to actually get a team to work together and move in the same direction.  And, we don't live in an autocratic society.  Right now, it's usually pretty easy for a developer to leave a company and get a job at higher pay.  There just aren't enough software developers for current demand.  So, trying to control every aspect of a person's thinking and loyalty is a futile experience.  Only the insecure will stick around in the face of utter control.

What I've seen work is respecting why the key players are at the table.  As in all things, [never delegate understanding](http://www.eamesoffice.com/the-work/never-delegate-understanding/).  A leader can't wield knowledge they never had.  Figure out what's actually making people tick and help them turn that into something valuable for the company.

A particularly loyal employee told me why he was willing to stay so long at a troubled company.  "The CEO never failed to appreciate my particular skill set.  After that, of course I'd do anything he asked."  The leader knew why this person was at the company, what brought him fulfillment and clarity.  The CEO honored that, and this talented human moved mountains for him.

Put another way, by recognizing the talents my friend had, they made it easy to answer the more-important question: "how can I help?"  Outside of caring for children, humans don't often do something for someone unless they actually want it.

### An Ugly Chapter (one time it all went terribly wrong)

As a counter example, I once had a particularly caustic conversation with a superior at my organization.  The event happened after a long series of strange behaviors: people being marginalized and fired and then lies about what happened, highly productive teams being dismantled because this particular leader wasn't in control, whole projects being scraped because a few problems were still unresolved.  Morale was pretty low and about half the engineering team had already left one way or another.

<img src="/images/the_dictator.gif" />

We had a lot of people kind of stuck and so I started showing them ways I break down a problem.  I like to start with ServiceObjects, or single-purpose classes.  The business logic is more apparent, it's easier to test, other abstractions are easy to compose once the work is broken down that way.  Most importantly, we're not lying to ourselves about what the "right way" to build a system looks like.  Does it work?  Can we improve it?  Is it worth it?  This is the foundation of a pragmatic approach to delivering systems (rather than whatever the hell this guy's been up to).  It solves the number one problem every coder has, actually coding something.

Anyway, I guess this code was offensive to him.  The back story involves many egregious and obvious failings of this particular person (making promises without understanding, having me work two positions because he hadn't planned or communicated, actually developing team members that were to take over the system after I was moved to another corner of the company).  It was a hornet's nest.

There was a bug in my code.  It involved about 3 lines of code.  It took me about 5 minutes to find where the bug was and 2 hours to keep him from trying to blame all the other parts of the system.  He was actually acting like a first-year coder throwing a tantrum.  It was a pathetic moment in our relationship.

The next day, he had built an elaborate graphic to try and show all the faults in my system.  He included parts of the system that was written way before I was there and systems that I didn't have the time to rewrite/refactor.  He chose the way to discuss this was in front of about 3 dozen people.  He chided and goaded me, everything but flat out calling me stupid in front of the company.

At this point, my mind goes to a series of facts.  This man has never delivered a full working system in his life, not at the scale and quantity that I do.  He has never stuck with a project until it was finished.  He has never built a team or developed another person's talent so that they are successful.

We finished the "conversation" and he ended up saying things like, "at least we didn't end up in a shouting match" and "I'll get the others to see it my way."  It was a point of pride for him that he could dominate this particular piece of code.

Was he right?  Absolutely not.  Not because there isn't a better way to write it.  Not because maybe we could have used other patterns, other abstractions.  We had the code we had because of the environment and choices he made.  Also, we got to this point because that is a way to evolve an idea.  Nobody that actually delivers systems goes online to try and find people that agree with them.  They open their editor and deliver systems and improve on them when they can.

**Did we have a clear view of where we were going?  No.  Did I know where I could help?  Apparently not.**

Even now, thinking about the experience, the story sounds fantastic.  Surely there was more going on?  Probably.  Could it have been worked out?  Probably.  But notice how at the end of the day, this person took from me any sense of participation, ownership or commitment to the company's success.

This was a crucial moment when something broke in me.  I stopped caring and started reaching out to my network for my next position.  It was like the moment a parent starts yelling at their kids to shut up and they'll tell them when they arrive.  A lot of potential good was destroyed in that moment.  At the very least, I had to conclude that this relationship doesn't work in this context.

### This isn't about culture

Notice how, in my opinion, the answer is to get someone that sees where a leader is going and wants to pitch in.  **It's not about creating culture.**  Despite all the hype, culture is a cheap substitute for strategy.

Actually think about that for a moment.  There's a strategy/culture trade off.  If there's a strong strategy, people get vested and excited about their contribution.  If not, people get excited about getting along, having fun, being personally recognized.  It becomes about looking good rather than doing good.  Even in cultures of delivery, the external pressure of delivering something isn't as useful as the internal desire to produce something important.

That means it's not about who's in charge.  It's not about leadership style.  **It's about wanting to be part of the core purpose of a team.**  And, in my experience, wanting to be part of that purpose is a lot easier and cheaper than trying to manufacture culture.

That's because when we get a job, we almost always developed some real talent to be there.

<img src="http://i.imgur.com/Ihgu0xe.gif" />

Developers especially paid an incredible price to be at their desks.  For me, it was attending lots of school, reading hundreds of books, spending near 80,000 hours of practice (I'm a workaholic though I'm less and less proud of that as I grow older).  I had to really want to be there, and my experience isn't unique.

We worked incredibly hard to get there.  We have incredibly critical reasons to be there.  Use that to get someone to care about where you're going, and you're a leader of software developers.

**This really is an issue.**

Believing in where we are going and having some ownership of the solution is the easiest cure.  I'm not talking about equity or options.  I'm talking about just letting people deliver worthwhile contributions and thanking them for it.

<img src="http://i.imgur.com/b3SwpNR.jpg" />
