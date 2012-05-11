--- 
layout: post
title: 'Princ&iacute;pios SOLID'
category: OOP
tags: 
- title: SOLID
  slug: solid
- title: Princ&iacute;pios SOLID
  slug: principios-solid  
- title: OOP
  slug: oop
---
<img alt="onix" src="https://fbcdn-sphotos-a.akamaihd.net/hphotos-ak-snc7/419567_276394325763474_214567638612810_673586_972615038_n.jpg" class="post_img goLeft">


Se a maioria dos programadores estivessem cientes desses princ�pios, com certeza o mundo seria um lugar melhor.
Os princ�pios SOLID s�o cinco princ�pios, ou pr�ticas, de programa��o orientada a objetos e design que foram introduzidos em um acr�nimo por [Robert Cecil Martin][uncle-bob], mais conhecido Uncle Bob, por volta dos anos 2000.
A utiliza��o desses princ�pios, como qualquer um que tire bom proveito de nossa amada [OOP][oop], trazem benef�cios no design de nossas aplica��es, tornando-as mais coesas.
Neste post voc� se deparar� com minha tentativa de facilitar de alguma forma a vida de alguns com *~tradu��es da minha cabe�a nesse momento de inspira��o~*. Eu geralmente n�o gosto de traduzir esse tipo de coisa, mas se algu�m passar por algum lugar desatento e ver esses termos traduzidos, ao ter lido aqui poder� associar com mais facilidade, ou n�o.

Daremos uma olhada por cima de cada um desses princ�pios, mas em breve estarei postando um conte�do para cada um deles com exemplos e talvez uma explica��o melhor.
No final estarei postando o c�digo-fonte de uma aplica��o que usei como exemplo de ferimentos desses princ�pios para refatorar durante uma apresenta��o.


## Single Responsability Principle

O [SRP][srp], ou em portugu�s *"Princ�pio de Responsabilidade �nica"* diz que todo objeto deve ter um �nica responsabilidade, e que a responsabilidade deve estar encapsulada pela classe.
Quando uma classe ou m�todo ~*n�o se limitando a eles*~ possui diversas responsabilidades, a possibilidade dessa classe precisar de mudar � mais alta. 
Com essa possibilidade, h� mais chances de uma mudan�a quebrar o c�digo e caso isso aconte�a, ser� muito mais dif�cil identificar o problema.
Al�m disso, a testabilidade desta classe ser� comprometida, pois em um cen�rio em que estamos testando unidades da aplica��o, seria mais trabalhoso e menos eficiente testar algo que possui mais de uma responsabilidade.


## Open/Close Principle

A ideia do OCP ou em portugu�s *"Princ�pio Aberto/Fechado"* � manter entidades da aplica��o abertas para extens�o, mas fechadas para modifica��o.
Evita a cria��o de bugs em c�digos funcionais e facilita a extens�o apesar da complexidade introduzida para a implementa��o dessa estrutura.


## Liskov Substitution Principle

Aparentemente o princ�pio SOLID mais chato de se entender, o LSP ou em portugu�s *"Princ�pio Substitui��o de Liskov"*. O conceito que originou esse princ�pio � bastante acad�mico, do tipo que um profissional que n�o esteja acostumado com termos e racioc�nios acad�rmicos provavelmente n�o entender� na primeira tentativa.
O princ�pio foi nomeado pelo nome de sua autora [Barbara Liskov][barbara-liskov].
O conceito, que veremos no post desse t�pico, � equivalente ao seguinte *"Deve ser poss�vel substituir uma classe base por suas classes derivadas"*. E � t�o simples como parece, at� ver sua origem.


## Interface Segregation Principle

O ISP, "Princ�pio de Segrega��o de Interface" espec�fica que clientes n�o devem ser for�ados a depender de interfaces que n�o usam. Ou seja, n�o criar contratos que nem todos os clientes possa implementar, mas sim criar contrato ~*interfaces*~ menores para que seus clientes as implementem por completo.


## Dependency Inversion Principle

E por �ltimo o DIP, ou "Princ�pio de Invers�o de Depend�ncia", nos diz duas coisas. M�dulos de alto n�vel n�o devem depender de m�dulos de baixo n�vel. E que abstra��es n�o devem depender de detalhes, mas detalhes devem depender de abstra��es.
� um princ�pio extremamente �til para mater seus m�dulos desacoplados e test�veis. Existem diversas ferramentas, al�m de outras pr�ticas, que nos auxiliam a utilizar esse princ�pio com mais efici�ncia.


Como eu disse, nos pr�ximos post veremos com mais detalhes cada um dos princ�pios.


Vou deixar aqui os slides de uma apresenta��o que fiz na empresa que trabalho atualmente. Sei que n�o � muito �til ~*principalmente esses meus*~, mas para quem quiser dar uma conferida est� a�.

<div style="width:425px" id="__ss_12226756"> <strong style="display:block;margin:12px 0 4px"><a href="http://www.slideshare.net/dyegocosta/princpios-solid-12226756" title="Princ�pios solid" target="_blank">Princ�pios solid</a></strong> <iframe src="http://www.slideshare.net/slideshow/embed_code/12226756" width="425" height="355" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe> </div><br />

[oop]:http://dyegocosta.com/category/oop
[uncle-bob]:http://en.wikipedia.org/wiki/Robert_Cecil_Martin
[srp]:http://dyegocosta.com/tags/srp
[barbara-liskov]:http://en.wikipedia.org/wiki/Barbara_Liskov