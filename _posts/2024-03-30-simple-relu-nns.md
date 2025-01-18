---
layout: post
title: ReLu NNs to compute some basic functions
description: We construct ReLu NNs that that compute the addition, maximum and absolute value functions.
date: 2024-03-30
permalink: /blog/simple_nns.html
tags: neuralnets main
---
This post will construct some tiny neural networks that compute some well known functions. We will be using the popular ReLu activation function:

$$
   σ(x) = \max\{x, 0\}
$$

for $x \in \mathbb{R}$.

### Addition
Let us start with a super simple function, one that adds two numbers:

$$
f(x_1, x_2) = x_1 + x_2
$$

for $x_1, x_2 \in \mathbb{R}$.

The following neural network performs this operation.

$$
\begin{bmatrix}
1 & 1
\end{bmatrix}
\begin{bmatrix}
x_1 \\
x_2
\end{bmatrix}
$$

We are now on our way to make more complicated functions.

### Absolute value function
We now try to compute

$$
   f(x) = |x|
$$

for $x \in \R$.

We first observe that

\begin{aligned}
   |x| &= σ(x) + σ(-x)
\end{aligned}
