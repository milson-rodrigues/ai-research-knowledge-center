# 00_ROTA-DE-CONSULTA (ponto de entrada)

Versão do kit: 1.0.0 | Versão deste arquivo: 1.3

Este arquivo entra nas fontes de **todo** projeto. Ele diz o que ler, em que ordem e o que conferir antes de entregar. Para mudar a rota, edite o mestre e reenvie aos projetos.

## Passo 0: acesso

Os arquivos da rota ficam na Biblioteca, pasta "ai-research-knowledge-center" (subpasta entre parênteses). Procure pelo **nome do arquivo**. Se não achar ou não conseguir abrir, diga qual arquivo faltou e peça o anexo. Não gere prompt sem ter lido `PROMPT-modelo.md`.

## Rota: leia antes de agir

| Situação | Arquivos (subpasta) | Partes |
|---|---|---|
| Projeto novo | `kickoff-projeto.md` (02_modelos); `playbook-orquestrador.md` (01_instrucoes) | Playbook seções 1 a 3 |
| Decisão de stack, arquitetura, modelo ou método | `kickoff-projeto.md` (02_modelos); `playbook-orquestrador.md` (01_instrucoes) | Kickoff Parte B; playbook seções 2 e 6 |
| **Gerar prompt para executor** | `PROMPT-modelo.md`; `guia-preenchimento-prompt.md` (02_modelos); `playbook-orquestrador.md` (01_instrucoes) | Playbook seções 3 e 4 |
| Recomendar skill | `skills-catalog.md` (04_skills) | Somente as listadas, com URL e commit fixado |
| Validar resposta do executor | `modelo-resposta-agente.md` (02_modelos); `playbook-orquestrador.md` (01_instrucoes) | Playbook seção 5 |
| **Criar ou atualizar arquivos de estado** (kickoff aprovado, fim de bloco, decisão aprovada, fim de fase) | `project-index.template.md`, `current-status.template.md`, `decisions.template.md` (03_continuidade) | Ler o template de cada arquivo que vai entregar e manter estrutura e campos |
| Bug complexo | `playbook-orquestrador.md` (01_instrucoes) | Seção 6 |
| **Handoff**: fechar fase, chat longo, ou o usuário pedir "gere o handoff", "prompt de continuidade" ou "novo chat" | `handoff-novo-chat.md` (03_continuidade) e o template de cada arquivo de estado que será entregue | Seção 2 do handoff, inteira |

## Portão obrigatório antes de entregar um prompt

1. Abra a resposta com o bloco **CONSULTA**: arquivos lidos e arquivos que não conseguiu acessar.
2. Confira o prompt contra o `PROMPT-modelo.md`:
   - Títulos de seção **idênticos** aos do modelo, sem traduzir, renomear ou fundir: `Header / Metadata`, `Execution Configuration`, `[ROLE]`, `[CONTEXT]`, `[TASK]`, `[AUTHORIZED CHANGES]`, `[CONSTRAINTS]`, `[CRITERIA]`, `[OUTPUT]`, `Expected State`. O conteúdo é em português.
   - Todos os campos de Header e de Execution Configuration presentes; use `N/A` quando não se aplicar.
   - ID pela convenção do `guia-preenchimento-prompt.md`.
   - Modelo e esforço: só os que o usuário declarou ter. Se não souber, pergunte.
   - Skill: só as do `skills-catalog.md`. Outra pode ser citada como candidata, nunca como aplicada.
3. Se algum item falhar, corrija antes de entregar.

## Regras

- O estado do projeto vem das fontes do projeto (`project-index.md`, `current-status.md`, `decisions.md`), nunca desta pasta. Os `*.template.md` em `03_continuidade` são modelos, não estado.
- Arquivo de estado entregue: abra com o bloco CONSULTA (template lido), siga o template correspondente e entregue o arquivo **completo**, pronto para substituir o das fontes, nunca só o trecho alterado.
- Pedido de handoff: execute a seção 2 do `handoff-novo-chat.md` sem exigir que o usuário cole o texto longo. Entregue `current-status.md` completo, `decisions.md` e `project-index.md` só se mudaram, e o texto de abertura do próximo chat já preenchido. Lembre o usuário de substituir os arquivos nas fontes do projeto e de abrir o novo chat **dentro do mesmo projeto** antes de colar o texto de abertura.
- Não reconstrua modelos de memória. Se o arquivo da rota não estiver acessível, o prompt não pode ser gerado.
