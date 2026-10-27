# Handoff para novo chat

Este procedimento é usado pelo fluxo `CONT-01`. A estrutura lógica de continuidade é compartilhada entre ambientes, mas a persistência deve respeitar as operações reais disponíveis. Não presuma sincronização entre Biblioteca, fontes do projeto, workspace local e GitHub.

## 1. Quando abrir um chat novo

- Uma fase ou bloco foi fechado.
- O chat ficou longo, repetitivo, lento ou contraditório.
- É necessário preservar o estado antes de mudar de conversa ou executor.

## 2. No chat atual, antes de fechar

Execute diretamente quando a intenção estiver clara:

1. Consulte o guia canônico, este procedimento e apenas os templates necessários.
2. Identifique o projeto e o ambiente de destino. Não presuma que existe uma pasta na Biblioteca; procure evidências.
3. Leia o estado atual e as decisões relevantes acessíveis. Consulte históricos apenas quando forem necessários para esclarecer decisões, evidências, dependências ou contradições.
4. Registre objetivo, estado confirmado, decisões aprovadas, evidências, testes executados/não executados/bloqueados, pendências, riscos e próxima ação.
5. Crie um arquivo histórico novo em `continuity/chat-<assunto>-<NN>.md`, usando a próxima sequência livre. Nunca sobrescreva registros históricos.
6. Prepare o conteúdo completo do estado atual e do índice, conforme as alterações necessárias.
7. Persista de acordo com o ambiente:
   - **Biblioteca do ChatGPT:** gere uma nova publicação completa com nome versionado; adicione-a; abra/relê e valide-a; só depois tente renomear ou excluir a versão anterior, se a plataforma permitir. Se não permitir, mantenha ambas e declare os status no índice.
   - **Agente local:** atualize os arquivos canônicos no workspace real e releia-os.
   - **GitHub:** atualize os arquivos canônicos na branch explicitamente selecionada, crie um novo histórico de conversa quando necessário e releia o conteúdo remoto.
8. Valide referências, preservação de decisões e integridade do histórico.
9. Informe os arquivos realmente lidos, criados, atualizados, excluídos e verificados. Se uma operação falhar, preserve a última versão válida e classifique a etapa como `PARCIAL` ou `BLOQUEADO`.

## 3. Prompt de abertura do próximo chat

Inclua no registro de continuidade um prompt preenchido, semelhante a:

```text
Novo chat do projeto [NOME] (sigla [SIGLA]), continuação do registro [ARQUIVO].

1. Consulte o índice vigente e leia o estado atual e as decisões relevantes no ambiente correto.
2. Confirme em até 5 linhas: fase atual, último bloco concluído, bloco em andamento, bloqueios e próxima ação.
3. Aponte inconsistências entre o registro e os arquivos atuais antes de prosseguir.
4. Consulte históricos adicionais somente se forem necessários para esclarecer uma dependência, decisão, evidência ou contradição.
5. Não trate hipóteses como fatos nem refaça trabalho já comprovado.
6. Prossiga dentro do escopo autorizado; pergunte apenas se uma decisão pendente alterar materialmente a execução.
```

## 4. Regras de publicação por ambiente

### 4.1 Biblioteca do ChatGPT

A Biblioteca funciona como repositório de publicações, não como um sistema de edição concorrente.

1. Identifique os arquivos existentes e leia o índice vigente quando acessível.
2. Gere um arquivo completo com nome de versão novo, por exemplo `current-status-v03.md`, `project-index-v03.md` ou `chat-continuidade-04.md`.
3. Adicione a publicação.
4. Abra/relê o arquivo e verifique conteúdo completo, referências e versão.
5. Só depois tente renomear ou excluir a versão anterior, se a plataforma permitir.
6. Se não for possível renomear ou excluir, mantenha as duas versões e marque claramente no índice `VIGENTE`, `SUBSTITUÍDO` ou `ARQUIVADO`.
7. Se a nova publicação não puder ser lida de volta, a versão anterior continua válida. Não declare sucesso.
8. Se não houver capacidade de escrita, entregue o Markdown completo e marque a persistência como `BLOQUEADO`.

Não carregue todos os históricos por padrão. Comece pelo estado atual e pelas decisões relevantes.

### 4.2 Agentes locais

- Confirme o workspace e o caminho antes de editar.
- Atualize os arquivos canônicos existentes; não gere cópias de estado sem necessidade.
- Preserve históricos e decisões anteriores.
- Releia os arquivos após gravar.

### 4.3 GitHub

- Confirme repositório, branch e caminho.
- Inspecione os arquivos atuais antes de alterar.
- Atualize `current-status.md`, `decisions.md) e o índice canônico diretamente, conforme necessário.
- Crie um novo arquivo de histórico para cada fechamento que deva ser preservado.
- Releia os arquivos remotos e verifique o diff após o commit. Não grave em `main` quando uma branch de trabalho tiver sido selecionada.

## 5. Modelo lógico dos arquivos

- `current-status.md`: estado operacional atual, próxima ação, testes e bloqueios.
- `decisions.md`: decisões aprovadas; decisões substituídas permanecem identificadas.
- `project-index-vN.md`: catálogo versionado na Biblioteca. Cada entrada contém nome, papel, status, versão/data quando aplicável e referência à versão substituta.
- `continuity/chat-<assunto>-<NN>.md`: histórico imutável de cada conversa.

Cada papel lógico deve ter uma única publicação `VIGENTE) quando houver evidência suficiente. O índice deve identificar as versões `SUBSTITUÍDO) e `ARQUIVADO). Se houver ambiguidade que não possa ser resolvida pelos arquivos disponíveis, interrompa a retomada e registre `BLOQUEADO`.

## 6. Critério de conclusão

A continuidade só pode ser classificada como `CONCLUÍDO` quando os arquivos necessários tiverem sido persistidos e verificados no ambiente real. Se parte da operação foi concluída, mas a publicação, releitura ou atualização do índice ficou pendente, use `PARCIAL). Se a plataforma impediu uma etapa necessária, use `BLOQUEADO`. Se a operação executada produziu resultado incorreto, use `FALHOU`.

Sempre diferencie testes executados, não executados e bloqueados. Não declare que um arquivo foi criado, alterado ou lido sem evidência.
