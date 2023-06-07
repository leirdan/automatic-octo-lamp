# C SHARP
> Todos os códigos escritos aqui serão desenvolvidos apenas no Windows, sistema operacional proprietário da Microsoft. Por preferência, utilizarei a IDE (Integrated Development Environment) **Visual Studio** para os códigos, salvo quando indicado.

## 1. ECOSSISTEMA .NET
O **C#** (pronuncia-se *C Sharp*) e o **ambiente .NET** (pronuncia-se *dotnet*) surgiram para contornar certos problemas envolvendo os softwares da Microsoft: por exemplo, quando um programa escrito em C precisava ser escrito em Visual Basic, além do programador precisar aprender a nova linguagem e reescrever todo o código, ele ainda tinha que reescrever todas as bibliotecas que ele iria usar de C para Visual Basic quando estas ainda não tinham sido "traduzidas"; tal situação ocasiona uma drástica redução de produtividade e toma muito tempo além do necessário para desenvolver esses programas. Além disso, era uma complicação ainda maior quando o aplicativo era pensado para ser executado em outros sistemas operacionais fora o Windows (como Linux, Mac OS e FreeBSD), pois o código teria que ser adaptado diversas vezes para "encaixar" na arquitetura de cada sistema operacional.

Com tais problemas em vigor, Microsoft e Sun Microsystems - empresa responsável por desenvolver o Java e sua máquina virtual, a JVM - firmaram um acordo para adotar o Java no Windows; contudo, os desenvolvedores da Microsoft desenvolveram uma linguagem denominada *J++*, uma versão do Java exclusiva para Windows, o que não estava no contrato e resultou em um processo da Sun contra a Microsoft, que teve que desenvolver seu próprio ecossistema para o Windows.

Assim, surgiu o que denominamos de Ecossistema .NET, que vem como uma forma de uniformizar, simplificar e melhorar o desenvolvimento de softwares da Microsoft; ele utiliza um conceito similar ao Java com sua máquina virtual, onde os programas são compilados na linguagem intermediária **MSIL** (sigla para **M**icro**s**oft **I**ntermediate **L**anguage) e executados em uma máquina virtual, a qual será implementada em qualquer sistema operacional. Ele pode ser entendido em camadas, as quais são:
* **Linguagem**: a **1ª camada**, é nela onde o desenvolvedor de fato programará na linguagem que desejar: C#, F#, VB.NET ou Python.NET. De fato, a linguagem escolhida não importa, visto que todo o código será compilado na próxima camada. Denominamos as linguagens acima como **linguagens .NET**, pois serão compiladas em MSIL;
* **Aplicação .NET**: a **2ª camada**, onde a aplicação em MSIL é gerada após a compilação do código em C#, VB.NET, etc. Pelo fato dos códigos .NET serem compilados em MSIL, é possível ter mais de 1 linguagem .NET em um mesmo projeto sem problemas;
* **Biblioteca .NET Framework**: a **3ª camada**, complementar à aplicação .NET, é o código MSIL que contém ferramentas que permitem o desenvolvimento dos aplicativos em .NET;
* **CLR - Common Language Runtime**: a **última camada**, é a **máquina virtual** que executa o código MSIL gerado pelo .NET em forma de código de máquina (código dos processadores). Essa máquina virtual CLR é executada em cima de qualquer sistema operacional; desse modo, por não ser executada diretamente sobre o SO, não é necessário reescrever código em .NET para diferentes SO's.

## 2. PRIMEIRO PROGRAMA

Criemos, a princípio, um arquivo de texto vazio em qualquer editor de texto (utilizarei o **Notepad++**, mas o Bloco de Notas serve da mesma forma). Nele, insira o seguinte código:

```cs
using System;

class Program {
	public static void Main (string[] args) { 
		Console.WriteLine("Hello, world!");
	}
} 
```

> O código acima imprime no console/terminal a mensagem "Hello, world", isso é o que é necessário saber por agora.

Salve o arquivo com um nome qualquer. Após salvar, o que devo fazer para ver o código funcionando? Simples: o .NET já vem instalado nos sistemas operacionais Windows desde o Windows XP; logo, existe um diretório que guarda todos os programas e arquivos necessários para fazer funcionar o ambiente .NET em seu computador, incluindo o **compilador** para gerar o código MSIL.

Onde está este compilador? Na pasta `C:\Windows\Microsoft.NET\Framework\v4.0.30319` do seu computador. O compilador é o arquivo executável `csc.exe`. Mas como posso chamar o compilador para transformar meu código C# em algo executável?

