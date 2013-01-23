--- 
layout: post
title: "Solu&ccedil;&otilde;es de m&iacute;dias de ponta-a-ponta na nuvem com o Windows Azure Media Services"
category: Windows Azure
tags: 
- title: Windows Azure Media Services
  slug: windows-azure-media-services
---

Começa aqui uma série na qual irei destrinchar as funcionalidades do Windows Azure Media Services. Veremos como aproveitar o poder da nuvem para trabalhar de ponta-a-ponta com soluções de mídias.  
"Let's the game begin"

<img src="/posts_images/22-01-bane.jpg" class="post_img" />   

## Para o que estamos olhando aqui?

Para o Windows Azure Media Services.
*Windows Azure Media Services* é um conjunto de componentes para criação de workflows de mídias customizados em um ambiente flexível, escalável e segurço. Com esse serviço você pode criar workflows para diversos fins, o suporte vai desde o transporte das mídias para a nuvem até a entrega deste conteúdo para qualquer disposítivo suportado, praticamente qualquer um. 
Vai depender da ideia e necessidade de seu negócio na hora de escolher o que usar do serviço, pois cada componente pode atender demandas diferentes.

<img src="/posts_images/22-01-media-services.png" class="post_img" />   

### Ingest  

A primeira coisa que você quer fazer é subir seu conteúdo pra nuvem e para isso você pode optar por transferir via HTTP/HTTPS ou via UDP, o que torna a transferencia bem mais rápida.  
Também é possível fazer uma pré-criptografia do arquivo antes de armazena-lo na nuvem




## Motivações

Por que esse serviço existe? Porque a Microsoft quis :-P  
YouTube, Netflix, Hulu, Quickflix, etc. Esses são exemplos de alguns serviços disponibilizados sobre uma plataforma de entrega de mídias. Esse mercado está crescendo absurdamente, dica. O Windows Azure Media Services está aí também para suprir esse mercado, dando suporte completo para a entrega de mídias de uma maneira fácil e poderosa.

Por que eu estou escrevendo sobre isso? Geralmente a resposta seria "porque eu quero", o que é meio obvio, mas dessa vez o que mais me motivou a aprender e trazer pra cá sobre esse assunto é o fato de que podemos encontrar facilmente vários posts falando que esse serviço existe, mas não como funciona (além de na documentação né gente, pfv). Então vamos pular de cabeça no que temos disponível hoje para aprender tudo que esse serviço nos prove *atualmente*.