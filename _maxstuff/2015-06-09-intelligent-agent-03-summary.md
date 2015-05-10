---
layout: post
title: "Intelligent Agent 03 Summary"
description: 
category: "IA"
tags: [IA]
---
{% include JB/setup %}

Information Extraction

1. [Approaches](#approaches)
  + [Manually crafted patterns](#man)
  + [Machine learning Approaches](#mac)
2. [Tasks and subtasks](#tasks)
3. [Evaluation](#eva)

<!--more-->

#Intelligent Agent Summary

> Information Extraction is the task of automatically extracting structured information from a unstructured and semi-structured documents.

##Approaches <a id="approaches"></a>
---

###Manually crafted patterns <a id="man"></a>

1. regular expression

2. Automata

3. NLP-based

**Rule-based/knowledge based**

    [person][office]of[org]
    [org][person][office]
    [org]in[loc]

###Machine learning Approaches <a id="mac"></a>

1. Label documents

2. Learn rules and patterns


###Tasks and subtasks <a id="tasks"></a>

Typical subtasks of IE include:

1. **Named entity recognition:** 

	a Named entity Extraction

	b Coreference Resolution (指代消解)

	c Relationship Extraction

2. **Semi-structured information Extraction:**

	- Table extract: Finding and extracting tables from documents

	- Comment extract

3. **Language and vocabulary analysis**

	- Terminology extraction

##Evaluation <a id="eva"></a>

1. Model solutions as labelled facts

2. Precision: $\frac{correctFoundFacts}{allFoundFacts}$

3. Recall: $\frac{correctFoundFacts}{allFacts}$

4. F-measure

$F-measure = \frac{2 \times precision \times recall}{Precision + Recall}$
