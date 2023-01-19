---
layout: page
title: Blog Archive
order: 10
---

{% for tag in site.tags %}
  <h3>{{ tag[0] }}</h3>
  <ul>
    {% for post in tag[1] %}
      <li><span class="post-meta">{{ post.date | date: "%b %d, %Y" }} - </span>
      <a href="{{site.baseurl}}{{ post.url }}"> {{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}