# Guia operacional — AI Research Knowledge Center

**Este é o índice operacional canônico e mutável do kit.** O fluxo, o roteamento de intenções, os caminhos de consulta e os critérios de execução são mantidos aqui. Os arquivos de bootstrap e rota são estáveis e apontam para este guia; não duplicam a lógica operacional.

- **Repositório:** `milson-rodrigues/ai-research-knowledge-center`
- **Branch canônica:** `main`
- **Este índice:** `00_GUIA-DE-CONFIGURACAO.md`
- **Bootstrap nas fontes do projeto:** `00_ROTA-DE-CONSULTA.md`
- **Instrução estável do projeto:** `01_instrucoes/rota-operacional.md`

## 1. Princípios operacionais

1. Classifique a intenção antes de consultar documentos.
2. Consulte este guia como índice e leia somente o fluxo selecionado e suas dependências obrigatórias.
3. Não percorra todos os documentos do repositório em toda solicitação.
4. Não leia um documento apenas porque ele existe; leia-o quando o fluxo o exigir.
5. Registre em `CONSULTA` somente arquivos realmente lidos, com caminho, fonte e commit/URL quando disponíveis.
6. Se uma dependência obrigatória não puder ser acessada, marque a etapa dependente como `BLOQUEADO`; não substitua silenciosamente a fonte por memória, cópia antiga ou Biblioteca.
7. Preserve decisões aprovadas e contratos do projeto. Não invente conteúdo, testes, resultados ou arquivos.
8. Não altere os arquivos de bootstrap estável durante tarefas comuns. Mudanças de fluxo são feitas neste guia ou nos documentos especializados autorizados.
9. Leia apenas o contexto específico do projeto que seja necessário para a intenção atual.
10. Se duas intenções forem necessárias, combine os fluxos mínimos e elimine leituras duplicadas.

## 2. Comandos de entrada e aliases

Os comandos abaixo são **aliases textuais do protocolo**, não comandos nativos garantidos em todas as plataformas. Quando o usuário digitar um deles, encaminhe para o fluxo correspondente. Também classifique pedidos em linguagem natural pelo mesmo índice.

| Alias | Intenção | Fluxo |
|---|---|---|
| `/continuidade` | Preparar continuidade, gerar prompt de continuidade, handoff ou preparar ambiente para novo chat | `CONT-01` |
| `/projeto` | Criar/iniciar projeto ou executar kickoff | `PROJ-01` |
| `/prompt` | Gerar somente um prompt executável sem solicitar execução | `PROMPT-01` |
| `/bug` | Investigar ou corrigir bug | `BUG-01` |
| `/validar` | Validar saída/execução de agente com evidências | `VALID-01` |
| `/arquitetura` | Avaliar arquitetura, stack, contratos ou trade-offs | `ARCH-01` |
| `/pesquisa` | Pesquisa técnica, metodologia ou avaliação de skill | `RES-01` |
| `/estado` | Consultar estado, decisões, pendências ou próxima ação | `STATE-01` |

### Regras dos aliases

- O assunto prevalece sobre o alias genérico. `/prompt continuidade` segue `CONT-01`; `/prompt bug` segue `BUG-01`.
- `/prompt` sozinho segue `PROMPT-01`.
- `@Continuidade` só deve ser tratado como menção a uma skill/agente quando essa skill/agente existir e estiver disponível na plataforma. Não suponha que `@...` seja um mecanismo universal.
- Se a plataforma não oferecer comandos ou menções nativas, os aliases continuam utilizáveis como texto na mensagem.
- Não pergunte novamente por informações já identificadas de forma inequívoca no contexto atual.

## 3. Índice de fluxos

