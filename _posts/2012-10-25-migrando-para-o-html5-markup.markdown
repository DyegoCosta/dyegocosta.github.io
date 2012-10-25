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

Atualmente tenho me atentado bastante em tecnologias de front-end e gostaria de compartilhar o que tenho visto com vocês.

(HTML5 = Novo markup + Nova API Javascript) Essa é a maneira mais simples e eficiente que vejo para definir o HTML5. A ideia é que ele seja chamado apenas de HTML daqui alguns anos, mas atualmente utilizamos esse termo para marcar o inicio das novas funcionalidades que estão sendo definidas e implementadas.  

Você é ou já foi um programador server-side? Você se preocupa/va em escrever um bom código? Um código coeso, limpo e de fácil leitura? A semântica do HTML traz grandes benefícios como um código server-side bem escrito. Pessoas leem esse código, e além disso, uma boa semântica é importante para a *otimização para motores de busca*, [SEO][seo], que se trata de *"um conjunto de estratégias com o objetivo de potencializar e melhorar o posicionamento de um site nas páginas de resultados naturais (orgânicos) nos sites de busca"*.

<img title="li" src="/images/li.jpg" class="post_img" />

A ideia desse post é fazer um refactoring no markup desse site. Também farei um refactoring no CSS, mas esse ficará em off :-P  

Atualmente estou utilizando o [Jekyll][jekyll], que é um gerador de páginas web estáticas escrito em Ruby. Ele utiliza templates html e mescla com meus posts que são escritos em markdown, e são esses templates que iremos refatorar.  
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
		<div id="comments">
			<!-- Scripts do Disqus omitidos -->	
		</div>
	</div>
</pre>

### Como ficou

Passei a utilizar algumas das novas tags que vieram com o HTML5, vamos ver o que mudou e o porque.

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
    		<section id="social">
    			<!-- Links de compartilhamento AddThis omitidos -->
    		</section>
    		<a href="/">Voltar</a>
			<section id="comments">
				<!-- Scripts do Disqus omitidos -->	
			</section>
		</footer>
	</article>
</pre>

A tag <mark>&lt;article&gt;</mark> substituiu a div que fazia o wrapper do conteúdo inteiro do post. Ela é utilizada para conteúdos que fazem sentido por si próprios, ou seja, o conteúdo do post pode existir dentro de outros contextos que continuará sendo um post.  

A tag <mark>&lt;header&gt;</mark> como o nome já diz, é o cabeçalho. Sim, é semanticamente correto ter mais de um cabeçalho dentro da página, desde que eles estejam em contextos diferentes. Dentro dessa tag temos agora a tag <mark>&lt;h1&gt;</mark> em vez da h2. Mas não é semanticamente incorreto haver mais de um h1 em página? Comumente é dito que sim, mas a resposta na realidade é **NÃO**, veja [esse vídeo][video] de 1 minuto com a explicação de alguém que tem crédito para falar isso, Matt Cutts, engenheiro da Google.  

Temos a tag <mark>&lt;section&gt;</mark> definindo o conteúdo de meu post. Essa tag define uma seção da página, dã. Sabemos que o post não se trata apenas de texto, então dado que estou utilizando a tag article para definir o contexto do meu post, estou usando agora a section para definir o contexto do texto do meu post.  

Assim como a tag header, a tag <mark>&lt;footer&gt;</mark> também é bem óbvia. É utilizada para definir o rodapé de um contexto. Como eu expliquei sobre a utilização da section, dentro desse footer eu defini duas seções diferentes, uma para comentários e uma para compartilhamentos de redes sociais.  

Durante a escrita desse post, comecei a utilizar a tag <mark>&lt;mark&gt;</mark>, uso para fazer o destaque de fundo amarelo em alguma das palavras do texto, e ele foi criado justamente para isso! Confesso que tive a ideia de utiliza-la após a tentativa fracassada de "escrever" as tag com os símbolos de maior e menor em volta como são utilizada por causa do Jekyll, e **PQP!** Lembrei o que tenho que fazer para conseguir chegar a esse resultado. Posso ter acabado de perder sua confiança, mas prefiro ser sincero :-D  

Mais uma que eu gostaria de comentar, que faz parte do meu refactoring geral da semantica do blog, é a tag <mark>&lt;aside&gt;</mark>, que trata de um conteúdo *ao lado*, *à parte*. Passei a utilizar ele no *menu* com meu GitHub, Twitter e RSS ao lado da página. Essa tag pode ser utilizada sempre que houver um conteúdo a parte do contexto atual que precise ser exibido. No caso de minha utilização, é à parte do conteúdo da página toda.  

Para mais tags HTML5, ou não, recomendo o [W3School][w3school], lá você poderá encontrar todo o tipo de informações que precisa para entender melhor o significado de qualquer tag existente.  

Por enquanto é isso pessoal, abraços.

[seo]:http://pt.wikipedia.org/wiki/Otimiza%C3%A7%C3%A3o_para_motores_de_busca
[servico-validacao]:http://validator.w3.org
[jekyll]:http://jekyllrb.com/
[video]:http://www.youtube.com/watch?v=GIn5qJKU8VM
[w3school]:http://www.w3schools.com/tags/default.asp