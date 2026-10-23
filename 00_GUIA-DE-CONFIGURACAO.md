# Guia de configuração do AI Research Knowledge Center

Este guia explica a instalação inicial e o uso diário. O **GitHub é a única fonte canônica dos documentos globais do kit**. A cópia de `00_ROTA-DE-CONSULTA.md` adicionada às fontes de cada projeto funciona como bootstrap permanente: a árvore operacional e as regras atuais são consultadas diretamente no GitHub a cada solicitação relevante.

## 1. Configuração única do acesso ao GitHub

1. Conecte o app GitHub ao ChatGPT em **Configurações → Apps/Plugins → GitHub**, autorize a conta e conceda acesso ao repositório `milson-rodrigues/ai-research-knowledge-center`.
2. O app GitHub do ChatGPT recupera conteúdo permitido do repositório sob demanda e é somente leitura; ele não publica alterações. A disponibilidade pode variar por plano e superfície do produto. Consulte a [documentação oficial de conexão com o GitHub](https://help.openai.com/en/articles/11145903-connecting-github-to-chatgpt).
3. Teste se o chat dentro de Projects consegue ler arquivos do repositório. Se não conseguir, trate a etapa que depende deles como `BLOQUEADO`; não troque silenciosamente para cópias antigas nem para a Biblioteca.
4. O seletor do app procura repositórios, não o conteúdo dos arquivos. Para leitura, informe o repositório e o caminho exato.

## 2. Configurar cada projeto do ChatGPT

1. Crie um projeto e adicione nas instruções o conteúdo atual de [`01_instrucoes/instrucao-projeto.md`](https://github.com/milson-rodrigues/ai-research-knowledge-center/blob/main/01_instrucoes/instrucao-projeto.md).
2. Em **Fontes do projeto**, adicione uma única vez [`00_ROTA-DE-CONSULTA.md`](https://github.com/milson-rodrigues/ai-research-knowledge-center/blob/main/00_ROTA-DE-CONSULTA.md). Esse arquivo é um bootstrap estável. Não será necessário substituí-lo por alterações comuns de regras, modelos, metodologias ou rotas: o chat consulta a rota dinâmica em `01_instrucoes/rota-operacional.md` diretamente no GitHub.
3. Mantenha os três arquivos de estado específicos do projeto nas fontes do projeto ou no repositório do próprio projeto:
   - `project-index.<projeto>.md`
   - `current-status.<projeto>.md`
   - `decisions.<projeto>.md`
   
   Na inicialização, crie-os a partir dos templates em `03_continuidade/`. Não os coloque no repositório global do kit.
4. **Não envie modelos, regras ou metodologias do kit para duplicar o conteúdo do GitHub.** Esses arquivos devem ser lidos sob demanda do repositório canônico.
5. Como recomendação, configure a memória do projeto conforme seu objetivo e isolamento de contexto. Consulte [Projects no ChatGPT](https://help.openai.com/en/articles/10169521-projects-in-chatgpt) para as opções atuais.

## 3. Fluxo de cada chat

1. O chat lê o bootstrap permanente nas fontes e consulta no GitHub a rota operacional atual.
2. Classifica a solicitação na árvore da rota: projeto novo, novo prompt/implementação, correção de bug, validação da execução, decisão de arquitetura, pesquisa/skill ou continuidade.
3. Busca no GitHub os documentos globais pertinentes e o estado específico do projeto. Abre respostas estruturadas com uma tabela `CONSULTA`.
4. Se faltar uma informação indispensável, faz perguntas objetivas; se houver contexto suficiente, entrega o artefato correspondente no formato do kit.
5. Para trabalho executável, prepara um prompt completo no formato de `02_modelos/PROMPT-modelo.md`, exigindo o relatório de execução padronizado.
6. O usuário envia esse prompt ao agente executor e devolve o relatório.
7. O chat compara critérios, alterações e testes com as evidências; classifica o resultado e decide se é possível avançar ou se é necessário corrigir.
8. No fechamento de bloco/fase, o chat entrega os arquivos de continuidade completos que mudaram. O usuário os salva nas fontes do projeto ou no repositório específico. O chat não afirma ter atualizado fontes por conta própria.

## 4. Limites importantes

- **GitHub do kit:** regras, modelos, instruções e metodologias globais. Essa é a fonte canônica, lida sob demanda.
- **GitHub do projeto / fontes do projeto ChatGPT:** estado real do trabalho, decisões aprovadas, relatórios e contexto específico. Identifique sempre qual fonte foi consultada.
- **Sem acesso ao GitHub:** não usar a Biblioteca do ChatGPT como plano B. Declarar o bloqueio e solicitar que o acesso ao GitHub seja restabelecido.
- **Agente executor:** é quem executa alterações concretas no código. O kit organiza e valida o processo, mas não substitui esse executor.
- **Decisões:** registrar em `decisions.md` somente após aprovação do usuário.
- **Segurança:** nunca salvar tokens, senhas ou credenciais em instruções, prompts ou arquivos de estado.

## 5. Testes de aceitação

Execute estes testes em um projeto de teste antes de confiar no fluxo para tarefas críticas.

| Teste | Procedimento | Resultado esperado |
|---|---|---|
| Leitura dinâmica | Peça um prompt e examine a tabela `CONSULTA` | A rota operacional e documentos de modelo/regras aparecem como fontes GitHub com caminho e identificador quando disponível |
| Bootstrap permanente | Altere um documento de regra no GitHub e faça novo pedido sem substituir o arquivo de fontes | O chat lê o documento/rota atual da `main`, não usa a versão antiga da conversa |
| Modelo do prompt | Peça um prompt executável | Os títulos e campos seguem o modelo atual e o relatório do executor é exigido |
| Estado desconhecido | Inicie sem arquivos reais de estado | O chat usa template claramente identificado; não inventa histórico ou decisões |
| Relatório sem evidências | Forneça um relatório que afirma sucesso sem testes ou evidências | O chat não marca `CONCLUÍDO`; solicita evidências ou identifica o bloqueio |
| Handoff | Peça o fechamento e inicie um novo chat no mesmo projeto | Os arquivos entregues preservam estado, decisões e próxima ação sem depender da memória do chat |

Se um teste falhar, registre o cenário, o comportamento observado e o arquivo canônico relacionado. Corrija primeiro o protocolo no GitHub; não peça para substituir o bootstrap por mudanças comuns no kit.

## Referências oficiais

- [Connecting GitHub to ChatGPT](https://help.openai.com/en/articles/11145903-connecting-github-to-chatgpt)
- [Projects in ChatGPT](https://help.openai.com/en/articles/10169521-projects-in-chatgpt)
