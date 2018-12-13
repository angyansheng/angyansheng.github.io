---
layout: page
title: Notes
sidebar_order: 2
---

{% assign post_list = site.pages | where_exp:"x","x.path contains 'notes/'"%}
{% for post in post_list -%}
<h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
{% endfor -%}