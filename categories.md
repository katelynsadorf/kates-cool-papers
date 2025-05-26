---
layout: page
title: Categories
permalink: /categories/
---

<div class="categories-grid">
  {% comment %}
    Iterate through documents in the 'categories' collection (files in _categories folder).
    Each 'cat_doc' is a page like _categories/bci.md.
  {% endcomment %}
  {% for cat_doc in site.collections.categories.docs %}
    {% assign fm_category = cat_doc.data.category %}   {% comment %} e.g., "bci" from bci.md frontmatter {% endcomment %}
    {% assign fm_title = cat_doc.data.title %}         {% comment %} e.g., "BCI (Brain-Computer Interfaces)" {% endcomment %}
    
    {% comment %} Count actual posts that belong to this category {% endcomment %}
    {% assign count = 0 %}
    {% for post in site.posts %}
      {% if post.categories contains fm_category %}
        {% assign count = count | plus: 1 %}
      {% endif %}
    {% endfor %}

    <a href="{{ cat_doc.url | relative_url }}" class="category-tile-link">
      <div class="category-tile">
        <h2 class="category-title">{{ fm_title }}</h2> {# Use title from _categories/xxx.md frontmatter #}
        <div class="post-count">
          {{ count }} paper{% if count != 1 %}s{% endif %}
        </div>
      </div>
    </a>
  {% endfor %}
</div>
