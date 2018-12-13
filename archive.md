---
layout: page
title: Archive
sidebar_order: 4
---

### Blog Posts ({{ site.categories.blog.size }})

<ul class="posts">
	{% for post in site.categories.blog -%}
		<li>{{ post.date | date_to_string }} &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
	{% endfor -%}
</ul>

### Notes ({{ site.categories.notes.size }})

<ul class="posts">
	{% for post in site.categories.notes -%}
		<li>{{ post.date | date_to_string }} &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
	{% endfor -%}
</ul>