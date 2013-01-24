---
layout: default
title: Posts com a categoria Dicas
category: Dicas
---
<h2 class="category">Dicas</h2>
<ul class="posts">
	{% for post in site.categories.Dicas %}
	<li>
		<p>
			<span>{{ post.date | date: "%d/%m/%Y" }}</span> &raquo; 
			<a href="{{ post.url }}">{{ post.title }}</a>
		</p>
	</li>
	{% endfor %}
</ul>
<h3><a href="/">Voltar</a></h3>