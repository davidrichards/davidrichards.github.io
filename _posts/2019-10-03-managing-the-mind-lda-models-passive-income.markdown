---
layout: post
title:  Managing the Mind, LDA Models, Passive Income
summary: Some work from Zat Rana, a passive income entrepreneur, and a data scientist.
date:   2019-10-03-04:41:24
categories: raw
---
# Identity and Existence Depend On Making Sense

With the internet, we have changed things about our identity and existence, specifically we translate ourselves and project it into a global network. This is the way it's always been done, but with our families, communities, corporations, or nations this was done at a relatively glacial pace. With global reach rather than just physical bubbles that surround us, we see the best and worst of humanity. And now we must make sense of more information than we ever did before.

[Rana, 2019]

# Address Conditioning

Before, even as recently as the mid-20th century, our sense of self came from local cultures, popular media, education, and life experiences. Now, without a coherent whole, but with access to humanity's knowledge, we can have great power but too much information that overwhelms us.

Carl Jung said, "The pendulum of the mind oscillates between sense and nonsense, not between right and wrong. The numinosum is dangerous because it lures men to extremes, so that a modest truth is regarded as truth and a minor mistake is equated with fatal error."

Since the nature of our minds isn't necessarily rational, we don't have filters that are objectively useful—right or wrong, say. Instead, we have filters that cohere to our state of mind, or sense of self, and we seek to maintain sanity in a more-complicated world than we can comprehend.

With more time and less information, most people could make sense of their world. Parents, teachers, friends could condition us to cope. If that didn't work, we could eventually reject the incoherent parts of this conditioning and restore short-term sanity.

[Rana, 2019]

# Address Shortcuts

A lot of what we face are not just more information in a larger network, but also hidden algorithms manipulated by the loudest rather than the best fit for our lives. When we can't rationally make sense of our world, we take shortcuts--evident in our current state of rampant and bling tribalism found on most social media networks. Those that don't take these shortcuts are marginalized in their confusion.

[Rana, 2019]

# Strategy for Winning

Until the internet can make more sense to us, our most important skill must be to create a sense-making apparatus in our minds. We must create our own information filters. 

We must see the whole network, not just our own node in it. We cannot assume the information presented to us was filtered as right or wrong, just because we belong to a tribe that gave us that information, even if it makes us feel emotionally secure.

Do the work. Which information must be consumed, and which must not? This, as a conscious decision, beyond personal bias, from diverse perspectives.

Ken Wilber asserts that everyone has some important piece of the truth. For example, a racist may make false language claims with true emotional experience. Even as misguided and detrimental as their words and subsequent actions may be, even as uncomfortable as this perspective makes us, there are things that are important to understand even there. 

We must step away from it all and think about what is consumed and how it all connects. We cannot close the gap between what makes sense and what is right without directly addressing the whole network and then detaching from the network to think about what was observed.

If we don't use our tools effectively, they will use us.

[Rana, 2019]

# Passive Income

A lot of people seek passive income from their startups. Rich Dad Poor Dad by Robert Kiyosaki or The 4-Hour Workweek by Tim Ferriss convinces us it's possible.

In Holstein's experience, it's not quite the way it works. Getting the ball rolling takes a lot of energy, but if you can get momentum, the ball will roll faster and you can let it go. It will keep going for at least a while without too much effort on our parts.

We still need to pay attention to the business to keep it moving. We have to oversee the people we are paying to make sure they are doing what they are paid to do. We can reduce the amount of labor at each step, but there's still labor.

[Holstein, 2019]

# Better than a Job

Even with ongoing effort required, passive income is better than the alternative. If passive income works like a weighted ball, traditional employment works like a weighted cube. We can't build momentum with a weighted cube. (We can earn more as we progress in our careers, but we have to show up to work still.)

[Holstein, 2019]

# Holstein's Case

With Holstein's business selling therapy apps for autistic children, some weeks she would work four hours, and some weeks required 40. The difference was she could choose when to put in 40 hours.

There was always marketing tasks, awareness of the competition, awareness of the industry, and whether changes in HIPAA legislation affected her business. In any industry, there are some day-to-day annoyances.

[Holstein, 2019]

# The Path Forward

Once you accept that the price of your dream is hard work, you can create what you're willing to work at. Happiness and purpose isn't seeking pleasure, but meaningful work. Self-actualization involves seeking challenges and conquering them. There's a limit to how much value we get from doing nothing. A month of no responsibility gets boring.

[Holstein, 2019]

# Currently Popular Magazines

According to Agility PR Solutions, whatever credibility they have, the current most-circulated magazines in the US start with AARP Magazine and AARP Bulletin, followed by Better Homes and Gardens, Game Informer Magazine, Good Housekeeping, Family Circle, People Magazine, Woman's Day, National Geographic, and Time.

If I relied on what's at the checkout stand at the grocery store, I would have come to other conclusions. This is more insight into a demographic preference.

[Agility PR Solutions, 2019]

# Basic LDA Tutorial

Topic modeling is an NLP task for creating topics from statistical modeling. Latent Dirichlet Allocation, or LDA, is one approach to classify text in a document to a topic. It provides both a topic per document model and a words per topic model. These models use Dirichlet distributions.

A Dirichlet distribution is a generalization of the beta distribution, often used as a prior distribution whose conjugate is either a categorical distribution or a multinomial distribution. In other words, a topic per document or words per topic model follow this structure. (Wikipedia, 2019)

I chose this tutorial because I wanted to find a simple recipe for LDA before applying LDA to vectors, and working through more advanced approached to topic modeling. This is a recipe tutorial for that purpose. Finishing the tutorial, I can see where the other approaches are more informative and useful. This is a good start to my work.

[Li, 2018]



# Code Organization

By using a Kaggle dataset, Li was able to take over a million headlines from over 15 years of news to train her model. Pandas can be used to load the data. nltk provides the stemming. gensim provides the preprocessing pipeline and a bag of words implementation. Once we have a bag of words corpus, we can use gensim again to provide a tf-idf model of the words.

[Li, 2018]

# LDA Model

LDA is constructed with the number of topics, number of passes, and number of workers as hyper parameters. gensim provides this tool as well. We can run this directly on the bag of words or on the tf-idf corpus. To evaluate the topics, we can apply unseen documents to our LDA and determine if the topic assignments make sense manually.

[Li, 2018]

## References:

Agility PR Solutions. (2019, June 12). Top 10 U.S. Magazines by Circulation. Retrieved October 3, 2019, from Agility PR Solutions website: https://www.agilitypr.com/resources/top-media-outlets/top-10-american-magazines/

Holstein, M. (2019, September 28). There Is No Such Thing As Passive Income. Retrieved October 3, 2019, from Medium website: https://entrepreneurshandbook.co/there-is-no-such-thing-as-passive-income-4b61cda05228

Rana, Z. (2019, September 29). The Most Important Skill in the 21st Century. Retrieved October 3, 2019, from Medium website: https://medium.com/personal-growth/the-most-important-skill-in-the-21st-century-773ef4c5298c
Li, S. (2018, June 1). Topic Modeling and Latent Dirichlet Allocation (LDA) in Python. Retrieved October 3, 2019, from Medium website: https://towardsdatascience.com/topic-modeling-and-latent-dirichlet-allocation-in-python-9bf156893c24

Wikipedia. (2019). Dirichlet distribution. In Wikipedia. Retrieved from https://en.wikipedia.org/w/index.php?title=Dirichlet_distribution&oldid=918785537


