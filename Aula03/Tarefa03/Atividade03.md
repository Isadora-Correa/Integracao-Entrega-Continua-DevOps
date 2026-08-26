# Tarefa 03 — Gerência de Configuração e Deploy

**Aula 03**
**Prazo:** 29 de agosto de 2026 às 23:59
**Status:** ✅ Concluída

[← Voltar ao repositório principal](../../README.md)

---

## Objetivo

A terceira atividade teve como objetivo aplicar na prática conceitos relacionados ao gerenciamento de configuração, controle de versão e publicação de uma aplicação web.

Para isso, foi utilizado um projeto desenvolvido em React, que posteriormente foi preparado para execução local, versionado utilizando Git, armazenado no GitHub e publicado utilizando a Vercel.

A proposta não era desenvolver uma nova aplicação do zero, mas compreender o processo necessário para obter um projeto existente e conduzi-lo até sua disponibilização em um ambiente público.

---

## Proposta da atividade

Foram solicitadas as seguintes etapas:

1. pesquisar um template ou projeto desenvolvido em React;
2. importar o projeto;
3. realizar alterações;
4. armazenar o projeto em um repositório no GitHub;
5. documentar todas as etapas realizadas;
6. registrar o desenvolvimento utilizando imagens e prints;
7. disponibilizar o link do repositório;
8. publicar a aplicação utilizando a Vercel;
9. disponibilizar o link da aplicação publicada.

---

## Projeto escolhido

Para realização da atividade foi utilizada uma landing page inspirada na apresentação do MacBook.

O projeto foi desenvolvido utilizando React e outras bibliotecas modernas para construção da interface, estilização, gerenciamento de estados, animações e renderização de elementos tridimensionais.

---

## Tecnologias utilizadas

### React

Biblioteca utilizada para construção da interface utilizando componentes.

### Vite

Ferramenta utilizada como ambiente de desenvolvimento e para geração do build da aplicação.

### JavaScript

Principal linguagem de programação utilizada pelo projeto.

### Tailwind CSS

Utilizado para auxiliar na estilização dos componentes.

### GSAP

Biblioteca utilizada para criação e controle das animações presentes na aplicação.

### Three.js e React Three Fiber

Utilizados para renderização e manipulação dos elementos tridimensionais presentes no projeto.

### Zustand

Utilizado para gerenciamento dos estados da aplicação.

### Git

Utilizado para controle de versão local.

### GitHub

Utilizado como repositório remoto para armazenamento do código-fonte.

### Vercel

Utilizada para realização do build e publicação da aplicação na internet.

---

## Estrutura do projeto

Após obter os arquivos, foi realizada uma análise da estrutura da aplicação.

Entre os principais diretórios e arquivos encontrados estavam:

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

### `src/`

Contém o código-fonte principal da aplicação React.

### `src/components/`

Contém os componentes utilizados para construção da interface.

### `src/constants/`

Concentra dados e constantes utilizados em diferentes partes da aplicação.

### `src/store/`

Contém configurações relacionadas ao gerenciamento de estados.

### `public/`

Armazena arquivos estáticos utilizados pelo projeto, como imagens, vídeos e modelos tridimensionais.

### `package.json`

Contém informações sobre o projeto, suas dependências e os scripts disponíveis.

### `vite.config.js`

Contém configurações específicas do Vite.

---

## Execução local

Antes de realizar qualquer processo de publicação, a aplicação foi testada localmente.

### Instalação das dependências

Inicialmente foi necessário instalar as dependências definidas no projeto.

```bash
npm install
```

O npm utiliza as informações existentes no arquivo `package.json` para identificar e instalar os pacotes necessários para a execução da aplicação.

---

### Inicialização do servidor

Após a instalação das dependências, o servidor de desenvolvimento foi iniciado utilizando:

```bash
npm run dev
```

O Vite disponibilizou então um endereço local para acesso à aplicação pelo navegador.

A execução local permitiu verificar o funcionamento de:

* componentes;
* imagens;
* animações;
* estilos;
* elementos tridimensionais;
* comportamento geral da aplicação.

---

### Validação do build

