--- 
layout: post
title: 'Interface Segregation Principle'
category: OOP
keywords: "oop, solid, SOLID, OOP, OO, POO, principios solid, solid principles, poo, oo, isp, ISP, Interface Segregation Principle"
tags: 
- title: SOLID
  slug: solid
- title: Princ&iacute;pios SOLID
  slug: principios-solid  
- title: OOP
  slug: oop
---

NÃ£o menos importante que qualquer um dos princÃ­pios, o ISP, ou princÃ­pio de SegregaÃ§Ã£o de Interface, preza uma abordagem bem simples ao seu cÃ³digo. Ele preza que um cliente nÃ£o deve ser forÃ§ado a depender de contratos que ele nÃ£o utilizarÃ¡.  
Seguindo o ISP nÃ³s teremos contratos de classes mais coesas. Em outras palavras, nÃ£o criaremos contratos gordos que alguma classe que precise implementÃ¡-lo, nÃ£o deixe de implementÃ¡-lo por completo.  
Particularmente eu evitaria um contrato gordo de todas as formas possÃ­veis, devido ao smell que ele traz. MAS em alguns casos ele possa ser necessÃ¡rio e nÃ£o trazer mal algum. NÃ£o sei se jÃ¡ notaram, mas alguns Frameworks possuem contratos monstruosos, e atÃ© que funcionam bem.


<img alt="Control room" src="/images/control-room.jpg" class="post_img" />


## O cÃ³digo

Eu nunca vi e nem espero ver um exemplo tÃ£o cretino como esse, mas foi algo que pensei para nÃ£o ter que demonstrar aqui exemplos que podem encontrar em outros lugares. Para verem por outro Ã¢ngulo :-|

### O sacrilÃ©gio

<pre name="code" class="c-sharp">
	public interface IBaseRepository&lt;TEnt&gt;
	{
		void Salvar(TEnt entidade);
		void Remover(TEnt entidade);
	}

	public abstract class BaseRepository&lt;TEnt&gt; : IBaseRepository&lt;TEnt&gt;
    {
        public virtual void Salvar(TEnt entidade)
        {
            // salvar a TEnt
        }

        public virtual void Remover(TEnt entidade)
        {
            // remover a TEnt
        }
    }
</pre>

A maioria de nossos repositÃ³rios poderÃ£o salvar e remover uma entidade do tipo especificado. Mas digamos que para uma particular entidade isso nÃ£o Ã© uma realidade, digamos que para a entidade Produto, nÃ£o seja possÃ­vel remove-lo.

<pre name="code" class="c-sharp">
	public interface IProdutoRepository : IBaseRepository&lt;Produto&gt;
	{
	}

	public abstract class ProdutoRepository : IProdutoRepository
    {
		public override void Remover(Produto entidade)
        {
            throw new NotImplementedException();
        }
    }
</pre>

Essa Ã© a maneira mais simples de se identificar a violaÃ§Ã£o do ISP, "<strong style="color:#069;">thrown new</strong> NotImplementedException();". Se eu nÃ£o posso fazer isso, nÃ£o deveria estar aÃ­, certo?

### Emagrecendo o contrato

NÃ£o pense que o IBaseRepository deixarÃ¡ de existir, ele sÃ³ implementarÃ¡ os dois contratos que obtivermos desse refactoring. Tendo em mente que ele nÃ£o deixarÃ¡ de existir para as outras implementaÃ§Ãµes que faziam bom uso dele, vamos ajustar a situaÃ§Ã£o para que o repositÃ³rio de Produto deixe de ferir o princÃ­pio.

<pre name="code" class="c-sharp">
	public interface IPersistenciaRepository&lt;TEnt&gt;
	{
		void Salvar(TEnt entidade);
	}

	public interface IRemocaoRepository&lt;TEnt&gt;
	{
		Remover(TEnt entidade);
	}
	
	public interface IBaseRepository&lt;TEnt&gt; : IPersistenciaRepository&lt;TEnt&gt;, IRemocaoRepository&lt;TEnt&gt;
	{
	}
	
	public interface IProdutoRepository : IPersistenciaRepository&lt;Produto&gt;
	{
	}

	public class ProdutoRepository&lt;TEnt&gt; : IProdutoRepository
    {
		public void Salvar(TEnt entidade)
        {
            // salvar a TEnt
        }
    }
</pre>

Dessa forma temos um contrato para o repositÃ³rio de Produto que sÃ³ o obriga a implementar o que ele realmente precisa. AlÃ©m disso, mantemos a forma original do nosso repositÃ³rio base, ou seja, nÃ£o afetarÃ¡ quem o implementava de maneira correta.

Tenha em mente que esse exemplo Ã© meramente ilustrativo, e nÃ£o condiz com o design que eu faria na vida real ~*esquivando de possÃ­veis julgamentos*~ Tente absorver apenas a ideia por trÃ¡s do exemplo.

Logo eu posto um projeto com todos os exemplos.  
Tenham um bom dia :-D