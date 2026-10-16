# KIT OPERACIONAL (versão 1.0.0)

Consolidado gerado a partir dos arquivos mestres da biblioteca IA Resource Knowledge Center. Contém: playbook, modelo de prompt, guia de preenchimento, modelo de resposta do agente, kickoff e handoff. Não editar aqui: alterar o mestre, subir a versão e regenerar.



=====================================================================
## ARQUIVO MESTRE: 01_instrucoes/playbook-orquestrador.md
=====================================================================

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


=====================================================================
## ARQUIVO MESTRE: 02_modelos/PROMPT-modelo.md
=====================================================================

# PROMPT-1.0.0 — [NOME_DO_PROMPT]

## Header / Metadata

- **ID:** PROMPT-1.0.0
- **Title:** [Título inequívoco]
- **Version:** 1.0.0
- **Status:** Draft | Proposed | Approved | Deprecated
- **Type:** Research | Implementation | Audit | Review | Documentation | Planning
- **Project:** [Projeto de destino]
- **Repository:** [Repositório, se aplicável]
- **Owner:** [Responsável]
- **Created:** [YYYY-MM-DD]
- **Last Updated:** [YYYY-MM-DD]
- **Previous Version:** [Versão anterior ou N/A]
- **Related Issue / PR:** [Referências ou N/A]

## Execution Configuration

- **Model:** [Modelo disponível e apropriado]
- **Effort:** [Esforço adequado à complexidade e ao risco]
- **Session:** [New | Continue | Handoff]
- **Mode:** [Research | Plan | Execute | Review | Audit]

## [ROLE]

Define o papel técnico, as responsabilidades e os limites do agente.

## [CONTEXT]

Define o estado confirmado do projeto, requisitos, decisões aprovadas, fontes canônicas e restrições relevantes.

## [TASK]

Define a tarefa, seu objetivo, escopo e resultado esperado.

## [AUTHORIZED CHANGES]

Lista explicitamente as alterações permitidas, os arquivos ou áreas afetados e as operações proibidas.

## [CONSTRAINTS]

Define limites técnicos, operacionais, de segurança, compatibilidade e custo.

## [CRITERIA]

Define critérios objetivos de aceite, testes exigidos e evidências necessárias.

## [OUTPUT]

Define o formato do resultado, arquivos esperados, relatório de execução, pendências e próximo passo.

## Expected State

Descreve o estado verificável esperado após a execução, incluindo o que deve permanecer inalterado.


=====================================================================
## ARQUIVO MESTRE: 02_modelos/guia-preenchimento-prompt.md
=====================================================================

# Guia de preenchimento do PROMPT

O modelo `PROMPT-modelo.md` é o seu padrão e permanece sem alterações. Este guia diz como o orquestrador deve preenchê-lo.

## Convenção de ID (RECOMENDAÇÃO)

`PROMPT-<SIGLA>-<NNN>-<semver>`, por exemplo `PROMPT-IMG-003-1.0.0`.
- `SIGLA`: sigla do projeto. `NNN`: sequência do prompt no projeto.
- Correção de um item: `PROMPT-<SIGLA>-<NNN>-COR-<n>-<semver>`.
- Nova versão do mesmo prompt: subir o semver e preencher `Previous Version`.
- O ID também nomeia o relatório do agente: `responses/resposta-<ID>.md`.

## Campo a campo

| Seção | O que o orquestrador preenche |
|---|---|
| Header | Status começa em `Proposed` e vira `Approved` quando o usuário aprovar. `Type` conforme o bloco. |
| Execution Configuration | Seguir a tabela do playbook (seção 3). Só modelos que o usuário tem. |
| ROLE | Papel técnico específico do bloco (ex.: "Engenheiro de backend responsável por X") e limites do agente. |
| CONTEXT | Estado confirmado; IDs de decisões aprovadas (`decisions.md`); contratos a preservar; caminhos canônicos. Sem colar o que o agente pode ler. |
| TASK | Um objetivo, escopo e resultado esperado. Dizer o que está fora do escopo. |
| AUTHORIZED CHANGES | Lista de caminhos/áreas permitidos e operações proibidas (exclusão, migração, dependência nova, rede, produção). Se não está listado, não está autorizado. |
| CONSTRAINTS | Compatibilidade, segurança, custo, desempenho, versões fixadas. |
| CRITERIA | Critérios **mensuráveis**, testes exigidos (caminho feliz, bordas, falhas) e a evidência aceita de cada um. |
| OUTPUT | Relatório `.md` no formato `modelo-resposta-agente`, arquivos esperados, pendências e próxima ação. |
| Expected State | Estado verificável ao final, e o que deve permanecer idêntico. |

