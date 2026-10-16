# Catálogo de skills aprovadas

Fica na Library (pasta IA Resource Knowledge Center). Cada skill entra **depois** de revisada. O orquestrador só recomenda o que está aqui, citando a versão fixada.

Formato: o padrão aberto de Agent Skills (SKILL.md com nome e descrição). Referência: https://agentskills.io/home. A disponibilidade de skills no ChatGPT depende do plano e do workspace (conferir o artigo "Skills in ChatGPT" em help.openai.com).

## Como cada skill é usada

| Modo | Quando | Observação |
|---|---|---|
| **Instalada** no ChatGPT | Uso frequente e plano com suporte | Ativação automática ou por @; revisar antes de instalar |
| **Copiada** como referência (arquivo) | Consulta pelo orquestrador ou pelo agente executor | Não ativa sozinha; anexar ou citar quando preciso |
| **Só link** | Não usar como fonte única | O conteúdo pode mudar sem aviso; fixar commit ou versão |

## Catálogo

| Nome | Origem (URL) | Versão / commit fixado | Licença | Uso (mobile / desktop / web / geral) | Modo | Revisada em | Quando usar |
|---|---|---|---|---|---|---|---|
| [a preencher] | | | | | | | |

## Critérios para aprovar uma skill

- [ ] Li o SKILL.md completo e todos os arquivos que ele referencia (scripts, templates).
- [ ] Nenhum script faz rede, lê credenciais, grava fora da pasta do projeto ou executa algo que eu não entendi.
- [ ] Licença compatível com o uso.
- [ ] Mantida (atividade recente) e com versão ou commit identificável.
- [ ] O escopo é estreito e a descrição diz claramente quando usar (evita ativação indevida).
- [ ] Testada em um caso real antes de entrar no catálogo.
- [ ] Versão fixada registrada acima; mudança de versão exige nova revisão.

## Para escolher skills por tipo de projeto

Pedir ao orquestrador (modo Research): pesquisar repositórios de skills para o tipo de projeto (mobile, desktop ou web), comparar por manutenção, escopo e risco, e propor candidatas **sem** adicioná-las: a aprovação é sua, pelos critérios acima.
