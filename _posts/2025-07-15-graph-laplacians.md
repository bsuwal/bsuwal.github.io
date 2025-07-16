---
layout: post
title: The Graph Laplacian
description: We try to develop an intuitive understanding of the Graph Laplacian, and elucidate connections to the Laplacian of a function in a continuous setting.
date: 2025-07-15
last_modified_at: 2025-07-16
permalink: /blog/graph-laplacians.html
tags: trees probability randomwalks main laplacian
---
[The main body of this write-up is a pdf linked here.]({{ site.url }}/assets/docs/laplacians.pdf)

I have long wanted to get an understanding of the graph Laplacian that pops up across the computer science and mathematics literature. The Laplacian of a function isa a widely used tool that captures fundamental properties of a (twice-differential) function and among other things conveys the (net) convexity of a function. I especially wanted to understand how the definitions of the Laplacian of a function in a continuous setting, like

$$
\Delta f = \sum_{i=1}^n \frac{\partial^2}{\partial x_i^2} f
$$

get translated into the discrete setting of a graph to look like

$$
L = D - A
$$

I have in this post put in my best effort to make this translation.

En route I:
* Present the definition of the Laplacian of a continuous function. I interpret it as the divergence of the gradient of a function, and also present those definitions.
* Describe how the graph setting is a discretization of the continuous function setting.
* Present the analogous definitions of the gradient and the divergence in the graph setting.
* Discuss how the graph setting is a generalization of the continuous setting. This is particularly not obvious to the first time learner, I think. More specifically, the continuous setting is the sum of second derivatives of a function. Because the notion of the first derivative in a graph is a function over the edges and the second derivative is a function over the edges, you cannot apply the same derivative function twice.
* Work through an example to show how $L = KK^T = D - A$ in the graph setting, where $K$, $D$ and $A$ are the incidence, degree and adjacency matrices respectively.
* Explain the arbitrary reason behind why the one sees the Laplacian with a positive or negative sign across the literature, i.e one might see it as $\Delta f = \sum_{i=1}^n \frac{\partial^2}{\partial x_i^2} f$ or $\Delta f = -\sum_{i=1}^n \frac{\partial^2}{\partial x_i^2} f$. (It depends on how you take the sign of the gradient. Our example actually results in $L = A-D$.)

Here are some other resources that I found helpful writing about this post:
* [Matthew N. Bernstein's blog post.](https://mbernste.github.io/posts/laplacian_matrix/)
* [This MathOverflow post](https://mathoverflow.net/questions/368963/intuitively-what-does-a-graph-laplacian-represent)
* [Keenan Crane's lecture on the Laplacian](https://www.youtube.com/watch?v=oEq9ROl9Umk&ab_channel=KeenanCrane)
* [Justin Solomon's lectures on the Laplacian](https://www.youtube.com/playlist?list=PLQ3UicqQtfNtHHgJRhkuBl3tzRdqeWUL9)
* [Delio Mugnolo's monograph](https://www.uni-ulm.de/fileadmin/website_uni_ulm/mawi.inst.010/mugnolo/springer.pdf)
