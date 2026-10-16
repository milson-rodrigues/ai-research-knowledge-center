# Kickoff de projeto

Objetivo: transformar uma ideia em um Dossiê de Arquitetura aprovado e em um plano de blocos, perguntando só o que muda decisão.

## Parte A: lacunas a fechar (checklist, não questionário)

Verificar o que já foi dito. Perguntar apenas o que falta **e** altera a decisão:

- Objetivo e problema; quem usa; o que é sucesso (critérios mensuráveis).
- Plataforma e ambiente: web, desktop, mobile; sistema operacional; hardware relevante.
- Restrições: prazo, orçamento/custo recorrente, licenças, conformidade, dados sensíveis.
- Integrações e dependências externas.
- Preferências ou proibições de tecnologia; conhecimento prévio do usuário.
- **Executores disponíveis:** quais IAs/agentes e modelos o usuário tem, e limites de uso.
- Escopo do MVP e o que fica fora.

## Parte B: Dossiê de Arquitetura (saída)

1. **Resumo e objetivo** (2 a 4 linhas).
2. **Requisitos e restrições** confirmados, separados de premissas (rotular FATO/INFERÊNCIA/HIPÓTESE).
3. **Decisões a tomar**, cada uma com no mínimo duas alternativas:

   | Decisão | Alternativa | Vantagens | Desvantagens | Complexidade | Risco | Custo |
   |---|---|---|---|---|---|---|

   Recomendação justificada. Para tecnologias, versões e APIs: fonte atual consultada, com link.
4. **Arquitetura proposta** (componentes, fluxo de dados, fronteiras).
5. **Método** (cadência, critérios de pronto) proporcional ao projeto.
6. **MVP e plano de blocos** (B01..Bn): objetivo, dependência, critério de aceite, risco.
7. **Riscos e pendências** abertos.
8. **Skills recomendadas**, vindas de `skills-catalog.md`, com versão fixada.
9. **Primeiro prompt** (B01, esqueleto executável) no formato `PROMPT-modelo.md`.

Após a aprovação do usuário: gerar `project-index.md`, `current-status.md` e `decisions.md` iniciais a partir dos templates.

## Parte C: eixos de decisão por tipo de projeto (ponto de partida, não resposta pronta)

Exemplo, editor de imagens: plataforma-alvo; motor de renderização e uso de GPU; formatos suportados; edição não destrutiva; desempenho com imagens grandes; extensibilidade (plugins); licenciamento de bibliotecas; empacotamento e distribuição. As alternativas concretas devem sair de pesquisa atual, não de memória.
