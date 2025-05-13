---
layout: notebook
title: Neural Networks
description:
permalink: /notebooks/neuralnets.html
nb_tag: neuralnets
last_modified_at: 2024-03-30
---
These posts are currently on the approximation error of neural networks for
different interesting but simple functions.

<b>Posts:<b>
{% for post in site.tags.neuralnets %}
<li>
<a href="{{ post.url }}">{{ post.date | date: '%Y %b %d' }}:    {{ post.title }}</a>
</li>
{% endfor %}
