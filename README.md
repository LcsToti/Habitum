<img width="2856" height="600" alt="image" src="https://github.com/user-attachments/assets/e0b99889-5039-4f16-99a4-0aa6553d75f2" />

# 🔁 Habitum (API)

O projeto **Habitum** é um aplicativo que ajuda a criar e manter hábitos saudáveis, reduzindo a procrastinação com lembretes, monitoramento de progresso e recompensas gamificadas. 
Ele transforma a construção de hábitos em uma experiência envolvente, tornando a rotina mais produtiva e motivadora. 
O app é voltado para adolescentes e jovens adultos que querem mais disciplina, mas enfrentam dificuldades com distrações e falta de constância.

⚠️ Este repositório inclui somente a API do sistema.

**CONFIRA** 🎬 [Vídeo de Apresentação - 1 minuto](https://youtu.be/Lhrk6t1Eofo)

## Tecnologias Utilizadas

#### Front-end (Mobile)
- **Linguagem:** JavaScript / TypeScript  
- **Framework:** React Native, Expo  

#### Back-end
- **Linguagem:** C#  
- **Framework:** ASP.NET Core Web API  
- **Padrões e práticas:** RESTful API, Entity Framework Core (ORM), Princípios SOLID

#### Banco de Dados
- **SGBD:** MySQL  
- **Ferramenta:** MySQL Workbench

#### Serviços Web / Integrações
- API REST entre front-end e back-end
- Hospedagem futura: Azure

#### Ambientes e Ferramentas de Desenvolvimento
- **IDE Front-end:** Visual Studio Code  
- **IDE Back-end:** Visual Studio 2022
- **Gerenciador de pacotes:** npm (front-end), NuGet (back-end)  
- **Controle de versão:** Git + GitHub

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
