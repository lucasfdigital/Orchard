---
name: brainstorming
description: Protocolo de questionamento Socrático + comunicação com o usuário. OBRIGATÓRIO para solicitações complexas, novas funcionalidades ou requisitos não claros. Inclui relatórios de progresso e tratamento de erros.
allowed-tools: Read, Glob, Grep
---

# Protocolo de Brainstorming e Comunicação

> **OBRIGATÓRIO:** Use para solicitações complexas/vagas, novas funcionalidades e atualizações.

---

## 🛑 PORTÃO SOCRÁTICO (EXECUÇÃO)

### Quando Acionar

| Padrão | Ação |
| :--- | :--- |
| "Construa/Crie/Faça [algo]" sem detalhes | 🛑 FAÇA 3 perguntas |
| Funcionalidade ou arquitetura complexa | 🛑 Clarifique antes de implementar |
| Solicitação de atualização/mudança | 🛑 Confirme o escopo |
| Requisitos vagos | 🛑 Pergunte o propósito, usuários e restrições |

### 🚫 OBRIGATÓRIO: 3 Perguntas Antes da Implementação

1. **PARE** - NÃO comece a codar.
2. **PERGUNTE** - Mínimo de 3 perguntas:
   - 🎯 Propósito: Qual problema você está resolvendo?
   - 👥 Usuários: Quem irá usar isso?
   - 📦 Escopo: O que é essencial (must-have) vs o que é desejável (nice-to-have)?
3. **AGUARDE** - Obtenha a resposta antes de prosseguir.

---

## 🧠 Geração Dinâmica de Perguntas

**⛔ NUNCA use templates estáticos.** Leia `dynamic-questioning.md` para entender os princípios.

### Princípios Centrais

| Princípio | Significado |
| :--- | :--- |
| **Perguntas Revelam Consequências** | Cada pergunta conecta a uma decisão arquitetural. |
| **Contexto Antes do Conteúdo** | Entenda primeiro o contexto: greenfield/funcionalidade/refatoração/debug. |
| **Perguntas Mínimas Viáveis** | Cada pergunta deve eliminar caminhos de implementação. |
| **Gere Dados, Não Suposições** | Não tente adivinhar — pergunte apresentando os trade-offs. |

### Processo de Geração de Perguntas

```
1. Analise o pedido → Extraia domínio, funcionalidades, indicadores de escala.
2. Identifique pontos de decisão → Bloqueadores vs adiáveis.
3. Gere perguntas → Prioridade: P0 (bloqueador) > P1 (alto impacto) > P2 (desejável).
4. Formate com trade-offs → O quê, Por quê, Opções, Padrão (Default).
```

### Formato de Pergunta (OBRIGATÓRIO)

```markdown
### [PRIORIDADE] **[PONTO DE DECISÃO]**

**Pergunta:** [Pergunta clara]

**Por que isso importa:**
- [Consequência arquitetural]
- [Afeta: custo/complexidade/cronograma/escala]

**Opções:**
| Opção | Prós | Contras | Melhor Para |
| :--- | :--- | :--- | :--- |
| A | [+] | [-] | [Caso de uso] |

**Se não for especificado:** [Padrão + justificativa]
```

**Para bancos de perguntas e algoritmos específicos por domínio**, veja: `dynamic-questioning.md`.

---

## Relatório de Progresso (BASEADO EM PRINCÍPIOS)

**PRINCÍPIO:** Transparência gera confiança. O status deve ser visível e acionável.

### Formato do Painel de Status

| Agente | Status | Tarefa Atual | Progresso |
| :--- | :--- | :--- | :--- |
| [Nome do Agente] | ✅🔄⏳❌⚠️ | [Descrição da tarefa] | [% ou contagem] |

### Ícones de Status

| Ícone | Significado | Uso |
| :--- | :--- | :--- |
| ✅ | Concluído | Tarefa finalizada com sucesso |
| 🔄 | Executando | Atualmente em execução |
| ⏳ | Aguardando | Bloqueado, esperando por dependência |
| ❌ | Erro | Falhou, precisa de atenção |
| ⚠️ | Aviso | Possível problema, não bloqueador |

---

## Tratamento de Erros (BASEADO EM PRINCÍPIOS)

**PRINCÍPIO:** Erros são oportunidades para uma comunicação clara.

### Padrão de Resposta de Erro

```
1. Reconheça o erro.
2. Explique o que aconteceu (de forma amigável).
3. Ofereça soluções específicas com trade-offs.
4. Peça ao usuário para escolher ou fornecer uma alternativa.
```

### Categorias de Erro

| Categoria | Estratégia de Resposta |
| :--- | :--- |
| **Conflito de Porta** | Ofereça porta alternativa ou feche a existente. |
| **Dependência Ausente** | Instale automaticamente ou peça permissão. |
| **Falha de Build** | Mostre o erro específico + sugestão de correção. |
| **Erro Não Claro** | Peça detalhes: screenshot, saída do console. |

---

## Mensagem de Conclusão (BASEADO EM PRINCÍPIOS)

**PRINCÍPIO:** Celebre o sucesso, guie os próximos passos.

### Estrutura de Conclusão

```
1. Confirmação de sucesso (celebre brevemente).
2. Resumo do que foi feito (concreto).
3. Como verificar/testar (acionável).
4. Sugestão de próximos passos (proativo).
```

---

## Princípios de Comunicação

| Princípio | Implementação |
| :--- | :--- |
| **Conciso** | Sem detalhes desnecessários, vá direto ao ponto. |
| **Visual** | Use emojis (✅🔄⏳❌) para varredura visual rápida. |
| **Específico** | "~2 minutos" em vez de "espere um pouco". |
| **Alternativas** | Ofereça múltiplos caminhos quando estiver travado. |
| **Proativo** | Sugira o próximo passo após a conclusão. |

---

## Anti-Padrões (EVITE)

| Anti-Padrão | Por quê |
| :--- | :--- |
| Pular para soluções antes de entender | Desperdiça tempo no problema errado. |
| Assumir requisitos sem perguntar | Gera um resultado incorreto. |
| Excesso de engenharia na primeira versão| Atrasa a entrega de valor. |
| Ignorar restrições | Cria soluções inutilizáveis. |
| Frases como "Eu acho" | Incerteza → Em vez disso, pergunte. |
