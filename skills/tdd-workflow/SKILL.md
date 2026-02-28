---
name: tdd-workflow
description: Princípios do workflow de Desenvolvimento Orientado a Testes (TDD). Ciclo RED-GREEN-REFACTOR.
allowed-tools: Read, Write, Edit, Glob, Grep, Bash
---

# Workflow de TDD

> Escreva os testes primeiro, o código depois.

---

## 1. O Ciclo do TDD

```
🔴 RED (Vermelho)       → Escreva um teste que falhe
       ↓
🟢 GREEN (Verde)        → Escreva o código mínimo para passar
       ↓
🔵 REFACTOR (Refatorar) → Melhore a qualidade do código
       ↓
   Repita...
```

---

## 2. As Três Leis do TDD

1. Escreva código de produção apenas para fazer um teste que falha passar.
2. Escreva apenas o teste suficiente para demonstrar a falha.
3. Escreva apenas o código suficiente para fazer o teste passar.

---

## 3. Princípios da Fase RED

### O que Escrever

| Foco | Exemplo |
| :--- | :--- |
| Comportamento | "should add two numbers" (deve somar dois números) |
| Casos de borda | "should handle empty input" (deve lidar com entrada vazia) |
| Estados de erro | "should throw for invalid data" (deve lançar erro para dados inválidos) |

### Regras da Fase RED

- O teste deve falhar primeiro.
- O nome do teste descreve o comportamento esperado.
- Idealmente, um "assertion" (afirmação) por teste.

---

## 4. Princípios da Fase GREEN

### Código Mínimo

| Princípio | Significado |
| :--- | :--- |
| **YAGNI** | "You Aren't Gonna Need It" (Você não vai precisar disso) |
| **Simplest thing** | Escreva o mínimo para passar no teste |
| **Sem otimização** | Apenas faça funcionar |

### Regras da Fase GREEN

- Não escreva código desnecessário.
- Não otimize ainda.
- Passe no teste, nada mais.

---

## 5. Princípios da Fase REFACTOR

### O que Melhorar

| Área | Ação |
| :--- | :--- |
| Duplicação | Extrair código comum |
| Nomenclatura | Tornar a intenção clara |
| Estrutura | Melhorar a organização |
| Complexidade | Simplificar a lógica |

### Regras de REFACTOR

- Todos os testes devem permanecer verdes.
- Pequenas mudanças incrementais.
- Faça o commit após cada refatoração.

---

## 6. Padrão AAA

Todo teste segue:

| Passo | Propósito |
| :--- | :--- |
| **Arrange (Organizar)**| Configurar os dados do teste |
| **Act (Agir)** | Executar o código sendo testado |
| **Assert (Afirmar)** | Verificar o resultado esperado |

---

## 7. Quando Usar TDD

| Cenário | Valor do TDD |
| :--- | :--- |
| Nova funcionalidade | Alto |
| Correção de bug | Alto (escreva o teste primeiro) |
| Lógica complexa | Alto |
| Exploratório | Baixo (faça um protótipo, depois use TDD) |
| Layout de UI | Baixo |

---

## 8. Priorização de Testes

| Prioridade | Tipo de Teste |
| :--- | :--- |
| 1 | Caminho feliz (Happy path) |
| 2 | Casos de erro |
| 3 | Casos de borda |
| 4 | Performance |

---

## 9. Anti-Padrões

| ❌ NÃO Faça | ✅ Faça |
| :--- | :--- |
| Pular a fase RED | Observe o teste falhar primeiro |
| Escrever testes depois | Escreva os testes antes |
| Super-dimensionar o início | Mantenha a simplicidade |
| Múltiplos asserts | Um comportamento por teste |
| Testar a implementação | Testar o comportamento |

---

## 10. TDD Aumentado por IA

### Padrão Multi-Agente

| Agente | Papel |
| :--- | :--- |
| Agente A | Escrever testes que falham (RED) |
| Agente B | Implementar para passar (GREEN) |
| Agente C | Otimizar (REFACTOR) |

---

> **Lembre-se:** O teste é a especificação. Se você não consegue escrever um teste, você não entende o requisito.
