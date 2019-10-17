---
layout: post
title:  Spell Checking Algorithms
summary: Choosing a spell checking algorithm means learning about how the algorithms work.
date:   2019-10-17-00:00:00
categories: raw
---
## Spell Checking

I'm personally interested in spell checking for the data augmentation as well as the index performance that could be applied to other NLP problems. I have labs that are working out spell checking models and making that effort available for my other models.

[Richards, 10/17/2019]

### Approximate String Search

Approximate string search finds a string in a list of strings, using a metric like Levenshtein, Damerau-Levenshtein, Hamming distance, Jaro-Winkler, or Strike a match.

In order to compare algorithms, Garbe is learning the maximum edit distance available by each algorithm and the time they take using the Damerau-Levensthein string comparison metric. 

Edit distance is a measure of how many operations are required to transform one string into another. In addition, word frequency can be used to sort and filter model suggestions.

[Garbe, 2018a]

### Weighted Edit Distance

An alternative approach to organizing spell checking results uses weighted edit distance. This takes into account key distance on a keyboard layout or similar metrics that reveal a user's intent. This can be implemented in a post-processing step relatively efficiently, because it only works on a very small list of words.

[Garbe, 2018a]

### Spell Checking Goals

Spell checking algorithms use the same goals to reduce their lookup times. They reduce the number of lookups and comparisons. They reduce the number of full edit distance calculations. They reduce the computational complexity of the edit distance calculation. Good solutions to spell checking include Norvig's Spelling Corrector, BK-tree, SymSpell, and LinSpell.

[Garbe, 2018a]

### Choosing a Spell Checking Algorithm

When speed is important, use SymSpell. It is 2-3 orders of magnitude than BK-Tree and 5-6 orders of magnitude faster than Norvig's algorithm.  When memory is important, use LinSpell. It is 10x faster than BK-Tree for the same memory usage. There is no obvious benefit for BK-Tree or Norvig's algorithm.

[Garbe, 2018a]

### Deep Learning and Spell Correction

Deep learning doesn't solve all the problems. Response ~0.1 seconds to spell a short word is really poor. SymSpell can produce corrections at 0.000033 seconds for an edit distance of 2 and 0.00018 seconds for an edit distance of 3 (2 or 3 operations to correct the spelling).

[Garbe, 2018b]

### Adjust SymSpell for Document Correction

To use SymSpell the way deep learning works, with compound splitting and decompounding problems, SymSpell would have to deal with mistakenly inserted space within a correct word, mistakenly omitted space between two correct words, and multiple input terms.

[Garbe, 2018b]

### Whole Document Process

In order to correct spelling on a whole document, individual tokens are generated, combined tokens are checked, sub-terms are generated from tokens to get split tokens, and a dictionary is generated with high correction quality.

A system like this can process about 5,000 words per second on an old single-core laptop.

This could be used for things like query correction, chatbots, post-processing OCR results, and automated proofreading.

[Garbe, 2018b]

### Frequency Dictionary

The frequency dictionary can be built by combining Google Books Ngram data with SCOWL data. SCOWL dictionary is a collection of correct words, and the Google Books Ngrams are what people type, including many misspellings. The frequency dictionary can be used for ranking.

[Garbe, 2018b]

### Improve SymSpell

For further work, we could explore calculating bigram probabilities for any words within a sliding window; using grammar and sentence elements from SyntaxNet; using keyboard proximity, phonetic proximity, and an author's personal vocabulary preferences.

[Garbe, 2018b]


## References:

Garbe, W. (2018, May 5). SymSpell vs. BK-tree: 100x faster fuzzy string search & spell checking. Retrieved October 17, 2019, from Medium website: https://towardsdatascience.com/symspell-vs-bk-tree-100x-faster-fuzzy-string-search-spell-checking-c4f10d80a078

Garbe, W. (2018, May 14). 1000x faster Spelling Correction. Retrieved October 17, 2019, from Medium website: https://towardsdatascience.com/symspellcompound-10ec8f467c9b


