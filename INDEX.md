# AI Research & Knowledge Center — Índice

**Versão do documento:** 2.0.0  
**Estado:** Baseline de governança implementada  
**Última revisão:** 2026-10-15

## Finalidade e autoridade

`INDEX.md` é o catálogo e ponto de roteamento. Ele informa quais registros existem e onde encontrá-los; não substitui o conteúdo, evidências ou aprovação registrados nos documentos de origem.

| Documento | Autoridade e conteúdo |
|---|---|
| `CURRENT.md` | Síntese operacional atual; somente conhecimento central aplicável e decisões aprovadas em vigor. |
| `DECISIONS.md` | Registro canônico de decisões transversais e sua aprovação, justificativa, escopo e estado. O owner aprova decisões cross-project. |
| `HISTORY.md` | Eventos significativos de criação, mudança semântica, validação, revisão, substituição e retirada. |
| `QUEUE.md` | Trabalho de pesquisa, revisão, revalidação e bloqueios ainda pendentes. |
| `sources/SOURCES.md` | Registro canônico de fontes e identificadores de proveniência. |
| `research/RES-TEMPLATE.md` | Contrato e modelo para registros de pesquisa `RES`. |
| `knowledge/KNOW-TEMPLATE.md` | Contrato e modelo para unidades reutilizáveis de conhecimento `KNOW`. |

Não há saída de PROMPT-0.2.0 disponível na estrutura inspecionada. Este baseline usa o `INDEX.md` encontrado e as aprovações explícitas de PROMPT-0.3.0; não afirma reproduzir nem reconciliar conteúdo ausente.

## Regras de uso

1. Consulte este índice antes de iniciar pesquisa ou reutilizar conhecimento.
2. Use o estado e as condições de aplicabilidade do registro detalhado; título ou presença no índice não equivalem a validação.
3. Registros centrais têm IDs estáveis e revisão semântica `rN` (por exemplo, `KNOW-001@r1`). Consumidores registram ID e revisão exatos quando a referência for relevante.
4. Adaptações específicas ficam no projeto consumidor e não alteram silenciosamente o registro central.
5. Uma atividade de pesquisa pode terminar sem produzir registro `KNOW` ou `DEC`.
6. Não há sincronização automática presumida entre projetos ChatGPT nem entre arquivos locais e fontes do ChatGPT. Compartilhe explicitamente o documento/referência necessária.

## Identidade, revisão e atualização

- Prefixos e IDs: `RES-###` (pesquisa), `KNOW-###` (unidade de conhecimento), `DEC-###` (decisão transversal) e `SRC-###` (fonte). IDs são únicos, permanentes e nunca reutilizados; lacunas não são preenchidas retroativamente.
- `rN` identifica a revisão semântica do registro, iniciando em `r1`. Mudança de conclusão, escopo, aplicabilidade, premissas materiais, evidência determinante ou estado de validação requer nova revisão semântica. Correção editorial ou atualização de metadado sem efeito no significado mantém a revisão.
- Preserve revisões anteriores ou seus snapshots/localizadores; registre substituição e relação entre IDs. Não sobrescreva o histórico semântico.
- A data de acesso é metadado da fonte, não substitui a revisão do registro.

## Catálogo

| ID | Título | Tipo/categoria | Ciclo de vida | Validação (KNOW) | Confiança (KNOW) | Revisão | Documento |
|---|---|---|---|---|---|---|---|
| — | Nenhum registro de pesquisa, conhecimento ou decisão técnica cadastrado nesta versão. | — | — | — | — | — | — |

As decisões GOV-001 a GOV-018 sobre esta governança estão no `DECISIONS.md`; elas não são afirmações de conhecimento técnico validado. Nenhuma unidade técnica `KNOW` está validada nesta versão.

## Categorias

Use categorias para classificar o assunto; categoria não define lifecycle nem tipo de registro. A taxonomia útil do índice anterior é preservada:

| Código | Categoria |
|---|---|
| ARCH | Arquitetura |
| AIENG | Engenharia de IA |
| MODEL | Modelos e provedores |
| PROMPT | Engenharia de prompts |
| SKILL | Skills e ferramentas |
| QA | Qualidade e testes |
| SEC | Segurança |
| OPS | Operação e observabilidade |
| PROCESS | Processo e entrega |
| RESEARCH | Pesquisa técnica |
| DECISION | Decisões transversais |
| RESOURCE | Recursos |

Registros `RES`, `KNOW` e `DEC` podem receber uma ou mais categorias. `OPEN-###` identifica item de fila, não registro de conhecimento. Prefixos `PAT`, `SKILL` e `REF` que apareciam como exemplos no índice anterior não têm contrato de registro nesta versão; não os use para criar registros até que um contrato seja definido.

## Vocabulários e separação de conceitos

Os estados são específicos ao tipo, conforme os contratos em `research/RES-TEMPLATE.md`, `knowledge/KNOW-TEMPLATE.md` e `DECISIONS.md`. Não use um estado de ciclo de vida como sinônimo de validação.

- **Lifecycle** indica a situação editorial/operacional do registro.
- **Validation state** indica se a afirmação de `KNOW` passou pela avaliação de evidência exigida.
- **Confidence** é `LOW`, `MEDIUM` ou `HIGH`; expressa quão bem a conclusão é sustentada no escopo declarado e não determina validação.
- Confiabilidade da fonte e força da evidência são avaliações distintas, registradas como justificativa junto à fonte/evidência, não como substitutos da confiança ou validação.

## Reutilização e publicação por consumidores

Antes de aplicar um registro: localize a revisão exata; avalie contexto, versão, pressupostos, limitações e evidências; registre no consumidor a referência `ID@rN`, data de consulta e avaliação de aplicabilidade. Registre adaptações locais com a referência de origem, motivo e diferença. Não publique adaptação como conhecimento central.

Uma referência fica **stale** quando sua revisão central mudou, foi substituída/retirada, uma fonte material foi invalidada ou um gatilho de revalidação ocorreu. O consumidor deve reavaliar antes de novo uso material e atualizar a referência local. Não se presume notificação automática.

## Checklist de consistência para publicação multi-arquivo

- [ ] IDs únicos e referências apontam para registros e caminhos existentes.
- [ ] `ID@rN`, ciclo de vida e validação usam os formatos/vocabulários definidos.
- [ ] Alterações semânticas incrementaram revisão; editoriais/metadados não incrementaram.
- [ ] `INDEX.md` aponta para revisão e estado atuais; `CURRENT.md` inclui somente conteúdo elegível.
- [ ] Aprovações, mudanças significativas e itens pendentes foram refletidos em `DECISIONS.md`, `HISTORY.md` e `QUEUE.md`, quando aplicável.
- [ ] Fontes usadas estão em `sources/SOURCES.md`, com proveniência suficiente; evidência suporta a afirmação indicada.
- [ ] Substituições, conflitos, limitações, adaptações de consumidores e fontes invalidadas estão rastreáveis.
- [ ] Não foi criado fato, fonte, atividade de pesquisa ou conhecimento validado sem evidência real.

Prefira Git quando disponível para histórico e revisão. Sem Git, mantenha revisões anteriores por cópias datadas ou snapshots identificáveis, registre alterações em `HISTORY.md` e atualize arquivos relacionados de forma coordenada.
