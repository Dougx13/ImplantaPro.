# ImplantaPro

> Sistema desktop para gestão de implantação de clientes, desenvolvido como simulação da rotina de um Analista de Implantação de Software.

O **ImplantaPro** centraliza o acompanhamento de um novo cliente desde o cadastro e a reunião de kickoff até a homologação, o go-live e a conclusão da implantação. A aplicação utiliza dados fictícios e foi criada para demonstrar processos de negócio, organização de informações e desenvolvimento de software desktop.

## Principais funcionalidades

- Dashboard com indicadores de implantações em andamento, concluídas, aguardando retorno, atrasadas e progresso médio;
- Cadastro, edição, pesquisa e exclusão permanente de clientes;
- Armazenamento de CNPJ, contato, segmento, telefone, e-mail, quantidade de usuários e observações internas;
- Identificação de **CRM** para segmentos de saúde/medicina e **OAB** para segmentos de advocacia;
- Fluxo de implantação com etapas de contratação, kickoff, configuração, importação de dados, treinamento, homologação e go-live;
- Controle de responsável, prazo, situação, data de conclusão e observações para cada etapa;
- Checklist de implantação com cálculo automático de progresso;
- Registro de treinamentos, participantes, instrutor e status;
- Histórico de atividades por cliente;
- Autenticação com criação de contas, administração de usuários, exclusão de usuários e senhas protegidas por hash PBKDF2;
- Tour guiado para novos usuários e opção de sair da conta com retorno à tela de login;
- Banco de dados SQLite local e portátil, sem necessidade de instalar SQL Server.

## Tecnologias utilizadas

| Tecnologia | Finalidade |
| --- | --- |
| C# / .NET 8 | Linguagem e plataforma da aplicação |
| WPF | Interface desktop Windows |
| Entity Framework Core | Persistência e acesso aos dados |
| SQLite | Banco de dados local portátil |
| MVVM | Organização entre interface, estado e regras da aplicação |

## Como executar pelo Visual Studio

1. Instale o [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0) e o Visual Studio com a carga de trabalho **Desenvolvimento para desktop com .NET**.
2. Clone ou baixe este repositório.
3. Abra o arquivo `ImplantaPro.sln`.
4. Defina `ImplantaPro.Desktop` como projeto de inicialização.
5. Pressione `F5`.

Na primeira execução, o arquivo `implantapro.db` é criado ao lado do executável. Ele guarda os usuários, clientes e demais registros da aplicação.

## Como executar pelo terminal

Na pasta raiz da solução, execute:

```powershell
dotnet restore
dotnet build
dotnet run --project .\ImplantaPro.Desktop
```

## Versão portátil

O projeto pode ser publicado como executável Windows autossuficiente. Essa versão funciona em outro computador sem SQL Server e sem a instalação do .NET, desde que estes arquivos permaneçam juntos:

```text
ImplantaPro.Desktop.exe
implantapro.db
```

Para gerar a publicação:

```powershell
dotnet publish .\ImplantaPro.Desktop\ImplantaPro.Desktop.csproj `
  -c Release `
  -r win-x64 `
  --self-contained true `
  -p:PublishSingleFile=true `
  -p:IncludeNativeLibrariesForSelfExtract=true `
  -o .\publish
```

## Estrutura do projeto

| Pasta/arquivo | Responsabilidade |
| --- | --- |
| `Models` | Entidades do domínio: clientes, etapas, checklist, treinamentos, usuários e histórico. |
| `Data` | `DbContext`, configuração do SQLite e inicialização do banco. |
| `Services` | Autenticação, hash de senha e sessão do usuário. |
| `ViewModels` | Estado das telas, comandos e regras de apresentação. |
| `MainWindow.xaml` | Tela principal do sistema e bindings WPF. |
| `LoginWindow.xaml` | Tela de acesso, criação de contas e exibição/ocultação de senha. |

## Credenciais de demonstração

| E-mail | Senha |
| --- | --- |
| `acesso@implantapro.local` | `Acesso@2026` |

> As demais senhas não são exibidas ou armazenadas em texto puro. O sistema utiliza hash PBKDF2 para protegê-las.

## Descrição para GitHub e LinkedIn

> Projeto desenvolvido como simulação de um processo de implantação de software, contemplando cadastro de clientes, parametrização, acompanhamento de etapas, checklist operacional, treinamento de usuários, homologação e entrada em produção. A solução foi construída em C# com WPF, Entity Framework Core e SQLite, incluindo autenticação de usuários e uma versão portátil para demonstração.

---

Desenvolvido por **Douglas Pinheiro Rodrigues**.