Abra o seu terminal e execute o seguinte:
`c:\Windows\Microsoft.NET\Framework\v4.0.30319\csc.exe hello_world.txt`. Esse comando executará o compilador no arquivo "hello_world.txt", gerando um novo arquivo: `hello_world.exe`. Assim, dentro do diretório onde está esse novo arquivo, digite no seu terminal: `hello_world.exe`. Desse modo, será impresso no terminal a mensagem "Hello, world!". Que prático, não é?!

Nem sempre...

## 3. MIGRANDO PARA O VISUAL STUDIO
O Visual Studio é uma IDE desenvolvida e mantida pela Microsoft, utilizada especialmente para a construção de aplicações em .NET Framework graças à toda sua estrutura, mas que abriga uma diversidade de outras linguagens como C++. É uma IDE extremamente poderosa: apesar de pesada, contém tudo que é necessário para aumentar a produtividade do programador.

Dentro do Visual Studio 2022, em `Novo -> Projeto`, seleciono, dentro da seleção de modelos, `Aplicativo do Console (.NET Framework)`; depois, o local onde o projeto será criado, o nome da solução, do projeto, a versão `.NET Framework 4.7.2` e confirmo.

Após criado, é gerado o seguinte código base:
```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace FirstProject
{
    internal class Program
    {
        static void Main(string[] args)
        {
        }
    }
}
```

Vamos por partes:
* `using System`: informa que estou usando a biblioteca .NET `System`, que vem com classes e funções já definidos, como `Console` e seus métodos. 
* `namespace`: uma forma de organizar e definir de onde vem cada trecho importado do seu código. Por exemplo, posso criar classes dentro de namespaces diferentes e, por meio do `using`, importar cada um dos namespaces e acessar suas classes e métodos, evitando que, por exemplo, precisemos escrever `System.Console.WriteLine()` e `System.Console.ReadLine()` múltiplas vezes.
* `método Main`: o método de "start" de sua aplicação.

Ao acessar a pasta onde está o novo projeto criado, temos um arquivo de extensão `.sln` e uma pasta com o nome do projeto (FirstProject). Este arquivo de extensão .sln refere-se à solução como um todo, ou seja, em um aplicativo .NET podem existir diversos projetos (FirstProject, SecondProject, ...) que pertencem à mesma solução (no meu caso, *AppConsole*).

Com algumas adições, produzo o seguinte código:
```cs
using System;

namespace FirstProject
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("hey, who are you?");
            var name = Console.ReadLine();
            Console.WriteLine("hello, " + name + "!");
        }
    }
}
```
> Obs.: `var` é uma keyword que diz que a variável deve ser do mesmo tipo que o valor que recebe, ou seja, é um tipo implícito; contudo, neste caso, poderia ser perfeitamente substuída por um tipo `string`.

## 4. VARIÁVEIS
Variáveis no C# devem ter um tipo declarado: nada de apenas `numero = 5` do Python; aqui, devemos utilizar `int idade = 5`. Essa declaração mais rígida nos permite evitar ambiguidade de código e tornar o código mais legível; particularmente, é preferível isso do que não saber rapidamente de que tipo/classe aquela variável deriva.  

Existem tipos de variáveis como as numéricas (`int, short, long, double, float`) e as textuais (`char, string`).

### 4.1 CONVERSÃO
Caso se depare com uma variável de um tipo diferente do que deseja trabalhar, é possível converter (à força) o valor da variável para um tipo diferente, como:
```cs
Console.WriteLine("Insira seu salário: ");
double salario = Console.Read();
Console.WriteLine("Seu salário é " + (int) salario);
```

O tipo entre parênteses sinaliza que a variável `salario` será convertida do tipo *double* para o tipo inteiro.

Contudo, não é necessário fazer conversões explícitas sempre. O C# trabalha com um sistema de conversão de tipos "menores" em "maiores". Tome a tabela abaixo como referência:

TIPO | TAMANHO
----- | -----
boolean | 1 byte
byte | 1 byte
short | 2 bytes
char | 2 bytes
int | 4 bytes
float | 4 bytes
long | 8 bytes
double | 8 bytes

Assim, temos que um variável do tipo *float* pode receber valores *inteiros* (pois tem "mais bytes"), enquanto o contrário não ocorre.

### 4.2 TEXTOS

