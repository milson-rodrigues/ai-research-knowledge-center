# Catálogo de skills

Fica na Biblioteca (pasta "ai-research-knowledge-center"). É um **índice de links com commit fixado**: não copie os SKILL.md para a Biblioteca. O orquestrador só recomenda como aplicada uma skill da tabela "Aprovadas". Outra pode ser citada como candidata, sem uso.

Formato: padrão aberto de Agent Skills (SKILL.md com nome e descrição). Referência: https://agentskills.io/home.

## Quem consome a skill

- **FATO (help.openai.com, "Skills in ChatGPT"):** skills nativas do ChatGPT são oferecidas a Business, Enterprise, Healthcare e Edu elegíveis. A página não lista o plano Go, não descreve invocação por `@` e não menciona uso dentro de Projects.
- **INFERÊNCIA:** com plano Go (deduzido do rótulo na tela, não confirmado), a instalação nativa provavelmente não está disponível.
- **RECOMENDAÇÃO:** quem consome a skill é o **agente executor**. O orquestrador escolhe a skill no catálogo e a cita no prompt do bloco, com URL, commit fixado e pasta de destino.

## Como cada skill é usada

| Modo | Quando | Observação |
|---|---|---|
| **Referenciada no prompt** (recomendado) | O executor baixa o commit fixado e usa a skill | O `AUTHORIZED CHANGES` do prompt deve **autorizar explicitamente** o download daquele commit; o exemplo do guia de preenchimento proíbe rede por padrão |
| **Instalada** no ChatGPT | Só se o plano oferecer skills | Ativação automática; revisar antes de instalar |
| **Só link, sem commit** | Nunca como fonte única | O conteúdo pode mudar sem aviso |

## Aprovadas

| Nome | Origem (URL) | Commit fixado | Licença | Tipo de projeto | Instalação no executor | Revisada em | Quando usar |
|---|---|---|---|---|---|---|---|
| [a preencher] | | | | | | | |

Tipos de projeto: mobile, desktop, web, teste, cybersecurity, ponta a ponta (e2e), geral.

## Critérios para aprovar uma skill

- [ ] Li o SKILL.md completo e todos os arquivos que ele referencia (scripts, templates).
- [ ] Nenhum script faz rede, lê credenciais, grava fora da pasta do projeto ou executa algo que eu não entendi.
- [ ] Licença compatível com o uso.
- [ ] Mantida (atividade recente) e com commit identificável.
- [ ] O escopo é estreito e a descrição diz claramente quando usar (evita ativação indevida).
- [ ] Testada em um caso real antes de entrar na tabela.
- [ ] Commit fixado registrado acima; mudança de commit exige nova revisão.

## Para escolher skills por tipo de projeto

Pedir ao orquestrador (modo Research): pesquisar repositórios de skills para o tipo de projeto, comparar por manutenção, escopo e risco, e propor candidatas **sem** adicioná-las. A aprovação é sua, pelos critérios acima. O orquestrador registra em `project-index.md` quais skills aprovadas o projeto usa.
