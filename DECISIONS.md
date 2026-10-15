# Decisões transversais

**Responsabilidade:** registro canônico de decisões cross-project. Somente o owner aprova uma decisão transversal. Pesquisa e proposta não equivalem a aprovação.

## Contrato de decisão

Cada decisão deve ter ID estável `DEC-###` (decisões de baseline de governança aprovadas aqui mantêm os IDs `GOV-###` já atribuídos), título, revisão `rN`, estado `PROPOSED|APPROVED|REJECTED|SUPERSEDED|WITHDRAWN`, data, autoridade/aprovação, contexto, decisão, justificativa, escopo/limites, impactos, referências/evidências quando houver, relações e histórico de revisão. Decisão aprovada recebe confirmação explícita do owner. Mudança semântica incrementa `rN`; mudança editorial mantém revisão. Decisões substituídas permanecem consultáveis e apontam para a sucessora.

## Baseline de governança aprovado

Fonte de aprovação: decisões explicitamente fornecidas pelo owner no contexto de PROMPT-0.3.0, em 2026-10-15. PROMPT-0.2.0 não estava disponível para inspeção. As entradas abaixo transcrevem apenas decisões aprovadas; não afirmam evidência técnica externa.

| ID | Decisão aprovada | Estado/revisão |
|---|---|---|
| GOV-001 | `INDEX.md` é o catálogo e documento de roteamento. | APPROVED / r1 |
| GOV-002 | `CURRENT.md` contém a síntese do conhecimento operacional atual. | APPROVED / r1 |
| GOV-003 | `DECISIONS.md` contém decisões cross-project. | APPROVED / r1 |
| GOV-004 | `HISTORY.md` registra mudanças significativas de conhecimento. | APPROVED / r1 |
| GOV-005 | `QUEUE.md` gerencia trabalho pendente de conhecimento e pesquisa. | APPROVED / r1 |
| GOV-006 | `sources/SOURCES.md` é o registro canônico de fontes. | APPROVED / r1 |
| GOV-007 | Consumidores referenciam ID e revisão central exatos quando relevante. | APPROVED / r1 |
| GOV-008 | Uma atividade de pesquisa não precisa produzir registro de conhecimento ou decisão. | APPROVED / r1 |
| GOV-009 | Confiança é independente do estado de validação. | APPROVED / r1 |
| GOV-010 | Adaptações específicas de consumidores permanecem no projeto consumidor. | APPROVED / r1 |
| GOV-011 | O owner é a autoridade de aprovação para decisões cross-project. | APPROVED / r1 |
| GOV-012 | Revisões são sob demanda; datas de revisão e trabalho pendente são registrados. | APPROVED / r1 |
| GOV-013 | Git é recomendado quando disponível, mas não obrigatório. | APPROVED / r1 |
| GOV-014 | Cada registro KNOW é uma unidade reutilizável com escopo definido. | APPROVED / r1 |
| GOV-015 | Alterações somente editoriais não incrementam a revisão semântica. | APPROVED / r1 |
| GOV-016 | Revisão temporal e revalidação acionada por eventos substituem expiração automática universal. | APPROVED / r1 |
| GOV-017 | Pesquisa, conhecimento e decisão têm ciclos de vida distintos. | APPROVED / r1 |
| GOV-018 | Confiança usa os valores `LOW`, `MEDIUM` e `HIGH`. | APPROVED / r1 |

## Contratos operacionais dos tipos

Estes contratos implementam os requisitos de PROMPT-0.3.0; não aprovam políticas técnicas para projetos consumidores.

### Pesquisa (`RES`)

Lifecycle: `PLANNED|ACTIVE|COMPLETED|BLOCKED|CANCELLED`. Registro obrigatório: ID, revisão, título/pergunta, escopo, lifecycle, datas de criação/atualização, método/limitações, fontes/evidências consultadas, achados com distinção entre observação e inferência, conclusão (inclusive inconclusiva), próxima ação e relações. `COMPLETED` significa que a atividade foi encerrada conforme escopo, não que seus achados são conhecimento validado. Pode terminar sem `KNOW` ou `DEC`.

### Conhecimento (`KNOW`)

Lifecycle: `DRAFT|ACTIVE|SUPERSEDED|WITHDRAWN|BLOCKED`. Validation state: `UNASSESSED|IN_PROGRESS|VALIDATED|REJECTED|REVALIDATION_REQUIRED`. São campos separados: lifecycle governa disponibilidade/continuidade do registro; validation state documenta o exame de evidência. `ACTIVE` não significa `VALIDATED`; somente `ACTIVE` + `VALIDATED` pode ser apresentado como conhecimento central validado. `BLOCKED` significa que o trabalho do registro não pode avançar; mantenha explícito o impedimento e a ação necessária.

Para transição a `VALIDATED`, o registro precisa: (1) ter pergunta/escopo e condições de aplicação precisos; (2) separar fatos observados, inferências e recomendações; (3) ligar cada afirmação material a evidência rastreável; (4) identificar versão, contexto e limitações das fontes; (5) avaliar qualidade/força, conflitos e limitações; (6) sustentar conclusão reproduzível ou justificar triangulação adequada ao tipo de alegação; (7) declarar confiança (`LOW|MEDIUM|HIGH`) com justificativa independente do estado; (8) documentar revisão por owner/revisor designado, data e pendências. A ausência de evidência adequada, conflito material não resolvido, fonte essencial inválida ou escopo indefinido impede validação.

Transições: `UNASSESSED` → `IN_PROGRESS` ao iniciar avaliação; → `VALIDATED` somente após cumprir os critérios acima; → `REJECTED` quando evidência disponível não sustenta a conclusão; → `REVALIDATION_REQUIRED` após gatilho material. Após reavaliação, registrar resultado e nova revisão semântica quando a conclusão/escopo/validade mudar. `SUPERSEDED` aponta para sucessor; `WITHDRAWN` registra motivo de retirada. Conflitos não resolvidos ficam explícitos e bloqueiam a conclusão afetada; fontes invalidadas são marcadas no registro da fonte e todas as afirmações dependentes passam a exigir revisão.

### Decisões (`DEC`)

Lifecycle: `PROPOSED|APPROVED|REJECTED|SUPERSEDED|WITHDRAWN`. Aprovação requer registro explícito do owner, data e escopo. `APPROVED` denota autoridade decisória, não verdade técnica universal. Mudança de contexto pode exigir revisão, substituição ou retirada; decisões anteriores permanecem preservadas.

## Confiança, validação e evidência

- **Source reliability:** quão identificável, competente, íntegra e adequada é uma fonte para a afirmação em questão; justifique por fonte, sem pontuação automática.
- **Evidence strength:** quão direta, pertinente, atual e corroborada é a evidência para uma afirmação; descreva por afirmação.
- **Confidence:** avaliação calibrada da conclusão dentro do escopo, `LOW|MEDIUM|HIGH`, com justificativa. Não é média de confiabilidade nem força.
- **Validation state:** resultado do processo de verificação do registro KNOW. Confiança alta não valida evidência fraca; `VALIDATED` não remove limitações registradas.

Revisão é sob demanda e registrada. Gatilhos de revalidação incluem fonte alterada/retirada, evidência contraditória, mudança relevante de versão/contexto, falha de reprodução, mudança de premissa ou relato de inaplicabilidade. Não há prazo universal de expiração.
