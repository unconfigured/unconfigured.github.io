---
layout: default
title: Archive
---

<div>
{% capture year %}0{%endcapture%}
{% for post in site.posts %}
  {% if year != post.date | date: "%Y" %}{% capture year %}{{post.date | date: "%Y"}}{%endcapture%}
  </div><div class="post"><h2>{{ year }}</h2>
  {% endif %}
  <a href="{{post.url}}">{{ post.date | date: "%d.%m.%Y" }} - {{ post.title }}</a><br>
{% endfor %}
</div>
