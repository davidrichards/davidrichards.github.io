---
layout: post
title:  Product Gaps and Matching Qustions
summary: A really good talk about how to deal with user experience gaps and a really good write up on an NLP problem finding duplicates in questions from Quora data.
date:   2019-10-18-07:01:26
categories: raw
---
## Product Customer Gap

As a company grows, the gap between the customer and the company often also grows. People start to do things for reasons other than the customer. This creates a gap between what a product is and why it exists. This makes it difficult to experience the product value.

[Wrobleski, 2019]

### State of the Internet

The world has about 7.7 billion people on it, about 5.6 billion of them are 14 years old or older. 5 billion people are mobile subscribers to the Internet. About 4 billion active smart phones are around right now.

When we use the Internet with our smartphones, we typically get a newsletter signup, a cookie compliance form, or a native app interstitial. Why are we doing this?

Given a full-screen interstitial to use the native app, about 9% of the users converted, but almost 70% of the users abandoned their session. By removing this, the 1-day active metric increased by 17% and the native application installation decreased by 2%—which is still a better result. In one study, about 53% of all sites surveyed had native app install ads interrupting the user experience.

[Wrobleski, 2019]

### Evidence from eCommerce Sites

Given the propensity to have goal-blocking behaviors on eCommerce sites, how did this get this way? The sites advertise jobs in user design, but the sites are user hostile. Talking to the user designers, they talk about the other parts of the organization that require these things, the "business" demands it, but these behaviors decrease business goals.

[Wrobleski, 2019]

### Customer Company Gap

The customer-company gap often occurs as a company grows and the functions and concerns on the products explode, creating distance between the decision makers and the customers.

It's like playing telephone, where people whisper a message into their neighbor's ear, only each person is highly incentived to change the message.

We can see this on something like a contact form, where the simplest form is changed when sales wants to generate leads, engineering wants the fields to represent how they are stored in the database, marketing wants demographics and an opt-in for the newsletter, and legal requires a terms of service form.

[Wrobleski, 2019]


### Conway's Law

In 1967, Melvin Conway introduced the concept that organizations produce designs that copy the organization. Everyone ships their org charts in their products.

[Wrobleski, 2019]


### Idea Implementation Gap

When we lose the purpose of our work in the design of it, because, "legal made me do it," or similar reasons, we create a gap in our products. Anything we do for reasons other than the customer increase this gap.

A common way we create an idea implementation gap is through competitive analysis. We look at what everyone else is doing and do what they are doing rather than testing if this practice turns our customers off. Sign up pages turn people off, as do introduction tutorials.

Get people to have the experience and get the value from the product as quickly as possible.

[Wrobleski, 2019]

### A/B Testing

When we test timid things, we get results, but not answers. If all of our small A/B tests were to hold true for customers long term, then we would expect a cumulative gain in user behavior, but we often see a much more gradual gains over time.

A common example is changing a call to action button to orange, which doesn't change the user's experience of value from the site.

It's better to take some risks with an A/B test and ensure there is an easy way to roll it back if things are not going well. Rather than changing colors or sizes, change the checkout flow or onboarding flow. Make a significant difference for the user and measure if that is working.

[Wrobleski, 2019]

### Design Systems

Design systems like components and styles guides are not enough to ensure the user is getting the experience we want for them. A style guide without thinking doesn't give us the answers.

[Wrobleski, 2019]

### Taking a Survey

A common problem we see is asking users to take a survey when they first arrive. What will they be able to say? It's better to ask people these things after the users have had experiences.

[Wrobleski, 2019]

### Consistency

Consistency isn't a good enough reason to do anything. There should be a customer-centric purpose to what we do.

[Wrobleski, 2019]

### First Fandom Gap

The journey between what something is and what it gives me should be direct and reliable. What something is and why it exists should match. This can be the difference between a first-time user and a true fan.

By increasing the likelihood our user will find something interesting to them increases the likelihood they will become a fan.

[Wrobleski, 2019]

### Use Case: Categories

Studies show that adding categories to an eCommerce layout increases the completed orders by 5%. A similar study shows categories increase revenue per customer. Both studies use business value metrics, or they measure how customers actually behave.

