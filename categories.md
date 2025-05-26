---
layout: page
title: Categories
permalink: /categories/
---

{% assign categories = site.categories | sort %}

<div class="categories-grid">
  {% for category in categories %}
    {% assign category_name = category | first %}
    {% assign posts = site.categories[category_name] %}
    
    <div class="category-tile">
      <h2 class="category-title">{{ category_name | capitalize }}</h2>
      <div class="post-count">
        {{ posts.size }} paper{% if posts.size != 1 %}s{% endif %}
      </div>
      <a href="{{ '/categories/' | append: category_name | downcase | relative_url }}" class="category-link">
        View all
      </a>
    </div>
  {% endfor %}
</div>
