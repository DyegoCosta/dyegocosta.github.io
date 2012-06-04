--- 
layout: post
title: 'Open/Closed Principle'
category: OOP
tags: 
- title: SOLID
  slug: solid
- title: Princ&iacute;pios SOLID
  slug: principios-solid  
- title: OOP
  slug: oop
---

A ideia do OCP, ou em português *"Princípio Aberto/Fechado"*, é manter as entidades da aplicação abertas para extensão, mas fechadas para modificação.
Evita a criação de bugs em códigos funcionais e facilita a extensão apesar da complexidade introduzida para a implementação dessa estrutura.
Esse princípio é um dos mais antigos do Design Orientado a Objetos, mas não vamos nos entediar aqui lendo sua história. Para quem se interessar, recomendo o artigo [The Open-Closed Principle][ocp-robert-martin-artile] escrito em 1996 por Robert Martin.

<img title="Porta holandesa" src="/images/dutch-door-ocp.jpg" class="post_img" style="margin-left:33%;" />
<p class="post_img_subtitle">Você não substituiria todas as portas de sua casa por portas desse tipo, certo?</p>

Esse princípio só deve ser utilizado em módulos que mudam com certa frequência e difícilmente será aplicado no design inicial de sua aplicação.
A menos que você tenha certeza de que um certo código irá mudar, falando em extensão que poderá ser visto no exemplo, não recomendo que utilize esse princípio.

## O código

Como eu disse, o princípio deve ser aplicado a um cenário onde puder se identificado uma constante mudança no código que influencia na mudança de outras entidades.
Isso geralmente é identificado durante o amadurecimento do módulo, por isso não é indicado sua aplicação imediata.
Vamos dar uma olhada em um exemplo real que me deparei a pouco tempo atrás.

### Violação do OCP

Estou utilizando a plataforma ASP.NET MVC, e esse código é de um helper que me ajuda na criação dos botões de uma área específica da aplicação.
A ideia era passar o tipo do botão que o helper se encarregaria em montar seu HTML e colocar uma imagem ~via uma classe do CSS~ de acordo com o tipo do botão.

<pre name="code" class="c-sharp">
public static MvcHtmlString MeuLink(this HtmlHelper helper, TipoBotao tipoBotao)
{
    var classeCss = string.Empty;
	var texto = string.Empty;
	
	switch(tipoBotao)
	{
		case TipoBotao.Salvar:
			classeCss = "iconeSalvar";
			texto = "Salvar";
		break;
		case TipoBotao.Cancelar:
			classeCss = "iconeCancelar";
			texto = "Cancelar";
		break;
	}

    var meuLink = string.Format("<a class='estiloPadraoDoBotao {0}'>{1}</a>", classeCss, texto);

    return MvcHtmlString.Create(meuLink);
}

public enum TipoBotao
{
    Salvar,
    Cancelar
}
</pre>

Note que caso eu precise de um novo botão, terei que adicionar um novo TipoBotao e modificar meu helper para que ele reconheça esse novo tipo. Assim então podemos ver que o helper não está fechado para modificação.

### Desacoplando

O que precisamos é de uma nova maneira de criar esses links de forma que se eu quiser adicionar um novo tipo, o helper não precisará ser modificado.

<pre name="code" class="c-sharp">
public static MvcHtmlString MeuLink(this HtmlHelper helper, TipoBotao tipoBotao)
{
    var classeCss = tipoBotao.ObterClasseCss();
    var texto = tipoBotao.Texto();

    var meuLink = string.Format("<a class='estiloPadraoDoBotao {0}'>{1}</a>", classeCss, texto);

    return MvcHtmlString.Create(meuLink);
}

public abstract class TipoBotao
{
    public abstract string ObterClasseCss();

    public abstract string Texto();
}

public sealed class BotaoSalvar : TipoBotao
{
    public override string ObterClasseCss()
    {
        return "iconeSalvar";
    }

    public override string Texto()
    {
        return "Salvar";
    }
}

public sealed class BotaoCancelar : TipoBotao
{
    public override string ObterClasseCss()
    {
        return "iconeCancelar";
    }

    public override string Texto()
    {
        return "Cancelar";
    }
}
</pre>

Dessa forma, caso eu queira adicionar um novo tipo de botão (Por exemplo um botão "Voltar", "Editar", "Novo", etc) a única coisa que precisarei fazer é criar um nova classe que implemente o TipoBotao.

Ressaltando o que eu disse, não utilize esse princípio a menos que identifique ser necessário.

[ocp-robert-martin-artile]:http://www.objectmentor.com/resources/articles/ocp.pdf