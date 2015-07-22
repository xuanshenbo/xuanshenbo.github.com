---
layout: post
title: "Discussion with Yi"
description: ""
category: "Mach"
tags: ["Machine Learning"]
---
{% include JB/setup %}

I had a nice discussion with Yi Mei last week.

Some important intuition was mentioned in the conversation:
1. Heuristic algorithm can be interpreter as a sampling process

![Imgur](http://i.imgur.com/VTC1wZ9.png)

We are basically sampling from the search space. 
Two main concerns, because there are many local minima, we have two criterions: 
1. Diversity
2. Convergence
We mainly want to keep the sampling diversity enough so that we 
don’t stuck at local minima(although it is inevitable because the 
global optimal is unknown). Meanwhile, we also want to quickly converge so that the algorithm runs fast.

2. It is hard to do theoretical over the heuristic algorithms, 
because it involve not only stochastic parameters but also highly depend on the test dataset(overfitting to the data).

But the most important fact is that it works, it works perfectly well and beyond what the most advanced math could do. Because so far the apply math could not really solve the complicated real world problems. Math always try to simplified problems until it can be solved but when it looks back, the problem is over simplified so that it becomes useless. 

On the other hand, heuristic algorithms does not have many concrete the theory. Basically what it does is sampling. Based on the simple assumption of affinity. The search space might not be completely discrete. However, because in the high dimensionality world, no algorithm could guarantee to find global minima. Everyone just care about find a reasonably good result in a feasible period of time. The heuristic algorithm does just that. 

Every “genetic operator” like mutation, crossover serves the two main criterions mentioned above. 

Crossover can be see as a convergence mechanism. Mutation can be see as a “jump out” mechanism that jump out the local minima and keep the population diverse enough.


So as we can’t really do theoretical study of heuristic algorithms. What we can do is sensitivity analysis which can be interpreted as:

1. intuition
2. empirical

Okay, so intuition comes from (might be) background knowledge or domain specific knowledge of the problem that you’re going to solve.

So, heuristic algorithm is just like other machine learning algorithms, you have to has more or less domain specific knowledge about the problem.

Empirical can be explained as, when we don’t have such intuition, maybe we don’t really know what kind of parameter will do well in this kind of data or problem. What we can do is basically try.

It kinds make the study an experimental study. That’s kind of strange in terms of computer science because there is no guarantee about the results where in computer science, most of things are deterministic.

---

First we make a convergence graph so that it is easy for us to analyze the behavior of the heuristic algorithm. It allows us easily compare between different algorithms and see if they are stuck at local minima.

The phenotype-genotype redundancy problem seems an issue. Which should be considered as the main problem with the current algorithm.

---

For the NSGA-II initialization,  because adding an instance could potentially drag the population toward to this instance, therefore, it still tend to cause the population “not” diversity enough. Because when the population starts to move towards this instance, they already miss the chance to go the opposite way where might exist better solutions. Therefore, one of the important measure is convergence. 

![Imgur](http://i.imgur.com/9Zedvtd.png)

Maybe the NSGA-II with initialization would be fast at first, because adding an instance would accelerate the convergence. But after a certain generations, because NSGA-II does not really moving towards any direction, it is less likely to stuck at same local minimum, so it could find better solutions. 

Therefore, as we analyse the convergence, we will confident to claim whether our algorithm is better than the original in both time efficiency and solution quality. 

So there are mainly two convergence measurements that everyone in the field would do:

1. Inverted generational Distance (IGP)
2. Hypervolume

Both are try to measure the quality of the Pareto front in terms of diversity and convergence.

---
Discussion about Memetic search
The basic idea is doing local search when there is a local minima found. 

Therefore, we could apply local search over (maybe) 5% top results.
This kind of idea could accelerate the convergence as well as does not affect diversity. If we apply incremental fitness function evaluation, the cost of local search is actually small. It seems like a quite reasonable thing to do. 

---

Discussion about:
1. Constructive Heuristic:
  + greedy
  + …
2. Meta-heuristic: like a superset of constructive heuristic
  + PSO
3. Hyper-heuristic
  + automatically decide of what meta-heuristic algorithm to use

The above is for the NSGA-II.
Now the PSO issue, because of the phenotype and genotype mapping issue. It potentially waste some computation power therefore the continuous PSO can be improved. The first thing we might do is observed the results from every generation, which we would see how much computation power is actually wasted. 

Because it is mainly a representation issue, the most straightforward solution is use a binary algorithm to solve this problem. Therefore, we are going to use binary PSO. So far we compared two multi-objective algorithms Multi-objective PSO and NSGA-II, but we don’t have a single-objective algorithm to compare with.  

We can also do convergence study on multi-objective PSO, see if it fast convergence. 

---

So basically, there are two things to do this tri:

1. Continue doing evaluation of the current algorithm by analysing the convergence.
2. Develop a single-objective binary PSO and imply on this problem.

Some new idea about the project or general heuristic algorithms.

Basic idea is, we are developing algorithms that applied on specific dataset, which is overfitting. Can we do generalization on the dataset first and apply algorithm on the generalization dataset, therefore, it kinds of prove the algorithm works well in this kind of problem without huge modification. 

By applying generalization over dataset, I mean maybe we can apply clustering algorithm (e.g., EM) over the dataset and try to make an assumptions over the dataset says: the dataset is constructed by several  gaussian distribution. Maybe we can construct fake test dataset by randomly generate from these distributions. So that we can make a claim that our algorithm does not overfitting to a specific dataset.

