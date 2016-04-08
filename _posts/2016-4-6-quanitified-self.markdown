---
layout: post
title:  Quantified Self
summary: An approach to measuring my throughput as a software developer
date:   2016-4-6-18:36:00
categories: development
---

As a software developer, I am at a good place.  I've been at this for about 20 years and I have enough mental capacity to produce complicated and meaningful systems.  I've learned a lot about many things generally and I am proficient or expert in the skills I use day to day.  The challenge that nags at me is that I don't want to waste this opportunity.

**The question I'm asking is how much am I producing and can I increase it?**  This is a difficult question and these are my notes about how I'm thinking about it.

> Programmer (noun): An organism that converts caffeine or alcohol into code.
>
> [Standard Definition](http://uncyclopedia.wikia.com/wiki/Programmer)

# What Good Am I?

I generally produce code, as well as documentation, data analysis, training and a few other things that are economically valuable.  As I think about the effort it takes to work on each technology, I think I've come up with a few factors that can give me a reasonable sense of what I'm producing.

### Complexity

**Whatever I'm using or writing, how complex is it?**

On a log10 scale, about how many features are available to me?  A gist with a few methods in it is about a 1.  It has at least one useful feature, but not quite 10.  Some libraries may be at about a 2, more than 10 features but less than 100.  Rails is about a 5.  All of the web technologies, testing, ORM features, deployment and related features add up to more than 1,000 items but fewer than 100,000.

### Similarity

**How familiar is this technology to me?**

Because technologies replace each other, there's usually a lot of shared understanding that doesn't have to be re-learned.  Sinatra and any other Rack-compliant Ruby microframework would probably have about an 80% overlap on features.  So would a lot of the CSS frameworks as well as the JavaScript frameworks.  R and data analysis with Python have about a 50% overlap.  Python and Spark data analysis only about 20%.  Those are my magic numbers: 80%, 50% and 20%.

### Time

**What did I actually do?**

How do I compare a blog article to a pull request?  I don't try to quantify their economic value, but I do try to guess about how many real hours I was able to dedicate on things.  If I put in 6 hours development time, but I also checked email, social media and some funny pictures during those 6 hours, then maybe I count it for 2.  The bottom-line question is how much intellectual throughput am I delivering during my most-productive years of my career.

I've started using [RescueTime](https://www.rescuetime.com) to see how well I'm actually using my time when I'm "working." I'm not sure if this is a great way to move forward or not (yet).

### Criticality

**Am I producing something critically important?**

Finally, there's a measure of how important it is to get something right.  If I'm writing a blog article like this, there really isn't a wrong answer here.  I'm sharing something that's solving a problem for me and may be helpful to you, but you may disagree and that's OK too.  If I'm writing a blog article that's quantifiable, it's a little more important to get it just right.  [Dave Thomas](https://pragdave.me/) told me at Lone Star Ruby Conference that he wrote unit tests for all the code he put in the [Pickaxe Book](https://pragprog.com/book/ruby/programming-ruby).  Each release of Ruby can be tested against the code in the book and then he knows what he needs to update to keep his book accurate.  I use the same logarithmic scale for these designations:

* Trivial (1): It doesn't matter if I'm right, or it's not provable either way
* Good Effort (2): It would be embarrassing if someone found a mistake in my work
* Professional (3): Someone is paying for something that works, it should work to the best of our knowledge when I deliver it
* Critical (4): Really bad things would happen if I got it wrong and I won't sleep at night if I'm unsure of things

All of these numbers are meant to be generic and rough.  If I spend a month on a critical system using a new-to-me technology, that's a whole lot more work than if I were to put a friend's home page together in exchange for lunch.  The way I combine these is to just multiply the numbers out and write them in a notebook.

<img src="http://i.imgur.com/ADphcxT.jpg" height="200px">

If you want, I've also had a good experience with [Ask me Everything](http://www.askmeevery.com/]).  It's a simple way to quantify life.

## Guesstimating a Baseline

I'm impatient.  Instead of counting everything from this point forward, I compare past efforts.  **How well did I develop my skills?**

I use the [Dreyfus model](https://en.wikipedia.org/wiki/Dreyfus_model_of_skill_acquisition) for understanding my skill level.  The levels stretch from a Novice, through Advanced Beginner, Competent, Proficient to Expert.  They are roughly on a base-10 logarithmic scale as well.  That is, it takes about 10x more effort to start changing a basic recipe into something that works for my own needs.  It's about another 10x effort to really see the big picture and 10x effort to work in real proficiency.

<img src="http://i.imgur.com/33CCuMc.png" height="200px"><img src="http://i.imgur.com/iJjpwLo.png" height="200px">


# Where Do I Go From Here?

So, those are my thoughts on how to get a baseline.  It's a complicated and subjective input, but at least it's an input.

As far as experimenting with actually taking advantage of these years, my friend Jeff Potter([@jpotts18](https://twitter.com/jpotts18)) shared this [link](http://www.fastcompany.com/3058441/how-to-be-a-success-at-everything/heres-how-a-month-of-exercise-affected-my-brain) about how 30 days of exercise affected the author's brain.  More specifically, he considered how exercise affected his brain's ability to develop new nerve cells (neurogenesis) which is thought to assist with problem-solving skills, creativity, rehabilitation and reducing stress.  The conversation is around running or jogging, weight training and interval training.  He reported clearheadedness after jogging, exhaustion after weight training and a bad mood after interval training.  This was highly unscientific, but is fraught with ideas for increasing mental output. (He also wrote up how cutting refined sugar affected his brain [here](http://www.fastcompany.com/3050319/lessons-learned/how-giving-up-refined-sugar-changed-my-brain)).

Another thing I'm preparing to do is [tDCS](https://en.wikipedia.org/wiki/Transcranial_direct-current_stimulation) (also [this link](https://www.reddit.com/r/tDCS/wiki/faq)).  The idea is I will experiment with low doses of direct current on my scalp which may polarize neurons and synapses and change excitability in parts of my brain.  There are different protocols or montages for different desired effects, such as addressing numerical skills or pain relief.  There has been some research on this since the 1960s but quite a bit of recent interest, including this [fascinating workup](http://www.radiolab.org/story/9-volt-nirvana/) by Radiolab.  More to come on that if it works well.

Finally, I've created a balanced list of things I want to work on with my spare time.  Without this, I was more prone to getting sucked into social media or mindless online activities during my early-evening hours.  What I did was create a little distribution class that could take a set of things I'd like to work on.  You could use the [code here](https://gist.github.com/davidrichards/60a93af268a6908f29017f283ecacc51) to generate your own list if you'd like.

So, that's a barrel full of thoughts about how I'm measuring progress and seeking to improve it.  If I get any real insight from all of this, I'll be sure to drop a note here.


