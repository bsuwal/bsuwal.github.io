---
layout: post
title: The Graph Laplacian of an undirected Graph
description: We discuss why an undirected graph still has the notion of a Graph Laplacian, which is still $L = D-A$ just like for a directed graph, even though the notions of gradient and divergence fundamentally require directed edges.
date: 2026-01-02
last_modified_at: 2026-01-02
permalink: /blog/graph-laplacians-undirected.html
tags: main trees probability randomwalks laplacian
---
In [the last post]({{ site.baseurl }}/graph-laplacians.html), we motivated how for a simple ***directed*** graph $G = (V, E)$ the graph Laplacian $L$ can be viewed as

$$
L = D - A
$$

where $D$ and $A$ are the degree and adjacency matrices of $G$.

Specifically, we interpreted the Laplacian as the divergence of the gradient of a function over the nodes of $G$. In doing so, the fact that the edges were directed was crucial for our definition of the gradient, which required the definition of the directional differences, which required a direction. It was also necessary for our notion of divergence, because the "net flow" outwards from a node was defined as the number of edges going out from the node minus the number of edges coming into the node. _Given how fundamental the need of a direction for the edges was to define $L$, can we find a define the Laplacian for an undirected graph?_

It does not seem to me that it is possible to write definitions of gradient and divergence without the notion of a directed edge. However, even a cursory look at the literature will reveal that the graph Laplacian _is_ defined for undirected graphs, and furthermore, it is the same as that for a directed graph: $L = D - A$. [^1] In this post we try to illuminate why this surprising fact makes sense, without betraying the direction-based machinery we built in the last post.

---
This is the statement we will work to convince ourselves of:

**Statement 1.** Let $G = (V, E)$ be an undirected graph, and $S$ be the set of all directed graphs $\vec{G} = (V, \vec{E})$ that induce $G$ as their undirected graph. Every $\vec{G} \in S$ has the same graph Laplacian $L = D - A$.

This proof sketch is built upon the following sequential arguments:
1. The Laplacian matrix $L = D - A$ exists for every directed graph $\vec{G}$.
2. Changing the direction of a single edge in $\vec{G}$ does not change $L$.
3. Any directed graph $\vec{G} \in S$ can be converted to $\vec{G'} \in A: \vec{G} \neq \vec{G'} $ in a finite number of single-edge direction change steps.

The first and third statements should not be controversial. We show an illustrating example why the second step is also true.[^2]

Consider the following two graphs, which are identical except for the direction of the edge $e_1$:

$G_1$             |  $G_2$
:-------------------------:|:-------------------------:
![]({{ site.url }}/assets/img/undirected_graph_laplacian/undirected_graph_laplacian_g1.png){: width="50%" }  |  ![]({{ site.url }}/assets/img/undirected_graph_laplacian/undirected_graph_laplacian_g2.png){: width="50%" }

We will write down the Laplacian of $G_1$ and $G_2$ as $L_1$ and $L_2$ respectively, factorized as the divergence of the gradient them both: [(see the last post for how to get this factorization).]({{ site.baseurl }}/graph-laplacians.html)

$$
L_1 =
\underset{div}{\begin{bmatrix}
1 & 0 & -1 \\
-1 & -1 & 0 \\
0 & 1 & 1
\end{bmatrix}}
\underset{\nabla}{\begin{bmatrix}
-1 & 1 & 0 \\
0 & 1 & -1 \\
1 & 0 & -1
\end{bmatrix}}
\begin{bmatrix}
f(v_1) \\
f(v_2) \\
f(v_3)
\end{bmatrix}
=
\begin{bmatrix}
1 \cdot -1 + \dots & 1 \cdot 1 + \dots & 1 \cdot 0 + \dots \\
-1 \cdot -1 + \dots & -1 \cdot 1 + \dots & -1 \cdot 0 + \dots \\
\dots & \dots & \dots
\end{bmatrix}
\begin{bmatrix}
f(v_1) \\
f(v_2) \\
f(v_3)
\end{bmatrix}
$$

$$
L_2 =
\underset{div}{\begin{bmatrix}
-1 & 0 & -1 \\
1 & -1 & 0 \\
0 & 1 & 1
\end{bmatrix}}
\underset{\nabla}{\begin{bmatrix}
1 & -1 & 0 \\
0 & 1 & -1 \\
1 & 0 & -1
\end{bmatrix}}
\begin{bmatrix}
f(v_1) \\
f(v_2) \\
f(v_3)
\end{bmatrix}
=
\begin{bmatrix}
-1 \cdot 1 + \dots & -1 \cdot -1 + \dots & -1 \cdot 0 + \dots \\
1 \cdot 1 + \dots & 1 \cdot -1 + \dots & 1 \cdot 0 + \dots \\
\dots & \dots & \dots
\end{bmatrix}
\begin{bmatrix}
f(v_1) \\
f(v_2) \\
f(v_3)
\end{bmatrix}
$$

You can see here that the elements of the resulting matrix remain the same. The change in the edge's direction results in a change in the gradient matrix, but it turns out that the corresponding change in the divergence matrix is such that when it is multiplied with the new gradient matrix the result is the same.

---
A corollary of this result is that given an undirected graph, we can ***arbitrarily***
assign direction to the edges, compute the gradients on the edges and then the divergences of those gradients, to get the Laplacian of that graph.

---
##### Footnotes:

[^1]: It is suggestive, and suspicious, that $L = D - A$ for directed graphs when both $D$ and $A$ do not have the direction of the edges encoded in them.

[^2]: Since our goal is more to facilitate understanding and develop intuition, we have chosen to provide an illuminating example instead of a proof.
