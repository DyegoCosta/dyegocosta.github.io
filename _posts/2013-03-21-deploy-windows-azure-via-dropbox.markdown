--- 
layout: post
title: "Windows Azure <3 Dropbox"
category: Windows Azure
keywords: "azure, windows azure, cloud, nuvem, computacao nas nuvens, internet, cloud computing, windows, microsoft,dropbox,deploy,deploy automatizado,windows azure web sites,web sites,skydrive,Windows Azure SDK,sdk"
tags: 
- title: Windows Azure Web Sites
  slug: windows-azure-web-sites
---
Atualmente existem diversas maneiras de publicar uma aplicação ou site utilizando o Windows Azure Web Sites e uma delas é através do Dropbox.  
O [Dropbox][dropbox] é um serviço para armazenamento e compartilhamento de arquivos na nuvem (fotos, documentos, vídeos, etc) muito utilizado tanto para uso pessoal como empresarial.  

O processo é publicação é muito simples, basta autorizarmos o Windows Azure a utilizar nosso serviço Dropbox, essa autorização criará uma nova pasta compartilhada (geralmente no caminho */Dropbox/Apps/Azure*) em que poderemos manter nossa aplicação/site para publicação.
Esse método de publicação é válido para todos os tipos de projeto suportado pelo serviço Windows Azure SDK, nesse exemplo publicaremos uma aplicação ASP.NET MVC.  

Podemos ir no [portal do Windows Azure][portal] e criar nosso Windows Azure Web Site utilizando escolhendo o Dropbox como o serviço de publicação.

<img src="/posts_images/Parte1_criando site.png" class="post_img" />
<img src="/posts_images/Parte2_criando site.png" class="post_img" />
<img src="/posts_images/Parte3_criando site.png" class="post_img" />

Será requisitado que você de acesso o serviço do Windows Azure em seu Dropbox.

<img src="/posts_images/Autorizando dropbox.png" class="post_img" />   

Você terá a opção de criar uma nova pasta ou já utilizar alguma existente, como já tenho meu projeto criado eu apenas moverei ele para a pasta em que o Windows Azure tem acesso e o escolherei.

<img src="/posts_images/escolhendo pasta.png" class="post_img" />   

E pronto! Se não houver nada de errado com nossa aplicação, ela estará no ar após o processo de publicação.

<img src="/posts_images/publicado.png" class="post_img" />   

Caso queira publicar alguma alteração feita basta utilizar o botão "Sync" que o Windows Azure realizará uma nova publicação e assim como nas outras formas de publicação será mantido o histórico de publicação tornando muito simples a possibilidade de retornar a alguma versão anterior.  

O site foi realmente publicado! :-)  
[http://azurelovesdropbox.azurewebsites.net/][http://azurelovesdropbox.azurewebsites.net/]

É isso pessoal, bem simples.  
Abraços

[dropbox]: http://www.dropbox.com
[portal]: http://manage.windowsazure.com
[http://azurelovesdropbox.azurewebsites.net/]:http://azurelovesdropbox.azurewebsites.net/