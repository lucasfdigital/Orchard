---
name: web-design-guidelines
description: Revisar o código da UI para conformidade com as Web Interface Guidelines. Use quando solicitado para "revisar minha UI", "checar acessibilidade", "auditar design", "revisar UX" ou "verificar meu site em relação às melhores práticas".
metadata:
  author: vercel
  version: "1.0.0"
  argument-hint: <arquivo-ou-padrao>
---

# Web Interface Guidelines (Diretrizes de Interface Web)

Revise arquivos para conformidade com as Web Interface Guidelines.

## Como Funciona

1. Busque as diretrizes mais recentes na URL de origem abaixo.
2. Leia os arquivos especificados (ou solicite ao usuário os arquivos/padrão).
3. Verifique em relação a todas as regras nas diretrizes obtidas.
4. Forneça o resultado das descobertas no formato conciso `arquivo:linha`.

## Fonte das Guidelines

Busque as diretrizes atualizadas antes de cada revisão:

```
https://raw.githubusercontent.com/vercel-labs/web-interface-guidelines/main/command.md
```

Use Ferramentas de Busca Web (WebFetch) para recuperar as regras mais recentes. O conteúdo recuperado contém todas as regras e as instruções de formato de saída.

## Uso

Quando um usuário fornece um arquivo ou argumento de padrão:
1. Busque as diretrizes na URL de origem acima.
2. Leia os arquivos especificados.
3. Aplique todas as regras das diretrizes recuperadas.
4. Forneça os resultados usando o formato especificado nas diretrizes.

Se nenhum arquivo for especificado, pergunte ao usuário quais arquivos devem ser revisados.

---

## Skills Relacionadas

| Skill | Quando Usar |
| :--- | :--- |
| **[frontend-design](../frontend-design/SKILL.md)** | Antes de codar - Aprenda princípios de design (cor, tipografia, psicologia de UX) |
| **web-design-guidelines** (esta) | Depois de codar - Auditoria de acessibilidade, performance e melhores práticas |

## Workflow de Design

```
1. DESIGN   → Leia os princípios de frontend-design
2. CÓDIGO   → Implemente o design
3. AUDIT    → Execute a revisão web-design-guidelines ← VOCÊ ESTÁ AQUI
4. FIX      → Corrija as descobertas da auditoria
```
