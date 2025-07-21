---
layout: page
title: News
permalink: /news/
---

{% for news in site.news %}
  <h2><a href="{{ news.url }}">{{ news.title }}</a></h2>
  <p>{{ news.excerpt }}</p>
{% endfor %}

