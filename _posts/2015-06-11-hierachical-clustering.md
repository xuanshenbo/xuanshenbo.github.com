---
layout: post
title: "Hierachical Clustering"
description: ""
category: "Clu"
tags: [IA, Clustering]
---
{% include JB/setup %}

1. [Top down](#top)
  + [Hierachical K-means](#kmeans)
2. [Bottom up](#bottom)
  + [Agglomerative clustering](#agglomerative)
3. [Distance Metrics](#distance)
  1. [Single links](#single)
  2. [Complete links](#complete)
  3. [Average links](#average)
  4. [Centroids](#centroids)


<!--more-->

We try to separate a set into several subset of the population. One of the problems of 
K-Means and other clustering algorithms is **picking the number of clusters**. You need to
pre-define $K$. Most of algorithms you either specify the number of cluster or some parameters
like a threshold that dictates how many clusters you end up with. We want the algorithm to pick
$K$ automatically. But, so far there is no good way to do it universally.

The root of this problem is:

> The number of clusters is an ambiguous thing. 

When you dealing with real world data, the data has multiple scales, it is a problem related to
the **granularity** of the data.

So, **the idea of** hierachical clustering is instead of picking the number of clusters, build
a hierachy. 

> top levels - coarse effects. low levels - fine grained

---

##Two Strategies

###Top down <a id="top"></a>

> start with all items in one cluster, split recursively

**Hierachical K-Means** <a id="kmeans"></a>

We know how to split the data into fine number of clusters (e.g., number = 2).

- run K-means algorithm on the original data $x_1 \dots x_n$
- for each of the clustering clusters: $c_j j = 1 \dots k$
  + recursively run K-means on points in $c_j$

![Imgur](http://i.imgur.com/eCvzEgL.png)

**Advantage:** Fast

**Disadvantage:** Greedy, can't cross boundries. Nearby points may end up in different clusters.


###Bottom up <a id="bottom"></a>

> start with singletons. Merge by some criteria.

**Agglomerative clustering** <a id="agglomerative"></a>

Idea: ensure nearby points end up in the same cluster 

Start with a collection $C$ of $n$ singleton clusters

- each cluster contains one data point: $c_i = $ {$x_i$}

Rpeat until only one cluster is remain:

- find a pair of clusters that is closest
- merge the cluster $c_i, c_j$ into a new cluster $c_{i + j}$
- rename $c_i, c_j$ from the collection $C$, add $c_{i + j}$

> This is not the distance between two instances. This is the distance between two clusters.

![Imgur](http://i.imgur.com/qKnAzqd.png)

It produces a dendrogram: hierachical tree of clusters

In this algorithm, you need to define a **distance metric** over clusters.

**Disadvantages:** Slow (much slower than K-means)

**Advantages:** If you want to produce a flat clustering, you pick a threshold on the distance, and cut the tree. Once you have a 
dendrogram, you can cut the data into any granularity.

---
##Distance metrics <a id="distance"></a>

###Single Link <a id="single"></a>

![Imgur](http://i.imgur.com/QIPm4Zx.png)

Look for distance between cloest elements in clusters.

**Advantages:** Simple, in many situations, it works well.

**Disadvantages** Produce long chains. Eventually, you will put two points that far away into a same cluster.

###Complete Link <a id="complete"></a>

![Imgur](http://i.imgur.com/t1DZPnM.png)

Measure the distance between farthest elements in clusters.

But once compute the distance, still compare the cloest.


In the above two measures, they produce different results. In **Single Link**, red and yellow will combine. 
However, In **Complete Link**, red and yellow will not combine, instead, yellow will combine with blue.

###Average Link <a id="average"></a>

![Imgur](http://i.imgur.com/FEghD6J.png)

Average of all pairwise distance. Less affected by outliers.

###Centroids <a id="centroids"></a>

![Imgur](http://i.imgur.com/QKh8jiW.png)

Distance between Centroids (means) of two clusters
