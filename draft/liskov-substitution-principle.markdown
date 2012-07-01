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
Esse princípio pode aparentar ser o mais complexo de se entender, mas não é. Bom, depende.
O LSP parece ser complexo pois foi descrito inicialmente de forma academica por [Barbara_Liskov][Barbara Liskov], e devido sua formalidade, ele pode não ser tão claro.
Sua definição inicial pode ser descrita como abaixo.
<p class="quote">
	Se para cada objeto **o1** do tipo **S** existe um objeto **o2** do tipo T, tal que, para todos os programas **P** definidos em termos de **T*, 
	o comportamento de **P** fica inalterado quando **o1** é substituiído por **o2**, então **S** é um subtipo de **T**.
</p>
Isso de fato assusta inicialmente. Mas mais uma vez podemos contar com Robert C. Martin para nos simplificar a ideia. E em suas palavras podemos definir o LSP como abaixo.
<p class="quote">
	Os subtipos devem ser substituíveis pelos seus tipos de base.
</p>
Simples assim. Depois de entender de maneira simplificada, até sua definição formal se torna clara. Então depois de terminar de ler o post, espero que seja capaz de entender a primeira definição citada.

[Barbara_Liskov]:http://en.wikipedia.org/wiki/Barbara_Liskov