---
layout: default
title: Archive
---

{% capture year %}0{%endcapture%}
{% for post in site.posts %}
  <div class="post">
  {% if year != post.date | date: "%Y" %}
  {% capture year %}{{post.date | date: "%Y"}}{%endcapture%}
  <h2>{{ year }}</h2>
  {% endif %}
  <a href="{{post.url}}">{{ post.date | date: "%d.%m.%Y" }} - {{ post.title }}</a><br>
  </div>
{% endfor %}
