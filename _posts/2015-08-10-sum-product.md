---
layout: post
title: "Sum Product"
description: ""
category: "Mach"
tags: ["Machine Learning"]
---
{% include JB/setup %}

<!--more-->

What problem is NP-hard in Probability graph model ?

Given a Probability graph model $P_{\Phi}$. A variable $X$ and a value $x \in Val(X)$ compute $P_{\Phi}$ is 
**NP-hard**. Or even decide if $P_\Phi(X = x) > 0$ is also NP-hard.

##Sum-Product

Given a graph model

![Imgur](http://i.imgur.com/9BmZ03n.png)

To compute $P(x_4)$, we just need to:

$P(x_4) = \displaystyle\sum_{x_1,x_2,x_3,x_5} = \phi x_1(x_1) \phi x_2(x_1, x_2) \phi x_3(x_2, x_3) \phi x_5(x_5, x_3) \phi x_4(x_2, x_3, x_4)$

$\phi x_1(x_1)$ denotes a factor who scope is $x_1$.

The inference of Markov model take exactly same form.

![Imgur](http://i.imgur.com/1KwcJDP.png?1)

$P(D) = \displaystyle\sum_{ABC} \phi_1(AB)\phi_2(BC)\phi_3(CD)\phi_4(AD)$

$\tilde{P}(ABCD)$ is the unnormalized measure. In order to normalize it. We need to divide by the partition function $Z$.

Marginalize all produce. That's why it is called Sum-Product.

$Z$ is called normalizing constant.

$P(D) = \frac{1}{Z} \tilde{P}(D)$ We can compute $\tilde{P}(D)$ first and then renormalizing it.

But, what if we already know some evidence, say $E = e$ ? We could do *Reduced Factors*

$P(Y \mid E = e) = \frac{P(Y, E = e)}{P(E = e)}$

$P(Y, E = e) = \displaystyle\sum_w P(Y, W, E = e) = \displaystyle\sum_w \frac{1}{Z} \prod\phi(D_k, E = e)$

$w$ is remaining variable. 

In plain english, we could eliminate those factor that contains $E \neq e$.

Why is the equation $\displaystyle\sum_w P(Y, w, E = e)$ hard to compute in general?

Answer: The summation over all $w$ is exponential. If $w$ has 100 binary values, then summing take $2^{100}$.
$P(Y, W, E = e)$ is always easy to compute because it is just the proudct of all conditional Probability distribution.


