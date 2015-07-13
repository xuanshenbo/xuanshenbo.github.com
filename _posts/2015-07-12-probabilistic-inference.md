---
layout: post
title: "Probabilistic inference"
description: ""
category: "pro"
tags: ["Probability"]
---
{% include JB/setup %}

<!--more-->

#Probabilistic Inference

![Imgur](http://i.imgur.com/tgNl43y.png)

Hidden variable is the variable we don't need to know, don't need to output,
but we need to compute during the process.

---

##Eumeration

> Eumeration goes through all the possibilities, adds them up and comes with an answer.

For example, 

$p(+b \mid +j, +m)$ can be determined by enumerate all hidden variables.

$p(+b, +j, +m) = \displaystyle\sum_A \displaystyle\sum_E p(+b)p(+j \mid A)p(+m \mid A)p(E)p(B)$

$p(+j, +m) = \displaystyle \sum_A p(+j \mid A)p(+m \mid A)$

$p(+b \mid +j, +m) = \frac{p(+b, +j, +m)}{p(+j, +m)}$

If the network is too big, practically, it is impossible to do. Therefore,
it needs some techniques.

###Pulling out terms

For example,

$\sum_e\sum_a p(+b)p(e)p(a\mid +b, e), p(+j \mid a)p(+m, a)$

The term $p(+b)$ has nothing to do with the summing up. Therefore, we 
can pull it out from the equation.

###Variable Elimination

![Imgur](http://i.imgur.com/KOO9SpQ.png)

$p(c, a, b) = \sum_a\sum_bp(c \mid b, a)p(b \mid a)p(a)$

First technique is called **elimination**:

Simply, calculate $p(b \mid a)$ first.

Second technique is called **marginalisation**:

It is just: $p(b, a) = \sum_a p(b \mid a)p(a)$

Nothing special, just doing calculation step by step.

###Approximate Inference - Sampling

Bascially, it is by sampling the observable result, and collect data
from the experiments.

The sampling has two advantages: 1. Computationally low cost 2. If we 
don't know the condition, we can still do Sampling.

If we want to compute conditional probability. We will have to use the 
technique called **Rejection Sampling**

For example, we want to sampling $p(a \mid c = cloudy)$, if the weather
is not cloudy, then we don't sampling until it is a cloudy day. 

It is also consistent.

But if we are sampling a small probability event, we ends up waiting 
forever and reject most of the samples.

###Likelihood Weighting

We fix the evidence variable. We say C is always positive and we
sample the rest variables. 

+b, +c
-b, +c
+b, +c

But we has a problem. The resulting sample end up being inconsistent.

We can fix this problem by assign probability to each sample and
weighting them correctly.

We are going to collect sample as before. But we add a probabilitic
weighting to each sample.


###Gibbs Sampling

Gibbs sampling uses Markov chain Monte Carlo

The idea is that we re-sample just one variable at a time conditioning 
on others.

That is, we have a set of variables.

And we initialise them to random variable keep the evidence fixed.

![Imgur](http://i.imgur.com/SkjeIwJ.png)

Now at each iteration through the loop. We select just one non-evidence 
variable and resample it. Based on all the other variables. And that will give us another sample.

---


