---
layout: notebook
title: Neural Networks
description:
permalink: /notebooks/neuralnets
nb_tag: neuralnets
last_modified_at: 2024-03-30
---
These posts are currently on the approximation error of neural networks for
different interesting but simple functions.

###### Posts:
{% for post in site.tags.neuralnets %}
- <a href="{{ post.url }}">{{ post.date | date: '%Y %b %d' }}:    {{ post.title }}</a>
{% endfor %}

###### Interesting Links:
- <a href="https://mjt.cs.illinois.edu/dlt/">Telgarksky's deep learning theory course</a>
