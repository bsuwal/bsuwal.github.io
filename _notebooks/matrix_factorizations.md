---
layout: notebook
title: Matrix Factorization
description:
permalink: /notebooks/matrix_factorization
nb_tag: matrix_factorization
last_modified_at: 2025-05-03
---
We wish to write a series of blog posts on the different ways one can factorize a matrix.

The goal is to describe how to interpret these matrix decompositions when possible
discuss the numerical stability of the algorithms used to generate them.

<b>Posts:<b>
{% for post in site.tags.matrix_factorization %}
<li>
<a href="{{ post.url }}">{{ post.date | date: '%Y %b %d' }}:    {{ post.title }}</a>
</li>
{% endfor %}
---

We wish to hopefully cover the following factorizations in future posts:
<ol>
<li> The LU decomposition </li>
<li> Eigendecomposition </li>
<li> SVD </li>
<li> The QR decomposition </li>
<li> Cholesky decomposition </li>
</ol>

**Reading list:**

* [This paper](https://math.mit.edu/~gs/everyone/lucrweb.pdf) describes a $A = CW^{-1}B$
factorization that it calls "magic".
* [Nick Hingham's "What is" series of blogposts](https://nhigham.com/index-of-what-is-articles/) seem like an incredible resource.
