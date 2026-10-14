# Tarefa 09 — Documentação de Software

> **Aula:** 09
>
> **Prazo:** 24 de outubro de 2026, às 23h59
>
> **Status:** 🔄 Em revisão

[← Voltar ao README principal](../../README.md)

## 🎯 Objetivo

Escolher um projeto de software e elaborar sua documentação, apresentando o objetivo, o problema que pretende resolver, o escopo e os principais requisitos funcionais e não funcionais, além das tecnologias, da arquitetura e da organização dos componentes.

O critério que orientou o trabalho foi a pergunta proposta em aula:

> "Se eu entrar hoje no GitHub do seu projeto, consigo entender e executar o projeto sem perguntar nada para vocês?"

## 📋 Proposta da atividade

1. Escolher um projeto de software.
2. Documentar objetivo, problema, escopo e requisitos funcionais e não funcionais.
3. Descrever tecnologias, arquitetura e organização dos componentes.
4. Criar ou atualizar o `README.md` do repositório no GitHub.
5. Incluir pré-requisitos e instruções de instalação, configuração e execução.
6. Documentar, quando aplicável, APIs, banco de dados, variáveis de ambiente, testes e deploy.

## 💻 Projeto documentado

O projeto escolhido foi o **InsEmpodera**, sistema web desenvolvido por estudantes da Fatec para o Instituto Empodera. A aplicação registra comunidades, atores sociais, recursos, atividades, diários de campo, fichas de primeiro contato e avaliações pessoais, com controle de acesso por perfis, relatórios e importação/exportação em Excel.

| Item | Informação |
| --- | --- |
| Repositório | [Oroboni/InsEmpodera](https://github.com/Oroboni/InsEmpodera) |
| Branch documentada | [`Online`](https://github.com/Oroboni/InsEmpodera/tree/Online), onde está o desenvolvimento ativo |
| Tecnologias principais | .NET 9, ASP.NET Core MVC, Entity Framework Core, MySQL/MariaDB, SQLite, ASP.NET Core Identity |
| Testes existentes | xUnit, Playwright, Vitest e Stryker.NET, executados com GitHub Actions |

### Equipe do projeto

- Isadora Correa
- Matheus Cuero
- Maria Julia Loureiro
- Sophia Marcelino

## 🗂️ Documentação produzida

O `README.md` do InsEmpodera foi reescrito como porta de entrada da documentação, e os detalhes técnicos foram distribuídos na pasta `docs/`:

```text
InsEmpodera/
├── README.md                          # Visão geral, execução rápida e índice
└── docs/
    ├── requisitos.md                  # RF-001 a RF-012, RNF-001 a RNF-014, regras e limitações
    ├── arquitetura.md                 # Componentes, inicialização, pipeline HTTP e autenticação
    ├── instalacao-e-configuracao.md   # Instalação com SQLite ou MySQL, variáveis e problemas comuns
    ├── banco-de-dados.md              # Entidades, modelo ER, chaves, dados iniciais e scripts
    ├── rotas-e-integracoes.md         # Rotas MVC, downloads, JSON e serviços externos
    ├── testes.md                      # Suítes automatizadas, CI e validação manual
    └── deploy.md                      # Pipelines, publicação manual e rollback
```

Os diagramas foram escritos em Mermaid, que o GitHub renderiza diretamente: visão geral da arquitetura, inicialização, fluxo de requisição, autenticação, modelo de dados e fluxo de entrega.

## ✅ Critérios atendidos

| Critério da aula | Onde foi atendido |
| --- | --- |
| Objetivo, problema e escopo | README — Visão geral e Escopo |
| Requisitos funcionais e não funcionais | README (resumo) e `docs/requisitos.md` |
| Tecnologias e versões | README — Tecnologias, com versões conferidas nos arquivos do projeto |
| Arquitetura e componentes | README — Arquitetura e `docs/arquitetura.md` |
| Pré-requisitos, instalação, configuração e execução | README — Como executar e `docs/instalacao-e-configuracao.md` |
| Variáveis de ambiente | README — Configuração |
| Banco de dados | `docs/banco-de-dados.md` |
| APIs | `docs/rotas-e-integracoes.md`, que registra que o sistema não possui API REST pública |
| Testes | `docs/testes.md`, com o registro do que foi e do que não foi executado |
| Deploy | `docs/deploy.md`, que descreve a implantação manual existente |
| Ausência de dados sensíveis | Exemplos com valores fictícios; nenhuma senha, IP ou identificador de infraestrutura repetido |

## 🧪 Validação realizada

Os comandos documentados foram executados em um ambiente macOS com .NET SDK 10 e uma instância MySQL temporária:

| Verificação | Resultado |
| --- | --- |
| Compilação da solução | Sucesso, sem erros |
| Execução em modo de demonstração (SQLite) | Login e todas as páginas do menu responderam corretamente |
| Criação do banco MySQL pelo EF Core e execução em `Development` | Banco criado com 34 tabelas; login validado em `https://localhost:7121` |
| Testes de backend | 220 aprovados |
| Testes de interface | 157 aprovados |

Os testes E2E e o script `testar.ps1` não foram executados, pois dependem do PowerShell e do download do Chromium.

## ⚠️ Principais descobertas

- A branch `main` do InsEmpodera está desatualizada; o código atual está na branch `Online`.
- O projeto não possui migrations: o esquema é criado pelo EF Core apenas no ambiente `Testing`.
- A versão atual do `Banco.txt` não é compatível com o modelo da aplicação e falhou ao ser importada.
- Algumas rotas antigas, fora do menu, retornam erro 500 por não terem página correspondente.
- O repositório contém dados de comunidades e pessoas, além de detalhes da infraestrutura AWS, que merecem revisão pela equipe.

## 🔗 Referências

- [Material da Aula 09](<../Conteúdo/Aula 09 - Documentação de Software.pdf>)
- [Aula — Documentação de Software](https://github.com/deivisontakatu/aula-documentacao-software), repositório de apoio da aula.
