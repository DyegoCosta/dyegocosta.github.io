--- 
layout: post
title: 'Interface Segregation Principle'
category: OOP
tags: 
- title: SOLID
  slug: solid
- title: Princ&iacute;pios SOLID
  slug: principios-solid  
- title: OOP
  slug: oop
---

Não menos importante que qualquer um dos princípios, o ISP, ou princípio de Segregação de Interface, preza uma abordagem bem simples ao seu código. Ele preza que um cliente não deve ser forçado a depender de contratos que ele não utilizará.  
Seguindo o ISP nós teremos contratos de classes mais coesas. Em outras palavras, não criaremos contratos gordos que alguma classe que precise implementá-lo, não deixe de implementá-lo por completo.  
Particularmente eu evitaria um contrato gordo de todas as formas possíveis, devido ao smell que ele traz. MAS em alguns casos ele possa ser necessário e não trazer mal algum. Não sei se já notaram, mas alguns Frameworks possuem contratos monstruosos, e até que funcionam bem.

<img alt="Control room" src="/images/control-room.jpg" class="post_img" style="margin:25px 12% 25px;"/>

## O código

Eu nunca vi e nem espero ver um exemplo tão cretino como esse, mas foi algo que pensei para não ter que demonstrar aqui exemplos que podem encontrar em outros lugares. Para verem por outro ângulo :-|

### O sacrilégio

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

A maioria de nossos repositórios poderão salvar e remover uma entidade do tipo especificado. Mas digamos que para uma particular entidade isso não é uma realidade, digamos que para a entidade Produto, não seja possível remove-lo.

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

Essa é a maneira mais simples de se identificar a violação do ISP, "<strong style="color:#069;">thrown new</strong> NotImplementedException();". Se eu não posso fazer isso, não deveria estar aí, certo?

### Emagrecendo o contrato

Não pense que o IBaseRepository deixará de existir, ele só implementará os dois contratos que obtivermos desse refactoring. Tendo em mente que ele não deixará de existir para as outras implementações que faziam bom uso dele, vamos ajustar a situação para que o repositório de Produto deixe de ferir o princípio.

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

Dessa forma temos um contrato para o repositório de Produto que só o obriga a implementar o que ele realmente precisa. Além disso, mantemos a forma original do nosso repositório base, ou seja, não afetará quem o implementava de maneira correta.

Tenha em mente que esse exemplo é meramente ilustrativo, e não condiz com o design que eu faria na vida real ~*esquivando de possíveis julgamentos*~ Tente absorver apenas a ideia por trás do exemplo.

Logo eu posto um projeto com todos os exemplos.  
Tenham um bom dia :-D