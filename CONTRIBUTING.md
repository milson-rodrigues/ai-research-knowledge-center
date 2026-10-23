# Como contribuir

Obrigado por ajudar a melhorar o AI Research Knowledge Center. Este repositório mantém as regras, rotas, modelos e metodologias usados para orientar trabalho de engenharia de software com IA. Contribuições devem melhorar clareza, confiabilidade, rastreabilidade ou facilidade de manutenção sem criar cópias conflitantes das regras.

## 1. Onde registrar problemas e ideias

Use **GitHub Issues** para acompanhar trabalho que ainda precisa ser analisado ou executado:

- **Bug:** comportamento incorreto, link quebrado, instrução contraditória, etapa ausente ou exemplo que não funciona como documentado. Use o formulário *Reportar bug*.
- **Melhoria:** nova capacidade, melhoria de fluxo, metodologia, documentação ou proposta de simplificação. Use o formulário *Propor melhoria*.
- **Dúvida ou discussão:** abra uma Issue e descreva o contexto e a pergunta.

Não mantenha um arquivo geral `BUGS.md`, `MELHORIAS.md` ou equivalente como backlog paralelo. Issues acompanham o problema, a discussão, a prioridade e o estado de resolução; commits e Pull Requests registram as alterações efetivamente propostas e incorporadas. Um documento Markdown de roadmap só deve existir se houver uma necessidade específica de planejamento editorial, não como substituto de Issues.

Antes de abrir uma Issue, pesquise as Issues existentes para evitar duplicatas. Use títulos objetivos e descreva um único problema ou proposta por Issue.

## 2. Fluxo recomendado

1. **Registre ou encontre uma Issue.** Explique o problema ou necessidade, o comportamento atual, o resultado esperado e as evidências disponíveis.
2. **Leia os documentos afetados.** Comece pelo [README](README.md), pela [rota operacional](01_instrucoes/rota-operacional.md) e pelos arquivos mestres relacionados.
3. **Delimite a alteração.** Prefira o menor conjunto de mudanças que resolva o problema. Não misture uma correção documental com uma mudança de metodologia não relacionada.
4. **Trabalhe em uma branch.** Convenções sugeridas: `docs/<assunto>`, `fix/<assunto>`, `feat/<assunto>` ou `method/<assunto>`.
5. **Atualize as referências dependentes.** Se mudar um documento mestre, procure links, instruções, diagramas e outros documentos que dependam dele.
6. **Valide a alteração.** Confira links relativos, caminhos de arquivos, consistência dos termos, estrutura Markdown, renderização Mermaid e legibilidade dos SVGs quando aplicável.
7. **Abra um Pull Request.** Vincule a Issue quando houver uma (`Closes #123`) e descreva o que mudou, por quê, o que foi validado e o que não foi possível validar.

Não faça commit direto na `main` como fluxo normal de contribuição. Use o Pull Request como revisão antes de incorporar a mudança. Para contribuições feitas pelo mantenedor, o mesmo checklist pode ser usado como revisão local.

## 3. Regras de arquitetura documental

### Fonte canônica e rota

- O repositório GitHub, branch `main`, é a fonte canônica dos documentos globais publicados.
- `00_ROTA-DE-CONSULTA.md` é um **bootstrap permanente**, mantido nas fontes de cada projeto ChatGPT. Não o altere por mudanças comuns nas regras, modelos ou metodologias, nem solicite que os projetos baixem a rota novamente.
- A árvore que pode evoluir fica em `01_instrucoes/rota-operacional.md`. Atualize esse arquivo quando mudar a classificação dos pedidos, os documentos que cada caminho exige ou as saídas do fluxo.
- O estado específico de uma aplicação pertence ao próprio projeto, não ao repositório global do kit.
- Não recorra à Biblioteca do ChatGPT, à memória ou a cópias antigas como substituto silencioso de documentos atuais inacessíveis.

### Documentos mestres e consolidado

- Altere primeiro o documento mestre responsável pelo conteúdo.
- Atualize documentos relacionados e referências no README quando necessário.
- Depois de alterar documentos mestres incluídos no consolidado, regenere `kit-operacional.md`. Ele é um snapshot para auditoria, não uma segunda fonte de verdade.
- Não replique regras completas em vários arquivos sem necessidade. Prefira links e responsabilidades claras.
- Preserve os títulos e campos de `02_modelos/PROMPT-modelo.md`, salvo quando a própria estrutura do modelo estiver sob revisão explícita.
- Separe decisões aprovadas, propostas, hipóteses e exemplos.

### Qualidade e segurança

- Priorize precisão, clareza, consistência, manutenibilidade e proporcionalidade entre benefício e complexidade.
- Para regras técnicas que dependam de comportamento externo, priorize documentação oficial e indique versão/commit quando isso for importante.
- Não declare testes, verificações, aprovações ou resultados que não tenham ocorrido.
- Registre testes executados, não executados e bloqueados de forma separada.
- Não inclua tokens, senhas, credenciais, dados pessoais, arquivos de estado de projetos de clientes ou outros segredos.
- Para skills externas, registre origem, licença, versão/commit, manutenção, dependências, riscos e evidências antes de propor aprovação.

## 4. Critérios para aceitar uma contribuição

Uma contribuição está pronta para revisão quando:

- [ ] Resolve um problema identificável ou atende a uma necessidade explícita.
- [ ] Está limitada ao escopo descrito e não introduz alterações não relacionadas.
- [ ] Mantém consistentes a rota operacional, os documentos mestres e as referências afetadas.
- [ ] Preserva o bootstrap permanente, salvo se a mudança for especificamente sobre o seu contrato.
- [ ] Atualiza `kit-operacional.md` quando altera documentos mestres incluídos nele.
- [ ] Não deixa links relativos, caminhos ou nomes de arquivos quebrados.
- [ ] Os diagramas continuam legíveis e coerentes com o processo documentado.
- [ ] As validações reais e as limitações restantes estão descritas no Pull Request.
- [ ] Não adiciona segredos nem informação específica de um projeto ao kit global.

Nem todas as contribuições exigem testes de código. Para alterações documentais, a verificação pode consistir em revisão de links, renderização, consistência cruzada e simulação do fluxo descrito.

## 5. Como descrever um Pull Request

Inclua:

- **Motivação:** qual problema ou oportunidade está sendo tratado.
- **Mudanças:** quais arquivos e comportamentos documentais foram alterados.
- **Impacto:** que outros documentos, fluxos ou projetos podem ser afetados.
- **Validação:** quais verificações foram feitas e seus resultados.
- **Limitações:** o que permanece sem validar, se houver.
- **Issue relacionada:** link ou número, quando existir.

Mudanças que alterem a arquitetura documental, a hierarquia de fontes ou o comportamento da rota precisam explicar os trade-offs e a estratégia de migração, se houver impacto sobre projetos já configurados.
