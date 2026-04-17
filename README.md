<img width="2856" height="600" alt="image" src="https://github.com/user-attachments/assets/e0b99889-5039-4f16-99a4-0aa6553d75f2" />

# 🔁 Habitum (API)

O projeto **Habitum** é um aplicativo que ajuda a criar e manter hábitos saudáveis, reduzindo a procrastinação com lembretes, monitoramento de progresso e recompensas gamificadas. 
Ele transforma a construção de hábitos em uma experiência envolvente, tornando a rotina mais produtiva e motivadora. 
O app é voltado para adolescentes e jovens adultos que querem mais disciplina, mas enfrentam dificuldades com distrações e falta de constância.

⚠️ Este repositório inclui somente a API do sistema.

**CONFIRA** 🎬 [Vídeo de Apresentação - 1 minuto](https://youtu.be/Lhrk6t1Eofo)

## Tecnologias Utilizadas

### Frontend

![Expo](https://img.shields.io/badge/expo-1C1E24?style=for-the-badge&logo=expo&logoColor=#D04A37)
![React Native](https://img.shields.io/badge/react_native-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)
![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/tailwindcss-%2338B2AC.svg?style=for-the-badge&logo=tailwind-css&logoColor=white)

### Backend

![C#](https://img.shields.io/badge/c%23-%23239120.svg?style=for-the-badge&logo=csharp&logoColor=white)
![.Net](https://img.shields.io/badge/.NET-5C2D91?style=for-the-badge&logo=.net&logoColor=white)
![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)

## Arquitetura

A aplicação segue uma arquitetura cliente-servidor, composta por três partes principais: aplicativo mobile, API e banco de dados.

O funcionamento ocorre da seguinte forma:

1. O aplicativo mobile envia requisições HTTP para a API
2. A API processa a lógica da aplicação
3. Os dados são armazenados e consultados no banco de dados
4. A API retorna uma resposta em formato JSON
5. O aplicativo exibe as informações para o usuário

```
[ App Mobile ] ⇄ [ API ] ⇄ [ Banco de Dados ]
```

### Backend

O backend é organizado em módulos para separar responsabilidades:

- **Features**: A ngrupam as funcionalidades da aplicação (contendo **DTOs**, **Interfaces**, **Services**, **Repositories** e **Controllers**)
- **Models**: representam as entidades do sistema e a estrutura dos dados
- **Exceptions**: definem erros personalizados da aplicação
- **Extensions**: centralizam configurações e extensões utilizadas no projeto

Essa organização mantém o código modular, facilitando manutenção e evolução do sistema.

# Instruções de utilização

### ✅ Pré-requisitos

- **.NET 9 SDK** (Preview): https://dotnet.microsoft.com/en-us/download/dotnet/9.0
- **MySQL 8.0+**
- (Opcional) **MySQL Workbench**
- **Git**
- (Opcional) **Visual Studio** ou VS Code com extensão C#

---

### 1. Clonar o repositório:

```bash
git clone https://github.com/ICEI-PUC-Minas-PMV-ADS/pmv-ads-2025-1-e3-proj-mov-t4-habitum
cd pmv-ads-2025-1-e3-proj-mov-t4-habitum/src/habitumAPI
```

---

### 2. Editar o arquivo `appsettings.json`:

```json
{
  "ConnectionStrings": {
    "HabitumContext": "Server=localhost;Port=3306;Database=habitum;User=root;Password=root;"
  }
}
```

> Altere `User` e `Password` conforme seu MySQL local. Se não for usar banco local, ajuste também `Server` e `Port`.

---

### 3. Aplicar Migrations:

> ⚠️ Se o `appsettings.json` não estiver corretamente configurado, este passo falhará.

**Com Visual Studio (Console NuGet):**

```powershell
Update-Database
```

**Ou no terminal:**

```bash
dotnet ef database update
```

---

### 4. Rodar o back-end:

```bash
dotnet run --launch-profile "dev"
```

> Acesse via Swagger em:  
> `https://localhost:5100/` (HTTPS)  
> ou `http://192.168.0.100:5100/` (HTTP, substitua o "192.168.0.100" pelo IP real da máquina)
