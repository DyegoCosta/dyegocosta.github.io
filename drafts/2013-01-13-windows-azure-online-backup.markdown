--- 
layout: post
title: 'Utilizando o Windows Azure Online Backup'
category: Windows Azure
tags: 
- title: Backup
  slug: backup
- title: Windows Server 2012
  slug: windows-server-2012
- title: Cloud
  slug: cloud
---

Nessa última semana eu vesti o boné de infra para testar o preview do Windows Azure Online Backup em uma máquina com o Windows Server 2012 Datacenter. De fato o processo para que você possa manter suas cópias de segurança nas nuvens é trivial, muito fácil.

Foi bem divertido o desafio, já que nunca trabalhei com o Windows Server. Subi uma VM com o Windows Server 2012 Datacenter, instalei algumas roles e features, configurei um domínio no AD, criei um usuário e fiz um backup local. Coisas banais mas divertidas pra mim, por não ser o meu dia-a-dia. Tudo isso com a ajuda de meu amigo [João Fuzinelli][fenrizio] :-)

Atualmente este serviço está na versão de avaliação, e é suportado nos ambientes Windows Server 2012, Windows Server 2012 Essentials, e System Center 2012.

Para utilizar o serviço é necessário que faça sua inscrição para a versão de avaliação através deste [link][online-backup-register], que é para um contrato de seis meses gratuitos de avaliação. Tendo feito o cadastro, é necessário que você baixe e instale o agente de backup em seu ambiente. O agente pode ser baixado através deste [link][agente].

## Registro do servidor

Tendo se cadastrado e instalado o agente, é necessário que você registre seu ambiente para a utilização do serviço, que pode ser feito via interface gráfica ou via PowerShell.  
Na imagem abaixo você pode visualizar onde iniciar o registro através da interface gráfica do agente.

<img src="/posts_images/15-01-agente.jpg" class="post_img" style="width: 90%;"/>

Através da interface gráfica é um passo-a-passo bem sugestivo e simples de seguir, então demonstrarei como é feito o registro via PowerShell. O registro via interface gráfica segue os mesmos passos.

<script src="https://gist.github.com/4490110.js?file=Registro.ps1"></script>

## Política e cópia instantânea

Para o agendamento de uma cópia de segurança é preciso criar uma política de backup, nela será configurado a periodicidade e a agenda do serviço, o local do qual será feito a cópia e também por quanto tempo as cópias feitas na nuvem serão mantidas.

<script src="https://gist.github.com/4542927.js?file=Política.ps1"></script>

Tendo criado a política você já pode ficar seguro de que nos horarios da agenda configurada serão feitas as cópias de segurança para a nuvem, as quais poderão ser recuperadas durante seu período de vida, que também foi definido na política.  
Utilizando essa política também é possível fazer um backup instantâneo, o qual utilizará as configurações da política e criara o backup na hora.  
Para criação de um backup instantâneo através de uma política existente é utilizado o comando abaixo.

<script src="https://gist.github.com/4543181.js?file=Backup_now.ps1"></script>

## Onde estão seus arquivos

Na imagem a baixo você pode ver os atuais servidores, e seu status, onde estão armazenados as cópias de segurança feitas através do serviço. Essa informação pode ser vista através do [portal][portal] do Windows Azure Backup.

<img src="/posts_images/15-01-service-health.jpg" class="post_img" />

[online-backup-register]: https://activedirectory.windowsazure.com/Signup/MainSignUp.aspx?OfferId=6061479A-02FA-46f0-9DA0-244298C3CD7B&culture=en&ali=1
[agente]: http://g.microsoftonline.com/0OB00EN/004
[portal]: https://portal.onlinebackup.microsoft.com/en-US/Dashboard
[fenrizio]: https://twitter.com/fenrizio