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

```c#
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

