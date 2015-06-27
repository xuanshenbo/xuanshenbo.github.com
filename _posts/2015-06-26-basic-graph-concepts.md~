---
layout: post
title: "Basic Graph Concepts"
description: ""
category: "Gra"
tags: [Graph]
---
{% include JB/setup %}


<!--more-->

**Cycle, loop and chord**

A cycle is directed path stat starts and returns to the same node. A *loop* is a path containing more than two nodes, 
irrespective of edge direction, that starts and returns to the same node. For example, 1-2-4-3-1 forms a loop, but the
graph is *acyclic* (contains no cycles). A *chord* is an edge that connects two non-adjacent nodes in a loop. For 
example, the 2-3 edge is a chord in the 1-2-4-3-1 loop.


**Markov blanket**

The Markov blanket of a node is its parents, children and the parents of its children (*excluding itself*).

![Imgur](http://i.imgur.com/riplQmJ.png)

In this case, $x_4$ is $x_1, x_2, x_3, x_5, x_6, x_7$


**Singly Connected Graph**

A graph is *singly connected* if there is only one path from any node A to any other node B. Otherwise the graph is
*multiply connected*. This definition applies regardless of whether or not the edges in the graph are directed. An 
alternative name for a singly connected graph is a *tree*. A multiply-connected graph is also called *loopy*.

![Imgur](http://i.imgur.com/ymN2Nps.png)


**Spanning Tree**

A spanning tree of an undirected graph G is a singly-connected subset of the existing edges such that the 
resulting singly-connected graph covers all nodes of G. On the below is a graph and an associated spanning tree.
A maximum weight spanning tree is a spanning tree such that the sum of all weights on the edges of the tree is at least
as large as any other spanning tree of G.

![Imgur](http://i.imgur.com/F9VSflr.png)

**Finding a maximal weight spanning tree**

An algorithm to find a spanning tree with maximal weight is as follows: Start by picking the edge with the largest 
weight and add this to the edge set. Then pick the next candidate edge which has the largest weight and add this to 
the edge set - if this results in an edge set with cycles, the reject the candidate edge and propose the next largest
edge weight. Note that there may be more than one maximal weight spanning tree.

---

##Numerically Encoding Graphs

###Edge list

As the name suggests, an edge list simply lists which node-node pairs are in the graph. For fig(2.2a), an edge
list is L = {(1,2), (2, 1), (1, 3), (3, 1), (2, 3), (3, 2), (2, 4), (4, 2), (3, 4), (4, 3)}. Undirected edges are 
listed twice, once for each direction. 

![Imgur](http://i.imgur.com/8BHfCrU.png)


###Ajacency matrix

An alternative is to use an *adjacency matrix*

$A = 
\begin{pmatrix}
0 & 1 & 1 & 0 \\
1 & 0 & 1 &1 \\
1 & 1 & 0 & 1 \\
0 & 1 & 1 & 0 \\
$

