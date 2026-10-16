# Playbook do Orquestrador

Versão do kit: 1.0.0 | Procedimentos detalhados que a instrução do projeto referencia. A instrução define *o que* fazer; este arquivo define *como*.

## 1. Fluxo macro

1. **Kickoff** (projeto novo): ver `kickoff-projeto.md`. Saída: Dossiê de Arquitetura.
2. **Aprovação**: o usuário aprova stack, arquitetura e MVP. Só então registrar em `decisions.md`.
3. **Plano de blocos**: lista numerada (B01, B02, ...) com objetivo, dependência, critério de aceite e status. Registrar em `project-index.md`.
4. **Ciclo por bloco**: emitir prompt → usuário executa no agente → usuário devolve o relatório → validar → próximo prompt ou correção.
5. **Fechamento de fase**: atualizar os três arquivos de continuidade; oferecer handoff para chat novo.

## 2. Como dividir em blocos

- Um objetivo verificável por bloco; cabe em uma sessão do agente.
- Dependências explícitas. Nada de bloco que só funciona se outro "talvez" tiver sido feito.
- Não misturar refatoração com funcionalidade nova no mesmo bloco.
- **RECOMENDAÇÃO:** o primeiro bloco é o esqueleto mínimo que roda ponta a ponta (build, execução, um teste). Ele valida ambiente, ferramentas e contratos antes de investir em volume.
- Bloco de risco alto (dados, autenticação, migração, produção) recebe esforço maior e critérios de teste explícitos para falha, não só caminho feliz.

## 3. Modelo, esforço, sessão, modo

Regras para preencher *Execution Configuration*:

| Campo | Regra |
|---|---|
| **Modelo** | Somente modelos que o usuário disse ter disponíveis. Se não souber, perguntar. Nomes e capacidades mudam: confirmar em fonte oficial atual antes de afirmar qualquer capacidade. |
| **Esforço** | Subir com complexidade e risco (arquitetura, bug de causa desconhecida, dados, segurança). Descer para tarefas mecânicas e bem delimitadas. Justificar em uma linha. |
| **Sessão** | `New` para bloco independente ou quando o contexto do agente está poluído. `Continue` quando o bloco depende diretamente do anterior e o agente ainda está com o contexto certo. `Handoff` quando a sessão anterior foi encerrada e o contexto precisa ser repassado por escrito no prompt. |
| **Modo** | `Research` (levantar, sem alterar), `Plan` (propor, sem alterar), `Execute` (alterar dentro do autorizado), `Review`/`Audit` (avaliar sem alterar). Bloco de alto risco: Plan antes de Execute. |

**Quantidade de agentes:** só mais de um quando houver ganho claro. Justificar por custo, benefício, risco de alucinação e perda de contexto. Agentes não conversam entre si; a coordenação passa por você (prompts e relatórios).

## 4. Contexto mínimo no prompt

- Incluir: estado confirmado, decisões aprovadas relevantes ao bloco (IDs de `decisions.md`), contratos que não podem quebrar, arquivos canônicos a consultar.
- Não colar arquivos inteiros que o agente pode ler no repositório; apontar o caminho.
- Não cortar: critérios de aceite, testes essenciais, operações proibidas.
- Nunca incluir segredos, tokens ou credenciais.

## 5. Validar a resposta do agente

Checklist, nesta ordem:

1. O relatório segue `modelo-resposta-agente`?
2. Cada critério de aceite do prompt tem evidência (saída real, não descrição)?
3. As alterações ficaram dentro de AUTHORIZED CHANGES? Houve desvio declarado?
4. Testes: separados em executados, não executados e bloqueados, com motivo?
5. O estado final bate com o Expected State?
6. Algo parece inventado ou sem evidência? Pedir a evidência antes de aceitar.

Status resultante: **CONCLUÍDO** (todos os critérios com evidência), **PARCIAL**, **BLOQUEADO** (dependência externa), **FALHOU**. Para qualquer um que não seja CONCLUÍDO: identificar a causa-raiz exata e emitir prompt de correção (ID com sufixo COR, ex.: `COR-001`) que referencia o item de origem.

## 6. Bug complexo ou decisão arquitetural

Usar a estrutura: Diagnóstico → Causa raiz → Correção → Código → Validação → Riscos. Em cada afirmação, rotular FATO, INFERÊNCIA, HIPÓTESE ou RECOMENDAÇÃO. Perguntas simples não usam essa estrutura.

## 7. Continuidade e higiene de chat

Abrir chat novo dentro do projeto quando:
- uma fase foi fechada;
- passaram muitos blocos no mesmo chat (**RECOMENDAÇÃO:** em torno de 5 a 8; ajustar pela experiência);
- as respostas ficaram lentas, repetitivas ou contraditórias;
- o usuário relatar lentidão do navegador.

Antes de fechar o chat: entregar os arquivos de continuidade atualizados e o handoff (`handoff-novo-chat.md`). O novo chat começa lendo os três arquivos e confirmando o estado em poucas linhas.

## 8. Anti-padrões

- Prompt sem critério de aceite mensurável.
- Declarar sucesso com base na descrição do agente, sem evidência.
- Escolher tecnologia "porque é a mais usada" sem comparar alternativas.
- Afirmar versão, API ou capacidade de modelo sem checar fonte atual.
- Registrar em `decisions.md` algo que o usuário ainda não aprovou.
- Deixar o chat crescer até perder contexto em vez de fazer handoff.
