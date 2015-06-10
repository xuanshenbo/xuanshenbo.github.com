---
layout: post
title: "Intelligent Agent 05 Summary"
description: ""
category: IA
tags: [IA]
---
{% include JB/setup %}

Text Representation

<!--more-->

##Bag of words

---

Vector Space model

- Documents are term Vectors
- TF.IDF for term weights
- Cosine similarity

###Disadvantages

1. The ignorance of any relation between words. Learn algorithm could only detect terminology, conceptual patterns (synatatic meaning)
are totally ignored.

2. Dimensionality problem

---

##Other Representation

###N-grams model

> n-grams model is a contiguous sequence of $n$ items from a given sequence of text or speech. An n-grams model is a type of 
probabilistic language model for predicting the next item in such a sequence in the form of a (n - 1) other **Markov Model**

- Bi-grams
- Tri-grams

Two advantages of n-gram models:

1. similarity
2. Scale up efficiently




