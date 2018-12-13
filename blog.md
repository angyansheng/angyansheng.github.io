---
layout: default
title: Blog
regenerate: true
sidebar_order: 1
---

<div class="posts">
  {% for post in site.categories.blog %}
  <div class="post">
    <h1 class="post-title">
      <a href="{{ post.url | relative_url }}">
        {{ post.title }}
      </a>
    </h1>

    <span class="post-date">{{ post.date | date_to_string }}</span>

    {%- if post.content contains '<!--more-->' -%}
      {{ post.excerpt }}
    {%- else -%}
      {{ post.content | split:'</p>' | first | markdownify | append: '</p>' }}
    {%- endif -%}
    
    <p><a href="{{ post.url | relative_url }}"> Read more</a></p>
  </div>
  {% endfor %}
</div>
