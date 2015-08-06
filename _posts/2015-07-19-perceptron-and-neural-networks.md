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

##Preference bias

Preference bias tells you something about the algorithm that you are using 
to learn. That tells you, given two representations, why I would 
prefer one over the other. 

###Initial weights

Small random values.

$\rightarrow$ Local minima variability

$\rightarrow$ low complexity: because the large weights could lead to 
overfitting.

So the neural networks implement a kind of bias that says Prefer correct
over incorrect but all things being equal, the simpler explanation, is 
preferred. $\rightarrow$ **Occam's Razor**.

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

---

##A more detailed explanation of Softmax

Softmax regression (or multinomial logistic regression) is a generalization of logistic regression to the case where 
we want to handle multiple classes. In logistic regression we assumed that the labels 
were binary: $y^{(i)} \in \\{0,1\\}$. 
We used such a classifier to distinguish between two kinds of hand-written digits. Softmax regression allows us 
to handle $y^{(i)} \in \\{1,\ldots,K\\}$ where $K$ is the number of classes.

Recall that in logistic regression, we had a training set $\\{ (x^{(1)}, y^{(1)}), \ldots, (x^{(m)}, y^{(m)}) \\}$ 
of $m$ labeled examples, where the input features are $x^{(i)} \in \Re^{n}$. 
With logistic regression, we were in the binary classification setting, so the labels were $y^{(i)} \in \\{0,1\\}$. 
Our hypothesis took the form:

$\begin{align}
h_\theta(x) = \frac{1}{1+\exp(-\theta^\top x)},
\end{align}$

and the model parameters $\theta$ were trained to minimize the cost function

$$\begin{align}
J(\theta) = -\left[ \sum_{i=1}^m y^{(i)} \log h_\theta(x^{(i)}) + (1-y^{(i)}) \log (1-h_\theta(x^{(i)})) \right]
\end{align}$$

In the softmax regression setting, we are interested in multi-class classification (as opposed to only binary 
classification), and so the label $y$ can take on $K$ different values, rather than only two. 
Thus, in our training set $\\{ (x^{(1)}, y^{(1)}), \ldots, (x^{(m)}, y^{(m)}) \\}$, we now have that 
$y^{(i)} \in \\{1, 2, \ldots, K\\}$. (Note that our convention will be to index the classes starting from 1, 
rather than from 0.) For example, in the MNIST digit recognition task, we would have $K=10$ different classes.

Given a test input $x$, we want our hypothesis to estimate the probability that $P(y=k \mid x)$ 
for each value of $k = 1, \ldots, K$. I.e., we want to estimate the probability of the class label taking on each of 
the $K$ different possible values. Thus, our hypothesis will output a $K$-dimensional vector (whose elements sum to 1) 
giving us our $K$ estimated probabilities. Concretely, our hypothesis $h_{\theta}(x)$ takes the form:

$$\begin{align}
h_\theta(x) = 
\begin{bmatrix} 
P(y = 1 | x; \theta) \\
P(y = 2 | x; \theta) \\
\vdots \\
P(y = K | x; \theta)
\end{bmatrix}
=
\frac{1}{ \sum_{j=1}^{K}{\exp(\theta^{(j)\top} x) }}
\begin{bmatrix}
\exp(\theta^{(1)\top} x ) \\
\exp(\theta^{(2)\top} x ) \\
\vdots \\
\exp(\theta^{(K)\top} x ) \\
\end{bmatrix}
\end{align}$$

Here $\theta^{(1)}, \theta^{(2)}, \ldots, \theta^{(K)} \in \Re^{n}$ are the parameters of our model. 
Notice that the term $\frac{1}{ \sum_{j=1}^{K}{\exp(\theta^{(j)\top} x) } }$ 
normalizes the distribution, so that it sums to one.

For convenience, we will also write $\theta$ to denote all the parameters of our model. When you implement 
softmax regression, it is usually convenient to represent $\theta$ as a $n$-by-$K$ matrix obtained by 
concatenating $\theta^{(1)}, \theta^{(2)}, \ldots, \theta^{(K)}$ into columns, so that

