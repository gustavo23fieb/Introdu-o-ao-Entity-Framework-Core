# Introdução ao Entity Framework Core
Início do Curso Entity Framwork Core

# O que é um ORM?
- Object relational mapping, ou seja mapeamento onjeto-relacional.(ORM)
- Com uma visão mais simplicada, o ORM possibilita o mapeamento das classes de seu projeto, com as tanelas de um banco de dados
  ```
  Aplicação > ORM > Banco de dados
```
CREATE TABLE Produtos(
Id INT PRIMARY KEY,
Descricao VARCHAR (100),
Valor DECIMAL (10,2) DEFAULT 0,
Estoque BIGINT DEFAULT 0
)
```
No código front de sua aplicação tem um classe chamada produto. exemplo abaixo:

```
public class Produto
{
  public int Id { get; set; }
  public string Descricao { get; set; }
  public decimal Valor { get; set; }
  public long Estoque { get; set; }
}
```
O ORM fica bem no meio desses dois códigos. entre sua aplicação e o banco de dados
- O ORM ele irá fazer exatamente esse papel, que é pegar essa informações do banco e criar uma instância já probulada

