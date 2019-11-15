---
layout: post
title:  Gold Standard Topic Modeling
summary: Some ideas for a full topic modeling solution, without deep learning
date:   2019-11-15-01:39:50
categories: summary
---

# Topic Modeling

Topic modeling can be a basic tool in an NLP toolkit. It can be used directly in application features as well as a feature in other models. Many common preprocessing and evaluation tools are shared with topic models and other NLP tasks.

## Methods

For non-deep learning methods, there seems be three main topic modeling approaches, Latent Dirichlet Allocation (LDA), Non-Negative Matrix Factorization (NMF), and Correlation Explanation (CorEx) (Kessel, 2019).

CorEx uses anchor words to focus the topics, then uses the similarity of the tokens in a document to assign a document to a topic. LDA andNMF take advantage of the sparse relationship between terms, documents, and topics and use the Dirichlet distribution to map these association (Subrahmannian, 2018)(Lyn, 2013). CorEx uses a latent tree approach to associate words and documents to topics (Gallagher, 2017).

## Preprocessing

Documents will need to be tokenized. It may be useful to clean for punctuation and stop words, normalize the tokens, and stem or lemmatize the words. Spelling correction may be a useful normalization step. Named entity recognition may be performed and only noun phrases used in topic modeling as well.

Small documents are harder to model (Subrahmannian, 2018), so data augmentation may be valuable too. Misspelling, synonyms, and hypernyms may be used to generate similar documents.

## Evaluation

Once we have topics, we can evaluate whether this is about the right number of topics with coherence. Topics with high coherence tend to be more human understandable. We also want topics that have a significant number of words. Consider topics that both have a higher coherence and a higher percentage of tokens used. (Subrahmannian, 2018)

Perplexity is an alternate approach to evaluating the number of topics, but it correlates poorly with human understanding. (Subrahmannian, 2018)

Treat the number of topics as a hyper parameter, adding topics while coherence lowers. 

Use relevance to test how well the topic keywords describe the topic. Relevance is the weighted sum of the probability of a word in a given topic and the lift. The lift for a word is the ratio of the probability of the word in the topic and in the corpus. (Subrahmannian, 2018)

## Topic Uses

Topics might be used to group documents directly, making it easier for end users to consume content.

Topics may be treated as a classification and used as a feature directly or treated as a sentence and an embedding generated. Spacy has a simple average of word embeds, but Sent2Vec and SkipThoughts are more sophisticated ways to create embeddings on sentences (Nader, 2019).

## Follow Up

Read at least 3-5 more overview articles. There may be important ideas missing.

Most of the articles I've reviewed so far are sparse in setting up the dataset or evaluating its use. I would like to read more of what Kessler is doing at the Pew Research Center on topic modeling.

Very little discussion is made on the timing and performance of these models in production. Measure how long it takes to prepare, train, and predict using these models. Measure the preprocessing time as well, as that must be applied to documents predicted in production.

Most people use deep learning for topic modeling. Some of this is inherent in the large language models like BERT or Albert, but people also treat topics as a distinct task. Build deep topic models as well as generative models to see how well topics can be used in production.

Using topic modeling in labs is the best way to create a practical tool out of these algorithms and ideas.

In Branch, use the context of events to evaluate topic models on the event prompts. This information can be transferred to document processing tools.

## References:

Gallagher, R. J., Reing, K., Kale, D., & Ver Steeg, G. (2017). Anchored Correlation Explanation: Topic Modeling with Minimal Domain Knowledge. Transactions of the Association for Computational Linguistics, 5, 529–542. https://doi.org/10.1162/tacl_a_00078

Kessel, P. van. (2019, August 1). Overcoming the limitations of topic models with a semi-supervised approach. Retrieved November 14, 2019, from Medium website: https://medium.com/pew-research-center-decoded/overcoming-the-limitations-of-topic-models-with-a-semi-supervised-approach-b947374e0455

Lyu, S., & Wang, X. (2013). On Algorithms for Sparse Multi-factor NMF. 13.

Nader, R. (2019, May 6). Natural Language Processing—Event Extraction. Retrieved November 14, 2019, from Medium website: https://towardsdatascience.com/natural-language-processing-event-extraction-f20d634661d3

Subrahmannian, S. (2018, July 19). Learn to Find Topics in a Text Corpus. Retrieved November 14, 2019, from Medium website: https://medium.com/@soorajsubrahmannian/extracting-hidden-topics-in-a-corpus-55b2214fc17d