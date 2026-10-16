# Guia de configuração (ChatGPT)

Rótulos: **FATO** = confirmado na documentação oficial da OpenAI, na tela do produto ou informado por você; **INFERÊNCIA** = dedução minha; **A VERIFICAR** = não confirmado; **RECOMENDAÇÃO** = decisão de projeto. Fontes e data da verificação no fim (2026-10-16).

## Parte 1: uma vez só (Biblioteca)

1. Na Biblioteca do ChatGPT (web), crie a pasta **ai-research-knowledge-center** e envie o conteúdo deste kit, com as subpastas (a sua Biblioteca já mostra as subpastas `01_instrucoes` a `04_skills`).
2. **FATO:** a Biblioteca está disponível na web, em Free, Go, Plus, Pro e Business, e em workspaces Enterprise, Edu e Healthcare, inclusive no EEE, Suíça e Reino Unido. Armazenamento: Free 500 MB, Go 4 GB, Plus e Business 20 GB, Pro 100 GB.
3. **FATO:** a referência automática a arquivos da Biblioteca é um controle de **dono de workspace**. A página não descreve esse controle para conta pessoal. **A VERIFICAR** se a sua conta lê a Biblioteca por conta própria.
4. **RECOMENDAÇÃO:** não conte com leitura automática. É para isso que existe o `00_ROTA-DE-CONSULTA.md`: ele entra nas fontes de todo projeto e manda o chat ler os modelos da Biblioteca por situação.

## Parte 2: para cada projeto novo

1. **Criar o projeto** e abrir Configurações do projeto (menu ••• do projeto).
2. **Memória.**
   - **FATO:** cada projeto usa memória **Padrão** ou **Project-only**, escolhida na criação ou alterada depois em Configurações do projeto → Memory (a mudança pode levar algumas horas). Em Project-only, memórias salvas não são referenciadas, os chats do projeto não referenciam conversas de fora e as de fora não referenciam as do projeto. Fora do Enterprise, a memória exige "Reference saved memories" e "Reference chat history" ligados.
   - **FATO (tela do projeto):** "Acesso à Biblioteca: Ativado" vale enquanto o projeto permanecer privado. Compartilhar o projeto desativa o acesso.
   - **A VERIFICAR:** se o acesso à Biblioteca depende do tipo de memória. A documentação não trata desse campo. Você relatou que depende; confira na tela ao trocar.
   - **RECOMENDAÇÃO:** testar Project-only, que isola o projeto. Se o acesso à Biblioteca deixar de funcionar, volte para Padrão. A instrução já proíbe usar outros chats ou projetos como fonte de estado.
3. **Instrução.** Cole o conteúdo de `01_instrucoes/instrucao-projeto.md` no campo Instruções.
   - **FATO:** as instruções do projeto valem só nele e substituem suas instruções personalizadas globais.
   - **FATO (informado por você):** o campo do projeto aceita até 8.000 caracteres; a instrução tem 4.140. A página de ajuda não cita esse limite.
   - **FATO:** instruções personalizadas globais têm 1.500 caracteres em Free e Go, e 5.000 nos demais planos. Não dependa delas.
4. **Fontes do projeto (5 arquivos).** Use o botão "Adicionar da Biblioteca" ou faça upload:
   - `00_ROTA-DE-CONSULTA.md`
   - `PROMPT-modelo.md`
   - `project-index.md`, `current-status.md`, `decisions.md`, criados a partir dos `.template.md`. No primeiro dia entram só com o cabeçalho. Quando o arquivo real existir, tire o template das fontes.
   - **FATO:** limite por projeto: Free 5, Go e Plus 25, Pro, Business, Edu e Enterprise 40. Só 10 arquivos podem ser enviados de uma vez. Arquivos salvos na Biblioteca não são apagados quando o projeto é excluído.
5. **Primeiro chat:** descreva a ideia. O chat abre com o bloco CONSULTA, lê os três arquivos de estado, faz o kickoff e devolve o Dossiê.

**Por que a rota nas fontes e não só a Biblioteca?**

