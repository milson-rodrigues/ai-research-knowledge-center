# Handoff para novo chat

Este procedimento é usado pelo fluxo `CONT-01`. O destino dos registros depende do ambiente: Biblioteca no ChatGPT quando houver suporte de leitura/gravação, workspace do projeto para agentes locais e repositório/branch selecionados para GitHub. Não presuma sincronização entre Biblioteca e fontes do projeto.

## 1. Quando abrir um chat novo

- Uma fase/bloco foi fechado.
- Muitos blocos no mesmo chat (referência: 5 a 8) ou respostas lentas, repetitivas ou contraditórias.
- Lentidão do navegador por chat longo.
- É necessário preservar o estado antes de mudar de conversa ou executor.

## 2. No chat atual, antes de fechar

Use o seguinte pedido ou execute diretamente quando a intenção do usuário já estiver clara:

~~~
Prepare o fechamento desta conversa conforme CONT-01.
1. Consulte somente o guia canônico, este procedimento e os templates realmente necessários.
2. Localize o estado e os registros de continuidade existentes no ambiente selecionado.
3. Crie um registro independente para esta conversa, sem sobrescrever registros anteriores. No ChatGPT, use a Biblioteca acessível e um nome sequencial como project-index-prompt_01.md, project-index-bug_01.md ou project-index-continuidade_01.md, escolhendo o próximo número livre após verificar os arquivos existentes. Em agente local, grave no workspace do projeto; no GitHub, no repositório e branch explicitamente selecionados.
4. Registre objetivo, ponto de encerramento, decisões aprovadas, evidências, testes executados/não executados/bloqueados, pendências e próxima ação. Não invente estado ausente.
5. Inclua o prompt completo para abrir o próximo chat e validar o estado antes de continuar.
6. Grave o arquivo e depois pesquise/list e releia o conteúdo para confirmar persistência. Não declare sucesso antes da verificação.
7. Se não houver capacidade de gravação, marque a gravação como BLOQUEADO e entregue o Markdown completo para salvamento manual.
8. Informe arquivos realmente lidos/criados/alterados e a localização de destino.
~~~

No ChatGPT, não exija substituir as fontes do projeto para cada conversa se o registro puder ser salvo e lido diretamente na Biblioteca. Não alegue que a Biblioteca e as fontes estão sincronizadas.

## 3. Prompt de abertura do próximo chat

O registro de continuidade deve incluir um prompt completo, preenchido, semelhante a:

~~~
Novo chat do projeto [NOME] (sigla [SIGLA]), continuação da conversa registrada em [ARQUIVO].
1. Leia o registro de continuidade e os arquivos de estado acessíveis no ambiente correto.
2. Confirme em até 5 linhas: fase atual, último bloco concluído, bloco em andamento, bloqueios e próxima ação.
3. Aponte inconsistências entre o registro e os arquivos atuais antes de prosseguir.
4. Não trate hipóteses como fatos nem refaça trabalho já comprovado.
5. Aguarde confirmação apenas se houver decisão pendente que altere materialmente a execução; caso contrário, prossiga dentro do escopo autorizado.
~~~

## 4. Critério de gravação por ambiente

- **ChatGPT:** procurar e ler a Biblioteca acessível; criar registro separado quando a ferramenta permitir; pesquisar e reler após a gravação. Fontes do projeto são separadas e não devem ser tratadas como cópia sincronizada.
- **Agentes locais:** gravar no workspace real e reler o arquivo.
- **GitHub:** conferir repositório, branch e caminho; criar registro sem sobrescrever o histórico; confirmar o conteúdo remoto após commit.
- **Sem escrita disponível:** fornecer o Markdown completo e marcar a gravação como BLOQUEADO.

O handoff só está concluído quando o registro estiver persistido e verificado, ou quando o bloqueio de gravação estiver claramente documentado.
