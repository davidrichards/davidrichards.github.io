---
layout: post
title:  Daily Post for September 5, 2019
summary: Rough draft ideas from things researched around September 5, 2019
date:   2019-09-05-08:49:14
categories: raw
---
## Rough Cuts

I've been using the slip box method for a while now, a method started by Niklas Luhmann, a German sociologist. He wrote 58 books and hundreds of articles in 30 years. His approach was simple:

* Read with a pen and paper, taking temporary notes.
* Create a set of bibliographic references.
* Copy temporary notes to a permanent location, with reference annotations.
* Collect notes for project files.

I've created a command line tool that combines IA Writer, Dropbox, and some code I wrote to organize my slips in an easy-enough way to create and organize them. What I haven't been doing is releasing much of what I'm learning. On a typical day, I read at least a few articles and have some worth-it-to-me notes on the things I read. I've decided to release these notes here, to give myself a chance to reflect on what I'm learning.


### Other Approaches

There are many other ways of doing this work, none of them are as satisfactory. For example, creating topics or other static organization creates complexity and requires me to know more than I can know right now.

Getting Things Done is an approach for business and startup culture. It doesn't extend well to research and creative work because it requires that I break down problems to their smallest component. I don't know what the smallest component is, and frankly it's a distraction to try and guess.

### WRITER

Another approache to the slip box method is WRITER, from Shaunta Grimes. WRITER: Writing, Reading, Ideation, Talking, Exercising, and Regrouping.

A good day could look like write fiction, read fiction, make a list of ten ideas, talk to someone I don't live with, exercise, review my day and play for tomorrow. The important thing is it takes a practice to keep the system going. Also, like the slip box method, these are tiny goals. You can skip an hour's worth of work. Everything on the list can be done in ten minutes each.

