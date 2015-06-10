---
layout: post
title: "Explicit semantic analysis"
description: ""
category: 
tags: []
---
{% include JB/setup %}

> Explicit semantic analysis (ESA) is a vectorial representation of text that uses a document corpus as a knowledge base.

<!--more-->


In ESA, a word is represented as a column vector in the tf-idf matrix of the text corpus and a document is represented as the 
centroid of the vectors representing its words. Typicall, the text corpus is Wikipedia, though other corpora have been used.

1. Represent texts as weighted mix of predetermined set of natural concepts

2. Natrual concepts: Defined by humans, easily explained

Wikipedia titles are the source of the concepts.

Utilised machine learning techniques to build a Semantic Interpreter, this maps fragments of text wo wiki concepts (attribute vector 
of words weighted by TF-IDF)

---

Wikipedia is a large and diverse knowledge base where each article can be considered a distinct concepts. In Wikipedia based ESA, a 
concept is generated for each article. Each concept is then represented as a vector of the words which occur in the article, weighted
by their tf-idf score.

The meaning of any given word can then be represented as vector of that word's relatedness, or "association weighting" to the Wikipedia
based concepts.

    "word" <concept1, weight1>, <concept2, weight2>, <concept3, weight3>...

