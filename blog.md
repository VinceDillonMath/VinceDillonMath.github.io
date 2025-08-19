---
layout: default
title: Blog
---

# Blog

Here, I'll post some very short (possibly handwavy) blog posts about things I'm interested in.

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a> — {{ post.date | date: "%B %d, %Y" }}
    </li>
  {% endfor %}
</ul>
