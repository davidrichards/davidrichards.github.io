---
layout: post
title:  Intuitive Boosting
summary: Take a minute to understand how boosting algorithms work and things to keep in mind when building models with them.
date:   2016-9-22-13:15:00
categories: development data
---

So, I've been working with some models that use **ensemble methods**. I wanted to take a step back and make sure I have a grasp of what's going on.  This helps me work with tools and use them more correctly.

What are you working on?

I am building some classification models for some financial transactions. I'm using [XGBoost](https://github.com/dmlc/xgboost) to prepare my models and I've been relying heavily on **[Jason Brownlee's good work](http://machinelearningmastery.com/gentle-introduction-xgboost-applied-machine-learning/)**.

### Why ensemble methods?

The idea is that for many types of problems, using a wide variety of learners will help me have a generalized model.  That is, to have a model that's generally useful.

Well that's just a basic idea for all machine learning, isn't it?

Exactly.  Machine learning is a [systematic study of systems and algorithms that improve their knowledge or performance with experience](https://www.amazon.com/Machine-Learning-Science-Algorithms-Sense/dp/1107422221).  Ensemble methods are a type of machine learning that have been [winning competitions over at Kaggle](http://mlwave.com/kaggle-ensembling-guide/).

<img src="http://i.imgur.com/h6D4zet.gif" />

### Why XGBoost in particular, and not just any library?

XGBoost is a focus on distributed ensemble methods.  It was taken on by [Tianqi Chen](https://github.com/tqchen) (from his [experience at the University of Washington](http://homes.cs.washington.edu/~tqchen/)).  He did an incredible job of handling these things, which makes it more practical than a lot of other machine learning approaches. I'd say most of the data analysis tools I've seen are built for data in the small.  XGBoost is about applying these concepts for larger problems. Real data services tend to want to grow up and work well on larger data sets.

So, let's dive into what's going on.

Right, before we do, I'm going to give a shout out to Leslie Valiant.

Who is she?

He.  He's a computer scientist that works at Harvard University. He wrote [Probably Approximately Correct](https://www.amazon.com/Probably-Approximately-Correct-Algorithms-Prospering/dp/0465032710) which gives me a foundation for computational biology. How we can get computers to helps us adapt in a complex world.

Why is this important?

We're going down a road with boosting and ensemble methods. If these directions are weak, [Brownlee](http://machinelearningmastery.com/gentle-introduction-xgboost-applied-machine-learning/) and [Valiant's](https://www.amazon.com/Probably-Approximately-Correct-Algorithms-Prospering/dp/0465032710) works will do a better job than I can do here.  **The most I hope to do here is review a few algorithms and demonstrate how they can be used.**

Right, let's go.

### Ensembles and Boosting

Ensemble methods are built on the premise of **hypothesis boosting**, the idea that weak hypotheses can be made better.  The weak learners handle the difficult observations.

Give me an example of this kind of learner.

A decision tree is this kind of learner. One of the most visually useful sites I've ever seen is found [at R2D3](http://www.r2d3.us/visual-intro-to-machine-learning-part-1/). They talk about how decision trees draw boundaries, find better boundaries, and generally work.

Why not just use a decision tree and be done with it?

No matter how much data I have, I don't have all the data and more is being produced as we speak. I'm always in danger of creating a learner that's good for my data, but not as good for the things I haven't seen yet. The idea is to produce something that's good at all the problems that are similar to the one that started the project.  One approach to making that work is to ask a lot less of each learner, and just have a lot of them.

But you brought this up in the context of hypothesis boosting, you've lost me already.

A learner is really a code form of an hypothesis, "I think that this data leads me to that conclusion."  It's a tool that we expect has some knowledge in it.  A decision tree will have an idea of what the most important feature is in my data, check it, then look for the next and the next.  It works through the tree until it's checked everything it thinks is important. Finally, it gives me an answer at it's bottom or leaf node.  For the [R2D3 example](http://www.r2d3.us/visual-intro-to-machine-learning-part-1/), they're building a learner that tries to predict if the description of a property is in San Francisco or New York.  So that's the answer I get back.  For my transaction models, I'm looking at whether I think something is a food purchase, or a travel-related expense.  Notice these overlap, so it gets interesting.  Whatever I'm doing, I'm hoping that I have enough clues in my data to come to the right conclusions.

### What's Gradient Boosting Generally?

OK, relying on [Brownlee](http://machinelearningmastery.com/gentle-introduction-xgboost-applied-machine-learning/) some more, gradient boosting involves three elements:

* A loss function is optimized
* A weak learner makes predictions
* Weak learners are added to minimize the loss function

#### So, the loss function?

You choose. It must be differentiable.  Regression might use squared error and classification might use [logarithmic loss](https://www.kaggle.com/wiki/LogarithmicLoss).

That makes sense. If I'm trying to draw a regression line, I just want to know how far my prediction is from the actual.  But the log loss is kind of new to me.

The [above link discusses](https://www.kaggle.com/wiki/LogarithmicLoss) it in terms of real code.  I found it useful to look at that:

    import scipy as sp
    def logloss(act, pred):
        epsilon = 1e-15
        pred = sp.maximum(epsilon, pred)
        pred = sp.minimum(1-epsilon, pred)
        ll = sum(act*sp.log(pred) + sp.subtract(1,act)*sp.log(sp.subtract(1,pred)))
        ll = ll * -1.0/len(act)
        return ll

So, using [scipy](http://www.scipy.org/), I define a small number. I make sure that the prediction is no less than this number (that it's not zero or less, really), and that it's not more than almost 1. Then it does the math which always looks less daunting to me in code vs equations, I'm not sure why.

Probably because I can run it myself and stay at it until I have an intuitive grasp of what is happening.

#### Weak Learners

Well, I could use that in any system.  **And weak learners?**

I'll get more into that later, but just know that we don't want a lot from each learner.  With [AdaBoost](http://scikit-learn.org/stable/modules/generated/sklearn.ensemble.AdaBoostClassifier.html), we're talking about decision stumps, or single decision points in each "tree".  With regular boosting, we're talking about short trees.  With Stochastic Gradient Descent, we're going to really embrace ways to make a diverse and useful set of weak learners.

#### Additive Learners

Then we get into this **additive part of boosting**.

This is where we say let's use gradient descent to minimize the loss function.

Now, gradient descent has been around for a while, help me feel comfortable with how it is accomplishing the additive step.

OK, I'll do that by first drawing the whole picture (from Brownlee):

> Trees are added one at a time, and existing trees in the model are not changed. A gradient descent procedure is used to minimize the loss when adding trees. Traditionally, gradient descent is used to minimize a set of parameters, such as the coefficients in a regression equation or weights in a neural network. After calculating error or loss, the weights are updated to minimize that error.
>
> Instead of parameters, we have weak learner sub-models or more specifically decision trees. After calculating the loss, to perform the gradient descent procedure, we must add a tree to the model that reduces the loss (i.e. follow the gradient). We do this by parameterizing the tree, then modify the parameters of the tree and move in the right direction by (reducing the residual loss. Generally this approach is called functional gradient descent or gradient descent with functions.

So, let me break this down:

* I make some trees.
* I use the loss function to compare my predictions with my training data.
* I get a number for that loss function.
* I calculate the loss function with new trees.
* I use the gradient descent algorithm to only add the trees that move me towards a lower loss.

And when do I stop?

When I can't find a tree that reduces the loss any more.

So this is the general boosting mind set?

Yes,

Also, let me take a moment to sing the praises of gradient descent.  This is the bomb when it comes to optimization.  It's very common, it's used in neural networks, deep learning (of course), many other approaches to learning from data.

I found this **[incredible resource that does an intuitive treatment of gradient descent](http://sebastianruder.com/optimizing-gradient-descent/).**

### What about stochastic gradient descent?

Well, we add a few new things:

* Tree constraints
* Shrinkage
* Random sampling
* Penalized learning

#### What tree constraints?

We don't want particularly good trees. We don't want large trees. We don't want too many splits, too many levels, or to show it too many data.

So we simply don't let the tree grow very much?

We don't but when it grows, we let it grow greedily.  Meaning, we're not pruning it back, we're not keeping a global memory of how a particular tree performs with the model at this stage. We just grow some trees, calculate the loss functions, add trees into the model with gradient descent.

I've [read in some Kaggle competitions](https://www.kaggle.com/forums/f/208/getting-started/t/22586/random-forest-understanding) they're running correlation statistics to find different learners to add to the model.  What's that about?

I'm looking for trees that perform well when others won't. By using constrained trees and searching for learners that have minimal use, I'm hoping to learn when they're useful and use them then.  This is a little different from the idea of Stochastic Gradient Descent, though. We grow constrained trees, calculate the loss function, add them when useful.

<img src="http://upload.wikimedia.org/wikipedia/en/7/7e/Person-tree.jpg" width="400" />

#### What about shrinkage?

By adding learners, I contribute to the overall ability to predict an outcome.  If I weight these new learners to be less than 1, I'm in effect slowing down the learning rate. That gives me more learners in my model, and a higher chance of getting a model that's generally useful.

Explain that to me like I don't know what you're talking about.

A tree makes a prediction and the weight of each tree involves how often it is accurate.  If I reduce the weight of the tree some more, well-performing trees have less of an impact. I can choose to multiply the natural weighting of a tree by 10-30%.

What does that give me?

That gives me a slower learning rate, more trees in my ensemble, and a higher likelihood that the combination of different trees is well generalized.

And this is called shrinkage?

In this context, that's what we're talking about.

<img src="http://i.imgur.com/uXzx62w.jpg" />

#### What does random sampling add?

This reduces which data is shown to the trees. It will randomly choose rows or columns before building a tree or randomly choose columns before each split.

This seems to be one of the more powerful ways to get a less-correlated ensemble of learners.

I think so. I mean, with shrinkage alone, we have no guarantee that the later trees will be all that different than the subsequent ones. And with constraints, we just say that the trees aren't very sophisticated. The closest thing we do to exposing our models to the real world during training is the random sampling. That's because we're using our model at a particular point in time or with limited information and finding ways to perform well anyway.

<img src="http://i.imgur.com/VTyYNNG.png" width="400" />

#### Penalized Learning

We're almost there.  What about **penalized learning?**

That's the introduction of different weighting functions from signal processing.  There is a [better discussion of it here](https://www.quora.com/What-is-the-difference-between-L1-and-L2-regularization).  One area where this is especially useful is with sparse feature spaces--when I am missing data points for a lot of the potential features.  The way that is done is we avoid generating high weights for parameters that are sparse.  We also stabilize the estimates that are more-highly correlated. So, we don't trust too much the weights we learn when we don't have a lot of data or when we've had a lot of learners come to the same conclusions from using similar learning techniques.

### Can I just send whatever data I have to an ensemble method?

No, you need numerical inputs for these methods.  You'll use [one hot encoding](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.get_dummies.html), [label encoding](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html), even some [data imputation](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Imputer.html) for missing values.  The trick to all of this is to get something and keep running the model in different ways so you get an intuitive grasp of how each step of data preparation informs your model differently and reacts differently to different learners.

Do I really need to impute data values? I mean, this doesn't require it, does it?

The penalized learning will deal with some of the issues if you don't impute the missing values. That can be a stronger model if your imputed values are going to confuse the model.  Some basic data exploration will also give you an idea of the kinds of decisions your making before you impute values.  For example, if a feature is missing 60% of the time, that's a very different thing than something missing less than 1% of the time.  Also, if you use the scikit-learn [imputer](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.Imputer.html), you're choosing between mean, median, and mode for imputed values. It's not too hard to imagine how these values can be misleading during the training of a model.

### So where do I go from here?

Well, if you just want to get your hands dirty with xgboost, I'd actually use [Brownlee's book](http://machinelearningmastery.com/gentle-introduction-xgboost-applied-machine-learning/) to get some practical examples typed out on your computer.  You'll get more support than the docs generally, and you'll get some assistance on practical things like serializing a model and reusing it later.

If you really want to get into each type of ensemble method, I'd embrace the scikit-learn example pages.  They use generally-available datasets and give you a direct opportunity to learn models and compare their results.  Here is the [AdaBoost example](http://scikit-learn.org/stable/modules/ensemble.html#adaboost).  There are bagging, random forests, totally random forests, gradient tree boosting, and many other examples there.  They also show distinctions between classification and regression, so you should be able to just follow that rabbit hole and have some fun.

Finally, I'm working on an article that shows how to do these concepts with XGBoost.  If you're impatient, you're interested in `colsample_bylevel`, `colsample_bytree`, `learning_rate`, `n_estimators`, `max_depth`, `subsample`, and a few other things that I haven't perfected yet for level 1 and level 2 penalized learning.

