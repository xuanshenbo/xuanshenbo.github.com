---
layout: post
title: "Probability Revision"
description: ""
category: "Pro"
tags: [Probability]
---
{% include JB/setup %}

<!--more-->

##Math notations

$\sum_x f(x) \equiv \sum_{s \in dom(x)} f(x = s)$


**Definition 1.1** (Rules of Probability for Discrete Variables)

The summation of the probability over all the state is 1:

$\sum_{x \in dom(x)} p(x = x) = 1$

This is called normalisation condition. We write $\sum_x p(x) = 1$ for short.

Two variables $x$ and $y$ can interact through

$p(x, y) = p(x) + p(y) - p(x \cap y)$


**Definition 1.2 (Set notation) An alternative notation in terms of set theory is to write**

$p(\text{x or y}) \equiv p(x \cup y)$

$p(x, y) \equiv p(x \cap y)$

**Definition 1.3 (Marginals) **

$p(x) = \sum_y p(x, y)$

**Definition 1.4 (Conditional Probability / Bayes' Rule)**

$p(x \mid y) = \frac{p(y \mid x)p(x)}{p(y)}$

**Definition 1.5 (Probability Density Functions) For a continuous variable x, the probability density f(x) is defined
such that**

$f(x) \geq 0, \int_-\infty^\infty f(x) \mathrm{d}x = 1$
