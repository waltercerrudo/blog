---
layout: default
title: Artículos en Publicar
permalink: /categories/publicar/
categories: publicar
---
<h1>Artículos en Publicar</h1>
<ul>
{% for post in site.posts %}
  {% if post.categories contains 'publicar' %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endif %}
{% endfor %}
</ul>
