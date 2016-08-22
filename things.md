---
layout: default
---

A complete list of things I've done with computers, including apps, side projects, amongst other things.

Still a work in progress!

{% for thing in site.things %}
  <h2 class='alt'>{{ thing.title }} <small>{{ thing.date | date: "%B %-d, %Y" }}</small></h2>
  <p class='alt'>{{thing.subtitle}}</p>
  <hr>
{% endfor %}