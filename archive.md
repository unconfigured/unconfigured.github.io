---
layout: default
title: Archiv
---

{% capture year %}0{%endcapture%}
{% for post in site.posts %}
  {% if year != post.date | date: "%Y" %}
  {% capture year %}{{post.date | date: "%Y"}}{%endcapture%}
  <h1>{{ year }}</h1>
  {% endif %}
  {{ post.date | date: "%Y-%m-%d" }} - {{ post.title }}<br>
{% endfor %}
