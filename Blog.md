---
layout: default
title: Blog
permalink: /blog/
---

<h1>Blog</h1>
<p class="subheading">Yeah this will probably remain dormant unless I have some kinda epiphany</p>

<ul>
  {% for post in site.posts %}
    <li><a href="{{ post.url }}">{{ post.title }}</a> — {{ post.date | date: "%B %d, %Y" }}</li>
  {% endfor %}
</ul>
