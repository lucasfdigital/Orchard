---
name: architecture
description: Framework de tomada de decisão arquitetural. Análise de requisitos, avaliação de trade-offs, documentação ADR. Use ao tomar decisões de arquitetura ou analisar o design do sistema.
allowed-tools: Read, Glob, Grep
---

# Framework de Decisão de Arquitetura

> "Requisitos impulsionam a arquitetura. Trade-offs informam as decisões. ADRs capturam a justificativa."

## 🎯 Regra de Leitura Seletiva

**Leia APENAS os arquivos relevantes para a solicitação!** Verifique o mapa de conteúdo e encontre o que precisa.

| Arquivo | Descrição | Quando Ler |
| :--- | :--- | :--- |
| `context-discovery.md` | Perguntas a fazer, classificação do projeto | Ao iniciar o design da arquitetura |
| `trade-off-analysis.md` | Templates de ADR, framework de trade-off | Ao documentar decisões |
| `pattern-selection.md` | Árvores de decisão, anti-padrões | Ao escolher padrões |
| `examples.md` | Exemplos de MVP, SaaS, Enterprise | Implementações de referência |
| `patterns-reference.md` | Consulta rápida para padrões | Comparação de padrões |

---

## 🔗 Skills Relacionadas

| Skill | Use Para |
| :--- | :--- |
| `@[skills/database-design]` | Design de schema de banco de dados |
| `@[skills/api-patterns]` | Padrões de design de API |
| `@[skills/deployment-procedures]` | Arquitetura de implantação |

---

## Princípio Central

**"A simplicidade é o último grau de sofisticação."**

- Comece simples.
- Adicione complexidade APENAS quando provado ser necessário.
- Você sempre pode adicionar padrões mais tarde.
- Remover complexidade é MUITO mais difícil do que adicioná-la.

---

## Checklist de Validação

Antes de finalizar a arquitetura:

- [ ] Requisitos claramente compreendidos.
- [ ] Restrições identificadas.
- [ ] Cada decisão possui análise de trade-off.
- [ ] Alternativas mais simples foram consideradas.
- [ ] ADRs (Architecture Decision Records) escritos para decisões significativas.
- [ ] A experiência da equipe corresponde aos padrões escolhidos.
