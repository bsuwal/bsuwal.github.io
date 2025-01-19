---
layout: notebook
title: Langur Burja (लंगुर बुर्जा)
description:
permalink: /notebooks/langur_burja.html
---
The following are posts about the popular board game Langur Burja, played in the hills of Nepal. I used to see people play it on the street near my home in Bhaktapur during Dashain, but I must have been sixteen when I played it myself for the first time myself when Thulo Mommy brought it for Bhai Tika.

| ![center-img]({{ site.url }}/assets/img/langur_burja/dice.png) |
|:--:|
| *I bought this set of beautiful handmade Langur Burja dice in Somerville(!) in Oct 2024.* |

The game can be pretty chaotic (and fun) to play in large groups. <a href="https://www.youtube.com/watch?v=7rjMdz5ZgCU">This</a>, <a href="https://www.youtube.com/watch?v=ME-Tt0exl6Y">this</a> and <a href="https://www.youtube.com/watch?v=neisLVv9Tg4">this</a> are some YouTube videos of Langur Burja being played during Dashain in Nepal.

The Julia code used to generate the plots <a href="https://github.com/bsuwal/langur_burja">is linked here</a>. 

<b>Posts:<b>
{% for post in site.tags.langur_burja %}
<li>
<a href="{{ post.url }}">{{ post.date | date: '%Y %b %d' }}:    {{ post.title }}</a>
</li>
{% endfor %}
---

In future posts we wish to study the canonical Langur Burja game (6 symbols, 6 dice) more. Some questions we wish to answer are
<ol>
<li>It is folklore knowledge that to win at Langur Burja you need to consistently make small bets across the board. We suspect that this must be false, but could we show it (or the converse) explicitly?</li>
<li>How does the effect of having multiple players who bet across the board affect the House's winnings?</li>
</ol>
