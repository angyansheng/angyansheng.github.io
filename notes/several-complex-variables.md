---
layout: page
title: Several Complex Variables
---

The theory of holomorphic functions in several complex variables is one of the cornerstones of 20th century mathematics. Far from being a simple generalisation of single-variable complex analysis, the development of this theory requires the modern viewpoint of homological algebra and sheaf theory.

These notes are adapted and expanded from the topics course MA4291 Several Complex Variables, offered in AY2018/19 Semester 1 by Prof Chin Chee Whye.

{% assign post_list = site.posts | where_exp:"x","x.path contains 'notes/_posts/scv'" | reverse %}
<ul class="posts">
	{% for post in post_list -%}
		<li><a href="{{ post.url }}">{{ post.title }}</a></li>
	{% endfor -%}
</ul>

{% assign latest_post = post_list | sort:"date" | last -%}
(In progress, last updated {{ latest_post.date | date_to_string }})