## Antes de entregar o prompt, o orquestrador confere

- [ ] Um único objetivo, escopo e fora-de-escopo claros.
- [ ] Critérios verificáveis, cada um com evidência exigida.
- [ ] Alterações autorizadas e proibidas listadas.
- [ ] Modelo e esforço realmente disponíveis ao usuário; sessão e modo coerentes.
- [ ] Nenhum segredo no texto.
- [ ] Nenhum fato de versão/API afirmado sem checagem em fonte atual.
- [ ] Entregue em bloco de código com cerca de 4 crases.

## Exemplo ilustrativo (fictício, só para mostrar a densidade esperada)

~~~
PROMPT-IMG-001-1.0.0 — Esqueleto executável do editor de imagens
Type: Implementation | Mode: Execute | Session: New
ROLE: engenheiro responsável por criar o esqueleto mínimo do projeto.
CONTEXT: decisões D-001 (plataforma) e D-002 (linguagem) aprovadas; repositório vazio.
TASK: criar a estrutura base que compila, abre uma janela vazia e executa um teste.
AUTHORIZED CHANGES: criar arquivos na raiz e em /src e /tests. Proibido: dependências fora da lista, acesso à rede, apagar arquivos.
CRITERIA: (1) build sem erros, evidência = saída do comando; (2) 1 teste passando, evidência = saída; (3) README com como executar.
OUTPUT: responses/resposta-PROMPT-IMG-001-1.0.0.md no formato do modelo.
Expected State: repositório com esqueleto que executa; nenhum arquivo fora de /src, /tests e raiz.
~~~

No uso real, o prompt completo segue todas as seções do `PROMPT-modelo.md`.


=====================================================================
## ARQUIVO MESTRE: 02_modelos/modelo-resposta-agente.md
=====================================================================

# Modelo de resposta do agente executor

O agente salva este relatório em `responses/resposta-<ID-do-prompt>.md` e o usuário o devolve ao orquestrador. Regras: preencher com resultados reais; não inventar saída de comando ou teste; se algo não foi executado, dizer.

## 1. Cabeçalho

- **Prompt ID:** [ID e versão]
- **Data:** [YYYY-MM-DD]
- **Modelo / Esforço usados:** [valores reais]
- **Status geral:** CONCLUÍDO | PARCIAL | BLOQUEADO | FALHOU

## 2. Resumo

Até 5 linhas: o que foi feito e o resultado.

## 3. Critérios de aceite

| Item | Critério (do prompt) | Status | Evidência |
|---|---|---|---|
| 1 | [texto] | CONCLUÍDO/PARCIAL/BLOQUEADO/FALHOU | [saída real, caminho de arquivo, comando] |

## 4. Alterações realizadas

Lista de arquivos criados, alterados e removidos, com uma linha sobre cada. Declarar qualquer alteração fora de AUTHORIZED CHANGES.

## 5. Testes

- **Executados:** comando e resultado real.
- **Não executados:** motivo.
- **Bloqueados:** motivo e o que desbloqueia.

## 6. Desvios do prompt

O que foi feito diferente do pedido e por quê. "Nenhum" se for o caso.

## 7. Causa-raiz (obrigatório se o status não for CONCLUÍDO)

Causa exata, rotulada como FATO, INFERÊNCIA ou HIPÓTESE, com a evidência que sustenta.

## 8. Riscos e pendências

Itens abertos, riscos identificados (só os reais), decisões que dependem do usuário.

## 9. Estado final verificado

Comparação com o Expected State do prompt: o que bate, o que diverge, o que permaneceu inalterado.

## 10. Próxima ação sugerida

Uma ação concreta.


=====================================================================
## ARQUIVO MESTRE: 02_modelos/kickoff-projeto.md
=====================================================================

# Kickoff de projeto

