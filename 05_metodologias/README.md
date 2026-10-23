# Metodologias de engenharia

Este diretório reúne procedimentos especializados que o orquestrador seleciona conforme o tipo e o risco da tarefa.

## Como escolher

| Metodologia | Usar quando | Resultado esperado |
|---|---|---|
| [Decomposição de tarefas](decomposicao-tarefas.md) | O trabalho envolve etapas ou dependências | Blocos ordenados, critérios e condições para avançar |
| [TDD](tdd.md) | Há comportamento testável a implementar ou corrigir | Ciclo Red → Green → Refactor com evidência de testes |
| [Diagnóstico de bugs](diagnostico-bugs.md) | A causa não está confirmada | Causa sustentada por evidência e correção com teste de regressão |
| [Revisão de código](revisao-codigo.md) | Existe um diff ou implementação a avaliar | Revisão independente da especificação, qualidade e riscos |

## Regras de uso

- Metodologias complementam, mas não substituem, `02_modelos/regras-prompt.md` e `01_instrucoes/playbook-orquestrador.md`.
- Escolha apenas as pertinentes; não aplique todas por padrão.
- Não declare uma metodologia executada sem apresentar atividades e evidências correspondentes.
- Inclua no prompt as etapas essenciais se o executor não tiver acesso ao arquivo.
- Se faltar uma condição para cumprir uma etapa (por exemplo, infraestrutura de testes), registre a limitação.

## Inspiração externa

A organização em práticas pequenas e combináveis é inspirada, entre outras referências, por [Matt Pocock — Skills for Real Engineers](https://github.com/mattpocock/skills). Este kit adapta os princípios ao seu próprio fluxo; não instala nem reproduz automaticamente skills externas.
