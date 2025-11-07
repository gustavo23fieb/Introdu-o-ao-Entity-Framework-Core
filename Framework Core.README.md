# Entity Framework Core
**Entity Framework Core** é o nome do produto, o papel que ele desempenha é o de um ORM.

Ele nos permite focar exatamente nas regras de negócio, abstraindo totalmente a camada de acesso
ao banco de dados, ou seja você não precisa escrever nenhum comando SQL em sua aplicação.

# Como Funciona o Entity Framework Core?
- Aplicação > Entity Framework Core ORM >  AO.NET > Banco de Dados

# Contexto Histórico do Entity Framework
- A primeira versão foi lançada em 2008 juntamente com o Linq + EF 3.5
- Em 2010 é lançada EF 4.0
- em 2011 a microsoft percebe que esse não é o melhor caminho e lanca o EF 4.1 como um pacote separado.
não tão aclopado no .NET Framework
- No mesmo ano em 2011 é lançada a versão 4.3
- entre a vesão 4.1 e a 4.3 surge o conceito de codefirst. Onde podemos criar nossa classes e dizer aos frameworks como elas serão mapeadas
-  em 2012 a microsoft surpreende a todos e apresenta o EF 5.0 como projeto de código aberto.
Disponibiliza os fontes em uma plataforma chamada codeplasq
- no ano posterior 2013 ela migra esse projeto para o GitHub junto com o EF 6.0
- no ano de 2017 é lançado o EF 6.2 que foi uma das versões mais estáveis do Entity Framework
- no ano de 2019 é lançado o que seria a última versão do Entity Framework que é a versão EF 6.4

# Contexto Histórico Do Entity Framework Core
- Ele foi anunciado em 2014 e seu nome inicial era Entity Framework 7
- No ano de 2016 é lançado sua primeira versão EF Core 1.0
- em 2017 é lançado a versão 2.0 que já trazia a possibilidade de mapeamento de funções calarios de um banco de dados.
- No ano de 2018 é lançado EF Core 2.1 (LTS - 2021) que trazia também algumas features importantes como:
lase load, suporte para transações, conversão de valores e o principal suporte ao grupbuy
- No ano de 2019 é lançada a versão EF Core 3.0
- Também em 2019 mais especificamente no dia 03/12/2019 é anunciada a versão EF Core 3.1(LTS -2022)

# Por que o Entity Framework foi reescrito do zero?

- No ano de 2012, 2013 a Microsoft já estava escrevendo o novo runtime para o .NET. Então o time do Entity Framework se reúne
e decide que ali seria hora certa de escrever o novo Rm para dar uma nova experiência ao usuário
- Em resumo o nascimento dele se deu por causa de otimização
