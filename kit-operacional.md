# KIT OPERACIONAL (versão 1.1.0)

Consolidado gerado a partir dos arquivos mestres da biblioteca IA Resource Knowledge Center. Contém os documentos operacionais centrais e o índice das novas regras/metodologias. Consolidado de conveniência: quando houver divergência, os arquivos mestres atuais são a fonte canônica. Não editar aqui como fonte de verdade; atualize os mestres e regenere.



=====================================================================
## ARQUIVO MESTRE: 01_instrucoes/playbook-orquestrador.md
=====================================================================

# Playbook do Orquestrador

Versão do kit: 1.1.0. A rota define **o que consultar**; regras e modelos definem **o que é obrigatório**; este playbook define **como coordenar o trabalho**.

## 1. Fluxo macro
1. Kickoff para projeto novo e criação do Dossiê de Arquitetura.
2. Aprovação do usuário para stack, arquitetura e MVP; só depois registrar decisões.
3. Plano em blocos B01, B02... com objetivo, dependências, risco, critérios e status.
4. Preparar prompt consultando modelo, guia, regras de prompt, este playbook e documentação/metodologias pertinentes.
5. Executar bloco, receber relatório, validar evidências e então corrigir ou avançar.
6. Fechar fase atualizando arquivos de continuidade e preparando handoff quando necessário.

## 2. Dividir e ordenar blocos
- Um objetivo verificável por bloco; dependências explícitas.
- Não misturar refatoração ampla e funcionalidade nova sem justificativa e autorização.
- Aplicar `05_metodologias/decomposicao-tarefas.md` em trabalhos com várias etapas.
- Respeitar dependências obrigatórias. Entre blocos prontos, equilibrar risco, custo, benefício e reversibilidade.
- Mudanças em dados, autenticação, migrações, contratos públicos ou produção exigem análise mais rigorosa, testes de falha e plano de reversão proporcional.
- Validar cada bloco antes de liberar o próximo. Paralelizar apenas tarefas comprovadamente independentes.

## 3. Modelo, esforço, sessão e modo
- **Modelo:** somente os modelos que o usuário declarou disponíveis; confirmar capacidades mutáveis em fonte oficial atual.
- **Esforço:** maior para arquitetura, bugs de causa desconhecida, dados e segurança; menor para tarefas mecânicas e delimitadas; justificar.
- **Sessão:** `New` para bloco independente/contexto poluído; `Continue` quando a continuidade direta é útil; `Handoff` quando o contexto deve ser repassado por escrito.
- **Modo:** `Research` investiga; `Plan` propõe sem alterar; `Execute` altera dentro da autorização; `Review`/`Audit` avalia sem alterar. Tarefas de alto risco devem passar por planejamento antes da execução.
- Usar vários agentes apenas quando o ganho superar custo de coordenação, risco de alucinação e perda de contexto.

## 4. Contexto mínimo
Incluir estado confirmado, decisões aprovadas, contratos a preservar, caminhos canônicos, critérios de aceite, testes essenciais, limites e operações proibidas. Não colar arquivos inteiros que o executor possa ler; não depender apenas de links sem acesso confirmado. Nunca incluir segredos.

## 5. Validar relatório
Verificar o modelo de resposta, evidências por critério, escopo autorizado, desvios, testes executados/não executados/bloqueados, estado esperado e Quality Gate. Status: `CONCLUÍDO`, `PARCIAL`, `BLOQUEADO` ou `FALHOU`. Para status diferente de concluído, registrar causa sustentada por evidência e próxima ação.

## 6. Bug complexo e decisão arquitetural
Usar Diagnóstico → Causa raiz → Correção → Arquivos/código → Validação → Riscos. Distinguir FATO, INFERÊNCIA, HIPÓTESE e RECOMENDAÇÃO. Aplicar diagnóstico de bugs quando pertinente.

## 7. Continuidade
Fazer handoff ao concluir uma fase ou quando o contexto ficar grande, contraditório ou lento. Atualizar arquivos de continuidade e seguir `03_continuidade/handoff-novo-chat.md`.

## 8. Anti-padrões
Prompt sem critério verificável; sucesso sem evidência; tecnologia escolhida sem comparação quando relevante; versões/API/capacidades sem fonte atual; decisão sem aprovação; alteração fora da autorização; lote grande de mudanças sem validação intermediária; inventar acesso, testes ou resultados.

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

O `PROMPT-modelo.md` define a estrutura obrigatória e deve ser preservado. As regras normativas ficam em `regras-prompt.md` para evitar duplicação.

## Consulta obrigatória antes de preencher
Consulte `regras-prompt.md`, `../01_instrucoes/playbook-orquestrador.md`, `../01_instrucoes/regras-projetos.md` quando houver impacto duradouro, a metodologia pertinente em `../05_metodologias/`, `modelo-resposta-agente.md` e `PROMPT-modelo.md`. O prompt final deve conter as instruções críticas; não dependa apenas de links que o executor talvez não consiga acessar. Se um arquivo necessário estiver indisponível, declare a limitação; não o reconstrua de memória.

