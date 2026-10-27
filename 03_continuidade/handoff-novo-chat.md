# Handoff para novo chat

Procedimento do fluxo `CONT-01`. A estrutura lógica é compartilhada, mas a persistência depende das capacidades reais do ambiente. Não presuma sincronização entre Biblioteca, fontes do projeto, workspace local e GitHub.

## 1. Quando abrir um chat novo

- Um bloco/fase foi concluído.
- O chat ficou longo, repetitivo, lento ou contraditório.
- É necessário preservar o estado antes de mudar de conversa ou executor.

## 2. Fechamento da conversa

1. Consulte o guia canônico, este procedimento e apenas os templates necessários.
2. Identifique o projeto e o ambiente real. Não presuma a existência de pasta ou arquivo sem evidência.
3. Leia o estado atual, o índice vigente e as decisões relevantes, quando acessíveis. Consulte históricos apenas quando necessários para resolver dependências, evidências, decisões ou contradições.
4. Registre fatos confirmados, decisões aprovadas, evidências, testes executados/não executados/bloqueados, pendências, riscos, próxima ação e prompt completo de abertura do próximo chat.
5. Crie um novo histórico em `continuity/chat-<assunto>-<NN>.md`, usando a próxima sequência livre. Nunca sobrescreva ou exclua históricos anteriores como parte da continuidade.
6. Valide conteúdo, referências e coerência com o estado atual.
7. Persista conforme o ambiente abaixo. Não declare sucesso sem evidência de gravação e releitura.

## 3. Publicação por ambiente

### 3.1 Chats de IA e Biblioteca do ChatGPT

A Biblioteca funciona como repositório de publicações, não como sistema de edição concorrente.

1. Leia o registro e o índice atuais, se estiverem acessíveis.
2. Gere um arquivo completo atualizado com nome de versão/sequência novo, por exemplo `current-status-v03.md`, `project-index-v03.md` ou `chat-continuidade-04.md`.
3. Adicione o arquivo à Biblioteca.
4. Abra/relê a publicação e confirme que está acessível e completa.
5. Somente depois, tente renomear ou excluir a versão anterior, se a plataforma permitir.
6. Se não for possível renomear/excluir, mantenha as versões e registre no índice `VIGENTE`, `SUBSTITUÍDO` ou `ARQUIVADO`. Deve haver uma única publicação vigente por papel lógico quando for possível determiná-la.
7. Se a nova versão não puder ser lida de volta, a anterior continua sendo a fonte válida. Não a exclua nem declare sucesso.
8. Se não houver ferramenta de escrita, entregue o Markdown completo e marque a persistência como `BLOQUEADO`.

Modelo lógico:
- `current-status.md`: estado operacional atual. Na Biblioteca, a publicação física pode ter sufixo de versão, por exemplo `current-status-v03.md`.
- `decisions.md`: decisões aprovadas; recomendações não aprovadas não entram como decisões.
- `project-index-vN.md`: catálogo versionado e ponto de entrada.
- `continuity/chat-<assunto>-<NN>.md`: histórico imutável de cada conversa.

O índice deve declarar o nome do arquivo, papel, versão/data quando aplicável, status e referência à versão substituta/anterior. Não carregue o histórico completo por padrão: comece pelo estado vigente e pelas decisões relevantes.

### 3.2 Agentes locais

- Confirme o workspace e o caminho antes de editar.
- Leia o arquivo atual e o template aplicável.
- Atualize diretamente os arquivos canônicos existentes, preservando conteúdo fora do escopo.
- Crie um novo arquivo de histórico para cada fechamento relevante.
- Releia os arquivos após gravar.

### 3.3 GitHub

- Confirme repositório, branch e caminhos.
- Inspecione o estado atual antes de editar.
- Atualize os arquivos canônicos diretamente na branch selecionada.
- Preserve históricos; crie um novo arquivo em `continuity/` quando houver novo registro.
- Releia os arquivos remotos e confira o diff após gravar. Não faça alterações em `main` quando houver uma branch de trabalho selecionada.

## 4. Prompt de abertura do próximo chat

Inclua no registro um prompt completo, preenchido, semelhante a:

```text
Continue o projeto [NOME], usando o registro [ARQUIVO].
1. Consulte o índice vigente, o estado atual e as decisões relevantes no ambiente correto.
2. Confirme fase, último bloco concluído, bloco em andamento, bloqueios e próxima ação.
3. Identifique divergências entre o registro e os arquivos atuais antes de prosseguir.
4. Consulte históricos adicionais apenas quando forem necessários para esclarecer dependências, decisões, evidências ou contradições.
5. Não trate hipóteses como fatos nem refaça trabalho comprovado.
6. Prossiga dentro do escopo autorizado; pergunte apenas quando uma decisão pendente alterar materialmente a execução.
```

## 5. Falhas e estados

- `CONCLUÍDO`: persistência e releitura verificadas; critérios do cenário atendidos.
- `PARCIAL`: parte do trabalho foi realizada, mas restam etapas.
- `BLOQUEADO`: ferramenta ou ambiente impediu uma etapa necessária.
- `FALHOU`: a operação foi executada, mas o resultado não cumpriu os critérios.

Se criação, atualização, releitura, renomeação ou exclusão falhar, preserve a última versão comprovadamente válida, identifique a operação exata e entregue o conteúdo completo para ação manual quando necessário.

## 6. Critério de conclusão

A continuidade só está concluída quando os arquivos necessários foram persistidos e verificados no ambiente real. Na Biblioteca, a permanência de versões antigas é aceitável quando a plataforma não permite removê-las, desde que o índice identifique inequivocamente a publicação vigente. Registre separadamente testes executados, não executados e bloqueados.