Para representar textos, temos dois tipos principais:
* `char`: representa 1 único caractere de acordo com a tabela ASCII, e seus valores devem ser escritos entre aspas simples; internamente, o tipo *char* representa um número na memória de acordo com a tabela mencionada acima. Podemos declarar valores de duas formas: utilizando diretamente o caractere - `char value = '=';` ou atribuindo o número do caractere na tabela ASCII - `char value = (char)61;`;
* `string`: representa uma cadeia de caracteres, e seus valores são escritos entre aspas duplas. Uma string pode ser vazia ou não e ter múltiplas linhas ou não; para quebrar linhas de uma string, podemos usar a expressão `\n`. Exemplos: `string hello = "hello, \n kingslayer.";`, `string alert = "be careful, dragons may lay ahead";`

## 5. CONTROLE DE FLUXO COM IF-ELSE

O uso dos comandos `if` e `else` permite que o programa realize diferentes procedimentos de acordo com certas condições, como liberar o acesso de certos usuários a áreas administrativas de um site, por exemplo. Para criar as condições, são usados operadores lógicos (`||`, `!` ou `&&`), e cada condição pode assumir um valor **booleano**, ou seja, `true` ou `false`.
Sua sintaxe é:
```cs
if (<condição> == true ou false) 
{
    <código>
}
else if (<condição> == true ou false) // Opcional 
{
    <código>
}
else 
{
    <código>
}
```
Podemos, além disso, colocar instruções *if* dentro de outros *if*, realizando uma verificação ainda mais complexa.


> Para exemplificar tudo isso, aqui está um código que, com base na idade inserida pelo usuário, informa se ele pode votar, e se é de obrigatório ou não:
```cs
using System;

namespace FirstProject
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Caro usuário, digite a sua idade: ");
            int age = Console.Read();
            // Se idade for maior ou igual a 16:
            if (age >= 16)
            {
                // Se idade for menor que 18 ou maior ou igual a 70:
                if (age < 18 || age >= 70)
                {
                    Console.WriteLine("Seu voto é facultativo!");
                }
                // Se a idade estiver entre 18 e 69:
                else
                {
                    Console.WriteLine("Seu voto é obrigatório.");
                }
            }   
            // Se idade for menor que 16:
            else
            {
                Console.WriteLine("Você não pode votar.");
            }
        }
    }
}
```

### 5.1 SWITCH CASE
Uma maneira alternativa de lidar com controle de fluxo e reduzir a quantidade de instruções *if*. Não é aplicável em todos os casos, mas ainda é muito útil. Sua sintaxe é:
```cs
switch (<variável>) 
{
    case <opção1>:
        <código a ser executado quando a opção 1 for escolhida>
        break;
    case <opção2>:
        <código a ser executado quando a opção 2 for escolhida>
        break;
    case <opção3>:
        <código a ser executado quando a opção 3 for escolhida>
        break;
    default:
        <código a ser executado quando nenhum dos outros casos for escolhido>
        break;
}
```

> Para exemplificar, será elaborado um algoritmo para imprimir as fórmulas do cálculo da área de certas figuras geométricas.
```cs
using System;

namespace FirstProject
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Caro usuário, informe a forma geométrica que deseja conhecer a fórmula da área: ");
            string age = Console.ReadLine();
            switch (age) {
                case "Triângulo":
                    Console.WriteLine("(base x altura) / 2");
                    break;
                case "Retângulo":
                    Console.WriteLine("base x altura");
                    break;
                case "Quadrado":
                    Console.WriteLine("lado elevado a 2");
                    break;
                case "Losângo":
                    Console.WriteLine("(diagonal Maior x diagonal menor) / 2");
                    break;
                case "Trapézio":
                    Console.WriteLine("(base Maior + base Menor) x altura / 2");
                    break;
                default:
                    Console.Write("Insira uma definida aqui.");
                    break;
            }
        }
    }
}
```

## 6. LAÇOS DE REPETIÇÃO
Serão analisados dois dos laços disponíveis na linguagem C#: o **for** e o **while**. Geralmente, eles são laços que podem ser convertidos um no outro e servem para executar diversas vezes um mesmo trecho de código de forma dinâmica. A seguir, estão mostrados dois exemplos de uso com cada um dos laços:
> Imprimir todos os múltiplos de 3:
```cs
/* WHILE */
static void Main(string[] args)
{
    Console.WriteLine("Os números múltiplos de 3 que estão no intervalo de 1 a 100 são:");
    int numero = 1;
    while (numero < 100)
    {
        if (numero % 3 == 0)
        {
            Console.WriteLine(numero);
        }
        numero++;
    }
}
```
```cs
/* FOR */
static void Main(string[] args)
{
    Console.WriteLine("Os números múltiplos de 3 que estão no intervalo de 1 a 100 são:");
    for (int num = 1; num <= 100; num++)
    {
        if (num % 3 == 0)
        {
            Console.WriteLine(num);
        }
    }
}
```

