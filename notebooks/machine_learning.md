---
layout: post
title: Machine Learning
description:
permalink: /notebooks/ml.html
---
I guess I am interested in machine learning now.

<br>
<b>Posts:<b>
{% for post in site.tags.learning %}
<li>
<a href="{{ post.url }}">{{ post.date | date: '%Y %b %d' }}:    {{ post.title }}</a>
</li>
{% endfor %}
