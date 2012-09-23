--- 
layout: post
title: 'Primeiros passos com o Selenium WebDriver'
category: Testes
tags: 
- title: Selenium
  slug: selenium
- title: Testes
  slug: testes
---

Antes de entrarmos em um cenário mais completo, vamos conhecer e dar nossos primeiros passos com o Selenium WebDriver.  
O Selenium WebDriver faz parte de um conjunto de ferramentas de automação de browser. Automação de browser? Sim, por mais que essas ferramentas 
sejam mais utilizadas para automação de testes, nada lhe impede de automatizar qualquer tarefa feita via browser. Junto com essa ferramenta 
existe o [Selenium Grid][SeleniumGrid], [Selenium RC][SeleniumRC] e o [Selenium IDE][SeleniumIDE]. 
É interessante ressaltar que essa ferramenta comporta diversos browsers e diversas linguagens de programação.

<center>
	<img title="Cheese" src="/images/cheese.jpg" class="post_img"/>
	<p class="post_img_subtitle">Se desanimou com a imagem, procure uma frase em negrito no post!</p>
</center>


## Uma breve história
O Selenium nasceu em 2004, criado por Jason Huggins, como uma biblioteca de Javascript capaz de conduzir interações com uma página web, que 
acabou se tornando o Selenium Core, utilizado pelos projeots Selenium IDE e RC.
A ferramenta Selenium WebDriver precede da ideia do [Selenium Remote Control (RC)][SeleniumRC], que ainda existe e é utilizado. O RC era uma 
grande novidade na época em que foi lançado, mas possuía algumas limitações devido a forma que foi construído. O WebDriver surgiu como um projeto paralelo,
criado por Simon Stewart nos laboratórios da Google justamente para solucionar as limitações do RC, que na época já era muito utilizado pela empresa.  
Em 2008 surge o Selenium WebDriver para a alegria de quem sofria com os pontos de limitações do RC.

## Mão na massa
Vamos ao clássico exemplo 'cheeses'. **Se você veio seco nesse post esperando um exemplo mais completo e mimimi, o que é meio difícil por causa do título, não ficará totalmente na mão!
Tenho um repositório com um exemplo mais bacana no meu GitHub, que pode ser acessado [aqui][selenium-repository]**. Pretendo escrever um post sobre esse exemplo e provavelmente deixa-lo mais legal no processo :-)

### Instalação

Sim! Podemos instalar via NuGet! Utilize o comando *Install-Package Selenium.Support* no *Package Manage Console*

<center>
	<img title="Instalação" alt="Instalação" src="/images/selenium-install.JPG" class="post_img"/>
</center>

Para quem não gosta do Console, é só pesquisar por *Selenium.Support* no *Manage NuGet Packages* :-P

### O código

É muito simples!

<pre name="code" class="c-sharp">
[TestMethod]
public void MeuTesteSuperMassaSoQueNao()
{
    IWebDriver driver = new FirefoxDriver();

    driver.Navigate().GoToUrl("http://www.google.com/");

    IWebElement query = driver.FindElement(By.Name("q"));

    query.SendKeys("Cheese");

    query.Submit();

    WebDriverWait wait = new WebDriverWait(driver, TimeSpan.FromSeconds(10));
    wait.Until((d) => { return d.Title.ToLower().StartsWith("cheese"); });

    driver.Title.Should().Contain("cheese");

    driver.Quit();
}
</pre>

Como podem ver, o código é autoexplicativo.
Estamos obtendo um IWebDriver, que representa o browser que iremos utilizar, e navegando para um endereço com ele.  
Em seguida buscamos um elemento na página, preenchemos e o submentemos, e assim aguardamos até que a página tenha uma particular aparência 
que esperamos. No final fechamos o browser.


Por enquanto ficamos por aqui, logo teremos mais!  
Abraços o/

[SeleniumGrid]:http://seleniumhq.org/projects/grid/
[SeleniumIDE]:http://seleniumhq.org/projects/ide/
[SeleniumRC]:http://seleniumhq.org/projects/remote-control/
[selenium-repository]:https://github.com/DyegoCosta/SeleniumSample