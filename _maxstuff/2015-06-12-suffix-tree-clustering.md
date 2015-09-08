---
layout: post
title: "Suffix Tree Clustering"
description: ""
category: "Clu"
tags: [Clustering, IA]
---
{% include JB/setup %}



1. [Web Search Results Clustering](#webclustering)
  + [Main issues](#main)
  + [Clustering algorithms](#algorithms)
2. [Traditional clustering algorithms](#traditional)
3. [Suffix Tree Clustering (STC)](#stc)
  + [Steps](#steps)
  + [Advantages](#advantages)



<!--more-->

###Web Search Results Clustering <a id="webclustering"></a>

Clustering methods are more challenging than classification methods, because they are conducted in a fully unsupervised way. 
Moreover, most traditional clustering algorithms cannot be directly used for search result clustering because of some practical issues.

For example, the algorithm should take the document snippets instead of the whole documents as input, since the downloading of original documents is time-consuming. 
The clustering algorithm should be fast enough for online calculation.

###Main issues <a id="main"></a>

1. Online or offline clustering?
2. What to use as input?
  + Entire Documents
  + Snippets 
  + Structured information
  + Other data
3. How to define similarity?
  - Content (i.e. vector space model)
  - Link analysis
  - Usage statistics
4. How to group similar Documents?
5. How to label the groups?

###Clustering algorithms <a id="algorithms"></a>

1. Distance-based
  + Hierarchical
    1. Agglomerative Hierarchical Clustering (AHC)
  + Flat
    1. K-means
    2. Single-pass
2. Other
  + Suffix Tree clustering  (Grouper)
  + Self-organizing maps
  + LSI (reducing the dimensinality of the vector-space)

###Traditional clustering algorithms <a id="traditional"></a>

Cluster Documents into topically-coherent groups according to content similarity and generate descriptive summaries for clusters.

However, these summaries are often unreadable, which make it difficult for web users to identify relevant clusters.

---

##Suffix Tree Clustering (STC) <a id="stc"></a>

STC not treats documents as a collection of words but as a string of words. On that way thus operates using the proximity information
between words. STC uses suffix tree structure to efficiently identify sets of documents that share common phrases and terms and uses
this information to create clusters and to concisely present their content.

1. linear
2. Incremental
3. Overlapping
4. Can be extended to hierarchical

###Steps <a id="steps"></a>

STC meanly includes four logical steps:

1. Cleaning
  + Stemming
  + Sentence boundary identification
  + Punctuation elimination
2. Suffix tree construction
  + Produces base clusters (internal nodes)
  + Base clusters are scored based on size and phrase score (which depends on length and word)
3. Merging base clusters
  + Highly overlapping clusters are merged

###Advantages <a id="advantages"></a>

STC has linear complexity $O(n)$

Linear complexity puts STC in the top of clustering algorithms. The low complexity return fast search in suffix tree. 
Because of that reason, this algorithm is used in online clustering.

