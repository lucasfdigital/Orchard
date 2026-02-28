---
name: react-best-practices
description: Otimização de performance de React e Next.js pela Engenharia da Vercel. Use ao construir componentes React, otimizar a performance, eliminar waterfalls, reduzir o tamanho do bundle, revisar código para problemas de performance ou implementar otimizações no lado do servidor/cliente.
allowed-tools: Read, Write, Edit, Glob, Grep, Bash
---

# Especialista em Performance de Next.js & React

> **Pela Engenharia da Vercel** - 57 regras de otimização priorizadas por impacto.
> **Filosofia:** Elimine waterfalls primeiro, otimize bundles depois, então faça micro-otimizações.

---

## 🎯 Regra de Leitura Seletiva (OBRIGATÓRIO)

**Leia APENAS as seções relevantes para a sua tarefa!** Verifique o mapa de conteúdo abaixo e selecione o que precisa.

> 🔴 **Para revisões de performance: Comece pelas seções CRÍTICAS (1-2), depois passe para ALTA/MÉDIA.**

---

## 📑 Mapa de Conteúdo

| Arquivo | Impacto | Regras | Quando Ler |
| :--- | :--- | :--- | :--- |
| `1-async-eliminating-waterfalls.md` | 🔴 **CRÍTICO** | 5 regras | Carregamento de página lento, chamadas de API sequenciais, waterfalls de coleta de dados |
| `2-bundle-bundle-size-optimization.md` | 🔴 **CRÍTICO** | 5 regras | Tamanho de bundle grande, Time to Interactive (TTI) lento, problemas de Primeiro Carregamento (First Load) |
| `3-server-server-side-performance.md` | 🟠 **ALTO** | 7 regras | SSR lento, otimização de rotas de API, waterfalls no lado do servidor |
| `4-client-client-side-data-fetching.md`| 🟡 **MÉDIO-ALTO** | 4 regras | Gerenciamento de dados no cliente, padrões SWR, desduplicação |
| `5-rerender-re-render-optimization.md` | 🟡 **MÉDIO** | 12 regras | Re-renders excessivos, performance do React, memoização |
| `6-rendering-rendering-performance.md` | 🟡 **MÉDIO** | 9 rules | Gargalos de renderização, virtualização, otimização de imagens |
| `7-js-javascript-performance.md` | ⚪ **BAIXO-MÉDIO** | 12 regras | Micro-otimizações, cache, performance de loops |
| `8-advanced-advanced-patterns.md` | 🔵 **VARIÁVEL** | 3 regras | Padrões avançados de React, useLatest, init-once |

**Total: 57 regras distribuídas em 8 categorias**

---

## 🚀 Árvore de Decisão Rápida

**Qual é o seu problema de performance?**

```
🐌 Carregamento lento de página / Longo Time to Interactive
  → Leia a Seção 1: Eliminando Waterfalls
  → Leia a Seção 2: Otimização do Tamanho do Bundle

📦 Tamanho do bundle grande (> 200KB)
  → Leia a Seção 2: Otimização do Tamanho do Bundle
  → Verifique: Imports dinâmicos, barrel imports, tree-shaking

🖥️ Renderização no lado do servidor (SSR) lenta
  → Leia a Seção 3: Performance no Lado do Servidor
  → Verifique: Coleta de dados paralela, streaming

🔄 Muitos re-renders / Lag na UI
  → Leia a Seção 5: Otimização de Re-render
  → Verifique: React.memo, useMemo, useCallback

🎨 Problemas de performance na renderização
  → Leia a Seção 6: Performance de Renderização
  → Verifique: Virtualização, layout thrashing

🌐 Problemas de coleta de dados no lado do cliente
  → Leia a Seção 4: Coleta de Dados no Lado do Cliente
  → Verifique: Desduplicação SWR, localStorage

✨ Precisa de padrões avançados
  → Leia a Seção 8: Padrões Avançados
```

---

## 📊 Guia de Prioridade de Impacto

**Use esta ordem ao realizar uma otimização abrangente:**

