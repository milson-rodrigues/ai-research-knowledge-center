# AI Research Knowledge Center

Kit versão **1.0.0** | Rota versão **1.3** | 2026-10-16

Biblioteca mestre para configurar o ChatGPT como Engenheiro Principal de Software, Orquestrador de Projetos com IA e Engenheiro de Prompt.

## Princípio

- **GitHub é o mestre versionado.** A pasta "ai-research-knowledge-center" na Biblioteca do ChatGPT é o espelho que os chats consultam. As fontes de cada projeto são o que o chat lê com certeza.
- **Ponto de entrada: `00_ROTA-DE-CONSULTA.md`.** Ele entra nas fontes de todo projeto e manda ler os modelos da Biblioteca conforme a situação (gerar prompt, validar resposta, atualizar estado, handoff). O chat abre cada resposta com o bloco CONSULTA, listando o que leu.
- **O estado de um projeto nunca fica aqui.** `project-index.md`, `current-status.md` e `decisions.md` vivem só nas fontes do projeto a que pertencem.

## Mapa

| Caminho | Função | Onde fica no ChatGPT |
|---|---|---|
| `00_ROTA-DE-CONSULTA.md` | Ponto de entrada: rota por situação e portão de conferência | Biblioteca **e** fontes de todo projeto |
| `00_GUIA-DE-CONFIGURACAO.md` | Passo a passo de configuração e testes | Não |
| `01_instrucoes/instrucao-projeto.md` | Texto do campo de instruções do projeto (limite do campo: 8.000 caracteres) | No campo do projeto |
| `01_instrucoes/playbook-orquestrador.md` | Procedimentos detalhados | Biblioteca (lido pela rota) |
| `02_modelos/PROMPT-modelo.md` | Seu modelo de prompt (inalterado) | Biblioteca **e** fontes de todo projeto (seguro contra falha de leitura) |
| `02_modelos/guia-preenchimento-prompt.md` | Como preencher cada campo | Biblioteca (lido pela rota) |
| `02_modelos/modelo-resposta-agente.md` | Formato do relatório do agente | Biblioteca (lido pela rota) |
| `02_modelos/kickoff-projeto.md` | Kickoff e Dossiê de Arquitetura | Biblioteca (lido pela rota) |
| `03_continuidade/handoff-novo-chat.md` | Passagem de um chat para o próximo | Biblioteca (lido pela rota) |
| `03_continuidade/*.template.md` | Modelos dos 3 arquivos de estado | Biblioteca. Cada projeto cria os arquivos reais a partir deles |
| `04_skills/skills-catalog.md` | Índice de skills: links com commit fixado | Biblioteca (lido pela rota) |
| `kit-operacional.md` | Consolidado de playbook + modelos | **Opcional:** fallback nas fontes do projeto, só se a Biblioteca não for legível |

## Fontes de cada projeto (5 arquivos)

1. `00_ROTA-DE-CONSULTA.md`
2. `PROMPT-modelo.md`
3. `project-index.md` (o real, criado do template)
4. `current-status.md` (o real)
5. `decisions.md` (o real)

Os `*.template.md` só entram nas fontes enquanto o arquivo real correspondente não existe.

## Manutenção

- Alterou qualquer modelo ou regra: subir a versão do kit, regenerar o `kit-operacional.md`, atualizar a Biblioteca e reenviar às fontes dos projetos os arquivos que estão lá (rota e `PROMPT-modelo.md`). Registrar a troca em `decisions.md` do projeto.
- Alterou só a rota: subir a versão no cabeçalho dela e reenviá-la às fontes dos projetos.
- A documentação da OpenAI não diz se um arquivo adicionado da Biblioteca ao projeto acompanha edições posteriores. Trate como cópia: depois de editar, reenvie.
- Nunca guardar segredos, tokens ou credenciais nesta pasta.
