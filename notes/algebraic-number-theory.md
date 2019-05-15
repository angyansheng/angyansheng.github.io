---
layout: page
title: Algebraic Number Theory
---

Algebraic number theory is concerned with __number fields__, finite extensions of $\bb Q$, whose elements are the __algebraic numbers__. It uses the methods of algebra to study notions from number theory, such as primes and factorisation.

These notes follow the graduate course MA5202 Number Theory, offered in AY2018/19 Semester 2 by Prof Chin Chee Whye. The main text for this course is D. A. Marcus, _Number Fields_, 2nd ed. (2018).

{% assign post_list = site.categories.notes | where_exp:"x","x.tags contains 'algebraic number theory'" | sort:"series-order" %}
<ul class="posts">
	{% for post in post_list -%}
		<li><a href="{{ post.url }}">{{ post.title }}</a></li>
	{% endfor -%}
</ul>

{% assign latest_post = post_list | sort:"date" | last -%}
(In progress, last updated {{ latest_post.date | date_to_string }})