---
layout: post
title: "Linear Regression"
description: ""
category: "Mach"
tags: ["Machine Learning"]
---
{% include JB/setup %}

##Linear Regression

> In statistics, linear regression is an approach for modeling the
relationship between a scalar dependent variable $y$ and one or more
explanatory variable denoted $X$.

![Imgur](http://i.imgur.com/B9X1R7M.png)

In other words, we try to fit the data using a line.

$y = kx + b$

which can best represent the trainning data. We can write the function as
following:

$h(x) = \theta_0 + \theta_1x$

<!--more-->

Then we define a cost function, which normally the least square error function.

$CostFunction = \frac{1}{2m}\displaystyle\sum_{i=1}^m (h(x) - y)^2$

$m$ denotes the number of input instance, $h(x)$ denotes the 
linear function.$h(x) - y$ denotes a single error from an instance. So
the meaning of this cost function is simply **aggregation of errors**.

Then the task become **Minimize the Error Function**.

It is easy to notices that the $CostFunction$ is a quadratic function.
The graph of this function might looks like this:

![Imgur](http://i.imgur.com/HvKVK0z.gif)

We'd like to find the global minima (in this case there is one minima).

We might rewrite the $CostFunction$ in terms of two parameters $\theta_0$,
$\theta_1$.

$J(\theta_0, \theta_1) = \frac{1}{2m}\displaystyle\sum_{i = 1}^m(h(\theta_0,\theta_1) - y)^2$

The gradient descent works like this,

We first compute the partial derivative of $J(\theta_0, \theta_1)$, 

$\theta_0 = \theta_0 - \alpha\frac{\mathrm d}{\mathrm d x} J(\theta_0))$

$\theta_1 = \theta_1 - \alpha\frac{\mathrm d}{\mathrm d x} J(\theta_1))$

$\alpha$ stand for learning rate, which means moving a step forward towards
the local minima, if the learning rate is small, then the accuracy is high
but the iteration is large. If the learning rate is large. Then the accuracy
is decreasing because when it is close to local minima, it will bouncing 
around the local minima.

###Implementation

We use matrix multiplication as follows.

![Imgur](http://i.imgur.com/r8VOK6r.png)

$N \times 2$ Matrix $\times$ $2 \times 1$ Matrix

So we can use $vector$ representation

$h(\bar x_i) = \bar\theta \bar x_i$

$h(\bar x) = \bar\theta \bar x$

Go back to partial derivative:

$\theta_j = \theta_j - \alpha\frac{1}{m}\displaystyle\sum_{i = 1}^m(h(\bar x) - \bar y) \cdot \bar x$

where $j = 1,2$

This is R Implementation of gradient decent

    gradient_descent <- function(x, y, theta){
    	m <- length(y)
    		iterations <- 1500
    		learning_rate <- 0.01
    
    		for(i in 1:iterations){
    			temp <- (x %*% theta - y)
    				theta[1] <- theta[1] - learning_rate * (1 / m) * sum(temp)
    				theta[2] <- theta[2] - learning_rate * (1 / m) * sum(temp * x[, 2])
    				if(i %% 100 == 0){
    					abline(theta[1], theta[2], col = "red")
    				}
    		}
    	theta
    }
