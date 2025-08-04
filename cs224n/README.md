#  What do we hope to teach?

1. The foundations of the effective modern methods for deep learning applied to NLP
 - Basics first: word vectors, feed-forword networks, recurrent networks, attention
 - Then key methods used in NLP in 2024: encoder-decoder models, transformers, pretraining, post-training(RLHF), efficient adaptation, interpretability, language model agents, etc.

2. A big picture understanding of human languages and the difficulties in understanding and producing them via computers

3. An understanding of and ability to build systems (in PyTorch) for some of the major problems in NLP:
 - Word meaning, dependency parsing, machine translation, question answering


# Lecture 1: Introduction and Word Vectors

## Word vectors

We will build a dense vector for each word, chosen so that it is similar to vectors of words that appear in similar contexts, measuring similarity as the vector dot (scalar) product

Note: word vectors are also called (word) embeddings or (neural) word representations

They are a distributed representation

## Word2vec: Overview

Word2vec is a framework for learning word vectors(Mikolov et al. 2013)

