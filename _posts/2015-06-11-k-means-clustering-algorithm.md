---
layout: post
title: "K means clustering algorithm"
description: ""
category: "Clu"
tags: [IA, Clustering]
---
{% include JB/setup %}


<!--more-->

#K-means clustering

input: K set of points $X_i \dots X_n$

place centroids $C_i, \dots, C_n$ at **random** locations

Repeat until convergence:

- for each point $x_i$
  * find nearest centroid $c_j$ (average min $D(x_i, c_j)$)
  * assign the point $x_i$ to cluster $j$
- for each cluster $j = 1 \dots k$: (recompute each cluster centroid position)
  * new centroid $c_j = $ mean of all points $x_i$ assigned to cluster $j$ in previous step.

Example:

![initial](http://i.imgur.com/nngazhf.png)

Initially, the random placed centroids **red** and **yellow** triangles.

![assign](http://i.imgur.com/NNl0XC4.png)

Calculate distance from $x_i$ to each centroid, and assign them into either cluster.

![Imgur](http://i.imgur.com/KcsH5xR.png)

Recompute the centroids of clusters.

![Imgur](http://i.imgur.com/NwBMqS2.png)

Repeat the steps until there is no items re-assign to a different cluster.


---

##Advantages and Disadvantages

---

**Disadvantages:** You can only take numeric attributes of the data. Because only numeric can be computed distances.

**Advantages:** K-means is fast.



