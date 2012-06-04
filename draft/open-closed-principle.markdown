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

A ideia do OCP ou em português *"Princípio Aberto/Fechado"* é manter entidades da aplicação abertas para extensão, mas fechadas para modificação.
Evita a criação de bugs em códigos funcionais e facilita a extensão apesar da complexidade introduzida para a implementação dessa estrutura.

<img title="Porta holandesa" src="/images/great-power-equals-great-responsability.jpg" class="post_img"/>
<p class="post_img_subtitle">Você não quer substituir todas as portas de sua casa por uma dessas, certo? ~nada a ver~.</p>

Esse princípio só deve ser utilizado em módulos que mudam com certa frequência e difícilmente será aplicado no design inicial de sua aplicação.
A menos que você tenha certeza de que um certo código irá mudar, falando em extensão que poderá ser visto no exemplo, não recomendo que utilize esse princípio.

