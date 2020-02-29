# The Official revendus.com.br C# Style Guide

Este style guide foca em leitura de código, simplicidade e consistência.

Ele deve ser usado **c#** mas também pode ser usado em **java**. 

## Inspiration

This style guide is based on C# and Unity conventions. 

## Table of Contents
- [Recomendação](#Recomendacao)
- [Nomenclature](#nomenclature)
  + [Namespaces](#namespaces)
  + [Convenção C#](convenção--c#)
  + [Nomeação](#Nomeação)
  + [Classes](#classes)
  + [Interfaces](#interfaces)
  + [Methods](#methods)
  + [Fields](#fields)
  + [Parameters](#parameters--parameters)
  + [Delegates](#delegates--delegates)
  + [Events](#events--events)
  + [Misc](#misc)
- [Declarations](#declarations)
  + [Access Level Modifiers](#access-level-modifiers)
  + [Fields & Variables](#fields--variables)
  + [Classes](#classes)
  + [Interfaces](#interfaces)
- [Spacing](#spacing)
  + [Indentation](#indentation)
  + [Line Length](#line-length)
  + [Vertical Spacing](#vertical-spacing)
- [Brace Style](#brace-style)
- [Switch Statements](#switch-statements)
- [Language](#language)
- [Copyright Statement](#copyright-statement)
- [Smiley Face](#smiley-face)
- [Credit](#credits)

## Recomendação
Toda vez que terminar um código, deve-se fazer a revisão deste guia.

## Nomenclature
No geração, a nomeação deve seguir os padrões do C#.

### Convenção C#
- [C# Coding Conventions](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)
- [C# Style Guide](https://github.com/raywenderlich/c-sharp-style-guide)
- [C# Coding Standards and Naming Conventions](http://www.dofactory.com/reference/csharp-coding-standards)


### Nomeação

Evitar ao máximo nome composto.

**AVOID**:

```csharp
RemetentesIds
```

**PREFER**:

```csharp
Ids
```
ou
```csharp
RemetentesId
```
### Namespaces

Todos os Namespaces devem estar em **PascalCase**. Não usar hífens ( - ) ou underscores ( \_ ). The exception to this rule are acronyms like GUI or HUD, which can be uppercase:

**AVOID**:

```csharp
com.revendus.comunicacao.envio
```

**PREFER**:

```csharp
Revemdis.Comunicacao.Envio
```

### Classes

Classes devem ser escritas em **PascalCase**. Por exemplo `Comunicacao`. 

### Interfaces

Interfaces devem ser escritas em **PascalCase** precedidas da letra **I**. Por exemplo `IComunicacao`. 

### Methods

Métodos devem ser escritos em **PascalCase**. Por Exemplo `FazerAlgumaCoisa()`. 

### Fields

Exemplo:

```csharp
public class MyClass 
{
    public int PublicField {get; set;};
    private int _myPrivate;
    protected int _myProtected;
}
```

**AVOID:**

```csharp
int myPrivateVariable
```

**PREFER:**

```csharp
private int _myPrivateVariable
```

Static fields são exceção é devem ser escritos em **_UPPERCASE**:

```csharp
public static int _VALOR_PROMOCIONAL_BASE = 42;
```
### Properties

Todas as propriedades devem ser escritas em **PascalCase**. Por exemplo:

```csharp
private int _numeroDaPagina;
public int NumeroDaPagina 
{
    get { return _numeroDaPagina; }
    set { _numeroDaPagina = value; }
}
```

**AVOID:**

```csharp
private int _numeroDaPagina;
public int NumeroDaPagina 
{
    get { return _numeroDaPagina; }
    set { _numeroDaPagina = value; }
}
```

**PREFER 1:**

```csharp
public int NumeroDaPagina {get; set;}
```

**PREFER 2:**

```csharp
private int _numeroDaPagina;
public int NumeroDaPagina 
{
    get { return _numeroDaPagina; } 
}
```

**PREFER 3:**

```csharp
  public int NumeroDaPagina
  {
      get;
      private set;
  }
```

### Parameters

Prametros devem ser escritos em **camelCase**.

**AVOID:**

```csharp
void FazerAlgumaCoisa(Mensagem Mensagem)
```

**PREFER 1:**

```csharp
private void FazerAlgumaCoisa(Mensagem mensagem)
```

**PREFER 2:**

```csharp
public static string DefinirId(this List<ItemRecebido> itens,
                               Action<StringBuilder, ItemRecebido> acaoItem)
{
        
}
```

Uso de apenas um caracter, singuarlmente, devem ser evitados a menos que estejam numa variável de loop temporário.

### Actions

Actions devem ser escritos em **PascalCase**. Por exemplo:

```csharp
public event Action<int> ValueChanged;
```

### Misc

No código, siglas devem ser tratadas como palavras. Por exemplo:

**AVOID:**

```csharp
XMLHTTPRequest
String URL
EncontrarMensagemPorID
```  

**PREFER:**

```csharp
XmlHttpRequest
String url
EncontrarMensagemPorId
```

## Declarations

### Access Level Modifiers

Todos os modificadores de nível de acesso devem ser definios de forma explícida para classes, métodos, propriedades e variáveis.

Exemplo:

```csharp
namespace Revendus.Erp.PageController
{
  internal class MyClass 
  {
      public int PublicField {get; set;};
      private int _myPrivate;
      protected int _myProtected;
  }
}

```

### Fields & Variables

Prefira declarações em múltiplas linhas, com base em comentário.

**AVOID:**

```csharp
private string username, twitterHandle;
```

**PREFER 1:**

```csharp
        /// <summary>
        /// Contém informações do usuário
        /// </summary>
        /// <remarks>
        /// Nível de classe porque preciso usar multiplas vezes
        /// </remarks>
        private string _username;
        /// <summary>
        /// Contém informaçõe do twitter
        /// </summary>
        /// <remarks>
        /// Definida pelo construtor, não muda, é usada em para referenciar
        /// informações do twitter para salvar no banco, validar, etc.
        /// </remarks>
        private string _twitterHandle;
```

**PREFER 2:**

```csharp
         #region variáveis para lidar com o twitter
        /// <summary>
        /// Contém informações do usuário
        /// </summary>
        /// <remarks>
        /// Nível de classe porque preciso usar multiplas vezes
        /// </remarks>
        private string _username;
        /// <summary>
        /// Contém informaçõe do twitter
        /// </summary>
        /// <remarks>
        /// Definida pelo construtor, não muda, é usada em para referenciar
        /// informações do twitter para salvar no banco, validar, etc.
        /// </remarks>
        private string _twitterHandle;
        #endregion
```

### Classes

1. Uma classe por arquivo.
2. Classe não deve ter mais de 50 linhas.
3. Usar inner classes somente quando o escopo for aprorieado.
4. No caso da classe precisar ter mais de 50 linhas, utilizar **design pattern** ou **partial classes**
5. [Usar os padrões de classes](padroes-de-classes.markdown)

### Interfaces

Todas as interfaces devem ter o prefixo com a letra **I**. 

**AVOID:**

```csharp
Comunicacao
```

**PREFER:**

```csharp
IComunicacao
```

## Spacing

Espaço é muito importante no código, pois seu código precisa ser legível. 

### Indentation

Seu código precisa ser identado com **espaços** — nunca tabs.  

#### Blocks

A Indentação deve considerar  **4 espaços** para uma leitura ótima:

**AVOID:**

```csharp
for (int i = 0; i < 10; i++) 
{
  Debug.Log("index=" + i);
}
```

**PREFER:**

```csharp
for (int i = 0; i < 10; i++) 
{
    Debug.Log("index=" + i);
}
```

#### Line Wraps

A quebra de linhas deve contém múltiplos **4 espaços** ou acompanhar o texto superior:

**AVOID:**

```csharp
CoolUiWidget widget =
        someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);
```

**PREFER:**

```csharp
var widget = someIncrediblyLongExpression(that, 
										  reallyWouldNotFit, 
										  on, 
										  aSingle, 
										  line);
```

### Line Length

As linhas não devem ter mais que **80** caracteres.

### Vertical Spacing

1. Deve haver exatamente uma linha vazia entre os métodos para ajudar na clareza visual
e organização. 

2. Ter um espaço em branco nos métodos para separar a funcionalidades.
Mas cuidado em fazer muitas seções de funcionalidade num mesmo método. 
Geralmente significa que você deve refatorar vários métodos.

## Brace Style

As chaves devem seguir a padrão de convensão do C#:

**AVOID:**

```csharp
-- código normalmente visto em JAVA (péssimo)
class MyClass {
    void DoSomething() {
        if (someTest) {
          // ...
        } else {
          // ...
        }
    }
}
```

**PREFER:**

```csharp
class MyClass
{
    void DoSomething()
    {
        if (someTest)
        {
          // ...
        }
        else
        {
          // ...
        }
    }
}
```

É necessário que declarações condicionais tenham chaves também,
independentemente do número de linhas.

**AVOID:**

```csharp
if (someTest)
    doSomething();  

if (someTest) doSomethingElse();
```

**PREFER:**

```csharp
if (someTest) 
{
    DoSomething();
}  

if (someTest)
{
    DoSomethingElse();
}
```
## Switch Statements

As instruções do switch vêm com o CASE `default` por padrão. Para evitar situações de erros, é necessário aplicar o padrão.

**AVOID:**  
  
```csharp
switch (variable) 
{
    case 1:
        break;
    case 2:
        break;
    default:
        break;
}
```

**PREFER:**  
  
```csharp
switch (variable) 
{
    case 1:
        break;	
    default:
        break;
}
```

## Language

Use o português brasileiro.

**AVOID:**

```csharp
string color = "red";
```

**PREFER:**

```csharp
string cor = "red";
```

A exceção acontece para classes do framework padrão.

## Credits

This style guide is a collaborative effort from the most stylish
raywenderlich.com team members:

- [Darryl Bayliss](https://github.com/DarrylBayliss)
- [Sam Davies](https://github.com/sammyd)
- [Mic Pringle](https://github.com/micpringle)
- [Brian Moakley](https://github.com/VegetarianZombie)
- [Ray Wenderlich](https://github.com/rwenderlich)
- [Eric Van de Kerckhove](https://github.com/BlackDragonBE)
- [Eduardo Xavier](https://github.com/eduxavier)