![Imgur](http://i.imgur.com/7515z0b.png)

##Cost function

We now describe the cost function that we’ll use for softmax regression. In the equation below, 
$1\\{\cdot\\}$ is the ”‘indicator function,”’ so that $1\\{\hbox{a true statement}\\}=1$, and 
$1\\{\hbox{a false statement}\\}=0$. For example, $1\\{2+2=4\\}$ evaluates to 1; whereas $1\\{1+1=5\\}$ evaluates to 0. 
Our cost function will be:

$$\begin{align}
J(\theta) = - \left[ \sum_{i=1}^{m} \sum_{k=1}^{K}  1\left\{y^{(i)} = k\right\} \log \frac{\exp(\theta^{(k)\top} x^{(i)})}{\sum_{j=1}^K \exp(\theta^{(j)\top} x^{(i)})}\right]
\end{align}$$

Notice that this generalizes the logistic regression cost function, which could also have been written:

$$\begin{align}
J(\theta) = - \left[ \sum_{i=1}^m   (1-y^{(i)}) \log (1-h_\theta(x^{(i)})) + y^{(i)} \log h_\theta(x^{(i)}) \right] \\
= - \left[ \sum_{i=1}^{m} \sum_{k=0}^{1} 1\left\{y^{(i)} = k\right\} \log P(y^{(i)} = k | x^{(i)} ; \theta) \right]
\end{align}$$

The softmax cost function is similar, except that we now sum over the $K$ different possible values of the class label. 
Note also that in softmax regression, we have that

$
P(y^{(i)} = k | x^{(i)} ; \theta) = \frac{\exp(\theta^{(k)\top} x^{(i)})}{\sum_{j=1}^K \exp(\theta^{(j)\top} x^{(i)}) }
$

We cannot solve for the minimum of $J(\theta)$ analytically, and thus as usual we’ll resort to an 
iterative optimization algorithm. Taking derivatives, one can show that the gradient is:

$$
\begin{align}
\nabla_{\theta^{(k)}} J(\theta) = - \sum_{i=1}^{m}{ \left[ x^{(i)} \left( 1\{ y^{(i)} = k\}  - P(y^{(i)} = k | x^{(i)}; \theta) \right) \right]  }
\end{align}
$$

Recall the meaning of the 

$\nabla_{\theta^{(k)}}$ 

notation. In particular, 

$\nabla_{\theta^{(k)}} J(\theta)$ 

is itself a vector, so that its $j$-th element is 

$\frac{\partial J(\theta)}{\partial \theta_{lk}}$ 

the partial derivative of $J(\theta)$ with respect to the $j$-th 
element of $\theta^{(k)}$.

Armed with this formula for the derivative, one can then plug it into a standard optimization package 
and have it minimize $J(\theta)$.

---

##Properties of softmax regression parameterization

Softmax regression has an unusual property that it has a “redundant” set of parameters. 
To explain what this means, suppose we take each of our parameter vectors $\theta^{(j)}$, and subtract some 
fixed vector $\psi$ from it, so that every $\theta^{(j)}$ is now replaced with $\theta^{(j)} - \psi$ 
(for every $j=1, \ldots, k$). Our hypothesis now estimates the class label probabilities as


$$\begin{align}
P(y^{(i)} = k | x^{(i)} ; \theta)
= \frac{\exp((\theta^{(k)}-\psi)^\top x^{(i)})}{\sum_{j=1}^K \exp( (\theta^{(j)}-\psi)^\top x^{(i)})}  \\
= \frac{\exp(\theta^{(k)\top} x^{(i)}) \exp(-\psi^\top x^{(i)})}{\sum_{j=1}^K \exp(\theta^{(j)\top} x^{(i)}) \exp(-\psi^\top x^{(i)})} \\
= \frac{\exp(\theta^{(k)\top} x^{(i)})}{\sum_{j=1}^K \exp(\theta^{(j)\top} x^{(i)})}.
\end{align}$$

In other words, subtracting $\psi$ from every $\theta^{(j)}$ does not affect our hypothesis’ predictions at all! 
This shows that softmax regression’s parameters are “redundant.” More formally, we say that our softmax model 
is ”‘overparameterized,”’ meaning that for any hypothesis we might fit to the data, there are multiple parameter 
settings that give rise to exactly the same hypothesis function $h_\theta$ mapping from inputs $x$ to the predictions.

Further, if the cost function $J(\theta)$ is minimized by some setting of the parameters 
$(\theta^{(1)}, \theta^{(2)},\ldots, \theta^{(k)})$, then it is also minimized by 
$(\theta^{(1)} - \psi, \theta^{(2)} - \psi,\ldots,\theta^{(k)} - \psi)$ for any value 
of $\psi$. Thus, the minimizer of $J(\theta)$ is not unique. (Interestingly, $J(\theta)$ is 
still convex, and thus gradient descent will not run into local optima problems. But the Hessian is 
singular/non-invertible, which causes a straightforward implementation of Newton’s method to run into 
numerical problems.)

Notice also that by setting $\psi = \theta^{(K)}$, one can always replace $\theta^{(K)}$ with 
$\theta^{(K)} - \psi = \vec{0}$ (the vector of all 0’s), without affecting the hypothesis. 
Thus, one could “eliminate” the vector of parameters $\theta^{(K)}$ (or any other 
$\theta^{(k)}$, for any single value of $k$), without harming the representational power of our hypothesis. 
Indeed, rather than optimizing over the $K\cdot n$ parameters $(\theta^{(1)}, \theta^{(2)},\ldots, \theta^{(K)})$ 
(where $\theta^{(k)} \in \Re^{n}$), one can instead set $\theta^{(K)} = \vec{0}$ and optimize only with 
respect to the $K \cdot n$ remaining parameters.

---

##Relationship to Logistic regression

In the special case where $K = 2$, one can show that softmax regression reduces to logistic regression. 
This shows that softmax regression is a generalization of logistic regression. Concretely, 
when $K=2$, the softmax regression hypothesis outputs

$$\begin{align}
h_\theta(x) =

\frac{1}{ \exp(\theta^{(1)\top}x)  + \exp( \theta^{(2)\top} x^{(i)} ) }
\begin{bmatrix}
\exp( \theta^{(1)\top} x ) \\
\exp( \theta^{(2)\top} x )
\end{bmatrix}
\end{align}$$

Taking advantage of the fact that this hypothesis is overparameterized and setting $\psi = \theta^{(2)}$, 
we can subtract $\theta^{(2)}$ from each of the two parameters, giving us

$$\begin{align}
h(x) =

\frac{1}{ \exp( (\theta^{(1)}-\theta^{(2)})^\top x^{(i)} ) + \exp(\vec{0}^\top x) }
\begin{bmatrix}
\exp( (\theta^{(1)}-\theta^{(2)})^\top x )
\exp( \vec{0}^\top x ) \\
\end{bmatrix} \\

=
\begin{bmatrix}
\frac{1}{ 1 + \exp( (\theta^{(1)}-\theta^{(2)})^\top x^{(i)} ) } \\
\frac{\exp( (\theta^{(1)}-\theta^{(2)})^\top x )}{ 1 + \exp( (\theta^{(1)}-\theta^{(2)})^\top x^{(i)} ) }
\end{bmatrix} \\

=
\begin{bmatrix}
\frac{1}{ 1  + \exp( (\theta^{(1)}-\theta^{(2)})^\top x^{(i)} ) } \\
1 - \frac{1}{ 1  + \exp( (\theta^{(1)}-\theta^{(2)})^\top x^{(i)} ) } \\
\end{bmatrix}
\end{align}$$

Thus, replacing $\theta^{(2)}-\theta^{(1)}$ with a single parameter vector $\theta'$, 
we find that softmax regression predicts the probability of one of the classes as 
$\frac{1}{ 1  + \exp(- (\theta')^\top x^{(i)} ) }$, and that of the other class as 
$1 - \frac{1}{ 1 + \exp(- (\theta')^\top x^{(i)} ) }$, same as logistic regression.


