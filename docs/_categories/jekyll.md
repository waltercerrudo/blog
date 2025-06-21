---
layout: default
title: Artículos en Jekyll
permalink: /blog/categories/jekyll/
categories: jekyll
---
<h1>Artículos en Jekyll</h1>
<ul>
{% for post in site.posts %}
  {% if post.categories contains 'jekyll' %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endif %}
{% endfor %}
</ul>