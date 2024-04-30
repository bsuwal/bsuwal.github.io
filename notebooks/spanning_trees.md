---
layout: post
title: Random walks and Uniform Spanning Trees
description:
permalink: /notebooks/trees.html
---
I love thinking about random walks on graphs, and using them to generate uniform spanning trees.

<br>
<b>Posts:<b>
{% for post in site.tags.trees %}
<li>
<a href="{{ post.url }}">{{ post.date | date: '%Y %b %d' }}:    {{ post.title }}</a>
</li>
{% endfor %}

<br>
<br>
<b>A wishlist of things I wish to learn and make posts about:</b>

The majority of the following will never become posts, but it is helpful for me
to have this list regardless.
<ul>
<li>Laplacian matrix interpretation from multivariable calculus.</li>
<li>Generating a uniform spanning tree using the Matrix Tree Theorem</li>
<li>Green's function</li>
</ul>
