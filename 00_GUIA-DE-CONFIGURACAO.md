# Guia de configuração (ChatGPT)

Rótulos: **FATO** = confirmado na documentação oficial da OpenAI, na tela do produto ou informado por você; **INFERÊNCIA** = dedução minha; **A VERIFICAR** = não confirmado; **RECOMENDAÇÃO** = decisão de projeto. Fontes e data da verificação no fim (2026-10-16).

## Parte 1: uma vez só (repositório e app GitHub)

1. **Repositório:** `milson-rodrigues/ai-research-knowledge-center`, branch `main`. **FATO (API do GitHub):** é privado.
2. **FATO (help.openai.com, "Connecting GitHub to ChatGPT"):** o app GitHub do ChatGPT recupera, sob demanda, conteúdo permitido do repositório (código, README e outros documentos). O acesso é ao vivo, sem índice, e **somente leitura**. Para escrever, a página aponta o Codex.
3. **FATO:** o app pode estar disponível no chat padrão, no deep research ou no agente, conforme plano, workspace e superfície. A página não lista planos e **não menciona Projects**.
4. **Ativar:** Configurações, Plugins (ou Apps), GitHub. Instale e autorize o app do ChatGPT no GitHub e escolha o repositório. **FATO:** repositórios levam cerca de 5 minutos para aparecer, e os privados só aparecem depois que o app é instalado para a conta certa e recebe acesso.
5. **FATO:** o seletor de repositórios do app busca nomes, não conteúdo. Por isso a rota informa o nome completo do repositório e o caminho exato de cada arquivo.
6. **A VERIFICAR:** se o app GitHub funciona dentro de chats de Projects na sua conta. É o primeiro teste da Parte 5.
7. **FATO:** o ChatGPT converte seus pedidos em consultas enviadas ao GitHub. Em conta pessoal, o uso para treinamento depende da opção "Improve the model for everyone". O repositório só tem modelos e regras, sem segredos.
8. **Plano B (opcional):** manter uma cópia dos arquivos na Biblioteca do ChatGPT. A rota só a usa se o app GitHub falhar, e o chat precisa declarar isso no bloco CONSULTA.

## Parte 2: para cada projeto novo

1. **Criar o projeto** e abrir Configurações do projeto (menu ••• do projeto).
2. **Memória.**
   - **FATO:** cada projeto usa memória **Padrão** ou **Project-only**, escolhida na criação ou alterada depois em Configurações do projeto → Memory (a mudança pode levar algumas horas). Em Project-only, memórias salvas não são referenciadas, os chats do projeto não referenciam conversas de fora e as de fora não referenciam as do projeto. Fora do Enterprise, a memória exige "Reference saved memories" e "Reference chat history" ligados.
   - **RECOMENDAÇÃO:** testar Project-only, que isola o projeto. A instrução já proíbe usar outros chats ou projetos como fonte de estado.
3. **Acesso à Biblioteca.**
   - **FATO (tela do projeto):** "Acesso à Biblioteca: Ativado" vale enquanto o projeto permanecer privado. Compartilhar o projeto desativa o acesso.
   - **RECOMENDAÇÃO:** para **testar o GitHub**, deixe o acesso à Biblioteca **Desativado**. Assim o chat não consegue cair no plano B sem você perceber. Reative depois, se quiser o plano B.
4. **Instrução.** Cole o conteúdo de `01_instrucoes/instrucao-projeto.md` no campo Instruções.
   - **FATO:** as instruções do projeto valem só nele e substituem suas instruções personalizadas globais.
   - **FATO (informado por você):** o campo do projeto aceita até 8.000 caracteres. A página de ajuda não cita esse limite.
   - **FATO:** instruções personalizadas globais têm 1.500 caracteres em Free e Go, e 5.000 nos demais planos. Não dependa delas.
5. **Fontes do projeto.** Adicione, por upload:
   - `00_ROTA-DE-CONSULTA.md`
   - `project-index.md`, `current-status.md`, `decisions.md`, criados a partir dos `.template.md`. No primeiro dia entram só com o cabeçalho. Quando o arquivo real existir, tire o template das fontes.
   - Opcional: `PROMPT-modelo.md`, como seguro, depois de validar que o GitHub funciona.
   - **FATO:** limite por projeto: Free 5, Go e Plus 25, Pro, Business, Edu e Enterprise 40. Só 10 arquivos podem ser enviados de uma vez.
6. **Primeiro chat:** descreva a ideia. O chat abre com o bloco CONSULTA, lê os três arquivos de estado, faz o kickoff e devolve o Dossiê.

**Onde guardar os modelos?**

