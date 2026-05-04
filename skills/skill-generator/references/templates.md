# Templates de Skills — Referência Rápida

> Use estes templates como ponto de partida. **Sempre adapte ao domínio específico.**

---

## Template A: Skill de Princípios

```markdown
---
name: nome-da-skill
description: >
  [O que esta skill capacita]. Use ao [contexto específico].
  Ativado por: "palavra1", "palavra2", "palavra3".
version: 1.0.0
allowed-tools: Read, Glob, Grep
---

# [Nome Legível]

> [Propósito em 1 linha.]

---

## Quando Usar

- [Situação 1]
- [Situação 2]
- [Situação 3]

---

## Princípio Central

> **[Declare a filosofia em uma frase de impacto.]**

---

## Processo de Decisão

Antes de [ação principal], responda:

1. **[Pergunta de contexto]** → Determina [consequência]
2. **[Pergunta de restrição]** → Determina [consequência]
3. **[Pergunta de objetivo]** → Determina [consequência]

---

## Árvore de Decisão

| Situação | Decisão Recomendada | Por quê |
| :--- | :--- | :--- |
| [caso A] | [ação] | [razão técnica/de negócio] |
| [caso B] | [ação] | [razão técnica/de negócio] |
| [caso C] | [ação] | [razão técnica/de negócio] |

---

## O Que Fazer

✅ [Ação recomendada 1]
✅ [Ação recomendada 2]
✅ [Ação recomendada 3]

## O Que NÃO Fazer

❌ [Anti-padrão 1] — porque [consequência]
❌ [Anti-padrão 2] — porque [consequência]

---

## Anti-Padrões

| Anti-Padrão | Por quê é ruim |
| :--- | :--- |
| [problema específico] | [consequência concreta] |
| [problema específico] | [consequência concreta] |
```

---

## Template B: Skill de Execução

```markdown
---
name: nome-da-skill
description: >
  [O que esta skill executa]. Use ao [contexto específico].
  Ativado por: "palavra1", "palavra2".
version: 1.0.0
allowed-tools: Read, Write, Edit, Glob, Grep
---

# [Nome Legível]

> [Propósito em 1 linha.]

---

## Quando Usar

- [Situação 1]
- [Situação 2]

---

## Pré-requisitos

- [ ] [O que deve existir antes]
- [ ] [Dependência ou configuração necessária]

---

## Protocolo de Execução

### Fase 1: [Nome da Fase]

**Objetivo:** [O que esta fase alcança]

```
Passo 1.1: [Instrução específica]
→ Verificação: [Como confirmar sucesso]

Passo 1.2: [Instrução específica]
→ Verificação: [Como confirmar sucesso]
```

### Fase 2: [Nome da Fase]

**Objetivo:** [O que esta fase alcança]

```
Passo 2.1: [Instrução específica]
→ Verificação: [Como confirmar sucesso]
```

---

## Formato de Saída (OBRIGATÓRIO)

```markdown
[Template exato do output esperado]
```

---

## Checklist de Conclusão

- [ ] [Critério 1 de "pronto"]
- [ ] [Critério 2 de "pronto"]
- [ ] [Critério 3 de "pronto"]

---

## Anti-Padrões

| Anti-Padrão | Por quê é ruim |
| :--- | :--- |
| [problema] | [consequência] |
```

---

## Template C: Skill de Orquestração

```markdown
---
name: nome-da-skill
description: >
  Orquestra [componentes/agentes/skills] para [objetivo].
  Use ao [contexto]. Ativado por: "palavra1", "palavra2".
version: 1.0.0
allowed-tools: Read, Write, Edit, Glob, Grep, Agent
---

# [Nome Legível] — Orquestrador de [Domínio]

> [Propósito em 1 linha.]

---

## 🗺️ Mapa de Conteúdo

**Leia APENAS os arquivos relevantes para a solicitação:**

| Arquivo | Descrição | Quando Ler |
| :--- | :--- | :--- |
| `references/guia.md` | [o que contém] | [quando carregar] |
| `references/checklist.md` | [o que contém] | [quando carregar] |

---

## Regra de Leitura Seletiva

> 🔴 **NÃO leia todos os arquivos.** Identifique o que é necessário e leia apenas isso.

---

## Protocolo de Orquestração

### Fase de Análise

1. [Como analisar a solicitação]
2. [Como determinar o caminho correto]

### Fase de Execução

| Condição | Ação |
| :--- | :--- |
| [caso 1] | [O que orquestrar] |
| [caso 2] | [O que orquestrar] |

---

## Agentes e Skills Relacionados

| Recurso | Tipo | Papel |
| :--- | :--- | :--- |
| `nome-agente` | Agente | [responsabilidade] |
| `nome-skill` | Skill | [responsabilidade] |

---

## Anti-Padrões

| Anti-Padrão | Por quê é ruim |
| :--- | :--- |
| Ler todos os arquivos de uma vez | Desperdiça contexto, aumenta latência |
| Orquestrar sem verificar pré-requisitos | Falhas em cascata |
```

---

## Guia de Nomeação

| Tipo de Skill | Padrão de Nome | Exemplos |
| :--- | :--- | :--- |
| Princípios de design | `[domínio]-design` | `frontend-design`, `mobile-design` |
| Boas práticas técnicas | `[tech]-best-practices` | `nodejs-best-practices` |
| Padrões de arquitetura | `[domínio]-patterns` | `api-patterns`, `tailwind-patterns` |
| Workflows de processo | `[processo]-workflow` | `tdd-workflow` |
| Ferramentas específicas | `[ferramenta]-[ação]` | `vulnerability-scanner` |
| Meta-skills (sobre o sistema) | `[ação]-[objeto]` | `skill-generator`, `intelligent-routing` |

---

## Palavras-chave de Ativação por Domínio

Use estas como base para a `description` da nova skill:

```
Frontend:   "UI", "componente", "layout", "estilo", "CSS", "design", "responsivo"
Backend:    "API", "endpoint", "servidor", "rota", "autenticação", "banco"
Mobile:     "app", "tela", "mobile", "iOS", "Android", "React Native", "Flutter"
Testes:     "teste", "cobertura", "unitário", "E2E", "automação", "QA"
Segurança:  "vulnerabilidade", "segurança", "pentest", "OWASP", "exploit"
DevOps:     "deploy", "CI/CD", "Docker", "Kubernetes", "produção", "pipeline"
Performance:"lento", "otimizar", "performance", "cache", "bundle", "profiling"
SEO:        "SEO", "meta", "ranking", "busca", "indexação", "sitemap"
Dados:      "ETL", "pipeline", "dados", "analytics", "DuckDB", "Polars"
```