| ID | Fluxo | Arquivo(s) base a consultar sob demanda | Saída |
|---|---|---|---|
| `CONT-01` | Continuidade e handoff | Seção 4 deste guia; `03_continuidade/handoff-novo-chat.md`; templates de continuidade aplicáveis | Arquivos de estado/handoff e/ou prompt de abertura |
| `PROJ-01` | Criação de projeto | `02_modelos/kickoff-projeto.md`; `01_instrucoes/playbook-orquestrador.md`; regras de projeto conforme o caso | Perguntas indispensáveis, dossiê, decisões pendentes e plano |
| `PROMPT-01` | Somente gerar prompt | `02_modelos/PROMPT-modelo.md`; `02_modelos/guia-preenchimento-prompt.md`; `02_modelos/regras-prompt.md`; `01_instrucoes/playbook-orquestrador.md`; `02_modelos/modelo-resposta-agente.md`; regras/metodologia somente se aplicáveis | Um prompt completo pronto para copiar |
| `BUG-01` | Investigar/corrigir bug | Dependências de `PROMPT-01` e `05_metodologias/diagnostico-bugs.md`; prompt, relatório, diff e logs disponíveis | Diagnóstico por evidências e prompt de investigação/correção |
| `VALID-01` | Validar execução | `02_modelos/modelo-resposta-agente.md`; prompt original; relatório, diff, logs e testes disponíveis | Status verificado, evidências, lacunas e próxima ação |
| `ARCH-01` | Arquitetura/stack/tecnologia | `01_instrucoes/regras-projetos.md`; playbook; documentação oficial atual pertinente | Alternativas, trade-offs, riscos e recomendação |
| `RES-01` | Pesquisa/metodologia/skill | `05_metodologias/README.md` e arquivo específico; para skills, `04_skills/skills-catalog.md` | Síntese fundamentada, limites e recomendação |
| `STATE-01` | Estado/decisões/pendências | Arquivos reais do projeto: `project-index.<projeto>.md`, `current-status.<projeto>.md`, `decisions.<projeto>.md` | Estado confirmado, inconsistências e próxima ação |

Os caminhos da tabela são referências para consulta seletiva, não uma lista a ser lida integralmente em cada solicitação. Se um fluxo não precisar de um documento opcional, não o leia.

## 4. Fluxo CONT-01 — continuidade

### 4.1 Classificar a operação

Diferencie:
- **Preparar ambiente:** localizar e preparar os arquivos necessários no destino escolhido.
- **Gerar prompt de continuidade:** produzir somente o prompt de transferência, sem escrever arquivos se não for necessário.
- **Fechar/handoff do chat atual:** atualizar o estado a partir do contexto e das evidências atuais, gerar os arquivos completos e o texto de abertura do próximo chat.
- **Continuar em novo chat:** ler os arquivos de estado disponíveis e confirmar o ponto de retomada antes de prosseguir.

Se a intenção for inequívoca, não pergunte qual operação é. Se a diferença alterar materialmente as ações e não puder ser inferida, faça uma pergunta objetiva.

### 4.2 Selecionar o ambiente

Use três categorias:

1. **Chats de IA** — ChatGPT, Claude ou outro produto de conversa.
2. **Agentes de IA** — agentes que trabalham num workspace/diretório de projeto, por exemplo Claude Code, Codex ou equivalente.
3. **GitHub** — destino remoto explicitamente selecionado, com repositório, branch e caminho.

Não confunda o provedor/modelo com o armazenamento. Identifique o produto e consulte a documentação necessária para saber onde os arquivos podem ser lidos ou escritos.

### 4.3 Resolver origem, destino e modelo de persistência

A continuidade mantém quatro papéis lógicos, independentemente do ambiente:

- `current-status.md`: fotografia do estado atual confirmado; atualizável.
- `decisions.md`: decisões aprovadas e seu histórico; não registrar recomendações como decisões aprovadas.
- `project-index-vN.md`: catálogo versionado dos registros e dos arquivos vigentes.
- `continuity/chat-<assunto>-<NN>.md`: registro imutável de cada conversa encerrada, incluindo o prompt completo para o próximo chat.

Use nomes de assunto claros e sequências livres. Exemplos: `chat-prompt-bug_01.md`, `chat-prompt-prompt_01.md`. Antes de criar um registro, pesquise/listar os arquivos da série e escolha o próximo número disponível. Nunca sobrescreva um histórico anterior.

#### Chats de IA e Biblioteca do ChatGPT

