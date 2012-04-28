---
layout: default
title: Posts tagged boring
tag: Boring
---
<h1 class="category">Boring</h1>
<ul class="posts">
	{% for post in site.posts %}				
	{% for tag in post.tags %}	
	{% if tag.title == page.tag %}	
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