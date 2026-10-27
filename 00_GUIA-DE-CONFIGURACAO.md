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

### 4.3 Resolver origem e destino

A persistência deve respeitar as operações efetivamente disponíveis em cada ambiente. A estrutura lógica é comum, mas o método de publicação não é.

#### Chats de IA e Biblioteca do ChatGPT

Trate a Biblioteca como um repositório de publicações: arquivos podem ser adicionados, renomeados ou excluídos conforme os recursos disponíveis, mas não presuma edição direta como em um sistema de arquivos.

- Identifique o projeto e procure os arquivos de continuidade acessíveis. Não afirme que existe uma pasta ou arquivo sem evidência.
- A estrutura lógica esperada é:
  - `current-status.md`: estado operacional atual;
  - `decisions.md`: decisões aprovadas;
  - `project-index-vN.md`: catálogo versionado;
  - `continuity/chat-<assunto>-<NN>.md`: histórico imutável por conversa.
- Ao atualizar um documento na Biblioteca, gere um arquivo completo com nome de versão/sequência nova, por exemplo `current-status-v03.md` ou `chat-continuidade-04.md`. Adicione a nova publicação e confirme que está acessível e completo antes de tentar renomear ou excluir a versão anterior.
- Se não for possível excluir ou renomear a versão antiga, mantenha as versões e registre no índice qual é `VIGENTE), `SUBSTITUÍDO) ou `ARQUIVADO). Não permita duas versões declaradas vigentes para o mesmo papel.
- Nunca exclua a última versão comprovadamente válida antes de validar a substituta. Se a nova publicação não puder ser lida de volta, a anterior continua sendo a fonte válida.
- Não presuma que Biblioteca e fontes do projeto sejam sincronizadas. Se a plataforma não oferecer leitura ou escrita, entregue o conteúdo completo e marque a etapa como `BLOQUEADO).

#### Agentes de IA

- Identifique o workspace real do projeto antes de escrever.
- Leia o arquivo atual e o template aplicável; preserve contratos e conteúdo fora do escopo.
- Atualize diretamente os arquivos canônicos existentes, sem criar versões paralelas desnecessárias.
- Crie um novo registro em `continuity/chat-<assunto>-<NN>.md` para cada fechamento que deva integrar o histórico imutável.
- Releia os arquivos gravados e valide o resultado. Não declare sucesso sem evidência.

#### GitHub

- Confirme repositório, branch e caminhos antes de alterar.
- Inspecione os arquivos atuais e atualize os arquivos canônicos diretamente na branch autorizada.
- Preserve os registros históricos; não crie uma nova versão de `current-status.md` ou `decisions.md` a cada sessão sem uma necessidade explícita.
- Use commits como histórico de alterações do estado canônico. Para registros de conversa que devam ser imutáveis, crie um novo arquivo em `continuity/`.
- Após gravar, releia os arquivos remotos e confira o diff. Não faça commit em `main` quando houver branch de trabalho definida.

O ambiente selecionado determina onde procurar e salvar. Não troque silenciosamente de ambiente nem use outra origem como fallback.

### 4.4 Identificar o projeto e localizar os arquivos

1. Inferir o nome do projeto somente quando houver evidência suficiente no contexto.
2. Se houver ambiguidade entre projetos, perguntar qual é o correto.
3. Localizar a pasta real de continuidade no ambiente selecionado.
4. Distinguir pasta inexistente de pasta inacessível.
5. Se a pasta não existir, informar o ambiente e o caminho consultado; não criar uma pasta substituta sem autorização e sem previsão no procedimento.
6. Identificar os templates e arquivos existentes antes de copiar ou renomear.

### 4.5 Preparar e validar

1. Consultar este guia, `03_continuidade/handoff-novo-chat.md` e apenas os templates pertinentes à operação.
2. Identificar o ambiente e o destino real. Listar ou pesquisar os arquivos existentes antes de criar ou substituir qualquer publicação.
3. Distinguir os quatro papéis: estado atual, decisões aprovadas, índice/catalogação e histórico de conversa. Não usar um registro histórico como substituto automático do estado atual.
4. Para a Biblioteca, publicar uma nova versão completa com nome novo; depois, abrir/ler a nova publicação e verificar conteúdo e referências. Somente após validação, tentar renomear ou excluir a anterior, se a plataforma permitir. Se não permitir, manter ambas e atualizar o índice para declarar o status de cada uma.
5. Para agentes locais e GitHub, atualizar os arquivos canônicos no local selecionado e reler o conteúdo gravado. No GitHub, conferir branch, commit e diff.
6. Criar um novo arquivo histórico para o fechamento de conversa, sem sobrescrever históricos existentes. Usar sequência livre e registrar somente fatos confirmados, decisões aprovadas, evidências, testes executados/não executados/bloqueados, pendências, próxima ação e prompt de abertura do próximo chat.
7. Carregar por padrão apenas o estado vigente e as decisões relevantes. Consultar registros históricos somente quando forem necessários para esclarecer dependências, evidências, decisões ou contradições.
8. Validar a integridade das referências do índice e a preservação do conteúdo anterior relevante.
9. Se a criação, leitura de verificação, atualização, renomeação ou exclusão falhar, preservar a última versão comprovadamente válida, marcar a etapa como `BLOQUEADO` ou `PARCIAL`, informar a operação exata e entregar o conteúdo completo para ação manual quando necessário.
10. Informar exatamente o que foi lido, criado, atualizado, excluído, verificado ou bloqueado. Não declarar persistência sem evidência.

### 4.6 Arquivos de estado, publicações e índice

Diferencie os papéis lógicos dos nomes físicos de publicação:

- **Estado atual:** `current-status.md`. Em agentes/GitHub, é o arquivo canônico atualizável. Na Biblioteca, a publicação física pode ter sufixo de versão, como `current-status-v03.md`; o índice deve apontar para a publicação vigente.
- **Decisões:** `decisions.md). Contém somente decisões aprovadas. Decisões substituídas permanecem registradas com status e referência à decisão sucessora.
- **Índice:** `project-index-vN.md) na Biblioteca, com versões publicadas; em workspace/GitHub, pode existir um índice canônico atualizável conforme a estrutura do projeto.
- **Histórico:** `continuity/chat-<assunto>-<NN>.md`. Cada registro de conversa é independente e imutável; não é removido durante a manutenção do índice.

Cada entrada do índice deve registrar nome do arquivo, papel, versão/data quando aplicável, status `VIGENTE`, `SUBSTITUÍDO` ou `ARQUIVADO`, e referência à publicação substituta/anterior quando houver. Deve existir exatamente uma publicação `VIGENTE` por papel lógico, sempre que houver evidência suficiente para determinar isso.

Na Biblioteca, se não for possível mudar o status dentro de um arquivo antigo, registre a substituição no novo índice vigente. Não presuma que seja possível editar metadados da publicação.

Em qualquer ambiente, decisões entram em `decisions.md` somente após aprovação. Se o estado real não existir, criar um estado inicial claramente identificado, sem simular histórico. A exclusão de uma versão anterior é opcional e condicionada à validação da nova; preservar duas versões identificadas é preferível a perder a última publicação válida.

### 4.7 Saída mínima

A resposta final de `CONT-01` deve registrar:
- ambiente e projeto;
- localização consultada e resultado da busca;
- arquivos lidos, criados e alterados;
- prompt de continuidade;
- bloqueios ou operações manuais restantes.

Se o pedido for apenas gerar o prompt, não execute gravações desnecessárias.

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
