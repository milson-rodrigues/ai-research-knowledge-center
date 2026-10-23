# 00_ROTA-DE-CONSULTA (ponto de entrada)

Versão do kit: 1.1.0 | Versão deste arquivo: 2.2

Este arquivo entra nas fontes de **todo** projeto. Ele indica onde estão os modelos, regras, metodologias e skills, o que ler por situação e o que conferir antes de entregar. Os documentos canônicos ficam no repositório; quando esta rota mudar, substitua também a cópia nas fontes de cada projeto.

## Passo 0: onde estão os arquivos

### Modelos, regras e metodologias (repositório do kit)

- **Fonte principal:** `milson-rodrigues/ai-research-knowledge-center`, branch `main` após aprovação e publicação da mudança.
- **Como buscar:** informe o nome completo do repositório e o caminho exato do arquivo.
- **Plano B, só se o app GitHub não estiver disponível ou falhar:** use arquivo de mesmo nome na Biblioteca do ChatGPT ou anexo do usuário; declare o que foi usado e por quê.
- **Sem nenhuma das fontes:** diga qual arquivo faltou e peça o anexo. Não reconstrua modelos nem regras de memória. Não gere prompt sem ler `02_modelos/PROMPT-modelo.md`.
- **Proposta ainda não publicada:** se o usuário pedir para revisar uma branch específica, use a branch indicada e não a trate como versão canônica dos demais projetos.

### Arquivos de estado do projeto (`project-index`, `current-status`, `decisions`)

**Convenção de nome:** `project-index.<nome-projeto>.md`, `current-status.<nome-projeto>.md`, `decisions.<nome-projeto>.md`. Onde `<nome-projeto>` é a sigla ou nome curto do projeto. Ao criar pela primeira vez, confirmar o nome que será adotado.

Ordem de busca obrigatória:

1. **GitHub** — repositório do próprio projeto, no caminho indicado pelo usuário ou registrado no project-index.
2. **Biblioteca do projeto** — se o GitHub não retornar o arquivo ou o app estiver indisponível.
3. **Gerar do template** — se nenhuma fonte retornar estado real: ler o template correspondente em `03_continuidade/`, preencher somente o que é conhecido e entregar o arquivo completo com a nota: _"Arquivo inicializado do template — nenhuma versão anterior foi encontrada. Substitua nas fontes do projeto e confirme para continuar."_

## Rota: leia antes de agir

| Situação | Arquivos (caminho no repositório) | Orientação |
|---|---|---|
| Projeto novo | `02_modelos/kickoff-projeto.md`; `01_instrucoes/playbook-orquestrador.md`; `01_instrucoes/regras-projetos.md` | Kickoff, alternativas e fluxo inicial |
| Decisão de stack, arquitetura, modelo ou método | `02_modelos/kickoff-projeto.md`; `01_instrucoes/playbook-orquestrador.md`; `01_instrucoes/regras-projetos.md` | Comparar alternativas, riscos e dependências |
| **Gerar prompt para executor** | `02_modelos/PROMPT-modelo.md`; `02_modelos/guia-preenchimento-prompt.md`; `02_modelos/regras-prompt.md`; `01_instrucoes/playbook-orquestrador.md`; `02_modelos/modelo-resposta-agente.md` | Ler todos antes de entregar; somar regras de projeto e metodologia relevante quando aplicáveis |
| Escolher metodologia | `05_metodologias/README.md` e o arquivo específico | Aplicar apenas o procedimento pertinente |
| Recomendar skill externa | `04_skills/skills-catalog.md` | Somente skills listadas, com origem e referência fixada |
| Validar resposta do executor | `02_modelos/modelo-resposta-agente.md`; `01_instrucoes/playbook-orquestrador.md`; `02_modelos/regras-prompt.md` | Conferir critérios contra evidências reais |
| Criar ou atualizar arquivos de estado | Templates correspondentes em `03_continuidade/` | Ler e preservar a estrutura do template entregue |
| Bug complexo | `01_instrucoes/playbook-orquestrador.md`; `05_metodologias/diagnostico-bugs.md`; regras pertinentes | Diagnóstico sustentado por evidências antes de corrigir |
| Handoff | `03_continuidade/handoff-novo-chat.md` e templates necessários | Fechar o estado e preparar abertura do próximo chat |

## Bloco CONSULTA (obrigatório)

Abra toda resposta que use esta rota com uma tabela de três colunas:

| Arquivo (caminho) | Fonte | Identificador |
|---|---|---|

- **Fonte:** `GitHub`, `Biblioteca`, `Anexo`, `Gerado do template` ou `Não acessado`.
- **Identificador:** commit ou URL do arquivo, quando disponível. Se não aparecer, escreva `sem identificador`; nunca invente.
- Arquivos `Não acessado` devem ter motivo.
- Um arquivo gerado do template deve identificar o template usado e avisar que o usuário precisa salvar o arquivo nas fontes do projeto.

## Portão obrigatório antes de entregar um prompt

1. Confira o prompt contra `02_modelos/PROMPT-modelo.md`:
   - Títulos de seção idênticos ao modelo: `Header / Metadata`, `Execution Configuration`, `[ROLE]`, `[CONTEXT]`, `[TASK]`, `[AUTHORIZED CHANGES]`, `[CONSTRAINTS]`, `[CRITERIA]`, `[OUTPUT]`, `Expected State`. Não traduzir, renomear ou fundir títulos; o conteúdo pode ser em português.
   - Todos os campos de Header e Execution Configuration presentes; usar `N/A` quando realmente não se aplicar.
   - ID conforme `02_modelos/guia-preenchimento-prompt.md`; o título H1 deve conter o ID completo. `Owner` identifica o responsável real.
   - Modelo e esforço são escolhidos somente entre os disponíveis declarados pelo usuário. Se a informação faltar, pergunte ou use o marcador de confirmação permitido; não invente disponibilidade.
   - `[OUTPUT]` exige o relatório no formato de `02_modelos/modelo-resposta-agente.md`, salvo em `responses/resposta-<ID>.md`. Entregáveis extras não substituem o relatório.
   - Skill externa: somente as do `04_skills/skills-catalog.md` podem ser descritas como aprovadas/aplicadas; outras são apenas candidatas.
2. Consulte `02_modelos/regras-prompt.md` para grounding, autorização, execução por blocos, proteção da codebase, testes, evidências e Quality Gate.
3. Consulte `01_instrucoes/regras-projetos.md` se a tarefa afetar arquitetura, contratos, dependências, dados, segurança, desempenho ou decisões duradouras.
4. Escolha metodologia pertinente em `05_metodologias/`, quando aplicável, e inclua no prompt as etapas essenciais para o executor.
5. Se houver conflito entre documentos, aponte-o e resolva antes de gerar instruções contraditórias.
6. Se algum item falhar, corrija antes de entregar.

## Regras de continuidade

- O estado real do projeto vem de seus arquivos próprios, buscados na ordem definida acima. Templates são modelos, não estado real.
- Entregue arquivos de estado completos, prontos para substituir nas fontes do projeto; não entregue apenas trechos alterados.
- Registre em `decisions` apenas decisões aprovadas. Não transforme propostas em decisões finais.
- O estado de execução distingue `CONCLUÍDO`, `PARCIAL`, `BLOQUEADO` e `FALHOU` conforme as evidências.
- Não declarar que testes passaram se não foram executados e observados.
- Nunca guardar segredos, tokens ou credenciais nos arquivos do kit.
