# Tarefa 04 — Ferramentas de integração e entrega contínua

> **Aula:** 04
>
> **Prazo:** 5 de setembro de 2026, às 23h59
>
> **Status:** ✅ Concluída

[← Voltar ao README principal](../../README.md)

## 🎯 Objetivo

Analisar e comparar ferramentas utilizadas em processos de **Integração Contínua (CI)** e **Entrega ou Implantação Contínua (CD)**, identificando suas características, funcionalidades, vantagens, limitações e os cenários em que cada solução é mais adequada.

A análise foi baseada no artigo *Practical Comparison Between the CI/CD Platforms Azure DevOps and GitHub*, de Vladislav Manolov, Daniela Gotseva e Nikolay Hinov, publicado em 2025 na revista *Future Internet*.

## 📋 Proposta da atividade

1. Ler o artigo indicado pelo professor.
2. Identificar as ferramentas e plataformas citadas pelos autores.
3. Analisar suas principais características e funcionalidades.
4. Comparar vantagens, limitações e diferenças relevantes.
5. Indicar os cenários em que cada ferramenta pode ser mais adequada.
6. Relacionar as soluções às práticas de integração e entrega contínua.

## 📖 Conceitos fundamentais

A **Integração Contínua (CI)** consiste em integrar alterações ao repositório compartilhado com frequência. A cada mudança, processos automatizados podem compilar o projeto e executar testes, permitindo identificar falhas rapidamente e manter o código em condições de ser entregue.

A **Entrega Contínua (Continuous Delivery)** amplia esse processo ao manter uma versão validada e pronta para publicação. A implantação em produção ainda pode depender de aprovação manual.

Já a **Implantação Contínua (Continuous Deployment)** automatiza também a liberação em produção: toda alteração que passa pelas verificações definidas no pipeline pode ser publicada sem intervenção manual.

Essas práticas reduzem tarefas repetitivas, antecipam a descoberta de erros, aumentam a rastreabilidade e tornam as entregas mais frequentes e previsíveis.

## 🔎 Ferramentas identificadas no artigo

O estudo concentra sua análise em **Azure DevOps** e **GitHub**, mas apresenta outras soluções que compõem o mercado de CI/CD.

### Plataformas e serviços de CI/CD

| Ferramenta | Característica principal |
| --- | --- |
| Azure DevOps | Suíte corporativa que reúne versionamento, pipelines, gestão de projetos, testes e artefatos |
| GitHub e GitHub Actions | Hospedagem Git e automação de workflows diretamente no repositório |
| Jenkins | Servidor de automação de código aberto, extensível por plugins |
| GitLab CI/CD | CI/CD integrado ao repositório e à plataforma GitLab |
| Bitbucket | Plataforma Git da Atlassian com automação por Bitbucket Pipelines |
| AWS CodePipeline | Serviço gerenciado de entrega contínua integrado à nuvem AWS |
| TeamCity | Servidor de CI/CD da JetBrains voltado a configurações avançadas de build |
| Travis CI | Serviço de CI conhecido pela configuração simples e pelo uso em projetos de código aberto |
| CircleCI | Plataforma de CI/CD em nuvem com foco em velocidade, paralelismo e otimização de builds |

### Serviços do Azure DevOps

O Azure DevOps é formado por serviços que podem ser utilizados em conjunto ou separadamente:

- **Azure Pipelines:** automação de build, testes e deploy;
- **Azure Repos:** hospedagem de repositórios Git e suporte ao TFVC;
- **Azure Boards:** gestão de tarefas, requisitos e acompanhamento do projeto;
- **Azure Test Plans:** planejamento, execução e rastreabilidade de testes;
- **Azure Artifacts:** armazenamento e distribuição de pacotes;
- **Azure DevOps Server:** alternativa instalada na infraestrutura da própria organização.

### Ferramentas e tecnologias complementares

Os autores também mencionam soluções que podem fazer parte do ecossistema de um pipeline, embora não sejam, isoladamente, plataformas completas de CI/CD:

