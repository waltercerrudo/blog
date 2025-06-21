---
layout: default
title: Artículos que NO son Jekyll ni Ruby
permalink: /categories/other/
categories: other
---
<h1>Artículos que NO son Jekyll ni Ruby</h1>
<ul>
{% for post in site.posts %}
  {% unless post.categories contains 'jekyll' or post.categories contains 'ruby' %}
    <li><a href="/blog{{ post.url }}">{{ post.title }}</a></li>
  {% endunless %}
{% endfor %}
</ul>