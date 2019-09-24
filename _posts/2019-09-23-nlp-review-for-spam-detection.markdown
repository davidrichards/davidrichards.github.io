---
layout: post
title:  NLP Review for Spam Detection
summary: A review of NLP tasks useful for review spam detection.
date:   2019-09-23-06:56:19
categories: raw
---
## NLP Method Review for Spam Detection

Spam detection can be used for reviews. Reviews influence people for purchase decisions and other important decisions. Unfortunately, generated online reviews are sometimes used to unfairly profit. Review spam also erodes consumer trust, making it more difficult to conduct business online.

There are untruthful reviews, brand reviews that fail to review the product, and non-reviews that contain unrelated text or advertisements. 

Manually reading reviews is often insufficient for determining untruthful reviews.

[Crawford, 2015]

### Scaling

The volume, velocity, variety, and veracity of comments online require scalable solutions. The number of comments to process for large sites range from the 10s to 100s of millions of comments.

[Crawford, 2015]

### Web Mining

Web mining uses the structure, content, and usage of a post to determine the type of post. Content mining focuses on information and knowledge extraction. An example of this is opinion mining, often sentiment analysis. Review spam detection is also a type of content mining.

[Crawford, 2015]

### State of the Art

The current state of the art of review spam detection is more effective than manual detection, it is still a difficult problem.

There are not enough distinguishing words. Typically, a bag of words approach is used on individual words or a small group of words for features.

Feature engineering is often used to improve review spam detection. Extracting syntactic and lexical features is a common feature engineering approach.

[Crawford, 2015]

### Reviewer Behavior

Modeling reviewer behavior is another approach to finding review spam. If there are multiple user ids for the same author, groups of spammers that have the same behavioral footprints, or relationships between the reviews and their authors, it is easier to find spam.

[Crawford, 2015]

### Curate Review Spam Datasets

Collecting and labeling enough data for these tasks is an important part of a spam detection project. Create artificial review spam datasets if you don't have enough labeled data. Either way, you need a review spam dataset.

[Crawford, 2015]

### Expand the Dataset

Data engineering can expand the dataset. Bag-of-words with POS tags words for review-centric and reviewer-centric models. Most good models use an amalgam of features. LIWC, abnormal behavioral features, and other linguistic features can expand the feature set. Efforts to extract style and syntax patterns work well with review-centric models.

[Crawford, 2015]

### Bag of Words

Bag of words takes n-grams and trains on them. It records the presence of words. Term frequency records the frequency of each term. Linguistic Inquiry and Word Count is building a dictionary specific to the dataset.

[Crawford, 2015]

### LIWC

LIWC are self-references (I, me, my), social words (mate, talk, they, child), positive emotions (love, nice, sweet), negative emotions (hurt, ugly, nasty), cognitive words (cause, know, ought), articles (a, an, the), big words (more than 6 letters). Other LIWC dimensions can be generated.

These dimensions are measured for our data, personal texts, and formal texts.

[Crawford, 2015]

### POS Tagging

Part of Speech tagging identifies the use of the word.

[Crawford, 2015]

### Overview of Features