| Opção | Vantagem | Desvantagem |
|---|---|---|
| GitHub como fonte, lido pelo app (**recomendada**) | Fonte única e versionada; sem reenviar arquivos; caminhos exatos | Depende do app estar disponível nos chats de projeto (não documentado); um commit na `main` muda todos os projetos de uma vez |
| Biblioteca do ChatGPT | Funcionou nos testes | Leitura automática não documentada em conta pessoal; reenvio manual a cada mudança |
| Tudo nas fontes do projeto | Máxima garantia de leitura | Ocupa vagas e diverge a cada mudança |

A rota é a única cópia fora do repositório. O campo "Versão da rota em uso" do `project-index.md` mostra se um projeto ficou para trás.

## Parte 3: rotina a cada chat

1. Abra o chat dentro do projeto. Ele abre a resposta com o bloco CONSULTA e confirma o estado pelos três arquivos.
2. Trabalhe bloco a bloco: prompt, agente, relatório, validação.
3. Ao fechar bloco, decisão ou fase: o chat entrega os arquivos de estado **completos**; **você substitui** os arquivos nas fontes. O chat não edita as fontes nem o repositório.
4. **Handoff:** com o chat grande, escreva **"Gere o handoff deste chat."** O chat entrega `current-status.md` completo, `decisions.md` e `project-index.md` se mudaram, e o texto de abertura. Substitua as fontes, abra o novo chat **dentro do mesmo projeto** e cole só o texto de abertura. Se o chat avisar que não leu os arquivos, anexe os três na primeira mensagem.
5. Não coloque arquivos de estado no repositório do kit: lá ficam só os modelos.

## Parte 4: skills

Siga `04_skills/skills-catalog.md`.

- **FATO:** skills nativas do ChatGPT são oferecidas a Business, Enterprise, Healthcare e Edu elegíveis. A página não lista o plano Go, não descreve `@` e não menciona Projects.
- **RECOMENDAÇÃO:** use o catálogo como índice de links com commit fixado. O orquestrador cita a skill no prompt do bloco, e quem a consome é o executor.
- O `AUTHORIZED CHANGES` do prompt precisa autorizar o download daquele commit. O exemplo do guia de preenchimento proíbe rede por padrão.
- Aprove cada skill pelos critérios do catálogo antes do uso: um script de skill roda no ambiente do executor.

## Parte 5: testes de aceitação (eu não consigo executá-los por você)

**Teste do GitHub** (projeto com Biblioteca desativada e só a rota nas fontes):

1. Peça: "Gere um prompt para fazer uma varredura de tudo que já foi criado, para darmos continuidade com o projeto."
2. No bloco CONSULTA, os arquivos de `02_modelos` e do playbook aparecem com **Fonte = GitHub**, com caminho e identificador (commit ou URL) ou `sem identificador`.
3. Se o chat disser que não tem o app GitHub neste chat, anote a mensagem exata. É a resposta ao item A VERIFICAR da Parte 1.

**Testes de qualidade** (em um projeto de teste):

4. O prompt tem os títulos idênticos aos do `PROMPT-modelo.md`, todos os campos de Header e Execution Configuration, e `[OUTPUT]` exigindo o relatório no formato `modelo-resposta-agente.md`.
5. Modelo e esforço sugeridos são só os que você declarou (ou `[A CONFIRMAR]`); skill citada só se estiver no catálogo.
6. Com os arquivos de estado vazios ou só template, o chat avisa em vez de inventar estado.
7. Ao colar um relatório de agente inventado e sem evidências, ele recusa declarar sucesso e pede evidência.
8. Ao fechar o bloco, entrega o `current-status.md` completo, no formato do template.
9. "Gere o handoff deste chat." entrega os arquivos e o texto de abertura; um chat novo no mesmo projeto, com as fontes substituídas, recupera o estado só pelos arquivos.

Se um teste falhar, anote qual e ajuste a rota (suba a versão dela).

## Fontes

- Connecting GitHub to ChatGPT: https://help.openai.com/en/articles/11145903-connecting-github-to-chatgpt
- Projects in ChatGPT: https://help.openai.com/en/articles/10169521-projects-in-chatgpt
- Using Library to manage files in ChatGPT: https://help.openai.com/en/articles/20001052-using-library-to-manage-files-in-chatgpt
- Skills in ChatGPT: https://help.openai.com/en/articles/20001066-skills-in-chatgpt
- Custom instructions: https://help.openai.com/en/articles/8096356-chatgpt-custom-instructions
- File uploads FAQ: https://help.openai.com/en/articles/8555545-file-uploads-faq
