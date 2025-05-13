---
layout: default
title: Asan Chowk | microblog
permalink: /microblog
---
These are "micro"-posts too small and spontaneous to be regular blog posts.

<table class="table table-sm table-borderless">
  {% assign posts = site.data.microblog.micro2025.microposts | sort: 'date' | reverse %}
  {% for post in posts %}
    <tr>
      <td scope="row" class="date-width">{{ post.date | date: "%b %-d, %Y" }}</td>
        <td>
          {{post.post}}
        </td>
    </tr>
{% endfor %}
