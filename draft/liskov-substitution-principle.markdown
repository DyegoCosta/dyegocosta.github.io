--- 
layout: post
title: 'Liskov Substitution Principle'
category: OOP
tags: 
- title: SOLID
  slug: solid
- title: Princ&iacute;pios SOLID
  slug: principios-solid  
- title: OOP
  slug: oop
---
Esse princ�pio pode aparentar ser o mais complexo de se entender, mas n�o �. Bom, depende.
O LSP parece ser complexo pois foi descrito inicialmente de forma academica por [Barbara_Liskov][Barbara Liskov], e devido sua formalidade, ele pode n�o ser t�o claro.
Sua defini��o inicial pode ser descrita como abaixo.
<p class="quote">
	Se para cada objeto **o1** do tipo **S** existe um objeto **o2** do tipo T, tal que, para todos os programas **P** definidos em termos de **T*, 
	o comportamento de **P** fica inalterado quando **o1** � substitui�do por **o2**, ent�o **S** � um subtipo de **T**.
</p>
Isso de fato assusta inicialmente. Mas mais uma vez podemos contar com Robert C. Martin para nos simplificar a ideia. E em suas palavras podemos definir o LSP como abaixo.
<p class="quote">
	Os subtipos devem ser substitu�veis pelos seus tipos de base.
</p>
Simples assim. Depois de entender de maneira simplificada, at� sua defini��o formal se torna clara. Ent�o depois de terminar de ler o post, espero que seja capaz de entender a primeira defini��o citada.

[Barbara_Liskov]:http://en.wikipedia.org/wiki/Barbara_Liskov