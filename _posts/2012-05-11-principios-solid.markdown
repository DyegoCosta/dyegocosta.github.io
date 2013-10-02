--- 
layout: post
title: 'SOLID Principles'
category: OOP
keywords: "oop, solid, SOLID, OOP, OO, POO, principios solid, solid principles, poo, oo, Single Responsability Principle, SRP, srp, Open Close Principle, ocp, OCP, Liskov Substitution Principle, lsp, LSP, Interface Segregation Principle, isp, ISP, Dependency Inversion Principle, DIP, dip"
tags: 
- title: SOLID
  slug: solid
- title: Princ&iacute;pios SOLID
  slug: principios-solid  
- title: OOP
  slug: oop
---

Se a maioria dos programadores estivessem cientes desses princípios, com certeza o mundo seria um lugar melhor.
Os princípios SOLID são cinco princípios, ou práticas, de programação orientada a objetos e design que foram introduzidos em um acrônimo por [Robert Cecil Martin][uncle-bob], mais conhecido Uncle Bob, por volta dos anos 2000.
A utilização desses princípios, como qualquer um que tire bom proveito de nossa amada [OOP][oop], trazem benefícios no design de nossas aplicações, tornando-as mais coesas.
Neste post você se deparará com minha tentativa de facilitar de alguma forma a vida de alguns com *~traduções da minha cabeça nesse momento de inspiração~*. Eu geralmente não gosto de traduzir esse tipo de coisa, mas se alguém passar por algum lugar desatento e ver esses termos traduzidos, ao ter lido aqui poderá associar com mais facilidade, ou não.
Daremos uma olhada por cima de cada um desses princípios, mas em breve estarei postando um conteúdo para cada um deles com exemplos e talvez uma explicação melhor.
No final estarei postando o código-fonte de uma aplicação que usei como exemplo de ferimentos desses princípios para refatorar durante uma apresentação.


## Single Responsability Principle

O [SRP][srp], ou em português *"Princípio de Responsabilidade Única"* diz que todo objeto deve ter um única responsabilidade, e que a responsabilidade deve estar encapsulada pela classe.
Quando uma classe ou método ~*não se limitando a eles*~ possui diversas responsabilidades, a possibilidade dessa classe precisar de mudar é mais alta. 
Com essa possibilidade, há mais chances de uma mudança quebrar o código e caso isso aconteça, será muito mais difícil identificar o problema.
Além disso, a testabilidade desta classe será comprometida, pois em um cenário em que estamos testando unidades da aplicação, seria mais trabalhoso e menos eficiente testar algo que possui mais de uma responsabilidade.


## Open/Close Principle

A ideia do OCP ou em português *"Princípio Aberto/Fechado"* é manter entidades da aplicação abertas para extensão, mas fechadas para modificação.
Evita a criação de bugs em códigos funcionais e facilita a extensão apesar da complexidade introduzida para a implementação dessa estrutura.


## Liskov Substitution Principle

Aparentemente o princípio SOLID mais chato de se entender, o LSP ou em português *"Princípio Substituição de Liskov"*. O conceito que originou esse princípio é bastante acadêmico, do tipo que um profissional que não esteja acostumado com termos e raciocínios acadêrmicos provavelmente não entenderá na primeira tentativa.
O princípio foi nomeado pelo nome de sua autora [Barbara Liskov][barbara-liskov].
O conceito, que veremos no post desse tópico, é equivalente ao seguinte *"Deve ser possível substituir uma classe base por suas classes derivadas"*. E é tão simples como parece, até ver sua origem.


## Interface Segregation Principle

O ISP, "Princípio de Segregação de Interface" específica que clientes não devem ser forçados a depender de interfaces que não usam. Ou seja, não criar contratos que nem todos os clientes possa implementar, mas sim criar contrato ~*interfaces*~ menores para que seus clientes as implementem por completo.


## Dependency Inversion Principle

E por último o DIP, ou "Princípio de Inversão de Dependência", nos diz duas coisas. Módulos de alto nível não devem depender de módulos de baixo nível. E que abstrações não devem depender de detalhes, mas detalhes devem depender de abstrações.
É um princípio extremamente útil para mater seus módulos desacoplados e testáveis. Existem diversas ferramentas, além de outras práticas, que nos auxiliam a utilizar esse princípio com mais eficiência.


Como eu disse, nos próximos post veremos com mais detalhes cada um dos princípios.


Vou deixar aqui os slides de uma apresentação que fiz na empresa que trabalho atualmente. Sei que não é muito útil ~*principalmente esses meus*~, mas para quem quiser dar uma conferida está aí.

<div style="width:425px" id="__ss_12226756"> <strong style="display:block;margin:12px 0 4px"><a href="http://www.slideshare.net/dyegocosta/princpios-solid-12226756" title="Princípios solid" target="_blank">Princípios solid</a></strong> <iframe src="http://www.slideshare.net/slideshow/embed_code/12226756" width="425" height="355" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe> </div><br />

[oop]:http://dyegocomy.com/category/oop
[uncle-bob]:http://en.wikipedia.org/wiki/Robert_Cecil_Martin
[srp]:http://dyegocomy.com/tags/srp
[barbara-liskov]:http://en.wikipedia.org/wiki/Barbara_Liskov