# Tarefa 03 — Gerência de configuração e deploy

> **Aula:** 03
>
> **Prazo:** 29 de agosto de 2026, às 23h59
>
> **Status:** ✅ Concluída

[← Voltar ao README principal](../../README.md)

## 🎯 Objetivo

Aplicar conceitos de gerenciamento de configuração, controle de versão e publicação de uma aplicação web.

Foi utilizado um projeto desenvolvido em React, preparado para execução local, versionado com Git, armazenado no GitHub e publicado na Vercel. A proposta não era desenvolver uma nova aplicação do zero, mas compreender o processo necessário para obter um projeto existente e conduzi-lo até sua disponibilização em um ambiente público.

## 📋 Proposta da atividade

1. Pesquisar um template ou projeto desenvolvido em React.
2. Importar o projeto e realizar alterações.
3. Armazenar o código em um repositório no GitHub.
4. Documentar todas as etapas realizadas com imagens e capturas de tela.
5. Disponibilizar o link do repositório.
6. Publicar a aplicação na Vercel.
7. Disponibilizar o link da aplicação publicada.

## 💻 Projeto escolhido

Foi utilizada uma landing page inspirada na apresentação do MacBook. O projeto emprega React e bibliotecas modernas para construir a interface, aplicar estilos, gerenciar estados, criar animações e renderizar elementos tridimensionais.

## 🧰 Tecnologias utilizadas

| Tecnologia | Utilização no projeto |
| --- | --- |
| React | Construção da interface com componentes |
| Vite | Ambiente de desenvolvimento e geração do build |
| JavaScript | Linguagem principal da aplicação |
| Tailwind CSS | Estilização dos componentes |
| GSAP | Criação e controle de animações |
| Three.js e React Three Fiber | Renderização e manipulação de elementos 3D |
| Zustand | Gerenciamento dos estados da aplicação |
| Git e GitHub | Versionamento local e armazenamento remoto |
| Vercel | Build e publicação da aplicação |

## 🗂️ Estrutura do projeto

```text
Macbook-Landing-Page/
├── public/
├── src/
│   ├── components/
│   ├── constants/
│   └── store/
├── index.html
├── package.json
└── vite.config.js
```

- `public/`: arquivos estáticos, como imagens, vídeos e modelos tridimensionais;
- `src/`: código-fonte principal da aplicação React;
- `src/components/`: componentes utilizados na interface;
- `src/constants/`: dados e constantes compartilhados;
- `src/store/`: configurações de gerenciamento de estado;
- `package.json`: dependências, scripts e informações do projeto;
- `vite.config.js`: configurações específicas do Vite.

## 🛠️ Desenvolvimento

### Execução local

Primeiro, as dependências definidas no `package.json` foram instaladas:

```bash
npm install
```

Em seguida, o servidor de desenvolvimento foi iniciado:

```bash
npm run dev
```

A execução local permitiu validar componentes, imagens, animações, estilos, elementos tridimensionais e o comportamento geral da aplicação.

Antes da publicação, também foi gerada uma versão de produção para confirmar que o projeto poderia ser compilado corretamente:

```bash
npm run build
```

### Versionamento com Git

Após a validação, os arquivos foram preparados e registrados no histórico do projeto:

```bash
git add .
git commit -m "0.0.1"
git push origin main
```

Durante esse processo, foi identificado que o projeto importado possuía um diretório `.git` próprio, com informações do repositório original. Como os arquivos seriam controlados diretamente pelo novo repositório do grupo, esse vínculo interno foi removido.

A situação ajudou a compreender o papel do diretório `.git`, responsável por armazenar os metadados e o histórico do repositório.

### Publicação na Vercel

Com a aplicação funcionando localmente e armazenada no GitHub, o repositório foi conectado à Vercel. A plataforma automatizou o fluxo de publicação:

```text
Obtenção do código → Instalação das dependências → Build → Deploy
```

## ✅ Resultado

A atividade demonstrou o ciclo completo de preparação e publicação de um projeto existente: análise da estrutura, instalação de dependências, execução local, validação do build, versionamento, armazenamento remoto e deploy automatizado.

## 🔗 Recursos

- [Repositório do projeto no GitHub](https://github.com/Isadora-Correa/copia-versionamento)

## 🧭 Navegação

[← Tarefa 02](../../Aula02/Tarefa02/Atividade02.md) · [README principal](../../README.md) · [Tarefa 04 →](../../Aula04/Tarefa04/Atividade04.md)
