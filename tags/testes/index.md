---
layout: default
title: Posts com a tag Testes
tag: testes
---
<h1 class="category">Testes</h1>
<ul class="posts">
	{% for post in site.posts %}				
	{% for tag in post.tags %}	
	{% if tag.slug == page.tag %}	
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