---
name: plan-writing
description: Planejamento estruturado de tarefas com decomposição clara, dependências e critérios de verificação. Use ao implementar funcionalidades, refatorar ou qualquer trabalho de múltiplas etapas.
allowed-tools: Read, Glob, Grep
---

# Escrita de Plano

> Fonte: obra/superpowers

## Visão Geral

Esta skill fornece uma estrutura para decompor o trabalho em tarefas claras e acionáveis, com critérios de verificação.

---

## Princípios de Decomposição de Tarefas

### 1. Tarefas Pequenas e Focadas
- Cada tarefa deve levar de 2 a 5 minutos.
- Um resultado claro por tarefa.
- Verificável de forma independente.

### 2. Verificação Clara
- Como você sabe que está pronto?
- O que você pode checar/testar?
- Qual é o resultado esperado?

### 3. Ordenação Lógica
- Dependências identificadas.
- Trabalho paralelo onde for possível.
- Caminho crítico destacado.
- **Fase X: A verificação é sempre a ÚLTIMA.**

### 4. Nomenclatura Dinâmica na Raiz do Projeto
- Os arquivos de plano são salvos como `{task-slug}.md` na RAIZ DO PROJETO.
- Nome derivado da tarefa (ex: "add auth" → `auth-feature.md`).
- **NUNCA** dentro de `.claude/`, `docs/` ou pastas temporárias.

---

## Princípios de Planejamento (NÃO são Templates!)

> 🔴 **NÃO existam templates fixos. Cada plano é ÚNICO para a tarefa.**

### Princípio 1: Mantenha-o CURTO

| ❌ Errado | ✅ Correto |
| :--- | :--- |
| 50 tarefas com sub-sub-tarefas | No máximo 5-10 tarefas claras |
| Cada micro-passo listado | Apenas itens acionáveis |
| Descrições verbosas | Uma linha por tarefa |

> **Regra:** Se o plano tiver mais de 1 página, está muito longo. Simplifique.

---

### Princípio 2: Seja ESPECÍFICO, Não Genérico

| ❌ Errado | ✅ Correto |
| :--- | :--- |
| "Configurar projeto" | "Rodar `npx create-next-app`" |
| "Adicionar autenticação" | "Instalar next-auth, criar `/api/auth/[...nextauth].ts`" |
| "Estilizar a UI" | "Adicionar classes Tailwind ao `Header.tsx`" |

> **Regra:** Cada tarefa deve ter um resultado claro e verificável.

---

### Princípio 3: Conteúdo Dinâmico Baseado no Tipo de Projeto

**Para NOVO PROJETO:**
- Qual stack técnica? (decida primeiro).
- Qual é o MVP? (funcionalidades mínimas).
- Qual é a estrutura de arquivos?

**Para ADIÇÃO DE FUNCIONALIDADE:**
- Quais arquivos são afetados?
- Quais dependências são necessárias?
- Como verificar se funciona?

**Para CORREÇÃO DE BUG:**
- Qual é a causa raiz?
- Qual arquivo/linha mudar?
- Como testar a correção?

---

### Princípio 4: Scripts São Específicos do Projeto

> 🔴 **NÃO copie e cole comandos de script. Escolha com base no tipo de projeto.**

| Tipo de Projeto | Scripts Relevantes |
| :--- | :--- |
| Frontend/React | `ux_audit.py`, `accessibility_checker.py` |
| Backend/API | `api_validator.py`, `security_scan.py` |
| Mobile | `mobile_audit.py` |
| Banco de Dados | `schema_validator.py` |
| Full-stack | Mistura dos acima com base no que foi alterado |

**Errado:** Adicionar todos os scripts a cada plano.
**Correto:** Apenas scripts relevantes para ESTA tarefa.

---

### Princípio 5: A Verificação é Simples

| ❌ Errado | ✅ Correto |
| :--- | :--- |
| "Verificar se o componente funciona" | "Rodar `npm run dev`, clicar no botão, ver o toast" |
| "Testar a API" | "`curl localhost:3000/api/users` retorna 200" |
| "Checar estilos" | "Abrir navegador, verificar se o toggle do modo escuro funciona" |

---

## Estrutura do Plano (Flexível, Não Fixa!)

```markdown
# [Nome da Tarefa]

## Objetivo
Uma frase: O que estamos construindo/corrigindo?

## Tarefas
- [ ] Tarefa 1: [Ação específica] → Verificar: [Como checar]
- [ ] Tarefa 2: [Ação específica] → Verificar: [Como checar]
- [ ] Tarefa 3: [Ação específica] → Verificar: [Como checar]

## Pronto Quando
- [ ] [Critério principal de sucesso]

## Notas
[Qualquer consideração importante]
```

> **Isso é tudo.** Sem fases, sem sub-seções, a menos que seja realmente necessário.
> Mantenha o mínimo. Adicione complexidade apenas quando exigido.

---

## Melhores Práticas (Referência Rápida)

1. **Comece com o objetivo** - O que estamos construindo/corrigindo?
2. **Máximo de 10 tarefas** - Se houver mais, divida em múltiplos planos.
3. **Cada tarefa verificável** - Critérios de "pronto" claros.
4. **Específico do projeto** - Nada de templates de copiar e colar.
5. **Atualize conforme avança** - Marque `[x]` quando concluído.

---

## Quando Usar

- Novo projeto do zero.
- Adição de uma funcionalidade.
- Correção de um bug (se for complexo).
- Refatoração de múltiplos arquivos.
