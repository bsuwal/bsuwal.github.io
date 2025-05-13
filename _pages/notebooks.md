---
layout: default
title: Asan Chowk | notebooks
permalink: /notebooks.html
---
These notebooks are just that - notebooks. They might be reading lists, groups of posts that I have written, or whatever.

<div class="post">
  <ul class="post-list">
    <table class="table table-sm table-borderless">
        {% for notebook in site.notebooks %}
        <tr>

            {% assign tagged_posts = site.tags.main | where: "tags", notebook.nb_tag %}
            {% assign sorted_tagged_posts = tagged_posts | sort: "last_modified_at" | reverse %}
            {% assign post = sorted_tagged_posts[0] %}

            <td>
              <a class="post-link" href="{{ notebook.url | relative_url }}"><b> {{ notebook.title }} </b> </a><br>
            </td>
            <td scope="row">
              <!-- {% assign last_update = post.last_modified_at | at_least: 2 %} -->
              {% if post.last_modified_at > notebook.last_modified_at %}
                  {% assign last_update = post.last_modified_at %}
              {% else %}
                  {% assign last_update = notebook.last_modified_at %}
              {% endif %}
              <i>Last updated: {{ last_update | date: "%b %-d, %Y" }} </i>
            </td>
        </tr>
    {% endfor %}
  </table>
  </ul>
</div>
