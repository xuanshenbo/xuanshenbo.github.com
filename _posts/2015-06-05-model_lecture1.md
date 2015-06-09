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

##Lecture One

###Sorting and Peer Effects

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

**Granovetter**


1. N Individuals

2. Each has a Threshold
	-  $T_j$ for person j
	- Join if $T_j$ others join

If you have 5 friends, the threshold for each of them willing to buy a purple hat is:
 
    0 1 1 1 2

0 means he is not influenced by other people, just wanna buy a purple hat.

1 means if only one of his friend get a purple hat, he will also get one

In the end, all people wearing purple hat.

Another example:

If you have 5 friends,

    0 1 2 3 4

In the end, all people wearing purple hat, but actually not so many people really want one. This is tail wagged the dog.

Collection Action

More Likely if:

- Lower Thresholds

- More Variation in thresholds

That's why it is very hard to predict collective behavior, because you not only need to know the average threshold, you also need to know the distributions, and how people connect to each other.

---

**Standing Ovations**

After a show, Do I stand up or not? You don't have much time to decide, 
you have a short time to make a judgement. This simplified this problem.

Standing Ovations is very suitable to let people thinking about rule based domain.

- Peer Effect: other people stand, you stand

- Information: other people seems know more information, you learn from them


1. Threshold to Stand: $T$

2. Quality: $Q$

3. Signal: $S = Q + E$

4. Initial Rule
	- If $S > T$,  Stand

5. Subsequent Rule
	- Stand if more X% stand

**Claim 1:** Higher Quality $Q$, Stand if $Q + error > T$ 
 
**Claim 2:** Lower Threshold $T$, more people stand, if $Q + error > T$

**Claim 3:** Lower X, more ovations. Stand if more than X%

 Signal: $S = Q + E$

- $E = Error$

- $E = Diversity$ People could have different preference or taste

Example:

    1000 people
    T = 60
    Q = 50
    T < Q Nobody will stand up

    E in [-50, +50]

![Imgur](http://i.imgur.com/pmFNIEv.jpg)

So, large variation, more people will stand up

So, in what situation, the Error $E$ is high?

* Audience

	- Diverse

	- Unsophisticated

* Performance

	- Multidimensional

	- Complex

1. Higher Quality

2. Lower Threshold

3. Larger Peer Effects

4. More Variation

Two more facts could influence this model:

5. Use Celebrities/Academic (People in front don't aware other people,
						People in back knows everyone, but nobody see them)
6. Large group

---

###Where can we apply the model?

Collective Action

Academic Performance

Urban Renewal

Fitness/Health

---

###Identification

Schelling or Standing Ovation

Homophily or Peer Effect?

Sorting:

    AABBAA

    BBABBA

We will observe Bs move to second group

Peer Effects:

We will observe Bs turn into A.

However, if we only take a snapshot, there is no way to distinguish to identify it. We need more data, dynamic data. On the other hand, it guide us to collect the data.
