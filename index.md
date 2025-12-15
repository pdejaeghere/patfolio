---
title: Journal de bord
layout: math
nav_order: 0
---
# Journal de bord

{% for post in site.posts %}
  <div class="post-card">

    <h2>{{ post.title }}</h2>
    <p><em>{{ post.date | date: "%d/%m/%Y" }}</em></p>

    {% if post.summary %}
      <p>{{ post.summary }}</p>
      <a href="{{ post.url | relative_url }}">Suite…</a>

    {% else %}
      <p>{{ post.content }}</p>

      {% if post.link_page %}
        <a href="{{ post.link_page | relative_url }}">Suite...</a>
     
      {% endif %}

    {% endif %}

  </div>
{% endfor %}
