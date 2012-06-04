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

A ideia do OCP ou em portugu�s *"Princ�pio Aberto/Fechado"* � manter entidades da aplica��o abertas para extens�o, mas fechadas para modifica��o.
Evita a cria��o de bugs em c�digos funcionais e facilita a extens�o apesar da complexidade introduzida para a implementa��o dessa estrutura.

<img title="Porta holandesa" src="/images/great-power-equals-great-responsability.jpg" class="post_img"/>
<p class="post_img_subtitle">Voc� n�o quer substituir todas as portas de sua casa por uma dessas, certo? ~nada a ver~.</p>

Esse princ�pio s� deve ser utilizado em m�dulos que mudam com certa frequ�ncia e dif�cilmente ser� aplicado no design inicial de sua aplica��o.
A menos que voc� tenha certeza de que um certo c�digo ir� mudar, falando em extens�o que poder� ser visto no exemplo, n�o recomendo que utilize esse princ�pio.