## Convenção de ID (RECOMENDAÇÃO)
`PROMPT-<SIGLA>-<NNN>-<semver>`, por exemplo `PROMPT-IMG-003-1.0.0`.
- Correção: `PROMPT-<SIGLA>-<NNN>-COR-<n>-<semver>`.
- Nova versão: subir o semver e preencher `Previous Version`.
- O relatório: `responses/resposta-<ID>.md`.

## Campo a campo
- **Header:** status `Proposed` até aprovação; definir tipo correto.
- **Execution Configuration:** somente modelos/esforços declarados disponíveis; seguir o playbook.
- **ROLE:** papel específico e limites do agente.
- **CONTEXT:** estado confirmado, decisões aprovadas, contratos e arquivos canônicos.
- **TASK:** um objetivo verificável, escopo e fora de escopo.
- **AUTHORIZED CHANGES:** áreas permitidas e operações proibidas; não alterar o que não está autorizado.
- **CONSTRAINTS:** limites técnicos, operacionais, de segurança, compatibilidade, versão e custo.
- **CRITERIA:** critérios mensuráveis, testes e evidência aceita por critério.
- **OUTPUT:** relatório padronizado, arquivos esperados, pendências e próxima ação.
- **Expected State:** estado final verificável e elementos que devem permanecer inalterados.

## Checklist
- Títulos de seção idênticos aos do modelo.
- Objetivo, escopo, fora de escopo e autorização explícitos.
- Critérios verificáveis e evidência exigida por critério.
- Dependências e blocos ordenados, quando aplicável.
- Modelo/esforço confirmados; sem inventar capacidades.
- Versões/API verificadas em fonte oficial quando necessário.
- Testes proporcionais ao risco e relatório exigido.
- Sem segredos; estado esperado e áreas preservadas definidos.

No uso real, preencher todas as seções de `PROMPT-modelo.md`; o consolidado resume as regras, e o documento mestre contém o guia completo.

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


=====================================================================
## EXTENSÃO: 02_modelos/regras-prompt.md
=====================================================================

# Regras essenciais de prompt

- Basear contexto em fontes canônicas e decisões aprovadas; priorizar documentação oficial atual para versões/API/comportamentos mutáveis.
- Distinguir fatos, inferências, hipóteses e recomendações; não inventar arquivos, resultados ou testes.
- Antes da execução, definir objetivo, escopo, fora de escopo, áreas autorizadas, dependências, riscos, critérios, testes e evidências.
- Em projetos multifásicos, dividir em blocos pequenos e validar cada bloco antes do próximo.
- Proteger contratos e comportamentos fora do escopo. Mudanças em código estável/produção exigem autorização, análise de impacto e validação adequada.
- Aplicar Quality Gate proporcional: manutenibilidade, arquitetura, extensibilidade, desempenho e complexidade versus benefício.
- Separar testes executados, não executados e bloqueados. Nunca declarar sucesso sem evidência real.
- Manter propostas separadas das decisões aprovadas; registrar conflitos e resolvê-los antes de emitir instruções contraditórias.

=====================================================================
## EXTENSÃO: 01_instrucoes/regras-projetos.md
=====================================================================

# Regras transversais de projeto

- Usar os arquivos canônicos do próprio projeto como fonte de estado; templates e exemplos não são estado real.
- Antes de alterar arquitetura/interfaces, identificar módulos, consumidores, contratos e decisões afetados; comparar alternativas relevantes.
- Não introduzir frameworks, dependências ou abstrações apenas por preferência ou popularidade.
- Preservar comportamentos fora do escopo e evitar refatorações oportunistas.
- Mudanças de alto impacto em dados, autenticação, migração ou produção exigem justificativa, autorização, análise de impacto, testes e reversão proporcionais.
- Avaliar manutenibilidade, arquitetura, extensibilidade, desempenho, segurança, custo operacional e complexidade de forma proporcional.
- Registrar decisões apenas após aprovação; atualizar documentação canônica e referências após a decisão.

=====================================================================
## EXTENSÃO: 05_metodologias/README.md
=====================================================================

Escolher metodologia de acordo com a tarefa; não aplicar todas por padrão:

- `decomposicao-tarefas.md`: transforma trabalhos multifásicos em blocos com dependências, riscos e critérios verificáveis.
- `tdd.md`: ciclo Red → Green → Refactor, testes de regressão e evidências.
- `diagnostico-bugs.md`: reproduzir, formular hipóteses, observar, determinar causa e corrigir minimamente.
- `revisao-codigo.md`: revisar aderência à especificação, qualidade, riscos, testes e limites autorizados.

Metodologias complementam as regras de prompt e o playbook. Relate as etapas realmente executadas e as limitações. Inspiração composável: https://github.com/mattpocock/skills.
