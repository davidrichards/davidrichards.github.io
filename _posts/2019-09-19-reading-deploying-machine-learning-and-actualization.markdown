---
layout: post
title:  Reading, Deploying Machine Learning, and Actualization
summary: Learning to appreciate what we're working with, from reading to data work to ourselves--all of today's reading focus my attention on appreciating what I have and handlig it well.
date:   2019-09-19-23:47:59
categories: raw
---

## Reading

It's easy to overlook the value of books. From a cover and a spine comes a block of paper, and in that paper are keys to the past and future, a voice living longer than the body that created it.

In book form, the thought patterns remain intact, coherent wisdom that may have taken a lifetime to acquire. Aristotle and Shakespeare, for example, offer complex experience in their works.

[Rana, 2019a]

### Intricate Systems

Today we write about 300 pages in a book, about 80,000 words. There are intricate systems of thought from the words themselves, but also the editing and the author's perfectionism involved in the book. It took memory and experience behind every sentence that adds incalculable depth to the work.

[Rana, 2019a]

### Insight into Ourselves

Appreciating what goes into a book, we can appreciate what goes into reading. Rather than just absorbing ideas, we can have a conversation with the author, actively relating to these ideas, gaining perspective.

Our own memories and experiences are emboldened. Things that didn't seem important before offer a more-profound insight after reading others' works.

In a sense, we have mostly incomplete ideas of our own experience, but can enhance insight into ourselves through the experience of reading.

[Rana, 2019a]

## Deploy Machine Learning

Generating predictions with our machine learning projects is only part of the solution. We train these systems offline, make a model available as a service, and then predict values online. By seeing the whole picture, we can think how to make this work available to users. Kaggle and data science bootcamps don't typically cover the whole process.

[Li, 2018]

### REST Microservice

One way to make a model available to users is to support a REST API that takes HTTP requests. Flask is a Python micro framework that focuses only on the work we need to do.

[Li, 2018]

### Naive Bayes Is a Good Beginning Spam Detector

With an example classifying spam from SMS messages, we can use a dataset to build a prediction model. Scikit-learn has a Naive Bayes classifier that can be used for this purpose. We import our data into a dataframe, split it for training and testing, create a model, fit the model, and evaluate the model. The result is a precision, recall, and f1-score for our model.

[Li, 2018]

### Persist the Model in Standard Format

Assuming this model solves the problem well, we want to persist the model so we can use it again without retraining it.

We use joblib.dump from scikit-learn to create a pickle version of our model. If we read the contents of this pickle file and use joblib.load, we will have a running model again. 

This is called persisting the model in standard format.

[Li, 2018]

### Organizing our Project

To organize a micro service, we can organize our core data, an application file, some HTML templates, and a CSS stylesheet.

The application file imports our machine learning dependencies, as well as Flask, render_template, url_for, and request from flask.

The predict route either uses a persisted model in standard format, or creates one with some initial data. It then makes a prediction from the request's data, and renders a result.

[Li, 2018]

## Create Async Tasks

With long-running REST calls, they can time out. With gunicorn and Flask, they recommend spawning 2-4 processes per core. With the server overhead, this can create slow throughput for services that may take a while to return.

An alternative is to create a Celery task queue and process these in an easier-to-scale system. In other words, instead of using a web server to order and manage your work, use Celery and a queue instead.

[Olechwierowicz, 2018]

## Actualization

<img src="https://i.imgur.com/SejlEAl.jpg" width="400" />

We survive or we thrive. To survive defends against what could go wrong, dealing with risk. It is handling the basic needs: food, shelter, and companionship. To thrive seeks to transcend limits, not from fear but desire and yearning.

We are born with different strengths and weaknesses in different environments guided by different people, leaving us at different places in our quest for actualization. But, information has been democratized. All of the answers are already out there and immediately available.

If we take initiative and have the courage to integrate this information, we can make up for the challenges in our lives. We actualize through meditation, see professionals, or talk with friends and family. The only way through is observing our emotional experience, accepting it, and working through it. Abundance is a gift, but we have to learn how to use it. The difference is taking responsibility (I would call it accountability).

