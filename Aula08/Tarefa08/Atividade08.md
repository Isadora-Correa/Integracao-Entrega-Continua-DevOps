# Tarefa 08 — Apresentação de ferramenta DevOps: Kubernetes

> **Aula:** 08
>
> **Formato:** apresentação em grupo, de 15 a 20 minutos
>
> **Status:** ✅ Concluída

[← Voltar ao README principal](../../README.md)

## 🎯 Objetivo

Apresentar e demonstrar uma ferramenta do ecossistema DevOps, destacando sua finalidade, seu funcionamento, sua aplicação e seus benefícios, de forma que a turma compreenda quando e como utilizá-la.

## 📋 Proposta da atividade

A apresentação deveria responder às seguintes perguntas:

1. O que é a ferramenta?
2. Qual problema ela resolve?
3. Em qual etapa do DevOps ela pode ser utilizada?
4. Como funciona?
5. Como utilizá-la na prática?
6. Quais são suas vantagens e limitações?
7. Como ela pode ser integrada a um projeto?

O roteiro sugerido pelo professor incluía introdução, problema, funcionamento, aplicação no DevOps, demonstração prática, integração, vantagens e limitações e conclusão.

## 💻 Ferramenta escolhida

O grupo escolheu o **Kubernetes (K8s)**, plataforma open-source de orquestração de contêineres criada pelo Google e mantida hoje pela CNCF (Cloud Native Computing Foundation). O nome vem do grego e significa "timoneiro".

O Kubernetes automatiza a implantação, o escalonamento e a operação de aplicações em contêineres, como os criados com Docker, administrando-os em um cluster de máquinas.

Os slides da apresentação estão em [Kubernetes_DevOps.pdf](Kubernetes_DevOps.pdf).

## 🧩 Conteúdo apresentado

### Problema resolvido

Quando uma aplicação usa dezenas ou centenas de contêineres, o gerenciamento manual se torna inviável. O Kubernetes trata quatro dificuldades principais:

| Dificuldade sem o Kubernetes | Solução com o Kubernetes |
| --- | --- |
| Escalonamento manual, que não acompanha picos de acesso | Escalonamento automático |
| Falhas não tratadas quando um contêiner trava | Autorrecuperação (*self-healing*) |
| Distribuição manual do tráfego entre réplicas | Balanceamento de carga |
| Atualizações arriscadas, com indisponibilidade | Atualizações graduais (*rolling updates*) |

### Etapa do DevOps

O Kubernetes atua na segunda metade do ciclo DevOps, quando o software já foi construído:

```text
Planejar → Codificar → Construir → Testar → Liberar → [ Implantar → Operar → Monitorar ]
```

- **Implantação:** recebe a imagem de contêiner gerada na integração contínua e a publica com `kubectl apply`.
- **Operação:** reinicia contêineres com falha, ajusta a escala e gerencia versões.
- **Monitoramento:** expõe métricas de saúde dos serviços para ferramentas de observabilidade.

### Funcionamento

Um cluster Kubernetes é dividido em duas partes:

| Parte | Componente | Função |
| --- | --- | --- |
| Control Plane | API Server | Porta de entrada de todos os comandos, como os do `kubectl` |
| Control Plane | etcd | Armazena o estado do cluster |
| Control Plane | Scheduler | Decide em qual nó cada novo Pod será executado |
| Control Plane | Controller Manager | Compara o estado atual com o desejado e corrige as diferenças |
| Worker Node | kubelet | Garante que os contêineres do nó estejam em execução |
| Worker Node | kube-proxy | Faz o roteamento de rede entre Pods e serviços |
| Worker Node | Container Runtime | Executa os contêineres, como o containerd |
| Worker Node | Pod | Menor unidade implantável, com um ou mais contêineres |

### Integração a um projeto

1. **Conteinerizar:** empacotar a aplicação com Docker e um `Dockerfile`.
2. **Criar manifestos:** escrever arquivos YAML de *Deployment* e *Service*, ou um *Helm chart*.
3. **Integrar ao CI/CD:** a pipeline (GitHub Actions ou GitLab CI) gera a imagem e executa `kubectl apply`.
4. **Publicar na nuvem:** implantar em um cluster gerenciado, como EKS, GKE ou AKS.
5. **Monitorar:** acompanhar com Prometheus e Grafana e ajustar os recursos.

### Demonstração prática

O slide 10 da apresentação foi reservado para a parte prática. Os passos da demonstração não estão registrados no material.

## ⚖️ Comparação e análise

| Aspecto | Análise |
| --- | --- |
| Facilidade de uso | Curva de aprendizado alta, com muitos conceitos novos (Pods, Services, ConfigMaps, RBAC) |
| Integração | Docker, Helm, Prometheus, Grafana, GitHub Actions, GitLab CI e clusters gerenciados (EKS, GKE e AKS) |
| Automação | Implantação, escalonamento, recuperação de falhas, balanceamento de carga e atualizações |
| Custo | Open-source; o próprio cluster consome CPU e memória para se gerenciar |
| Escalabilidade | Ajusta o número de réplicas conforme a demanda e funciona em qualquer nuvem ou servidor próprio |
| Limitações | Configuração complexa, YAMLs extensos e excesso de estrutura para aplicações simples ou equipes pequenas |

## ✅ Conclusão

O Kubernetes transforma um conjunto de contêineres isolados em um sistema que se escala, se recupera e se atualiza automaticamente, e por isso se tornou o padrão de mercado para operar aplicações em produção. Ele se integra ao DevOps principalmente nas etapas de implantação, operação e monitoramento. Apesar da complexidade, traz benefícios importantes para projetos que precisam de escala e alta disponibilidade.

## 👥 Integrantes

- Isadora Correa
- Maria Júlia Loureiro
- Rafaela Riganti
- Ronaldo Junior
- Sophia Marcelino

## 🔗 Referências

- [Material da Aula 08](<../Conteúdo/Aula 08 - Apresentação Ferramentas Devops.pdf>)
- [Slides da apresentação](Kubernetes_DevOps.pdf)
- ARUNDEL, J.; DOMINGUS, J. *DevOps nativo de nuvem com Kubernetes*. São Paulo: Novatec, 2019.
