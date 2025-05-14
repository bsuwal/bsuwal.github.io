---
layout: notebook
title: Markov Chains and Random walks
description:
nb_tag: randomwalks
permalink: /notebooks/randomwalks
last_modified_at: 2025-05-18
---
I love thinking about random walks and Markov Chains on discrete state spaces.

###### Posts:
{% for post in site.tags.randomwalks %}
<li>
<a href="{{ post.url }}">{{ post.date | date: '%Y %b %d' }}:    {{ post.title }}</a>
</li>
{% endfor %}

<br>
###### Potential future posts may include:
- The Laplacian Matrix
- Generating a uniform spanning tree using the Matrix Tree Theorem
- Green's function


###### To read / Interesting links:
- <a href="https://markov-chains.com/">Yuval Peres's course</a> on Markov Chains
