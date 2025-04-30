---
layout: page
title: Blog
permalink: /blog/
---

<div class="blog-posts">
  {% for post in site.posts %}
    <article class="post">
      <header class="post-header">
        <h2 class="post-title">
          <a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
        </h2>
        <p class="post-meta">
          <time datetime="{{ post.date | date_to_xmlschema }}">
            {{ post.date | date: "%b %-d, %Y" }}
          </time>
          {% if post.author %}
            • <span>{{ post.author }}</span>
          {% endif %}
        </p>
      </header>

      <div class="post-content">
        {{ post.excerpt | strip_html | truncatewords: 50 }}
        <a href="{{ post.url | relative_url }}" class="read-more">Read more</a>
      </div>
    </article>
  {% endfor %}
</div> 