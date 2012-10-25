---
layout: default
title: Posts com a categoria Testes
category: Testes
---
<h2 class="category">Testes</h2>
<ul class="posts">
	{% for post in site.posts %}				
	{% for category in post.categories %}	
	{% if category.title == page.category %}	
	<li>
		<p>
			<span>{{ post.date | date: "%d/%m/%Y" }}</span> &raquo; 
			<a href="{{ post.url }}">{{ post.title }}</a>
		</p>
	</li>
	{% endif %}	
	{% endfor %}
	{% endfor %}
</ul>
<h3><a href="/">Voltar</a></h3>