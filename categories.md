---
layout: page
title: Categories
permalink: /categories/
---

<div class="categories-grid">
  {% for category in site.categories %}
    {% assign category_name = category[0] %}
    <div class="category-tile">
      <h2 class="category-title">{{ category_name | capitalize }}</h2>
      <ul class="category-posts">
        {% for post in site.categories[category_name] %}
          <li>
            <a href="{{ post.url }}">{{ post.title }}</a>
            <span class="post-date">{{ post.date | date: "%b %-d, %Y" }}</span>
          </li>
        {% endfor %}
      </ul>
    </div>
  {% endfor %}
</div>
