# Contrato e template de conhecimento (`KNOW`)

Cada `KNOW-###` é uma unidade reutilizável com escopo e condições explícitos. IDs não mudam; revisão semântica começa em `r1` e incrementa apenas quando o significado/validade material muda. Preserve revisões anteriores por histórico ou snapshot identificável.

Lifecycle: `DRAFT|ACTIVE|SUPERSEDED|WITHDRAWN|BLOCKED`. Validation state: `UNASSESSED|IN_PROGRESS|VALIDATED|REJECTED|REVALIDATION_REQUIRED`. Somente lifecycle `ACTIVE` com validation `VALIDATED` é conhecimento central validado. Confiança independente: `LOW|MEDIUM|HIGH`.

## Template

```markdown
# KNOW-### — [Título]

- Revision: r1
- Lifecycle: DRAFT
- Validation state: UNASSESSED
- Confidence: LOW | MEDIUM | HIGH — rationale, or not assessed
- Created: YYYY-MM-DD
- Updated: YYYY-MM-DD
- Reviewed: YYYY-MM-DD or not yet reviewed
- Next review / trigger: on demand; specify known trigger
- Scope and question:
- Conclusion:
- Applicability / prerequisites:
- Do not apply when:
- Claims and evidence:
  - Claim:
  - Sources: SRC-### (exact version/commit and locator)
  - Evidence strength and rationale:
- Source reliability and limitations:
- Conflicts / counterevidence:
- Assumptions, risks, and limitations:
- Validation review: reviewer/authority, date, criteria checked, outcome
- Revalidation triggers / pending work:
- Replaces / supersedes / related: KNOW-###@rN, RES-###@rN, DEC-###@rN
- Consumer adaptations: link/reference only; adaptations remain local
- Semantic revision note:
```

Para `VALIDATED`, cumpra integralmente os critérios e transições de `DECISIONS.md`. Ausência de informação é marcada como `unknown` ou pendência, nunca preenchida por suposição. Evidência conflitante material, fonte essencial inválida ou escopo ambíguo impede validação da afirmação afetada. Se somente parte das afirmações estiver sustentada, restrinja explicitamente a conclusão/escopo ou mantenha validação pendente.
