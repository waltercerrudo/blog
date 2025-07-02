---
layout: default
title: Artículos
nav_order: 2
---

<div class="post-list">
  {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
  {% assign posts_asc = site.posts | sort: "date" | reverse %}
  {%- for post in posts_asc -%}
    <div class="post-card">
      <h3>
        <a class="post-link" href="{{ post.url | relative_url }}" >
          {{ post.title | escape }}
        </a>
      </h3>
      <span class="post-author">
        by {{ post.author | default: "Autor desconocido" }}
      </span>
      <span class="post-meta">
        {{ post.date | date: date_format }}
      </span>
      <div class="post-img">
        {% if post.image and post.image.path %}
          <img src="{{ site.baseurl }}{{ post.image.path }}" alt="{{ post.image.alt }}">
        {% endif %}
        <div class="post-excerpt">
          {{ post.excerpt | markdownify }}
        </div>
      </div>
    </div>
  {%- endfor -%}