When available, related features can be included, such as for the review, the reviewer, the maximum number of reviews, the percentage of positive reviews, the review length, the reviewer deviation (spammers' ratings tend to deviate from the average review more than legitimate reviewers), and maximum content similarity (such as cosine similarity, but many metrics are available).

[Crawford, 2015]

### Supervised Learning and Gold Standard Datasets

Supervised learning requires labels. This can include opinion mining, summarizing opinions.

With Jaccard similarity over 90%, overly-similar reviews can be found, using w-shingling.

Also, Symantec Language Models (SLM) can be used to describe the review, reviewer, and product.

Logistic regression model can be setup with AUC evaluating the model strength.

Naive Bayes and Support Vector Machines are also good models for labeled data.

When building these kinds of models, feature selection is part of the model-building process, not only to improve the results, but avoid overfitting the models.

Amazon Mechanical Turk can be used to build labels--people were asked to write fake reviews of positive sentiment for hotels. These were compared with truthful 5-star reviews. This was repeated for negative reviews. This became the gold standard dataset for review spam. Human results were about 61% accurate, compared to machine learning results of 90%.

[Crawford, 2015]

### SAGE

By combining spam reviews from different domains and using Sparse Additive Generative Models, SAGE, a generative Bayesian approach, they could test each feature of the sample data (deceptive vs truthful, positive vs negative, experienced vs non-experiences, hotel vs restaurant vs doctor). LIWC and POS were useful with SAGE models.

[Crawford, 2015]

### Lexical and Syntactic Features

Another approach learns lexical features (character and word features) or syntactic features (writing style at the sentence level with punctuation or the function of words), and using SVM or Naive Bayes.

[Crawford, 2015]

### Imbalanced Class Distribution

Reviews have an imbalanced class distribution: there are relatively few instances of known spam. This means the majority class is often predicted too easily. With basic metrics like duplicate (or near duplicate) reviews, brand reviews, or non-reviews are all considered spam. 

With Random Undersampling and Random Oversampling, we can address the imbalanced class distribution. Naive Bayes and SVM work with these efforts.

[Crawford, 2015]

### Unsupervised Learning

Unsupervised learning works without labels. You can create an approximation method for the degree of untruthfulness in reviews based on the overlap of semantic content using Semantic Language Models. You can also create context-sensitive concept associations to detect similarity of reviews--more similar reviews are more-likely spam. Cosine similarity can be used. SLM is particularly useful for unsupervised models, rather than Naive Bayes or SVM.

[Crawford, 2015]

### Semi-Supervised Learning and Co-Training

Semi-supervised learning uses some labels. Co-training incrementally applies labels to unlabeled data, training 2 classifiers on 2 sets of data. The more-confident samples are added to a training set for the classifier, and the models are retrained. Content, sentiment, product, and metadata features can be used to support these co-training models. Naive Bayes, Logistic Regression, SVM, and 10-fold cross validation were used for treatments when working on co-training models, with Naive Bayes performing the best.

[Crawford, 2015]

### PU-Learning

PU-Learning is another approach to semi-supervised learning. PU-Learning detects negative instances in unlabeled data. All data is trained, and positive results are removed. The process is repeated until a stop criterion. Naive Bayes and SVM work well with this approach. Because one training set is used, it's difficult to compare with co-training, and difficult to measure how these models perform in the real world.

[Crawford, 2015]

### Reviewer Models

Learning models on reviewers is easier than on reviews. With the many new features available with these models, Information Gain can be used to limit features to the top 1-2% of features.

[Crawford, 2015]

### Rules and Rule Groups

Learning rules and rule groups used by reviewers can be done with Class Association Rules (CAR). This process can find unusual patterns used by spam reviewers.

[Crawford, 2015]

### Bursty Activity

There is a bursty nature of spam reviewers. This means certain reviews get sudden attention from many reviewers in a time period To find bursty activity, Kernel Density Estimation (KDE) can be used.

[Crawford, 2015]

### Reviewer Features

Some reviewer features include Ratio of Amazon Verified Purchase, Rating Deviation, Burst Review Ratio, Review Content Similarity, and Reviewer Burstiness.

[Crawford, 2015]

### Problems with Synthetic Datasets

The supervised learning models used from synthetic labels don't transfer well to real-world problems, or at least researchers are skeptical. In some tests, real-world application was significantly lower than with the training sets.

[Crawford, 2015]


## References:

Crawford, M., Khoshgoftaar, T. M., Prusa, J. D., Richter, A. N., & Al Najada, H. (2015). Survey of review spam detection using machine learning techniques. Journal of Big Data, 2(1), 23. https://doi.org/10.1186/s40537-015-0029-9