Objetivo: transformar uma ideia em um Dossiê de Arquitetura aprovado e em um plano de blocos, perguntando só o que muda decisão.

## Parte A: lacunas a fechar (checklist, não questionário)

Verificar o que já foi dito. Perguntar apenas o que falta **e** altera a decisão:

- Objetivo e problema; quem usa; o que é sucesso (critérios mensuráveis).
- Plataforma e ambiente: web, desktop, mobile; sistema operacional; hardware relevante.
- Restrições: prazo, orçamento/custo recorrente, licenças, conformidade, dados sensíveis.
- Integrações e dependências externas.
- Preferências ou proibições de tecnologia; conhecimento prévio do usuário.
- **Executores disponíveis:** quais IAs/agentes e modelos o usuário tem, e limites de uso.
- Escopo do MVP e o que fica fora.

## Parte B: Dossiê de Arquitetura (saída)

1. **Resumo e objetivo** (2 a 4 linhas).
2. **Requisitos e restrições** confirmados, separados de premissas (rotular FATO/INFERÊNCIA/HIPÓTESE).
3. **Decisões a tomar**, cada uma com no mínimo duas alternativas:

   | Decisão | Alternativa | Vantagens | Desvantagens | Complexidade | Risco | Custo |
   |---|---|---|---|---|---|---|

   Recomendação justificada. Para tecnologias, versões e APIs: fonte atual consultada, com link.
4. **Arquitetura proposta** (componentes, fluxo de dados, fronteiras).
5. **Método** (cadência, critérios de pronto) proporcional ao projeto.
6. **MVP e plano de blocos** (B01..Bn): objetivo, dependência, critério de aceite, risco.
7. **Riscos e pendências** abertos.
8. **Skills recomendadas**, vindas de `skills-catalog.md`, com versão fixada.
9. **Primeiro prompt** (B01, esqueleto executável) no formato `PROMPT-modelo.md`.

Após a aprovação do usuário: gerar `project-index.md`, `current-status.md` e `decisions.md` iniciais a partir dos templates.

## Parte C: eixos de decisão por tipo de projeto (ponto de partida, não resposta pronta)

Exemplo, editor de imagens: plataforma-alvo; motor de renderização e uso de GPU; formatos suportados; edição não destrutiva; desempenho com imagens grandes; extensibilidade (plugins); licenciamento de bibliotecas; empacotamento e distribuição. As alternativas concretas devem sair de pesquisa atual, não de memória.


=====================================================================
## ARQUIVO MESTRE: 03_continuidade/handoff-novo-chat.md
=====================================================================

# Handoff para novo chat

Os três arquivos de continuidade estão nas fontes do projeto, então o handoff é curto: ele só ancora o novo chat.

## 1. Quando abrir um chat novo

- Fase fechada.
- Muitos blocos no mesmo chat (referência: 5 a 8) ou respostas lentas, repetitivas ou contraditórias.
- Lentidão do navegador por chat longo.

## 2. No chat atual, antes de fechar

Enviar:

~~~
Prepare o fechamento deste chat. Entregue, completos e prontos para substituir os arquivos das fontes:
1. current-status.md atualizado.
2. decisions.md e project-index.md, apenas se mudaram.
3. O texto de abertura do próximo chat (modelo de handoff-novo-chat.md), preenchido.
Liste o que ficou pendente e qualquer ponto que você não conseguiu confirmar.
~~~

Depois: substituir os arquivos nas fontes do projeto pelas versões novas (o ChatGPT não edita as fontes por conta própria).

## 3. Abertura do novo chat (dentro do mesmo projeto)

~~~
Novo chat do projeto [NOME] (sigla [SIGLA]), continuação do chat anterior.
1. Leia project-index.md, current-status.md e decisions.md das fontes.
2. Confirme em até 5 linhas: fase atual, último bloco concluído, bloco em andamento, bloqueios e próxima ação.
3. Aponte qualquer inconsistência entre os arquivos antes de seguir.
4. Aguarde minha confirmação para continuar.

Contexto adicional desta sessão: [nada | o que for essencial e não está nos arquivos]
~~~

## 4. Se o ChatGPT não conseguir ler os arquivos

Anexe os três arquivos na primeira mensagem. Não deixe o chat reconstruir o estado de memória.