- Trate a Biblioteca como armazenamento separado e repositório de publicações; não presuma sincronização com fontes do Projeto, workspace ou GitHub.
- Identifique o projeto e a pasta de destino. Se a subpasta `continuity/` não existir e a plataforma permitir, crie-a dentro do projeto correto e confirme sua presença.
- Para um novo histórico, crie um arquivo completo com nome novo, publique-o e releia-o para confirmar persistência e integridade.
- Para atualizar estado ou índice, publique uma nova versão física, releia e valide-a antes de tentar renomear/excluir a anterior. Se a plataforma não permitir renomear/excluir, mantenha as versões e marque inequivocamente `VIGENTE`, `SUBSTITUÍDO` ou `ARQUIVADO` no índice vigente.
- Se a escrita não estiver disponível, entregue o Markdown completo e marque somente a persistência não realizada como `BLOQUEADO`. Nunca declare publicação sem evidência de releitura.

#### Agentes de IA

- Confirme o workspace real e inspecione os arquivos atuais antes de editar.
- Atualize diretamente `current-status.md` e o índice canônico quando apropriado; preserve o histórico de decisões e crie novos registros de conversa.
- Releia os arquivos gravados para verificar persistência.

#### GitHub

- Confirme repositório, branch e caminhos; inspecione os arquivos existentes antes de alterar.
- Atualize os arquivos vigentes diretamente na branch autorizada e adicione históricos em novos arquivos.
- Releia os arquivos remotos e verifique o diff/commit. Não altere `main) quando uma branch de teste estiver selecionada.

### 4.4 Identificar projeto e arquivos

1. Inferir o projeto somente quando houver evidência suficiente; se houver ambiguidade material, perguntar.
2. Localizar a pasta real do projeto e a pasta de continuidade no ambiente selecionado.
3. Distinguir pasta ausente de pasta inacessível.
4. Se o projeto estiver identificado e `continuity/` estiver ausente, criá-la no local correto quando a plataforma permitir; confirmar a criação antes de publicar arquivos. Nunca criar em um destino alternativo.
5. Localizar os templates e os arquivos de estado/histórico existentes. Não inventar registros nem assumir que o índice representa perfeitamente os arquivos reais.

### 4.5 Ciclo funcional de continuidade

O fluxo principal é **localizar → ler → retomar → registrar → publicar → reler → atualizar índice/estado**. Testes de falha são complementares e não são pré-requisito para executar o ciclo normal.

#### Ao iniciar ou continuar um chat

1. Ler o índice vigente e `current-status.md` (ou a publicação física vigente na Biblioteca).
2. Ler `decisions.md) para decisões relevantes ao trabalho atual.
3. Selecionar e ler históricos pertinentes, seguindo referências do índice. Não carregar todo o histórico por padrão; consultar registros adicionais quando houver dependências, bugs, decisões, evidências ou contradições a esclarecer.
4. Comparar o resumo com as evidências e os arquivos atuais acessíveis. Distinguir fatos verificados, relatos, hipóteses e pendências.
5. Confirmar fase, último trabalho comprovado, testes executados/não executados/bloqueados e próxima ação. Só então prosseguir.

#### Ao encerrar uma conversa relevante

1. Consultar `03_continuidade/handoff-novo-chat.md` e somente os templates necessários.
2. Registrar fatos confirmados, mudanças realizadas, evidências, bugs, decisões aprovadas, testes executados/não executados/bloqueados, pendências, riscos e próxima ação.
3. Incluir o prompt completo de abertura do próximo chat, com instrução explícita para ler o índice, o estado, decisões relevantes e históricos necessários.
4. Criar um novo arquivo `continuity/chat-<assunto>-<NN>.md), sem sobrescrever históricos existentes.
5. Publicar/gravar o arquivo no destino real e relê-lo integralmente, ou com verificação suficiente para confirmar todo o conteúdo, integridade e referências.
6. Atualizar `current-status.md) se o estado confirmado mudou. Atualizar o índice se foram adicionados registros, alterados estados ou modificadas referências. Preservar o histórico das decisões aprovadas.
7. Na Biblioteca, publicar versões físicas novas para estado/índice quando necessário; validar a nova publicação antes de tentar remover/renomear a anterior. Se remoção/renomeação não for suportada, manter versões identificadas no índice.
8. Informar exatamente o que foi lido, criado, atualizado e verificado. Se uma operação falhar, preservar a última versão válida e marcar a etapa como `PARCIAL` ou `BLOQUEADO`.

