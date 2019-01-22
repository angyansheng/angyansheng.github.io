---
layout: page
title: Commutative Algebra
---

Commutative algebra studies __commutative rings__ and __modules__ over these rings, which are the basic objects of algebraic geometry and algebraic number theory. Homological algebra is the study of __homology__ theories from algebraic topology, giving us powerful algebraic tools for applications in many fields of mathematics.

These notes follow the graduate course MA5204 Graduate Algebra IIA, offered in AY2018/19 Semester 2 by Prof Chin Chee Whye. The main text for this course is H. Matsumara, _Commutative Ring Theory_ (1989).

{% assign post_list = site.categories.notes | where_exp:"x","x.tags contains 'commutative algebra'" | reverse %}
<ul class="posts">
	{% for post in post_list -%}
		<li><a href="{{ post.url }}">{{ post.title }}</a></li>
	{% endfor -%}
</ul>

{% assign latest_post = post_list | sort:"date" | last -%}
(In progress, last updated {{ latest_post.date | date_to_string }})