# Modelo de resposta do agente executor

O agente salva este relatório em `responses/resposta-<ID-do-prompt>.md` e o usuário o devolve ao orquestrador. Regras: preencher com resultados reais; não inventar saída de comando ou teste; se algo não foi executado, dizer.

## 1. Cabeçalho

- **Prompt ID:** [ID e versão]
- **Data:** [YYYY-MM-DD]
- **Modelo / Esforço usados:** [valores reais]
- **Status geral:** CONCLUÍDO | PARCIAL | BLOQUEADO | FALHOU

## 2. Resumo

Até 5 linhas: o que foi feito e o resultado.

## 3. Critérios de aceite

| Item | Critério (do prompt) | Status | Evidência |
|---|---|---|---|
| 1 | [texto] | CONCLUÍDO/PARCIAL/BLOQUEADO/FALHOU | [saída real, caminho de arquivo, comando] |

## 4. Alterações realizadas

Lista de arquivos criados, alterados e removidos, com uma linha sobre cada. Declarar qualquer alteração fora de AUTHORIZED CHANGES.

## 5. Testes

- **Executados:** comando e resultado real.
- **Não executados:** motivo.
- **Bloqueados:** motivo e o que desbloqueia.

## 6. Desvios do prompt

O que foi feito diferente do pedido e por quê. "Nenhum" se for o caso.

## 7. Causa-raiz (obrigatório se o status não for CONCLUÍDO)

Causa exata, rotulada como FATO, INFERÊNCIA ou HIPÓTESE, com a evidência que sustenta.

## 8. Riscos e pendências

Itens abertos, riscos identificados (só os reais), decisões que dependem do usuário.

## 9. Estado final verificado

Comparação com o Expected State do prompt: o que bate, o que diverge, o que permaneceu inalterado.

## 10. Próxima ação sugerida

Uma ação concreta.
