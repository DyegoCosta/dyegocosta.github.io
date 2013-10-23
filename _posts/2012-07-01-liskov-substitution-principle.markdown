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
Nos princípios SOLID, esse pode aparentar ser o mais complexo de se entender, mas não é. Bom, depende.
O LSP parece ser complexo pois foi descrito inicialmente de forma academica, e devido sua formalidade, ele pode não ser tão claro.
Sua definição inicial, escrita por [Barbara Liskov][Barbara_Liskov], pode ser descrita como abaixo.
<p class="quote">
	Se para cada objeto o&sup1; do tipo S existe um objeto o&sup2; do tipo T, tal que, para todos os programas P definidos em termos de T, 
	o comportamento de P fica inalterado quando o&sup1; é substituiído por o&sup2;, então S é um subtipo de T.
</p>



<img title="Mr. Bean" src="/images/wtf_bean.jpg" class="post_img"/>



Isso de fato assusta inicialmente ~*me assustou*~. Mas mais uma vez podemos (pude) contar com Robert C. Martin para nos (me) simplificar a ideia. E em suas palavras podemos definir o LSP como abaixo.
<p class="quote">
	Os subtipos devem ser substituíveis pelos seus tipos de base.
</p>
Simples assim. Depois de entender de maneira simplificada, até sua definição formal se torna clara. Então depois de terminar de ler o post, espero que seja capaz de entender a primeira definição citada.


Utilizaremos um exemplo bastante comum para a definição desse princípio. Usaremos as entidades Retangulo e Quadrado e veremos como podemos relaciona-las de uma maneira que não fira o LSP.

##É-Um
É-Um é um termo bastante utilizado em Análise Orientada a Objetos, mas raramente definido. O Quadrado é um Retangulo, sendo assim, o Quadrado deve derivar de Retangulo, certo?
Nem sempre, e não nesse caso. Erros assim são comuns e geralmente são identificados apenas depois de vistos no código.

##Le código

###A violação
<pre name="code" class="c-sharp">
	public class Retangulo
    {
        protected double Altura { get; set; }
        protected double Largura { get; set; }

        public virtual void DefinirAltura(double altura)
        {
            Altura = altura;
        }

        public virtual void DefinirLargura(double largura)
        {
            Largura = largura;
        }

        public virtual double Area()
        {
            return Altura * Largura;
        }
    }
	
	public class Quadrado : Retangulo
    {
        public override void DefinirAltura(double altura)
        {
            Altura = altura;
            Largura = altura;
        }

        public override void DefinirLargura(double largura)
        {
            Largura = largura;
            Altura = largura;
        }

        public override double Area()
        {
            return Altura * Altura;
        }
    }
</pre>

Não podemos esperar que o teste abaixo passe da mesma forma em que foi escrito caso eu queira testar o comportamento do Quadrado em relação a obtenção de sua área.
Note que para o Retangulo eu preciso definir a altura e largura, pois dependo dos dois para o cálculo da área. Para o quadrado é o mesmo, mas como a altura e largura sempre serão iguais, sobreescrevemos métodos para quando alteramos uma, a outra também será alterada para o mesmo valor.
Isso quebraria nosso teste caso utilizássemos o Quadrado, pois não posso esperar a mesma área, já que ao chamar o método DefinirLargura() depois do método DefinirAltura(), a altura será redefinida pelo DefinirLargura.

<pre name="code" class="c-sharp">
	[TestMethod]
    public void Calculo_Da_Area_Do_Retangulo()
    {
        // Arrange
        Retangulo retângulo = new Retangulo();            
		retângulo.DefinirAltura(10m);
        retângulo.DefinirLargura(20m);
		
        // Act
        var area = retângulo.Area();

        // Assert
        Assert.AreEqual(200m, area);
    }
</pre>

O <strong>É-Um</strong> está relacionado ao comportamento, sendo assim, podemos notar que esse conceito não é válido para esse caso, pois o comportamento do Quadrado não é compatível com as necessidades do Retangulo.

###Repensando
<pre name="code" class="c-sharp">
	public abstract class FormaGeometrica
    {
        public abstract double Area();
    }
</pre>

<pre name="code" class="c-sharp">
	public class Quadrado : FormaGeometrica
    {
        public double TamanhoLados { get; set; }

        public void SetTamanhoLados(double tamanhoLados)
        {
            TamanhoLados = tamanhoLados;
        }

        public override double Area()
        {
            return Math.Pow(TamanhoLados, 2d);
        }
    }
	
	public class Retangulo : FormaGeometrica
    {
        public double Altura { get; private set; }
        public double Largura { get; private set; }

        public virtual void SetAltura(double altura)
        {
            Altura = altura;
        }

        public virtual void SetLargura(double largura)
        {
            Largura = largura;
        }

        public override double Area()
        {
            return Altura * Largura;
        }
    }
</pre>

Nesse caso um Quadrado não pode ser um Retangulo, mas os dois podem ser uma FormaGeometrica. Então, delegamos cada necessidade específica para o cálculo da área para cada uma de nossas formas e podemos manter o contráto de cálculo de área em nossa classe FormaGeometrica.

[Barbara_Liskov]:http://en.wikipedia.org/wiki/Barbara_Liskov