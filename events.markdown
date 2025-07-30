---
layout: page
title: Events
permalink: /events/
---

{% assign events = site.events | sort: 'date' %}

<ul>
  {% for event in events %}
    <li><a href="{{ event.url }}">{{ event.title }}</a></li>
    <p> {{event.summary}} </p>
  {% endfor %}
</ul>