### 4.6 Regras de integridade

- Históricos de conversa são append-only: um novo fechamento gera novo arquivo; não se reescrevem nem removem históricos antigos na manutenção rotineira.
- `current-status.md` é uma fotografia operacional atualizável, não um substituto dos históricos.
- `decisions.md` preserva decisões aprovadas e registra quando uma decisão é substituída, com referência à sucessora quando disponível.
- O índice cataloga os arquivos reais, seu papel, data/versão, status e relações entre versões. Deve indicar claramente o arquivo vigente para cada papel lógico.
- Se o estado real não existir, criar um estado inicial explicitamente identificado como inicial; não inventar histórico de execução.
- Não declarar sucesso sem evidência de persistência e releitura.
- Falhas ao criar, reler, renomear ou excluir são testes complementares. Não impedem o uso normal quando o ciclo de criação e leitura funciona; devem ser registradas quando ocorrerem naturalmente ou forem testadas deliberadamente.

### 4.7 Saída mínima

A resposta de `CONT-01` registra ambiente/projeto, caminhos consultados, arquivos realmente lidos/criados/atualizados, evidências de releitura, estado confirmado, pendências e prompt de continuidade. Se o usuário pedir somente um prompt, não realizar gravações desnecessárias.

## 5. Fluxos especializados

### PROJ-01 — criar projeto

1. Consultar o kickoff e o playbook.
2. Perguntar somente requisitos que alterem arquitetura, escopo, segurança, custo ou critérios de aceite.
3. Apresentar alternativas e decisões pendentes; não tratar recomendação como decisão aprovada.
4. Após as aprovações necessárias, preparar o plano de blocos e os arquivos iniciais conforme os templates.
5. Quando houver implementação, usar as dependências de `PROMPT-01`.

### PROMPT-01 — gerar somente um prompt

1. Ler `02_modelos/PROMPT-modelo.md`, `02_modelos/guia-preenchimento-prompt.md`, `02_modelos/regras-prompt.md`, `01_instrucoes/playbook-orquestrador.md` e `02_modelos/modelo-resposta-agente.md`.
2. Ler regras de projeto e metodologia somente quando o escopo exigir.
3. Inspecionar o estado específico do projeto se a tarefa depender dele.
4. Perguntar apenas dados indispensáveis que alterem a execução.
5. Entregar um único prompt completo, mantendo a estrutura do modelo. Não executar o trabalho solicitado pelo prompt.

### BUG-01 — investigar/corrigir bug

1. Consultar `05_metodologias/diagnostico-bugs.md` e as dependências de `PROMPT-01`.
2. Inspecionar erro, logs, reprodução, diff e relatório disponíveis.
3. Separar causa comprovada de hipótese. Se a causa não estiver comprovada, preparar investigação antes de prescrever correção.
4. Delimitar a correção mínima e os testes necessários.

### VALID-01 — validar execução

1. Comparar o prompt original, relatório do agente, mudanças e evidências.
2. Classificar como `CONCLUÍDO`, `PARCIAL`, `BLOQUEADO` ou `FALHOU`.
3. Não declarar conclusão apenas com base no relato do executor.
4. Atualizar arquivos de continuidade somente com fatos verificados.

### ARCH-01 — arquitetura/stack

1. Consultar regras de projeto e documentação oficial atual relevante.
2. Comparar alternativas, trade-offs, risco, custo e manutenção.
3. Recomendar uma opção e explicitar as decisões que dependem de aprovação.
4. Não executar mudanças de alto impacto sem autorização.

### RES-01 — pesquisa/metodologia/skill

1. Consultar o índice especializado e somente os documentos pertinentes.
2. Diferenciar fatos, inferências e recomendações.
3. Para skills, usar `04_skills/skills-catalog.md`; candidatas não são skills aprovadas.
4. Pesquisar fontes atuais quando a pergunta envolver tecnologia ou informação mutável.

### STATE-01 — estado/decisões

1. Procurar os arquivos de estado reais no local registrado pelo projeto.
2. Não usar o estado de outro chat/projeto nem reconstruir decisões por memória.
3. Identificar divergências entre índice, status e decisões.
4. Informar próxima ação com base no estado confirmado.

