---
layout: post
title: Markov Chains and Random walks
description:
permalink: /notebooks/randomwalks.html
---
I love thinking about random walks and Markov Chains.

<b>Posts:<b>
{% for post in site.tags.randomwalks %}
<li>
<a href="{{ post.url }}">{{ post.date | date: '%Y %b %d' }}:    {{ post.title }}</a>
</li>
{% endfor %}

<br>
<b>A wishlist of things I wish to learn and make posts about:</b>
<ul>
<li>Laplacian matrix interpretation from multivariable calculus.</li>
<li>Generating a uniform spanning tree using the Matrix Tree Theorem</li>
<li>Green's function</li>
</ul>
