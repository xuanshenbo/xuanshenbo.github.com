---
layout: post
title: "Intelligent Agent 01 Summary"
description: ""
category: IA
tags: [IA]
---
{% include JB/setup %}


<!--more-->


#Intelligent Agent Summary

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

$Cosine Similarity = \frac{A \cdot B}{\parallel A \parallel \parallel B \parallel}$


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

---

##Evaluation

###Evaluation Criteria

1. **Recall** is the fraction of the documents that are relevant to the query that are successfully retrieved

$Recall = \frac{\mid \{\text{relevant documents}\} \cap \{\text{retrieved documents}\} \mid}{\mid \{\text{relevant documents}\}\mid}$

2. **Precision** is the fraction of retrieved documents that are relevant to the query.

$Precision = \frac{\mid \{\text{relevant documents}\} \cap \{\text{retrieved documents}\} \mid}{\mid \{\text{retrieved documents}\}\mid}$

###How to evaluate two IR systems ?

Traditionally, one uses a "test collection" composed of three entities:

1. a set of queries (or "information needs")
2. a target dataset (where to look for items that will satisfy the information needs)
3. a set of relevant assessments (the items satisfy the information needs)

Based on this test collection one can compare the resuls of a query using two different IR systems.

**Systems effectiveness: evaluation measures**

**Set-based measures:** documents in the ranking are treated as unique and the ordering of result is ignored.

1. Precision

2. Recall 

Precision and Recall hold an approximate inverse relationship. But it is not always the case.

Compared with other measures, Precision is simple to compute because one only considers the set of retrieved documents. However to compute
recall requires comparing the set of retrieved documents with entire collection. Which is impossible in many cases (web search).

In web search, the focus is typicall on obtaining high precision by finding as many relevant documents in the top $n$ results. However,
there are certain domain, the focus is on find all relevant document through an exhaustive-search, alternative recall-oriented 
measures can be employed: $e$ measure and $f$ measure.

**Rank-based measures:** Based on evaluating ranked retrieval results where not only the number of relevant documents, but also
returning relevant documents higher in the ranked lists. A common way to evaluate ranked documents is to compute precision at various
levels of recall.
