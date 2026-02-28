---
description: Workflow sistemático para limpar código, reduzir dívida técnica e aplicar Clean Architecture.
---

# /refactor - Refatoração Sistêmica e Clean Code

> **ARQUEOLOGIA TÉCNICA** - Remova o "cheiro de código" (code smell) e aplique padrões de elite do Orchard.

---

## 📋 Missão do Workflow

Este comando ativa o `@code-archaeologist` e o `@clean-code` especialista para:
1. **Identificar Dívida Técnica**: Código duplicado, funções Deus, variáveis confusas.
2. **Aplicar Padrões Modernos**: Decomposição de funções, SRP (Single Responsibility Principle).
3. **Melhorar a Legibilidade**: Auto-documentação e nomes significativos.
4. **Respeitar Contratos**: Garantir que as mudanças não quebrem as interfaces existentes.

---

## 🚀 Passos de Refatoração

### 1. Pesquisa e Análise
O Agente realiza um `grep_search` para encontrar padrões de dívida técnica ou foca no arquivo solicitado pelo usuário.

### 2. Deep Refactor Thinking (Interno)
- Quem depende deste arquivo? (Verifique Imports).
- Este código é crítico para o negócio (Gold) ou de suporte (Bronze)?
- Como posso reduzir a complexidade ciclomática?

### 3. Execução Modular
// turbo
1. `python .agent/skills/clean-code/scripts/complexity_analyzer.py .`
2. `python .agent/skills/lint-and-validate/scripts/lint_runner.py .`

### 4. Proposta de Mudança
O Agente apresenta um diff ou resumo das mudanças ANTES de aplicar:
- **Removido**: [Ex: Funções redundantes]
- **Melhorado**: [Ex: Tipagem de Props]
- **Nova Estrutura**: [Ex: Extração para Custom Hook]

---

## 🎯 Critérios de Aceitação

| Check | Regra Orchard |
| :--- | :--- |
| **SRP** | A função faz apenas UMA coisa após o refactor? |
| **Testes** | A refatoração manteve o comportamento original (sem breaking changes)? |
| **Lint** | O novo código passa 100% no lint/typescript? |
| **Nomes** | Os nomes são auto-explicativos (sem necessidade de comentários)? |

---

## 🛠️ Técnico

Este workflow utiliza os seguintes agentes e skills:
- **Agentes**: `@code-archaeologist`, `@debugger`, `@backend-specialist`.
- **Skills**: `clean-code`, `architecture`, `lint-and-validate`.

> 🔴 **Regra:** Nunca refatore sem entender o impacto emocional e técnico do código no sistema. Sempre valide com `@code-archaeologist` primeiro.
