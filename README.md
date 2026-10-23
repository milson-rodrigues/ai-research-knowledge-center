<div align="center">

# AI Research Knowledge Center

**Um sistema documental para orientar agentes de IA em engenharia de software.**

Regras claras · Prompts verificáveis · Execução por blocos · Evidências reais

[Começar](#comece-por-aqui) · [Como funciona](#como-o-sistema-funciona) · [Estrutura](#mapa-do-repositório) · [Benefícios](#por-que-usar)

</div>

---

## O que é

O **AI Research Knowledge Center** organiza os modelos, regras, procedimentos, metodologias e skills utilizados para orientar o ChatGPT e outros agentes durante trabalhos de engenharia de software.

Em vez de concentrar tudo em um prompt gigante, cada arquivo tem uma responsabilidade clara:

- **Modelos:** padronizam a estrutura de prompts, relatórios e kickoffs.
- **Regras:** estabelecem limites de escopo, qualidade e evidências.
- **Playbook:** coordena as etapas e o trabalho do orquestrador.
- **Metodologias:** descrevem práticas específicas, como TDD, diagnóstico de bugs e revisão de código.
- **Skills:** catalogam recursos externos com origem e versão identificáveis.
- **Continuidade:** preserva o estado e as decisões de cada projeto.

> O kit orienta o trabalho; não substitui as decisões aprovadas, a documentação oficial, os testes nem as evidências da execução.

## Comece por aqui

1. **Configure o ChatGPT:** siga [`00_GUIA-DE-CONFIGURACAO.md`](00_GUIA-DE-CONFIGURACAO.md).
2. **Adicione o bootstrap uma única vez:** disponibilize [`00_ROTA-DE-CONSULTA.md`](00_ROTA-DE-CONSULTA.md) nas fontes do projeto. Ele permanece estável e manda consultar a rota operacional atual no GitHub; mudanças normais do kit não exigem reenviar esse arquivo.
3. **Mantenha os arquivos de estado do projeto:** crie a partir dos templates em `03_continuidade/` os arquivos reais `project-index.<projeto>.md`, `current-status.<projeto>.md` e `decisions.<projeto>.md`. Esses arquivos pertencem ao projeto e não devem ser guardados como estado global do kit.
4. **Prepare o prompt:** leia o modelo, o guia de preenchimento, as regras, o playbook e, quando aplicável, as regras do projeto e a metodologia específica.
5. **Valide o resultado:** exija relatório no formato [`02_modelos/modelo-resposta-agente.md`](02_modelos/modelo-resposta-agente.md) e confira as evidências antes de avançar.

## Por que usar

| Risco comum | Como o kit ajuda |
|---|---|
| Requisitos ambíguos | Explicita objetivo, escopo, restrições e critérios de aceite |
| Prompts inconsistentes | Mantém um modelo fixo e um guia de preenchimento |
| Alterações não autorizadas | Separa mudanças permitidas das proibidas |
| Implementação grande demais | Divide o trabalho em blocos com dependências claras |
| Sucesso declarado sem prova | Exige testes e evidências reais por critério |
| Código difícil de manter | Considera arquitetura, extensibilidade, desempenho e complexidade proporcional |
| Perda de contexto | Usa arquivos de estado e handoff entre chats |
| Regras contraditórias | Define documentos canônicos e responsabilidades explícitas |

## Como o sistema funciona

O bootstrap fica nas fontes do projeto ChatGPT. Em cada solicitação relevante, o chat lê do GitHub a rota operacional atual, classifica o pedido e consulta somente os documentos pertinentes. Os modelos e as regras globais não são copiados para o projeto.

```mermaid
flowchart TD
    A["Pedido do usuário"] --> B["Bootstrap permanente"]
    B --> C["Ler rota operacional atual no GitHub"]
    C --> D{"Tipo de pedido"}
    D -->|Projeto novo| E["Kickoff e requisitos"]
    E --> F{"Falta informação essencial?"}
    F -->|Sim| Q["Perguntas objetivas"]
    F -->|Não| G["Dossiê, alternativas e aprovação"]
    G --> H["Plano de blocos"]
    D -->|Prompt / implementação| I["Inspecionar estado, escopo e critérios"]
    D -->|Bug / correção| J["Ler erro, prompt, relatório e diff"]
    J --> K["Diagnosticar ou delimitar correção"]
    D -->|Validar execução| L["Comparar prompt, relatório e evidências"]
    L --> M{"Critérios comprovados?"}
    M -->|Sim| N["Registrar status verificado"]
    M -->|Não| O["Identificar lacunas e próxima ação"]
    D -->|Arquitetura / pesquisa| P["Consultar fontes e comparar alternativas"]
    D -->|Estado / handoff| R["Ler estado e templates pertinentes"]
    H --> S["Montagem comum do prompt"]
    I --> S
    K --> S
    O --> S
    S --> T["Modelo + guia + regras + playbook + relatório"]
    T --> U{"Informação suficiente?"}
    U -->|Não| Q
    U -->|Sim| V["Entregar prompt completo"]
    V --> W["Usuário envia ao agente executor"]
    W --> X["Executor devolve relatório"]
    X --> L
    N --> Y["Atualizar continuidade com evidências"]
    Y --> Z{"Há próximo bloco aprovado?"}
    Z -->|Sim| I
    Z -->|Não| AA["Fechar fase / handoff"]
    Q --> AB["Entregar resultado no formato do kit"]
    P --> AB
    R --> AB
    AA --> AB
```

### O ciclo em linguagem direta

1. **Consultar:** ler a rota operacional atual e os arquivos indicados no GitHub. Registrar os arquivos realmente lidos na tabela `CONSULTA`.
2. **Entender:** recuperar o estado e as decisões específicas do projeto; distinguir fatos, hipóteses e lacunas.
3. **Escolher o caminho:** projeto novo, prompt/implementação, bug/correção, validação, pesquisa/arquitetura ou continuidade.
4. **Preparar:** quando houver tarefa executável, todos os caminhos convergem para `02_modelos/PROMPT-modelo.md`, combinado com o guia, regras, playbook e relatório padronizado.
5. **Perguntar ou entregar:** se faltar um dado indispensável, fazer perguntas objetivas. Caso contrário, entregar um prompt completo, com alterações autorizadas, restrições, critérios de aceite, testes e estado esperado.
6. **Executar:** o usuário envia o prompt ao agente executor e devolve o relatório produzido por ele.
7. **Validar:** comparar os critérios com evidências reais e marcar `CONCLUÍDO`, `PARCIAL`, `BLOQUEADO` ou `FALHOU`.
8. **Repetir ou encerrar:** se algo falhou, investigar a causa e preparar um prompt de correção; se passou, atualizar os arquivos de continuidade e liberar o próximo bloco aprovado.

**Importante:** o kit orquestra e valida; não executa sozinho as alterações de código. O agente executor é quem realiza o trabalho concreto.
  
## Como os arquivos se relacionam

O fluxo detalhado mostra as relações entre os documentos. O infográfico é a visão resumida. As duas imagens são SVGs, com cartões de contraste próprio e texto vetorial. Para entender as ramificações conforme o tipo de pedido, veja também a árvore abaixo.

### Fluxo detalhado — dependências e retorno

<p align="center">
  <img src="assets/relacionamento-arquivos.svg" alt="Fluxo detalhado: rota de consulta, guia, modelo, regras, playbook, metodologia, prompt, agente executor, modelo de resposta, validação e atualização de estado." width="850">
</p>

### Infográfico — visão resumida

<p align="center">
  <img src="assets/relacionamento-arquivos-infografico.svg" alt="Infográfico resumido: rota de consulta, guia de prompt, regras e playbook, metodologia, prompt final, agente, relatório, validação e continuidade." width="1000">
</p>

### Responsabilidade de cada camada

| Camada | Arquivo | Responsabilidade |
|---|---|---|
| Bootstrap estável | [`00_ROTA-DE-CONSULTA.md`](00_ROTA-DE-CONSULTA.md) | Ponto de entrada permanente nas fontes do projeto; direciona para a rota dinâmica no GitHub |
| Rota operacional | [`01_instrucoes/rota-operacional.md`](01_instrucoes/rota-operacional.md) | Árvore de decisão que pode evoluir sem reenviar o bootstrap |
| Modelo | [`02_modelos/PROMPT-modelo.md`](02_modelos/PROMPT-modelo.md) | Define os títulos e a estrutura do prompt |
| Preenchimento | [`02_modelos/guia-preenchimento-prompt.md`](02_modelos/guia-preenchimento-prompt.md) | Explica como preencher os campos |
| Regras de prompt | [`02_modelos/regras-prompt.md`](02_modelos/regras-prompt.md) | Define grounding, escopo, Quality Gate, testes e evidências |
| Orquestração | [`01_instrucoes/playbook-orquestrador.md`](01_instrucoes/playbook-orquestrador.md) | Coordena planejamento, blocos, validação e handoff |
| Regras do projeto | [`01_instrucoes/regras-projetos.md`](01_instrucoes/regras-projetos.md) | Orienta arquitetura, contratos e evolução do projeto |
| Metodologias | [`05_metodologias/`](05_metodologias/) | Apresenta procedimentos especializados aplicáveis por necessidade |
| Relatório | [`02_modelos/modelo-resposta-agente.md`](02_modelos/modelo-resposta-agente.md) | Registra alterações, testes, evidências, desvios e estado final |
| Continuidade | [`03_continuidade/`](03_continuidade/) | Fornece templates de estado e handoff |

**Regra de composição:** metodologia complementa as regras permanentes; não as substitui. O prompt final precisa conter as instruções críticas para o executor e não pode depender exclusivamente de links que talvez ele não consiga acessar.

## Mapa do repositório

```text
.
├── README.md
├── 00_ROTA-DE-CONSULTA.md
├── 00_GUIA-DE-CONFIGURACAO.md
├── 01_instrucoes/
│   ├── instrucao-projeto.md
│   ├── rota-operacional.md
│   ├── playbook-orquestrador.md
│   └── regras-projetos.md
├── 02_modelos/
│   ├── PROMPT-modelo.md
│   ├── guia-preenchimento-prompt.md
│   ├── regras-prompt.md
│   ├── modelo-resposta-agente.md
│   └── kickoff-projeto.md
├── 03_continuidade/
│   ├── handoff-novo-chat.md
│   └── *.template.md
├── 04_skills/
│   └── skills-catalog.md
├── 05_metodologias/
│   ├── README.md
│   ├── decomposicao-tarefas.md
│   ├── tdd.md
│   ├── diagnostico-bugs.md
│   └── revisao-codigo.md
├── assets/
│   ├── Como os Documentos se Relacionam.png
│   ├── Fluxograma do Processo de Consulta.png
│   ├── relacionamento-arquivos-infografico.svg
│   ├── relacionamento-arquivos.svg
└── kit-operacional.md
```

## Princípios de engenharia

- **Clarificar antes de construir:** compreender objetivo, escopo, limitações e critérios.
- **Dividir para validar:** declarar dependências e validar cada bloco antes do próximo.
- **Preservar o que funciona:** não expandir escopo silenciosamente nem alterar áreas não autorizadas.
- **Usar fontes confiáveis:** preferir documentação oficial atual para versões, APIs e comportamentos mutáveis.
- **Testar proporcionalmente ao risco:** relatar separadamente testes executados, não executados e bloqueados.
- **Não inventar evidências:** resultados só são declarados quando realmente observados.
- **Aplicar o Quality Gate:** avaliar manutenibilidade, arquitetura, extensibilidade, desempenho e se a complexidade introduzida é proporcional ao benefício.
- **Diferenciar propostas de decisões:** somente decisões aprovadas entram no registro canônico.

## Execução por blocos e Quality Gate

Cada bloco deve conter objetivo verificável, escopo autorizado, dependências, critérios de aceite, testes/evidências e condição de interrupção. Tarefas que afetam dados, autenticação, migrações, contratos públicos ou produção exigem análise e validação proporcionalmente mais rigorosas.

O Quality Gate não exige refatorar tudo: avalia apenas os critérios pertinentes ao escopo e ao risco. Uma alteração deve gerar benefício que justifique a complexidade e o custo introduzidos.

## Skills e metodologias

- Use [`04_skills/skills-catalog.md`](04_skills/skills-catalog.md) para skills externas aprovadas e com referência fixada.
- Use [`05_metodologias/README.md`](05_metodologias/README.md) para escolher o procedimento adequado ao problema.
- Não aplique todas as metodologias por padrão nem declare uma metodologia executada sem registrar as etapas e evidências correspondentes.

## Manutenção e versionamento

- Este repositório é a fonte canônica das regras e modelos do kit; o estado de cada projeto fica nas fontes daquele projeto.
- Os documentos globais do kit são consultados exclusivamente no GitHub. Se ele estiver indisponível, declare bloqueio em vez de usar cópias antigas.
- Ao alterar regras, modelos ou metodologias, atualize as referências relacionadas e regenere `kit-operacional.md` para mantê-lo alinhado.
- `00_ROTA-DE-CONSULTA.md` é um bootstrap permanente: mudanças comuns são feitas em `01_instrucoes/rota-operacional.md` e nos documentos mestres, sem solicitar novo upload do bootstrap.
- Uma mudança na branch de trabalho não é publicada automaticamente para os projetos: revise o diff e incorpore a proposta na branch principal somente após aprovação.
- Nunca armazene senhas, tokens ou credenciais.

## Referências e inspirações

- [Matt Pocock — Skills for Real Engineers](https://github.com/mattpocock/skills): práticas pequenas e combináveis para clarificação de requisitos, loops de feedback, TDD, diagnóstico e revisão de arquitetura. O kit adapta esses princípios sem importar automaticamente skills ou fluxos externos.
- [Documentação oficial do GitHub](https://docs.github.com/): referência para o comportamento da plataforma.
- Documentação oficial da linguagem, framework ou serviço do projeto: referência prioritária para APIs, versões e comportamento técnico mutável.

<div align="center">

**Menos suposições. Blocos menores. Feedback real. Mudanças auditáveis.**

</div>
