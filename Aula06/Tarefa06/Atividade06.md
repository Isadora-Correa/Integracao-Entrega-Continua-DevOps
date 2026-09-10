# Tarefa 06 — Integração de pipeline e análise de repositórios

> **Aula:** 06
>
> **Prazo:** 19 de setembro de 2026, às 23h59
>
> **Status:** 🚧 Em andamento

[← Voltar ao README principal](../../README.md)

## 🎯 Objetivo

Integrar uma pipeline ao projeto utilizando o GitHub Actions e configurar sua execução automática sempre que um novo `push` for realizado na branch principal (`main`).

A atividade também propõe pesquisar e analisar pelo menos três repositórios do GitHub que utilizem pipelines, destacando suas características, funcionalidades, gatilhos e histórico de execução.

## 📋 Proposta da atividade

1. Integrar uma pipeline ao projeto com GitHub Actions.
2. Configurar o workflow para ser executado a cada `push` na branch `main`.
3. Executar e verificar o funcionamento das etapas automatizadas.
4. Buscar repositórios do GitHub que possuam integração de pipeline.
5. Selecionar pelo menos três repositórios.
6. Analisar as características, funcionalidades, gatilhos e o histórico de cada pipeline.
7. Documentar os resultados obtidos.

## 1️⃣ Parte 1 — Pipeline do projeto

### Projeto escolhido

A pipeline foi integrada a este repositório, responsável por armazenar os conteúdos e as atividades da disciplina de Integração e Entrega Contínua. Como o projeto é composto principalmente por documentos Markdown e materiais em PDF, as etapas foram adaptadas para validar, empacotar e publicar essa documentação.

### Arquivo do workflow

O workflow está definido em:

```text
.github/workflows/pipeline.yml
```

O gatilho principal atende ao requisito da atividade:

```yaml
on:
  push:
    branches: [main]
```

Também foi incluído o gatilho `workflow_dispatch`, que permite iniciar uma execução manualmente pela aba **Actions** quando for necessário testar ou repetir o processo.

### Actions utilizadas

| Action | Função na pipeline |
| --- | --- |
| `actions/checkout@v7` | Baixa o conteúdo do repositório no ambiente de execução |
| `actions/upload-artifact@v7` | Armazena temporariamente a documentação e o pacote gerados |
| `actions/download-artifact@v8` | Recupera os artefatos em jobs posteriores |
| `peaceiris/actions-gh-pages@v4.1.0` | Publica a documentação na branch `gh-pages` |

### Etapas da pipeline

Os jobs foram conectados com a propriedade `needs`, formando um fluxo sequencial semelhante ao utilizado na Tarefa 05:

```text
Build
  ↓
Test
  ↓
Quality
  ↓
Security
  ↓
Package
  ↓
Deploy
  ↓
Smoke Test
  ↓
Performance
  ↓
Monitoring
```

#### 1. Build

Prepara a documentação para publicação. O README principal é copiado como `index.md`, as pastas das aulas são adicionadas ao diretório `dist` e os arquivos essenciais são conferidos. O resultado é salvo como artefato para os jobs seguintes.

#### 2. Test

Verifica se existem pelo menos seis atividades documentadas e analisa todos os links locais presentes nos arquivos Markdown. A execução falha caso algum caminho referencie um arquivo inexistente.

#### 3. Quality

Confere o padrão dos documentos Markdown. A etapa exige um título principal no início de cada arquivo e identifica espaços ou tabulações desnecessárias no final das linhas.

#### 4. Security

Pesquisa padrões conhecidos de chaves privadas, tokens do GitHub e chaves de acesso da AWS. A publicação é interrompida quando uma possível credencial exposta é encontrada.

#### 5. Package

Recupera o artefato gerado no build, cria o pacote compactado `documentacao-devops.tar.gz`, verifica sua integridade e o disponibiliza como artefato da execução.

#### 6. Deploy

Publica o conteúdo preparado na branch `gh-pages`. O token temporário fornecido pelo GitHub Actions autoriza a atualização da branch durante a execução.

#### 7. Smoke Test

Baixa a versão recém-publicada e confirma a existência do índice e das atividades essenciais. Essa verificação garante que os arquivos chegaram ao destino esperado.

#### 8. Performance

Calcula o tamanho total da documentação publicada e verifica se o resultado permanece abaixo do limite de 50 MB estabelecido para o projeto.

#### 9. Monitoring

Consulta o repositório remoto e confirma que a branch `gh-pages` está disponível. Quando essa verificação termina com sucesso, a pipeline é considerada concluída.

### Execução esperada

Após o envio do workflow à branch `main`, o GitHub Actions deverá iniciar a pipeline automaticamente. Cada job aparecerá como um nó no gráfico da execução e somente avançará quando a etapa anterior for concluída com sucesso.

```text
Novo push em main → Validações → Empacotamento → Publicação → Verificações finais
```

## 2️⃣ Parte 2 — Análise de repositórios

> ⏳ **Aguardando os prints e os links dos três repositórios escolhidos.**

Nesta parte serão registradas, para cada repositório, as seguintes informações:

- objetivo e características do projeto;
- arquivo e estrutura do workflow;
- funcionalidades automatizadas;
- eventos utilizados como gatilhos;
- organização e dependência entre os jobs;
- histórico de execuções;
- resultados, falhas e aspectos relevantes observados.

### Repositório 1

Informações a serem adicionadas.

### Repositório 2

Informações a serem adicionadas.

### Repositório 3

Informações a serem adicionadas.

## 🚧 Resultado parcial

A primeira parte da atividade foi implementada com uma pipeline adequada à estrutura deste repositório. O workflow automatiza a validação da documentação, a busca por possíveis credenciais, o empacotamento, a publicação e as verificações finais.

A atividade permanecerá marcada como **em andamento** até que a análise dos três repositórios seja incluída.

## 🔗 Recursos

- [Workflow da Tarefa 06](../../.github/workflows/pipeline.yml)
- [Repositório da disciplina](https://github.com/Isadora-Correa/Integracao-Entrega-Continua-DevOps)
- [Material da Aula 06](<../Conteúdo/Aula 06 - Revisão Ferramentas e Pipelines.pdf>)

## 🧭 Navegação

[← Tarefa 05](../../Aula05/Tarefa05/Atividade05.md) · [README principal](../../README.md)