By removing the barriers to see the categories, and adding some products in the natural swipe zone, without making people stretch their thumbs to interact with the product, a site can be optimal for selling products.

[Wrobleski, 2019]

### Standards

Many "standards" aren't standard. In India, when Amazon rolled out their mobile app, people thought the search icon was a ping pong paddle.

The floppy disk icon doesn't mean anything directly to many users today.

A short page with a call to action on the top doesn't mean anything if the call to action is visible rather than if it's visible when the user is ready to use it.

If things look foreign, even if they're standard, people ignore it. We are being trained to close all alerts and pop ups before reading them, even if they're useful to us. An integrated feature, something that looks like it belongs in the product, is something people use.

Branding could be handled with size, typography, and color, but we often want something with imagery, something that is a hook. We can do some of that, but why? Balance the value a customer gets from the brand with the internal desires of company decision makers. The bottom line is always whether something is helping the customer.

[Wrobleski, 2019]


### First Experience

The first experience someone has with a product is often very difficult to overcome. In one study, the team realized the customer value was directly related to their mental model around what the product is used for. Once they realized this new goal, everything they tried to change the customer's use of the product were mediocre.

Take care that a user's first experience moves them closer to a valuable experience with the product.

[Wrobleski, 2019]

### Fix the Gaps

Generally, to fix gaps in products, acknowledge that the gaps exist, measure meaningful behavior, and spend time with the customers.

To mind the gap, check if the customer's voice is included in the decision making. Are requirements departmentalized? Do critical customer experiences underperform?

Finding useful metrics means spending time to get them right. Test what behaviors you want to incentivize, and address the tradeoff between long-term user-centric metrics and short-term operational metrics.

Getting closer to the customer means we do it regularly and often, we value qualitative and quantitative information about the customer, and we lean towards measuring customer behavior more than other things.

[Wrobleski, 2019]

### Find Good Metrics

How do you decide what to measure? What behavior do you want? What might you measure? For everything you might measure, what would happen if we measure this in term of what actions we as product owners would take. Rank list the potential metrics from the biggest and clearest measures that impact our goals for our customers. Prefer long-term user behavior over short-term operational behavior. Collect data on a few of the top metrics and see if it leads to the outcomes we proposed. Keep the good metrics. Regularly and visibly track the best metrics.

[Wrobleski, 2019]

## Predicting Duplicates

Quora and Stack Exchange are question-driven knowledge storing platforms. One problem they have is users submitting duplicate questions. By identifying these duplicates, the product can be more valuable because users don't answer the same question multiple times and the discussion can focus on one proper question. Even when using different words, if the meaning is the same, these are duplicates.

[Surabathula, 2019]

### Organizing the Problem

Given a large set of labeled data, marking questions as duplicate or not duplicate, we can use NLP techniques to find the difference in meaning or intent. With these machine learning models, we can predict whether a pair of questions are duplicate.

[Surabathula, 2019]

### Preprocessing

Most NLP tasks require text cleanup, then embeds the text into a vector space. This cleanup can remove elements that don't contribute significantly to the text's meaning—tags, repeating whitespace, and frequently occurring words are examples of elements that can be removed. This can be further-simplified with stemming.

[Surabathula, 2019]

### Character-Level Embedding

Embedding maps words into word vectors, or numbers. These are built with very large data sets like Wikipedia or the Common Crawl. Fastest uses both and converts terms to trigrams (e.g. fishing becomes fishing, fis, ish, shi, hin, and ing).

This is called a character n-gram and is more robust against out of vocabulary or OOV words. Word2vec is not as robust to OOV.

[Surabathula, 2019]

### Word2vec Intersected

Word2vec can be intersected with training data. No words are added, but pre-trained words transfer their weights to our model. This is a form of transfer learning.

[Surabathula, 2019]

### GloVe

GloVe is another embedding model, based on the Common Crawl.  OOV are randomly mapped to one of 50 random vectors. To see how this works, dimension reduction can be applied to the vectors and the words plotted in a 2D space.

[Surabathula, 2019]

### Similarity

