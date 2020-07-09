# Organização das classes

Um bom layout usa formatação para enfatizar a estrutura do código e para facilitar a leitura de código.

## Ordem dos elementos em uma classe:

* Fields 
* Constructors 
* Finalizers (Destructors) 
* Delegates 
* Events 
* Enums 
* Interfaces 
* Properties 
* Indexers 
* Methods 
* Structs 
* Classes

## Exemplos

Variáveis de classe (Fields) devem ser declaradas antes de construtor, seguindo a ordem de maior para menor visibilidade.

```C#
public class Foo
{
    public string _var1;
    protected string _var2;
    private string _var3;

    public Foo()
    {
        
    }
}    
```

Propriedades devem ser declaradas após o construtor, seguindo a ordem de maior para menor visibilidade.

```C#
public class Foo
{
    public Foo()
    {

    }

    public string Var1 { get; set; }
    protected string Var2 { get; set; }
    private string Var3 { get; set; }
}    
```

Métodos devem ser declarados após as propriedades, observando a ordem em que são chamados no código, agrupados pelo grau de visibilidade da maior para a menor.

```C#
public class Foo
{
    public Foo()
    {

    }

    public string Var1 { get; set; }

    public void Method1()
    {
        PrivateMethod1();
        ProtectedMethod();
        PrivateMethod2();
    }

    protected void ProtectedMethod()
    {

    }

    private void PrivateMethod1()
    {

    }

    private void PrivateMethod2()
    {
        
    }
}
```



