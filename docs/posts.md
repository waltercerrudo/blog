---
layout: default
title: Artículos
nav_order: 2
---

# Artículos

<div class="post-list" style="padding:0;">
  {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
  {% assign posts_asc = site.posts | sort: "date" | reverse %}
  {%- for post in posts_asc -%}
    <div style="margin-bottom:2.5em; list-style:none; background:#f9f9fb; border-radius:8px; box-shadow:0 2px 8px rgba(0,0,0,0.04); padding:1.5em;">
      <h3 style="margin-bottom:0.3em; font-size:1.6em; font-weight:700; color:#2d3748; letter-spacing:-0.5px;">
        <a class="post-link" href="{{ post.url | relative_url }}" style="text-decoration:none; color:inherit;">
          {{ post.title | escape }}
        </a>
      </h3>
      <span class="post-meta" style="display:block; font-size:1em; color:#6c757d; margin-bottom:1em; font-style:italic;">
        {{ post.date | date: date_format }}
      </span>
      <div style="display:flex; align-items:flex-start;">
        {% if post.image and post.image.path %}
          <img src="{{ site.baseurl }}{{ post.image.path }}" alt="{{ post.image.alt }}" style="max-width:250px; height:auto; margin-right:1.5em; border-radius:6px; box-shadow:0 1px 4px rgba(0,0,0,0.08);">
        {% endif %}
        <div style="flex:1; font-size:1.1em; color:#444; line-height:1.7;">
          {{ post.excerpt | markdownify }}
        </div>
      </div>
    </div>
  {%- endfor -%}
