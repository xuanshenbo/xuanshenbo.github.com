---
layout: post
title: "EM algorithm"
description: ""
category: "Mach"
tags: ["Machine Learning"]
---
{% include JB/setup %}


##IID

> We assume the data is IID which means identically distributed and 
independently drawn from same distribution.

---

##Mixture models

Recall types of clustering methods

1. hard clustering: clusters do not overlap
  + element either belongs to cluster or it does not
2. soft clustering: clusters may overlap 
  + stength of association between clusters and instances

###Mixture models (soft clustering)

1. probabilistically-sounded way of doing soft clustering 
2. each cluster: a generative model (Gaussian or multinomial)
3. parameters(e.g. mean/covariance are unknown)

---

<!--more-->

###Expectation Maximization algorithm

> Automatically discover all parameters for K 
"sources"(k guassian distribution)


In the first graph, if we already know which point come from which
distribution, then it is easy to figure out the parameters of the 
Guassian distribution.


But if we don't know which point come from which distribution (figure 2), 
it is going to be tricky.

But, if we know the parameters of the two distribution, we could 
figure it out by calculating the probabilities of each data point. 

![Imgur](http://i.imgur.com/YImqSmE.png)

Therefore, we have a chicken and egg problem.

If somebody told you the mean and variance, you could figure out which 
distribution the data came from. On the other hand, if you know which 
data point came from which distribution, you could calculate the 
mean and variance.

So you need one to imply the other.

That's basically what **EM** algorithm does for you.

EM algorithm

+  start with two randomly placed Guassian $(\mu_a, \sigma_a^2)(\mu_b, \sigma_b^2)$
+  for each point: $P(b \mid x_i) = $ does it look like it came from b ? 
Unlike *K-means*, it does not assign a binary (yes or no) to a point, but 
assign a probability to a data point. Thus, it is a soft boundary.
+  adjust$(\mu_a, \sigma_a^2)$ and $(\mu_b, \sigma_b^2)$ to fit points
assigned to them.
+ Iterating until it converges

---

##Example

![Imgur](http://i.imgur.com/KdzeM2r.png)

At first, we assign random value to two guassian distribution.

Then we compute the probabilities for all the points. And then assigned 
value to these points.

![Imgur](http://i.imgur.com/UboizLz.png)

Once we have done the color assignment. We could re-compute the the mean 
and variance for both distributions.

$\mu_b = \frac{b_1x_1 + b_2x_2 + \dots + b_nx_n}{b_1 + b_2 + \dots + b_n}$

$\sigma_b^2 = \frac{b_1(x_1 - \mu_b)^2 + \dots + b_n(x_n - \mu_b)^2}{b_1 + b_2 + \dots + b_n}$

After this step, your guassian distribution will looks like this.

![Imgur](http://i.imgur.com/zDi4u59.png)

And it eventually will looks like this:

![Imgur](http://i.imgur.com/zDkdUrP.png)
