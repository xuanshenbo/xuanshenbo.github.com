---
layout: post
title: "Intelligent Agent 04 Summary"
description: ""
category: "IA"
tags: [IA]
---
{% include JB/setup %}

Recommender System

<!--more-->

#Intelligent Agent Summary


##Recommender System
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

###Collaborative filtering

Collaborative filtering methods are based on collecting and analyzing a large amount of information on user's behaviors, activities or preferences and predicting what users will like based 
on their similarity to other users.

Collaborative filtering is based on the assumption that people agree on past will agree in the future.

A key **advantage** of the collaborative filtering methods is that it does not rely on machine analyzable content and therefore it is capable of accurately recommending complex items such as "movie"
without require an "understanding" of the item itself.

Algorithms to measure user similarity or item similarity:

1. KNN

2. Pearson correlation

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


