<img width="2856" height="600" alt="Banner Habitum" src="https://github.com/user-attachments/assets/e0b99889-5039-4f16-99a4-0aa6553d75f2" />

# 🔁 Habitum (API)

O projeto **Habitum** é um aplicativo que ajuda a criar e manter hábitos saudáveis, reduzindo a procrastinação com lembretes, monitoramento de progresso e recompensas gamificadas.
Ele transforma a construção de hábitos em uma experiência envolvente, tornando a rotina mais produtiva e motivadora.
O app é voltado para adolescentes e jovens adultos que querem mais disciplina, mas enfrentam dificuldades com distrações e falta de constância.

> ⚠️ **Este repositório contém somente a API.** O aplicativo mobile é um componente separado do sistema.

🔗 **Swagger da API publicada:** https://habitum-api.lucastoti.com

🎬 **[Vídeo de apresentação — 1 minuto](https://youtu.be/Lhrk6t1Eofo)**

## Tecnologias utilizadas

### Aplicativo mobile (componente separado)

![Expo](https://img.shields.io/badge/expo-1C1E24?style=for-the-badge&logo=expo&logoColor=%23D04A37)
![React Native](https://img.shields.io/badge/react_native-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)
![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/tailwindcss-%2338B2AC.svg?style=for-the-badge&logo=tailwind-css&logoColor=white)

### Backend

![C#](https://img.shields.io/badge/c%23-%23239120.svg?style=for-the-badge&logo=csharp&logoColor=white)
![.NET 8](https://img.shields.io/badge/.NET_8-5C2D91?style=for-the-badge&logo=.net&logoColor=white)
![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)

## Arquitetura

A aplicação segue uma arquitetura cliente-servidor, composta por três partes principais: aplicativo mobile, API e banco de dados.

O funcionamento ocorre da seguinte forma:

1. O aplicativo mobile envia requisições HTTP para a API.
2. A API processa a lógica da aplicação.
3. Os dados são armazenados e consultados no banco de dados.
4. A API retorna respostas em formato JSON.
5. O aplicativo exibe as informações para o usuário.

```text
[ App Mobile ] ⇄ [ API ] ⇄ [ Banco de Dados ]
```

### Organização do backend

O backend é organizado em módulos para separar responsabilidades:

- **Features:** agrupam funcionalidades da aplicação, como autenticação, usuários, desafios, notificações e relacionamentos, com controllers, services e repositories.
- **Models:** representam as entidades e o contexto de dados.
- **Exceptions:** definem erros personalizados da aplicação.
- **Extensions:** centralizam o registro de serviços e as configurações de banco de dados, autenticação, CORS, Swagger e tarefas agendadas.
- **Middlewares:** concentram comportamentos executados durante o processamento das requisições.
- **Migrations:** versionam as alterações do esquema do banco com o Entity Framework Core.

Essa organização mantém o código modular, facilitando a manutenção e a evolução do sistema.

## Instruções de utilização

### Pré-requisitos

- [.NET 8 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)
- **MySQL 8.0** em execução
- **Git**
- **EF Core CLI** (`dotnet-ef`), para aplicar as migrations
- Opcional: MySQL Workbench e Visual Studio/VS Code com suporte a C#

### 1. Clonar o repositório

```bash
git clone https://github.com/LcsToti/Habitum.git
cd Habitum/src
```

### 2. Configurar a conexão com o MySQL e a autenticação JWT

No arquivo `src/appsettings.json` (dentro do diretório `src`), configure as seções `ConnectionStrings` e `JwtSettings` com os valores do seu ambiente:

```json
{
  "ConnectionStrings": {
    "HabitumContext": "Server=localhost;Port=3306;Database=habitum;User=root;Password=SUA_SENHA;"
  },
  "JwtSettings": {
    "SecretKey": "SUBSTITUA_POR_UMA_CHAVE_ALEATORIA_LONGA_E_SECRETA",
    "Issuer": "HabitumAPI",
    "Audience": "HabitumClient"
  }
}
```

> O exemplo mostra apenas as seções que precisam ser preenchidas; preserve as demais configurações do arquivo. Não publique credenciais ou chaves reais em commits. Em desenvolvimento, você também pode usar **.NET User Secrets** para armazená-las fora do repositório.

### 3. Restaurar dependências e aplicar migrations

Na pasta `Habitum/src`:

```bash
dotnet restore
dotnet tool install --global dotnet-ef --version 8.0.3
dotnet ef database update
```

Se `dotnet-ef` já estiver instalado, não é necessário instalá-lo novamente; verifique se está em uma versão compatível com o EF Core 8.

> O MySQL deve estar em execução e a string de conexão deve apontar para uma instância acessível antes de aplicar as migrations.

### 4. Executar a API

```bash
dotnet run --launch-profile dev
```

A documentação Swagger estará disponível, no ambiente de desenvolvimento, em:

**http://localhost:5100/**

O perfil `dev` utiliza HTTP na porta **5100**, conforme `src/Properties/launchSettings.json`.

### Observação sobre Docker

O repositório também inclui `Dockerfile`, `docker-compose.yml` e scripts de inicialização. O Compose existente foi preparado para uma infraestrutura que utiliza a rede Docker externa `npm-data_default`; por isso, **não é uma configuração local independente pronta para executar sem adaptações**.
