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

**Definition 1.3 (Marginals)**

$p(x) = \sum_y p(x, y)$

**Definition 1.4 (Conditional Probability / Bayes' Rule)**

$p(x \mid y) = \frac{p(y \mid x)p(x)}{p(y)}$

**Definition 1.5 (Probability Density Functions) For a continuous variable x, the probability density f(x) is defined
such that**

$f(x) \geq 0, \int_{-\infty}^\infty f(x) \mathrm{d}x = 1$

and the probability that $x$ falls in an interval [a, b] is given by

$p(a \leq x \leq b) = \int_a^b f(x) \mathrm{d}x$

Unlike probabilities, probability densities can take positive values greater than 1.

**Definition 1.6 (Independence)**

$p(x, y) = p(x)p(y)$

Provided that $p(x) \neq \text{0 and }p(y) \neq$0 independence of x and y is equivalent to

$p(x \mid y) = p(x)$

$\Leftrightarrow$

$p(y \mid x) = p(y)$

we write $x \bot y$

**Definition 1.7 (Conditional Independence)**

$X \bot Y \mid Z$

denotes that the two sets of variables $X$ and $Y$ are independent of each other provided we know the state of the set
of variables $Z$. For conditional independence, $X$ and $Y$ must be independent given all states of $Z$, means:

$p(X, Y \mid Z) = p(X \mid Z)p(y \mid Z)$

If $X$ and $Y$ are not conditionally independent, they are conditionally dependent, This is written:

$X \top Y \mid Z$

Similarly $X \top Y \mid \emptyset$ can be written as $X \top Y$

---

##Probabilistic Reasoning

The central paradigm of probabilistic reasoning is to identify all relevant variables $x_1, \dots, x_N$ in the 
environment, and make a probabilistic model $p(x_1, \dots, x_N)$ of their interaction. Reasoning(inference) is then 
performed by introducing *evidence* that sets variables in known states, and subsequently computing probabilities
of interest, conditioned on this evidence. 

---

##Prior, Likelihood and Posterior

Much of science deals with problems of the form: tell me something about the variable $\theta$ given that 
I have observed data $D$ and have some knowledge of the underlying data generating mechanism. Our interest is 
then the quantity

$p(\theta \mid D) = \frac{p(D \mid \theta)p(\theta)}{p(D)}$

We know, for continuous situation, 

$p(D)$ = $\int_{\theta}p(D, \theta)$

$= \int_{\theta} p(D \mid \theta)p(\theta)$

Therefore,

$p(\theta \mid D) = \frac{p(D \mid \theta)p(\theta)}{\int_{\theta}p(D \mid \theta)p(\theta)}$

This shows how form a forward or *generative model* $p(D \mid \theta)$ of the dataset, and coupled with a *prior* belief
$p(\theta)$ about which variable values are appropriate, we can infer the *posterior* distribution $p(\theta \mid D)$
of the variable in light of the observed data. The *most probable a posteriori (MAP)* setting is that which maximises
the posterior,$\theta{\ast} = \text{arg }max_{\theta}$ $p(\theta \mid D)$, namely that $\theta$ that maximises the Likelihood $p(D \mid \theta)$
of the model generating the observed data.

![Imgur](http://i.imgur.com/bmWzqrR.png)

The interesting thing is the probability are reverted. We know 
about evidence B, but we really care about the variable A.

For example B is a test result. This diagnostic reasoning which is from 
evidence to its causes is turned up-side-down into cause-reasoning.

Worth noting that the marginal likelihood or evidence $p(B)$ is hard 
to compute. It is always expanded by total probability formula.

$p(B) = \displaystyle\sum_a p(B \mid A = a)p(A = a)$

![Imgur](http://i.imgur.com/FPhy3Cu.png)

How many parameters does it take to specify the entire Bayes network?

The answer is 3.

It takes one parameter to specify $p(A)$, and two parameters to 
specify $p(B \mid A)$ and $p(B \mid \neg A)$


---

##Computing trick

we know:

$p(A \mid B) + p(\neg A \mid B) = 1$

We specify:

$p'(A \mid B) = p(B \mid A)p(A)$

$p'(\neg A \mid B) = p(B \mid \neg A)p(\neg A)$

Therefore,

$p(A \mid B) = \eta * p'(A \mid B)$

$p(\neg A \mid B) = \eta *  p'(\neg A \mid B)$

$\eta = \frac{1}{p'(A \mid B) + p'(\neg A \mid B)}$

This could let us avoid calculating the evidence $p(B)$

---

##Graphs

**Definition 2.1 (Graphs)**

A graph G consists of nodes (vertices) and edges (links) between nodes. Edges may be directed or undirected. Edges can also have associated weight.