> Calcular e imprimir os fatoriais de 1 a 10:
```cs
/*  WHILE */
static void Main(string[] args)
{
    Console.WriteLine("Os fatoriais de cada número de 1 a 10 são: ");
    int numero = 1;
    int result = 1;
    while (numero <= 10)
    {
        while (numero <= 10)
            {
                result *= numero;
                Console.WriteLine($"Fatorial de {numero}: {result}");
                numero++;
            }
    }
}
```

```cs
/*  FOR */
static void Main(string[] args)
{
    Console.WriteLine("Os fatoriais de cada número de 1 a 10 são: ");
    int result = 1;
    for (int num = 1; num <= 10; num++)
    {
        result *= num;
        Console.WriteLine($"Fatorial de {num}: {result}")
    }
}
```
##
# PROGRAMAÇÃO ORIENTADA A OBJETOS COM C SHARP

Nesta seção, serão explicados fundamentos, conceitos e práticas da *Programação Orientada a Objetos* (**POO**), intrínseco ao C# e essencial para a boa utilização da linguagem. Algumas de suas vantagens incluem a *reutilização de código*, *organização* e *melhor manutenção* - tendo em vista que, pela concentração do código em trechos específicos, torna-se mais fácil procurar e encontrar erros.

> Para aplicação prática, foi idealizada uma situação de uma loja de discos de rock e heavy metal, mas que também aluga guitarras elétricas para músicos, chamada *Hellfire Store*.
## 1. FUNDAMENTOS
### 1.1 CLASSES
Classes nada mais são que uma forma eficaz de organizar e concentrar o seu código, sendo um "modelo" que define a estrutura de certos objetos que serão usados no algoritmo. Cada classe tem *atributos* e *métodos*; abaixo, um exemplo da estrutura da classe Album da loja Hellfire no arquivo `Album.cs`:
```cs
public class Album
{
    public string Title;
    public string Description;
    public string Country;
    public double Weight;
    public int Quantity;
    public double Price;
    public int? DaysOfLastPurchase; // atributo opcional
    public double? Discount = 0.0; // atributo opcional e com valor padrão
}
```
### 1.2 OBJETOS
Objetos são criados a partir de uma classe previamente definida e usados para representar entidades do mundo real. São declarados da mesma forma que uma variável, mas contém chaves e valores. Exemplo de declaração de um objeto (álbum) no arquivo `Program.cs` (no mesmo projeto que Album.cs):
```cs
Album album01 = new Album();
// Declarando valores para cada uma das propriedades obrigatórias.
album01.Title = "Rising";
album01.Description = "A phenomenal album!";
album01.Country = "UK";
album01.Weight = 0.256;            
album01.Price = 60;
album01.Quantity = 4;
album01.DaysOfLastPurchase = 120;
// Acessando tais valores com um "."
Console.WriteLine(album01.Title); // Rising
Console.WriteLine(album01.Weight); // 0,256
Console.WriteLine(album01.Description); // A phenomenal album!
Console.WriteLine(album01.Country); // UK
```

### 1.3 MÉTODOS
Funções dentro de classes são denominadas métodos, e são o que garantem que a classe tenha comportamentos próprios. Os métodos são importantes para que concentremos algoritmos e procedimentos importantes em um só local, chamando-os posteriormente e tornando a manutenção mais fácil. Exemplo de método que realiza a venda de um disco, implementado na classe `Album.cs`:
```cs
public void SellRecord()
{
    if (this.Quantity > 0)
    {
        Console.Write($"the album's price is US${this.Price}. will you buy it? ");
        var option = Console.ReadLine();
        if (option == "yes")
        {
            this.Quantity--;
            Console.Write($"there are left {this.Quantity} units of this disc. ");
            Console.WriteLine("thanks, bye!");
        } else if (option == "no")
        {
            Console.WriteLine("okay.");
        }
        else
        {
            Console.WriteLine("you didn't answer my question..");
            SellRecord(); // executa a função novamente para o usuário decidir.
        }
    }
}
```
> Obs.: a keyword `this` é uma palavra genérica utilizada em classes para tornar o comportamento da classe genérico. Assim, ela se refere sempre ao objeto que foi criado utilizando a classe e que está acessando o método no momento. Por exemplo, perceba que, na linha:
> ```cs
>album01.SellRecord();
>```
> o valor de *Quantity* no método será substituido de *this.Quantity* por 4 (quantidade de album01).

