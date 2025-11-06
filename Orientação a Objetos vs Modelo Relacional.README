# Orienteção a Objetos vs Modelo Relacional
- A Orientação a objetos é muito rica em diversos aspectos da programação
- pode representar uma estrutura de dados de difentes formas como: Herança, Polimorfismo, Composição
- Já o relacional apesar do bancos de dados terem evoluidos bastantes nos ultimos anos, o seu papel principal
continua de ser um repositório que é armazenar e entregar pro consumidor posteriormente
- O ORM é a ponte entre o mundo real da programação Orientada a Objetos e o mundo relacional

# Herança
- A Herança é uma classe que é derivada de uma outra classe ou a classe mãe como muitos conhecem
- que tem suas propriedades e herda as propriedades dessa classe mãe juntamente com seus comportamentos
- exemplo abaixo:

```
public class Pessoa
{
  public int Id { ger; set; }
  public string Nome { get; set; }
  public int Idade { get; set;}
  public string Email { get; set; }
  public string CPF { get; set;}

public bool ECPFValido()
{
  // TODO:
}

  public bool EEmailValido()
{
  // TODO
}

public void FazAniversario()
{
  Idade++;
}
}
```
**Composição**
- Basicamente é quando você tem uma classe composta por uma outra classe. Exemplo abaixo

```
public class ItemPedido
{
  public Guid Key { get; set; }
  public Guid ProdutoId { get; set; }
  public int Quantidade { get; set; }
  public decimal Valor { get; set; }
  public int PedidoId { get; set;}
  public Pedido Pedido { get; set;}
}
```
```
public class Pedido
{
  public int Id { get; set; }
  public int ClientId { get; set; }
  public DateTime DataPedido { get; set; }
  public String Observacao { get; set; }
  public List<ItemPedido> Itens { get; set; }
}
```
