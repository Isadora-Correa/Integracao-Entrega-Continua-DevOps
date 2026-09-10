# Tarefa 05 — Pipeline automatizada com GitHub Actions

> **Aula:** 05
>
> **Prazo:** 12 de setembro de 2026, às 23h59
>
> **Status:** ✅ Concluída

[← Voltar ao README principal](../../README.md)

## 🎯 Objetivo

Desenvolver um projeto que utilize três Actions disponíveis no GitHub Marketplace em uma pipeline automatizada, aplicando cada uma delas em uma etapa adequada do processo de integração e entrega contínua.

Também fizeram parte da atividade a configuração e a execução do workflow no GitHub Actions, a verificação de todas as etapas e a documentação das funções e contribuições de cada Action.

## 📋 Proposta da atividade

1. Escolher três Actions disponíveis no GitHub Marketplace.
2. Desenvolver um projeto que utilize as ferramentas selecionadas.
3. Aplicar cada Action em uma etapa adequada da pipeline.
4. Configurar o workflow no GitHub Actions.
5. Executar a pipeline e verificar o funcionamento de cada etapa.
6. Documentar as Actions utilizadas, suas funções e suas contribuições para a automação.

## 💻 Projeto desenvolvido

O projeto criado foi o **UX em Foco**, uma página educativa sobre UX Design. Além de apresentar conteúdos relacionados à experiência do usuário, a aplicação serviu como base para demonstrar um fluxo automatizado de integração e entrega contínua com GitHub Actions.

O projeto utiliza HTML, CSS e JavaScript na interface e Node.js para executar os scripts de build, testes e análise de qualidade definidos no `package.json`.

## 🧰 Tecnologias utilizadas

- HTML, CSS e JavaScript;
- Node.js 22 e npm;
- Git e GitHub;
- GitHub Actions;
- GitHub Pages;
- Vercel.

## ⚙️ Actions selecionadas

| Action | Etapa | Função | Contribuição para a automação |
| --- | --- | --- | --- |
| `actions/checkout@v5` | Preparação | Baixa o conteúdo do repositório para o ambiente temporário do job | Permite que os arquivos do projeto sejam acessados pelas etapas de build, teste, análise e deploy |
| `actions/setup-node@v6` | Preparação do ambiente | Instala e configura o Node.js 22, além de habilitar o cache do npm | Padroniza o ambiente de execução e reduz o tempo gasto com a instalação de dependências |
| `peaceiris/actions-gh-pages@v4.1.0` | Deploy | Publica o conteúdo da pasta `dist` na branch `gh-pages` | Automatiza a disponibilização da versão validada no GitHub Pages |

### `actions/checkout@v5`

Cada job do GitHub Actions é executado em um ambiente isolado. Por isso, a Action de checkout é utilizada no início dos jobs que precisam acessar o código. Ela obtém a versão correta do repositório e prepara os arquivos para os comandos seguintes.

### `actions/setup-node@v6`

Essa Action configura o Node.js 22 e o cache do npm. Com um ambiente padronizado, os comandos `npm ci`, `npm test`, `npm run lint` e `npm run build` podem ser executados da mesma maneira em diferentes jobs e execuções.

### `peaceiris/actions-gh-pages@v4.1.0`

Após todas as validações anteriores, essa Action recebe a pasta `dist`, gerada pelo build de produção, e publica seu conteúdo na branch `gh-pages`. O acesso é autorizado pelo `GITHUB_TOKEN` disponibilizado durante o workflow.

## 🗂️ Estrutura principal do projeto

```text
Pipeline-Devops/
├── .github/
│   └── workflows/
│       └── pipeline.yml
├── scripts/
├── tests/
├── index.html
├── style.css
├── script.js
├── package.json
├── package-lock.json
└── vercel.json
```

O arquivo `.github/workflows/pipeline.yml` contém a definição da pipeline. Os diretórios `scripts` e `tests` armazenam as rotinas utilizadas nas verificações do projeto.

## 🔄 Funcionamento da pipeline

A pipeline é iniciada nas seguintes situações:

- envio de commits para a branch `main`;
- abertura ou atualização de pull requests destinados à `main`;
- execução manual por meio de `workflow_dispatch`.

Os jobs são associados com a propriedade `needs`. Dessa forma, cada etapa só começa quando sua dependência termina com sucesso:

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

### 1. Build

Instala as dependências com `npm ci`, gera a aplicação e verifica se os arquivos esperados foram criados na pasta `dist`.

### 2. Test

Executa os testes automatizados do projeto por meio do comando `npm test`.

### 3. Quality

Executa `npm run lint` para analisar a qualidade e a padronização do código.

### 4. Security

Utiliza `npm audit --audit-level=high` para interromper a pipeline caso sejam encontradas vulnerabilidades de nível alto ou crítico nas dependências.

### 5. Package

Gera novamente o build de produção e confere os arquivos que serão utilizados na publicação.

### 6. Deploy

Publica a pasta `dist` na branch `gh-pages` com `peaceiris/actions-gh-pages`. Essa etapa ocorre somente em eventos de `push` na branch `main`, evitando o deploy de alterações que ainda estejam apenas em pull requests.

### 7. Smoke Test

Inicia a aplicação em um servidor local temporário e utiliza `curl` para verificar se a página responde corretamente.

### 8. Performance

Calcula o tamanho total da pasta `dist` e confirma que o site permanece abaixo do limite de 1 MB definido no workflow.

### 9. Monitoring

Confirma que a branch `gh-pages` está disponível no repositório, indicando que a publicação foi realizada, e finaliza o fluxo com uma mensagem de sucesso.

## 🧪 Execução local

As principais verificações da pipeline também podem ser reproduzidas localmente:

```bash
npm ci
npm run lint
npm test
npm run build
```

Essa possibilidade facilita a identificação de problemas antes de enviar alterações ao repositório remoto.

## ✅ Resultado

A atividade resultou em uma pipeline completa e organizada em etapas independentes. A automação prepara o ambiente, instala dependências, gera o build, executa testes, avalia a qualidade e a segurança, prepara os arquivos, realiza o deploy e verifica a publicação.

As três Actions selecionadas desempenham funções complementares: o checkout fornece o código, o setup-node prepara o ambiente e a Action do GitHub Pages publica o resultado. O encadeamento dos jobs impede que uma versão com falha avance até o deploy, aumentando a confiabilidade do processo.

Além da publicação automatizada na branch `gh-pages`, a aplicação também está disponível na Vercel pelo endereço fornecido para a atividade.

## 🔗 Recursos

- [Aplicação publicada na Vercel](https://pipelinedevops.vercel.app/)
- [Repositório Pipeline-Devops](https://github.com/Isadora-Correa/Pipeline-Devops)
- [Workflow da pipeline](https://github.com/Isadora-Correa/Pipeline-Devops/blob/main/.github/workflows/pipeline.yml)
- [Material da Aula 05](<../Conteúdo/Aula 05 - Pipeline de Integração Contínua.pdf>)

## 🧭 Navegação

[← Tarefa 04](../../Aula04/Tarefa04/Atividade04.md) · [README principal](../../README.md) · [Tarefa 06 →](../../Aula06/Tarefa06/Atividade06.md)
