---
layout: default
title: Blog
permalink: /blog/
---

<h1 style="text-align: center;">Blog</h1>
<p class="subheading" style="text-align: center;">Excuse my infrequent updates, the Shakespeare in me likes his naps</p>

<!-- Search Bar -->
<div class="blog-search">
  <div class="search-wrapper full-width">
    <input type="text" id="searchInput" placeholder="Search tags or titles (e.g. technology, movies)">
    <button class="search-icon">
      <i class="fas fa-search"></i>
    </button>
  </div>
</div>

<!-- Blog List -->
<ul class="blog-list">
  {% for post in site.posts %}
    <li class="blog-preview" data-tags="{{ post.tags | join: ' ' }}">
      <a href="{{ post.url }}">
        <div class="title-row">
          <h2 class="blog-title">{{ post.title }}</h2>
          <span class="blog-meta">
            {{ post.date | date: "%b %d, %Y" }} &bull;
            {% assign words = post.content | number_of_words %}
            {% assign readtime = words | divided_by:200 %}
            {% if readtime < 1 %}
              &lt; 1 min read
            {% else %}
              {{ readtime }} min read
            {% endif %}
          </span>
        </div>

        <!-- Preview starts after marker -->
        {% assign parts = post.content | split: '<!-- start -->' %}
        <p class="blog-snippet">
          {{ parts[1] | strip_html | truncatewords: 30 }}
        </p>
      </a>

      <!-- Tag pills (clickable) -->
      <div class="tag-pills">
        {% for tag in post.tags %}
          <span class="pill tag-filter" data-tag="{{ tag }}">{{ tag }}</span>
        {% endfor %}
      </div>
    </li>
  {% endfor %}
</ul>

<!-- Blog Filter Script -->
<script>
  const input = document.getElementById("searchInput");
  const button = document.querySelector(".search-icon");
  const posts = document.querySelectorAll(".blog-preview");

  function filterPosts() {
    const query = input.value.toLowerCase();
    posts.forEach(post => {
      const text = post.innerText.toLowerCase();
      const tags = post.getAttribute("data-tags").toLowerCase();
      post.style.display = (text.includes(query) || tags.includes(query)) ? "block" : "none";
    });
  }

  input.addEventListener("input", filterPosts);
  button.addEventListener("click", filterPosts);

  // Clickable tag pills to auto-fill and filter
  document.querySelectorAll('.tag-filter').forEach(pill => {
    pill.addEventListener('click', function() {
      const tag = this.getAttribute('data-tag');
      input.value = tag;
      filterPosts();
    });
  });
</script>
