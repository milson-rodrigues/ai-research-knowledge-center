# Metodologia: decomposição de tarefas

## Objetivo

Transformar um objetivo em blocos pequenos, verificáveis e ordenados por dependências, reduzindo risco e facilitando a validação.

## Procedimento

1. **Definir resultado:** declarar o objetivo técnico/de negócio e o que fica fora do escopo.
2. **Inventariar restrições:** contratos, decisões aprovadas, áreas sensíveis e operações proibidas.
3. **Mapear dependências reais:** identificar quais blocos bloqueiam outros; não inventar dependências por conveniência.
4. **Definir blocos:** cada bloco com resultado verificável e escopo autorizado.
5. **Estimar risco e reversibilidade:** considerar dados, autenticação, interfaces públicas, produção, dependências e consumidores.
6. **Ordenar:** cumprir dependências obrigatórias; entre blocos prontos, equilibrar risco, custo, benefício e reversibilidade.
7. **Planejar validação:** associar critérios de aceite, testes e evidências a cada bloco.
8. **Executar por etapas:** validar o estado atual antes de liberar o próximo bloco. Paralelizar apenas com independência comprovada e benefício claro.
9. **Registrar continuidade:** atualizar status, resultados, bloqueios e próxima ação.

## Modelo de bloco

| Campo | Conteúdo |
|---|---|
| ID | `B01`, `B02` etc. |
| Objetivo | Resultado único e verificável |
| Escopo | Incluído e excluído |
| Dependências | IDs predecessores ou `Nenhum` |
| Risco | Impacto e reversibilidade |
| Autorização | Arquivos/áreas e operações permitidas |
| Critérios | Condições objetivas de conclusão |
| Testes/evidências | Como os critérios serão comprovados |
| Interrupção | Condições para bloquear ou pedir autorização |

## Critério de conclusão

Um bloco só é `CONCLUÍDO` quando cada critério possui evidência suficiente, as alterações respeitam a autorização e o estado final corresponde ao esperado. Caso contrário, registrar `PARCIAL`, `BLOQUEADO` ou `FALHOU`, com motivo e próxima ação.
