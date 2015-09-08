---
layout: post
title: "Some terminologies in Markov Chain"
description: ""
category: "Mach"
tags: ["Machine Learning"]
---
{% include JB/setup %}

##Stochastic matrix

In math, a Stochastic matrix (also termed probability matrix, transition matrix,
substitution matrix or Markov matrix) is a matrix used to describe the transitions 
of a Markov Chain.

Each of its entries is a nonnegative real number representing a probability.

**A right Stochastic matrix** is a real square matrix, with row summing to 1.

**A Left Stochastic matrix** is a real square matrix, with each column summing to 1.


A stationary probability vector $\pi$ is defined as a distribution, that does 
not change under application of the transition matrix. It is defined as a probability
distribution on the set ${1,\dots,n}$ which is also a row eigenvector of the probability matrix, associated with eigenvalue 1.

$\pi P = \pi$

