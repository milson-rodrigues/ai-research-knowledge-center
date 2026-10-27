# Testes de aceitação — CONT-01 e continuidade por ambiente

## Objetivo

Validar separadamente a continuidade na Biblioteca do ChatGPT, em workspace de agente e no GitHub. Os critérios abaixo não significam que os testes foram executados.

## Estados permitidos

- `CONCLUÍDO`: evidência comprova todos os critérios do cenário.
- `PARCIAL`: parte do cenário passou, mas há etapas pendentes.
- `BLOQUEADO`: ambiente/ferramenta impediu uma etapa necessária.
- `FALHOU`: operação executada, mas resultado incorreto.

## Preparação

1. Identificar projeto, ambiente e destino real.
2. Listar arquivos existentes e ler índice/estado atuais, quando acessíveis.
3. Registrar versões e evidências antes de alterar arquivos.
4. Preferir arquivos de teste descartáveis.
5. Nunca excluir a última versão comprovadamente válida antes de validar a substituta.

## Cenários de aceitação

| ID | Cenário | Procedimento | Critério de aprovação | Estado/evidência |
|---|---|---|---|---|
| CT-01 | Identificar projeto e destino | Localizar projeto e pasta `continuidade`; se o projeto existir e a subpasta estiver ausente, criá-la no local correto e confirmar sua presença | Projeto e caminho confirmados; subpasta criada quando ausente e suportada; falha de acesso não é confundida com inexistência | Pendente |
| CT-02 | Publicar versão na Biblioteca | Criar arquivo completo com nome novo, adicionar e reler | Nova publicação acessível e completa antes de alterar a anterior | Pendente |
| CT-03 | Renomear/excluir versão anterior | Após validar a nova, tentar a operação se suportada | Se indisponível, preservar ambas e registrar a limitação no índice | Pendente |
| CT-04 | Separar estado e histórico | Inspecionar papéis dos arquivos | Estado, decisões, catálogo e históricos têm responsabilidades distintas | Pendente |
| CT-05 | Status de publicação | Registrar status no índice | Status `VIGENTE`, `SUBSTITUÍDO` ou `ARQUIVADO`; uma vigente por papel quando determinável | Pendente |
| CT-06 | Falha ao criar versão | Simular ou observar falha de gravação | Versão anterior preservada; operação marcada `BLOQUEADO` | Pendente |
| CT-07 | Falha de releitura | Não conseguir abrir/validar nova publicação | Não declarar sucesso nem excluir versão anterior | Pendente |
| CT-08 | Falha ao excluir/renomear | Operação indisponível ou falha | Manter ambas; índice identifica a vigente; sem cópias de contorno | Pendente |
| CT-09 | Atualização em agente/GitHub | Atualizar arquivo canônico e reler | Destino correto, conteúdo persistido e alterações delimitadas | Pendente |
| CT-10 | Histórico imutável | Criar novo registro de conversa | Históricos anteriores não são sobrescritos ou removidos | Pendente |
| CT-11 | Carregamento mínimo | Retomar a partir do estado vigente | Ler estado e decisões relevantes; buscar histórico adicional somente quando necessário | Pendente |
| CT-12 | Seleção de históricos | Escolher um ou mais registros | Ler apenas selecionados e dependências necessárias | Pendente |
| CT-13 | Índice divergente | Comparar catálogo com arquivos reais | Divergências reportadas antes de confiar no catálogo | Pendente |
| CT-14 | Versões ambíguas | Apresentar múltiplas versões sem status claro | Não escolher por suposição; resolver por evidência ou bloquear | Pendente |
| CT-15 | Prompt de abertura | Gerar e usar o handoff | Próxima ação, bloqueios e decisões confirmados nas fontes disponíveis | Pendente |
| CT-16 | Relatório final | Consolidar a execução | Separar testes executados, não executados e bloqueados com evidências | Pendente |

## Registro obrigatório de cada execução

Para cada cenário, registrar data, ambiente, projeto/caminho, arquivos consultados, operação executada, evidência antes/depois, resultado, status e próxima ação.

## Critério de aprovação do fluxo completo

1. Projeto e destino identificados por evidência.
2. Na Biblioteca, nova publicação completa é adicionada e relida antes de alterar a anterior.
3. Se não houver suporte a exclusão/renomeação, versões antigas permanecem e o índice declara a vigente.
4. Estado atual, decisões, índice e histórico têm papéis separados.
5. O índice registra status e referências de versão.
6. Se a nova publicação não puder ser lida, a versão anterior permanece válida.
7. O contexto inicial usa estado e decisões relevantes, sem carregar todo o histórico por padrão.
8. Históricos não são sobrescritos nem removidos.
9. Testes são executados separadamente por ambiente; aprovação em um não comprova os demais.

Não marque um cenário como executado apenas porque seu procedimento está documentado.


### Regra de criação para CT-01

A ausência de `continuidade/` dentro de uma pasta de projeto identificada não é, por si só, um bloqueio. O executor deve criar a subpasta no projeto correto quando a plataforma permitir e verificar que ela existe. Em seguida, deve inspecionar os arquivos necessários e criar os que estiverem ausentes a partir dos templates aplicáveis, identificando claramente arquivos iniciais. É bloqueio somente se o projeto/destino não puder ser identificado ou a operação necessária não estiver disponível. Nunca criar uma pasta substituta em outro local.