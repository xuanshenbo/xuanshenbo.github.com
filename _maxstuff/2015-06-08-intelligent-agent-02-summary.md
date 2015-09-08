---
layout: post
title: "Intelligent Agent 02 Summary"
description: ""
category: IA
tags: [IA]
---
{% include JB/setup %}

Personalised Search

1. [Personalized Search](#personal)
  + [Query Expansion](#expansion)
  + [Search results filtering](#filtering)
  + [Personal information gathering](#gathering)
    1. [Implicit](#implicit)
    2. [Explicit](#explicit)
  + [Disadvantages](#disadvantages)
2. [Personalized Mobile Search Engine](#mobile)
  + [Client-Server architecture](#architecture)
    1. [Client](#client)
    2. [Server](#server)
  + [Evaluation](#evalution)
3. [PageRank](#pagerank)
  + [Two hypothesis](#hypothesis)
    1. [Quantitative](#quantitative)
    2. [Qualitative](#qualitative)
  + [Initial Stage](#initial)
  + [Update Stage](#update)

<!--more-->


#Intelligent Agent Summary

## Personalized Search <a id="personal"></a>

> Personalized search refers to search experiences that are tailored specifically to an individual's interests 
by incorporating information about the individual beyond specific query provided.

Two general approaches to personalizing search results:

1. Modifying the user's query <a id="expansion"></a>

2. Re-ranking search results <a id="filtering"></a>


Modifying the user's query is also called **query expansion**, 
**query expansion** involves evaluting a user's input (typed into the 
search query area and sometimes other type of data), and expanding the 
search to match additional documents.

Re-ranking search results are also called **Search results filtering/adaptation** 
are based on personal preference, therefore, the data type can be various.

Personal information gathering: <a id="gathering"></a>

1. **Implicit:** to gather data about the user in an implicit, non-invasive way <a id="implicit"></a>
  - click-through data
  - dwell time on page
  - bookmarks & tags

2. **Explicit:** user supplied information <a id="explicit"></a>

Typically use supervised machine learning:

1. Relevant(Binary: Yes or No)

2. Training data:
  + Labeled data
  + Assume clicked docs are relevent

3. Machine learning methods

  + KNN
  + SVM
  + ...


---

###Disadvantages for Personalised Search <a id="disadvantages"></a>

1. The personalised search narrows the search space. Therefore, it might limits the diversity of search result.

2. Privacy issues. Selling users' profile or preference to other companies.

---

###Personalised Mobile Search Engine <a id="mobile"></a>

**Motivation:** It's hard for user to type on Mobile. So the query can
be short. PMSE aims to tailor search result to user's preference.

####Terms

1. **Ontology:** Formal naming, defining and ordering of the entities in a 
given domain, and their interrelationships.

2. **ARR:** Average Relevant Ranking

3. **Entropy:** The uncertainty about the information content

4. **Top-N Precision:** Precision of results, considering only those in the top $N$ entities

---

###Client-Server architecture <a id="architecture"></a>

**Client:** The client is the user's interface, it collects user's data (clickthrough data, ontology data, history) and send them <a id="client"></a>
to the server. It displays the results. (**Naive Bayes & Voting System**)

**Server:** Responsile for forwarding queries to a search engine and extracts the ontological information from the results and stores it. <a id="server"></a>
Then, the ontological information combines with the input vectors in RSVM training to create weighted content. Then, combines with GPS 
data. In the end, use these information to re-rank the results.

**Evaluation of Personalised search system** <a id="evaluation"></a>

Quantitative & Qualitative

User rank all search results $\Rightarrow$ ARR and Top-N precision. There is no qualitative data collected in this experiment.

---

###PageRank

**Terms**

    Forward links: a hyperlink to a page 
    Back links: a hyperlink to the current page

PageRank is based on two hypothesis: <a id="hypothesis"></a>

1. **Quantitative hypothesis:** More back links, more important the page <a id="quantitative"></a>

2. **Qualitative hypothesis:** The link from highly ranked Page has high weight <a id="qualitative"></a>

**Initial Stage:** Built a network based on links. Assign same PageRank value to each page. <a id="initial"></a>

**Update Stage:** Every Page divide its PageRank value equally by the number of its forward links. Therefore, every link has its weight. <a id="update"></a>

$Link weight = \frac{PageRank}{\parallel forward links \parallel}$


Because there are some dangling links which has 0 forward link. The PageRank formula makes use of damping factor $q$. The meaning of 
$q$ is the probability of a user continue browsing from current page. $1 - q$ is the probability that user stop browsing.

PageRank formula: 

$PR = \sum_{n} \text{backlink's weight} \times q \times (1 - q)$



