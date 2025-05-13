---
layout: notebook
title: Markov Chains and Random walks
description:
nb_tag: randomwalks
last_modified_at: 2025-05-18
---
I love thinking about random walks and Markov Chains.

<b>Posts:<b>
{% for post in site.tags.randomwalks %}
<li>
<a href="{{ post.url }}">{{ post.date | date: '%Y %b %d' }}:    {{ post.title }}</a>
</li>
{% endfor %}

<br>
<b>Potential future posts may include:</b>
<ul>
<li>The multivariable calculus interpretation of the Laplacian matrix</li>
<li>Generating a uniform spanning tree using the Matrix Tree Theorem</li>
<li>Green's function</li>
</ul>
