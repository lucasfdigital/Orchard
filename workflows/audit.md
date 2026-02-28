---
description: Realiza uma auditoria completa de saúde do projeto (Segurança, Lint, Performance e UX).
---

# /audit - Auditoria de Saúde do Projeto

> **ORQUESTRAÇÃO DE QUALIDADE** - Execute uma bateria completa de testes e análises automáticas para garantir a integridade do código.

---

## 📋 O que este workflow faz

Este comando ativará o `@orchestrator` para coordenar os seguintes especialistas:
1. **`@security-auditor`**: Scan de vulnerabilidades e segredos expostos.
2. **`@debugger`**: Busca por erros comuns de lint e tipagem.
3. **`@performance-optimizer`**: Auditoria de Core Web Vitals e Lighthouse.
4. **`@frontend-specialist`**: Auditoria de UX e Acessibilidade (se aplicável).

---

## 🚀 Passos de Execução

### 1. Preparação
O Orquestrador identifica a stack tecnológica e prepara os scripts necessários.

### 2. Execução Sequencial
// turbo
1. `python .agent/skills/vulnerability-scanner/scripts/security_scan.py .`
2. `python .agent/skills/lint-and-validate/scripts/lint_runner.py .`
3. `python .agent/skills/performance-profiling/scripts/lighthouse_audit.py .`
4. `python .agent/skills/frontend-design/scripts/ux_audit.py .`

### 3. Consolidação de Relatório
O Agente gera um painel visual de "Saúde do Projeto" no chat.

---

## 📊 Formato do Relatório de Saída

```markdown
# 🍎 Relatório de Auditoria Orchard: [Nome do Projeto]

### 🛡️ Segurança (Security Scan)
- [Status: ✅ Passou | ❌ Falhou]
- **Vulnerabilidades:** [X críticas, Y moderadas]
- **Segredos:** [Nenhum encontrado | 🚨 Alerta de Segredo em .env]

### 🧹 Código e Lint (Lint & Type Check)
- [Status: ✅ Passou | ⚠️ Avisos]
- **Erros de Lint:** [X]
- **Cobertura de Tipos:** [X%]

### ⚡ Performance (Lighthouse/CWV)
- **Performance:** [Score 0-100]
- **Acessibilidade:** [Score 0-100]
- **Melhoria Sugerida:** [Ex: Otimizar imagens hero.webp]

### 🎨 Experiência do Usuário (UX Audit)
- **Checklist Miller:** [✅ OK]
- **Contraste de Cor:** [✅ OK]

---
**💡 Recomendação Principal:** [Ação prioritária a ser tomada]
```

---

## 🛠️ Técnico

Este workflow utiliza os seguintes agentes e scripts:
- **Agentes**: `@orchestrator`, `@security-auditor`, `@performance-optimizer`.
- **Scripts**: Localizados em `.agent/skills/*/scripts/`.

> 🔴 **Regra:** Não tente corrigir os erros automaticamente. Primeiro reporte, depois peça permissão para o usuário (Portão Socrático).
