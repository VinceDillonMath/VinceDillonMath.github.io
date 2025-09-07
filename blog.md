---
layout: default
title: Blog
---

<h1>Blog</h1>

<div class="blog-list">
  {% for post in site.posts %}
    <div class="blog-card">
      {% if post.thumbnail %}
        <a href="{{ post.url }}">
          <img src="{{ post.thumbnail }}" alt="Thumbnail for {{ post.title }}" class="blog-thumb">
        </a>
      {% endif %}

      <div class="blog-info">
        <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
        <p class="blog-date">{{ post.date | date: "%B %d, %Y" }}</p>
        <p class="blog-excerpt">
          {% if post.excerpt %}
            {{ post.excerpt }}
          {% else %}
            {{ post.content | strip_html | truncate: 150 }}
          {% endif %}
        </p>
      </div>
    </div>
  {% endfor %}
</div>