Exemplo de outro método que foi implementado para garantir descontos em discos que não vendem há um tempo e são mais caros:
```cs
public void AssignDiscount(double price, int? days)
    {
        if (price > 100 && days >= 120)
        {
            this.Discount = price * 0.10;
        }
    }
```

## 2. NAMESPACES
*Namespaces* são uma ferramenta nas linguagens *C* que possibilita ao programador determinar de onde um código/classe/qualquer coisa vem no seu programa. Suponha que, em uma solução, hajam duas ou mais classes com o mesmo nome mas que referem-se a coisas distintas; como saber qual devo utilizar e como faço para selecionar apenas ela? Através da instrução namespace e sua complementar, *using*. Sua sintaxe é:
```cs
using <namespace>;

namespace <nome> {
    // restante do código
}

```
Um exemplo de namespace que é usado recorrentemente é o `System`, o qual contém uma infinidade de métodos e a classe `Console`, por exemplo.

Na situação da *Hellfire Store*, foi criada uma classe adicional de clientes, agrupada em um namespace, tal que temos o seguinte código:
```cs
namespace HellfireStore
{
    public class Client
    {
        public string Name;
        protected string Address;
        public int BoughtHowManyAlbums;
    }
}
```
Agora, foi criada uma nova classe para criar contas para os músicos que fazem o aluguel das guitarras, chamada `Account.cs`:

```cs
using HellfireStore;
using System;

class Account
{
    public Client Client;
    public int Rents;
    public DateTime Created_At;
    public double? Discount;

    public bool GetDiscount()
    {
        if (this.Rents < 6 || (this.Created_At.Month - DateTime.Now.Month) < 6)
        {
            return false;
        }
        else
        {
            this.Discount = 0.10;
            return true;
        }
    }
}
```
> Perceba o uso do `using HellfireStore`. Tal instrução informa ao compilador que o programa fará uso dos códigos presentes neste namespace (ou seja, a classe *Client*); sem isso, teríamos que escrever, sempre, `public HellfireStore.Client client;`

Por fim, falta apenas a classe que representa as guitarras. Assim, temos:
```cs
namespace HellfireStore
{
    enum HandOrientation
    {
        LEFT = 0,
        RIGHT = 1,
        BOTH = 2
    }

    class Guitars
    {
        private readonly int id;
        public string Model;
        public long ItemNumber;
        public string Brand;
        public string Color;
        public string PredominantMaterial;
        public HandOrientation HandOrientation;
        public double Price;
    }
}
```
> A estrutura *Enum* não é de tamanha importância agora. Neste caso, ela só guarda alguns valores específicos e imutáveis.

Agora, de volta ao arquivo `Program.cs`, será deletado todo o conteúdo anterior e criado um novo para testes.

Program.cs:
```cs
using HellfireStore;

internal class Program
{
    static void Main(string[] args)
    {
        Account nergal = new Account();
        nergal.Client = new Client
        {
            Name = "Adam 'Nergal' Michal Darski",
            BoughtHowManyAlbums = 14 // 14 vezes que comprou discos
        };
        nergal.Rents = 8; // 8 vezes que alugou uma guitarra
        nergal.Created_At = DateTime.Now;
        if (nergal.GetDiscount())
        {
            Console.WriteLine($"{nergal.Client.Name} have some discount!");
        }
        // Executa este.
        else
        {
            Console.WriteLine($"{nergal.Client.Name} doesn't have discount.");
        }
    }
}
```

Perceba que, caso o `using HellfireStore` seja excluído, não haverá problemas para a classe *Account*, somente para a *Client*, visto que *Account* não pertence a nenhum namespace. Contudo, é uma boa prática não deixar pedaços de códigos jogados e "sem origem"; portanto, haverá a seguinte adição no código de `Account.cs`:
```cs
using System;
// Remoção de using HellfireStore;

namespace HellfireStore // Adição
{
    class Account
    {
        public Client Client; // Por estarem dentro do mesmo namespace, uma classe pode acessar a outra sem problemas.
        public int Rents;
        public DateTime Created_At;
        public double? Discount;

        public bool GetDiscount()
        {
            if (this.Rents < 6 || (this.Created_At.Month - DateTime.Now.Month) < 6)
            {
                return false;
            }
            else
            {
                this.Discount = 0.10;
                return true;
            }
        }
    }
}
```

Entretanto, perceba, não há utilização em nenhum momento da classe `Guitars.cs`. Assim, como é possível criar os objetos "guitarra" dentro da conta ao invés de só informar quantas vezes o cliente alugou uma guitarra?