- **Git e TFVC:** sistemas de controle de versão;
- **Docker:** criação e execução de aplicações em contêineres;
- **Kubernetes e Azure Kubernetes Service (AKS):** orquestração de contêineres;
- **Terraform:** infraestrutura como código;
- **Azure App Service, Azure Functions e máquinas virtuais:** ambientes de implantação;
- **Microsoft Azure, Amazon Web Services (AWS) e Google Cloud:** provedores de nuvem;
- **Microsoft Entra ID (Azure Active Directory), Azure Policy e Microsoft Defender for DevOps:** identidade, políticas e segurança no ecossistema Microsoft;
- **GitHub Advanced Security e Dependabot:** análise de código, segredos e dependências vulneráveis;
- **HashiCorp Vault:** gerenciamento de segredos;
- **Prometheus:** monitoramento;
- **Visual Studio, Microsoft Teams, Power BI, Jira, Confluence e ServiceNow:** desenvolvimento, colaboração, gestão e integração com processos organizacionais;
- **GitHub Copilot:** assistência ao desenvolvimento baseada em inteligência artificial.

## ⚖️ Comparação principal: Azure DevOps e GitHub

Embora pertençam à Microsoft e ofereçam recursos semelhantes, as duas plataformas seguem propostas diferentes. O Azure DevOps adota uma abordagem corporativa e estruturada para todo o ciclo de desenvolvimento. O GitHub parte do repositório Git e oferece uma experiência mais colaborativa, modular e próxima do fluxo diário dos desenvolvedores.

| Critério | Azure DevOps | GitHub |
| --- | --- | --- |
| Foco | Gestão completa do ciclo de desenvolvimento | Colaboração em código e automação baseada em Git |
| CI/CD | Azure Pipelines | GitHub Actions |
| Versionamento | Git e TFVC | Exclusivamente Git |
| Configuração | Pipelines visuais ou em YAML | Workflows em YAML dentro de `.github/workflows` |
| Gestão de projetos | Azure Boards, com processos estruturados | Issues, Projects e pull requests, com fluxo mais simples |
| Testes | Azure Test Plans e integração direta com pipelines | GitHub Actions e ferramentas externas |
| Artefatos | Azure Artifacts | GitHub Packages e artefatos dos workflows |
| Segurança | RBAC, políticas, integração de identidade e controles centralizados | Advanced Security, Dependabot, análise de código e segredos |
| Integrações | Forte integração com Azure e produtos Microsoft | Marketplace amplo, APIs, webhooks e integrações variadas |
| Infraestrutura | Nuvem, ambiente híbrido ou servidor próprio | GitHub Cloud ou GitHub Enterprise Server |
| Facilidade de adoção | Maior curva de aprendizado | Interface mais simples para quem já utiliza GitHub |
| Público mais adequado | Grandes empresas e ambientes regulados | Código aberto, startups e equipes ágeis |

### Azure DevOps

O **Azure DevOps** oferece uma solução integrada para planejar o trabalho, armazenar código, executar testes, criar artefatos e automatizar entregas. O Azure Pipelines aceita pipelines com múltiplas etapas, execuções paralelas e agentes hospedados pela Microsoft ou mantidos pela própria organização.

#### Vantagens

- reúne diferentes etapas do ciclo de desenvolvimento em uma única suíte;
- oferece controle detalhado de permissões, aprovações e ambientes;
- integra-se profundamente ao Azure e ao ecossistema Microsoft;
- suporta Git e o sistema centralizado TFVC;
- atende pipelines complexos, aplicações monolíticas e arquiteturas com vários repositórios;
- disponibiliza opção em nuvem e instalação local com Azure DevOps Server;
- favorece auditoria, governança e conformidade em organizações reguladas.

#### Limitações

- possui interface mais complexa e maior curva de aprendizado;
- pode exigir mais tempo de configuração e administração;
- sua maior vantagem aparece em ambientes Microsoft, embora aceite outras nuvens;
- os custos podem crescer conforme aumentam usuários, execuções paralelas, testes e armazenamento;
- pode ser uma solução mais extensa do que o necessário para projetos pequenos.

#### Situações mais adequadas

É indicado para grandes empresas, órgãos governamentais, instituições financeiras, organizações de saúde e outros ambientes que exigem processos formais, auditoria, aprovações, controle de acesso e integração com infraestrutura híbrida ou legada.

### GitHub e GitHub Actions

