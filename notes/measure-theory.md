---
layout: page
title: Measure Theory
---

Measure theory is the study of __measures__ on a set, which are assignments of a "size" to some of its subsets. Measures give rise to the theory of __Lebesgue integration__, which is more general and has better properties than Riemann integration.

These notes closely follow the graduate course MA5205 Graduate Analysis I, offered in AY2018/19 Semester 1 by Prof Denny Leung.

{% assign post_list = site.categories.notes | where_exp:"x","x.tags contains 'measure theory'" | reverse %}
<ul class="posts">
	{% for post in post_list -%}
		<li><a href="{{ post.url }}">{{ post.title }}</a></li>
	{% endfor -%}
</ul>

{% assign latest_post = post_list | sort:"date" | last -%}
(In progress, last updated {{ latest_post.date | date_to_string }})