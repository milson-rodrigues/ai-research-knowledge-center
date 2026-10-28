# Testes de aceitação — CONT-01 e continuidade por ambiente

## Objetivo

Validar primeiro o ciclo funcional principal de continuidade: localizar o destino, criar/ler arquivos válidos, registrar o estado real e retomar o trabalho. Os testes de falha são complementares e não são pré-requisito para utilizar o fluxo normal.

## Estados permitidos

- `CONCLUÍDO`: evidência comprova todos os critérios do cenário.
- `PARCIAL`: parte do cenário passou, mas há etapas pendentes.
- `BLOQUEADO`: ambiente/ferramenta impediu uma etapa necessária.
- `FALHOU`: operação executada, mas resultado incorreto.

## Cenários principais — devem ser priorizados

| ID | Cenário | Procedimento | Critério de aprovação | Estado/evidência |
|---|---|---|---|---|
| CORE-01 | Localizar projeto e destino | Identificar projeto e pasta de continuidade; criar `continuity/` no projeto correto se ausente e suportado | Destino confirmado; ausência não é confundida com falha de acesso; pasta criada no local correto quando possível | Pendente |
| CORE-02 | Criar registro de histórico válido | Consultar template aplicável, registrar fatos do chat, testes, evidências, bugs, decisões, pendências e próximo passo | Arquivo completo, sem fatos inventados, com prompt integral de abertura do próximo chat | Pendente |
| CORE-03 | Persistir e reler histórico | Gravar/publicar o novo registro no ambiente selecionado e abri-lo novamente | Conteúdo persistido, acessível, íntegro e no destino correto | Pendente |
| CORE-04 | Ler contexto para retomar | Ler índice vigente, estado atual, decisões relevantes e históricos pertinentes | Retomada correta, com separação entre fatos confirmados, relatos, hipóteses e pendências; sem carregar todo o histórico por padrão | Pendente |
| CORE-05 | Atualizar estado e índice | Quando o registro mudar o estado ou catálogo, publicar/atualizar os arquivos correspondentes | Estado atual reflete evidências; índice aponta para arquivos reais e versão vigente; decisões aprovadas preservadas | Pendente |
| CORE-06 | Histórico append-only | Criar outro registro sobre o mesmo assunto | Usar próxima sequência livre; não sobrescrever nem remover registros anteriores | Pendente |
| CORE-07 | Adaptadores de persistência | Executar ciclo no ambiente selecionado (Biblioteca, workspace de agente ou GitHub) | Operações correspondem às capacidades reais do ambiente; gravação seguida de releitura | Pendente |
| CORE-08 | Prompt de continuidade | Inspecionar o prompt de abertura incluído no registro | Instrui o próximo chat a ler índice, estado, decisões e históricos necessários antes de agir | Pendente |

## Cenários complementares — falhas e casos-limite

Esses cenários não bloqueiam o uso normal do ciclo principal. Executá-los quando houver oportunidade segura ou quando o plano de teste exigir. Não simular falhas destrutivas sobre a última versão válida.

| ID | Cenário | Procedimento | Critério de aprovação | Estado/evidência |
|---|---|---|---|---|
| AUX-01 | Falha ao criar/publicar | Observar ou testar falha segura de gravação | Preservar última versão válida; marcar a etapa como `BLOQUEADO`; não declarar sucesso | Pendente |
| AUX-02 | Falha de releitura | Não conseguir abrir/validar nova publicação | Não excluir a versão anterior nem afirmar persistência | Pendente |
| AUX-03 | Renomear/excluir indisponível | Verificar capacidade real do ambiente após validar a nova publicação | Preservar versões e indicar claramente a vigente no índice | Pendente |
| AUX-04 | Índice divergente | Comparar índice com arquivos reais | Reportar divergências e não confiar cegamente no catálogo | Pendente |
| AUX-05 | Versões ambíguas | Encontrar múltiplas versões sem status claro | Resolver por evidência ou bloquear a seleção, sem adivinhar | Pendente |

## Registro obrigatório de cada execução

Para cada cenário executado, registrar data, ambiente, projeto/caminho, arquivos consultados, operação, evidência antes/depois, resultado, status e próxima ação. Marcar explicitamente cenários não executados e bloqueados. A existência do procedimento não significa que o teste foi executado.

## Critério de aprovação do ciclo principal

O ciclo principal pode ser considerado `CONCLUÍDO` quando:

1. Projeto e destino foram identificados por evidência.
2. Um histórico completo foi criado a partir de informações sustentadas pelo chat e pelas evidências.
3. O histórico foi persistido e relido no ambiente real.
4. O contexto foi recuperado usando índice, estado atual, decisões relevantes e históricos necessários.
5. O registro contém o prompt completo de abertura do próximo chat.
6. Históricos anteriores foram preservados.
7. Testes executados, não executados e bloqueados estão separados.
8. O índice e o estado foram atualizados quando necessário.

A aprovação do ciclo principal não implica que os cenários complementares de falha foram executados nem que todos os adaptadores foram validados. Cada ambiente deve ser validado separadamente.

