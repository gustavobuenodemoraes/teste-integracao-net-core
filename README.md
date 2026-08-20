# 📋 Coisas a Fazer — Testes de Integração & Dublês de Teste em .NET Core

Aplicação desenvolvida para demonstrar estratégias de **Testes de Integração**, uso de **Dublês de Teste (Test Doubles)** e isolamento de dependências externas em uma arquitetura orientada a comandos (CQRS Lite) no .NET Core.

---

## 🎯 Objetivo & Conceitos Aplicados

O repositório aborda a transição de validações manuais para testes automatizados de integração:

- **Padrão Command Handler:** Separação de intenções (`Commands`) e execuções (`Handlers`) para cadastro e gerenciamento de tarefas.
- **Test Doubles (Fakes, Stubs e Mocks):** Substituição da persistência real (`IRepositorioTarefas`) por implementações controladas (`RepoFakeTarefas` / `RepositorioFake`) durante a suíte de testes.
- **Testes de Integração em Camadas:**
  - **Handlers:** Validação do fluxo completo de execução de regras de negócio (`CadastraTarefaHandler`, `GerenciaPrazoDasTarefasHandler`).
  - **Controllers:** Testes de integração direta sobre endpoints MVC (`TarefasControllerEndpointCadastraTarefa`).
  - **I/O Redirection:** Simulação de entrada e saída em testes com `ConsoleReadLine` e `ConsoleWriteLine`[cite: 3].

---

## 🏗️ Estrutura da Solução

```text
├── src/
│   ├── Alura.CoisasAFazer.Core/            # Entidades de domínio, Enums e Commands[cite: 3]
│   ├── Alura.CoisasAFazer.Infrastructure/  # DbContext (EF Core) e Repositórios[cite: 3]
│   ├── Alura.CoisasAFazer.Services/        # Handlers e processamento de regras de negócio[cite: 3]
│   └── Alura.CoisasAFazer.WebApp/          # Interface Web / API ASP.NET Core MVC[cite: 3]
│
├── tests/
│   ├── Alura.CoisasAFazer.ConsoleApp/     # Validação manual via console de testes[cite: 3]
│   └── Alura.CoisasAFazer.Testes/         # Suíte automatizada de testes de integração e mocks[cite: 3]
│
└── Alura.CoisasAFazer.sln                 # Arquivo de solução .NET[cite: 3]