---
layout: page
title: Computing Barycenters on Wasserstein Submanifolds
description: Given only partial information of our submanifold, can we still find barycenters?
img: 
importance: 1
category: work
related_publications: true
---

Within statistics, the first statistical task one wants to be able to carry out when given a finite sample is to take the **empirical average**. To be precise, consider the setting where we are given $$(x_i)_{i \in [n]} \subseteq (\mathbb{R}^d, \lVert \cdot \rVert_2)$$ sampled according to some unknown distribution. Then, the sample mean can be explicitly computed as follows:

$$ 
    \hat{\mu}_n := \frac{1}{n} \sum_{i=1}^n x_i.
$$

This form actually implicitly codifies the _center of mass_. To see this explicitly, we note that this actually is the minimizer for the following variational problem - by simply looking at first order optimality conditions:

$$ 
    \operatorname{argmin}_{x \in \mathbb{R}^d} \frac{1}{2n} \sum_{i=1}^n \lVert x - x_i \rVert^2. 
$$

This variational problem gives us the potential energy that comes from comparing a point with the point cloud that is given by $$(x_i)_{i \in [n]}$$. Naturally, one can state the above variational problem to more general spaces, by simply replacing the Euclidean distance with some other distance metric. However, the problem with changing the space is that we no longer are guaranteed the nice explicit form of the sample mean. 

**The point: to find the center of mass in non-Euclidean settings, we need to appeal to non-Euclidean first-order optimization ideas.**