## 6. Montagem comum de prompt executável

Quando `PROJ-01`, `BUG-01` ou outro fluxo precisar de um prompt de execução, reutilize as dependências de `PROMPT-01` sem reler arquivos já consultados na mesma solicitação.

O prompt deve conter objetivo, contexto, alterações autorizadas/proibidas, restrições, critérios de aceite, testes, evidências esperadas e estado final esperado. Inclua instruções críticas no próprio prompt; não dependa somente de links externos.

## 7. Consulta, desempenho e bloqueios

- Abra respostas de planejamento, prompt, validação, arquitetura e continuidade com uma tabela `CONSULTA`.
- Registre apenas arquivos efetivamente lidos e o identificador disponível.
- Reutilize conteúdo já consultado na mesma solicitação, desde que seja da mesma versão e a fonte esteja identificada.
- Não execute varreduras gerais do repositório para um fluxo específico.
- Se o GitHub ou um arquivo obrigatório estiver indisponível, marque a etapa dependente como `BLOQUEADO` e indique o caminho.
- Não declare inexistência quando o acesso falhou.
- Não afirme que uma fonte do ChatGPT foi alterada automaticamente. Verifique a capacidade real de escrita; se não existir, entregue arquivos para importação manual.

## 8. Testes de aceitação do roteador

| ID | Entrada | Resultado esperado |
|---|---|---|
| T01 | `/continuidade` | Executa apenas `CONT-01` e suas dependências |
| T02 | `/prompt continuidade` | Encaminha para `CONT-01`, não para o fluxo genérico |
| T03 | `/prompt` | Executa `PROMPT-01` e entrega somente o prompt |
| T04 | `/bug` sem causa comprovada | Diagnóstico antes de correção prescritiva |
| T05 | `/validar` com relatório sem evidências | Não marca `CONCLUÍDO` |
| T06 | `/continuidade` com pasta inexistente | Informa caminho pesquisado e bloqueia preparação dependente |
| T07 | `/continuidade` no ambiente ChatGPT | Procura na Biblioteca e fontes acessíveis; cria registro independente na Biblioteca quando houver suporte; relê para verificar; se gravação indisponível, marca `BLOQUEADO` e entrega Markdown completo |
| T11 | Índice com várias versões candidatas | Não escolhe arbitrariamente; verifica evidências ou bloqueia com a inconsistência descrita |
| T12 | Seleção de um ou mais registros | Lê apenas os selecionados e as dependências necessárias |
| T13 | Publicação versionada na Biblioteca | Cria nova publicação completa, relê e valida; tenta renomear/excluir a anterior apenas depois, se suportado; caso contrário, mantém ambas e declara status no índice |
| T14 | Falha ao excluir/renomear versão antiga | Mantém ambas as publicações, declara uma `VIGENTE` e a outra `SUBSTITUÍDO`, sem criar cópias de contorno |
| T15 | Atualização completa na Biblioteca | Confirma que a nova publicação foi relida, que o índice identifica uma única versão `VIGENTE` por papel e que históricos continuam intactos; versões antigas podem permanecer |
| T08 | Pedido de arquitetura | Não consulta templates de continuidade sem necessidade |
| T09 | Continuidade + correção de bug | Combina `CONT-01` e `BUG-01`, sem repetir dependências |
| T10 | Menção `@Continuidade` sem skill disponível | Trata como texto comum e usa o roteador |

Estes são critérios de aceitação; só devem ser marcados como executados após testes reais.

## 9. Referências

- [README do repositório](README.md)
- [Templates e handoff](03_continuidade/handoff-novo-chat.md)
- [Modelo de prompt](02_modelos/PROMPT-modelo.md)
- [Guia de preenchimento](02_modelos/guia-preenchimento-prompt.md)
- [Regras de prompt](02_modelos/regras-prompt.md)
- [Playbook do orquestrador](01_instrucoes/playbook-orquestrador.md)
- [Diagnóstico de bugs](05_metodologias/diagnostico-bugs.md)
- [Catálogo de skills](04_skills/skills-catalog.md)
