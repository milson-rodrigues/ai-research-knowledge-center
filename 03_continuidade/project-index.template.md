# project-index.md: [NOME DO PROJETO]

Catálogo e ponto de entrada do projeto. Em workspace/GitHub pode ser atualizado como arquivo canônico; na Biblioteca, publicar uma nova versão completa do índice e preservar a anterior até validar a nova. Atualizado em: [YYYY-MM-DD]

- **Versão/publicação:** [vNN]
- **Status desta publicação:** [VIGENTE | SUBSTITUÍDO | ARQUIVADO]
- **Versão anterior:** [nome/versão ou "nenhuma"]
- **Motivo da publicação:** [..]

- **Sigla (para IDs de prompt):** [SIGLA]
- **Fonte canônica do kit:** `milson-rodrigues/ai-research-knowledge-center`, branch `main`, consultada sob demanda.
- **Bootstrap nas fontes do projeto:** `00_ROTA-DE-CONSULTA.md` — instalado uma vez; não precisa ser atualizado em mudanças comuns do kit.

## 1. Identificação

- **Objetivo:** [uma frase]
- **Usuários / público:** [quem]
- **Fase atual:** [Discovery | MVP | Evolução | Manutenção]
- **Repositório / local do código:** [link ou caminho]

## 2. Fontes e arquivos canônicos

| Arquivo | Onde fica | Função | Status da publicação |
|---|---|---|---|
| project-index.md / project-index-vN.md | Biblioteca, fontes do projeto ou repositório do projeto | Catálogo vigente; na Biblioteca, usar publicação versionada | VIGENTE / SUBSTITUÍDO / ARQUIVADO |
| current-status.md / current-status-vNN.md | Biblioteca, fontes do projeto ou repositório do projeto | Estado real da execução; na Biblioteca, publicação versionada | VIGENTE / SUBSTITUÍDO / ARQUIVADO |
| decisions.md | Biblioteca, fontes do projeto ou repositório do projeto | Decisões aprovadas | VIGENTE / SUBSTITUÍDO / ARQUIVADO |
| 00_ROTA-DE-CONSULTA.md | Fontes do projeto ChatGPT | Bootstrap permanente; aponta para `00_GUIA-DE-CONFIGURACAO.md` |
| 00_GUIA-DE-CONFIGURACAO.md | Repositório do kit, branch `main` | Índice operacional canônico e mutável; aliases, fluxos e dependências |
| 01_instrucoes/rota-operacional.md | Repositório do kit, branch `main` | Ponte estável para o guia canônico; não mantém uma árvore separada |
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
