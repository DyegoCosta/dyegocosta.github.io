---
layout: default
title: Posts com a categoria OOP
category: OOP
---
<h2 class="category">OOP</h2>
<ul class="posts">
	{% for post in site.categories.OOP %}
	<li>
		<p>
			<span>{{ post.date | date: "%d/%m/%Y" }}</span> &raquo; 
			<a href="{{ post.url }}">{{ post.title }}</a>
		</p>
	</li>
	{% endfor %}
</ul>
<h3><a href="/">Voltar</a></h3>