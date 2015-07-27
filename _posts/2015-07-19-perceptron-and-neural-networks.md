---
layout: post
title: "Perceptron and Neural Networks"
description: ""
category: "Mach"
tags: ["Machine Learning"]
---
{% include JB/setup %}

<!--more-->

##McCulloch and Pitts' Neuron:

1. a set of weighted inputs $w_i$ that correspond to the synapses
2. an adder that sums the input signals
3. an activation function (initially a threshold function) that decides
whether the neuron fires for the current inputs

![Imgur](http://i.imgur.com/83irn3l.png)

---

##Limitations

One question that is worth considering is how realistic is this model of
a neuron? The answer is **Not very**.

The inputs to a real neuron are not necessarily summed linearly: there
may be non-linear summations. However, the most noticeable difference is
that real neurons do not output a single output response. Furthermore,
the neurons are not updated sequentially according to a computer clock,
but update themselves randomly.

It is possible to improve the model to include many of these features,
but it is already complicated enough. M and P's neurons already 
provide a great deal of interesting behavior that resembles the action 
of the brain.

---

##Problems with squared error

The squared error measure has some drawbacks:

1. If the desired output is 1 and the actual output is 0.000000001
there is almost no gradient for a logistic unit to fix up the error
2. If we are trying to assign probabilities to mutually exclusive class
labels, we know that the outputs should sum to 1, but we are depriving
the network of the knowledge.

**Is there a different cost function that works better?**

**Yes**: Force the outputs to represent a probability distribution across
discrete alternatives.

---

#Restriction bias

Restriction bias tells you something about the representational power
of whatever data structure that you're using.
So in this case, the network of neurons.

And it tells you the set of hypotheses that you're willing to consider.

So in Perceptron, we were only considering planes. 

Sigmoids: much more complex, not much restriction.

$\rightarrow$ Boolean function: network of threshold-like units 

$\rightarrow$ Continuous function: "Connected", a single hidden layer,
as long as we have enough hidden unit, each unit can worry about one
little patch of the function, and the patch get set at the hidden layer.
And output layer get stitched together.

$\rightarrow$ Arbitrary, add one more layer, so two layer. 







---

##Softmax

It is a kind of soft continuous version of the maximum function. 
So the way the units in a softmax group work, is that they each 
receive some total import to they have accumulated from below. 

![Imgur](http://i.imgur.com/Tp55CUW.png)

That $Z_i$ for the unit is called the 'logit'. 

Because of the bottom of that equation, is the some of the top line over 
all possibilities. 

So we force the $y_i$ to represent a probability distribution over
mutually exclusive alternatives just the the equation.

This equation has a nice derivative. If you ask how $z_i$ affect $y_i$.
It is obvious depending on other $z_i$. 

**If we are using softmax group as the output, what is the right cost
function**.

The answer is the negative log probability of the correct answer.
That is we want to maximize the log probability of getting answer right.

So if one of the target values is the one when the remaining ones are
zero. Then we simply sum of all possible answers. We put zeros in front
of wrong answers. 

![Imgur](http://i.imgur.com/n0HtEJE.png)

That's called cross-entropy cost function.

$C$ has a very big gradient when the target value is 1 and the output 
is almost zero.

For example, a value of 0.000001 is much better than 0.000000001
The value $c$ increase a lot.

That cost function $C$ has a very steep derivative when the answer is very
wrong, and exactly balanced the fact with the way that output changes It
should change the input divided by $z$. It is very flat when the answer 
is very well.

![Imgur](http://i.imgur.com/EhO7CA0.png)

And when you multiply together, to get the derivative of the cross entropy.
with respect the logit going into $i$ per unit $i$. 

So that derivative is how fast the cost function changes as you change 
the output of the unit times how fast the output as you change the $i$.
And notice we need to add up across the $j$, because when you change the 
$i$, the output of all different unit changes. 