```
1️⃣ CRÍTICO (Maiores ganhos - Faça primeiro):
   ├─ Seção 1: Eliminando Waterfalls
   │  └─ Cada waterfall adiciona latência total de rede (100-500ms+)
   └─ Seção 2: Otimização do Tamanho do Bundle
      └─ Afeta o Time to Interactive e o Largest Contentful Paint

2️⃣ ALTO (Impacto significativo - Faça em segundo):
   └─ Seção 3: Performance no Lado do Servidor
      └─ Elimina waterfalls no servidor, tempos de resposta mais rápidos

3️⃣ MÉDIO (Ganhos moderados - Faça em terceiro):
   ├─ Seção 4: Coleta de Dados no Lado do Cliente
   ├─ Seção 5: Otimização de Re-render
   └─ Seção 6: Performance de Renderização

4️⃣ BAIXO (Polimento - Faça por último):
   ├─ Seção 7: Performance de JavaScript
   └─ Seção 8: Padrões Avançados
```

---

## 🔗 Skills Relacionadas

| Necessidade | Skill |
| :--- | :--- |
| Padrões de design de API | `@[skills/api-patterns]` |
| Otimização de banco de dados | `@[skills/database-design]` |
| Estratégias de teste | `@[skills/testing-patterns]` |
| Princípios de design UI/UX | `@[skills/frontend-design]` |
| Padrões de TypeScript | `@[skills/typescript-expert]` |
| Implantação e DevOps | `@[skills/deployment-procedures]` |

---

## ✅ Checklist de Revisão de Performance

Antes de lançar para produção:

**Crítico (Deve Corrigir):**
- [ ] Nenhum carregamento de dados sequencial (waterfalls eliminados).
- [ ] Tamanho do bundle principal < 200KB.
- [ ] Sem barrel imports no código da aplicação.
- [ ] Imports dinâmicos usados para grandes componentes.
- [ ] Coleta de dados paralela sempre que possível.

**Alta Prioridade:**
- [ ] Componentes de servidor usados onde apropriado.
- [ ] Rotas de API otimizadas (sem consultas N+1).
- [ ] Fronteiras (boundaries) de Suspense para coleta de dados.
- [ ] Geração estática usada onde possível.

**Média Prioridade:**
- [ ] Computações pesadas memoizadas.
- [ ] Renderização de listas virtualizada (se > 100 itens).
- [ ] Imagens otimizadas com next/image.
- [ ] Sem re-renders desnecessários.

**Baixa Prioridade (Polimento):**
- [ ] Loops de caminho crítico otimizados.
- [ ] Padrões de RegExp movidos para o topo (hoisted).
- [ ] Acesso a propriedades em cache dentro de loops.

---

## ❌ Anti-Padrões (Erros Comuns)

**NÃO FAÇA:**
- ❌ Usar `await` sequencial para operações independentes.
- ❌ Importar bibliotecas inteiras quando precisa de apenas uma função.
- ❌ Usar barrel exports (re-exports no `index.ts`) no código da aplicação.
- ❌ Esquecer imports dinâmicos para grandes componentes/bibliotecas.
- ❌ Buscar dados no useEffect sem desduplicação.
- ❌ Esquecer de memoizar computações pesadas.
- ❌ Usar componentes de cliente quando componentes de servidor funcionariam.

**FAÇA:**
- ✅ Busque dados em paralelo com `Promise.all()`.
- ✅ Use imports dinâmicos: `const Comp = dynamic(() => import('./Pesado'))`.
- ✅ Importe diretamente: `import { especifico } from 'biblioteca/especifico'`.
- ✅ Use boundaries de Suspense para uma melhor UX.
- ✅ Aproveite os React Server Components.
- ✅ Meça a performance antes de otimizar.
- ✅ Use as otimizações integradas do Next.js (next/image, next/font).

---

## 🎯 Como Usar Esta Skill

### Para Novas Funcionalidades:
1. Verifique as **Seções 1 e 2** durante a construção (evite waterfalls, mantenha o bundle pequeno).
2. Use componentes de servidor por padrão (Seção 3).
3. Aplique memoização para operações pesadas (Seção 5).

