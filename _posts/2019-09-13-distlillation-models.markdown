---
layout: post
title:  Distlillation Models
summary: Focusing NLP models with model distillation, a case outline.
date:   2019-09-13-19:24:38
categories: raw
---
## BERT

BERT is a pre-trained model from Google. There is a bert-as-a-service repository that provides a Flask application and a CLI to interface BERT. This can be setup as a multi-host solution in production or setup locally for development.

[Antyukhov, 2019]

### Admitting to BERT Limitations

Before, NLP models were built either from tokens or word embeddings. Now, most NLP models begin with BERT and fine tune the results for a specific NLP task. These language models were trained on unlabelled texts, so they have been trained with word and sentence-level meanings, co-references, syntaxes, and similar patterns. Still, using these tools, they are slow and resource intensive.

[Piersman, 2019]

### Introducing Model Distillation

Google's BERT, RoBERTa, XLNet, and other language models are doing very well, but they are difficult to move into production because they are very large. Model distillation can be used to train spaCy to perform similarly on sentiment analysis tasks.

[Piersman, 2019]

### Language Model Parameters

The base and multilingual models for BERT have 110 million parameters. BERT-large has 340 million parameters. Facebook's XLM has 665 parameters. OpenAI's GPT-2 has 774 million parameters. Language is complex, and traditional models with fewer parameters won't be able to handle the complexity of language tasks as well.

There are three approaches to reducing parameters: quanitization which reduces precision, pruning removes parts of the networks, and distillation creates a smaller model that mimics the larger one.

[Piersman, 2019]

### A Successful Distillation Project

The research project created models to predict positive and negative product reviews with a distilled model.

They used 6 languages. They mapped two stars or fewer as negative, and others as positive. 

They trained on 1,000 samples, 1,000 for early stopping development, and 1,000 for testing.

They built a baseline using a balanced dataset (50% positive), and random prediction. 

With a spaCy stacked ensemble bag-of-words model, they got 80-85% accuracy for all languages. With BERT, they achieved 85% to 90% for all languages. The BERT models took 700 MB on disk and were significantly slower to infer labels.

[Piersman, 2019]

### Teacher-Student Metaphor

A teacher/student metaphor works to understand a distillation model. The teacher, the BERT model, produced values, and a simpler BiLSTM model is the student.

To get more data, they augmented the data they had. They mask random words, replaced random words with other words that have the same part of speech, they sampled a random n-gram of 1-5 terms, and they sampled random sentences.

The student model is not shown the labels, but the output values, so it can learn the probable best class exactly. Alternatively, the student model can be trained with logits instead of probabilities.

The distilled spaCy model performed better than the original spaCy model, and nearly as well as the BERT model.

[Piersman, 2019]


## References:

Peirsman, Y. (2019, August 27). Distilling BERT models with spaCy. Retrieved September 13, 2019, from Medium website: https://towardsdatascience.com/distilling-bert-models-with-spacy-277c7edc426c


