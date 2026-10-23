# Guia de preenchimento do PROMPT

O `PROMPT-modelo.md` é o padrão estrutural do kit e deve ser preservado. Este guia orienta seu preenchimento; as regras normativas ficam em documento próprio para evitar duplicação.

## Consulta obrigatória antes de preencher

Antes de criar ou atualizar um prompt, consulte:

1. [`regras-prompt.md`](regras-prompt.md) — grounding, autorização, execução por blocos, proteção do código existente, testes e evidências.
2. [`../01_instrucoes/playbook-orquestrador.md`](../01_instrucoes/playbook-orquestrador.md) — fluxo operacional, dependências, configuração de execução e validação.
3. [`../01_instrucoes/regras-projetos.md`](../01_instrucoes/regras-projetos.md) — quando houver impacto em arquitetura, contratos, manutenção ou evolução do projeto.
4. A metodologia pertinente em [`../05_metodologias/`](../05_metodologias/), quando aplicável.
5. [`modelo-resposta-agente.md`](modelo-resposta-agente.md) — formato do relatório exigido do executor.
6. [`PROMPT-modelo.md`](PROMPT-modelo.md) — estrutura exata a preservar.

O prompt final deve conter as instruções essenciais para o executor. Não depender apenas de links para arquivos que ele talvez não consiga acessar. Se um documento necessário estiver indisponível, declarar a limitação; não reconstruí-lo de memória.

## Convenção de ID (RECOMENDAÇÃO)

`PROMPT-<SIGLA>-<NNN>-<semver>`, por exemplo `PROMPT-IMG-003-1.0.0`.

- `SIGLA`: sigla do projeto. `NNN`: sequência do prompt no projeto.
- Correção: `PROMPT-<SIGLA>-<NNN>-COR-<n>-<semver>`.
- Nova versão: subir o semver e preencher `Previous Version`.
- O ID também nomeia o relatório do agente: `responses/resposta-<ID>.md`.

## Campo a campo

| Seção | O que preencher |
|---|---|
| Header | Status começa em `Proposed` e muda para `Approved` após aprovação do usuário. Definir `Type` conforme a tarefa. |
| Execution Configuration | Seguir o playbook; usar apenas modelos declarados como disponíveis pelo usuário. |
| ROLE | Papel técnico específico e limites do agente. |
| CONTEXT | Estado confirmado, decisões aprovadas, contratos e caminhos canônicos; não colar o que o agente pode ler. |
| TASK | Objetivo verificável, escopo e resultado esperado; declarar o que fica fora do escopo. |
| AUTHORIZED CHANGES | Caminhos/áreas permitidos e operações proibidas. O que não estiver autorizado não deve ser alterado. |
| CONSTRAINTS | Limites técnicos, operacionais, de segurança, compatibilidade, versões e custo. |
| CRITERIA | Critérios mensuráveis, testes exigidos e evidência aceita por critério. |
| OUTPUT | Relatório no formato do modelo de resposta, arquivos esperados, pendências e próxima ação. |
| Expected State | Estado verificável ao final e elementos que devem permanecer inalterados. |

## Planejamento mínimo

Antes de liberar execução, confirmar:

- objetivo, escopo e fora de escopo;
- contexto confirmado, decisões aprovadas e fontes canônicas;
- áreas autorizadas e operações proibidas;
- dependências e ordem dos blocos, quando houver várias etapas;
- risco e estratégia de validação proporcional;
- critérios de aceite e evidências esperadas;
- executor, modelo, esforço, sessão e modo conforme a rota;
- metodologia pertinente, se houver;
- estado esperado e elementos que devem permanecer inalterados.

Se faltar uma informação indispensável, pergunte ou declare o bloqueio. Não transforme hipótese em fato apenas para preencher um campo.

## Checklist antes de entregar

- [ ] Títulos e estrutura idênticos aos de `PROMPT-modelo.md`.
- [ ] Objetivo principal, escopo e fora de escopo claros.
- [ ] Critérios verificáveis e evidência definida por critério.
- [ ] Alterações autorizadas e proibidas explicitadas.
- [ ] Dependências e blocos ordenados, quando aplicável.
- [ ] Modelo/esforço confirmados segundo a rota; nenhum modelo inventado.
- [ ] Fatos de versão/API conferidos em fonte oficial atual quando necessário.
- [ ] Testes proporcionais ao risco definidos.
- [ ] Regras essenciais presentes no prompt final.
- [ ] Nenhum segredo no texto.
- [ ] Relatório do executor exigido.
- [ ] Estado esperado e elementos a preservar descritos.

## Exemplo ilustrativo (fictício)

```text
PROMPT-IMG-001-1.0.0 — Esqueleto executável do editor de imagens
Type: Implementation | Mode: Execute | Session: New
ROLE: engenheiro responsável por criar o esqueleto mínimo do projeto.
CONTEXT: decisões de plataforma e linguagem aprovadas; repositório vazio.
TASK: criar a estrutura base que compila, abre uma janela vazia e executa um teste.
AUTHORIZED CHANGES: criar arquivos na raiz, /src e /tests. Proibido: dependências não aprovadas, rede, excluir arquivos.
CRITERIA: build sem erros com saída do comando; um teste passando com resultado observado; README com instruções de execução.
OUTPUT: responses/resposta-PROMPT-IMG-001-1.0.0.md no formato do modelo.
Expected State: esqueleto funcional; arquivos fora do escopo permanecem inalterados.
```

No uso real, o prompt completo segue todas as seções de `PROMPT-modelo.md`.
