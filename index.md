---
layout: default
title: Blog
---

<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{% if jekyll.environment == 'production' %}/blog/{% endif %}{{ post.url }}">{{ post.title }}</a></h2>
      <p>{{ post.excerpt }}</p>
    </li>
  {% endfor %}
</ul>