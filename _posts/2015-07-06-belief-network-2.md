---
layout: post
title: "Belief Network 2"
description: ""
category: "Mach"
tags: ["Machine Learning"]
---
{% include JB/setup %}


<!--more-->

##The impack of collisions

**Definition 3.2**

Given a path $P$, a *collider* is a node $c$ on $P$ with neighbours $a$ and
$b$ on $P$ such that $a \rightarrow c \leftarrow b$. Note that a collider
is path specific.

![Imgur](http://i.imgur.com/yFrzhM8.png)

![Imgur](http://i.imgur.com/IcfvIWh.png)

In a general BN, how can we check if $x \bot y \mid z$. In fig(3.7a), x
and y are independent when conditioned on z since

$p(x, y \mid z) = p(x \mid z)p(y \mid z)$

Similarly, for fig(3.7b), x and y are independent conditioned on z since.

$p(x, y \mid z) \propto p(z \mid x)p(x)p(y \mid z)$

which is a function of x multiplied by a function of y. In fig(3.7c),
however, x and y are graphically dependent since 
$p(x, y \mid z) \propto p(z \mid x, y)p(x)p(y)$; in this situation,
variable $z$ is a collider. The arrows of its neighbours are pointing
towards it. In (d), when we condition on z, x and y will be graphically
dependent, since 

$p(x, y \mid z) = \frac{p(x, y, z)}{p(z)} \displaystyle\sum_w p(z \mid w)p(w\mid x, y)p(x)p(y) \neq p(x \mid z)p(y \mid z)$

The above inequality holds due to the term $p(w \mid x, y)$ only in specific
cases such as $p(w \mid x, y) = const$, would x and y be independent. 
Intuitively, variable w becomes dependent on the value of z, and since x 
y are conditionally dependent on w, they are also conditionally dependent 
on z.

If there is a non-collider z which is conditioned along the path between 
x and y, then this path cannot induce dependence between x and y. 
Similarly, if there is a path between x and y which contains a collider, 
provided that this collider is not in the conditioning set (and neither 
are any of its decendants) then this path does not make x and y dependent.
If there is a path between x and y which contains no colliders and no 
conditioning variables, then this path 'd-connects' x and y. Note that a 
collider is defined *relative to a path*. In fig(3.8a), the variable d 
is a collider along the path a - b - d -c, but not along the path a - b -d
-e (since, relative to the path, the two arrows do not point towards to d).

Consider the BN: $A \rightarrow B \leftarrow C$. Here A and C are 
(unconditionally) independent. However, conditioning of B makes them 
'graphically' dependent. Intuitively, whilst we believe the root causes
independent, given the value of the observation, this tells us something
about the state of *both* the causes, coupling them and making them 
(generally) dependent. In definition 3.3, below we describe the effect 
that conditioning/marginalisation has on the graph of the remaining
varirables.

**Definition 3.3 (Some properties of belief networks)**

It is useful to understand what effect conditioning or marginalising a 
variable has on a belief network.

![Imgur](http://i.imgur.com/4OX6syG.png)


Marginalising over C makes A and B independent. A and B are 
(unconditionally) independent: $p(A, B) = p(A)p(B)$. In the absence of

any information about the effect C, we retain this belief.

![Imgur](http://i.imgur.com/OjDJ4af.png)

Conditioning on C makes A and B (graphically) dependent. In general,

$p(A,B \mid C) \neq p(A \mid C) p (B \mid C)$. Although the causes are 
a priori independent, knowing the effect C in general tells us something 
about how the casuses colluded to bring about the effect observed.

![Imgur](http://i.imgur.com/gsc7FCX.png)

Conditioning on D, a decendent of a collider C, makes A and B (graphically)
dependent.

![Imgur](http://i.imgur.com/jjfT9bS.png)


$p(A, B, C) = p(A \mid C)p(B \mid C)p(C)$

Here there is a 'cause' C and independent 'effects' A and B.

![Imgur](http://i.imgur.com/H6gmtod.png)

Marginalising over C makes A and B (graphically) dependent. In general,
$p(A, B) \neq p(A)p(B)$. Although we don't know the 'cause', the 'effects'
will nevertheless be dependent.

![Imgur](http://i.imgur.com/3B1ihpM.png)

Conditioning on C makes A and B independent: $p(A, B \mid C) = p(A \mid C)p(B \mid C)$.
If you know the 'cause' C, you know everything about how each effect occurs,
independent of the other effect. This is also true for reversing the 
arrow from A to C, in the case A would 'cause' C and then C 'cause' B.
Conditioning on C blocks the ability of A to influence B.

![Imgur](http://i.imgur.com/hHqK3fD.png)

---

##Graphical path manipulations for independence

Intuitively, we now have all the tools we need to understand when x is 
independent of y conditioned on z. We need to look at each path between 
x and y. Coloring x as red and y as green and the conditioning node z as
yellow, we need to examine each path between x and y and adjust the edges,
following the intuitive rules in fig(3.9)

![Imgur](http://i.imgur.com/nDJtKeK.png)

![Imgur](http://i.imgur.com/DZxPDUA.png)
