---
layout: post
title: "naive Bayes"
description: ""
category: "Mach"
tags: ["Machine Learning"]
---
{% include JB/setup %}

<!--more-->

We're using SPAM email detection as an example.

---

##Maximum likelihood

For example, we detect 8 emails, they are: S S S H H H H H

We assume:

$p(S) = \pi$

$p(y_i) = \pi\text{ if	}y_i = S$

$p(y_i) = 1 - \pi\text{ if	}y_i = H$

Then we use binary representation of SPAM and HAM.

$p(y_i) = \pi^{y_i} \cdot (1 - \pi)^{1 - y_i}$

Next, we assume every Email is independent.

$p(data) = \prod_{i = 1}p(y_i) = \pi^{count(y_i = 1)} \cdot (1 - \pi)^{count(y_i = 0)}$

In this example, we have 3 SPAMs and 5 HAMs.

$= \pi^3 \cdot (1 - \pi)^5$

Now we need to maximum this equation. Instead of directing maximum this
equation, we could maximum the log of this equation. 

$\log (p(data)) = 3 \cdot \log (\pi) + 5 \cdot \log (1 - \pi)$

The maximum value is obtained by calculate the derivative equals 0.

$(\log (p(data)))' = 0 = \frac{3}{\pi} - \frac{5}{1 - \pi}$

$ \pi = \frac{3}{8}$

---

Bayes Network

![Imgur](http://i.imgur.com/Mw4auOt.png)

Acutally, we construct a Bayes network, and use words as events to predict
the posterior probability.

---

Laplace Smooth

There is huge problem in this method. If a word does not exist in SPAM in
the learning data. Then the email that contains this word will never be 
detect as SPAM because of the calculation of joint probability.

The different exist in the calculation of Maximum likelihood.

In previous, we calculate the maximum likelihood using derivative or
using $p(x) = \frac{count(x)}{N}$

Now, with Laplace smooth, it becomes:

$p(x) = \frac{count(x) + k}{N + k\mid x \mid}$

where $k$ is laplace smooth parameter. $k \mid x \mid$ is $k$ times
the number of different categories.

