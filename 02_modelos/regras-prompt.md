# Regras para elaboração e execução de prompts

**Status:** vigente no kit a partir da versão 1.1.0.  
**Finalidade:** definir requisitos normativos para prompts de engenharia sem duplicar o fluxo operacional do playbook.

## 1. Grounding, fontes e precisão

1. Use arquivos canônicos do projeto e decisões aprovadas como fonte do contexto.
2. Para versões, APIs, capacidades de modelos e comportamentos mutáveis, priorize documentação oficial atual.
3. Separe fatos confirmados, inferências, hipóteses e recomendações quando a distinção afetar uma decisão.
4. Não invente arquivos, funcionalidades, dependências, resultados de comandos, testes executados ou evidências.
5. Se uma fonte necessária estiver indisponível, declare a limitação e seu impacto. Não reconstrua seu conteúdo de memória.
6. Identifique as fontes usadas quando fundamentarem uma decisão técnica relevante.

## 2. Análise antes da execução

Antes de autorizar alterações, identifique o objetivo verificável, escopo e fora de escopo, contexto confirmado, decisões aprovadas, contratos a preservar, arquivos autorizados, operações proibidas, dependências, riscos, critérios de aceite, testes e evidências esperadas. Defina condições de interrupção e reversão quando o risco justificar.

Peça esclarecimento quando faltar informação indispensável. Se a incerteza não impedir uma etapa segura de pesquisa ou planejamento, registre-a e limite o trabalho ao que pode ser comprovado.

## 3. Execução por blocos

Para trabalhos com múltiplas etapas, cada bloco deve conter:

1. objetivo e resultado verificável;
2. escopo autorizado;
3. dependências explícitas;
4. risco e reversibilidade;
5. critérios de aceite;
6. testes e evidências;
7. condição para avançar ou interromper.

Respeite dependências obrigatórias. Entre blocos prontos, balanceie risco, custo, benefício e reversibilidade. Valide o bloco atual antes de iniciar o próximo. Não implemente tudo de uma vez quando isso dificultar o isolamento de falhas ou aumentar o risco.

## 4. Proteção da codebase

- Não altere arquivos ou áreas fora de `AUTHORIZED CHANGES`.
- Não misture refatoração ampla com funcionalidade nova sem justificativa e autorização.
- Preserve contratos, compatibilidade e comportamentos existentes fora do escopo.
- Mudanças em código estável ou de produção exigem justificativa explícita, autorização, análise de impacto e validação adequada.
- A proteção do código não é uma proibição absoluta de corrigir defeitos: a mudança deve ser necessária, delimitada, autorizada, testada e documentada.
- Se for preciso ampliar o escopo, interrompa a alteração afetada e peça autorização antes de continuar.

## 5. Quality Gate

Avalie conforme o risco e o escopo:

- **Manutenibilidade:** facilidade de corrigir, entender e modificar.
- **Arquitetura:** aderência a fronteiras, responsabilidades, contratos e padrões aprovados.
- **Extensibilidade:** possibilidade de ampliar capacidades sem refatoração desnecessária.
- **Desempenho:** gargalos evitáveis, regressões e custos operacionais relevantes.
- **Proporcionalidade:** benefício esperado versus complexidade, custo e superfície de falha.

Não exija refatorações ou medições sem relação com a tarefa. Registre riscos e justifique quando um critério não for aplicável.

## 6. Testes e evidências

1. Defina testes proporcionais ao risco antes da execução.
2. Considere caminhos de sucesso, casos de borda e falhas quando pertinentes.
3. Execute testes unitários, de integração e regressão mínima quando disponíveis e apropriados.
4. Separe testes **executados**, **não executados** e **bloqueados**, com motivo.
5. Não marque critério como concluído sem evidência compatível.
6. Se não for possível executar testes, declare o que continua sem verificação e ajuste o status final.

## 7. Auditabilidade e comunicação

O relatório deve permitir reconstruir o ocorrido: arquivos criados/alterados/removidos; comandos e testes realmente executados; evidência por critério; desvios e justificativas; riscos e pendências; comparação entre estado esperado e verificado.

Comunique bloqueios e mudanças de escopo quando forem identificados. Não apresente proposta como decisão aprovada.

## 8. Decisões

- Use o arquivo canônico de decisões do projeto para decisões aprovadas.
- Registre alternativas, justificativa, consequências e fontes relevantes.
- Mantenha propostas, hipóteses e questões em aberto separadas das decisões definitivas.
- Use identificadores como `D-001` ou `#DECISAO` somente conforme a convenção adotada no projeto; não crie outra fonte de verdade.

## 9. Conflitos e conclusão

Se documentos ou instruções entrarem em conflito, identifique os arquivos e a regra conflitante. Não emita instruções contraditórias. Respeite requisitos explícitos aprovados e restrições de segurança; peça decisão quando o conflito afetar escopo, arquitetura ou comportamento; atualize a documentação canônica após aprovação.

Um prompt está pronto quando segue a estrutura do modelo, tem objetivo e critérios verificáveis, define autorização e limites, incorpora as regras pertinentes, explicita dependências/testes/evidências, exige o relatório padronizado e não apresenta fatos sem suporte.
