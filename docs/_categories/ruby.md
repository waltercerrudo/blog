---
layout: default
title: Artículos en Jekyll
permalink: /categories/ruby/
categories: ruby
---
<h1>Artículos en Ruby</h1>
<ul>
{% for post in site.posts %}
  {% if post.categories contains 'jekyll' %}
    <li><a href="/blog/{{ post }}">{{ post.title }}</a></li>
  {% endif %}
{% endfor %}
</ul>