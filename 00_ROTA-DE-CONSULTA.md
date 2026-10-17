# 00_ROTA-DE-CONSULTA (ponto de entrada)

Versão do kit: 1.0.0 | Versão deste arquivo: 2.1

Este arquivo entra nas fontes de **todo** projeto. Ele diz onde estão os modelos, o que ler por situação e o que conferir antes de entregar. Os modelos moram no repositório GitHub; para mudar a rota, edite o mestre no repositório e reenvie este arquivo aos projetos.

## Passo 0: onde estão os arquivos

### Modelos, regras e skills (repositório do kit)

- **Fonte principal:** repositório `milson-rodrigues/ai-research-knowledge-center`, branch `main`. É privado e o acesso é **somente leitura**, pelo app GitHub do ChatGPT.
- **Como buscar:** o seletor de repositórios do app procura só nomes, não conteúdo. Informe o nome completo do repositório e o **caminho exato** do arquivo (coluna "Arquivos" abaixo).
- **Plano B, só se o app GitHub não estiver disponível ou falhar:** arquivo de mesmo nome na Biblioteca do ChatGPT, ou anexo do usuário. Diga que usou o plano B e por quê.
- **Sem nenhuma das fontes:** diga qual arquivo faltou e peça o anexo. Não reconstrua de memória. Não gere prompt sem ter lido `02_modelos/PROMPT-modelo.md`.

### Arquivos de estado do projeto (project-index, current-status, decisions)

**Convenção de nome:** `project-index.<nome-projeto>.md`, `current-status.<nome-projeto>.md`, `decisions.<nome-projeto>.md`  
Onde `<nome-projeto>` é a sigla ou nome curto do projeto (ex.: `IaOpcUaClient`). Ao gerar do template, use o mesmo nome do projeto já em uso; se for o primeiro arquivo, pergunte ao usuário qual nome adotar.

Ordem de busca obrigatória:

1. **GitHub** — repositório do próprio projeto (caminho exato informado pelo usuário ou registrado no project-index).
2. **Biblioteca do projeto** — se o GitHub não retornar o arquivo ou o app não estiver disponível.
3. **Gerar do template** — se nenhuma das fontes acima retornar o arquivo (ou o arquivo for só o template sem estado real): leia o template correspondente em `03_continuidade/` do repositório `milson-rodrigues/ai-research-knowledge-center`, preencha os campos com o que for conhecido neste chat e entregue o arquivo ao usuário com a nota: _"Arquivo inicializado do template — nenhuma versão anterior foi encontrada. Substitua nas fontes do projeto e confirme para continuar."_ Não assuma estado de outros chats ou projetos.


## Rota: leia antes de agir

| Situação | Arquivos (caminho no repositório) | Partes |
|---|---|---|
| Projeto novo | `02_modelos/kickoff-projeto.md`; `01_instrucoes/playbook-orquestrador.md` | Playbook seções 1 a 3 |
| Decisão de stack, arquitetura, modelo ou método | `02_modelos/kickoff-projeto.md`; `01_instrucoes/playbook-orquestrador.md` | Kickoff Parte B; playbook seções 2 e 6 |
| **Gerar prompt para executor** | `02_modelos/PROMPT-modelo.md`; `02_modelos/guia-preenchimento-prompt.md`; `02_modelos/modelo-resposta-agente.md`; `01_instrucoes/playbook-orquestrador.md` | Playbook seções 3 e 4 |
| Recomendar skill | `04_skills/skills-catalog.md` | Somente as listadas, com URL e commit fixado |
| Validar resposta do executor | `02_modelos/modelo-resposta-agente.md`; `01_instrucoes/playbook-orquestrador.md` | Playbook seção 5 |
| **Criar ou atualizar arquivos de estado** (kickoff aprovado, fim de bloco, decisão aprovada, fim de fase) | `03_continuidade/project-index.template.md`; `03_continuidade/current-status.template.md`; `03_continuidade/decisions.template.md` | Ler o template de cada arquivo que vai entregar e manter estrutura e campos |
| Bug complexo | `01_instrucoes/playbook-orquestrador.md` | Seção 6 |
| **Handoff**: fechar fase, chat longo, ou o usuário pedir "gere o handoff", "prompt de continuidade" ou "novo chat" | `03_continuidade/handoff-novo-chat.md` e o template de cada arquivo de estado que será entregue | Seção 2 do handoff, inteira |

