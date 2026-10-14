# Tarefa 09 — Documentação de Software

> **Aula:** 09
>
> **Prazo:** 24 de outubro de 2026, às 23h59
>
> **Status:** ✅ Concluída

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
| Importação do `Banco.txt` corrigido e uso da aplicação sobre ele | Sem erros; login e telas principais funcionando |

Os testes E2E e o script `testar.ps1` não foram executados, pois dependem do PowerShell e do download do Chromium.

## 🛠️ Problemas encontrados e correções

A análise do código para a documentação revelou problemas que foram corrigidos no próprio projeto:

| Problema encontrado | Correção |
| --- | --- |
| A branch `main` estava 173 commits atrás da `Online` | Integrada pela [PR #8](https://github.com/Oroboni/InsEmpodera/pull/8) |
| O `Banco.txt` tinha as chaves trocadas para `binary(16)` e falhava na importação | Restaurados os tipos originais, compatíveis com a aplicação, com valores padrão aceitos pelo MySQL e pelo MariaDB |
| `Database/Empodera.schema.sql` estava desatualizado, sem as colunas do Identity | Regenerado a partir do modelo atual |
| Oito rotas antigas, fora do menu, retornavam erro 500 | Passaram a redirecionar para as telas equivalentes |
| O README dos testes E2E afirmava que eles usavam SQLite e que a recuperação de senha era apenas visual | Texto corrigido |

As correções foram integradas à branch `main` pela [PR #9](https://github.com/Oroboni/InsEmpodera/pull/9), mantendo a branch `Online` para o desenvolvimento. Os testes continuaram aprovados depois delas (220 no backend e 157 na interface).

Permanecem como pontos de atenção para a equipe: o projeto não possui migrations, e o repositório contém dados de comunidades e pessoas, além de detalhes da infraestrutura AWS.

## 🔗 Referências

- [Material da Aula 09](<../Conteúdo/Aula 09 - Documentação de Software.pdf>)
- [Aula — Documentação de Software](https://github.com/deivisontakatu/aula-documentacao-software), repositório de apoio da aula.
