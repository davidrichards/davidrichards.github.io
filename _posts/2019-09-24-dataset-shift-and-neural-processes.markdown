---
layout: post
title:  Dataset Shift and Neural Processes
summary: Some notes on how to maintain models in production, plus implementing gaussian processes in a neural network.
date:   2019-09-24-06:06:56
categories: raw
---
## Detecting Dataset Shift

Machine learning systems have strong dependencies on their inputs, but often fail silently. There are several methods for detecting dataset shift. Using covariates and label distributions, we can begin to measure whether a system is working well. Of all the approaches, a two-sample testing approach with pre-trained classifiers designed to detect dimensionality reduction works the best.

[Rabanser, 2019]

### Machine Learning Debugging Is Rare

Predictive deep models are used in most advanced human-interacting software systems. These models are designed to drive real-world decisions.

Traditionally, software problems are detected during compilation or at least before deployment. Some problems occur only during runtime, but are caught. The worst kind of problems are never caught and the system is working incorrectly. 

Testing and maintaining machine learning models is especially difficult. Even subtle changes in input data distributions can degrade model performance. This can sometimes be detected with adversarial examples. Most machine learning pipelines do not monitor for distribution shift.

[Rabanser, 2019]

### Problem Space

Effective monitoring will detect distribution shift with as few samples as possible, providing a quantity of the amount of shift, and identifying which samples appear over-represented.

This paper focuses mostly on detecting the shift and identifying which samples have shifted, using two-sample testing. Specifically, this approach compares the source distribution with the target distribution.

This is simple for univariate distributions, but most of our models have high-dimensional inputs.

[Rabanser, 2019]

### Two-Sample Tests Alone Scale Poorly

Kernel-based multivariate two-sample tests scale poorly with dataset size. The statistical power of these models decay badly as well.

[Rabanser, 2019]

### Domain Classifiers

One approach to dataset shift detection could be to train a classifier to distinguish between source and target examples. For every class, hold out some samples and test if the domain is different more than 50% of the time.

This works well on simple models, but has not been worked out well for high-dimensional data until this paper.

This type of model is called a domain classifier. The classifiers trained on the original task are label classifiers.

Domain classifiers reduce the problem to a single dimension. This may take a lot of training data. The domain-classification requires the target data is split in half: half for training the domain model and half for running the two-sample tests.

[Rabanser, 2019]

### Black Box Shift Detection

The black box shift detection or BBSD. Given a label classifier with an confusion matrix that is verifiable on the training data (invertible), then simply detect that the source distribution differs from the target distribution. This is efficient.

[Rabanser, 2019]

### Anomaly Detection

More generally, distribution shift is an anomaly detection problem. Anomaly detection has used density estimation, margin-based work such as one-class SVMs, and tree-based isolation forests. GANs have been used with this task. If the change is abrupt, it can be handled with change point detection on a time series.

[Rabanser, 2019]

### Domain Adaptation

Domain adaptation is another way to address the problem. Domain adaptation assumes the change is either covariate shift or label shift.

[Rabanser, 2019]

### Outlier Detection

Outlier detection, or out-of-distribution sample detection models (OOD) limit the maximum softmax entry allowed in a neural network classifier. This can be adjusted with temperature scaling or adversarial perturbations on the input. Model ensembles can also be used to detect reliability.

[Rabanser, 2019]

### Subjective Yet Sufficient

Reducing the dimensions before using a two-sample test is generally subjective, but the likelihood of pathological cases is small, so finding an effective dimension reduction without defending against worst-case adversarial attacks is reasonable.

[Rabanser, 2019]

### PCA

Principal Component Analysis (PCA) can be used to find and order the components of variability. I.e., the first principal component accounts for most of the variability. MMD or KS tests are appropriate for PCA.

[Rabanser, 2019]

### SRP

Sparse Random Projection (SRP) is less expensive in high dimensions. A tradeoff for a controlled level of accuracy for faster processing is done. MMD or KS tests are appropriate for SRP.

[Rabanser, 2019]

### Autoencoders

Autoencoders (TAE and UAE) are trained and untrained autoencoders that have an encoder to a latent space, and a decoder from the latent space. The latent space has a lower dimension than the input space. MMD or KS tests are appropriate for autoencoders.

[Rabanser, 2019]

### Label Classifiers

Label classifiers, specifically black box shift detection can be used. Similarly, outputs to a deep network multiplied by the source data reduces the dimensionality of that data. This works with both softmax outputs and hard-threshold outputs. Chi-Squared tests are appropriate for label classifiers.

[Rabanser, 2019]

### Domain Classifiers

A domain classifier can be used, explicitly learning the difference between the source and target. This is done by training the classifier with the first half of the data and applying that model to the second half and conducting a significance test to determine if the the classifier's performance is different than random chance. Binomial testing is appropriate for domain classifiers.

[Rabanser, 2019]

### Choosing Statistical Hypothesis Tests

For each dimension reduction technique, a statistical hypothesis test is needed to test the approach. Maximum Mean Discrepancy (MMD) can be used for multi-dimensional representations. A baseline alternative to MMD is the Kolmogorov-Smirnov test (KS). Chi-Squared tests are appropriate for categorical testing. The domain classifier requires binomial testing.

[Rabanser, 2019]

### Representing Changes in the Dataset

Because these methods do not detect outliers, we are not confident which samples are in-distribution or out-of-distribution, but we do know what a typical sample looks like in a shifted distribution. This can be done with a domain classifier, finding the most anomalous samples. The other approaches do not offer this feature.

[Rabanser, 2019]

### Results

Aggregated univariate test outperformed multivariate tests. 

BBSDs performed the best for dimensionality reduction.

Small shifts are not surprisingly harder to detect than large or medium shifts.

The more samples from the target domain, the more confident we are in detecting a dataset shift. Given enough data, even the smallest shifts are detectible, therefore when to take action is an open problem.

These methods are not designed for online data (a continuous stream of data).

The results might be less effective on different problems, this article used image classification to explore their models.

[Rabanser, 2019]

## Neural Processes

Neural networks are parameterized functions that approximate a labeled data with high precision, using gradient descent to learn the function. Gaussian processes are probabilistic models that define a distribution over possible functions and are updated with new data using the rules of probabilistic inference. Gaussian processes are probabilistic, data-efficient, and flexible, but they are computationally intensive. 

Neural processes combine neural networks with gaussian processes to define distributions over functions. They are still computationally efficient during training and evaluation. They can still update their priors from data. These work with regression and optimization problems.

[Garnelo, 2018]

### Deep Learning

There are many ways to approximate functions. In recent years, deep learning models are a popular way to do this. Because they use a large number of training data, neural networks require a lot of work during training. The evaluation and testing are relatively quick, only requiring forward passes. Because neural networks cannot be updated after training, these tools are not optimal for all problems.

[Garnelo, 2018]


## References:

Garnelo, M., Schwarz, J., Rosenbaum, D., Viola, F., Rezende, D. J., Eslami, S. M. A., & Teh, Y. W. (2018). Neural Processes. ArXiv:1807.01622 [Cs, Stat]. Retrieved from http://arxiv.org/abs/1807.01622

Rabanser, S., Günnemann, S., & Lipton, Z. C. (2018). Failing Loudly: An Empirical Study of Methods for Detecting Dataset Shift. ArXiv:1810.11953 [Cs, Stat]. Retrieved from http://arxiv.org/abs/1810.11953


