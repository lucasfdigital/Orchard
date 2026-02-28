---
name: documentation-templates
description: Templates de documentação e diretrizes de estrutura. README, documentação de API, comentários de código e documentação amigável para IA.
allowed-tools: Read, Glob, Grep
---

# Templates de Documentação

> Templates e diretrizes de estrutura para tipos comuns de documentação.

---

## 1. Estrutura do README

### Seções Essenciais (Ordem de Prioridade)

| Seção | Propósito |
| :--- | :--- |
| **Título + Descrição Curta** | O que é isso? |
| **Início Rápido (Quick Start)** | Rodando em <5 min |
| **Funcionalidades** | O que eu posso fazer? |
| **Configuração** | Como customizar |
| **Referência da API** | Link para documentação detalhada |
| **Contribuição** | Como ajudar |
| **Licença** | Aspectos legais |

### Template de README

```markdown
# Nome do Projeto

Breve descrição em uma única linha.

## Início Rápido

[Passos mínimos para executar]

## Funcionalidades

- Funcionalidade 1
- Funcionalidade 2

## Configuração

| Variável | Descrição | Padrão |
| :--- | :--- | :--- |
| PORT | Porta do servidor | 3000 |

## Documentação

- [Referência da API](./docs/api.md)
- [Arquitetura](./docs/architecture.md)

## Licença

MIT
```

---

## 2. Estrutura de Documentação de API

### Template por Endpoint

```markdown
## GET /usuarios/:id

Obtém um usuário pelo ID.

**Parâmetros:**
| Nome | Tipo | Obrigatório | Descrição |
| :--- | :--- | :--- | :--- |
| id | string | Sim | ID do usuário |

**Resposta:**
- 200: Objeto do usuário
- 404: Usuário não encontrado

**Exemplo:**
[Exemplo de requisição e resposta]
```

---

## 3. Diretrizes de Comentários de Código

### Template JSDoc/TSDoc

```typescript
/**
 * Breve descrição do que a função faz.
 * 
 * @param paramName - Descrição do parâmetro
 * @returns Descrição do valor de retorno
 * @throws ErrorType - Quando este erro ocorre
 * 
 * @example
 * const result = nomeDaFuncao(entrada);
 */
```

### Quando Comentar

| ✅ Comente | ❌ NÃO Comente |
| :--- | :--- |
| O porquê (lógica de negócio) | O quê (óbvio) |
| Algoritmos complexos | Cada linha do código |
| Comportamento não óbvio | Código autoexplicativo |
| Contratos de API | Detalhes de implementação |

---

## 4. Template de Changelog (Mantenha um Changelog)

```markdown
# Changelog

## [Não lançado]
### Adicionado
- Nova funcionalidade

## [1.0.0] - 2025-01-01
### Adicionado
- Lançamento inicial
### Alterado
- Dependência atualizada
### Corrigido
- Correção de bug
```

---

## 5. Architecture Decision Record (ADR)

```markdown
# ADR-001: [Título]

## Status
Aceito / Obsoleto / Substituído

## Contexto
Por que estamos tomando esta decisão?

## Decisão
O que decidimos?

## Consequências
Quais são os trade-offs?
```

---

## 6. Documentação Amigável para IA (2025)

### Template llms.txt

Para crawlers e agentes de IA:

```markdown
# Nome do Projeto
> Objetivo em uma linha.

## Arquivos Principais
- [src/index.ts]: Ponto de entrada principal
- [src/api/]: Rotas da API
- [docs/]: Documentação

## Conceitos Chave
- Conceito 1: Breve explicação
- Conceito 2: Breve explicação
```

### Documentação Pronta para MCP

Para indexação RAG:
- Hierarquia clara de H1-H3.
- Exemplos JSON/YAML para estruturas de dados.
- Diagramas Mermaid para fluxos.
- Seções auto-contidas.

---

## 7. Princípios de Estrutura

| Princípio | Por que |
| :--- | :--- |
| **Escaneável** | Use cabeçalhos, listas e tabelas. |
| **Exemplos primeiro** | Mostre, não apenas fale. |
| **Detalhe progressivo** | Do Simples → Complexo. |
| **Atualizado** | Documentação desatualizada é enganosa. |

---

> **Lembre-se:** Templates são pontos de partida. Adapte-os às necessidades do seu projeto.
