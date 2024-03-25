---
layout: post
title: Neural Networks
description:
permalink: /notebooks/neuralnets.html
---
These posts are currently on the approximation error of neural networks for
different interesting but simple functions.

<br>
<b>Posts:<b>
{% for post in site.tags.neuralnets %}
<li>
<a href="{{ post.url }}">{{ post.date | date: '%Y %b %d' }}:    {{ post.title }}</a>
</li>
{% endfor %}

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<b>A wishlist of things I wish to learn and make posts about:</b>

The majority of the following will never become posts, but it is helpful for me
to have this list regardless.
<ul>
<li>Approximating f(x)=x^2</li>
</ul>
