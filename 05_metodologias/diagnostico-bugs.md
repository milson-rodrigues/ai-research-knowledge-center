# Metodologia: diagnóstico de bugs

## Objetivo

Encontrar uma causa sustentada por evidência antes de implementar a correção, reduzindo mudanças especulativas e regressões.

## Procedimento

1. **Reproduzir:** registrar passos, entradas, ambiente e resultado observado. Se não for reproduzível, declarar isso.
2. **Delimitar:** reduzir o caso ao menor exemplo útil e identificar módulos/contratos envolvidos.
3. **Formular hipóteses:** registrar explicações candidatas, evidência que as apoiaria/refutaria e próximo experimento seguro.
4. **Observar:** usar logs, depurador, métricas ou testes disponíveis; não fabricar observações.
5. **Estabelecer causa:** diferenciar causa confirmada de hipótese não provada.
6. **Criar regressão:** quando possível, fazer o teste falhar antes da correção.
7. **Corrigir minimamente:** alterar apenas o escopo necessário, sem refatorações alheias.
8. **Validar:** executar teste de regressão e testes adjacentes proporcionais ao risco.
9. **Relatar:** descrever diagnóstico, causa, correção, evidências, riscos e trabalho não verificado.

## Formato recomendado para bugs complexos

**Diagnóstico → Causa raiz → Correção → Código/arquivos → Validação → Riscos.** Rotular alegações relevantes como `FATO`, `INFERÊNCIA` ou `HIPÓTESE`.

## Critério de conclusão

A causa e correção estão sustentadas por evidências e a regressão relevante foi verificada, ou o relatório identifica precisamente o que impediu essa confirmação.
