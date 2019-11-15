---
layout: default
title: Blog
---
<div class="container">
<ul class="list-unstyled">
  {% for post in site.posts %}
    {% capture post_date %}{{ post.date }}{% endcapture %}
    <li>
      <h2><a href="{% if jekyll.environment == 'production' %}/blog{% endif %}{{ post.url }}">{{ post.title }}</a></h2>
      <p>{{ post.excerpt | strip_html }}</p>
      <hr>
    </li>
  {% endfor %}
</ul>
</div>
