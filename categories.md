---
layout: page
title: Categories
permalink: /categories/
---

<div class="categories-grid">
  {% for category in site.categories %}
    {% assign category_name = category | first %}
    {% assign category_posts = category | last %}
    {% assign category_page = site.categories | where: 'category', category_name | first %}
    <a href="{{ category_page.url | relative_url }}" class="category-tile-link">
      <div class="category-tile">
        <h2 class="category-title">{{ category_name | capitalize }}</h2>
        <div class="post-count">
          {{ category_posts.size }} paper{% if category_posts.size != 1 %}s{% endif %}
        </div>
      </div>
    </a>
  {% endfor %}
</div>
