# EF¨EF Core
- Será abordado sobre: Performance, Consultas geradas e Inserção de registros em massa.

- Quando falado de performance o EF Core sai na frente por ser um produto que foi totalmente escrito do zero e muito mais otimizado
- ele é até 140% mais rápido que sua versão anterior
- Exemplo de Consultas: 

```
var alunos = ef6
.Alunos
.Include ("Cursos")
.Where(p => p.Nome == "Gustavo Ribeiro")
.ToList();
```
- Se utilizarmos o EF6, utilizando exatamente essa consulta acima, ele irá produzir uma care muito complexa.

```
SELECT
[Project1]. [C1] AS [C1],
[Project1]. [Id] AS [Id],
[Project1]. [Nome] AS [NOME],
[Project1].[C2] AS [C2],
[Project1].[Id1] AS [Id1],
[Project1].[Descricao] AS [Descricao],
[Project]. [AlunoId] AS [AlunoId]
FROM ( SELECT
[Exten1]. [Id] AS [Id],
[Extent1. [Nome] AS [Nome},
1 AS [C1],
[Extent2].[Id] AS [id],
[Extent2].[Descricao] AS [Descricao],
[Extent2].[Aluno] AS [AlunoId],
CASE WHEN([Extent2].[Id] IS NULL) THEN CAST(NULL AS int) ELSE 1 END AS [C2]
LEFT OUTER JOIN [dbo].[Cursos] AS [Extent2] ON [Extent1].[Id] = [Extent2].[AlunoId]
WHERE N 'Gustavo Ribeiro' = [Extent1].[Nome]
) AS[Project1]
ORDER BY [Project1].[Id] ASC, [Project1].[C2] ASC
```

- Agora, utilizando a mesma consulta com o EF Core:

```
var alunos = efcore
.Alunos
.Include ("Cursos")
.Where(p => p.Nome == "Gustavo Ribeiro")
.ToList();
```
- Ele ira produzir este exemplo abaixo:

```
SELECT [a].[Id], [a].[Nome], [c].[Id], [c].[AlunoId], [c].[Descricao]
FROM [Alunos] AS [a]
LEFT JOIN [Cursos] AS [C] ON [a].[Id] = [c].[AlunoId]
WHERE [a].[Nome] = N'Gustavo Ribeiro'
ORDER BY [a].[Id], [c].[Id]
```

- Percebe que existe uma diferença drastica. O EF Core produz uma muito mais limpa, muito mais otimizada

- Veremos agora um exemplo de Inserção em massa

```
for (int i = 1; i<= 5; i++)
{
  ef.Alunos.Add(new Aluno
  {
    Nome = $"Aluno {i}",
    Cursos = new[]
    {
      new Curso
      {
          Descricao= $"Curso {i}"
      }
    }
});
ef.SaveChanges();
```

veja um exemplo abaixo de como ficaria usando as aplicações:

```
TextData                                                                                                 AplicationName
exec sp_reset_connection                                                                                 EF6
exec sp_executesq1 N'INSERT [dbo].[Alunos] ([Nome]) VALUES (@0) SELECT [Id] FROM [dbo].[Alunos] WHERE... EF6
exec sp_executesq1 N'INSERT [dbo].[Alunos] ([Nome]) VALUES (@0) SELECT [Id] FROM [dbo].[Alunos] WHERE... EF6
exec sp_executesq1 N'INSERT [dbo].[Alunos] ([Nome]) VALUES (@0) SELECT [Id] FROM [dbo].[Alunos] WHERE... EF6
exec sp_executesq1 N'INSERT [dbo].[Alunos] ([Nome]) VALUES (@0) SELECT [Id] FROM [dbo].[Alunos] WHERE... EF6
exec sp_executesq1 N'INSERT [dbo].[Alunos] ([Nome]) VALUES (@0) SELECT [Id] FROM [dbo].[Alunos] WHERE... EF6
exec sp_executesq1 N'INSERT [dbo].[Cursos] ([Descricao], [AlunoId]) VALUES (@0) SELECT [Id] FROM [dbo].[Alunos] WHERE... EF6
exec sp_executesq1 N'INSERT [dbo].[Cursos] ([Descricao], [AlunoId]) VALUES (@0) SELECT [Id] FROM [dbo].[Alunos] WHERE... EF6
exec sp_executesq1 N'INSERT [dbo].[Cursos] ([Descricao], [AlunoId]) VALUES (@0) SELECT [Id] FROM [dbo].[Alunos] WHERE... EF6
exec sp_executesq1 N'INSERT [dbo].[Cursos] ([Descricao], [AlunoId]) VALUES (@0) SELECT [Id] FROM [dbo].[Alunos] WHERE... EF6
exec sp_executesq1 N'INSERT [dbo].[Cursos] ([Descricao], [AlunoId]) VALUES (@0) SELECT [Id] FROM [dbo].[Alunos] WHERE... EF6
_________________________________________________________________________________________________________________________________
exec sp_executeesq1 N'SET NOCOUNT ON; DECLARE @insertedo TABLE ([[id] bigint, [_Position] [int]); MERGE[...] EF Core
exec sp_executeesq1 N'SET NOCOUNT ON; DECLARE @insertedo TABLE ([[id] bigint, [_Position] [int]); MERGE[...] EF Core
```

- Percebe-se que o Entity Framework gerou um comando específico para cada objeto em nossa lista
- Já o Entity Framework Core ele foi muito mais inteligente.
Ele pegou os objetos que estavam na lista e gerou um unico comando com todas as informações para serem persistidas na base de dados.
