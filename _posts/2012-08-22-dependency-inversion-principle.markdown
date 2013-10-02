--- 
layout: post
title: 'Dependency Inversion Principle'
category: OOP
keywords: "oop, solid, SOLID, OOP, OO, POO, principios solid, solid principles, poo, oo, dip, DIP, Dependency Inversion Principle"
tags: 
- title: SOLID
  slug: solid
- title: Princ&iacute;pios SOLID
  slug: principios-solid  
- title: OOP
  slug: oop
---

Fechando a série de posts com a visão geral dos princípios SOLID, temos o Dependency Inversion Principle, ou Princípio de Inversão de Dependência 
Esse princípio possui duas abordagens, primeiramente que um módulo de alto nível não deve depender de outro de baixo nível, e além disso, que abstrações não devem depender de detalhes. 
Claro que podem existir diversos módulos entre os mais altos e os mais baixos, o DIP se aplica a qualquer indício de dependência desnecessária.


<img alt="" src="/images/cat-and-fish.jpg" class="post_img"/>


## Alto e baixo nível

O princípio presa que um módulo de alto nível não deve depender de outro(s) de baixo nível, mas que ambos devem depender de abstrações.
Um módulo de alto nível está relacionado a entidades de negócio e de interação com o usuário, e baixo nível está relacionado a entidades de infraestrutura, como módulos de persistencia.  
Mas por que não é recomendável que um módulo dependa do outro? Em um cenário simples em que você possui uma GUI dependente de um módulo de persistência, 
essa dependência compromete a testabilidade de seu módulo, e além disso, pelo módulo estar dependente de uma implementação, a troca desse módulo será extremamente penosa. A abstração nos ajuda a remover essa dependência dentre os módulos.

## Le código

Utilizarei um exemplo simples onde um Controller do ASP.NET Web API está dependente da implementação de um repositório.
Exemplo meramente ilustrativo, um Controller não necessariamente faria utilidade de um repositório, dependendo do cenário.

<pre name="code" class="c-sharp">
public class RepositorioCliente
{
    public Cliente ObterPorId(int id)
    {
        return DB.Clientes.Get(id);
    }
}

public class ClienteController : ApiController
{
    public Cliente Get(int id)
    {
		var repositorio = new RepositorioCliente();
		
        return repositorio.ObterPorId(id);
    }
}
</pre>

Nesse exemplo o RepositorioCliente está abstraindo a utilização do banco de dados, o que é algo bom, mas note que nosso Controller está totalmente dependente da implementação do repositório.
Para que nosso Controller não fique dependente da implementação de nosso repositório, precisamos abstrair essa implementação.

<pre name="code" class="c-sharp">
public interface IRepositorioCliente
{
    public Cliente ObterPorId(int id);
}

public class ClienteController : ApiController
{
	private IRepositorioCliente _repositorioCliente;
	
	public ClienteController(IRepositorioCliente repositorioCliente)
	{
		_repositorioCliente = repositorioCliente;
	}

    public Cliente Get(int id)
    {
		return _repositorioCliente.ObterPorId(id);
    }
}
</pre>

Para o Controller, não importa a implementação do repositório, caso ele nos traga o que buscamos. Nesse caso, se precisarmos mudar a implementação do repositório, a mudança será transparente para nosso Controller.
Com isso teremos ganhos na testabilidade, pois podemos facilmente mockar o comportamento de nosso repositório 










