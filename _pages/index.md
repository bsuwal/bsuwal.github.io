---
layout: default
title: blog
permalink: /
pagination:
  enabled: true
  collection: posts
  permalink: /page/:num/
  per_page: 10
  sort_field: date
  sort_reverse: true
  trail:
    before: 1 # The number of links before the current page
    after: 3  # The number of links after the current page
---

<div class="post">

  <!-- <div class="header-bar">
    <h2>{{ site.blog_name }}</h2>
    <h2>{{ site.blog_description }}</h2>
  </div> -->

  <ul class="post-list">
    <table class="table table-sm table-borderless">

    {% for post in paginator.posts %}
    <tr>
      <th scope="row">{{ post.date | date: "%b %-d, %Y" }}</th>
      <td>
          <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </td>
      <td>
          {{ post.subtitle }}
      </td>
    </tr>
    <!-- <li>
      <h3>
        {% if post.redirect == blank %}
          <a class="post-title" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
        {% else %}
        <a class="post-title" href="{% if post.redirect contains '://' %}{{ post.redirect }}{% else %}{{ post.redirect | relative_url }}{% endif %}">{{ post.title }}</a>
        {% endif %}
      </h3> -->
      <!-- <p>{{ post.description }}</p> -->
      <!-- <p class="post-meta"> {{read_time}} min read &nbsp; &middot; &nbsp; -->
        <!-- {{ post.date | date: '%B %-d, %Y' }} -->
      <!-- </p> -->
      <!-- <p class="post-tags">
        <a href="{{ year | prepend: '/blog/' | prepend: site.baseurl}}">
          <i class="fas fa-calendar fa-sm"></i> {{ year }} </a>

          {% if tags != "" %}
          &nbsp; &middot; &nbsp;
            {% for tag in post.tags %}
            <a href="{{ tag | prepend: '/blog/tag/' | prepend: site.baseurl}}">
              <i class="fas fa-hashtag fa-sm"></i> {{ tag }}</a> &nbsp;
              {% endfor %}
          {% endif %}

          {% if categories != "" %}
          &nbsp; &middot; &nbsp;
            {% for category in post.categories %}
            <a href="{{ category | prepend: '/blog/category/' | prepend: site.baseurl}}">
              <i class="fas fa-tag fa-sm"></i> {{ category }}</a> &nbsp;
              {% endfor %}
          {% endif %}
    </p> -->
    <!-- </li> -->

    {% endfor %}
  </table>

  </ul>

  <!-- {% include pagination.html %} -->

</div>
