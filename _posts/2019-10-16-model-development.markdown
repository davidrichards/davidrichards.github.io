---
layout: post
title:  Model Development
summary: General process for developing a machine learning model.
date:   2019-10-16-00:00:00
categories: raw
---
## Model Development

As an approach to building a model from scratch, this article provides a relatively reliable way to address a problem.

It starts with an adequate definition, stating explicitly the project objectives and outputs. Then, gather data, choose a success metric, and how to evaluate the model. Be sure to compare and contrast this evaluation process against other common approaches.

Take a look at the data and prepare it, specifically addressing the data format, missing values, categorical values, and feature encodings. Split the data correctly.

Choose a learning algorithm, determine what overfitting and underfitting will look like in this context, describing how this algorithm learns, whether regularization is appropriate for this problem.

Build a baseline or benchmark model. Optimize the model with hyperparameter search, data engineering, and other creative approaches to maximizing the algorithm's performance.

[Roman, 2019]

### Problem Definition

During the problem definition, some of the expectations and limitations should be discovered. What is really expected for this effort? Is this tenable? Can we get the outputs from the inputs available? Is there prior work that can give us creative or a more-effective approach to the problem?

[Roman, 2019]

### Collect Data

When collecting the data, identify problems in the data, in the shape of the data, and in gathering the data. (You might be able to build an effective model offline, but working online in production often offers several challenges that should be identified at this stage.)

[Roman, 2019]

### Choose a Metric

"If you can't measure it, you can't improve it." Peter Drucker said.

Is precision, accuracy, or a business metric the best outcome of this work? Regression problems can use mean squared error or related metrics. Classification problems often use metrics related to precision, accuracy, and recall.

[Roman, 2019]

### Evaluation Protocol

Evaluating the model involves a protocol like a hold out validation set, k-fold validation, iterated k-fold validation with shuffling. (Sometimes the data is split into train, test, and validation sets, so that the iteration over the train-test cycle doesn't adjust the model tuning to overfit on the test dataset.)

However you're evaluating the model, ensure datasets are representative of the data. For classification problems, this can be done  with shuffling and checking the whole spectrum of the data is represented in each. With prediction problems, shuffling cannot be done (so a protocol using a windowed progression often works.)

Ensure there are no duplicate data records.

[Roman, 2019]

### Prepare Data

When preparing data, decide and document how you will deal with missing data, such as eliminating samples or features with missing values. You can also impute the missing values with heuristics, pre-built estimators, or use a mean value from the rest of the values. 

Categorical data needs to be adjusted. For ordinal data, integers can preserve the order of the categories. For nominal data, encoding such as one-hot encoding, label encoding (or feature embedding vectors) can be used.

For many algorithms, the numerical values should be scaled. This can be normalized from 0 to 1 or standardized with a mean of 0 and a standard deviation of 1. Feature selection can remove redundant features, avoiding some overfitting problems.

Principal Component Analysis can be used to select features.

[Roman, 2019]

### Over and Underfitting

Before using an algorithm, grasp how it learns. This demonstrates how a model may be overfit or underfit.

If you are dealing with overfitting, you might get more data or regularize your data. Regularization is limiting how much information the model can store. If the model can't just memorize a mapping between inputs and outputs, it will focus on the relevant ones that are more-generally useful.

Another form of regularization is weight regularization, forcing weights to be relatively small.

[Roman, 2019]

### Baseline Models

When developing a benchmark model, we want to measure improvement of our work against something easy or obvious. This might look like a kNN, Naive Bayes, EWMA. The goal is to choose something that takes far less time and compute and predict.

[Roman, 2019]

### Optimize the Model

When we improve our model, we often use cross validation, looking at different approaches to the same problem. The best-performing model can then be optimized by tuning its hyperparameters.

[Roman, 2019]


## References:

Roman, V. (2019, April 2). How To Develop a Machine Learning Model From Scratch. Retrieved October 16, 2019, from Medium website: https://towardsdatascience.com/machine-learning-general-process-8f1b510bd8af


