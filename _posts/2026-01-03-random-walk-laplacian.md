---
layout: post
title: The Random Walk Laplacian
description: We show how the random walk laplacian $L_{rw} = I - P$ is related to the Graph Laplacian $L = D - A$.
date: 2026-01-03
last_modified_at: 2026-01-03
permalink: /blog/rw-laplacian.html
tags: main trees probability randomwalks laplacian
---
In the previous posts we discussed the graph laplacian

$$
L = D - A
$$

where $D$ and $A$ are the degree and adjacency matrices respectively. The _random walk Laplacian_ however is expressed as

$$
L_{rw} = I - P
$$

where $P$ is the random-walk transition matrix on the graph.

While this may seem puzzling at first glance, $L_{rw}$ turns out to simply be $L$
normalized by the degrees of the nodes.

$$
\begin{aligned}
L_{rw}
&= D^{-1}L \\
&= D^{-1}(D - A) \\
&= D^{-1}D - D^{-1}A \\
&= I - P
\end{aligned}
$$

Some other properties about $L_{rw}$:
- $L_{rw}$ has the same eigenvectors as $P$. If $λ$ is an eigenvalue of $L_{rw}$, then $1 - λ$ is an eigenvalue of $P$:

$$
\begin{aligned}
λx &= L_{rw} x \\
&= (I - P)x \\
&= x - Px \\
Px &= x - λx \\
Px &= (1 - λ)x
\end{aligned}
$$

- The stationary distribution of $x$ is defined as $x = xP$. This can be now
rewritten as $xL_{rw} = 0$:

$$
\begin{aligned}
x &= xP \\
x - xP &= 0 \\
x(I-P) &= 0  \\
xL_{rw} &- 0
\end{aligned}
$$

- There is, unfortunately, no immediate relationship between the eigenvectors of
$L$ and $L_{rw}$. [(Relevant Math StackExchange)](https://math.stackexchange.com/questions/1846769/eigenvalues-of-product-of-a-matrix-with-a-diagonal-matrix)

This post is an elaboration of [a Math StackExchange answer by Misha Lavrov](https://math.stackexchange.com/questions/4174140/significance-of-the-random-walk-normalized-graph-laplacian).
