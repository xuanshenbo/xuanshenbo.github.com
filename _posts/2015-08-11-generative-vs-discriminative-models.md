---
layout: post
title: "Generative vs Discriminative models"
description: ""
category: "Mach"
tags: ["Machine Learning"]
---
{% include JB/setup %}

<!--more-->

##Generative model 

---

For example, we have a classification task. We have a dataset which contains a bunch of features:
$x_1, x_2, \dots, x_n$, and we have a a bunch of class labels $c_1, c_2, \dots, c_m$

In generative model, we try to generate the distribution of $p(x \mid c)$.

We want to get the distribution of $x$ on each class label. For example:

![Imgur](http://i.imgur.com/BGFVgNl.png?1)

We want to get the distribution of $P(x \mid c=1)$ and $P(x \mid c=2)$. 


---

## Discriminative model 

---

In discriminative model, we try to model the decision boundary. We try to find the 
distribution of $P(c \mid x)$.

##Difference and comparison

Give an intuitive example of these two models. Say you and a kid visit the zoo. After coming back from
the zoo, you give the kid two pictures of horse and elephant. Then you ask him to tell which one is 
elephant. This is a discriminative model. The kid knows how to separate them, because he captures some 
features of elephant.

And then, you give him a paper and ask him to draw a picture of an elephant. This is a generative model,
because the kid is acutally needs to know which part of the elephant looks like and generate a sample.

You see, the generative model is much expensive than discriminative model.

In summary.

**Discriminative model**:

Pros:
  + Easy to model, require fewer observation
Cons:
  + We can not generate samples from it. Just to classify, not to generate 

**Generative model**:

Pros:
  + We get the underlying idea of what the class is built on.
Cons:
  + Very expensive, lots of parameters/data

Examples:

	Naive bayes: generative model 
	logistic regression: Discriminative model
