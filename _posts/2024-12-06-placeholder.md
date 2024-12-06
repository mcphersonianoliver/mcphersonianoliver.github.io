---
layout: post
title: Proximal Operators - Optimization Perspective 
date: 2024-12-06 16:40:16
description: placeholder
tags: optimization gradient-flows
categories: Optimization Foundations
toc:
  beginning: true
---
In many applications and domains, one can boil down the crux of a problem to one of optimization. For simplicity, assume we are optimizing a function $f: \mathbb{R}^d \rightarrow \mathbb{R}$ over $(\mathbb{R},\lVert \cdot \rVert_2)$ that has nice properties - for instance, convex, lower-semi continuous, etc. Without loss of generality, suppose we wish to minimize said function:

$$
  \min_{x \in \mathbb{R}^d} f(x).
$$

For exposition's sake, assume further that $f \in C^1(\mathbb{R}^d)$, then one can do a _gradient descent_ style algorithm. That is, starting from some initialization $x_0$, one obtains the sequence of iterates $\{x_n\}_{n \geq 0}$ in an iterative fashion:

$$
  x_{n+1} = x_{n} - \alpha_{n+1} \nabla f(x_n),
$$

where $\{\alpha_n\}_{n \geq 0}$ is a sequence of step-sizes. 

Because of the easy of statement, and the prevalence within many machine learning centric disciplines, gradient descent - and it's closely related optimization relatives - enjoys a lot of publicity and study. Serving also as a way of teaching student's how to prove different types of convergence rates, and how a function classes' characteristics effect the outcome, gradient descent style algorithms rightfully take much of the spotlight!

This being said, today I wanted to focus on the lesser known _proximal point method_ and the corresponding _proximal operator_. In some communities, where gradient descent is seen as _forward euler_, the natural foil is _backward euler_ - which is actually the _proximal point method_! If you have taken any _numerical analysis_ or _numerical PDEs_ course, it should come out no surprise that this method comes with many theoretical benefits. Beyond nice benefits regarding numerical stability, the proximal operator itself is of much interest for theoretical applications. The main theoretical application we wish to build towards is that of establishing the notion of a _gradient flow in 2-Wasserstein space_. Before leaving theory, we highlight how we may allow ourselves to change our geometric interpretation of _proximal_. By doing so, we can also make connections with general _regularization based ideas_ that often play a role in signal processing and statistical learning adjacent fields. Lastly, while these methods are generally impractical for general functions, we will highlight ideas for making them more computationally feasible - with a slight payment of using a surrogate for our functions of interest.

## Proximal Operator and Proximal Point Method