Calculating the similarity on pairwise distance and weighing this by TF-IDF compares two words from different questions. There are many distance calculations including Chebeshev, Bray-Curtis, Cosine, Correlation, Canberra, Cityblock, Euclidean, L1, L2, Minkowski, Squared Euclidean, and Housdorff.

TF-IDF increases proportionally with the number of times a term appears and decreases proportionally with the number of questions that use it.

[Surabathula, 2019]

### Levenshtein

Levenshtein distance measures the edit distance between two words. There are several ratios used. Simple ratio is one. The best partial subset of each term is another. Token sort alphabetizes the tokens then applies a simple ratio. Token set ratio finds the intersection of both components and compares them with the remaining components.

[Surabathula, 2019]

### Word Vectors with TF-IDF

Word vectors the are averaged with TF-IDF weights find a weighted centroid for each question.

[Surabathula, 2019]

### Splitting and Folding

For NLP problems, a train-test ratio of 2:1 works well. A train-validation ratio of 4:1 works well. Validation is used during model optimization. Logistic regression and gradient boosted machines can use n-fold cross validation with n of 5 or 10.

[Surabathula, 2019]

### Logistic Regression

Logistic regression uses the logistic function, an s-shaped function, to separate values into a 0 or 1 output. It takes a real input.

Overfitting can be managed with ridge regularization, or L2.

Cross validation is a good way to discover how to tune a logistic regression model. For this model, we learn the regularization factor and the stopping factor. This is done n-times, and the hyper parameters for the best trial (or fold) are used.

[Surabathula, 2019]

### High Precision Requirement

A model with high precision avoids matching questions incorrectly. Accuracy, precision, recall, and area under ROC curve can be used to see how the model performs.

[Surabathula, 2019]

### Gradient Boosted Machines

Gradient Boosted Machines, using XGBoost, creates an ensemble of many decision trees. Overfitting is managed by limiting the tree depth of each tree in the model. Also, L2 regularization of leaf weight is applied.

For this model, the number of boosted trees to fit, the L2 regularization term weights, the maximum trend path, the learning rate, and the minimum loss to make a partition on a leaf must be learned through n-fold cross validation.

[Surabathula, 2019]

### Deep Learning with Attention

A deep learning model can be setup by organizing a deep learning model with attention to predict a class label over pairs of sentences. What this means is the model pays attention to each word in question while encoding every word in the other question.

The encoding is the dot product of the word vectors of the first question with the vectors of the second one.

This takes an embed layer, an encode layer, an attend layer, and a prediction or classification layer. 

Overfitting is addressed with dropout regularization and early stopping. 

The hyperparameters are the dropout regularization rate for each network, the optimization method (Adam, RMSProp, Nadam, SGD), the learning rate for the optimization method, the number of samples or batch size per gradient update, and the number of epochs used.

These parameters can be optimize using tree-structured Parzen, or TPE. This is a type of sequential model-based optimization, or SMBO, which uses historic values to build and evaluate models. In Python, hyperas can be used to provide TPE.

Early stopping is applied as the model begins to overfit.

[Surabathula, 2019]

### Deep Learning with Hierarchical Attention

A deep learning model with hierarchical attention uses this attention to reduce an encoded matrix (or sequence of words) to a vector. It learns context vectors for two attention stages, one for words and another for questions.

The layers of this model are an embed layer, encoded words, word attention, encode questions, question attention, and a prediction or classification layer.

Overfitting is addressed with dropout regularization and early stopping. 

The hyperparameters for this model are the dropout regularization rates for the word encoder and question encoder, the optimization method, the initial learning rate, the learning rate decay, the batch size, and the number of epochs used.

These parameters can be learned with TPE. Early stopping can also be applied when the model begins to overfit.

[Surabathula, 2019]


## References:

surabathula,  siri. (2019, October 9). Identifying Duplicate Questions: A Machine Learning Case Study. Retrieved October 18, 2019, from Medium website: https://medium.springboard.com/identifying-duplicate-questions-a-machine-learning-case-study-37117723844

Wroblewski, L. (2019). Mind the gap, user centered design in large organizations with Luke Wroblewski. Retrieved from https://www.youtube.com/watch?v=mAiNdU1go1A


