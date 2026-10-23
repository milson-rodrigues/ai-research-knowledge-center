# project-index.md: [NOME DO PROJETO]

Catálogo e ponto de entrada do projeto. Este arquivo fica nas **fontes do projeto**. Atualizado em: [YYYY-MM-DD]

- **Sigla (para IDs de prompt):** [SIGLA]
- **Fonte canônica do kit:** `milson-rodrigues/ai-research-knowledge-center`, branch `main`, consultada sob demanda.
- **Bootstrap nas fontes do projeto:** `00_ROTA-DE-CONSULTA.md` — instalado uma vez; não precisa ser atualizado em mudanças comuns do kit.

## 1. Identificação

- **Objetivo:** [uma frase]
- **Usuários / público:** [quem]
- **Fase atual:** [Discovery | MVP | Evolução | Manutenção]
- **Repositório / local do código:** [link ou caminho]

## 2. Fontes e arquivos canônicos

| Arquivo | Onde fica | Função |
|---|---|---|
| project-index.md | Fontes do projeto ou repositório do projeto | Este catálogo |
| current-status.md | Fontes do projeto ou repositório do projeto | Estado real da execução |
| decisions.md | Fontes do projeto ou repositório do projeto | Decisões aprovadas |
| 00_ROTA-DE-CONSULTA.md | Fontes do projeto ChatGPT | Bootstrap permanente; aponta para a rota operacional atual no GitHub |
| 01_instrucoes/rota-operacional.md | Repositório do kit, branch `main` | Árvore dinâmica consultada sob demanda, sem cópia no projeto |
| PROMPT-modelo.md | Repositório do kit, `02_modelos/` | Modelo de prompt atual |
| skills-catalog.md | Repositório do kit, `04_skills/` | Índice de skills e referências aprovadas |
| kit-operacional.md | Repositório do kit, branch `main` | Snapshot consolidado para auditoria; não é a fonte canônica nem precisa ser copiado para as fontes do projeto |

## 3. Stack aprovada (resumo)

Apenas referências: [D-001 plataforma], [D-002 linguagem], ... Detalhes em `decisions.md`.

## 4. Mapa de blocos

| Bloco | Objetivo | Depende de | Prompt ID | Status |
|---|---|---|---|---|
| B01 | [..] | n/a | [..] | Planejado / Em andamento / Concluído / Bloqueado |

## 5. Convenções

- Nome de prompts: `PROMPT-<SIGLA>-<NNN>-<semver>`
- Relatórios dos agentes: `responses/resposta-<ID>.md`
- Estrutura de pastas do repositório: [resumo]
- Padrões de código e nomes a preservar: [lista]

## 6. Executores disponíveis

| Executor (IA/agente) | Modelos | Observações / limites |
|---|---|---|

## 7. Skills em uso neste projeto

[Referências a skills aprovadas no `skills-catalog.md`, com versão/commit fixado]

## 8. Glossário (opcional)
