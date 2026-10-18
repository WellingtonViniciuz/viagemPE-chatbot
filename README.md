# Guia de Desenvolvimento e Integração: Projeto Chatbot

Este documento estabelece as diretrizes de metodologia, integração da equipe e boas práticas de controle de versão (Git) para o desenvolvimento do nosso Chatbot. O objetivo é garantir um código limpo, entregas contínuas e alinhamento entre todos os membros da equipe.

---

## 1. Metodologia de Desenvolvimento

Adotaremos uma abordagem **Ágil** (baseada em Scrum/Kanban) para garantir flexibilidade e entregas incrementais do fluxo conversacional e integrações.

*   **Ciclos de Desenvolvimento (Sprints):** Trabalharemos em ciclos curtos (ex: 1 a 2 semanas). Cada ciclo terá um objetivo claro (ex: "Finalizar fluxo de boas-vindas", "Integrar com API de pagamentos").
*   **Gestão de Tarefas:** Utilizaremos um quadro Kanban (ex: Trello, Jira, GitHub Projects) com as colunas: `Backlog`, `To Do`, `In Progress`, `Code Review`, `Testing` e `Done`.
*   **Alinhamento Diário (Daily):** Reuniões rápidas (15 min) para sincronização da equipe:
    *   O que fiz ontem?
    *   O que vou fazer hoje?
    *   Existe algum bloqueio?
*   **Testes de Fluxo:** Por se tratar de um chatbot, as tarefas de desenvolvimento devem incluir testes de intenções (NLP) e caminhos de conversação antes de serem movidas para *Code Review*.

---

## 2. Integração da Equipe e Controle de Versão (Git)

Nosso fluxo de trabalho será baseado no **Gitflow simplificado**. Ninguém deve commitar diretamente nas branches de produção.

### 2.1. Estrutura de Branches Principais
*   `main` (ou `master`): Código em produção. Altamente instável, deve conter apenas código testado e aprovado.
*   `develop`: Branch de integração. Recebe as novas funcionalidades testadas antes do lançamento oficial.

### 2.2. Criando Novas Branches
Toda nova tarefa deve ter sua própria branch, criada a partir da `develop`. Utilize o seguinte padrão de nomenclatura:

*   **Funcionalidades (Novos fluxos, integrações):** `feature/nome-da-tarefa` (ex: `feature/integracao-whatsapp`)
*   **Correção de Bugs:** `bugfix/nome-do-bug` (ex: `bugfix/loop-infinito-saudacao`)
*   **Correções Críticas em Produção:** `hotfix/nome-do-erro` (estas saem da `main` e voltam para `main` e `develop`)
*   **Documentação ou Ajustes Menores:** `chore/atualiza-readme` ou `docs/arquitetura`

### 2.3. Padrão de Commits (Semantic Commits)
Mensagens de commit claras ajudam a entender o histórico do chatbot. Use o padrão:
*   `feat:` para novas funcionalidades (ex: `feat: adiciona intenção de cancelamento`)
*   `fix:` para correções (ex: `fix: corrige timeout na resposta da API`)
*   `docs:` para documentação
*   `refactor:` para refatoração de código sem alterar funcionalidade

---

## 3. Pull Requests (PRs) e Code Review

Para que uma branch seja integrada à `develop` ou `main`, é obrigatório a abertura de um **Pull Request (PR)**.

### 3.1. Regras para Abertura de PR
1.  Garanta que seu código está atualizado com a branch de destino (`git pull origin develop`).
2.  Descreva claramente o que foi feito no PR.
3.  Se houver alterações em fluxos de diálogo, inclua um exemplo de como testar a conversa.

### 3.2. Template de Descrição do PR
Ao abrir um PR, preencha as seguintes informações:
> **O que foi feito?**
> (Descreva a funcionalidade ou correção. Ex: Criado o fluxo de agendamento de consultas.)
>
> **Como testar?**
> (Ex: Envie a mensagem "Quero marcar horário" para o bot e siga as instruções na tela.)
>
> **Task relacionada:** (Link para o card no Jira/Trello)

### 3.3. Processo de Revisão (Code Review)
*   Nenhum PR pode ser "auto-aprovado".
*   É necessária a aprovação de pelo menos **1 outro desenvolvedor** da equipe.
*   **O que o revisor deve olhar?** Qualidade do código, possíveis falhas de segurança, performance, e se o fluxo conversacional faz sentido.
*   Após a aprovação, o autor do PR (ou o revisor designado) realiza o *Merge*.

---

## 4. Próximos Passos
1.  Todos os membros da equipe devem clonar o repositório.
2.  Configurar acesso aos quadros de tarefas.
3.  Qualquer dúvida sobre o fluxo, comunique no canal de desenvolvimento!