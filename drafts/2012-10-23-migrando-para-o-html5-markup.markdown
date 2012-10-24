--- 
layout: post
title: 'Migrando para o HTML5 Markup'
category: Web
tags: 
- title: HTML
  slug: html
- title: WebStandards
  slug: webStandards
---

Atualmente tenho me atendado bastante em tecnologias de front-end e gostaria de compartilhar o que tenho visto com vocês.

(HTML5 = Novo markup + Nova API Javascript) Essa é a maneira mais simples e eficiente que vejo para definir o HTML5. A ideia é que ele seja chamado apenas de HTML daqui alguns anos, mas atualmente utilizamos esse termo para marcar o inicio das novas funcionalidades que estão sendo definidas e implementadas.  

A ideia desse post é fazer um refactoring no markup desse site para que ele se enquadre nos padrões do [serviço de validação][servico-validacao] de markup do W3C. Também farei um refactoring no CSS, mas esse ficará em off :-P  

Atualmente estou utilizando o [Jekyll][jekyll], que é um gerador de páginas web estáticas escrito em Ruby. Ele utiliza templates html e mescla com meus posts, que escrevo com markdown, e são esses templates que iremos refatorar.  
Atualmente possuo dois templates simples, um para posts e o padrão do resto da página. Além dessas páginas, também refatorarei a página inicial, que utiliza o template padrão.

## Template dos posts

### Como era

<pre name="code" class="html">
	<div class="post">
		<h2 class="post_title">{{ page.title }}</h2>
		<div class="index_meta">
			<div class="post_date">{{ page.date | date: "%d/%m/%Y" }}</div>
			<div class="post_comments_count">
				<a href="{{page.url}}#disqus_thread" data-disqus-identifier="{{page.id}}">
				Deixe um coment&aacute;rio</a>
			</div>			
		</div>
		<div class="post_content">
			{{ content }}
		</div>	
		<!-- Links de compartilhamento AddThis omitidos -->
	    <h3><a href="/">Voltar</a></h3>
		<div id="syntaxhighlighter">
			<!-- Scripts do Syntaxhighlighter omitidos -->
		</div>
		<div id="comments">
			<!-- Scripts do Disqus omitidos -->	
		</div>
	</div>
</pre>

### Como ficou

<pre name="code" class="html">
	<article class="post">	
		<header>
			<h1 class="post_title">{{ page.title }}</h1>
			<div class="index_meta">
				<div class="post_date">{{ page.date | date: "%d/%m/%Y" }}</div>
				<div class="post_comments_count">
					<a href="{{page.url}}#disqus_thread" data-disqus-identifier="{{page.id}}">Deixe um coment&aacute;rio</a></div>			
			</div>
		<header>
		
		<section class="content">
			{{ content }}
		</section>

    	<footer>
    		<!-- Links de compartilhamento AddThis omitidos -->
    		<a href="/">Voltar</a>
			<section id="comments">
				<!-- Scripts do Disqus omitidos -->	
			</section>
		</footer>
	</article>
	<embed id="syntaxhighlighter">
		<!-- Scripts do Syntaxhighlighter omitidos -->
	</embed>
</pre>

[servico-validacao]:http://validator.w3.org
[jekyll]:http://jekyllrb.com/