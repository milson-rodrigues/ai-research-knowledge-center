# Testes de aceitação — CONT-01 e continuidade por ambiente

## Objetivo

Validar o fluxo de continuidade separadamente na Biblioteca do ChatGPT, em workspace de agente e no GitHub. Os critérios são especificações, não evidência de execução.

## Estados permitidos

- `CONCLUÍDO`: evidência comprova todos os critérios do cenário.
- `PARCIAL`: parte do cenário passou, mas há etapas pendentes.
- `BLOQUEADO`: o ambiente/ferramenta impediu uma etapa.
- `FALHOU`: a operação foi executada, mas não cumpriu o resultado esperado.

## Preparação

1. Identificar ambiente, projeto e destino real.
2. Listar os arquivos existentes e ler o índice/estado atual, quando acessíveis.
3. Registrar as versões e evidências antes de alterar qualquer arquivo.
4. Usar arquivos de teste descartáveis sempre que possível.
5. Nunca excluir a última versão comprovadamente válida antes de validar a substituta.

## Cenários

| ID | Cenário | Procedimento | Critério de aprovação | Estado/evidência |
|---|---|---|---|---|
| CT-01 | Identificar projeto e destino | Procurar os arquivos de estado no ambiente selecionado | Projeto, caminho e arquivos encontrados documentados; acesso falho não é confundido com inexistência | Pendente |
| CT-02 | Publicar nova versão na Biblioteca | Gerar arquivo completo com nome novo, adicionar, abrir e reler | Nova publicação acessível e completa antes de qualquer alteração à anterior | Pendente |
| CT-03 | Excluir/renomear versão antiga | Após validar a nova, tentar operação se suportada | Se indisponível, preservar ambas e documentar a limitação; nunca perder a versão válida | Pendente |
| CT-04 | Separar estado, decisões, índice e histórico | Inspecionar nomes, funções e referências | Estado atual, decisões aprovadas, catálogo e histórico têm papéis distintos | Pendente |
| CT-05 | Status das publicações | Registrar status no índice | Cada publicação tem status `VIGENTE`, `SUBSTITUÍDO` ou `ARQUIVADO`; uma única vigente por papel quando determinável | Pendente |
| CT-06 | Falha de publicação | Simular ou observar falha de criação | Versão anterior permanece válida; resultado marcado `BLOQUEADO) | Pendente |
| CT-07 | Falha de releitura | Não conseguir abrir/confirmar nova publicação | Não declarar sucesso nem excluir a anterior | Pendente |
| CT-08 | Falha ao excluir/renomear | Operação não suportada ou falha | Manter as versões e tornar inequívoca a vigente no índice | Pendente |
| CT-09 | Atualizar estado em agente/GitHub | Atualizar arquivo canônico e reler | Arquivo no destino correto contém a atualização; diff preserva conteúdo fora do escopo | Pendente |
| CT-10 | Histórico imutável | Criar novo registro de conversa | Histórico anterior não é sobrescrito nem removido | Pendente |
| CT-11 | Carregamento mínimo de contexto | Iniciar continuidade a partir do estado vigente | Lê estado e decisões relevantes; consulta histórico adicional apenas quando necessário | Pendente |
| CT-12 | Seleção explícita de históricos | Solicitar um ou vários registros | Somente os selecionados e dependências necessárias são lidos | Pendente |
| CT-13 | Índice divergente dos arquivos | Comparar catálogo com listagem real | Divergência é reportada antes de confiar no catálogo | Pendente |
| CT-14 | Versões ambíguas | Apresentar duas versões candidatas sem status claro | Não escolher por suposição; bloquear ou solicitar evidência para resolver | Pendente |
| CT-15 | Prompt de abertura | Gerar e usar o prompt de handoff | Próxima ação, bloqueios e decisões são confirmados a partir das fontes disponíveis | Pendente |
| CT-16 | Relatório final | Consolidar execução | Separa testes executados, não executados e bloqueados, com evidências | Pendente |

## Registro obrigatório de cada execução

Para cada cenário, registrar:

- Data e ambiente.
- Projeto e caminho consultados.
- Arquivos lidos e operação executada.
- Evidência antes/depois (conteúdo relido, captura ou identificador do commit).
- Resultado observado.
- Estado: `CONCLUÍDO`, `PARCIAL`, `BLOQUEADO) ou `FALHOU`.
- Próxima ação para cenários não concluídos.

## Critério de aprovação do fluxo completo

1. O projeto e o destino são identificados por evidência.
2. Na Biblioteca, a nova publicação é adicionada e relida antes de alterar a anterior.
3. Se não houver suporte para excluir/renomear, as versões permanecem e o índice identifica a vigente.
4. Estado atual, decisões, índice e histórico são separados.
5. O índice explicita status e referências de versão.
6. A versão anterior permanece válida se a nova não puder ser lida de volta.
7. O contexto inicial usa estado atual e decisões relevantes, sem carregar todo o histórico por padrão.
8. Os registros históricos não são sobrescritos ou excluídos.
9. Testes são executados separadamente por ambiente; aprovação em um ambiente não comprova os demais.

Nenhum cenário deve ser marcado como executado apenas porque seu procedimento está documentado.
