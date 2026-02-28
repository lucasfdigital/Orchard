---
description: Cria um plano de projeto usando o agente project-planner. Sem escrita de código - apenas geração do arquivo de plano.
---

# /plan - Modo de Planejamento de Projeto

$ARGUMENTS

---

## 🔴 REGRAS CRÍTICAS

1. **SEM ESCRITA DE CÓDIGO** - Este comando cria apenas o arquivo de plano.
2. **Use o agente project-planner** - NÃO o modo Plan nativo do Agente Orchard.
3. **Portão Socrático** - Faça perguntas clarificadoras antes de planejar.
4. **Nomenclatura Dinâmica** - Arquivo de plano nomeado com base na tarefa.

---

## Tarefa

Use o agente `project-planner` com este contexto:

```
CONTEXTO:
- Pedido do Usuário: $ARGUMENTS
- Modo: APENAS PLANEJAMENTO (sem código)
- Saída: docs/PLAN-{task-slug}.md (nomenclatura dinâmica)

REGRAS DE NOMENCLATURA:
1. Extraia 2-3 palavras-chave do pedido
2. Minúsculas, separadas por hífen
3. Máximo de 30 caracteres
4. Exemplo: "e-commerce cart" → PLAN-ecommerce-cart.md

REGRAS:
1. Siga o project-planner.md Fase -1 (Verificação de Contexto)
2. Siga o project-planner.md Fase 0 (Portão Socrático)
3. Crie PLAN-{slug}.md com a decomposição de tarefas
4. NÃO escreva nenhum arquivo de código
5. RELATE o nome exato do arquivo criado
```

---

## Saída Esperada

| Entregável | Localização |
| :--- | :--- |
| Plano de Projeto | `docs/PLAN-{task-slug}.md` |
| Decomposição de Tarefas | Dentro do arquivo de plano |
| Atribuições de Agentes | Dentro do arquivo de plano |
| Checklist de Verificação | Fase X no arquivo de plano |

---

## Após o Planejamento

Diga ao usuário:
```
[OK] Plano criado: docs/PLAN-{slug}.md

Próximos passos:
- Revise o plano
- Execute `/create` para iniciar a implementação
- Ou modifique o plano manualmente
```

---

## Exemplos de Nomenclatura

| Pedido | Arquivo de Plano |
| :--- | :--- |
| `/plan site de e-commerce com carrinho` | `docs/PLAN-ecommerce-carrinho.md` |
| `/plan app mobile para fitness` | `docs/PLAN-fitness-app.md` |
| `/plan adicionar modo escuro` | `docs/PLAN-modo-escuro.md` |
| `/plan corrigir bug de autenticação` | `docs/PLAN-erro-auth.md` |
| `/plan dashboard SaaS` | `docs/PLAN-saas-dashboard.md` |

---

## Uso

```
/plan site de e-commerce com carrinho
/plan app mobile para fitness tracking
/plan dashboard SaaS com analytics
```