[Rana, 2019b]

### Different Types of Selection

Running to survive a lion attack out of fear is survival. Those species that didn't have these fear impulses went extinct. If a species doesn't have the capacity to survive in their environment, the code in their body is not passed to the next generation, and ends with them. This is natural selection.

Even though poverty and difficult living conditions exist for many people, we don't worry about becoming a meal for a lion. Evolution also works with sexual selection, competing for resources and territory. Status and wealth games are an indirect manifestation of sexual selection.

Even though these ideas are more complicated than this, at its core we have a deep desire to survive and reproduce.

[Rana, 2019b]

### From Physical to Emotional

Abraham Maslow said, "A musician must make music, an artist must paint, a poet must write, if he is to be ultimately at peace with himself. What a man can be, he must be."

In order to do this, in order to thrive, an emotional foundation needs to be built. Our lives have changed in the modern world from physical issues moderating survival to emotional issues, moderating sanity.

[Rana, 2019b]

### Interruptions

We have artificial light, sound, and smell interrupting our lives. Media devices fill our lives with information. We get more information than we could absorb over many lifetimes. Some of the information is false and useless.

We don't know how to handle this. When our mind is so often in conflict with itself, we don't have the energy to do what we want to do. We have to train our minds how to deal with this problem.

[Rana, 2019b]

### Differentiation and Integration

Mihaly Csikszentmihalyi interviewed 91 of the world’s most successful people (including 14 Nobel Prize winners) and found that these people were differentiated and integrated--they exposed themselves to an abundance of different things, but also did the work to absorb and make sense of the world as a whole. 

Differentiation discovers individual values and integration is the narrative or meaning that drives those values in daily action.

[Rana, 2019b]

### Integration without Differentiation

When we integrate and don't differentiate, we don't expose ourselves to complexity. We use the ideologies of family, culture, or political affiliation.

It's easier to ignore noise from this perspective, it's the default way to see the world. There is still emotional conflict, living in denial of our own body's experiences.

[Rana, 2019b]

### Differentiation without Integration

When we differentiate without integrating, we expose ourselves to different things around the world, picking values that express us individually, but these things don't come together.

With this problem, the deep connection is available, but it's harder to work out in daily life. Distractions, addictions, and other things get in the way. It's common for people with this problem to have continued issues form their childhood.

[Rana, 2019b]

### Bottlenecks

A bottleneck arises when things come up that keep us from getting what we want. We blame the company we work for, or our credentials. Maybe we reach for productivity tools or change our lifestyle.

This works occasionally, but typically, there are deeper problems. We are living in conflict with ourselves. When we know we're not ready to deal with these bigger issues, we'll make up a false reason why we are experiencing a bottleneck. At some point, we have a harder time making sense of our life.

[Rana, 2019b]

### Cultivate Awareness

To fix this, we cultivate awareness. We become our own therapists. How are we getting in our own way? What advice do we need? The only person who can look after us consistently is ourselves.

[Rana, 2019b]


## References:

Li, S. (2018, December 17). Develop a NLP Model in Python & Deploy It with Flask, Step by Step. Retrieved September 19, 2019, from Medium website: https://towardsdatascience.com/develop-a-nlp-model-in-python-deploy-it-with-flask-step-by-step-744f3bdd7776

Olechwierowicz, G. (2018, June 11). Long computations over REST HTTP in Python. Retrieved September 19, 2019, from Medium website: https://medium.com/@grzegorzolechwierowicz/long-computations-over-rest-http-in-python-4569b1187e80

Rana, Z. (2019, September 15). Reading Is a Conversation. Retrieved September 19, 2019, from Design Luck website: https://designluck.com/reading-is-a-conversation/

Rana, Z. (2019, September 16). Becoming Who You Are: Why Don’t Most People Reach Their Potential? Retrieved September 19, 2019, from Medium website: https://medium.com/personal-growth/becoming-who-you-are-why-dont-most-people-reach-their-potential-df0335ac1655


