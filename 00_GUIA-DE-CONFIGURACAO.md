# Guia de configuração (ChatGPT)

Rótulos: **FATO** = confirmado na documentação da OpenAI; **A VERIFICAR** = depende do seu plano/tela e não pude confirmar; **RECOMENDAÇÃO** = decisão de projeto.

## Parte 1: uma vez só (Library)

1. Na Library do ChatGPT (web), abra a pasta **IA Resource Knowledge Center** e envie o conteúdo deste kit mantendo as subpastas, se a Library aceitar subpastas (**A VERIFICAR**; senão, envie os arquivos soltos com os mesmos nomes).
2. **FATO:** a Library só está disponível na web e em planos específicos (Plus, Pro, Business, fora de EEE, Suíça e Reino Unido). **A VERIFICAR** o seu caso.
3. **FATO:** quando existe a configuração de busca na Library, ela controla se o ChatGPT busca arquivos da Library sozinho; desligada, você ainda pode anexar manualmente. Por isso o kit não depende da Library para operar (parte 2).

## Parte 2: para cada projeto novo

1. **Criar o projeto.** Sobre a memória: o projeto pode usar memória exclusiva (só os chats e arquivos dele) ou a memória padrão (que enxerga também a memória geral da sua conta).
   - **RECOMENDAÇÃO:** memória exclusiva do projeto, para a continuidade vir só dos arquivos do projeto e nada vazar de outros contextos.
   - **A VERIFICAR (fonte secundária):** ela só pode ser escolhida **na criação** e não pode ser adicionada depois; também exige a memória pessoal ligada nas configurações. Confira a tela de criação.
2. **Colar a instrução.** Abra o menu do projeto (•••) → Configurações do projeto → instruções, e cole o conteúdo de `01_instrucoes/instrucao-projeto.md`.
   - **FATO:** as instruções do projeto valem só nele e substituem suas instruções personalizadas globais.
   - **A VERIFICAR:** o limite de caracteres do campo. Se não couber, mantenha só os blocos FONTES E CONTINUIDADE, CONDUTA e PROMPTS no campo; o restante já está no `playbook-orquestrador.md`.
3. **Adicionar às fontes do projeto (4 arquivos):**
   - `kit-operacional.md` (cópia do kit)
   - `project-index.md`, `current-status.md`, `decisions.md` (criados a partir dos `.template.md`, preenchidos no kickoff; no primeiro dia podem entrar só com o cabeçalho)
   - Opcional: `skills-catalog.md`, quando o projeto usar skills.
   - **FATO:** os arquivos do projeto entram como contexto dos chats dele. **A VERIFICAR:** o limite de arquivos do seu plano (Business/Enterprise/Edu: 40).
4. **Iniciar o primeiro chat** descrevendo a ideia. O orquestrador deve ler os três arquivos, fazer o kickoff e devolver o Dossiê.

**Por que cópia do kit em cada projeto e não só a Library?** Comparação:

| Opção | Vantagem | Desvantagem |
|---|---|---|
| Só Library | Uma cópia só, sem divergência | Leitura automática não garantida; chat pode agir sem o playbook |
| Cópia em cada projeto (**recomendada**) | Garante o playbook no contexto do projeto | Pode ficar desatualizada; exige atualizar os projetos ativos ao mudar a versão |

A divergência é controlada pela versão do kit (README) e pelo campo "Versão do kit em uso" no `project-index.md`.

## Parte 3: rotina a cada chat

1. Abrir o chat dentro do projeto. O orquestrador lê os três arquivos e confirma o estado.
2. Trabalhar bloco a bloco: prompt → agente → relatório → validação.
3. Ao fechar bloco ou fase: o ChatGPT entrega os arquivos atualizados; **você substitui** os arquivos nas fontes do projeto (ele não edita fontes sozinho; **A VERIFICAR** se seu plano oferece edição direta).
4. Chat longo ou fase fechada: seguir `handoff-novo-chat.md` e abrir chat novo no mesmo projeto.

## Parte 4: skills

Seguir `04_skills/skills-catalog.md`. Resumo: instalar como Skill só as de uso constante (se o plano permitir), manter no catálogo a versão fixada e a data de revisão, e não usar link do GitHub como fonte única. Disponibilidade de Skills no ChatGPT: **A VERIFICAR** no artigo "Skills in ChatGPT" (help.openai.com).

## Parte 5: testes de aceitação (eu não consigo executá-los por você)

Crie um projeto de teste (ex.: "editor de imagens") e confirme:

1. O chat lê `project-index.md`, `current-status.md` e `decisions.md` e confirma o estado antes de agir. Com os arquivos vazios, ele avisa em vez de inventar estado.
2. Faz perguntas só sobre lacunas que mudam decisão (não despeja um questionário).
3. Devolve alternativas comparadas (vantagens, desvantagens, complexidade, risco) e pesquisa fonte atual para tecnologias.
4. Entrega o prompt do bloco no formato completo do `PROMPT-modelo.md`, em bloco de código, com modelo/esforço de acordo com o que você informou ter.
5. Ao colar um relatório de agente inventado e sem evidências, ele recusa declarar sucesso e pede evidência.
6. Ao fechar o bloco, entrega `current-status.md` atualizado completo.
7. O handoff abre um chat novo que recupera o estado só pelos arquivos.

Se um teste falhar, anote qual e ajuste a instrução (subir a versão do kit).
