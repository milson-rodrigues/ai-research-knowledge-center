# AI Research Knowledge Center

Kit versão **1.0.0** | Rota versão **2.0** | 2026-10-16

Repositório mestre para configurar o ChatGPT como Engenheiro Principal de Software, Orquestrador de Projetos com IA e Engenheiro de Prompt.

## Princípio

- **Este repositório é a fonte única dos modelos, regras e skills.** O chat de cada projeto lê os arquivos pelo app GitHub do ChatGPT (somente leitura), seguindo o `00_ROTA-DE-CONSULTA.md`.
- **Ponto de entrada: `00_ROTA-DE-CONSULTA.md`.** É a única cópia que vai para as fontes do projeto. Ela dá o nome do repositório, o caminho exato de cada arquivo e o que ler por situação (gerar prompt, validar resposta, atualizar estado, handoff).
- **Todo uso é rastreável.** Cada resposta abre com o bloco CONSULTA, que informa, por arquivo, a fonte (GitHub, Biblioteca, anexo, fonte do projeto ou não acessado).
- **O estado de um projeto nunca fica aqui.** `project-index.md`, `current-status.md` e `decisions.md` vivem só nas fontes do projeto a que pertencem.
- **Plano B declarado:** se o app GitHub não estiver disponível no chat, a rota permite a Biblioteca do ChatGPT ou um anexo, e o chat precisa dizer que usou o plano B.

## Mapa

| Caminho | Função | Como o chat lê |
|---|---|---|
| `00_ROTA-DE-CONSULTA.md` | Ponto de entrada: rota por situação, bloco CONSULTA e portão de conferência | Fontes de todo projeto (cópia) |
| `00_GUIA-DE-CONFIGURACAO.md` | Passo a passo de configuração e testes | Não |
| `01_instrucoes/instrucao-projeto.md` | Texto do campo de instruções do projeto (limite do campo: 8.000 caracteres) | No campo do projeto |
| `01_instrucoes/playbook-orquestrador.md` | Procedimentos detalhados | GitHub, pela rota |
| `02_modelos/PROMPT-modelo.md` | Seu modelo de prompt (inalterado) | GitHub, pela rota (cópia opcional nas fontes, como seguro) |
| `02_modelos/guia-preenchimento-prompt.md` | Como preencher cada campo | GitHub, pela rota |
| `02_modelos/modelo-resposta-agente.md` | Formato do relatório do agente | GitHub, pela rota |
| `02_modelos/kickoff-projeto.md` | Kickoff e Dossiê de Arquitetura | GitHub, pela rota |
| `03_continuidade/handoff-novo-chat.md` | Passagem de um chat para o próximo | GitHub, pela rota |
| `03_continuidade/*.template.md` | Modelos dos 3 arquivos de estado | GitHub, pela rota. Cada projeto cria os arquivos reais a partir deles |
| `04_skills/skills-catalog.md` | Índice de skills: links com commit fixado | GitHub, pela rota |
| `kit-operacional.md` | Consolidado de playbook + modelos | **Opcional:** fallback nas fontes do projeto, só se o GitHub não for legível |

## Fontes de cada projeto

1. `00_ROTA-DE-CONSULTA.md`
2. `project-index.md` (o real, criado do template)
3. `current-status.md` (o real)
4. `decisions.md` (o real)

Opcional: `PROMPT-modelo.md`, como seguro se o app GitHub não funcionar nos chats do projeto. Os `*.template.md` só entram nas fontes enquanto o arquivo real correspondente não existe.

## Manutenção

- **Um commit na `main` vale para todos os projetos de imediato**, porque não há versão por projeto. Para congelar uma versão, crie uma tag (por exemplo, `kit-1.0.0`) e aponte a rota para ela.
- Alterou qualquer modelo ou regra: subir a versão do kit e regenerar o `kit-operacional.md`. Registrar a troca em `decisions.md` do projeto.
- Alterou a rota: subir a versão no cabeçalho dela e reenviá-la às fontes dos projetos. É a única cópia fora do repositório.
- O repositório é privado. Nunca guardar segredos, tokens ou credenciais nele.
