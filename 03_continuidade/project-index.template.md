# project-index.md: [NOME DO PROJETO]

Catálogo e ponto de entrada do projeto. Este arquivo fica nas **fontes do projeto**. Atualizado em: [YYYY-MM-DD] | Versão do kit em uso: [1.0.0] | Versão da rota em uso: [2.0]

## 1. Identificação

- **Sigla (para IDs de prompt):** [SIGLA]
- **Objetivo:** [uma frase]
- **Usuários / público:** [quem]
- **Fase atual:** [Discovery | MVP | Evolução | Manutenção]
- **Repositório / local do código:** [link ou caminho]

## 2. Fontes e arquivos canônicos

| Arquivo | Onde fica | Função |
|---|---|---|
| project-index.md | Fontes do projeto | Este catálogo |
| current-status.md | Fontes do projeto | Estado atual |
| decisions.md | Fontes do projeto | Decisões aprovadas |
| 00_ROTA-DE-CONSULTA.md | Fontes do projeto | Ponto de entrada: rota de consulta (versão [x.y]) |
| PROMPT-modelo.md | Repositório GitHub (opcional nas fontes, como seguro) | Modelo de prompt |
| skills-catalog.md | Repositório GitHub, `04_skills/` | Índice de skills aprovadas |
| kit-operacional.md | Opcional: fontes do projeto, só como fallback | Playbook e modelos (versão [x.y.z]) |

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

[Referências ao `skills-catalog.md`, com versão fixada]

## 8. Glossário (opcional)
