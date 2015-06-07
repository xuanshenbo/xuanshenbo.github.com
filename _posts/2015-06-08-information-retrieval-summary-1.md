---
layout: post
title: "Information Retrieval Summary 1"
description: ""
category: 
tags: []
---
{% include JB/setup %}


<!--more-->


#Information Intelligent Summary

##Basic Concepts:

**Agent:**

An agent is anything that can be viewed as perceiving its environment through sensors and acting upon that environment through effectors.

---

####Information Retrieval

    The field of information Retrival deals with the representation, storage, organization of, access of Information items.

#####Information Agent

**Percepts:**

1. User's query

2. Documents

3. Users' feedback

4. Users' actions

**Actions:**

1. Follow links

2. Retrieve documents

3. Query search engine

4. Expand query

**Goals**

Find the exact information, orgainse the Information

**Environment**

1. the Internet

**Some technical drawbacks**

- Different tasks, interfaces, formats are hard to combine

- Domain knowledge does not scale well

---

#####Search Engine

    Search a large collection documents to find the ones that satisfied an information need

What search Engines do:

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

###Text representation

**Term weights** reflect the estimated importance of each term. The more often a word occurs in a document, the better that term is in describing what the document is about.
On the other hand, terms that appear in many documents in the collection are not very useful for distinguishing documents.


Term weight $W_{ij} = TF \times IDF $

$TF$: Term Frequency

$TF = \frac{termCount}{documentLength}$

$IDF$: Inverse Document Frequency

$IDF = \log (\frac{N}{\mid {d \in D : t \in d} \mid})$





