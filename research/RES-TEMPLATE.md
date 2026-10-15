# Contrato e template de pesquisa (`RES`)

Uma pesquisa registra uma atividade e seus resultados no escopo declarado; não implica que exista uma conclusão generalizável, decisão ou unidade KNOW. Use `RES-###` estável e revisão semântica `rN`. Lifecycle: `PLANNED|ACTIVE|COMPLETED|BLOCKED|CANCELLED`. `COMPLETED` significa encerramento da atividade, mesmo quando inconclusiva.

## Template

```markdown
# RES-### — [Título]

- Revision: r1
- Lifecycle: PLANNED
- Created: YYYY-MM-DD
- Updated: YYYY-MM-DD
- Reviewed: YYYY-MM-DD or not yet reviewed
- Question and scope:
- Context / versions:
- Method:
- Sources: SRC-### (or none)
- Findings (observations):
- Inferences (with reasoning):
- Conclusion: (including inconclusive)
- Confidence, if a conclusion is stated: LOW | MEDIUM | HIGH — rationale
- Limitations / conflicts:
- Next action / blocker:
- Related records: KNOW-###@rN / DEC-###@rN (if any)
- Semantic revision note:
```

Registre fontes no arquivo canônico `sources/SOURCES.md`. Diferencie resultados observados, inferências e recomendações. Se lifecycle `BLOCKED`, indique dependência e próxima ação. Não crie KNOW ou DEC automaticamente; só crie se a evidência e necessidade justificarem. Sem conclusão, não atribua confiança à pesquisa como se fosse validação.
