---
layout: default
title: Posts com a categoria Windows Azure
categories: 
- title: Windows Azure
  slug: windows-azure
  autoslug: windows-azure
---
<h2 class="category">Windows Azure</h2>
<ul class="posts">
	{% for post in site.posts %}
	{% if post.category == 'Windows Azure' %}
	<li>
		<p>
			<span>{{ post.date | date: "%d/%m/%Y" }}</span> &raquo; 
			<a href="{{ post.url }}">{{ post.title }}</a>
		</p>
	</li>
	{% endif %}
	{% endfor %}
</ul>
<h3><a href="/">Voltar</a></h3>