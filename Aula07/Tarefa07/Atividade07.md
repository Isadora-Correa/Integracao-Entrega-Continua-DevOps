# Tarefa 07 — Testes automatizados e pipeline de CI

> **Aula:** 07
>
> **Prazo:** 26 de setembro de 2026, às 23h59
>
> **Status:** ✅ Concluída

[← Voltar ao README principal](../../README.md)

## 🎯 Objetivo

Criar um novo projeto que integre três tipos de testes automatizados — **unitário, integração e performance** — organizando cada suíte para que possa ser executada e analisada de maneira independente.

O projeto também deveria possuir uma pipeline de Integração Contínua com GitHub Actions, configurada para instalar as dependências e executar automaticamente os três tipos de testes após cada `push` na branch `main`.

## 📋 Proposta da atividade

1. Criar um novo projeto.
2. Implementar testes unitários.
3. Implementar testes de integração.
4. Implementar testes de performance.
5. Permitir que cada tipo de teste seja executado separadamente.
6. Criar um workflow YAML no GitHub Actions.
7. Configurar a execução automática após cada `push` na `main`.
8. Instalar as dependências e executar as três suítes na pipeline.
9. Verificar e apresentar os resultados.

## 💻 Projeto desenvolvido

O projeto criado foi a **UX Feedback API**, uma API REST para registrar avaliações sobre a experiência de uso de interfaces, sistemas e aplicativos.

A aplicação foi desenvolvida com Node.js, JavaScript e Express. Os dados são mantidos em memória, dispensando a configuração de um banco de dados e permitindo concentrar a atividade na implementação dos testes e da pipeline.

### Rotas disponíveis

| Método | Rota | Descrição |
| --- | --- | --- |
| `GET` | `/feedbacks` | Lista todos os feedbacks cadastrados |
| `GET` | `/feedbacks/:id` | Localiza um feedback pelo ID |
| `POST` | `/feedbacks` | Cria um feedback com projeto, nota e comentário |
| `DELETE` | `/feedbacks/:id` | Exclui um feedback existente |

As notas aceitas são números inteiros entre 1 e 5. O serviço também valida a presença do nome do projeto e do comentário antes de criar um novo registro.

## 🧰 Tecnologias utilizadas

| Tecnologia | Utilização |
| --- | --- |
| Node.js 22 | Ambiente de execução da aplicação |
| JavaScript | Linguagem utilizada no projeto e nos testes |
| Express | Criação da API e das rotas HTTP |
| Jest | Execução dos testes unitários e de integração |
| Supertest | Requisições à aplicação Express durante os testes de integração |
| k6 | Simulação de carga e análise de performance |
| Git e GitHub | Versionamento e armazenamento remoto |
| GitHub Actions | Execução automatizada das três suítes de testes |

## 🗂️ Estrutura do projeto

```text
automated-testing-ci/
├── .github/
│   └── workflows/
│       └── ci.yml
├── scripts/
│   └── run-performance.sh
├── src/
│   ├── controllers/
│   │   └── feedbackController.js
│   ├── routes/
│   │   └── feedbackRoutes.js
│   ├── services/
│   │   └── feedbackService.js
│   ├── app.js
│   └── server.js
├── tests/
│   ├── integration/
│   │   └── feedbackRoutes.test.js
│   ├── performance/
│   │   └── feedbacks.k6.js
│   └── unit/
│       └── feedbackService.test.js
├── package.json
├── package-lock.json
└── README.md
```

A separação entre `unit`, `integration` e `performance` facilita a execução individual, a identificação de falhas e a manutenção de cada categoria.

## 🧪 Testes automatizados

### 1. Testes unitários

Os testes unitários verificam isoladamente as funções do `feedbackService`, sem realizar requisições HTTP. A suíte possui sete casos de teste e analisa:

- aceitação de notas inteiras entre 1 e 5;
- rejeição de notas inválidas;
- validação de um feedback completo;
- identificação de todos os campos incorretos;
- criação de feedback com ID incremental;
- remoção de espaços externos nos textos;
- lançamento de erro para dados inválidos;
- localização de registros pelo ID.

Execução independente:

```bash
npm run test:unit
```

O script utiliza Jest com `--runInBand`, executando a suíte do diretório `tests/unit` em sequência.

### 2. Testes de integração

Os testes de integração utilizam Jest e Supertest para validar o funcionamento conjunto das rotas, controladores e serviços da API. O Supertest envia requisições diretamente à aplicação Express, sem a necessidade de abrir uma porta externa.

Os sete casos implementados verificam:

- listagem dos feedbacks;
- busca de um registro existente;
- resposta `404` para ID inexistente;
- criação de um feedback válido com resposta `201`;
- resposta `400` para dados inválidos;
- exclusão de um registro com resposta `204`;
- tentativa de excluir um ID inexistente.

O armazenamento em memória é reiniciado antes de cada teste, evitando que um caso altere o resultado do seguinte.

Execução independente:

