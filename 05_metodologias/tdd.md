# Metodologia: Test-Driven Development (TDD)

## Quando usar

Use em funcionalidades ou correções com comportamento observável e testes automatizáveis. Se a codebase não tiver infraestrutura de testes adequada, declare a limitação e proponha um passo seguro para obter feedback antes de mudanças amplas.

## Ciclo Red → Green → Refactor

1. **Red:** escrever um teste pequeno que descreva o comportamento e confirmar falha pela razão esperada.
2. **Green:** implementar a menor mudança capaz de fazer o teste passar.
3. **Refactor:** melhorar o desenho sem alterar o comportamento; manter testes relevantes passando.
4. **Regressão:** executar testes relacionados aos contratos e áreas adjacentes afetados.
5. **Evidências:** informar comandos reais, resultados observados e testes não executados/bloqueados.

## Regras

- Não inventar saídas de testes.
- Não alterar o teste só para esconder uma falha sem verificar a intenção do requisito.
- Separar testes unitários, integração e regressão quando a arquitetura e o risco justificarem.
- Evitar refatoração não relacionada ao objetivo do bloco.
- Se não for possível executar testes, declarar a limitação e não alegar validação bem-sucedida.

## Critério de conclusão

O comportamento está coberto por testes pertinentes; os testes executados passam; as alterações respeitam o escopo; limitações e evidências estão no relatório.
