---
layout: default
title: Writing
permalink: /writing/
---

<section class="writing-header">
    <div class="container">
        <h1>Writing</h1>
        <p>Articles, blog posts, and thoughts on technology, blockchain, and digital marketing.</p>
    </div>
</section>

<section class="writing-content">
    <div class="container">
        <div class="categories">
            <h2>Categories</h2>
            <div class="category-list">
                {% assign categories = site.categories | sort %}
                {% for category in categories %}
                <a href="{{ '/categories/' | relative_url }}{{ category[0] | slugify }}" class="category-link">
                    {{ category[0] | capitalize }}
                    <span class="post-count">({{ category[1] | size }})</span>
                </a>
                {% endfor %}
            </div>
        </div>

        <div class="posts-list">
            {% for post in site.posts %}
            <article class="post-item">
                <div class="post-content">
                    <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
                    <div class="post-meta">
                        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %-d, %Y" }}</time>
                        {% if post.categories.size > 0 %}
                        <span class="post-categories">
                            {% for category in post.categories %}
                            <a href="{{ '/categories/' | relative_url }}{{ category | slugify }}">{{ category }}</a>
                            {% unless forloop.last %}, {% endunless %}
                            {% endfor %}
                        </span>
                        {% endif %}
                    </div>
                    <p class="post-excerpt">{{ post.excerpt | strip_html | truncatewords: 50 }}</p>
                    <a href="{{ post.url | relative_url }}" class="read-more">Read more →</a>
                </div>
            </article>
            {% endfor %}
        </div>
    </div>
</section> 