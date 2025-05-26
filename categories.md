---
layout: page
title: Categories
permalink: /categories/
---

<div class="categories-grid">
  {% for category in site.categories %}
    {% assign category_name = category[0] %}
    <a href="/categories/{{ category_name | slugify }}" class="category-tile-link">
      <div class="category-tile">
        <h2 class="category-title">{{ category_name | capitalize }}</h2>
        <div class="post-count">{{ site.categories[category_name].size }} paper{% if site.categories[category_name].size != 1 %}s{% endif %}</div>
      </div>
    </a>
  {% endfor %}
</div>
