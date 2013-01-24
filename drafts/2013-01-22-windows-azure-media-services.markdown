--- 
layout: post
title: "Solu&ccedil;&otilde;es de m&iacute;dias na nuvem com o Windows Azure Media Services"
category: Windows Azure
tags: 
- title: Windows Azure Media Services
  slug: windows-azure-media-services
---

Começa aqui uma série na qual irei destrinchar as funcionalidades do Windows Azure Media Services. Veremos como aproveitar o poder da nuvem para trabalhar de ponta-a-ponta com soluções de mídias.  
"Let's the game begin"

<img src="/posts_images/22-01-bane.jpg" class="post_img" />   

## Para o que estamos olhando aqui?

O **Windows Azure Media Services** é um conjunto de componentes para criação de workflows de mídias customizados em um ambiente flexível, escalável e segurço. Com esse serviço você pode criar workflows para diversos fins, o suporte vai desde o transporte das mídias para a nuvem até a entrega deste conteúdo para qualquer disposítivo suportado, praticamente qualquer um. 
Vai depender da ideia e necessidade de seu negócio na hora de escolher o que usar do serviço, pois cada componente pode atender demandas diferentes.

<img src="/posts_images/22-01-media-services.png" class="post_img" />   

### Ingest  

A primeira coisa que você quer fazer é subir seu conteúdo pra nuvem e para isso você pode optar por transferir via HTTP/HTTPS. Também é possível fazer o upload via UDP, que torna a transferência bem mais rápida do que via HTTP.  
Também é possível fazer uma pré-criptografia (AES 256) do arquivo antes de armazena-lo na nuvem

### Encoding

Atualmente o Windows Azure Media Encoder suporta diversos formatos, o que levará a sua decisão de quando usar um ou outro é o tipo de aparelho para o qual você irá entregar essa mídia.
Você pode ver uma lista completa dos atuais formatos de mídia, tanto de importação como para exportação, através deste [link][encoding].  
Também é possível utilizar encoders de terceiros, que estão disponíveis no [Windows Azure Marketplace][mkt_place].

### Content protection

Nem sempre você quer disponbilizar seu conteúdo publicamente. A proteção de conteúdo se torna bastante interessante quando você quer monetizar o que está distribuido.  
As atuais formas de criptografia são o [PlayReady][playready], Common Encryption e AES, e essas tecnologias estão disponíveis para os conteúdos transmitidos via [Smooth Streaming][smooth-streaming] e/ou [Apple HLS][apple-hls]. Mas também é válido lembrar que a Microsoft está criando vínculos com outras empresas para disponilizarem novas formas de proteção de conteúdo, assim como estão fazendo para todos os outros componentes do serviço.

### On-Demand Streaming

O componente está integrado com o Azure CDN (e também com CDN de terceiros, Akamai), então todo o conteúdo distribuido sob demanda será enviado dos servidores mais próximos de quem está requisitando.  
Largura de banda garantida, assim como auto recovery, redundância de conteúdo para caso de queda e alta disponbilidade.
Uma coisa bacana de se fazer streaming com esse serviço é o Dynamic Remux que permite que você tenha armazenado seu conteúdo de vídeo no formato MP4 e o disponibilize em diversos outros formatos, o que reduz o espaço de armazenamento utilizado, logo, o custo.

## Motivações

YouTube, Netflix, Hulu, Quickflix, etc. Esses são exemplos de alguns serviços disponibilizados sobre uma plataforma de entrega de mídias. Esse mercado está crescendo absurdamente, dica. O Windows Azure Media Services está aí também para suprir esse mercado, dando suporte completo para a entrega de mídias de uma maneira fácil e poderosa.

O que mais me motivou a aprender e compartilhar sobre esse assunto é o fato de que podemos encontrar facilmente vários lugares falando que esse serviço existe, mas não como funciona (além de na documentação né, pfv). Então vamos pular de cabeça no que temos disponível hoje para aprender tudo que esse serviço nos prove *atualmente*.

[encoding]: http://msdn.microsoft.com/en-us/library/windowsazure/hh973634.aspx#import_formats
[mkt_place]: https://datamarket.azure.com/
[smooth-streaming]: http://www.iis.net/downloads/microsoft/smooth-streaming
[apple-hls]: https://developer.apple.com/resources/http-streaming/
[playready]: http://en.wikipedia.org/wiki/PlayReady