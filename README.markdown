# The Official revendus.com.br C# Style Guide

Este style guide foca em leitura de código, simplicidade e consistência.

Ele deve ser usado **c#** mas também pode ser usado em **java**. 

## Inspiration

This style guide is based on C# and Unity conventions. 

## Table of Contents
- [Recomendação] (#Recomendacao)
- [Nomenclature](#nomenclature)
  + [Namespaces](#namespaces)
  + [Convenção C#] (convenção--c#)
  + [Nomeação](#Nomeação)
  + [Classes & Interfaces](#classes--interfaces)
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

Spacing is especially important in raywenderlich.com code, as code needs to be easily readable as part of the tutorial. 

### Indentation

Indentation should be done using **spaces** — never tabs.  

#### Blocks

Indentation for blocks uses **4 spaces** for optimal readability:

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

Indentation for line wraps should use **4 spaces** (not the default 8):

**AVOID:**

```csharp
CoolUiWidget widget =
        someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);
```

**PREFER:**

```csharp
CoolUiWidget widget =
    someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);
```

### Line Length

Lines should be no longer than **100** characters long.

### Vertical Spacing

There should be exactly one blank line between methods to aid in visual clarity 
and organization. Whitespace within methods should separate functionality, but 
having too many sections in a method often means you should refactor into
several methods.


## Brace Style

All braces get their own line as it is a C# convention:

**AVOID:**

```csharp
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

Conditional statements are always required to be enclosed with braces,
irrespective of the number of lines required.

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

Switch-statements come with `default` case by default (heh). If the `default` case is never reached, be sure to remove it.

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
    case 2:
        break;
}
```

## Language

Use US English spelling.

**AVOID:**

```csharp
string colour = "red";
```

**PREFER:**

```csharp
string color = "red";
```

The exception here is `MonoBehaviour` as that's what the class is actually called.

## Copyright Statement

The following copyright statement should be included at the top of every source file:

    /*
     * Copyright (c) 2020 Razeware LLC
     * 
     * Permission is hereby granted, free of charge, to any person obtaining a copy
     * of this software and associated documentation files (the "Software"), to deal
     * in the Software without restriction, including without limitation the rights
     * to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
     * copies of the Software, and to permit persons to whom the Software is
     * furnished to do so, subject to the following conditions:
     * 
     * The above copyright notice and this permission notice shall be included in
     * all copies or substantial portions of the Software.
     *
     * Notwithstanding the foregoing, you may not use, copy, modify, merge, publish, 
     * distribute, sublicense, create a derivative work, and/or sell copies of the 
     * Software in any work that is designed, intended, or marketed for pedagogical or 
     * instructional purposes related to programming, coding, application development, 
     * or information technology.  Permission for such use, copying, modification,
     * merger, publication, distribution, sublicensing, creation of derivative works, 
     * or sale is expressly withheld.
     *    
     * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
     * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
     * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
     * AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
     * LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
     * OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
     * THE SOFTWARE.
     */

## Smiley Face

Smiley faces are a very prominent style feature of the raywenderlich.com site!
It is very important to have the correct smile signifying the immense amount of happiness and excitement for the coding topic. The closing square bracket ] is used because it represents the largest smile able to be captured using ASCII art. A closing parenthesis ("**:)**") creates a half-hearted smile, and thus is not preferred.

**AVOID**:

:)

**PREFER**:

:]  
  
> **NOTE**: Do not use smileys in your scripts.

## Credits

This style guide is a collaborative effort from the most stylish
raywenderlich.com team members:

- [Darryl Bayliss](https://github.com/DarrylBayliss)
- [Sam Davies](https://github.com/sammyd)
- [Mic Pringle](https://github.com/micpringle)
- [Brian Moakley](https://github.com/VegetarianZombie)
- [Ray Wenderlich](https://github.com/rwenderlich)
- [Eric Van de Kerckhove](https://github.com/BlackDragonBE)

