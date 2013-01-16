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
	{% for post in site.categories.windows-azure %}
	<li>
		<p>
			<span>{{ post.date | date: "%d/%m/%Y" }}</span> &raquo; 
			<a href="{{ post.url }}">{{ post.title }}</a>
		</p>
	</li>
	{% endfor %}
</ul>
<h3><a href="/">Voltar</a></h3>