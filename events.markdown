---
layout: page
title: Events
permalink: /events/
---

{% assign events = site.events | sort: 'date' %}

<ul>
  {% for event in events %}
    <div>
    {{event.date  | date: '%B %d, %Y' }}<br/>
    <a href="{{ event.url }}">{{ event.title }}</a><br/>
    {{event.summary}}
    </div>
  {% endfor %}
</ul>