Antes da publicação também foi realizada a geração da versão de produção:

```bash
npm run build
```

Essa etapa permitiu verificar se o projeto poderia ser compilado corretamente para produção antes de realizar o deploy.

---

## Versionamento com Git

Após a validação do funcionamento da aplicação, o projeto foi preparado para versionamento.

Os arquivos foram adicionados à área de preparação utilizando:

```bash
git add .
```

Em seguida foi criado o commit correspondente à versão utilizada na atividade:

```bash
git commit -m "0.0.1"
```

Depois da criação do commit, as alterações foram enviadas para o repositório remoto:

```bash
git push origin main
```

---

## Repositório Git interno

Durante o processo de versionamento foi identificado que o projeto importado possuía um diretório `.git` próprio.

Isso significava que o projeto mantinha informações relacionadas ao repositório original de onde havia sido obtido.

Como o objetivo da atividade era controlar os arquivos diretamente pelo novo repositório utilizado pelo grupo, foi necessário remover esse vínculo Git interno.

Essa situação também permitiu compreender melhor o papel do diretório `.git`, responsável por armazenar informações relacionadas ao repositório e ao seu histórico.

---

## GitHub

Após o processo de versionamento local, o código foi armazenado em um repositório próprio no GitHub.

O GitHub passou a cumprir duas funções principais durante a atividade:

1. armazenar remotamente o código-fonte e seu histórico de versões;
2. servir como origem do código utilizado posteriormente pela Vercel.

### Repositório do projeto

**GitHub:**
https://github.com/Isadora-Correa/copia-versionamento

[Acessar repositório no GitHub](https://github.com/Isadora-Correa/copia-versionamento)

---

## Publicação na Vercel

Com o projeto funcionando localmente e armazenado no GitHub, foi realizada sua publicação utilizando a Vercel.

O repositório foi conectado diretamente à plataforma.

A partir dessa integração, a Vercel realizou automaticamente etapas como:

```text
Obtenção do código
        ↓
Instalação das dependências
        ↓
       Build
        ↓
      Deploy
        ↓
Aplicação publicada
```

No ambiente local essas etapas precisaram ser executadas manualmente.

Na Vercel, grande parte desse processo foi automatizada.

### Aplicação publicada

**Vercel:**
https://fatec-devops.vercel.app/

[Acessar aplicação publicada](https://fatec-devops.vercel.app/)

---

## Integração entre GitHub e Vercel

Depois da conexão entre as plataformas, o GitHub passou a funcionar como origem do código utilizado pela Vercel.

Assim, novas versões armazenadas no repositório podem ser utilizadas pela plataforma para gerar novos deployments da aplicação.

O fluxo utilizado durante a atividade pode ser representado por:

```text
Projeto local
      ↓
     Git
      ↓
   GitHub
      ↓
   Vercel
      ↓
Aplicação publicada
```

Essa integração demonstra, de maneira simplificada, um fluxo comum utilizado no gerenciamento e entrega de aplicações web modernas.

---

## Resultado

Ao final da atividade foi possível realizar todo o fluxo necessário para obter uma aplicação existente e disponibilizá-la na internet.

Foram realizadas as seguintes etapas:

* obtenção do projeto;
* análise de sua estrutura;
* instalação das dependências;
* execução local;
* validação do build;
* controle de versão utilizando Git;
* publicação do código no GitHub;
* integração entre GitHub e Vercel;
* deploy da aplicação.

---

## Resultado final

| Recurso                   | Link                                                                                                   |
| ------------------------- | ------------------------------------------------------------------------------------------------------ |
| **Código-fonte — GitHub** | [github.com/Isadora-Correa/copia-versionamento](https://github.com/Isadora-Correa/copia-versionamento) |
| **Aplicação — Vercel**    | [fatec-devops.vercel.app](https://fatec-devops.vercel.app/)                                            |

---

## Navegação

[← Tarefa 02](../../Aula02/Tarefa02/Atividade02.md)

[Voltar ao README principal](../../README.md)

[Próxima atividade → Tarefa 04](../../Aula04/Tarefa04/Atividade04.md)
