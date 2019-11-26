---
layout: post
title:  Few Hop Learning and Modality
summary: Some Deep Learning notes.
date:   2019-11-25-03:18:20
categories: raw
---
## Meta Learning

Artificial Neural Networks are effective when there are large datasets and they can be trained on IID sampling until convergence, but without those two conditions they are prone to over-fitting and catastrophic forgetting. Gradient-based meta-learning successfully extracts a high-level structure of the problem that is stationary. It requires a meta-dataset, a dataset of datasets that can be trained using a few samples without over-fitting. It can also reduce risks of forgetting with continual learning problems.

[Javed, 2019]

### Build

To build a gradient-based meta-learner, we require a meta-objective (a function minimized during meta-training), and meta-parameters (the parameters needed to perform the meta-training.

MAML is an example of this kind of training. In the case of MAML, it learns the initiation of a neural network that performs well with few-shot learning.

Other approaches is to learn an encoder that transforms input data to a vector representation. Meta-learning can also learn the learning rates, an update rule, a causal structure, or the complete learning algorithm. The meta-objective can also be trained to minimize second-order metrics like catastrophic forgetting.

[Javed, 2019]

### MRCL

MRCL is significantly better for incremental learning than MAML. MAML only maximizes generalization and fast adaptation, but MRCL minimizes interference.

Interference, in an incremental learning context, refers to interfering with past memories, forgetting older learning when applying incremental updates.

[Javed, 2019]

## Generalization

Generalizing machine learning methods can be less effective when working beyond the training distribution. A test set that is sampled from the training data often provides the same concepts in both the training and test data.

A more general approach would find patterns and adapt them through transfer learning. In this way, instead of learning from scratch, the algorithm is learning which distributions match and how to adapt them for fine tuning.

[Bengio, 2019]

### Causal Meta Learning

If we can discover causal variables and how they are related to each other, we can more-successfully apply learned distributions to data. We do this by either performing interventions (comparing actual outcomes for each value of the variable), or imagining them (applying a scenario where the value would be different, even if this has not been observed).

At least for high-level variables, we should be able to infer the effect of their different values on the outcome of our models (e.g. raining causes the opening of an umbrella, not the other way around).

[Bengio, 2019]

### Transfer Learning

Machine learning generally makes assumptions about the data distribution. These methods also makes assumptions about how the data changes.

When knowledge about the distribution is represented appropriately, causal changes only affect one or a few ground truth mechanisms.

This is hard to verify directly, but it is the assumption of these methods. Put another way, if we have the right knowledge representation and well-trained models, we can adapt them quickly to new data.

We use a generative process to compose independent mechanisms and very few ground truth mechanisms and parameters are needed to do this. In practice, this means only a few updates and a few examples are required to transfer knowledge from well-trained models to new ones.

[Bengio, 2019]

### Meta Function for Causal Models

By measuring the speed of adoption, we can optimize how knowledge is represented, factorized, and structured. The more meta-examples we have, the better our results. This turns the nuisance of changes in distribution caused by non-stationarity, uncontrolled interventions, and similar problems into a training signal. We find better ways to factorize knowledge into components and mechanisms. We create a fast transfer and robust models this way.

[Bengio, 2019]

### Causal Model Approach

The approach to learn this way is to first generate synthetic data, then prove we can learn the direction of causality, and finally obtain a training signal about how to transform raw observed data and map it to latent variables. Later, more real-world data can be used to generate a more diverse set of distributions.

[Bengio, 2019]

## RNNs

Feed forward networks have an input layer, 1 or more hidden layers, and an output layer. RNNs have an input layer for the first item in a sequence, the second item goes in the first hidden layer multiplied against the input layer. The second in a sequence is multiplied against the first in the sequence, and so on. The output layer demonstrates the desired output, then back propagation adjusts the weights. This is one way to create sequential memory in a neural network.

[Nguyen, 2018]

### LSTMs and GRUs

The problem with RNNs is the early layers are diminished through the multiplication. A small adjustment on one layer means even smaller weights on the next layer. To get around this, LSTMs and GRUs use tensor operations to add and subtract values to the layers, effectively creating long-term memory.

[Nguyen, 2018]

### Tradeoff

The tradeoff between RNNs and LSTMs or GRUs is RNNs are faster but lose the input from their earlier values while the LSTMs and GRUs are more capable of using the full sequence at the cost of longer training times.

[Nguyen, 2018]

## Modality

Modality refers to the way humans experience reality, such as hearing sounds or feeling texture. With learning models, this often means combining language, visual, and vocal signals in the same model. This area of research has a lot of potential, but has five main challenges: representation, translation, alignment, fusion, and co-learning.

[Baltrušaitis, 2017]

### Representation

Representation is a problem of how to represent and summarize the data that uses the complements and redundancies of the modalities. An example is language is often symbolic while audio and visual data is represented as signals.

[Baltrušaitis, 2017]

### Translation

Translation is the problem with open-ended or subjective relationships between the types of data. There may be many appropriate ways to describe an image and no canonical solution exists.

[Baltrušaitis, 2017]

### Alignment

Alignment problems occur when the signal from one dataset must be matched with that of another. There can be long-range and ambiguous dependencies between these two datasets.

[Baltrušaitis, 2017]

### Fusion

Fusion involves balancing the predictive power of the different modalities: how much noise, is there, what is the predictive power of this information, and is there missing data in one or more modalities?

[Baltrušaitis, 2017]

### Co-Training

Co-training is an effort to transfer knowledge from one modality to another. We see this with co-training, conceptual grounding, and zero-shot learning algorithms. This becomes more important when one modality has limited resources.

[Baltrušaitis, 2017]


## References:

Bengio, Y., Deleu, T., Rahaman, N., Ke, R., Lachapelle, S., Bilaniuk, O., … Pal, C. (2019). A Meta-Transfer Objective for Learning to Disentangle Causal Mechanisms. ArXiv:1901.10912 [Cs, Stat]. Retrieved from http://arxiv.org/abs/1901.10912

Baltrušaitis, T., Ahuja, C., & Morency, L.-P. (2017). Multimodal Machine Learning: A Survey and Taxonomy. ArXiv:1705.09406 [Cs]. Retrieved from http://arxiv.org/abs/1705.09406

Javed, K., Yao, H., & White, M. (2019). Is Fast Adaptation All You Need? ArXiv:1910.01705 [Cs, Stat]. Retrieved from http://arxiv.org/abs/1910.01705

Nguyen, M. (2019, July 10). Illustrated Guide to Recurrent Neural Networks. Retrieved November 25, 2019, from Medium website: https://towardsdatascience.com/illustrated-guide-to-recurrent-neural-networks-79e5eb8049c9



