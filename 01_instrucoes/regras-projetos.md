# Regras transversais de projeto

**Status:** vigente no kit a partir da versão 1.1.0.  
**Escopo:** princípios para manutenção e evolução de projetos que usam o kit.

Este documento complementa o playbook e as regras de prompt. Não substitui decisões aprovadas, contratos nem a documentação canônica do projeto.

## 1. Fonte de verdade

- Obtenha o estado específico do projeto a partir de seus arquivos canônicos.
- Diferencie documentação normativa, decisões aprovadas, propostas e notas de execução.
- Não trate exemplos ou templates como dados reais do projeto.
- Se fontes conflitarem, registre o conflito e resolva-o antes de uma mudança que dependa dele.

## 2. Arquitetura e contratos

Antes de alterar arquitetura ou interfaces:

1. identifique módulos, consumidores e contratos afetados;
2. confirme padrões e decisões aprovados;
3. avalie impacto em compatibilidade, dados, segurança, desempenho e manutenção;
4. compare alternativas para decisões técnicas relevantes;
5. prefira a mudança mínima que resolva o problema sem criar acoplamento desnecessário.

Não introduza frameworks, dependências ou abstrações apenas por preferência pessoal ou popularidade.

## 3. Preservação de comportamento

- Preserve comportamentos fora do escopo.
- Evite refatorações oportunistas junto de funcionalidades novas.
- Não altere código estável ou de produção sem justificativa explícita, autorização, análise de impacto e validação proporcional.
- Mudanças envolvendo dados, autenticação, migração ou produção exigem rigor adicional em revisão, testes e reversão.
- Se uma alteração inesperada se tornar necessária, interrompa o caminho afetado e obtenha autorização antes de ampliar o escopo.

## 4. Qualidade contínua

Avalie de forma proporcional: manutenibilidade; coerência arquitetural; extensibilidade; desempenho e recursos; segurança e privacidade; custo operacional; complexidade adicionada versus benefício; observabilidade e diagnóstico.

Qualidade não é justificativa automática para refatorar. Explique o problema observado, benefício esperado, risco e alternativa de não mudar.

## 5. Decisões e evolução

- Registre como decisão somente o que o usuário aprovou.
- Inclua contexto, alternativas, justificativa, consequências e condição de reavaliação quando relevante.
- Mantenha propostas e hipóteses separadas do registro de decisões.
- Atualize documentação canônica e referências dependentes após aprovação.
- Não mantenha cópias divergentes de regras sem definir qual é a fonte oficial.

## 6. Proporcionalidade e evidências

A profundidade da análise deve acompanhar o risco, o impacto e a reversibilidade. Registre testes e evidências reais; declare limitações, riscos e validações pendentes. Não assuma que uma mudança é segura apenas porque é pequena, nem que uma tarefa simples exige uma revisão arquitetural completa.
