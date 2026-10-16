# IA Resource Knowledge Center

Kit versão **1.0.0** | 2026-10-16

Biblioteca mestre para configurar o ChatGPT como Engenheiro Principal de Software, Orquestrador de Projetos com IA e Engenheiro de Prompt.

## Princípio

- **Esta pasta é o mestre reutilizável.** Aqui ficam os modelos e regras de referência.
- **Cada projeto carrega o que precisa para operar** nas suas próprias fontes: os 3 arquivos de continuidade e uma cópia do `kit-operacional.md`. A Library não tem leitura automática garantida em todo chat, então o essencial do projeto não depende dela.

## Mapa

| Caminho | Função | Vai para as fontes do projeto? |
|---|---|---|
| `00_GUIA-DE-CONFIGURACAO.md` | Passo a passo de configuração e testes | Não |
| `01_instrucoes/instrucao-projeto.md` | Texto a colar no campo de instruções do projeto | Não (vai no campo) |
| `01_instrucoes/playbook-orquestrador.md` | Procedimentos detalhados | Via `kit-operacional.md` |
| `02_modelos/PROMPT-modelo.md` | Seu modelo de prompt (inalterado) | Via `kit-operacional.md` |
| `02_modelos/guia-preenchimento-prompt.md` | Como preencher cada campo | Via `kit-operacional.md` |
| `02_modelos/modelo-resposta-agente.md` | Formato do relatório do agente | Via `kit-operacional.md` |
| `02_modelos/kickoff-projeto.md` | Kickoff e Dossiê de Arquitetura | Via `kit-operacional.md` |
| `03_continuidade/handoff-novo-chat.md` | Passagem de um chat para o próximo | Via `kit-operacional.md` |
| `03_continuidade/*.template.md` | Modelos dos 3 arquivos por projeto | Cada um vira arquivo do projeto |
| `04_skills/skills-catalog.md` | Skills aprovadas | Opcional (anexar quando o projeto usar skills) |
| `kit-operacional.md` | Consolidado de playbook + modelos | **Sim, em todo projeto** |

## Manutenção

- Alterou qualquer modelo ou regra: subir a versão do kit, regenerar o `kit-operacional.md` e atualizar os projetos ativos. Registrar a troca em `decisions.md` do projeto.
- Nunca guardar segredos, tokens ou credenciais nesta pasta.
