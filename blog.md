---
layout: default
title: Blog
---

<h1>Blog Posts</h1>

<ul class="post-list">
  {% for post in site.posts %}
    <li>
      <h2>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </h2>
      <span class="post-date">{{ post.date | date: "%B %d, %Y" }}</span>
      {% if post.tags %}
        <span class="post-tags">
          {% for tag in post.tags %}
            <a href="/tags/{{ tag }}">{{ tag }}</a>{% unless forloop.last %}, {% endunless %}
          {% endfor %}
        </span>
      {% endif %}
      <p>{{ post.excerpt }}</p>
    </li>
  {% endfor %}
</ul>