---
layout: post
title:  Daily Post for September 5, 2019
summary: Rough draft ideas from things researched around September 5, 2019
date:   2019-09-05-23:48:51
categories: raw
---
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

Scikit Learn offers many scoring functions for each type of predictor (classification, clustering, and regression). You can also define your own metrics or use multiple metrics. The important thing is to understand and choose informative metrics that improve insight during  model development.

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

Recall is a predictor's ability to find positive samples. Precision is the predictor's ability to not label positive for negative values. An F-measure (whether F beta or F1) is the weighted harmonic mean of precision recall.

[Pedregosa, 2011]

### References

Pedregosa, F. (2011). 3.3. Model evaluation: Quantifying the quality of predictions — scikit-learn 0.21.3 documentation. Retrieved September 5, 2019, from https://scikit-learn.org/stable/modules/model_evaluation.html

Watts, A. (1951). The wisdom of insecurity. New York: Vintage Books.


