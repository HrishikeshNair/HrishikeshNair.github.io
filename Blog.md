---
layout: default
title: Blog
permalink: /blog/
---

<h1>Blog</h1>
<p class="subheading">Excuse my infrequent updates, the Shakespeare in me likes his naps</p>

<ul>
  {% for post in site.posts %}
    <li><a href="{{ post.url }}">{{ post.title }}</a> — {{ post.date | date: "%B %d, %Y" }}</li>
  {% endfor %}
</ul>