[external link](https://medium.com/60-months-to-ironman/how-to-be-a-good-writer-with-a-good-life-929508b0bb1e)

### Creative Writing and Slip Box

It's not enough to research. I am a writer. I work with fiction and poetry to learn and express myself. The Slip Box supports creative writing by organizing my research, permanently storing observations, and simplifying tasks.

Ideally, I should be able to even organize stories this way, outlining beats, scenes, sequences, and whole stories. I should be able to track open questions and organize the tools I can setup before I start to write.

### Data Work and Slip Box

I should be able to organize my data work this way too. Many data scientists have a closed approach to their data work, much like stale study guides that suggest starting with a blank sheet of paper, with a hypothesis, or some other interruption to the work.

Smart work takes one step at a time. It is scalable. It takes linear effort to extend it. This type or organization reduces distraction and should work well.

The actual code, the Jupyter notebooks, libraries, models, data, operations, platforms, and other tools I use for my data work can be organized like project files. It is not different than creating permanent slips and writing at most a preliminary draft from my notes.

### Intelligence Can Be Simple

Intelligence is generally awareness and functionality, rather than IQ or some external measure.

That means I can measure whether organizing slips increases awareness. Can I find them? Can I understand them after I forgot the context when they were written? Can I address any part of my  research? Can I keep an open mind? Can I form opinions? Can I ask questions, make arguments, change my opinions?

That also means I can measure whether organizing slips increases functionality. Can I manage more complexity? Can I find what I'm looking for? Do I have serendipitous insight by combining new things? Is it easy to extend old ideas with new information?

# Data Work Is Never Complete

Like with software, a data project is never finished until I shut it down. That doesn't mean I keep working on it, but there can be new arguments, problems with new data, new questions, or new methods to apply to old systems.

Better to find the tools that use old approaches and update them together. Better to consider what could be different without disrupting what's already working. Better to remain calm when difficult choices and presentations are appropriate.

### Context Free Discussion

A context-free discussion of verifiable facts is promising. Consider a slip as an answer in a question and answer NLP task. A lot of great next steps can come from putting my best work out there, making it available for data tools.

Bringing the whole conversation full circle is critical. A lot of data work isn't about creating the most accurate models, but scaling them, collaborating with others, adapting good ideas in the organization, finding latent variables, and training people to continue and improve the effort. All of that can be enhanced by high quality slips.

### Writing Has Many Steps

Writing involves reading, research, thinking, and tinkering. The slip box method splits these steps into different time slots, making it easier to do one thing at a time. Also, it makes it easier to do a step when I'm ready, instead of when I start the first step. 

Any thought of sufficient complexity requires writing—memory and logic are limited resources. By writing, I seek coherence by creating distance between each step.

[Ahrens, 2018]

## Results

With slip box, I keep revisiting areas I couldn't master before, thinks like port forwarding, VPNs, security, and non-FastAI machine learning. These are areas I can't focus my career on, but are an important foundational part of my research. It's worth taking the effort.

The difference is the process. Rough notes begin to make sense. I filter these and convert some of them into permanent notes. I can search, link, order, organize, and refine the permanent notes. This means something is only important if it's important—if it fits into my life, and moves things forward for me.


## Alan Watts

With a Master's Degree in theology and a doctorate in divinity, Watts interpreted Zen Buddhism, as well as Indian and Chinese philosophy. He wrote 20 books and regularly appeared on the television show, Eastern Wisdom and the Modern Life.

[Watts, 1951]

### Insecurity

"For the poets have seen the truth that life, change, movement, and insecurity are so many names for the same thing."

In this way, truth is beauty, movement and rhythm are also the same. When sculpture, architecture, and painting appear to be in motion from their stillness, they become interesting. Change is not only destruction, but a pattern of movement, like a river that must flow out to flow in. Life and death are not in opposition, but the same force from different perspectives. In the human body we see the complexity of circulation, digestion, and respiration—stopping this would kill any of us.

[Watts, 1951]

### Consciousness

Our consciousness, the thing we call "I", is experience, sensation, thought, and feeling in motion. However, we don't often notice because of our perspective. Life is writing its record on us, and we think we're stable all along. If we don't realize this, we try to make sense of the world without taking into account the change, we try and resist it, to fix it.

[Watts, 1951]

### Religion

What most of us think is religion seeks to make sense of life by fixation, eternal life by becoming one with an unchangeable God. We try to understand things by holding them fixed, and experience discord when our ideas don't fit observation.

Thoughts and words are conventions, not to be taken too seriously. Money is a convention, as is gold, but if we have all the gold in the world and can't farm our own crops, we will starve.

[Watts, 1951]

## Accuracy

There are three ways to evaluate the quality of predictions: from an estimator's score, from the cross-validation scoring parameter, and from metrics. Each estimator's score can be handled differently, depending on the algorithm. Cross validation scoring relies on the cross validation algorithm. The metric functions are usually what people refer to when talking about model accuracy. You can also create baseline metrics to compare a model against random predictions.

[Pedregosa, 2011]

#### Accuracy Conventions

All scoring metrics follow the convention that higher values are better than lower values. For metrics that work differently, there is an alternative version that follows this convention, e.g. mean squared error has a negative mean squared error variant that follows this convention.

[Pedregosa, 2011]

### Scikit Learn Accuracy Standards

Scikit Learn offers many scoring functions for each type of predictor [classification, clustering, and regression]. You can also define your own metrics or use multiple metrics. The important thing is to understand and choose informative metrics that improve insight during  model development.

[Pedregosa, 2011]

### Multi-class Metrics

When a metric is primarily designed to handle binary classification, like an F1 score or ROC AUC score, then it can be extended to a multiclass problem by treating is as a set of binary problems--one for each class. The values are then averaged. A macro averaging finds the mean of each class with an equal weight given to each. A weighted averaging score weights each value by the classes' presence in the data. There are several other averaging methods.

[Pedregosa, 2011]

### Human Annotation

Cohen's Kappa can be used when working with human annotators. This accounts for the difference in human agreement.

[Pedregosa, 2011]

### Confusion Matrix

A confusion matrix demonstrates true classifications along the diagonal and the classes confused in other squares. A normalized confusion matrix shows the percentage of accurate vs inaccurate predictions.

[Pedregosa, 2011]

### Precision and Recall

Recall is a predictor's ability to find positive samples. Precision is the predictor's ability to not label positive for negative values. An F-measure [whether F beta or F1] is the weighted harmonic mean of precision recall.

[Pedregosa, 2011]

## References

Ahrens, S. (2017). How to Take Smart Notes: One Simple Technique to Boost Writing, Learning and Thinking for Students, Academics and Nonfiction Book Writers.

Pedregosa, F. [2011]. 3.3. Model evaluation: Quantifying the quality of predictions — scikit-learn 0.21.3 documentation. Retrieved September 5, 2019, from https://scikit-learn.org/stable/modules/model_evaluation.html

Watts, A. [1951]. The wisdom of insecurity. New York: Vintage Books.


