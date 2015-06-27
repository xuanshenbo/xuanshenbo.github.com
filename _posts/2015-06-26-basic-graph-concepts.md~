---
layout: post
title: "Basic Graph Concepts"
description: ""
category: "Gra"
tags: [Graph]
---
{% include JB/setup %}

###Summary

+ A graph is made of nodes and edges, which we will use to represent variables and relations between them
+ A DAG is an acyclic graph and will be useful for representing 'causal' relationships between variables
+ Neighbouring nodes on an undirected graph will be useful represent dependent variables.
+ A graph is singly-connected if there is only one path from any node to any other - otherwise the graph is 
multiply-connected.
+ A Clique is group of nodes all of which are connected to each other
+ The adjacency matrix is a machine-readable description of a graph. Powers of the adjacency matrix give information
on the paths between nodes.



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

![Imgur](http://i.imgur.com/QAhc7kO.png)

Where $A_{ij} = 1$ if there is an edge from node $i$ to node $j$ in the graph, and 0 otherwise.
An undirected graph has a symmetric adjacency matrix. 

Provided that the nodes are labelled in *ancestral order* (parents always come before children) a directed Graph 
(fig2.2b) can be represented as a triangular adjacency matrix:

![Imgur](http://i.imgur.com/FtMnZ0Q.png)\

**Clique matrix**

For an undirected graph with N nodes and maximal cliques $C_1, \dots, C_K$ a clique matrix is an $N \times K$ matrix in 
which each column $c_k$ has zeros except for ones on entries describing the clique. For example

![Imgur](http://i.imgur.com/pzsS27P.png)

**Graph Confusions** 

**State Transition Diagrams**

Such representations are used in Markov chains and finite state automata. Each state is a node and a directed edge
between  node $i$ and $j$ (with an associated weight $p_{ij}$ ) represents that a transition from state $i$ to state $j$
can occur with probability $p_{ij}$. From the graphical models perspective we use a directed graph 
$x(t) \rightarrow x(t + 1)$ to represent this Markov chain. The state-transition diagram provides a more detailed 
graphical description of the conditional probability table $p(x(t + 1) \mid x(t))$.

**Neural Networks**

Neural networks also have nodes and edges. In general, however, neural networks are graphical representations of
*functions*, whereas graphical models are representations of distributions.
