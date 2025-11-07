# O que é Code first?

**Code First** é a abordagem mais popular e natural para quem rá utilizar o Entity Framework Core.
 Basicamente o que você faz é o seguinte, em vez de criar todo banco de dados primeiro, você como programador se concentra no domínio,
e começa criando suas classes que posteriormente irão se materializar em tabelas de seu banco de dados, com as classes criadas,
você faz todo mapeamento através de métodos de extensão, o qual são conhecidos como **Fluent API** que é uma das formas de fazer todo mapeamento
de entidades utilizando métodos, ou **Data Annotations, que são atributos adicionados a uma classe ou uma propriedade.

# O que é DataBase First?

Diferente do **Code First**, no processo **Database First** primeiramente é criado o banco de dados, tabelas, campos e índices.
- 1°- Escrever todas as classes que representa suas entidades e relacionamentos, manualmente.
- 2°- É uma forma mais fácil, que é fazer engenharia revesa do banco de dados sem a necessidade de escrever todo código do zero, este processo chama-se Scaffold.

# O que é DbContext?
Em poucas palavras podemos definir como combinação dos padrões **UoW(Unit-of-Work)** e **Repository**, que contém um conjunto de métedos responsáveis
por gravar e ler informações do banco de dados.
O **DbContext** é classe principal e mais importante que você terá acesso, o objetivo dela é simplificar a interação de sua aplicação com seu banco de dados.

  Ela é responsável por:
- Configurar seu modelo de dados
- Gerenciar a conexão com o banco de dados
- Consultar e persistir dados em seu banco
- Fazer toda rastreabilidade de objetos
- Materializar resultados das consultas
- Cache de primeiro nível

Existe um outro método muito importante que é o **OnConfiguring**: 
É usado par informar qual provider se´ra utilizado e informar a string de conexão, logger, serviços customizados e outros.
Outro método extremamente impotante é o **OnmodelCreating**:
É usado para configurar todo modelo de dados que serão posteriormente transformados em tabelas e comandos SQL's.
E tem o mais importante que é o **SaveChanges**:
Método resonsável por coletar os dados que sofreram alterações e persistit no banco de dados.
