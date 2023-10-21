---
layout: post
title: Random walks and Spanning Trees
description:
permalink: /notebooks/trees.html
---
My notes on things about random walks or spanning trees, or uses of random walks to generate spanning trees.

<br><br><br>
<b>Posts:<b>
{% for post in site.tags.trees %}
<li>
<a href="{{ post.url }}">{{ post.date | date: '%Y %b %d' }}:    {{ post.title }}</a>
</li>
{% endfor %}



<br><br><br>
<b>A wishlist of future potential posts:<b>
<ul>
<li>Cayley's formula</li>
<li>Matrix Tree Theorem</li>
<li>Generating a uniform spanning tree using the Matrix Tree Theorem</li>
</ul>
