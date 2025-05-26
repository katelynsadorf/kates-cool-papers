---
layout: page
title: Categories
permalink: /categories/
---

<div class="categories-grid">
  {% for category in site.categories %}
    {% assign category_name = category | first %}
    {% assign posts = category[1] %}
    
    <a href="{{ '/categories/' | append: category_name | downcase | relative_url }}" class="category-tile-link">
      <div class="category-tile">
        <h2 class="category-title">{{ category_name | capitalize }}</h2>
        <div class="post-count">
          {% assign count = 0 %}
          {% for post in site.posts %}
            {% if post.categories contains category_name %}
              {% assign count = count | plus: 1 %}
            {% endif %}
          {% endfor %}
          {{ count }} paper{% if count != 1 %}s{% endif %}
        </div>
      </div>
    </a>
  {% endfor %}
</div>
