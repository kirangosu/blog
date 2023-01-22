---
layout: page
title: Blog Archive
order: 10
---

<h3>All Posts</h3>
{% for post in site.posts %}
  <ul class="post-list">
    <li>
      <span class="post-meta">{{ post.date | date: "%b %d, %Y" }}</span>
      <a class="post-link" href="{{site.baseurl}}{{post.url}}"> {{post.title}} </a>
      <span class="post-excerpt"> {{ post.excerpt }}</span>
    </li>
  </ul>
{% endfor %}

<hr />

<h3>Tags</h3>
{% for tag in site.tags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}

<div class="post-link">{{ t | downcase }}</div>
<ul>
{% for post in posts %}
  {% if post.tags contains t %}
  <li>
    <a href="{{site.baseurl}}{{ post.url }}">{{ post.title }}</a>
    <span class="post-meta">{{ post.date | date: "%b %d, %Y" }}</span>
  </li>
  {% endif %}
{% endfor %}
</ul>
{% endfor %}

<!-- {% for tag in site.tags %}
  <h3>{{ tag[0] }}</h3>
  <ul>
    {% for post in tag[1] %}
      <li>
        <a href="{{site.baseurl}}{{ post.url }}"> {{ post.title }}</a>
        <span class="post-meta">{{ post.date | date: "%b %d, %Y" }}</span>
      </li>
      <span class="post-excerpt"> {{ post.excerpt }}</span>
    {% endfor %}
  </ul>
{% endfor %} -->