### Para Revisões de Performance:
1. Comece pela **Seção 1** (waterfalls = maior impacto).
2. Depois a **Seção 2** (tamanho do bundle).
3. Depois a **Seção 3** (lado do servidor).
4. Finalmente outras seções conforme necessário.

### Para Depuração de Performance Lenta:
1. Identifique o sintoma (carregamento lento, lag, etc.).
2. Use a Árvore de Decisão Rápida acima.
3. Leia a seção relevante.
4. Aplique correções na ordem de prioridade.

---

## 📚 Caminho de Aprendizado

**Iniciante (Foco no Crítico):**
→ Seção 1: Eliminando Waterfalls
→ Seção 2: Otimização do Tamanho do Bundle

**Intermediário (Adicione Alta Prioridade):**
→ Seção 3: Performance no Lado do Servidor
→ Seção 5: Otimização de Re-render

**Avançado (Otimização Completa):**
→ Todas as seções + Seção 8: Padrões Avançados

---

## 🔍 Script de Validação

| Script | Propósito | Comando |
| :--- | :--- | :--- |
| `scripts/react_performance_checker.py` | Auditoria de performance automatizada | `python scripts/react_performance_checker.py <caminho_do_projeto>` |

---

## 📖 Detalhes das Seções

### Seção 1: Eliminando Waterfalls (CRÍTICO)
**Impacto:** Cada waterfall adiciona mais de 100-500ms de latência.
**Conceitos Chave:** Coleta paralela, Promise.all(), boundaries de Suspense, preloading.

### Seção 2: Otimização do Tamanho do Bundle (CRÍTICO)
**Impacto:** Afeta diretamente o Time to Interactive e o Largest Contentful Paint.
**Conceitos Chave:** Imports dinâmicos, tree-shaking, evitar barrel imports.

### Seção 3: Performance no Lado do Servidor (ALTO)
**Impacto:** Respostas do servidor mais rápidas, melhor SEO.
**Conceitos Chave:** Coleta paralela no servidor, streaming, otimização de rotas de API.

### Seção 4: Coleta de Dados no Lado do Cliente (MÉDIO-ALTO)
**Impacto:** Reduz requisições redundantes, melhor UX.
**Conceitos Chave:** Desduplicação SWR, cache no localStorage, event listeners.

### Seção 5: Otimização de Re-render (MÉDIO)
**Impacto:** UI mais fluida, menos computação desperdiçada.
**Conceitos Chave:** React.memo, useMemo, useCallback, estrutura de componentes.

### Seção 6: Performance de Renderização (MÉDIO)
**Impacto:** Melhor eficiência de renderização.
**Conceitos Chave:** Virtualização, otimização de imagem, layout thrashing.

### Seção 7: Performance de JavaScript (BAIXO-MÉDIO)
**Impacto:** Melhorias incrementais em caminhos críticos.
**Conceitos Chave:** Otimização de loops, cache, hoisting de RegExp.

### Seção 8: Padrões Avançados (VARIÁVEL)
**Impacto:** Casos de uso específicos.
**Conceitos Chave:** Hook useLatest, padrões init-once, referências de handlers de eventos.

---

## 🎓 Resumo de Melhores Práticas

**Regras de Ouro:**
1. **Meça primeiro** - Use o Profile do React DevTools, Chrome DevTools.
2. **Maior impacto primeiro** - Waterfalls → Bundle → Servidor → Micro.
3. **Não otimize demais** - Foque nos gargalos reais.
4. **Use os recursos da plataforma** - O Next.js já possui otimizações integradas.
5. **Pense nos usuários** - Condições do mundo real importam.

**Mentalidade de Performance:**
- Cada `await` em sequência = waterfall potencial.
- Cada `import` = inchaço potencial do bundle.
- Cada re-render = computação desperdiçada (se desnecessário).
- Componentes de servidor = menos JavaScript enviado para o cliente.
- Meça, não adivinhe.

---

**Fonte:** Engenharia da Vercel
**Data:** Janeiro de 2026
**Versão:** 1.0.0
**Total de Regras:** 57 distribuídas em 8 categorias
