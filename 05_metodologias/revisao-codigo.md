# Metodologia: revisão de código

## Objetivo

Verificar se uma alteração implementa a especificação e mantém os padrões de engenharia sem ultrapassar o escopo aprovado.

## Preparação

- Identificar o diff e sua referência de base.
- Ler o prompt de origem, os critérios de aceite e decisões relevantes.
- Confirmar regras e convenções do projeto.
- Não presumir que arquivos não inspecionados estão corretos.

## Eixo A — aderência à especificação

- Todos os critérios foram cobertos?
- Existe comportamento ausente, divergente ou fora do escopo?
- Casos de borda e falha pertinentes foram tratados?
- O estado final corresponde ao `Expected State`?

## Eixo B — qualidade técnica

- A alteração respeita arquitetura, contratos e compatibilidade?
- Há risco de regressão, segurança, integridade dos dados ou desempenho?
- Há duplicação, acoplamento ou complexidade evitável sem ampliar o escopo?
- Os testes são adequados ao risco?
- As mudanças permanecem dentro de `AUTHORIZED CHANGES`?

## Relatório de achados

Para cada achado, informar severidade (crítica/alta/média/baixa, com justificativa), arquivo e símbolo/linha quando disponível, evidência concreta, impacto e recomendação de correção mínima.

Separe defeitos comprovados de preocupações hipotéticas. Não invente achados nem afirme que testes passaram sem executar os comandos correspondentes.

## Critério de conclusão

A revisão cobre os eixos aplicáveis, apresenta evidências dos achados e identifica o que não pôde ser inspecionado ou validado. Uma revisão sem achados não prova automaticamente a ausência de defeitos.