O **GitHub** é uma plataforma centrada em repositórios Git e colaboração. Sua solução de CI/CD, o **GitHub Actions**, executa workflows acionados por eventos como commits, pull requests, criação de versões ou ações manuais. Os arquivos YAML permanecem no próprio repositório, próximos ao código que automatizam.

#### Vantagens

- oferece experiência conhecida e acessível para usuários de Git;
- integra versionamento, revisão de código, issues e automação;
- facilita a criação de workflows orientados a eventos;
- possui amplo Marketplace de ações e integrações reutilizáveis;
- funciona bem para projetos de código aberto e equipes distribuídas;
- permite runners hospedados pelo GitHub ou pela própria organização;
- favorece entregas rápidas e fluxos ágeis de desenvolvimento.

#### Limitações

- utiliza apenas Git e não atende equipes dependentes de TFVC;
- testes e gestão corporativa avançada podem depender de integrações ou produtos adicionais;
- recursos de segurança e governança mais avançados exigem planos superiores;
- workflows extensos podem se tornar difíceis de manter;
- projetos empresariais muito grandes podem exigir maior planejamento de runners, custos e limites de execução.

#### Situações mais adequadas

É recomendado para projetos de código aberto, desenvolvedores independentes, startups e equipes pequenas ou médias que já hospedam o código no GitHub e desejam automação simples, modular e integrada aos pull requests.

## 🧰 Comparação das demais plataformas de CI/CD

| Ferramenta | Vantagens | Limitações | Cenário mais adequado |
| --- | --- | --- | --- |
| Jenkins | Código aberto, altamente personalizável e com grande quantidade de plugins | Exige instalação, atualizações, segurança e manutenção da infraestrutura | Organizações com equipe técnica especializada e necessidade de controle ou integrações personalizadas |
| GitLab CI/CD | Repositório, CI/CD, segurança e gestão reunidos em uma plataforma | Administração da edição própria pode ser complexa e a adoção pode exigir migração para o ecossistema GitLab | Equipes que procuram uma experiência DevOps integrada em SaaS ou instalação própria |
| Bitbucket | Integração natural com Jira e Confluence e configuração de pipelines junto ao código | Ecossistema e comunidade menores do que os do GitHub; maior benefício dentro do conjunto Atlassian | Equipes pequenas ou médias que já utilizam produtos Atlassian |
| AWS CodePipeline | Serviço gerenciado, escalável e integrado a serviços da AWS | Pode gerar dependência do provedor e ser menos conveniente em ambientes fora da AWS | Aplicações cuja infraestrutura e implantação estão concentradas na AWS |
| TeamCity | Interface madura, configurações poderosas de build e suporte a diferentes ambientes | Licenciamento e manutenção podem elevar custos e esforço operacional | Empresas com builds complexos que valorizam controle e suporte comercial |
| Travis CI | Configuração relativamente simples e histórico de adoção em código aberto | Menor abrangência como plataforma DevOps e menos controle empresarial do que suítes completas | Projetos menores que necessitam de CI direta e sem uma plataforma extensa |
| CircleCI | Paralelismo, cache e otimização de desempenho dos pipelines | Custos e dependência do serviço podem crescer com o volume de execução | Equipes que priorizam rapidez de feedback e builds em nuvem otimizados |

## 📊 Principais diferenças observadas

### Integração e automação

O Azure Pipelines oferece maior controle sobre dependências, aprovações, ambientes e pipelines com várias etapas. O GitHub Actions utiliza uma abordagem orientada a eventos e integrada ao repositório, o que simplifica automações menores e favorece a reutilização de ações da comunidade.

Jenkins apresenta o maior grau de personalização, mas transfere para a organização a responsabilidade pela infraestrutura. Serviços como AWS CodePipeline, Travis CI e CircleCI reduzem esse trabalho operacional por serem gerenciados, porém criam maior dependência de seus respectivos serviços e modelos de cobrança.

### Escalabilidade e desempenho

O Azure DevOps se destaca em projetos empresariais de grande porte, pipelines com múltiplas etapas, ambientes híbridos e equipes distribuídas. O GitHub Actions atende bem equipes pequenas e médias, especialmente quando todo o fluxo já ocorre no GitHub.

