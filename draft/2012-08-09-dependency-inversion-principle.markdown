--- 
layout: post
title: 'Dependency Inversion Principle'
category: OOP
tags: 
- title: SOLID
  slug: solid
- title: Princ&iacute;pios SOLID
  slug: principios-solid  
- title: OOP
  slug: oop
---

Fechando a série de posts com a visão geral dos princípios SOLID, temos o Dependency Inversion Principle.  
Esse princípio possui duas abordagens, primeiramente que um módulo de alto nível não deve depender de outro de baixo nível, e além disso, que abstrações não devem dependender de detalhes. 
Vamos nos alinhar com cada uma delas.

<img alt="" src="/images/cat-and-fish.jpg" class="post_img"/>

## Alto e baixo nível

O princípio presa que um módulo de alto nível não deve depender de outro(s) de baixo nível, mas que ambos devem depender de abstrações.
Um módulo de alto nível está relacionado a entidades de negócio e de interação com o usuário, e baixo nível está relacionado a entidades de infraestrutura, como módulos de persistencia. 
Mas por que não é recomendável que um módulo dependa do outro? 