---
layout: post
title: "Information Retrieval 01 Summary"
description: ""
category: IR
tags: [IR]
---
{% include JB/setup %}


<!--more-->


#Information Intelligent Summary

##Basic Concepts:

**Agent:**

An agent is anything that can be viewed as perceiving its environment through sensors and acting upon that environment through effectors.

---

###Information Retrieval

The field of information Retrival deals with the representation, storage, organization of, access of Information items.

---

###Information Agent

**Percepts:** what the agents perceives from its environment

1. User's query

2. Documents

3. Users' feedback

4. Users' actions

**Actions:** what the agent can do in its environment

1. Follow links

2. Retrieve documents

3. Query search engine

4. Expand query

**Goals:** what should the agent try to achieve

Find the exact information, orgainse the Information

**Environment:** what the agent acts and perceives within

1. the Internet

**Some technical drawbacks**

- Different tasks, interfaces, formats are hard to combine

- Domain knowledge does not scale well

---

##Search Engine

    Search a large collection documents to find the ones that satisfied an information need

**What search Engines do:**

1. Indexing(Scape & Store)

2. Document representation

3. Comparison with query

4. Evaluation/feedback

**Indexing:**

1. Mannual indexing: libraries

2. Automatic indexing: indexing program assigns keywords, pharases, other features

**Popular Retrieval models:**

1. Exact Match: Boolean (Yes or No)

2. Best Match: 

	- Vector Space (Cosine Similarity)

	- Citation analysis models

	- Probabilistic models

---

##Vector space model 

Any text object can be represented by a term vector.

Example:

    D1: 0.3, 0.1, 0.4
    D2: 0.8, 0.5, 0.6
    Query: 0.0, 0.2, 0.0

**Cosine Similarity:** Similarity is determined by distance in a vector space.

$Cosine Similarity = \frac{\sum^{n}_{i=1} X_i Y_i}{\sqrt{\sum_{i=1}^{n}X_i^2}\sqrt{\sum_{i=1}^{n}Y_i^2}}$

$Cosine Similarity = \frac{\sum^{n}_{i=1} X_i Y_i}{\sum^{n}_{i=1} X_i}$


---

##Text representation

**Term weights** reflect the estimated importance of each term. The more often a word occurs in a document, the better that term is in describing what the document is about.
On the other hand, terms that appear in many documents in the collection are not very useful for distinguishing documents.


Term weight $W_{ij} = TF \times IDF $

$TF$: Term Frequency

$TF = \frac{termCount}{documentLength}$

$IDF$: Inverse Document Frequency

$IDF = \log (\frac{N}{\mid \{d \in D : t \in d\} \mid})$


Where 

$N:$ total number of documents in the corpus

$\mid \{d \in D : t \in d\} \mid:$ the number of documents where term $t$ appears. If the term is not in the corpus, this will
lead to a division-by-zero. It is therefore common to adjust the donominator to 1 + $\mid \{d \in D : t \in d\} \mid:$

Example:

    D1: cat eat mouse, mouse eat chocolate
    D2: cat eat mouse
    D3: mouse eat chocolate mouse 
    Query: cat 

Term Frequency of D1:

$TF: \frac{1}{6}, \frac{2}{6}, \frac{2}{6}, \frac{1}{6}$

$IDF$ of D1:

$IDF: \log(\frac{4}{4}), \log(\frac{4}{3}), \log(\frac{4}{3}), \log(\frac{4}{2})$

$Weights = IDF \times TF$



