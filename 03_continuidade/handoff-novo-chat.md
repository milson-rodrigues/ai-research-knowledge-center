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
1. Consulte o guia canônico, este procedimento e apenas os templates necessários.
2. Identifique o ambiente e localize os registros e o índice central no destino real; não misture Biblioteca, fontes do projeto, workspace local e GitHub.
3. No ChatGPT, liste os arquivos relevantes e leia a versão vigente de project-index-vN.md. Se houver ambiguidade de versão, não escolha por suposição.
4. Apresente a seleção de contexto: todos os registros pertinentes, um ou vários registros específicos, o mais recente de um assunto ou somente o estado atual. Leia apenas o que foi selecionado e as dependências necessárias.
5. Crie um registro independente com o próximo número livre da série do assunto, sem sobrescrever ou excluir históricos existentes.
6. Registre objetivo, ponto de encerramento, decisões aprovadas, evidências, testes executados/não executados/bloqueados, pendências, próxima ação e prompt completo para abrir o próximo chat. Não invente estado ausente.
7. Grave o registro e depois liste/busque e releia o conteúdo para confirmar persistência.
8. Atualize o índice: criar a próxima project-index-vN.md a partir do conteúdo integral da versão vigente; registrar versão anterior, data, motivo e mudanças; gravar, reler e validar a nova versão; somente depois excluir a versão anterior; por fim, listar novamente e confirmar que apenas a versão nova permanece.
9. Se qualquer etapa de escrita, leitura de verificação ou exclusão falhar, preserve a última versão comprovadamente válida, marque BLOQUEADO, descreva a etapa exata e forneça o Markdown completo para salvamento manual. Não crie cópias alternativas repetidamente e não declare sucesso sem evidência.
10. Informe os arquivos realmente lidos/criados/alterados/excluídos, o destino e as evidências da verificação.
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


## 5. Seleção de contexto e índice versionado

### 5.1 Catálogo e seleção

O índice `project-index-vN.md` é o catálogo central para os registros de continuidade da Biblioteca do ChatGPT. Cada registro de conversa mantém nome sequencial por assunto, como `project-index-prompt_01.md` e `project-index-bug_01.md`. Esses registros são históricos independentes e não devem ser apagados ao atualizar o índice.

Ao preparar a continuidade, ofereça estas opções:

- todos os registros catalogados pertinentes ao projeto;
- um ou vários registros escolhidos pelo usuário;
- o registro mais recente de um assunto específico;
- somente o estado atual do projeto.

A escolha determina quais históricos serão lidos. Leia também as dependências necessárias, mas não carregue todos os históricos por padrão. Se o índice não catalogar um arquivo que aparece na listagem real, sinalize a divergência antes de confiar no catálogo.

### 5.2 Versionamento

1. Identificar e ler a única versão vigente `project-index-vN.md`.
2. Preparar a próxima versão com número sequencial livre, preservando o conteúdo anterior e alterando somente o necessário.
3. Incluir no arquivo: versão nova, data, versão anterior, motivo, seções modificadas e registros adicionados/removidos.
4. Gravar a nova versão e pesquisar/listar e reler o arquivo persistido.
5. Conferir que o conteúdo anterior relevante foi preservado, que as mudanças estão presentes e que o catálogo corresponde aos registros reais.
6. Somente após a validação, excluir a versão anterior.
7. Listar novamente e confirmar que somente a última versão do índice permanece.

### 5.3 Falhas e proteção contra perda

Se a ferramenta não permitir criação, leitura de verificação ou exclusão, preservar a última versão comprovadamente válida e marcar a operação como `BLOQUEADO`. Descrever o passo que falhou e fornecer o conteúdo completo que precisa ser salvo manualmente. Não presumir que a Biblioteca e as fontes do projeto estão sincronizadas. Não tentar contornar a falha criando indefinidamente arquivos alternativos.

### 5.4 Critério de conclusão

A continuidade só pode ser classificada como concluída quando o registro da conversa e a nova versão do índice tiverem sido lidos de volta com sucesso, o catálogo estiver consistente e a listagem final confirmar que apenas a última versão do índice permanece. Se o registro tiver sido criado, mas a atualização ou exclusão do índice estiver bloqueada, classificar o fluxo como `PARCIAL` ou `BLOQUEADO` e informar a evidência.
