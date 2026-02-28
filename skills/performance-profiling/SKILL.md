---
name: performance-profiling
description: Princípios de profiling de performance. Técnicas de medição, análise e otimização.
allowed-tools: Read, Glob, Grep, Bash
---

# Profiling de Performance

> Meça, analise, otimize - nessa ordem.

---

## 🔧 Scripts de Runtime

**Execute estes para profiling automatizado:**

| Script | Propósito | Uso |
| :--- | :--- | :--- |
| `scripts/lighthouse_audit.py` | Auditoria de performance do Lighthouse | `python scripts/lighthouse_audit.py https://exemplo.com` |

---

## 1. Core Web Vitals

### Objetivos

| Métrica | Bom | Ruim | O que mede |
| :--- | :--- | :--- | :--- |
| **LCP** | < 2.5s | > 4.0s | Carregamento (Largest Contentful Paint) |
| **INP** | < 200ms | > 500ms | Interatividade (Interaction to Next Paint) |
| **CLS** | < 0.1 | > 0.25 | Estabilidade Visual (Cumulative Layout Shift) |

### Quando Medir

| Estágio | Ferramenta |
| :--- | :--- |
| Desenvolvimento | Lighthouse Local |
| CI/CD | Lighthouse CI |
| Produção | RUM (Real User Monitoring) |

---

## 2. Workflow de Profiling

### O Processo de 4 Passos

```
1. BASELINE   → Medir o estado atual
2. IDENTIFICAR → Encontrar o gargalo
3. CORRIGIR   → Fazer a mudança direcionada
4. VALIDAR    → Confirmar a melhoria
```

### Seleção de Ferramenta de Profiling

| Problema | Ferramenta |
| :--- | :--- |
| Carregamento da página | Lighthouse |
| Tamanho do bundle | Bundle analyzer |
| Tempo de execução | DevTools Performance |
| Memória | DevTools Memory |
| Rede | DevTools Network |

---

## 3. Análise de Bundle

### O que Procurar

| Problema | Indicador |
| :--- | :--- |
| Dependências grandes | Topo do bundle |
| Código duplicado | Múltiplos chunks |
| Código não utilizado | Baixa cobertura |
| Falta de code splitting | Chunk único grande |

### Ações de Otimização

| Descoberta | Ação |
| :--- | :--- |
| Biblioteca grande | Importar módulos específicos |
| Dep. duplicadas | Dedupelar, atualizar versões |
| Rota no bundle principal | Code splitting |
| Exports não utilizados | Tree shaking |

---

## 4. Profiling em Tempo de Execução (Runtime)

### Análise da Aba de Performance

| Padrão | Significado |
| :--- | :--- |
| Tarefas longas (>50ms) | Bloqueio da UI |
| Muitas tarefas pequenas | Possível oportunidade de loteamento (batching) |
| Layout/paint | Gargalo de renderização |
| Script | Execução de JavaScript |

### Análise da Aba de Memória

| Padrão | Significado |
| :--- | :--- |
| Heap crescente | Possível vazamento (leak) |
| Grande memória retida | Verifique as referências |
| DOM desanexado | Não foi limpo corretamente |

---

## 5. Gargalos Comuns

### Por Sintoma

| Sintoma | Causa Provável |
| :--- | :--- |
| Carregamento inicial lento | JS grande, bloqueio de renderização |
| Interações lentas | Handlers de eventos pesados |
| Travamentos na rolagem | Layout thrashing |
| Memória crescente | Leaks, referências retidas |

---

## 6. Prioridades de Ganhos Rápidos (Quick Win)

| Prioridade | Ação | Impacto |
| :--- | :--- | :--- |
| 1 | Habilitar compressão | Alto |
| 2 | Lazy load de imagens | Alto |
| 3 | Code splitting de rotas | Alto |
| 4 | Cache de assets estáticos | Médio |
| 5 | Otimizar imagens | Médio |

---

## 7. Anti-Padrões

| ❌ NÃO Faça | ✅ Faça |
| :--- | :--- |
| Adivinhar os problemas | Faça o profiling primeiro |
| Micro-otimizar | Corrija o maior problema |
| Otimizar cedo demais | Otimize quando necessário |
| Ignorar usuários reais | Use dados de RUM |

---

> **Lembre-se:** O código mais rápido é o código que não roda. Remova antes de otimizar.
