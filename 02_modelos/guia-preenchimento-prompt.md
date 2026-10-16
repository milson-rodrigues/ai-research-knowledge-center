# Guia de preenchimento do PROMPT

O modelo `PROMPT-modelo.md` é o seu padrão e permanece sem alterações. Este guia diz como o orquestrador deve preenchê-lo.

## Convenção de ID (RECOMENDAÇÃO)

`PROMPT-<SIGLA>-<NNN>-<semver>`, por exemplo `PROMPT-IMG-003-1.0.0`.
- `SIGLA`: sigla do projeto. `NNN`: sequência do prompt no projeto.
- Correção de um item: `PROMPT-<SIGLA>-<NNN>-COR-<n>-<semver>`.
- Nova versão do mesmo prompt: subir o semver e preencher `Previous Version`.
- O ID também nomeia o relatório do agente: `responses/resposta-<ID>.md`.

## Campo a campo

| Seção | O que o orquestrador preenche |
|---|---|
| Header | Status começa em `Proposed` e vira `Approved` quando o usuário aprovar. `Type` conforme o bloco. |
| Execution Configuration | Seguir a tabela do playbook (seção 3). Só modelos que o usuário tem. |
| ROLE | Papel técnico específico do bloco (ex.: "Engenheiro de backend responsável por X") e limites do agente. |
| CONTEXT | Estado confirmado; IDs de decisões aprovadas (`decisions.md`); contratos a preservar; caminhos canônicos. Sem colar o que o agente pode ler. |
| TASK | Um objetivo, escopo e resultado esperado. Dizer o que está fora do escopo. |
| AUTHORIZED CHANGES | Lista de caminhos/áreas permitidos e operações proibidas (exclusão, migração, dependência nova, rede, produção). Se não está listado, não está autorizado. |
| CONSTRAINTS | Compatibilidade, segurança, custo, desempenho, versões fixadas. |
| CRITERIA | Critérios **mensuráveis**, testes exigidos (caminho feliz, bordas, falhas) e a evidência aceita de cada um. |
| OUTPUT | Relatório `.md` no formato `modelo-resposta-agente`, arquivos esperados, pendências e próxima ação. |
| Expected State | Estado verificável ao final, e o que deve permanecer idêntico. |

## Antes de entregar o prompt, o orquestrador confere

- [ ] Um único objetivo, escopo e fora-de-escopo claros.
- [ ] Critérios verificáveis, cada um com evidência exigida.
- [ ] Alterações autorizadas e proibidas listadas.
- [ ] Modelo e esforço realmente disponíveis ao usuário; sessão e modo coerentes.
- [ ] Nenhum segredo no texto.
- [ ] Nenhum fato de versão/API afirmado sem checagem em fonte atual.
- [ ] Entregue em bloco de código com cerca de 4 crases.

## Exemplo ilustrativo (fictício, só para mostrar a densidade esperada)

~~~
PROMPT-IMG-001-1.0.0 — Esqueleto executável do editor de imagens
Type: Implementation | Mode: Execute | Session: New
ROLE: engenheiro responsável por criar o esqueleto mínimo do projeto.
CONTEXT: decisões D-001 (plataforma) e D-002 (linguagem) aprovadas; repositório vazio.
TASK: criar a estrutura base que compila, abre uma janela vazia e executa um teste.
AUTHORIZED CHANGES: criar arquivos na raiz e em /src e /tests. Proibido: dependências fora da lista, acesso à rede, apagar arquivos.
CRITERIA: (1) build sem erros, evidência = saída do comando; (2) 1 teste passando, evidência = saída; (3) README com como executar.
OUTPUT: responses/resposta-PROMPT-IMG-001-1.0.0.md no formato do modelo.
Expected State: repositório com esqueleto que executa; nenhum arquivo fora de /src, /tests e raiz.
~~~

No uso real, o prompt completo segue todas as seções do `PROMPT-modelo.md`.
