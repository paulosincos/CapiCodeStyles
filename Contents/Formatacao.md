# Formatação

## Linhas em branco

Definições de uso de linhas em branco.

### Separação de elementos em classes

Devem haver separações de linhas em branco entre:

- métodos;
- construtores;
- listas de propriedades e/ou campos;
- Qualquer outros elementos que formem um "bloco visual", como um uma sub classe, ou a definição de um enum interno.

Exemplo:
```c#
public class Exemplo
{
    private readonly _private1;
    private readonly _private2;
    private readonly _private3;

    public Exemplo()
    {
      // constrói exemplo...
    }

    public string PropriedadeA { get; set; }
    public int PropriedadeB { get; set; }
    public DateTime PropriedadeC { get; set; }

    public void FazerAlgo()
    {
      // faz algo...
    }

    public void FazerAlgoDiferente()
    {
      // faz algo diferente...
    }
}
```

### Organização de um algoritimo

Devem haver linhas em branco separando instruções de blocos de código do restante do código dentro de um bloco.

Exemplo:

```c#
public void ReporEstoque()
{
  if (!EstaPronto)
  {
    DeixarPronto();
  }

  ContinuarOQuePrecisaFazer();
  var estoque = ObterEstoque();
  var quantidade = ObterQuantidadeAtual(estoque);

  while (quantidade < QuantidadeMaxima)
  {
    quantidade += GerarIncremento(estoque);
  }

  AvisarSetorVendas();
}
```

### Linhas em branco não permitidas

**Não** devem haver linhas em branco em:

- Início e fim de arquivos;
- Início e fim de classes;
- Início e fim de métodos;
- Entre lista de propriedades e/ou campos;
- Inícios e finais de blocos de chaves.

Também não deve haver uma separação maior que 1 linha em branco aos locais em que se aplica o uso de linhas em branco.

## Complexidade em condicionais encadeadas

Não devem haver mais do que 3 expressões boleanas concatenadas dentro de condicionais encadeadas.

Exemplos incorreto:

```C#
if (Traje.Tipo == TipoDeTrajeEsperado
  && (
    IdadeAtual >= IdadeMinima
    || EstaAcompanhadoDeResponsavel
  )
  && PossuiIngresso)
{
  // if com 4 condicionais boleanas
}
```

Exemplos corretos:

```C#
var haResponsabilidadeLegal = IdadeAtual >= IdadeMinima
    || EstaAcompanhadoDeResponsavel;

if (Traje.Tipo == TipoDeTrajeEsperado
  && haResponsabilidadeLegal
  && PossuiIngresso)
{
  // if com 3 expressões boleanas
}
```

Usando uma classe rica e indo além:

```C#
// Definição de propriedades na classe com getter:
public bool HaResponsabilidadeLegal => IdadeAtual >= IdadeMinima || EstaAcompanhadoDeResponsavel; // Apenas 2 operadores aqui
public bool PossuiTrajeAdequado => Traje.Tipo == TipoDeTrajeEsperado;
public bool PodeEntrar => HaResponsabilidadeLegal && PossuiTrajeAdequado && PossuiIngresso; // Apenas 3 operadores aqui

// Código comportamental dentro do algorítimo:
if (PodeEntrar)
{
  // if com 1 expressão booleana, diminuindo a complexidade geral do método em que se encontra.
}
```

## Tamanhos

Definições gerais de tamanhos permitidos.

### Arquivos

Um arquivo de código não deve ultrapassar 100 linhas.

Se o seu aquivo está maior do que isso, tente abstrair mais, criando novas classes e delegando a elas partes da responsabilidade da classe inicial.

### Métodos

Um método não deve ultrapassar 20 linhas, incluindo sua assinatura e bloco.

Se um método passar deste tamanho, tente abstrai-lo mais, criando mais métodos, separando melhor a responsabilidade.

### Linhas

Não usar mais de uma instrução por linha. Considera-se instrução tudo que é finalizado por um ponto e vírgula. Salvo exceção, a instrução _for_, neste caso, use o bom senso para quebrar ou não linhas.

Linhas não podem ultrapassar **100** caracteres, salvo exceções por nomes grandes de elementos de código.

Caso ultrapasse o limite de caracteres, quebra corretamente as expressões dessa linha em várias linhas.

#### Quebrando linhas

Uma vez que for necessário quebrar linhas, a linha deve ser quebrada em todos os locais possíveis, sendo um local de quebra de linha:

- Acesso a métodos e/ou propriedades por ponto ( **.** );
- Separação por vírgula de parametros em declarações ou consumos de métodos;

Expressões lambdas, quando necessário, podem ser quebradas após a declaração do lambda ( **=>** ).

## Métodos

Métodos que contiverem apenas uma linhas de código devem ser convertidos em _expression bodied methods_.

---

## TODOs

identação, chaves obrigatórias,

tamanho dos arquivos e métodos,

quantidade de parametros dos métodos, tuplas

comentários

alinhamento de declarações.

Espaço e não tab.

unica instrução por linha.

Espaços em parametros de métodos

Parênteses em construções sem parametros

Operadores binários separados por espaços

Casts (Separados por espaços?)

Remover associações implicitas declaradas explicitamente

Nomes de métodos e outros elementos, padrões de nomeclatura

Static factories ao invés de sobrecarga de construtores ?

Não deixar código comentado

Como escrever comentários

Recomendar Productivity Power tools e Sonar Lint, falar de como configurar

Adicionar exemplos em todos os tópicos possíveis

Quebrar este artigo em sub-tópicos ???