---
layout: post
title:  Pace and Pipeline
summary: Notes on the pace of work and an NLP preprocessing pipeline.
date:   2019-11-14-19:12:34
categories: raw
---
## Productivity through Pace

Listen to yourself. Meditate in the morning to stay focused and stop checking if the competition is catching up. Sleep enough. Master the delicate art of taking care of yourself.

Results come to people who lead boring lives--they know one day they will get there. Find your rhythm and own your system.

[Thompson, 2019]

### Productivity through Pace

Listen to yourself. Meditate in the morning to stay focused and stop checking if the competition is catching up. Sleep enough. Master the delicate art of taking care of yourself.

Results come to people who lead boring lives--they know one day they will get there. Find your rhythm and own your system.

[Thompson, 2019]

### Lumberjack

An allegory for productivity is two lumberjacks went to the woods, the young one hustled and the old one took his time, but cut down more trees. Incredulous, the young one demanded a reason. "Every hour I took a break to rest and sharpen my axe." the older one said.

[Thompson, 2019]

### Choose Your Race

Being young, we feel invincible. What we lack in experience we gain in hard work. In our forties, we can't compete with the young lumberjacks any longer. Remove ourselves from that race and move at our own pace.

[Thompson, 2019]

## Setup an NLP Pipeline

A simple pipeline can be setup that is reusable. It should include the steps above: tokenization, cleaning, normalization, and lemmatization. It should use the sklearn interface standards, with reasonable defaults, documentation, fit and transform methods, and returning the right values. Using all of the cores is important for efficiency. This article provided a feature-rich but slow preprocessing pipeline.

[Balatsko, 2019]

### Tokenization

Tokenization splits text into tokens. This can be words or sentences. Both nltk and spacy have good support for this. The nltk.tokenize module has sent_tokenize and word_tokenize. The en_core_web_sm module creates iterators on processed text. The differences are important between the tools, such as how they punctuation and whitespace. Spacy keeps whitespace in strange ways, but handles URLs, emails, and Twitter-style mentions.

[Balatsko, 2019]

### Cleaning Punctuation

Cleaning data can involve removing punctuation when the punctuation doesn't add value to our NLP task. It's better to remove punctuation after tokenization. It's important to remove punctuation for TF-IDF, Count, and Binary vectorization. However, be careful--even Spacy-based removal can lose important tokens.

[Balatsko, 2019]

### Cleaning Stop Words

Cleaning stop words is another important step for reducing the noise in a dataset. Spacy recognizes 312 stopwords, NLTK 179. Look at samples to see how this cleaning step will perform.

[Balatsko, 2019]

### Normalization

Normalization involves converting dates, numbers, currency,  and percent signs to text. It also means expanding abbreviations and correcting spelling mistakes. The normalize library is pretty good with this.

[Balatsko, 2019]


### Stemming and Lemmatization

Stemming reduces inflection in words to their root forms. Lemmatization reduces the inflected words to root words in the language. A Lemmatized word produces a Lemma (plural of lemma is lemmas or lemmata). Lemmas are the canonical, dictionary, or citation form of words.

[Balatsko, 2019]


## References:

Balatsko, M. (2019, May 21). Text preprocessing steps and universal pipeline. Retrieved November 14, 2019, from Medium website: https://towardsdatascience.com/text-preprocessing-steps-and-universal-pipeline-94233cb6725a

Thompson, M. (2019, November 14). Success Comes to Those Who Own Their Pace. Retrieved November 14, 2019, from Medium website: https://psiloveyou.xyz/success-comes-to-those-who-own-their-pace-e87a9ac6a195


