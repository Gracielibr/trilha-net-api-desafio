# API Gerenciadora de Tarefas - Desafio .NET DIO
## Descrição do Projeto
Este projeto é um sistema gerenciador de tarefas desenvolvido como parte do desafio da trilha .NET da DIO. A aplicação consiste em uma API RESTful que permite realizar operações CRUD (Create, Read, Update, Delete) em uma lista de tarefas, com funcionalidades para organização da rotina diária.

### Tecnologias Utilizadas
- .NET 9.0 - Framework principal

- Entity Framework Core 9.0 - ORM para acesso a dados

- SQLite - Banco de dados relacional (arquivo .db)

- Swagger/OpenAPI - Documentação e teste da API

- ASP.NET Core Web API - Estrutura da API REST

### Estrutura do Projeto
TrilhaApiDesafio/
├── Controllers/
│   └── TarefaController.cs
├── Models/
│   └── Tarefa.cs
├── Context/
│   └── OrganizadorContext.cs
├── Migrations/
│   └── (arquivos de migração)
├── Properties/
├── Program.cs
├── appsettings.json
├── appsettings.Development.json
└── TrilhaApiDesafio.csproj

## Passo a Passo da Implementação
### 1. Fork e Clonagem do Repositório
- Realizado fork do repositório original da DIO

- Clonado para a máquina local no diretório D:\DIO\desfio-tarefas

### 2. Atualização de Versões
- Atualizado o projeto de .NET 6.0 para .NET 9.0

- Atualizados os pacotes NuGet:

- Microsoft.EntityFrameworkCore.SqlServer para versão 9.0.0

- Microsoft.EntityFrameworkCore.Tools para versão 9.0.0

- Swashbuckle.AspNetCore para versão 7.2.0

- Microsoft.AspNetCore.Mvc.NewtonsoftJson para versão 9.0.0

### 3. Configuração do Banco de Dados
- Alterada a conexão de SQL Server para SQLite devido à ausência do LocalDB

- Configurada a string de conexão no appsettings.json e appsettings.Development.json

- Criado arquivo de banco de dados SQLite: OrganizadorDB.db

### 4. Implementação dos Endpoints
Completados todos os métodos do TarefaController.cs:

#### GET /Tarefa/{id}

- Busca uma tarefa pelo ID

- Retorna NotFound se não encontrada

#### GET /Tarefa/ObterTodos

- Retorna todas as tarefas cadastradas

#### GET /Tarefa/ObterPorTitulo

- Filtra tarefas por título (contém)

#### GET /Tarefa/ObterPorData

-Filtra tarefas por data específica

#### GET /Tarefa/ObterPorStatus

- Filtra tarefas por status (Pendente/Finalizado)

#### POST /Tarefa

- Cria uma nova tarefa

- Validação da data não pode ser vazia

#### PUT /Tarefa/{id}

- Atualiza uma tarefa existente

- Validação da data e existência do registro

#### DELETE /Tarefa/{id}

- Remove uma tarefa do sistema

### 5. Configuração do Entity Framework
- Criado DbContext (OrganizadorContext) com DbSet<Tarefa>

- Configurada injeção de dependência no Program.cs

- Adicionado suporte para serialização de enums (JsonStringEnumConverter)
### 6. Migrações do Banco de Dados
- Criada migration inicial: InitialCreate

- Executado comando para criar a tabela no banco:
```
dotnet ef migrations add InitialCreate
dotnet ef database update
```
### 7. Modelo de Dados
A classe Tarefa contém as seguintes propriedades:

- Id (int): Identificador único

- Titulo (string): Título da tarefa

- Descricao (string): Descrição detalhada

- Data (DateTime): Data da tarefa

- Status (EnumStatusTarefa): Status (Pendente/Finalizado)

### 8. Execução da Aplicação
A API está configurada para rodar em:

HTTP: http://localhost:5181

HTTPS: https://localhost:7295

Swagger UI: https://localhost:7295/swagger

## Estrutura do Banco de Dados
A tabela Tarefas contém as seguintes colunas:

- Id (INTEGER, PRIMARY KEY, AUTOINCREMENT)

- Titulo (TEXT, NOT NULL)

- Descricao (TEXT, NOT NULL)

- Data (TEXT, NOT NULL)

- Status (INTEGER, NOT NULL)

## Considerações Finais
Este projeto representou um desafio prático onde não partimos do zero, mas sim de um código base fornecido através de um fork. A proposta era completar uma API seguindo especificações pré-definidas, corrigindo e implementando o que estava faltando.

Como desenvolvedor em formação na trilha .NET da DIO, este exercício foi valioso para consolidar conhecimentos adquiridos sobre Entity Framework e construção de APIs Web. Embora não tenha sido meu primeiro contato com desenvolvimento de APIs (já tendo trabalhado com Minimal APIs anteriormente), esta foi uma oportunidade de trabalhar com uma estrutura mais completa seguindo o padrão MVC.

**O processo envolveu várias etapas importantes:**

- **Adaptação do ambiente:** Tive que atualizar versões do .NET e pacotes NuGet para compatibilidade com meu sistema, migrando de .NET 6 para .NET 9.

- **Solução de problemas de infraestrutura:** Encontrei desafios com o banco de dados SQL Server LocalDB que não estava disponível no meu ambiente. Isso me levou a pesquisar alternativas e implementar uma solução com SQLite, o que exigiu ajustes na configuração do DbContext e nas strings de conexão.

- **Implementação lógica:** Completei os métodos do controller que estavam marcados com "TODO", seguindo as regras de negócio especificadas. Isso incluiu a criação dos endpoints CRUD e dos filtros por título, data e status.

- **Gerenciamento de migrations:** Aprendi na prática como criar e aplicar migrações do Entity Framework, um conceito que havia estudado teoricamente mas não tinha implementado em projetos anteriores.

- **Configuração do projeto:** Tive que entender e ajustar arquivos de configuração como appsettings.json e Program.cs para que toda a aplicação funcionasse corretamente.

O resultado final é uma API RESTful completamente funcional para gerenciamento de tarefas, com todos os endpoints solicitados operacionais. A implementação do Swagger facilita o teste e a documentação da API, enquanto o uso do SQLite torna o projeto portável e fácil de executar em qualquer ambiente.

Este desafio reforçou a importância de saber ler e entender código escrito por outros desenvolvedores, adaptar soluções a diferentes ambientes e seguir especificações técnicas rigorosas - competências essenciais para qualquer desenvolvedor profissional.