## Bloco CONSULTA (obrigatório)

Abra toda resposta que use a rota com uma tabela de três colunas:

| Arquivo (caminho) | Fonte | Identificador |
|---|---|---|

- **Fonte:** `GitHub`, `Biblioteca`, `Anexo`, `Gerado do template` ou `Não acessado`.
- **Identificador:** o commit ou a URL do arquivo no GitHub, quando o app mostrar. Se não mostrar, escreva `sem identificador`. Nunca invente.
- Arquivo `Não acessado` deve vir com o motivo.
- Arquivo `Gerado do template` deve indicar qual template foi usado e que o usuário precisa salvar o arquivo gerado nas fontes do projeto.

## Portão obrigatório antes de entregar um prompt

1. Confira o prompt contra o `PROMPT-modelo.md`:
   - Títulos de seção **idênticos** aos do modelo, sem traduzir, renomear ou fundir: `Header / Metadata`, `Execution Configuration`, `[ROLE]`, `[CONTEXT]`, `[TASK]`, `[AUTHORIZED CHANGES]`, `[CONSTRAINTS]`, `[CRITERIA]`, `[OUTPUT]`, `Expected State`. O conteúdo é em português.
   - Todos os campos de Header e de Execution Configuration presentes; use `N/A` quando não se aplicar.
   - ID pela convenção do `guia-preenchimento-prompt.md`, e o título H1 do prompt com esse mesmo ID completo (não `PROMPT-1.0.0`). `Owner` com o nome do usuário, não um cargo genérico.
   - Modelo e esforço: só os que o usuário declarou (lista "Executores disponíveis" do `project-index.md`). Sem declaração, escreva `[A CONFIRMAR: informe o executor]` e peça a informação na mesma resposta. Não escreva "X ou outro modelo".
   - `[OUTPUT]` exige o relatório do executor no formato de `modelo-resposta-agente.md`, salvo em `responses/resposta-<ID>.md`. Entregáveis extras (por exemplo, de uma auditoria) são adicionais e não substituem esse relatório.
   - Skill: só as do `skills-catalog.md`. Outra pode ser citada como candidata, nunca como aplicada.
2. Se algum item falhar, corrija antes de entregar.

## Regras

- O estado do projeto vem dos arquivos de estado do projeto (`project-index.md`, `current-status.md`, `decisions.md`), buscados na ordem: GitHub do projeto → Biblioteca do projeto → gerado do template. Os `*.template.md` do repositório do kit são modelos, não estado.
- Arquivo de estado gerado do template: entregue ao usuário com a nota _"Arquivo inicializado do template — nenhuma versão anterior foi encontrada. Substitua nas fontes do projeto e confirme para continuar."_ Registre `Gerado do template` no bloco CONSULTA.
- Arquivo de estado entregue: abra com o bloco CONSULTA (template lido), siga o template correspondente e entregue o arquivo **completo**, pronto para substituir o das fontes, nunca só o trecho alterado.
- Pedido de handoff: execute a seção 2 do `handoff-novo-chat.md` sem exigir que o usuário cole o texto longo. Entregue `current-status.md` completo, `decisions.md` e `project-index.md` só se mudaram, e o texto de abertura do próximo chat já preenchido. Lembre o usuário de substituir os arquivos nas fontes do projeto e de abrir o novo chat **dentro do mesmo projeto** antes de colar o texto de abertura.
- O repositório é somente leitura para você: não tente escrever nele nem pedir permissão de escrita.
- Não reconstrua modelos de memória. Se nenhuma fonte der acesso a um arquivo da rota, o prompt que depende dele não pode ser gerado.
