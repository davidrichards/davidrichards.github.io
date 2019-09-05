---
layout: post
title:  Daily Post for September 4, 2019
summary: Rough draft ideas from things researched around September 4, 2019
date:   2019-09-04-00:00:00
categories: raw
---
# Thinking About Search

So, I've been thinking about ways to approach search with a deep network. Here are a few notes on that.

### Using tf.Estimator

With tf.Estimator, we can build a feature extractor. We define an input function that executes text preprocessing. The output of this function is a dictionary to feed into BERT. By default, tf.Estiator rebuilds and reinitializes the computational graph for each predict call, but we can pass a generator to the function that yields the features we're after.

The model function loads a pbtxt file that was saved from preprocessing and maps the dictionary to the correct input nodes. Think of the feed dictionary as an abbreviated set of features and the input nodes as a longer-version ready for all entries to the model.

(Antyukhov, 2019)

### Configuring the Feature Extractor

For sentence-level tasks, we can pool the input layer, at least as a rule of thumb. Later we might fine tune this. Either way, the BERT service allows us to set parameters rather than change the network configuration in code. Another parameter to consider is the sequence length, the shorter the allowed sequence, the faster the inference. Once complete, expect about 380 MB for the english model, which makes our work portable enough.

(Antyukhov, 2019)

### Nearest Neighbor Search

Using nearest neighbor search, we find the closest point between the query and an article. This means vectorize the features for each sample, vectorize the query, compute the distance between the query and each sample, sort the samples by distance, and retrieve labels for the samples. With TensorFlow or any tensor library, you can do the distance calculations efficiently. This approach works for finding similar items with any vectorizer model.

(Antyukhov, 2019)

### Reduce Dimensions

After generating embeddings on a set of documents, we have a multi-dimensional output. With T-SNE, we can reduce the feature space to three dimensions. These embeddings can be seen in the Embedding Projector.

(Antyukhov, 2019)

### Feature Extraction with BERT

Feature extraction with BERT or other Neural Probabilistic Language Models prepares data for downstream NLP tasks. These are sometimes called Natural Language Understanding modules. One such task is computing similarity between text samples which is used for instance-based learning like K-NN.

(Antyukhov, 2019)

### BERT

BERT is a pre-trained model from Google. There is a bert-as-a-service repository that provides a Flask application and a CLI to interface BERT. This can be setup as a multi-host solution in production or setup locally for development.

[Antyukhov, 2019]

# Thinking About Trump

I'm also thinking too much about Donald Trump and the future of Democracy in America. It's like a moth to a flame—obsessing over things I can't control is creating a real problem for me, but say what you will, I believe in the many of the institutions that have served humanity, including a free and independent press.

## Trump's Attack on Media

Trump has been attacking "Fake News" for years, which is eroding people's beliefs in institutional safety. The media is protected by the Constitution and is vital for the country to be governed effectively. These attacks not only support Trump's political position, but also misrepresent vital information for people's health and safety, such as incorrectly and repeatedly warning Alabama residents of Hurricane Dorian.

(Stelter, 2019)

## References

Antyukhov, D. (2019, July 9). Building a Search Engine with BERT and TensorFlow. Retrieved September 3, 2019, from Medium website: https://towardsdatascience.com/building-a-search-engine-with-bert-and-tensorflow-c6fdc0186c8a

Stelter, B. (2019, September 2). Why Trump’s constant attacks on an independent press are so dangerousâCNN. Retrieved September 3, 2019, from https://www.cnn.com/2019/09/02/media/trump-press-attacks-media/index.html