Jenkins e GitLab instalados localmente podem ser dimensionados conforme a infraestrutura disponível, mas exigem administração. As soluções em nuvem simplificam a expansão, embora imponham limites de execução, armazenamento ou concorrência de acordo com o plano contratado.

### Segurança e conformidade

O Azure DevOps prioriza governança centralizada, controle de acesso baseado em função, integração com identidade corporativa e políticas de implantação. Essas características favorecem ambientes sujeitos a auditorias e normas regulatórias.

O GitHub integra a segurança ao fluxo do desenvolvedor por meio de análise de código, detecção de segredos e alertas de dependências. Essa abordagem facilita a correção durante pull requests, mas alguns recursos avançados dependem do GitHub Advanced Security e de planos empresariais.

Em qualquer plataforma, a segurança final depende também de boas práticas: proteger credenciais, limitar permissões, revisar dependências, manter runners e plugins atualizados e separar os ambientes de desenvolvimento, teste e produção.

### Custos

Não existe uma ferramenta universalmente mais barata. O custo depende do número de usuários, minutos de execução, paralelismo, armazenamento, agentes, runners e recursos empresariais contratados.

GitHub, GitLab e algumas soluções gerenciadas oferecem planos iniciais acessíveis, especialmente para projetos públicos ou equipes menores. O Azure DevOps pode oferecer melhor relação entre custo e controle para empresas que utilizam seus serviços de maneira integrada. Jenkins não exige licença para o software, mas demanda infraestrutura e profissionais para operação e manutenção.

### Experiência de uso

O GitHub possui adoção mais direta para equipes familiarizadas com repositórios Git, pull requests e desenvolvimento colaborativo. O Azure DevOps apresenta mais recursos em uma única interface, mas requer maior aprendizado. Bitbucket é especialmente conveniente para usuários de Jira e Confluence, enquanto GitLab busca oferecer todo o ciclo DevOps em uma experiência unificada.

## ✅ Resultado da análise

A comparação demonstra que **não existe uma única plataforma ideal para todos os projetos**. A escolha deve considerar o tamanho da equipe, a complexidade dos pipelines, os requisitos de segurança, o ambiente de implantação, as integrações existentes, o orçamento e a capacidade de administrar infraestrutura.

O **Azure DevOps** é mais adequado quando a organização necessita de uma suíte completa, processos estruturados, governança centralizada, integração com produtos Microsoft e suporte a ambientes híbridos. O **GitHub** é mais indicado quando a prioridade é colaboração, simplicidade, desenvolvimento baseado em Git, projetos de código aberto e automações próximas ao repositório.

Entre as alternativas, **Jenkins** oferece maior liberdade de personalização; **GitLab CI/CD** se destaca pela plataforma integrada; **Bitbucket** combina bem com o ecossistema Atlassian; **AWS CodePipeline** favorece projetos hospedados na AWS; **TeamCity** atende builds empresariais complexos; e **Travis CI** e **CircleCI** são opções práticas para automação gerenciada em projetos que valorizam configuração rápida e retorno ágil.

Uma organização também pode combinar ferramentas. Por exemplo, é possível manter o código no GitHub, executar determinadas automações no GitHub Actions e utilizar serviços de nuvem, segurança, monitoramento e infraestrutura como código nas demais etapas. Mais importante do que escolher a ferramenta mais popular é selecionar um conjunto coerente com as necessidades técnicas e organizacionais do projeto.

## 🔗 Recursos

- [Artigo na MDPI](https://www.mdpi.com/1999-5903/17/4/153)
- [Material da Aula 04](<../Conteúdo/Aula 04 - Ferramentas de Integração e Entrega Contínua.pdf>)
- [Artigo disponível no repositório](../Referência/futureinternet-17-00153.pdf)

## 📚 Referência

MANOLOV, Vladislav; GOTSEVA, Daniela; HINOV, Nikolay. Practical Comparison Between the CI/CD Platforms Azure DevOps and GitHub. *Future Internet*, v. 17, n. 4, art. 153, 2025. DOI: [10.3390/fi17040153](https://doi.org/10.3390/fi17040153).

## 🧭 Navegação

[← Tarefa 03](../../Aula03/Tarefa03/Atividade03.md) · [README principal](../../README.md) · [Tarefa 05 →](../../Aula05/Tarefa05/Atividade05.md)
