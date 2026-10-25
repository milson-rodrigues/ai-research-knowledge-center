# 00_ROTA-DE-CONSULTA.md — bootstrap estável

**Função:** ponto de entrada permanente nas fontes de cada projeto. Este arquivo é estável e não replica os fluxos operacionais do kit.

## Fonte canônica

- **Repositório:** `milson-rodrigues/ai-research-knowledge-center`
- **Branch:** `main`
- **Índice operacional e roteador:** [`00_GUIA-DE-CONFIGURACAO.md`](https://github.com/milson-rodrigues/ai-research-knowledge-center/blob/main/00_GUIA-DE-CONFIGURACAO.md)

## Procedimento

Para cada solicitação relevante que use o kit:

1. Consulte no GitHub a versão atual de `00_GUIA-DE-CONFIGURACAO.md`, na branch `main`.
2. Identifique a intenção do usuário e siga somente o fluxo indicado pelo guia e suas dependências obrigatórias.
3. Consulte os documentos especializados pelos caminhos indicados no fluxo; não faça leitura integral do repositório por padrão.
4. Leia os arquivos reais de estado do projeto no destino identificado pelo fluxo.
5. Em respostas de planejamento, prompts, arquitetura, validação e continuidade, apresente uma tabela `CONSULTA` com as fontes realmente lidas e seus identificadores disponíveis.
6. Se o guia ou um arquivo obrigatório não puder ser acessado, marque a etapa dependente como `BLOQUEADO` e explique o caminho indisponível. Não use memória, cópias antigas ou Biblioteca como fallback silencioso.
7. Não afirme que um arquivo foi lido, encontrado, alterado ou salvo sem evidência da operação.
8. Preserve decisões aprovadas e contratos do projeto. Nunca inclua senhas, tokens ou credenciais.

## Estabilidade

Este bootstrap é permanente. Não o substitua por alterações comuns do kit. O roteamento, os aliases, os caminhos e os fluxos mutáveis são mantidos em `00_GUIA-DE-CONFIGURACAO.md`. A ponte `01_instrucoes/rota-operacional.md` também é estável e aponta para o mesmo guia.
