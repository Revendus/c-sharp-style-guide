
# Classes e Design Patterns
Primeiro, é preciso se familiralizar com Design Patterns, principalmente se você entende vagamente e no sabe de cabeça o que usar e quando usar. Estudo todos os padrões se atentando as diferentes categorias **Creational, Structural e Behavioral**  

Para entender a estrutura atual ou mesmo criar seguindo nosso padrão, recomenda-se  domínio completo dos seguintes padrões:
1. Comportamental
..1. https://www.dofactory.com/net/template-method-design-pattern 
..2. https://www.dofactory.com/net/strategy-design-pattern
..3. https://www.dofactory.com/net/command-design-pattern
2. Esrutural
..1. https://www.dofactory.com/net/facade-design-pattern 
..2. https://www.dofactory.com/net/proxy-design-pattern
..3. https://www.dofactory.com/net/decorator-design-pattern
3. Criacional
..1. https://www.dofactory.com/net/singleton-design-pattern 
..2. https://www.dofactory.com/net/abstract-factory-design-pattern

Mais informações aqui: https://www.dofactory.com/net/design-patterns

**Orientação geral**
1. Decore esses 9 padrões.
2. Tenha domínio dos padrões na ordem de categoria (Comportamental, Estrutual e criacional)
3. Não se preocupe em criar seu algorítimo aplicando o padrão primeiro. Faça seu algorítimo primeiro, depois aplique o padrão. Com o tempo você vai usar os padrões de forma tácita e fará a medida que for concluindo seu desenvolvimento.
4. Decore esses 9 padrões.
5. Decore esses 9 padrões de novo.
6. Decore esses 9 padrões mais uma vez.


Por exemplo, dividir os arquivos em grupos:
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