```bash
npm run test:integration
```

### 3. Testes de performance

O teste de performance utiliza k6 para simular acessos concorrentes ao endpoint `GET /feedbacks`. O cenário executa **cinco usuários virtuais durante cinco segundos**.

```javascript
export const options = {
  vus: 5,
  duration: '5s',
  thresholds: {
    http_req_duration: ['p(95)<500'],
    http_req_failed: ['rate<0.01'],
    checks: ['rate>0.99']
  }
};
```

Os critérios definidos exigem:

- percentil 95 do tempo de resposta abaixo de 500 ms;
- taxa de requisições com falha inferior a 1%;
- mais de 99% das verificações concluídas com sucesso;
- resposta HTTP com status `200`;
- corpo da resposta contendo uma lista.

Execução independente:

```bash
npm run test:performance
```

O script `run-performance.sh` inicia a API temporariamente, aguarda sua disponibilidade, executa o k6 e encerra o servidor mesmo quando ocorre uma falha.

## ⚙️ Scripts disponíveis

Os comandos foram definidos no `package.json`:

| Comando | Função |
| --- | --- |
| `npm start` | Inicia a API na porta 3000 |
| `npm run test:unit` | Executa apenas os testes unitários |
| `npm run test:integration` | Executa apenas os testes de integração |
| `npm run test:performance` | Inicia a API e executa o cenário do k6 |
| `npm test` | Executa as suítes unitária e de integração em sequência |

## 🔄 Pipeline de Integração Contínua

O workflow foi criado em `.github/workflows/ci.yml` e recebe o nome **Continuous Integration**.

### Gatilhos

A pipeline é iniciada automaticamente a cada `push` na branch `main`:

```yaml
on:
  push:
    branches:
      - main
  workflow_dispatch:
```

O gatilho `workflow_dispatch` também permite iniciar o processo manualmente pela aba Actions.

As permissões foram limitadas a `contents: read`, suficientes para baixar e testar o código sem conceder acesso de escrita ao workflow.

### Jobs independentes

A pipeline possui três jobs independentes, exibidos separadamente no gráfico do GitHub Actions:

```text
                 ┌─ Unit Tests
Push na main ────┼─ Integration Tests
                 └─ Performance Tests
```

Como não existe uma dependência `needs` entre eles, os jobs podem ser executados em paralelo. Uma falha em qualquer suíte faz com que o workflow seja marcado como falho, mas os demais testes continuam produzindo resultados próprios.

### Etapas compartilhadas

Os três jobs utilizam `ubuntu-latest` e executam estas etapas:

1. checkout do repositório;
2. configuração do Node.js 22 LTS e do cache do npm;
3. instalação reprodutível das dependências com `npm ci`;
4. execução da suíte correspondente ao job.

O job **Performance Tests** possui uma etapa adicional com `grafana/setup-k6-action@v1`, responsável por instalar o k6 antes do teste de carga.

| Job | Comando principal | Ferramenta |
| --- | --- | --- |
| Unit Tests | `npm run test:unit` | Jest |
| Integration Tests | `npm run test:integration` | Jest e Supertest |
| Performance Tests | `npm run test:performance` | k6 |

## ▶️ Execução e resultados

As suítes unitária e de integração foram reproduzidas localmente com instalação limpa das dependências por meio de `npm ci`.

| Suíte | Arquivos | Testes | Resultado |
| --- | :---: | :---: | :---: |
| Unitária | 1 | 7 | ✅ Aprovada |
| Integração | 1 | 7 | ✅ Aprovada |
| Performance | 1 | Cenário com 5 VUs por 5 segundos | Executada pelo job com k6 |

O npm também realizou a auditoria de 365 pacotes e não encontrou vulnerabilidades. A execução local do teste de performance depende da instalação do k6; na pipeline, essa dependência é preparada automaticamente pela Action da Grafana.

## ✅ Resultado

A atividade resultou em uma API organizada e acompanhada por três níveis complementares de validação:

- os **testes unitários** verificam isoladamente as regras de negócio;
- os **testes de integração** avaliam o comportamento completo dos endpoints;
- o **teste de performance** mede estabilidade e tempo de resposta sob acessos simultâneos.

A separação em diretórios, scripts e jobs independentes torna mais simples identificar em qual nível uma falha ocorreu. A pipeline automatiza a preparação do ambiente e executa as três suítes após cada `push` na `main`, fornecendo retorno contínuo sobre a qualidade do projeto.

## 🔗 Recursos

- [Repositório automated-testing-ci](https://github.com/Isadora-Correa/automated-testing-ci)
- [Workflow de integração contínua](https://github.com/Isadora-Correa/automated-testing-ci/blob/main/.github/workflows/ci.yml)
- [Material da Aula 07](<../Conteúdo/Aula 07 - Testes Automatizados.pdf>)

## 🧭 Navegação

[← Tarefa 06](../../Aula06/Tarefa06/Atividade06.md) · [README principal](../../README.md)
