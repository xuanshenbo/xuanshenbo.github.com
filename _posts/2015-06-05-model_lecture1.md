---
layout: post
title: "Model Lecture 01 Summary"
description: ""
category: "Model"
tags: [Model]
---
{% include JB/setup %}

<!--more-->

#Model Thinking

###Lecture One

####Sorting and Peer Effects

![Imgur](http://i.imgur.com/TvtYxb7.png?1)

**Sorting:** When you looking at this map, the segregation is quite clear. This shows people choose to live with people a lot like they do. 

**Peer Effects:** We change our behaviors to match other people. For example, if you hang out with a group of people who smoke, you will probably start smoking. 

So, these forces make people to choose where they live and what kind of 
people they wanna to be, to believe what other people believe, to act like other people. 

So, we are going to construct some models to understand these behaviors.

---

###Models

1. Schelling

2. Granovetter

3. Standing Ovation

---

####Two Model Categories

**Equation Based Model**

    Score = 50 + 5 Hours

This is a linear model.

**Agent Based Model**

1. individuals (people, countries ...)

2. behaviors (If the behavior might be optimize, then the model is called game theory model, each individual optimize its behavior)

3. outcomes

---

###Schelling

Schelling try to understand segregation.

![Segregation](http://i.imgur.com/EQni893.png)

Schelling construct an **Agent based model**
Schelling's model is about people choosing where to live.
He simplified the problem:
Each person now thinking about should I stay or should I move.

![Checkerboard](http://i.imgur.com/ZMP6ubs.png)

For example, the person has been allocated on a checker board, 
a person live in X, and No.3 is blank. Red represents rich people, grey represents poor people. So, now the person lived in X is thinking about 3/7 neighbors are like me. Should I stay or leave?

This is called **Threshold based rule**. Based on this threshold, he decided whether move or stay.

The empirical experiments show that the higher the threshold, the 
stronger segregation there will be until the threshold "hits" on a upper bound that the algorithms will never converge, it just running forever because it never satisfied the requirements.


**Tipping phenomenon**

1. Exodus Tip

One person leave the system causes other people leave.

2. Genesis Tip

One person come in, causes other people leave.

One of the important thing that this model tells us is the macro behavior does not consist with what people want. 

---
## Measurement
### Index Similarity

![Imgur](http://i.imgur.com/N0sN0nd.png)

$Rich = 12 \times 10 + 6 \times 5 = 150 $

$Poor = 6 \times 10 + 4 \times 5 = 90$

$BlueIndex = \mid \frac{10}{150} - \frac{0}{90} \mid = \frac{1}{15}$

$YellowIndex = \mid \frac{0}{150} - \frac{10}{90} \mid = \frac{1}{9}$   
 
$GreenIndex = \mid \frac{5}{150} - \frac{5}{90} \mid = \frac{1}{45}$

$Total = 12 \times \frac{1}{15} + 6 \times \frac{1}{9} + 6 \times \frac{1}{45} = \frac{72}{45}$

Normally, we divide the result by 2 to scale it down 

$\frac{Total}{2}= \frac{72}{90} = 0.8 $

Therefore, the segregation is 80%.

---

###Peer Effects

####Granovetter

Model

1. N Individuals

2. Each has a Threshold
	-  $T_j$ for person j
	- Join if $T_j$ others join


