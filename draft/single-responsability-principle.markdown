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

Quando uma classe ou método ~não se limitando a eles~ possui diversas responsabilidades, a possibilidade da necessiade de mudança é mais alta. 
Com essa possibilidade, há mais chances de uma mudança quebrar o código e caso isso aconteça, será muito mais difícil identificar o problema.
Além disso, a testabilidade desta classe será comprometida, pois em um cenário em que estamos testando unidades da aplicação, seria mais trabalhoso e menos eficiente testar algo que possui mais de uma responsabilidade. 
O SRP, ou em português "Princípio de Responsabilidade Única" diz que todo objeto deve ter um única responsabilidade, e que a responsabilidade deve estar encapsulada pela classe.
Ou com as palavras de Robert C. Martin ~aka Uncle Bob~, "Uma classe deve ter apenas um motivo para mudar".

{{ /images/great-power-equals-great-responsability.jpg | image_tag }}
<img title="Wolverine" src="/images/great-power-equals-great-responsability.jpg" class="post_img"/>
<p class="post_img_subtitle">Vamos ouvir o Tio Ben e deixar os grandes poderes e responsabilidades para nosso amigo Wolverine.</p>

Pode parecer estranho para quem não está acostumado com esse tipo de prática, mas ao aplicá-la, podemos notar um aumento significante de nosso métodos e classes.
Feito de maneira correta, isso é ótimo, apesar do inicial smell antes de acostumar.

## The Stepdown Rule

No livro [Clean Code][clean-code], o Uncle Bob nos explica a "The Stepdown Rule"* que pode ser identificada como a aplicação do SRP.
Essa regra nos ensina a escrever um código que possa ser lido em um mesmo nível abstração.
Ao ler um método podemos esperar que ele execute mais de uma funcionalidade para chegar em um resultado final, por exemplo, para obtermos um resultado temos que fazer uma validação de nossos inputs, dois cálculo diferentes e algo mais, antes de retornar esse resultado. 
Tendo isso em mente, para cada particularidade do método escreveremos outro método ~em boa parte das vezes eles serão privados, a menos que você identifique que uma ação é de responsabilidade de outra classe~. 
Fazendo isso, teremos um método que chama diversos menores ~provavelmente não tantos né?~ e poderemos ler muito mais facilmente esse método composto.

Vamos dar uma olhada em um exemplo mostrado no livro [Agile Principles, Patterns and Practices in C#][agile-csharp-book], também do meu autor favorito, Uncle Bob**.


## Código ruim



## Responsabilidades delegadas




\* É muito estranho citar algo que comece com ~the~, porque fica ~a the~ ou ~a a~ :-(
** Esperem ver muitas citações desse autor em meus textos :-)

[clean-code]:
[agile-csharp-book]: