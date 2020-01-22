---
layout: post
title:  Blackbox Combinatorial Solvers
summary: There are opportunities afoot
date:   2020-01-21-03:18:20
categories: opinion
---

Neural networks are powerful, and they're getting ever more powerful. Reading Vlastelica et al's recent paper, I think something important is happening. This could be a simpler way to solve some problems I've been working on lately.

In recent years, Jeremy Howard and the FastAI team have done a great job implementing papers that extend the state of the art with deep learning. Discriminate Learning Rates, Gradual Unfreezing, and Slanted Triangular Learning Rates create generally effective ways train a network quickly. ULMFiT demonstrated a smarter way to transfer learning with NLP tasks. Many others have implemented attention networks, Transformers, and large language models broke the ceiling on what neural networks can do. (Roberti, 2019)

Vlastelica and his team, however, have come up with something really impressive. They recognize the strength of deep learning for feature extraction, but also admit to the difficulty they have learning combinatorial problems. A neural network can learn any function, discussed by the universal approximation theorem, but not necessarily efficiently. (Vlastelica, 2019)

## Combinatorial Problems

Old-fashioned combinatorial problems learn the structure and sometimes exact solution to problems. These include finding the quickest routes, minimum or maximum cut in a graph, a perfect matching minimum cost, a solution to a traveling salesman problem, matching graphs, and solutions to other problems. (Pogančić, 2020)

Data applications addressing these kinds of problems involve reducing costs, maximizing profits, dispatching service personnel, fixing errors, planning work that isn't going well, and offering decision support.

The good news is combining old solutions with new tools, these kinds of applications become more tractable. The older solutions take structured input, which the neural networks provide, and then offer common sense or optimized tools as part of the backward pass, which are harder for neural networks to learn.

## Demonstrated Advantages

In the paper, the traveling salesman problem was addressed with an MIP solver from Gurobi. A perfect matching problem was learned with a Blossom V algorithm. The shortest path used Djikstra's algorithm. The interesting thing is the inputs for each model were messy. Flags and a set of maps were used for the traveling salesman problem. The MNIST dataset was used to address the perfect matching problem. World of Warcraft maps were used for finding the shortest path.

Real life has messy inputs. An introductory problem with linear programming is a diet model: what to eat to get a nutritious diet for little money? If I was tedious, I could use that kind of model to pick my next meal, but if I was clever I could use a neural network to use a picture of the contents of my fridge instead. Or, I could take an incomplete log of what I've been eating and some information about where I am as input, and incorporate a diet model to come up with what to cook for dinner.

The paper focuses on accuracy and efficiency, but I'm more interested in tractable solutions. Explain how these solutions work, explain how they apply to business problems, explain what data we have, and you've just hinted towards one of these hybrid models.

## References

Pogančić, M. V. (2020, January 17). The Fusion of Deep Learning and Combinatorics. Medium. https://towardsdatascience.com/the-fusion-of-deep-learning-and-combinatorics-4d0112a74fa7

Roberti, M. (2020, January 11). Fastai with 🤗Transformers (BERT, RoBERTa, XLNet, XLM, DistilBERT). Medium. https://towardsdatascience.com/fastai-with-transformers-bert-roberta-xlnet-xlm-distilbert-4f41ee18ecb2

Vlastelica, M., Paulus, A., Musil, V., Martius, G., & Rolínek, M. (2019). Differentiation of Blackbox Combinatorial Solvers. ArXiv:1912.02175 [Cs, Stat]. http://arxiv.org/abs/1912.02175