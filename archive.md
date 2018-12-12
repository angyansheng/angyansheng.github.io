---
layout: page
title: Archive
---

### Blog Posts ({{ site.posts.size }})

<ul class="posts">
	{% for post in site.posts -%}
		<li>{{ post.date | date_to_string }} &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
	{% endfor -%}
</ul>