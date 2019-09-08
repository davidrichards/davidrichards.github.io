---
layout: post
title:  Daily Post for September 6, 2019
summary: Conversations around poetry, the scikit-learn interface, machine learning, and craft annotation.
date:   2019-09-06-22:20:22
categories: raw
---
## My Life

From Srd:

They asked how's my life,
I stoped breathing for a while
and said in my head,

"This is my life...."

[external link](https://www.instagram.com/p/B1_sosYh-Rg/?utm_source=ig_web_button_share_sheet)

This is exactly what Watts is talking about, with change and perspective, anxiety and flow. Poets get it, how change works, how perspective works.

## Interfaces

Designing any software requires focusing on strong interfaces that are easy to understand and extend. This coincides with pushing details deeper into modules.

## Scikit-Learn Interfaces

Because of scikit-learn's popularity and use for very different types of users in a complex domain, it has a lot to teach us. The focus of the project is to be a library, rather than a domain-specific language, embracing generic interface concerns. The scope of the project includes leaning algorithms, model evaluation, model selection, and preprocessing tasks. The project has stayed focused on the library, avoiding graphical interfaces and command-line interfaces.

[Buitinck, 2013]

### Estimators

Estimators generally implement the fit function to set them up. Other machine learning tasks such as feature extraction are implemented as estimators. Hyper-parameters are named for easier composition and exposed as public attributes. Constructors do not take data and do not perform learning. After training, parameters are exposed as public attributes with a trailing underscore such as coef_ for learned coefficients in a linear model. Fit returns the estimator object it was called on, again for composition.

[Buitinck, 2013]

### Extension

Scikit-learn can be extended by implementing the same interface as core estimators. This means using fit, predict, and similar functions. These tools can be used in pipelines or in grid search. New classes are not tied to scikit-learn, it is a library rather than a framework. Users wanting a banana should not get the gorrila and the entire jungle with it.

[Buitinck, 2013]

### Meta

A meta estimator combines estimators, such as with ensemble learning. In this case, a decision tree can be used for the ensemble model. Multiclass and multilabel classifiers are composed from binary classifiers. This is how logistic regression can be transformed into a multiclass model.

[Buitinck, 2013]

### Basic Data Decision

Datasets are consistent with optimization in mind. For supervised learning, for example, X is represented as a NumPy matrix an y as a vector with each row in a matrix as one sample. For sparse data, SciPy sparse matrices are used. Loading and preprocessing tools can reuse these conventions. Batch processing is the default interface for efficiency reasons, taking a matrix of samples rather than a single sample per call. Even online learning algorithms are designed to take mini-batches rather than single items. Lower-level optimizations can take advantage of these batches.

[Buitinck, 2013]

### Similar Tools

Other tools similar to scikit-learn are Weka and Orange for GUI-driven tools. SofiaML and Vowpal Wabbit are command-line specific. MATLAB and R create interactive environments similar to scikit-learn and Jupyter.Gensim is a Python tool that implements a different interface that works well with bigger data, using iterable and generators.

[Buitinck, 2013]

### Prediction

Prediction is done with the predict function consistently. To quantify the predictions, optional functions like predict_proba and decision_function might be implemented. These are algorithm-specific. A transformer might be added to the model to prepare typical data input for algorithm-specific formats. This uses a fit(model).transform(model) interface, as well as a fit_transform(model) shortcut.

[Buitinck, 2013]

### Dependencies

External dependencies are only Python, NumPy, and SciPy when possible. Cython is used when practical. Visualization uses Matplotlib and Graphviz. When useful, LIBSVM and LIBLINEAR are used.

[Buitinck, 2013]

### Pipeline and FeatureUnion

A pipeline can be constructed using Pipeline and FeatureUnion objects. Pipeline is typically sufficient for most composed models. It works as a fit on the first value, the output is a transform for the next step. Whatever the final step is, the composition becomes, such as a predictor or a transformer. An example of FeatureUnion combines linear PCA with kernel PCA using FeatureUnion, then selecting the k-best features, and using that in a Logistic Regression model using Pipeline.

[Buitinck, 2013]

### Cross Validation

Cross validation and scoring functions can be used to train and test models effectively.

[Buitinck, 2013]

### Model Selection

Model selection finds the hyperparameters that optimize a model for its use. This could be done with GridSearchCV or RandomizedSearchCV. The grid search uses a cartesian product of all hyperparameters and searches them all. Randomized search is a bit smarter and less brute-force.

[Buitinck, 2013]

### Limits and Consistencies

Generally, all objects must be consistent with a limited interface and consistent documentation. Parameters and parameter values must be inspectable. Only learning classes are exposed. Data is represented in NumPy or SciPy data types. Tasks are expressed as sequences. Code reuse is embraced whenever possible. Defaults are designed to create generally good results.

[Buitinck, 2013]

### Estimators and Models

The choice to make estimators also serve as models was designed for usability. It avoids parallel class structures. It makes it easier to deploy a model in a new environment. Models can also be exported into generic formats, such as PMML.

[Buitinck, 2013]

### Quality

Quality is enhanced with unit-test coverage and style consistency. All features must have documentation and examples. Major changes require a code review of two or more developers.

[Buitinck, 2013]

### Python Numerical Computing

Scikit embraces NumPy and SciPy, numerical computing libraries in Python. These packages have been optimized for various architectures and are used by many data-centric libraries. The scikits are domain-specific tools, such as scikit-learn and scikit-image.

[Buitinck, 2013]

### Create Reasonable Tools

Learning to control complexity and usability is the key. I can build libraries, like the FastAI tools, that hide the complexity and make it easier to think about things in terms of how the researchers are improving models. This involves actual design, optimizing for reusability and complexity.

This is the basis of the tools discussed in A Philosophy of Software Design by John Ousterhout.

### Information Hiding

Each module should encapsulate a few pieces of information, design decisions that other modules don't need to use. In fact, it's better that they don't. Once they do, they encode dependencies that make it harder to manage the project. Private variables and methods can be read and create this. Also, using the same design decisions, such as file formats, creates this dependency indirectly.

This can be handled in layers (Richards, 2019). Meaning, if I have two modules that work on the same file format, say, I can encapsulate these with another module that generically works on a problem. The tools in a lower layer are meant to deal with that file format, and tools above the interface are meant to generically solve the problem no matter what type of file or resource is used.

[Ousterhout, 2018]

### Information Leakage

The opposite of information hiding is information leaking, what we call it when the information gets out. It's more important to pay attention to dependencies, rather.

This is a process of design, figuring out what's generally useful, how far we should go to get what we need, understanding how we back into problems when we're not aware.

Ousterhout identifies information leakage as one of the most important red flags in software design.

[Ousterhout, 2018]

### General Purpose Modules

A general purpose approach to organizing software uses the investment mindset, spending a bit more time up front to save time later on. It tries to predict future uses of the software whereas special purpose classes are specific to what can be used and tested immediately. The theory for writing specific code is it is easier to refactor later in an iterative approach.

A somewhat general class tends to create a more cohesive design, that is easier to refactor and easier to understand. It is a way to prepare for refactoring. Put another way, even though we don't know exactly a codebase will need to change, we know that certain kinds of change are more likely than others.

[Ousterhout, 2018]

# Annotating CRAFT

Annotating text can be done in many ways, this effort uses ontologies to annotate biomedical journal articles with ontologies ranging from 1,000 to 1,000,000 terms. They measure accuracy with interannotator agreement measures. This process could be used for annotating any kind of text with concept mentions.

Advanced NLP often depend on gold-standard corpora with effective annotations. Ontologies are one way to represent these annotations in a consistent way. The Colorado Richly Annotated Full-Text corpus (CRAFT) annotates 97 articles with over 750,000 words. They are focusing on word-level annotation, rather than sentence-level or abstract-only annotations. They are using the Open Biomedical Ontologies (OBO). The results have been 90%+ agreement for all annotations process but one, which has over 80% agreement.

[Bada, 2010]

# NLP with Small Corpora

For one text classification problem, the author started with a baseline model using Logistic regression on TF-IDF because he only had a few thousand labeled examples. It didn't work very well. The bag of words representation often needs larger data sets to work.

[Hadar, 2018]

### Deep Learning Typically Uses Larger Datasets

Deep learning has generally worked well with machine translation, question and answering, summarization, and natural language inference, but these systems often have hundreds of thousands or millions of labeled data points.

Larger datasets are useful to avoid over fitting. Because a deep language model has many parameters, they tend to memorize the training set and perform poorly with unseen data.

[Hadar, 2018]

### Regularization

Regularization methods are designed to avoid over fitting. They have a strong theoretical background and are generalized for most machine learning problems. L1 and L2 regularization requires we add weight size to the model's loss function and seek to minimize this loss. Weights that make minor improvements to the model are reduced to zero. L1 regularization uses the sum of weights and L2 regularization uses the sum of square weights.

[Hadar, 2018]

### Dropout

Dropout will reduce random nodes to zero during training with a probability of p. This prevents the network from relying on specific neurons or the interaction of specific neurons. Ideally, only important patterns that generalize well are learned in the network.

[Hadar, 2018]

### Early Stopping

Early stopping monitors when the model begins to overfit, when the error on the validation set begins to increase, then we stop training. With smaller datasets, this can happen after just 5 or 10 epochs.

[Hadar, 2018]

### Monitor Parameter and Layer Counts

With smaller datasets, be careful with the number of layers and neurons on each layer. Convolutional layers have even fewer parameters than fully connected layers, so experiment with the network architecture to detect over fitting problems.

[Hadar, 2018]

### Data Augmentation

Data augmentation creates data from training data by changing it in a way that doesn't change the label. For example, with images, rotating the image, zooming into parts of the image, changing the size or projection of the image can create a much larger training dataset.

With text problems, we can't make random changes to augment the data. We can replace synonyms in sentences. We can translate the text to another language then back to our source language. This can create a transformation like, "I like this movie very much," to, "I really like this movie." This method is called back translation. Documents can be cropped, say 5 consecutive sentences taken at a time. There is a possibility that GANs and generative models can be useful for data augmentation.

[Hadar, 2018]

### Transfer Learning

Transfer learning uses models trained on a large dataset and fitting them to my own problem. This can be used as weight initialization to some of the layers or as a feature extractor.

[Hadar, 2018]

### Embedding Layer

An NLP deep learning architecture often starts with an embedding layer. This is a one-hot encoded words represented in a numerical vector. If we use Word2Vec, FastText, or Glove, we can get these embeddings quickly. Intuitively, this adds context to each word, because the way these words were used or how they've been interchangeable to each other in previous texts are represented in the embeddings.

[Hadar, 2018]

### Reduce Parameters with Sentence-Level Inputs

If we use sentences rather than words for the input of the model, we reduce the model size and the parameter size. We can encode these sentences with Facebook's InferSent or Google's Universal sentence encoder. We can also use skip-thought vectors or language models to encode our sentences. Skip-thought vectors are built from trying to predict the previous and succeeding sentences, grouping similarly-purposed sentences. Language models are built from trying to predict the succeeding words. ULMFiT, Open-AI transformer, and BERT are recent language models that have performed well and are trained on large corpora.

[Hadar, 2018]

### Unsupervised Methods

Autoencoding or masked language models are unsupervised methods that pretrain our models only on the text we have.

The Deepmoji project demonstrates how to do self-supervision, or automated label extraction. They learned to predict emoji and then used that to predict sentiment. Other self-supervised tasks could predict the headline, the publisher, the number of comments, the number of shares, and other measurable labels. One problem with self-supervised models is mapping the pre-trained labels to the labels we're interested in.

In companies, we often train many models on the same dataset. If the source data was already used for another purpose, those models can be used for pre training our data.

[Hadar, 2018]

### Feature Engineering

Deep learning was supposed to kill feature engineering, but with sparse data, we can boost performance with some engineering tasks. For example, we can include the number of comments, the tags, or other features that are already attached to our documents.

A multimodal architecture builds at least two networks, one for text and one for tabular features. We merge their output layers without softmax, and add a few more layers. These can be difficult because the features often overpower the text.

We can use word-level features such as part of speech tagging, semantic role labeling, and entity extraction. We can use one-hot encodings or embeddings of the word features with these features on the input layer. For example, use the output from a sentiment dictionary and add a feature for whether this word is included in the dictionary.

Preprocessing can also boost performance, such as stemming words, replacing specific words with more general ones, or creating an automated summary with something like text rank.

[Hadar, 2018]

## Craft Annotation

Learning to study work I admire, figure out how it works, even parts of it. Articulate what I learn in writing. This is often done in an annotation: written from the writer's perspective in a way that directly serves the development of my own work. For example, pick an element, technique, or device that is essential to the story. How is it unusual or puzzling? Or, take an element, technique, or device in my own work and see how it was implemented in this other work.

[Turchi, 2005]

### Use Experienced Voices

Lecture and craft books can be an inspiration for checking our work. Apply what I'm learning to what I'm writing. For example, you may notice that Updike's A&P is not just set in a grocery story, but in an A&P near the beach from the eyes of a teenaged narrator, and that this is essential to the strength of the story. How does he do it? How is the narrator characterized by these details?

[Turchi, 2005]

### Craft Annotation: Falling Inn Love 8 Sequences

Romantic comedies, cozy murders, and crime procedurals are unabashed rule followers. They are what they are, they are not trying to do anything else. In this way, we can see many of the most predictable story craft ideas worked out, in this case the 8-sequence structure in a 3-Act story where we watch Gabriela and Jake fall in love.

A 3-Act story typically breaks into 25%/50%/25% of the story, which Falling Inn Love does perfectly. The first Act is for exposition: who are these people? The second Act is for rising action: ratchet things up, what will happen now? The third Act resolves the conflict.

#### Act One

The first sequence is the Inciting Incident where we get to know our main character and give them a challenge. In this case, Gabriela's company fails, she breaks up with her boyfriend, and she sees a chance to win an inn in New Zealand. Gabriella is a cute acquaintance to us, nothing rising above stereotypes.

Sequence two is accepting the invitation. In this case Gabriela applies and wins the competition. We get to know her through exposition in her application. Gabriella is braver, naive, but willing to do hard things.

#### Act Two

Sequence three is for building tension. In a romantic comedy, if it hasn't happened yet, it's our meet cute, which is where Gabriela meets Jake. In Act 2, the main character does not have the skill to deal with her antagonism. We see this at least 20 times in 20-second beats (goats and faucets and everything is going wrong here). Gabriella is completely over her head, and everything she experiences reinforces that.

Sequence four is the midpoint, where the climax is mirrored. Gabriella decides to go home and partners with Jake 50/50 to get the Inn fixed and then she'll move back to San Francisco. Gabriella is showing that decisiveness, moving away from coupling with Jake.

Sequence five is where Gabriella and Jake take a picnic, are spending romantic time together, and have a crescendo moment on a beach at sunset. Nothing happens, they are flirting with love. Gabriella is available for love, confident, doing things as a couple rather than as a single.

Sequence six is a fight. They finish the inn, and things are not likely going to go forward for Gabriella and Jake. Gabriella is showing she has character, but it's not working out for her.

#### Act Three

Sequence seven, Gabriella's old boyfriend shows up with a competing buyer for the inn. Will they take the offer? There's a fire, and Jake rushes off to handle the burning of the competing bed and breakfast, one of the people wanting to buy the inn. Gabriella is changing, seeing she has all the options, is moving into her decision by recognizing the people around her.

Sequence eight, we find Gabriella deciding to keep the inn, stay in New Zealand, then check with Jake if that works for him. It's important that the main characters have their own choices, which they do here. Villains don't make decisions, heroes do. They fall in love and things end as expected. Gabriella is transformed by her journey, making her own decisions, the audience is confident in her ability to handle life.

Reading this annotation, it seems trite. Stories are meant to make us feel things, which I barely did in this case—useful for seeing classic story craft in cardboard cutout fashion. What I know I have a hard time with is writing the trite in the first draft, and asking harder questions of my stories in subsequent drafts. I want to rush all of my insight and ideas into the story too quickly, without giving me time to listen to the story and have an experience learning while writing. This story is a strong first draft, produced and released for all it was meant to be, a light comedy for a weekday night at home.

## References

Bada, M., Eckert, M., Palmer, M., & Hunter, L. (2010). An Overview of the CRAFT Concept Annotation Guidelines. Proceedings of the Fourth Linguistic Annotation Workshop, 207–211. Retrieved from https://www.aclweb.org/anthology/W10-1833

Buitinck, L., Louppe, G., Blondel, M., Pedregosa, F., Mueller, A., Grisel, O., … Varoquaux, G. (2013). API design for machine learning software: Experiences from the scikit-learn project. ArXiv:1309.0238 [Cs]. Retrieved from http://arxiv.org/abs/1309.0238

Hadar, Y. (2018, October 25). Lessons Learned from Applying Deep Learning for NLP Without Big Data. Retrieved September 6, 2019, from Medium website: https://towardsdatascience.com/lessons-learned-from-applying-deep-learning-for-nlp-without-big-data-d470db4f27bf

Ousterhout, J. (2018). A Philosophy of Software Design. Retrieved from http://dl.acm.org/citation.cfm?id=3288797

Turchi, P. (2005). Resources for Writers. Retrieved September 6, 2019, from http://www.peterturchi.com/resources-for-writers/