| Opção | Vantagem | Desvantagem |
|---|---|---|
| Só Biblioteca | Um lugar para atualizar | Leitura automática não documentada em conta pessoal; falha silenciosa |
| Biblioteca + rota e `PROMPT-modelo.md` nas fontes (**recomendada**) | A leitura da rota é garantida; o desvio mais caro (prompt fora do modelo) fica coberto | Duas cópias a reenviar quando mudar |
| Tudo nas fontes | Máxima garantia | Ocupa vagas e diverge a cada mudança |

`kit-operacional.md` é fallback opcional: anexe-o às fontes só se a Biblioteca não for legível. O campo "Versão da rota em uso" do `project-index.md` mostra se um projeto ficou para trás.

## Parte 3: rotina a cada chat

1. Abra o chat dentro do projeto. O chat abre a resposta com o bloco CONSULTA e confirma o estado pelos três arquivos.
2. Trabalhe bloco a bloco: prompt, agente, relatório, validação.
3. Ao fechar bloco, decisão ou fase: o chat entrega os arquivos de estado **completos**; **você substitui** os arquivos nas fontes. O chat não edita as fontes.
4. **Handoff:** com o chat grande, escreva **"Gere o handoff deste chat."** O chat entrega `current-status.md` completo, `decisions.md` e `project-index.md` se mudaram, e o texto de abertura. Substitua as fontes, abra o novo chat **dentro do mesmo projeto** e cole só o texto de abertura. Se o chat avisar que não leu os arquivos, anexe os três na primeira mensagem.
5. Não suba arquivos de estado para a Biblioteca: lá ficam só os modelos.

## Parte 4: skills

Siga `04_skills/skills-catalog.md`.

- **FATO:** skills nativas do ChatGPT são oferecidas a Business, Enterprise, Healthcare e Edu elegíveis. A página não lista o plano Go, não descreve `@` e não menciona Projects.
- **RECOMENDAÇÃO:** use o catálogo como índice de links com commit fixado. O orquestrador cita a skill no prompt do bloco, e quem a consome é o executor.
- O `AUTHORIZED CHANGES` do prompt precisa autorizar o download daquele commit. O exemplo do guia de preenchimento proíbe rede por padrão.
- Aprove cada skill pelos critérios do catálogo antes do uso: um script de skill roda no ambiente do executor.

## Parte 5: testes de aceitação (eu não consigo executá-los por você)

Em um projeto de teste, confirme:

1. Cada resposta abre com o bloco CONSULTA, com os arquivos certos. Se um arquivo não abriu, o chat avisa em vez de improvisar.
2. O prompt gerado tem os títulos idênticos aos do `PROMPT-modelo.md`, incluindo `[AUTHORIZED CHANGES]`, e todos os campos de Header e Execution Configuration.
3. Modelo e esforço sugeridos são só os que você declarou ter; skill citada só se estiver no catálogo.
4. Com os arquivos de estado vazios ou só template, o chat avisa em vez de inventar estado.
5. Ao colar um relatório de agente inventado e sem evidências, ele recusa declarar sucesso e pede evidência.
6. Ao fechar o bloco, entrega o `current-status.md` completo, no formato do template.
7. "Gere o handoff deste chat." entrega os arquivos e o texto de abertura; um chat novo no mesmo projeto, com as fontes substituídas, recupera o estado só pelos arquivos.

Se um teste falhar, anote qual e ajuste a rota (suba a versão dela).

## Fontes

- Projects in ChatGPT: https://help.openai.com/en/articles/10169521-projects-in-chatgpt
- Using Library to manage files in ChatGPT: https://help.openai.com/en/articles/20001052-using-library-to-manage-files-in-chatgpt
- Skills in ChatGPT: https://help.openai.com/en/articles/20001066-skills-in-chatgpt
- Custom instructions: https://help.openai.com/en/articles/8096356-chatgpt-custom-instructions
- File uploads FAQ: https://help.openai.com/en/articles/8555545-file-uploads-faq
