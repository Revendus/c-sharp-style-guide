# Guia oficial do C# / Java Style Guide do revendus.com.br

Este style guide foca em leitura de código, simplicidade e consistência.

Ele deve ser usado **c#** mas também pode ser usado em **java**. 


## Table of Contents
- [Recomendação](#recomenda%C3%A7%C3%A3o)
- [Nomeação](#Nomeação)
- [Nomenclature](#nomenclature)
  + [Namespaces](#namespaces)
  + [Convenção C#](convenção--c#)
  + [Classes](#classes)
  + [Exception](#exception)
  + [Interfaces](#interfaces)
  + [Methods](#methods)
  + [Fields](#fields)
  + [Parameters](#parameters--parameters)
  + [Delegates](#delegates--delegates)
  + [Events](#events--events)
  + [Enums](#enums)
  + [Misc](#misc)
- [Declarations](#declarations)
  + [Access Level Modifiers](#access-level-modifiers)
  + [Fields & Variables](#fields--variables)
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

## Nomenclature
No geração, a nomeação deve seguir os padrões do C#.

### Convenção C#
- [C# Coding Conventions](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)
- [C# Style Guide](https://github.com/raywenderlich/c-sharp-style-guide)
- [C# Coding Standards and Naming Conventions](http://www.dofactory.com/reference/csharp-coding-standards)



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

Organize os namespaces numa estrutura clara e definida, que represente o módulo.
```csharp 
// Examples
namespace Revendus.Erp.Processo.Area.MeuProcessoEspecifico
{
}
namespace Revendus.Erp.Processo.Area.MeuProcessoEspecifico.Extensoes
{
}
```



### Exception

Use o sufixo Exception na criação de novas classes que são exceptions.

Exemplo:
```csharp 
public class BarcodeReadException : System.Exception
{
}
```

### Interfaces

Interfaces devem ser escritas em **PascalCase** precedidas da letra **I**. 


**AVOID:**

```csharp
public interface Corpo
{
}
public interface MensagemCollection
{
}
public interface Agrupavel
{
}
```

**PREFER:**

```csharp
public interface ICorpo
{
}
public interface IMensagemCollection
{
}
public interface IAgrupavel
{
}
```

### Methods

Métodos devem ser escritos em **PascalCase**. Por Exemplo `FazerAlgumaCoisa()`. 

Exemplo:

```csharp
public class ClientActivity
{
  public void ClearStatistics()
  {
    //...
  }
  public void CalculateStatistics()
  {
    //...
  }
}
```

Use dois parametros com nome **sender** e **letra e** no event handler. O sender é o parametro que representa o objeto que disparou o evento.

```csharp
public void ReadBarcodeEventHandler(object sender, ReadBarcodeEventArgs e)
{
  //...
}
```
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
private void CasarNaIgreja(string name, string Name)

```

**PREFER 1:**

```csharp
private void FazerAlgumaCoisa(Mensagem mensagem)
private void CasarNaIgreja(string noivo, string noiva)
```

**PREFER 2:**

```csharp
public static string DefinirId(this List<ItemRecebido> itens,
                               Action<StringBuilder, ItemRecebido> acaoItem)
{
        
}
```

### Delegates

### Events

### Enums

Defina a numeração. Não herde tipos, não faça use prefixo ou sufixo para enums.

**AVOID:**

```csharp
public enum Color
{
  Red,
  Green,
  Blue,
  Yellow,
  Magenta,
  Cyan
} 
public enum Direction : long
{
  North = 1,
  East = 2,
  South = 3,
  West = 4
} 
public enum CoinEnum
{
  Penny,
  Nickel,
  Dime,
  Quarter,
  Dollar
} 
[Flags]
public enum DockingsFlags
{
  None = 0,
  Top = 1,
  Right = 2, 
  Bottom = 4,
  Left = 8
}
```

**PREFER 1:**

```csharp
public enum Dockings
{
  None = 0,
  Top = 1,
  Right = 2, 
  Bottom = 4,
  Left = 8
}
public enum Direction 
{
  North = 1,
  East = 2,
  South = 3,
  West = 4
} 
public enum Coin
{
  Penny,
  Nickel,
  Dime,
  Quarter,
  Dollar
}
[Flags]
public enum Dockings
{
  None = 0,
  Top = 1,
  Right = 2, 
  Bottom = 4,
  Left = 8
}
```


Uso de apenas um caracter, singuarlmente, devem ser evitados a menos que estejam numa variável de loop temporário.

### Actions

Actions devem ser escritos em **PascalCase**. Por exemplo:

```csharp
public event Action<int> ValueChanged;
```

### Delegates

```csharp 
public delegate void ReadBarcodeDelegate(object sender, ReadBarcodeEventArgs e);
```

### EventArgs

Use sufixo EventArgs na criação de novas casses:

```csharp 
// Correct
public class BarcodeReadEventArgs : System.EventArgs
{
}
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

#### USe nomes tipos primitivos (C# aliases) como `int`, `float`, `string` para declaração de variáveis. Use tipos do .NET Framework como `Int32`, `Single`, `String` para acessar memebros estáticos como `Int32.TryParse` ou `String.Join`.

```csharp
// Correct
string firstName;
int lastIndex;
bool isSaved;
string commaSeparatedNames = String.Join(", ", names);
int index = Int32.Parse(input);
// Avoid
String firstName;
Int32 lastIndex;
Boolean isSaved;
string commaSeparatedNames = string.Join(", ", names);
int index = int.Parse(input);
```



## Declarations

### Regras para nomes
#### 1. Use nome significados. O exemplo a seguir usa clientesDoRio para clientes localizados no Rio:

```csharp
var clientesDoRio = from customer in customers
  where customer.City == "Rio" 
  select customer.Name;
```

#### 2. Nunca use abreviações Exceto para nomes comuns como Id, Xml, Ftp, Uri.

```csharp    
// Correct
UserGroup userGroup;
Assignment employeeAssignment;
     
// Avoid
UserGroup usrGrp;
Assignment empAssignment; 

// Exceptions
CustomerId customerId;
XmlDocument xmlDocument;
FtpHelper ftpHelper;
UriPart uriPart;
```

#### 3. Use tipo implícito var para declaração local de variáveis. Exception: tipos primitivos (int, string, double, etc). 

```csharp 
var stream = File.Create(path);
var customers = new Dictionary();
// Exceptions
int index = 100;
string timeSheet;
bool isCompleted;
```


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

#### Não use tipos de identificação em nomes de variáveis

```csharp
// correto
int counter;
string name;
    
// Incorreto
int iCounter;
string strName;


```

#### Usar camelCasing para argumentos e variáveis locais

```csharp
public class UserLog
{
  public void Add(LogEvent logEvent)
  {
    int itemCount = logEvent.Items.Count;
    // ...
  }
}
```

#### Não usar CAPS para constantes e variáveis readonly:

```csharp
// Correct
public const string ShippingType = "DropShip";
// Avoid
public const string SHIPPINGTYPE = "DropShip";
```
Exceção para variáveis estáticas.



### Classes

Classes devem ser escritas em **PascalCase**. Por exemplo `Comunicacao`. 

Exemplo:

```csharp
public class ClientActivity
{
  public void ClearStatistics()
  {
    //...
  }
  public void CalculateStatistics()
  {
    //...
  }
}
```

**Regras**
1. Uma classe por arquivo.
2. Classe não deve ter mais de 50 linhas.
3. Usar inner classes somente quando o escopo for aprorieado.
4. No caso da classe precisar ter mais de 50 linhas, utilizar **design pattern** ou **partial classes**
5. [Usar os padrões de classes](padroes-de-classes.markdown)

#### Nome da classe tem que acompanhar o nome do arquivo. Exceção: arquivos com classes partial que refletem o propósito do arquivo fonte. Exemplo: designer, generated, extensão, etc. 

```csharp 
// Located in Task.cs
public partial class Task
{
}
// Located in Task.generated.cs
public partial class Task
{
}
```

#### Declare todos os membros no tipo da classe. Variáveis estáticas no topo de tudo:

```csharp 
// Correct
public class Contabilidade
{
  public static string _OBJECT_NAME;
  public static decimal _SQL_CONSULTA_ESPECIFICA;
  private int _quantidade;
  
  public string Numero { get; set; }
  public DateTime Abertura { get; set; }
  public DateTime Fechamento { get; set; }
  public decimal Balanco { get; set; }
  
  // Constructor
  public Contabilidade()
  {
    // ...
  }
}
```

#### Use substantivos e adjetivos para nomear uma classe.

1. Sempre tem que ter um substantivo
2. Use o ajetivo conforme variação do nome

(Referência de Substantivo)[https://www.todamateria.com.br/substantivos/]

```csharp 
public class Empregado
{
}
public class EmpregadoClt
{
}
public class EmpregadoCollection
{
}
```

#### Use terminações para DTOs (Data Transfer Objects)


```csharp 
public class EmpregadoDto
{
 //para Data Transfer Objects, representando uma consulta SQL ou LINQ TO SQL
}
public class EmpregadoView
{
//para Data Transfer Objects com função de visualização na UI
}
public class EmpregadoRequest
{
//para Data Transfer Objects de requisção entre endpoints diferentes
//UI chamando um service (web, Rest, componente)
}
public class EmpregadoResponse
{
//para Data Transfer Objects de requisção entre endpoints diferentes
//Um service (web, Rest, componente) retornando uma mensagem ao consumidor
}
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

