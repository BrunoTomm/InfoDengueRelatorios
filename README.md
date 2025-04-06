# 🦟 InfoDengue Relatório

Este projeto é uma API em ASP.NET Core 8 que consulta e armazena dados epidemiológicos relacionados às arboviroses (_dengue_, _chikungunya_ e _zika_) a partir da API pública do InfoDengue. Ele permite o gerenciamento de relatórios, consulta por município, agrupamento por doenças e controle de solicitantes.

---

## 📦 Tecnologias Utilizadas

- .NET 8
- ASP.NET Core Web API
- Entity Framework Core
- CQRS + MediatR
- AutoMapper
- Swashbuckle (Swagger)
- SQL Server (via EF)
- Clean Architecture (Camadas: Domain, Application, Infra, WebAPI)

---

## 🔧 Configuração e Execução

1. **Clone o projeto:**

   ```bash
   git clone https://github.com/BrunoTomm/InfoDengueRelatorios.git
   ```

2. **Configure o appsettings.json:**

   - Adicione a `ConnectionString` do SQL Server

3. **Rode as migrations (caso aplicável):**
   ```bash
   dotnet ef database update
   ```

---

## 📚 Funcionalidades

### ✅ Relatórios Epidemiológicos

- `/api/InfoDengue/relatorios/sp-rj`  
  Gera relatórios com os dados dos municípios de **São Paulo** e **Rio de Janeiro**.

- `/api/InfoDengue/relatorios/por-codigo-ibge`  
  Gera relatórios para um município específico a partir do **Código IBGE**.

---

### 📊 Dados Agrupados

- `/api/InfoDengue/relatorios/total-casos/sp-rj`  
  Retorna o **total de casos** de arboviroses por município (SP/RJ).

- `/api/InfoDengue/relatorios/total-casos/por-arbovirose`  
  Retorna o **total de casos por arbovirose** em um município específico.

---

### 🧾 Histórico

- `/api/InfoDengue/relatorios-historico`  
  Lista todo o histórico de relatórios gerados, incluindo nome e CPF do solicitante.

---

### 🙋 Solicitantes

- `/api/InfoDengue/solicitantes`  
  Lista todos os usuários que solicitaram relatórios, com seus respectivos dados.

---

## 📌 Enum Arboviroses

```csharp
public enum TipoArbovirose
{
    dengue = 1,
    chikungunya = 2,
    zika = 3
}
```

---

## 📁 Estrutura do Projeto

```
src/
│
├── InfoDengueRelatorio.Dominio         → Regras de negócio, entidades, DTOs
├── InfoDengueRelatorio.Infra           → Persistência, Repositórios, EF Core
├── InfoDengueRelatorio.WebApi          → Controllers, Configurações de Startup
├── InfoDengueRelatorio.Cliente         → Consumo da API InfoDengue
```

---

## ✅ Boas Práticas Adotadas

- Separação de responsabilidades (Domain Driven Design)
- Injeção de dependência por construtor
- Conversão de enums descritivos no Swagger
- Validação de CPF e dados via `DataAnnotations`
- Manipulação segura com `try/catch` e mensagens amigáveis
- `CancellationToken` aplicado nas chamadas assíncronas

---

## ✍️ Autor

## **Bruno Tomm**

## 📄 Licença

MIT License. Livre para uso e modificação.
