--- 
layout: post
title: 'Utilizando o Windows Azure Online Backup'
category: 'Windows Azure'
keywords: "azure, windows azure, cloud, nuvem, computacao nas nuvens, internet, cloud computing, windows, microsoft, backup, online backup, windows azure online backup"
tags: 
- title: Backup
  slug: backup
- title: Windows Server 2012
  slug: windows-server-2012
---

Nessa última semana eu vesti o boné de infra para testar o preview do Windows Azure Online Backup em uma máquina com o Windows Server 2012 Datacenter. De fato o processo para que você possa manter suas cópias de segurança nas nuvens é trivial, muito fácil.

Foi bem divertido o desafio, já que nunca trabalhei com o Windows Server. Subi uma VM com o Windows Server 2012 Datacenter, instalei algumas roles e features, configurei um domínio no AD, criei um usuário e fiz um backup local. Coisas banais mas divertidas pra mim, por não ser o meu dia-a-dia. Toda essa parte com a ajuda de meu amigo [João Fuzinelli][fenrizio] :-)

Atualmente este serviço está na versão de avaliação e é suportado nos ambientes Windows Server 2012, Windows Server 2012 Essentials, e System Center 2012.

Para utilizar o serviço é necessário que faça sua inscrição para a versão de avaliação através deste [link][online-backup-register], que é para um contrato de seis meses gratuitos de avaliação. Tendo feito o cadastro, é necessário que você baixe e instale o agente de backup em seu ambiente. O agente pode ser baixado através deste [link][agente].

## Registro do servidor

Tendo se cadastrado e instalado o agente, é necessário que você registre seu ambiente para a utilização do serviço, que pode ser feito via interface gráfica ou via PowerShell.  
Na imagem abaixo você pode visualizar onde iniciar o registro através da interface gráfica do agente.

<img src="/posts_images/15-01-agente.jpg" class="post_img" style="width: 90%;"/>

Através da interface gráfica é um passo-a-passo bem sugestivo e simples de seguir, então demonstrarei como é feito o registro via PowerShell. O registro via interface gráfica segue os mesmos passos.

<pre name="code" class="ruby">
	# Credenciais do serviço
	$pwd = ConvertTo-SecureString -String "m!nh@S3nh@" -AsPlainText -Force
	$cred = New-Object -TypeName System.Management.Automation.PsCredential -ArgumentList "usuairo@endereco.onmicrosoft.com", $pwd
	Start-OBRegistration -Credential $cred
	 
	# Definição do Proxy (se houver)
	$pwd = ConvertTo-SecureString -String "SenhaDeMeuProxy" -AsPlainText -Force
	Set-OBMachineSetting -ProxyServer "MeuServidorDeProxy" -ProxyPort 80 -ProxyUsername "Dominio\MeuUsuario" -ProxyPassword $pwd
 
	# Definição da chave de criptografia

	$pass = ConvertTo-SecureString -String "1234567890123456" -AsPlainText -Force
	Set-OBMachineSetting -EncryptionPassphrase $pass
</pre>

## Política e cópia instantânea

Para o agendamento de uma cópia de segurança é preciso criar uma política de backup, nela será configurado a periodicidade e a agenda do serviço, o local do qual será feito a cópia e também por quanto tempo as cópias feitas na nuvem serão mantidas.

<pre name="code" class="ruby">
	$policy = New-OBPolicy
	$filespec = New-OBFileSpec -FileSpec C:\temp # Local do qual será feito a cópia de segurança na nuvem
	$sched = New-OBSchedule -DaysOfWeek "Monday" -TimesOfDay "09:30" # Periodicidade e agenda do backup
	$ret = New-OBRetentionPolicy
	 
	Add-OBFileSpec -Policy $policy -FileSpec $filespec
	Set-OBSchedule -Policy $policy -Schedule $sched
	Set-OBRetentionPolicy -Policy $policy -RetentionPolicy $ret
	 
	Set-OBPolicy -Policy $policy
</pre>

Tendo criado a política você já pode ficar seguro de que nos horários da agenda configurada serão feitas as cópias de segurança para a nuvem, as quais poderão ser recuperadas durante seu período de vida, que também foi definido na política.  
Utilizando essa política também é possível fazer um backup instantâneo, o qual utilizará as configurações da política e criara o backup na hora.  
Para criação de um backup instantâneo através de uma política existente é utilizado o comando abaixo.

<pre name="code" class="ruby">
	Get-OBPolicy|Start-OBBAckup
</pre>

## Recuperando seus dados

É possível recuperar a última cópia de segurança feita através do script abaixo. Sendo que o parametro "DestinationPath" é o local para onde será recuperado os dados na nuvem.

<pre name="code" class="ruby">
	$sources = Get-OBRecoverableSource
	$RP = Get-OBRecoverableItem -Source $sources[0]
	$RO = New-OBRecoveryOption -overwritetype overwrite -DestinationPath C:\\Restauracao
	 
	Start-OBRecovery -RecoverableItem $RP -RecoveryOption $RO -Async
</pre>

## Qual é o antônimo de registrar?

Durma com essa.  
Caso você queira cancelar o registro do seu ambiente, é muito simples. Utilizando o script abaixo o registro será cancelado. Nesse caso, ao invés de adicionar as credenciais eu estou a requisitando para que não rode de uma só vez, mas nada te impede de passa-la direto no script.

<pre name="code" class="ruby">
	Start-OBUnregistration -Credential (get-credential)
</pre>

## Onde estão seus arquivos

Na imagem a baixo você pode ver os atuais servidores e seu status, onde estão armazenados as cópias de segurança feitas através do serviço. Essa informação pode ser vista através do [portal][portal] do Windows Azure Backup.

<img src="/posts_images/15-01-service-health.jpg" class="post_img" />

É válido ressaltar que este serviço ainda está em versão de avaliação e ainda não está disponível para todos os países.

[online-backup-register]: https://activedirectory.windowsazure.com/Signup/MainSignUp.aspx?OfferId=6061479A-02FA-46f0-9DA0-244298C3CD7B&culture=en&ali=1
[agente]: http://g.microsoftonline.com/0OB00EN/004
[portal]: https://portal.onlinebackup.microsoft.com/en-US/Dashboard
[fenrizio]: https://twitter.com/fenrizio