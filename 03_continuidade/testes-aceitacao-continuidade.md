# Testes de aceitação — CONT-01 e índice versionado

## Objetivo

Verificar por evidências o fluxo de continuidade, a seleção de registros e o versionamento do índice central no ambiente de teste. Os critérios abaixo não significam que os testes já foram executados.

## Estados permitidos

- `CONCLUÍDO`: evidência comprova todos os critérios do cenário.
- `PARCIAL`: parte do cenário passou, mas há etapas pendentes.
- `BLOQUEADO`: o ambiente/ferramenta impediu a execução de uma etapa.
- `FALHOU`: a operação foi executada, mas não cumpriu o resultado esperado.

## Preparação

1. Identificar explicitamente o ambiente de teste e o caminho real de armazenamento.
2. Listar os arquivos existentes antes de qualquer alteração.
3. Ler o índice vigente e registrar sua versão, identificador e conteúdo.
4. Não executar exclusões se não existir uma cópia nova verificada.
5. Usar arquivos de teste descartáveis sempre que possível. Não usar registros reais do usuário como dados de teste sem necessidade.

## Cenários

| ID | Cenário | Procedimento | Critério de aprovação | Estado/evidência |
|---|---|---|---|---|
| CT-01 | Descobrir índice vigente | Listar os arquivos e ler o índice | Uma única versão vigente identificada; se houver ambiguidade, bloqueio explícito | Pendente |
| CT-02 | Comparar catálogo e arquivos | Comparar entradas do índice com registros existentes | Divergências reportadas; nenhum arquivo inventado | Pendente |
| CT-03 | Selecionar um registro | Escolher um registro específico | Só o registro escolhido e dependências necessárias são lidos | Pendente |
| CT-04 | Selecionar vários registros | Escolher duas ou mais entradas | Contexto consolidado sem perder diferenças ou decisões conflitantes | Pendente |
| CT-05 | Selecionar todos | Escolher todos os registros pertinentes | Todos os registros catalogados pertinentes são considerados; não varre o kit inteiro sem necessidade | Pendente |
| CT-06 | Selecionar último de um assunto | Solicitar o mais recente de uma série | Identifica a sequência mais alta real e verifica o arquivo | Pendente |
| CT-07 | Criar registro de continuidade | Criar o próximo número livre da série | Registro independente criado sem sobrescrita e relido | Pendente |
| CT-08 | Gerar nova versão | Copiar o índice vigente para o próximo número e documentar mudanças | Conteúdo anterior relevante preservado e mudanças explicitadas | Pendente |
| CT-09 | Verificar antes de excluir | Reler a nova versão antes de remover a antiga | Exclusão só ocorre após validação integral da nova versão | Pendente |
| CT-10 | Excluir versão antiga | Excluir a versão anterior após validação | Exclusão confirmada e listagem final mostra somente a versão mais nova | Pendente |
| CT-11 | Falha ao criar nova versão | Simular ou identificar falha de gravação | Versão antiga permanece; operação marcada BLOQUEADO | Pendente |
| CT-12 | Falha ao excluir antiga | Simular ou identificar falha de exclusão | Não alegar sucesso; documentar que duas versões permanecem e interromper novas atualizações | Pendente |
| CT-13 | Falha de releitura | Impedir ou não conseguir verificar o conteúdo novo | Não excluir versão antiga; classificar BLOQUEADO | Pendente |
| CT-14 | Integridade do histórico | Comparar os registros de conversa antes e depois | Nenhum registro histórico removido ou sobrescrito pelo versionamento do índice | Pendente |
| CT-15 | Reabrir novo chat | Usar o prompt de abertura gerado | Próxima ação, bloqueios e decisões confirmados a partir dos arquivos | Pendente |
| CT-16 | Relatório final | Consolidar os resultados | Distingue testes executados, não executados e bloqueados com evidências | Pendente |

## Registro obrigatório de cada execução

Para cada cenário, registrar:
- data e ambiente;
- arquivo(s) consultado(s);
- operação executada;
- evidência de leitura antes/depois;
- resultado observado;
- estado: `CONCLUÍDO`, `PARCIAL`, `BLOQUEADO` ou `FALHOU`;
- próxima ação para cenários não concluídos.

## Critério de aprovação do fluxo completo

O fluxo completo só passa se:
1. a seleção de contexto respeitar a escolha do usuário;
2. o registro de continuidade for criado e relido;
3. a nova versão do índice for criada, relida e validada;
4. a versão antiga só for excluída depois da validação;
5. a listagem final mostrar apenas a última versão do índice;
6. os registros de conversa permanecerem intactos;
7. falhas forem relatadas sem alegações de sucesso.

Executar e registrar os cenários separadamente para GitHub, Biblioteca do ChatGPT e qualquer outro ambiente. A aprovação em um ambiente não comprova os demais.
