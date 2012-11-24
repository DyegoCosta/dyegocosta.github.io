---
layout: default
title: Posts com a categoria Web
category: Web
---
<h2 class="category">Web</h2>
<ul class="posts">
	{% for post in site.categories.Web %}
	<li>
		<p>
			<span>{{ post.date | date: "%d/%m/%Y" }}</span> &raquo; 
			<a href="{{ post.url }}">{{ post.title }}</a>
		</p>
	</li>
	{% endfor %}
</ul>
<h3><a href="/">Voltar</a></h3>