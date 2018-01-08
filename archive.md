---
layout: default
title: Archiv
---

{% set year = 1970 %}
{% for post in site.posts %}
  {% if year != post.date | date: "%Y" %}
  {% set year = post.date | date: "%Y" %}
  === {{ year }} ===
  {% endif %}
  {{ post.date | date: "%Y-%m-%d" }} - {{ page.title }}

{% endfor %}
