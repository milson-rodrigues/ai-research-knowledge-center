# Playbook do Orquestrador

Versão do kit: 1.1.0 | Procedimentos operacionais do orquestrador.

A rota (`00_ROTA-DE-CONSULTA.md`) define **o que consultar**. As regras de prompt (`../02_modelos/regras-prompt.md`) definem **os requisitos obrigatórios**. Este playbook define **como coordenar o trabalho**. Regras transversais ficam em `regras-projetos.md`; metodologias específicas estão em `../05_metodologias/`.

## 1. Fluxo macro

1. **Kickoff:** para projeto novo, seguir `../02_modelos/kickoff-projeto.md` e produzir o Dossiê de Arquitetura.
2. **Aprovação:** usuário aprova stack, arquitetura e MVP; só então registrar decisões em `decisions`.
3. **Plano de blocos:** enumerar B01, B02 etc. com objetivo, dependências, risco, critérios e status. Registrar no arquivo de índice do projeto.
4. **Preparação do prompt:** consultar `PROMPT-modelo.md`, `guia-preenchimento-prompt.md`, `regras-prompt.md`, este playbook e os documentos do projeto/metodologias pertinentes.
5. **Ciclo por bloco:** emitir prompt → usuário executa no agente → receber relatório → validar por evidências → próximo prompt ou correção.
6. **Fechamento:** atualizar arquivos de continuidade e preparar handoff quando necessário.

## 2. Dividir e ordenar blocos

- Um objetivo verificável por bloco, preferencialmente compatível com uma sessão do executor.
- Declarar dependências explícitas; não presumir que uma etapa foi concluída.
- Não misturar refatoração ampla e funcionalidade nova no mesmo bloco sem justificativa e autorização.
- Para trabalho com várias etapas, aplicar `../05_metodologias/decomposicao-tarefas.md`.
- Respeitar dependências obrigatórias. Entre blocos prontos, equilibrar risco, custo, benefício e reversibilidade — não escolher somente pelo menor esforço.
- Blocos que afetem dados, autenticação, migrações, contratos públicos ou produção exigem análise mais rigorosa, testes de falha e plano de reversão proporcional.
- Validar cada bloco antes de liberar o próximo. Paralelizar apenas tarefas comprovadamente independentes quando o ganho superar o custo de coordenação.

## 3. Modelo, esforço, sessão e modo

| Campo | Regra |
|---|---|
| **Modelo** | Somente modelos declarados como disponíveis pelo usuário. Se não souber, perguntar. Confirmar capacidades mutáveis em fonte oficial atual. |
| **Esforço** | Maior para arquitetura, bugs de causa desconhecida, dados e segurança; menor para tarefas mecânicas e bem delimitadas. Justificar em uma linha. |
| **Sessão** | `New` para bloco independente ou contexto poluído; `Continue` quando a continuidade direta ainda é útil; `Handoff` quando o contexto precisa ser repassado por escrito. |
| **Modo** | `Research` (investigar sem alterar), `Plan` (propor sem alterar), `Execute` (alterar dentro da autorização), `Review`/`Audit` (avaliar sem alterar). Tarefa de alto risco passa por planejamento antes da execução. |

Usar múltiplos agentes apenas quando houver ganho claro; considerar custo, benefício, risco de alucinação e perda de contexto. Coordenar por prompts, artefatos e relatórios explícitos.

## 4. Contexto mínimo no prompt

- Incluir estado confirmado, decisões aprovadas relevantes, contratos a preservar e caminhos canônicos.
- Não colar arquivos inteiros que o executor pode ler diretamente; apontar os caminhos somente quando o acesso estiver confirmado.
- Não omitir critérios de aceite, testes essenciais, limites de alteração ou operações proibidas.
- Nunca incluir segredos, tokens ou credenciais.
- Se não houver certeza de que o executor acessa documentos externos, incluir diretamente as instruções críticas no prompt.

## 5. Validar a resposta do agente

1. O relatório segue `../02_modelos/modelo-resposta-agente.md`?
2. Cada critério tem evidência real e pertinente?
3. As alterações ficaram dentro de `AUTHORIZED CHANGES`? Desvios foram declarados?
4. Testes estão separados em executados, não executados e bloqueados, com motivo?
5. O estado final corresponde ao `Expected State`?
6. Existem afirmações sem evidência ou incompatíveis com arquivos consultados?
7. Foram avaliados os aspectos pertinentes do Quality Gate de `../02_modelos/regras-prompt.md`?

Status: **CONCLUÍDO** (critérios comprovados), **PARCIAL**, **BLOQUEADO** ou **FALHOU**. Para resultado diferente de concluído, informar causa sustentada por evidência e próxima ação. Criar prompt de correção referenciando o original quando apropriado.

## 6. Bug complexo ou decisão arquitetural

Usar: Diagnóstico → Causa raiz → Correção → Código/arquivos → Validação → Riscos. Rotular alegações relevantes como `FATO`, `INFERÊNCIA`, `HIPÓTESE` ou `RECOMENDAÇÃO`. Para bugs, aplicar `../05_metodologias/diagnostico-bugs.md` quando pertinente. Perguntas simples não exigem essa estrutura.

## 7. Continuidade e higiene de chat

Abrir chat novo quando uma fase concluir, o contexto ficar grande ou contraditório, ou houver lentidão que atrapalhe o trabalho. O número de blocos é apenas um sinal; use julgamento. Antes do handoff, atualizar arquivos de continuidade e seguir `../03_continuidade/handoff-novo-chat.md`.

## 8. Anti-padrões

- Prompt sem critério de aceite mensurável.
- Declarar sucesso sem evidência real.
- Escolher tecnologia sem comparar alternativas quando a decisão for relevante.
- Afirmar versão, API ou capacidade de modelo sem fonte atual.
- Registrar como decisão algo que o usuário não aprovou.
- Alterar arquivos fora da autorização.
- Implementar muitas mudanças sem validação intermediária quando isso aumentar o risco.
- Inventar acesso a arquivos, execução de testes ou resultados.
