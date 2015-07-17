---
layout: post
title: "Explicit semantic analysis"
description: ""
category: "IA"
tags: [IA]
---
{% include JB/setup %}

> Explicit semantic analysis (ESA) is a vectorial representation of text that uses a document corpus as a knowledge base.



In ESA, a word is represented as a column vector in the tf-idf matrix of the text corpus and a document is represented as the 
centroid of the vectors representing its words. Typicall, the text corpus is Wikipedia, though other corpora have been used.

1. Represent texts as weighted mix of predetermined set of natural concepts

2. Natrual concepts: Defined by humans, easily explained

<!--more-->
Wikipedia titles are the source of the concepts.

Utilised machine learning techniques to build a Semantic Interpreter, this maps fragments of text wo wiki concepts (attribute vector 
of words weighted by TF-IDF)

---

Wikipedia is a large and diverse knowledge base where each article can be considered a distinct concepts. In Wikipedia based ESA, a 
concept is generated for each article. Each concept is then represented as a vector of the words which occur in the article, weighted
by their tf-idf score.


Every Wikipedia article represents a **concept**.

![catwiki](http://i.imgur.com/5pwYXbV.jpg?1)

> The **semantics** of a word is the vector of its **associations** with Wikipedia concepts.

![vector](http://i.imgur.com/pqHMvyh.png?1)

The meaning of any given word can then be represented as vector of that word's relatedness, or "association weighting" to the Wikipedia
based concepts.

    "word" <concept1, weight1>, <concept2, weight2>, <concept3, weight3>...
    "Mars" <planet, 0.90>, <Solar system, 0.85>, <jupiter, 0.30>...

---

###Explicit Semantic Analysis Documents

Large documents are represented as a combination of individual word vectors derived from the words within a document.
The resultant document vectors are known as "concept" vectors. 

For example, a concept vector might look like this:

    "Mars" <planet, 0.90>, <Solar system, 0.85>, <jupiter, 0.30>...
    "explorer" <adventurer, 0.90>, <pioneer, 0.85> ...
	...
	...

Graphically, we can represent a concept vector as the centroid of the word vectors it is composed of. The image below illustrates
the centroid of a set of vectors.

![centroid](http://i.imgur.com/Z3hbLfK.png)

So, to compare how similar two phrases are we can create their concept vectors from their constituent word vectors and then
compare the two, again using cosine similarity.

