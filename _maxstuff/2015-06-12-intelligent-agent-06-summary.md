---
layout: post
title: "Intelligent Agent 06 Summary"
description: ""
category: "IA"
tags: [IA]
---
{% include JB/setup %}

1. [Feature Extraction](#extraction)
2. [Feature Selection](#selection)
  - [Filter](#filter)
  - [Wrapper](#wrapper)

<!--more-->

##Feature Extraction <a id="extraction"></a>

> Feature extraction is an attribute reduction process. Unlike feature selection, which ranks the existing attributes according to their
predictive significance, feature extraction actually transforms the attributes. The transformed attributes, or **features**, are linear
combination of the original attributes.

The feature extraction process results in a much smaller and richer set of attributes.

Feature extraction projects a data set with higher dimensionality onto a smaller number of dimensions. 

Feature extraction can be used to extract the themes of a document collection, where documents are represents by a set of key words and 
their frequencies. 

---

##Feature Selection <a id="selection"></a>

Performance of text classification algorithms can be optimized by selecting only a subset of the discriminative terms.

1. **Filter:** <a id="filter"></a>
   Filter model relies on general characteristics of the data to evaluate and select feature subsets without involving any mining 
   algorithm. Filter type methods select variables regardless of the model. It tend to select redundant variables because they does 
   not consider the relationships between variables.

2. **Wrapper:** <a id="wrapper"></a>
   The wrapper model requires one predetermined mining algorithm and uses its performance as the evaluation criterion. It searches 
   for features better suited to the mining algorithm aimming to improve mining performance, but it also tends to be more 
   computationally expensive than the filter model.

###General procedure of feature selection

1. Subset generation, this is a process of heuristic search with each state in the search space specifying a candidate subset for
evaluation

2. Subset evaluation

###Approach
+ Greedy Search
  - Start from empty set or full set and add/delete one at a time
  - Heuristic for adding/deleting


