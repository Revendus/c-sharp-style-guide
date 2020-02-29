# Padrões de codificação do C# e Convenções de nomeação


| Object Name               | Notation   | Length | Plural | Prefix | Suffix | Abbreviation | Char Mask          | Underscores |
|:--------------------------|:-----------|-------:|:-------|:-------|:-------|:-------------|:-------------------|:------------|
| Classe                    | PascalCase |    128 | No     | No     | Yes    | No           | [A-z][0-9]         | No          |
| Construtor                | PascalCase |    128 | No     | No     | Yes    | No           | [A-z][0-9]         | No          |
| Método                    | PascalCase |    128 | Yes    | No     | No     | No           | [A-z][0-9]         | No          |
| Método (argumentos)       | camelCase  |    128 | Yes    | No     | No     | Yes          | [A-z][0-9]         | No          |
| Variáveis locais          | camelCase  |     50 | Yes    | No     | No     | Yes          | [A-z][0-9]         | No          |
| Constants name            | PascalCase |     50 | No     | No     | No     | No           | [A-z][0-9]         | No          |
| Field name                | camelCase  |     50 | Yes    | No     | No     | Yes          | [A-z][0-9]         | Yes         |
| Properties name           | PascalCase |     50 | Yes    | No     | No     | Yes          | [A-z][0-9]         | No          |
| Delegate name             | PascalCase |    128 | No     | No     | Yes    | Yes          | [A-z]              | No          |
| Enum type name            | PascalCase |    128 | Yes    | No     | No     | No           | [A-z]              | No          |





#### 5. Use nome significados. O exemplo a seguir usa clientesDoRio para clientes localizados no Rio:

```csharp
var clientesDoRio = from customer in customers
  where customer.City == "Rio" 
  select customer.Name;
```

#### 6. Nunca use abreviações Exceto para nomes comuns como Id, Xml, Ftp, Uri.

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

#### 7. Use PascalCasing para abreviações de 3 caracteres ou mais. Para 2 caracteres use uppercase:

```csharp  
HtmlHelper htmlHelper;
FtpTransfer ftpTransfer;
UIControl uiControl;
```

#### 8. Não use sobrelinha em identificadores. Exceção: você pode usar como prefixo em variáveis privadas

```csharp 
// Correct
public DateTime clientAppointment;
public TimeSpan timeLeft;    
// Avoid
public DateTime client_Appointment;
public TimeSpan time_Left; 
// Exception (Class field)
private DateTime _registrationDate;
```

#### 9. USe nomes tipos primitivos (C# aliases) como `int`, `float`, `string` para declaração de variáveis. Use tipos do .NET Framework como `Int32`, `Single`, `String` para acessar memebros estáticos como `Int32.TryParse` ou `String.Join`.

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

#### 10. Use tipo implícito var para declaração local de variáveis. Exception: tipos primitivos (int, string, double, etc). 

```csharp 
var stream = File.Create(path);
var customers = new Dictionary();
// Exceptions
int index = 100;
string timeSheet;
bool isCompleted;
```

#### 11. Use substantivos e adjetivos para nomear uma classe.

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

#### 11. Use terminações para DTOs (Data Transfer Objects)


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




***Why: consistent with the Microsoft's .NET Framework and consistent with prior rule of no type indicators in identifiers.***

#### 21. Do use suffix EventArgs at creation of the new classes comprising the information on event:

```csharp 
// Correct
public class BarcodeReadEventArgs : System.EventArgs
{
}
```

***Why: consistent with the Microsoft's .NET Framework and easy to read.***

#### 22. Do name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:

```csharp 
public delegate void ReadBarcodeEventHandler(object sender, ReadBarcodeEventArgs e);
```

***Why: consistent with the Microsoft's .NET Framework and easy to read.***

#### 23. Do not create names of parameters in methods (or constructors) which differ only by the register:

```csharp 
// Avoid
private void MyFunction(string name, string Name)
{
  //...
}
```

***Why: consistent with the Microsoft's .NET Framework and easy to read, and also excludes possibility of occurrence of conflict situations.***

#### 24. DO use two parameters named sender and e in event handlers. The sender parameter represents the object that raised the event. The sender parameter is typically of type object, even if it is possible to employ a more specific type.

```csharp
public void ReadBarcodeEventHandler(object sender, ReadBarcodeEventArgs e)
{
  //...
}
```

***Why: consistent with the Microsoft's .NET Framework***

***Why: consistent with the Microsoft's .NET Framework and consistent with prior rule of no type indicators in identifiers.***

#### 25. Do use suffix Exception at creation of the new classes comprising the information on exception:

```csharp 
// Correct
public class BarcodeReadException : System.Exception
{
}
```

***Why: consistent with the Microsoft's .NET Framework and easy to read.***

#### 26. Do use suffix Any, Is, Have or similar keywords for boolean identifier :

```csharp 
// Correct
public static bool IsNullOrEmpty(string value) {
    return (value == null || value.Length == 0);
}
```

***Why: consistent with the Microsoft's .NET Framework and easy to read.***

## Offical Reference

1. [MSDN General Naming Conventions](http://msdn.microsoft.com/en-us/library/ms229045(v=vs.110).aspx)
2. [DoFactory C# Coding Standards and Naming Conventions](http://www.dofactory.com/reference/csharp-coding-standards) 
3. [MSDN Naming Guidelines](http://msdn.microsoft.com/en-us/library/xzf533w0%28v=vs.71%29.aspx)
4. [MSDN Framework Design Guidelines](http://msdn.microsoft.com/en-us/library/ms229042.aspx)