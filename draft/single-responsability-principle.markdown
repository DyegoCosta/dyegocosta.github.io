--- 
layout: post
title: 'Single Responsability Principle'
category: OOP
tags: 
- title: SOLID
  slug: solid
- title: Princ&iacute;pios SOLID
  slug: principios-solid  
- title: OOP
  slug: oop
---

Quando uma classe ou m�todo ~n�o se limitando a eles~ possui diversas responsabilidades, a possibilidade da necessiade de mudan�a � mais alta. 
Com essa possibilidade, h� mais chances de uma mudan�a quebrar o c�digo e caso isso aconte�a, ser� muito mais dif�cil identificar o problema.
Al�m disso, a testabilidade desta classe ser� comprometida, pois em um cen�rio em que estamos testando unidades da aplica��o, seria mais trabalhoso e menos eficiente testar algo que possui mais de uma responsabilidade. 
O SRP, ou em portugu�s "Princ�pio de Responsabilidade �nica" diz que todo objeto deve ter um �nica responsabilidade, e que a responsabilidade deve estar encapsulada pela classe.
Ou com as palavras de Robert C. Martin ~aka Uncle Bob~, "Uma classe deve ter apenas um motivo para mudar".

{{ /images/great-power-equals-great-responsability.jpg | image_tag }}
<img title="Wolverine" src="/images/great-power-equals-great-responsability.jpg" class="post_img"/>
<p class="post_img_subtitle">Vamos ouvir o Tio Ben e deixar os grandes poderes e responsabilidades para nosso amigo Wolverine.</p>

Pode parecer estranho para quem n�o est� acostumado com esse tipo de pr�tica, mas ao aplic�-la, podemos notar um aumento significante de nosso m�todos e classes.
Feito de maneira correta, isso � �timo, apesar do inicial smell antes de acostumar.

## The Stepdown Rule

No livro [Clean Code][clean-code], o Uncle Bob nos explica a "The Stepdown Rule"* que pode ser identificada como a aplica��o do SRP.
Essa regra nos ensina a escrever um c�digo que possa ser lido em um mesmo n�vel abstra��o.
Ao ler um m�todo podemos esperar que ele execute mais de uma funcionalidade para chegar em um resultado final, por exemplo, para obtermos um resultado temos que fazer uma valida��o de nossos inputs, dois c�lculo diferentes e algo mais, antes de retornar esse resultado. 
Tendo isso em mente, para cada particularidade do m�todo escreveremos outro m�todo ~em boa parte das vezes eles ser�o privados, a menos que voc� identifique que uma a��o � de responsabilidade de outra classe~. 
Fazendo isso, teremos um m�todo que chama diversos menores ~provavelmente n�o tantos n�?~ e poderemos ler muito mais facilmente esse m�todo composto.

Vamos dar uma olhada em um exemplo mostrado no livro [Agile Principles, Patterns and Practices in C#][agile-csharp-book], tamb�m do meu autor favorito, Uncle Bob**.


## C�digo ruim



## Responsabilidades delegadas




\* � muito estranho citar algo que comece com ~the~, porque fica ~a the~ ou ~a a~ :-(
** Esperem ver muitas cita��es desse autor em meus textos :-)

[clean-code]:
[agile-csharp-book]: