# Fila de pesquisa e governança

Use IDs únicos `OPEN-###`. Lifecycle do item: `OPEN|IN_PROGRESS|BLOCKED|DONE|CANCELLED`. Cada item contém título, tipo, prioridade, data de abertura/última revisão, pergunta ou trabalho, responsável/autoridade quando conhecido, dependências, próxima ação, critério de conclusão e referências. Atualize estado/data ao revisar; revisões são sob demanda. Fila não é catálogo de conclusões.

| ID | Estado | Prioridade | Aberto em / revisado em | Trabalho pendente | Dependência / próxima ação | Critério de conclusão |
|---|---|---|---|---|---|---|
| OPEN-001 | BLOCKED | Normal | 2026-10-15 / 2026-10-15 | Comparar este baseline com a especificação/saída de PROMPT-0.2.0. | Arquivo não existe na estrutura inspecionada. Quando disponível, conferir diferenças e atualizar documentos com aprovação apropriada; não presumir seu conteúdo. | Diferenças revisadas e inconsistências resolvidas ou documentadas. |
| OPEN-002 | OPEN | Normal | 2026-10-15 / 2026-10-15 | Executar primeira pesquisa técnica quando houver pergunta priorizada. | Nenhuma pergunta ou evidência técnica fornecida nesta execução. Definir escopo e fontes reais antes de criar `RES`/`KNOW`. | Pesquisa concluída com rastreabilidade; criar KNOW/DEC somente se justificado. |

Não há pesquisas técnicas pendentes específicas identificadas além da ausência de uma pergunta priorizada. Não invente responsáveis ou prazos. Itens concluídos podem permanecer para rastreabilidade ou ser arquivados em `HISTORY.md` com referência.
