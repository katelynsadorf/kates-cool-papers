---
layout: page
title: Categories
permalink: /categories/
---

<p>Debug Info:</p>
<p>Categories Collection Size: {{ site.collections.categories.docs | size }}</p>
<p>Categories Hash Keys: {{ site.categories | keys | join: ", " }}</p>

<div class="categories-grid">
  {% for category in site.categories %}
    {% assign category_name = category[0] %}
    {% assign posts = category[1] %}
    
    {% comment %} Find the category page to get the title {% endcomment %}
    {% assign category_page = nil %}
    {% for doc in site.categories.docs %}
      {% if doc.category == category_name %}
        {% assign category_page = doc %}
        {% break %}
      {% endif %}
    {% endfor %}
    
    <a href="{{ '/categories/' | append: category_name | downcase | relative_url }}" class="category-tile-link">
      <div class="category-tile">
        <h2 class="category-title">
          {% if category_page %}
            {{ category_page.title }}
          {% else %}
            {{ category_name | capitalize }}
          {% endif %}
        </h2>
        <div class="post-count">
          {{ posts.size }} paper{% if posts.size != 1 %}s{% endif %}
        </div>
      </div>
    </a>
  {% endfor %}
</div>
