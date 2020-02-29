# Classes e Design Patterns
É muito comum se estudar orientação objetos, saber as definições de classes, interfaces, métodos, níveis de acesso, mas é um pouco difícil aplicar no dia a dia. 

Aqui, nós consideramos que se o desenvolvedor trabalhar com algumas limitações, ele vai se obrigar a aplicar algum padrão. Por exemplo, se uma classe tiver um limite máximo de linhas, o desenvolvimento do módulo se obriga a aplicar padrões de projeto. 

Em nosso style guide, o limite é de 50 linhas é suficiente para uma classe comportar algoritmo e suas documentações / comentários.  A media que se torna necessário aumentar essa quantidade de linhas, o desenvolvedor se obrigado a aplicar princípios de acoplamento, coerência e padrões de projeto (clássicos e o nosso) para organizar a classe, tanto de forma física ou lógica.

## Conteúdo
- [Classes e Design Patterns](#classes--e--design--patterns)
- [Técnicas Básicas](#t%C3%A9cnicas-b%C3%A1sicas)
  + [Regras de Ouro](#regras-de-ouro)
  + [Coesão e Acoplamento](#coes%C3%A3o-e-acoplamento)
  + [Design Patterns Tradicionais e obrigatórios](#design-patterns-tradicionais-e-obrigat%C3%B3rios)
  + [Design Pattern - Mash-up - Partial](#design-patterns-mash-up-partial)

# Técnicas Básicas

## Regras de Ouro

**Regra de Ouro** 
Seu código deve ser claro como uma redação. Inspirado como uma poesia. A prática da comunicação é importante. Pois se você fala ou escreve mal sobre qualquer assunto. Teu código vai ser ruim também. 

**Regra de Ouro Branco** 
Você não escreve pra você. Você escreve para os outros!
Será que alguém vai entender o que eu fiz? Será que esse nome expressa o que quero dizer? Essas perguntas são autocríticas e nos forçam a revisar o que estamos fazendo.

**Regra de Ouro Rose**
Não interessa a linguagem de programação. Engenharia de software é o mais importante!

## Coesão e acoplamento

**Coerência** é definida como a qualidade de ser lógico, consistente e capaz 
de ser entendido. Imagine a coerência como um edifício.

**Coesão** por outro lado, refere-se ao ato de formar uma unidade inteira. 
É efetivamente um subconjunto de coerência. 
Imagine a coesão como os tijolos e o cimento que compõem o edifício.

## Design Patterns Tradicionais e obrigatórios

Recomenda-se domínio completo dos seguintes padrões:

### Design pattern comportamental
  1. https://www.dofactory.com/net/template-method-design-pattern 
  2. https://www.dofactory.com/net/strategy-design-pattern
  3. https://www.dofactory.com/net/command-design-pattern
### Design pattern esrutural
  1. https://www.dofactory.com/net/facade-design-pattern 
  2. https://www.dofactory.com/net/proxy-design-pattern
  3. https://www.dofactory.com/net/decorator-design-pattern
## Design pattern criacional
  1. https://www.dofactory.com/net/singleton-design-pattern 
  2. https://www.dofactory.com/net/abstract-factory-design-pattern

Mais informações aqui: https://www.dofactory.com/net/design-patterns

**Orientação geral**
1. Decore esses 9 padrões.
2. Tenha domínio dos padrões na ordem de categoria (Comportamental, Estrutual e criacional)
3. Não se preocupe em criar seu algorítimo aplicando o padrão primeiro. Faça seu algorítimo primeiro, depois aplique o padrão. Com o tempo você vai usar os padrões de forma tácita e fará a medida que for concluindo seu desenvolvimento.
4. Decore esses 9 padrões.
5. Decore esses 9 padrões de novo.
6. Decore esses 9 padrões mais uma vez.

## Design Patterns Mash-up (partial)

Organizar sua lógica em arquivos físicos diferentes podem ajudar seu código a ficar mais manutenível.

Por exemplo, dividir uma class Core, que está no arquivo Core.cs em sub grupos seguindo o exemplo a seguir:
1. Core.cs
2. Core.Grupo1.cs
3. Core.Grupo2.cs

**Core.cs**
```csharp
using System.Collections.Generic;
using System.Linq;

namespace Revendus.Core.Processo.Mensagem.Enviar
{
    /// <summary>
    /// Objetivo da classe, bem curto.
    /// </summary>
    /// <remarks>
    /// linha 1 de documentação
    /// linha 2 de documentação
    /// linha 3 de documentação
    /// linha 4 de documentação
    /// linha 5 de documentação
    /// </remarks>
    public partial class Core
    {
        #region construtor
        private readonly IController _controller;
        private Data.Remetente _remetente;

        public Data.Remetente Remetente
        {
            get { return _remetente; }
        }
        public Core(IController controller)
        {
            _controller = controller;
        }

        public Core()
            : this(new Controller())
        {

        }
        #endregion
      
       
        public void Executar()
        {
            FazerPasso1();
            if (FazerPasso2())
            {
                FazerPasso3();
                FazerPasso4();
            }           
        }
    }
}

```
**Core.Grupo1.cs**
No arquivo físico Core.Grupo1.cs terá os métodos com responsabilidades similares:

```csharp
using System.Collections.Generic;
using System.Linq;

namespace Revendus.Core.Processo.Mensagem.Enviar
{
    public partial class Core
    {
        /// <summary>
        /// Objetivo do FazerPasso1, bem curto. Posi o nome do método deve se explicar sozinho
        /// </summary>
        /// <remarks>
        /// linha 1 de documentação
        /// linha 2 de documentação
        /// </remarks>
        public void FazerPasso1()
        {
                    
        }
        /// <summary>
        /// Objetivo do FazerPasso2, bem curto. Posi o nome do método deve se explicar sozinho
        /// </summary>
        /// <remarks>
        /// linha 1 de documentação
        /// linha 2 de documentação
        /// </remarks>
        public void FazerPasso2()
        {
                    
        }
    }
}
```

**Core.Grupo2.cs**
No arquivo físico Core.Grupo1.cs terá os métodos com responsabilidades similares:

```csharp
using System.Collections.Generic;
using System.Linq;

namespace Revendus.Core.Processo.Mensagem.Enviar
{
    public partial class Core
    {
        /// <summary>
        /// Objetivo do FazerPasso4, bem curto. Posi o nome do método deve se explicar sozinho
        /// </summary>
        /// <remarks>
        /// linha 1 de documentação
        /// linha 2 de documentação
        /// </remarks>
        public void FazerPasso3()
        {
                    
        }
        /// <summary>
        /// Objetivo do FazerPasso4, bem curto. Posi o nome do método deve se explicar sozinho
        /// </summary>
        /// <remarks>
        /// linha 1 de documentação
        /// linha 2 de documentação
        /// </remarks>
        public void FazerPasso4()
        {
                    
        }
    }
}
