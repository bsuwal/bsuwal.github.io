---
layout: default
title: Asan Chowk | notebooks
permalink: /notebooks
---
These notebooks are just that - notebooks. They might be reading lists, groups of posts that I have written, or whatever.

{% comment %}
  Liquid can't sort an array by a computed value directly, so for each notebook
  we build a "sortable_date::permalink" string, sort those strings (descending),
  then look each notebook back up by its permalink in that order.
{% endcomment %}
{% assign sort_keys = "" | split: "" %}
{% for notebook in site.notebooks %}
  {% assign tagged_posts = site.tags.main | where: "tags", notebook.nb_tag %}
  {% assign sorted_tagged_posts = tagged_posts | sort: "last_modified_at" | reverse %}
  {% assign post = sorted_tagged_posts[0] %}
  {% if post.last_modified_at > notebook.last_modified_at %}
      {% assign last_update = post.last_modified_at %}
  {% else %}
      {% assign last_update = notebook.last_modified_at %}
  {% endif %}
  {% assign sort_key = last_update | date: "%Y-%m-%dT%H:%M:%S" | append: "::" | append: notebook.permalink %}
  {% assign sort_keys = sort_keys | push: sort_key %}
{% endfor %}
{% assign sorted_keys = sort_keys | sort | reverse %}

<div class="post">
  <ul class="post-list">
    <table class="table table-sm table-borderless">
        {% for key in sorted_keys %}
        {% assign notebook_permalink = key | split: "::" | last %}
        {% assign notebook = site.notebooks | where: "permalink", notebook_permalink | first %}
        <tr>

            {% assign tagged_posts = site.tags.main | where: "tags", notebook.nb_tag %}
            {% assign sorted_tagged_posts = tagged_posts | sort: "last_modified_at" | reverse %}
            {% assign post = sorted_tagged_posts[0] %}

            <td>
              <a class="post-link" href="{{ notebook.url | relative_url }}"><b> {{ notebook.title }} </b> </a><br>
            </td>
            <td scope="row">
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
