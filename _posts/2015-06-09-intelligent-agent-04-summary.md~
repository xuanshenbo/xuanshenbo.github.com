---
layout: post
title: "Intelligent Agent 04 Summary"
description: ""
category: "IA"
tags: [IA]
---
{% include JB/setup %}

#Intelligent Agent Summary

Recommender System


1. [Recommender System Overview](#overview)
2. [Collaborative filtering](#collaborative)
  * [Memory-based](#memory)
    1. [User-based](#user)
    2. [Item-based](#item)
  * [Model-based](#model)
3. [Content-based filtering](#content)
		

<!--more-->

---


##Recommender System Overview <a id="overview"></a>
---

Recommender Systems provide a lot of recommendations in one of two ways:

1. **Collaborative filtering:** building a model from a user's past behavior, as well as similar decisions made by other people

2. **content-based filtering:** use a series of discrete characteristics of an item in order to recommend additional items with similar properties.

###An Example

**last.fm** creates a "station" of recommended songs by observing what bands and individual tracks the user has listened to on a regular basis and comparing those
against the listening behavior of ther users. **Collaborative Filtering**

**Pandora** uses the properties of a song or artist (a subset of the 400 attributes) in order to seed a "station" that plays music with similar properties. **Content-based filtering**

###Strengths and weakness

**Last.fm** requires large amount of information on a user in order to make accurate recommendation. Th is an example of **the cold start problem** and it is the common problem in Collaborative filtering.

**Pandora** needs little information to start. But it is far limited in scope (Only recommend similar musics).

---

###Collaborative filtering <a id="collaborative"></a>

Collaborative filtering methods are based on collecting and analyzing a large amount of information on user's behaviors, activities or preferences and predicting what users will like based 
on their similarity to other users.

Collaborative filtering is based on the assumption that people agree on past will agree in the future.

A key **advantage** of the collaborative filtering methods is that it does not rely on machine analyzable content and therefore it is capable of accurately recommending complex items such as "movie"
without require an "understanding" of the item itself.

Algorithms to measure user similarity or item similarity:

1. KNN

2. Pearson correlation

---

###Weakness

---

Collaborative filtering approaches often suffer from three problems:

1. **Cold Start:** These systems often require a large amount of existing data on a user in order to make accurate predications.

2. **Scalability:** In many of the environments in which these systems make recommendations, there are millions of users and products.
Thus, a large number of computation power is often necessary to calculate recommendations.

3. **Sparsity:** The most active user will only rated a small subset of the overall database. When the matrix is sparse, the clustering
algorithms do not work well.


---

###Memory-based <a id="memory"></a>

This approach uses user rating data to compute the similarity between users or items. This was an early approach userd in many commercial
systems. It's effective and easy to implement.

Typical examples of this approach are neighbour-based collaborative filtering and item-based/user-based top-N recommendations.

**User-based algorithms** <a id="user"></a>

The first step of the algorithm is to obtain the user history profile, which can be represented as a ratings matrix, each entry is the
rate of a user given to an item. A ratings matrix consists of a table where each row represents a user, each column represented an item.

The second step is to calculate the similarity between users and find their nearest neighbours. There are many similarity measure methods
such as Pearson correlation.

The last step is to calculate the items rating (Prediction). The rating is computed by a weighted average of 
the ratings by the neighbours.

**Item-based algorithms** <a id="item"></a>

Same matrix with user-based matrix. But the critical step is to compute the similarity between items. And get top-N similar items.
The prediction is then computed by taking a weighted average of the target user's ratings on these similar items.


###Model-based <a id="model"></a>

Models are developed using dataming, machine learning algorithms to find patterns based on training data, such as **Bayesian network, 
clustering, and rule-based approaches**.

---

###Content-based <a id="content"></a>

Content-based filtering methods on a description of the item and a profile of the user's preferences. 
In a content-based Recommender system, keywords are used to describe the items. A user's profile is built to indicate the type of 
item this user likes. These algorithms try to recommend items that one similar to those a user liked in the past.

To create user profile, the system most focus on two types of information:

1. A model of the user's preferences

2. A history of the user's interaction with the Recommender system 

These methods use an item profile (features) characterizing the item within the system. The system creates a 
content-based profile of users based on a weighted vector of item features.

A key issue with content-based filtering is whether the system is able to learn user preferences from user's 
actions regarding one content source and user them across other content type.

---



###Model

When building a model from a user's profile, a distribution is often made between explicit and implicit forms of data collection.

Explicit data:

1. Rate items

2. Compare items

3. Create a like-list

Implicit data:

1. Item viewed.

2. Click through data.

3. ...


