---
name: clean-code
description: Padrões de codificação pragmáticos - concisos, diretos, sem excesso de engenharia, sem comentários desnecessários.
allowed-tools: Read, Write, Edit
version: 2.0
priority: CRITICAL
---

# Clean Code - Padrões de Codificação Pragmática para IA

> **SKILL CRÍTICA** - Seja **conciso, direto e focado na solução**.

---

## Princípios Centrais

| Princípio | Regra |
| :--- | :--- |
| **SRP** | Responsabilidade Única - cada função/classe faz APENAS UMA coisa. |
| **DRY** | Não se Repita - extraia duplicatas, reuse. |
| **KISS** | Mantenha o Simples - a solução mais simples que funciona. |
| **YAGNI** | Você Não Vai Precisar Disso - não construa funcionalidades não utilizadas. |
| **Escoteiro** | Deixe o código mais limpo do que o encontrou. |

---

## Regras de Nomenclatura

| Elemento | Convenção |
| :--- | :--- |
| **Variáveis** | Revelar intenção: `userCount` em vez de `n`. |
| **Funções** | Verbo + substantivo: `getUserById()` em vez de `user()`. |
| **Booleanos** | Forma de pergunta: `isActive`, `hasPermission`, `canEdit`. |
| **Constantes** | SCREAMING_SNAKE: `MAX_RETRY_COUNT`. |

> **Regra:** Se você precisa de um comentário para explicar um nome, renomeie-o.

---

## Regras de Função

| Regra | Descrição |
| :--- | :--- |
| **Pequena** | Máximo 20 linhas, idealmente 5-10. |
| **Uma Coisa** | Faz uma coisa e faz bem. |
| **Um Nível** | Um nível de abstração por função. |
| **Poucos Args** | Máximo 3 argumentos, preferencialmente 0-2. |
| **Sem Efeitos Colaterais** | Não mude as entradas de forma inesperada. |

---

## Estrutura do Código

| Padrão | Aplicação |
| :--- | :--- |
| **Guard Clauses** | Retornos antecipados para casos de borda. |
| **Raso > Aninhado** | Evite aninhamento profundo (máx 2 níveis). |
| **Composição** | Funções pequenas compostas entre si. |
| **Colocação** | Mantenha o código relacionado próximo. |

---

## Estilo de Codificação da IA

| Situação | Ação |
| :--- | :--- |
| Usuário pede funcionalidade | Escreva-a diretamente. |
| Usuário relata bug | Corrija-o, não explique. |
| Requisito não está claro | Pergunte, não presuma. |

---

## Anti-Padrões (NÃO FAÇA)

| ❌ Padrão | ✅ Correção |
| :--- | :--- |
| Comentar cada linha | Delete comentários óbvios. |
| Helper para uma linha | Coloque o código inline. |
| Factory para 2 objetos | Instanciação direta. |
| utils.ts com 1 função | Coloque o código onde ele é usado. |
| "Primeiro vamos importar..." | Apenas escreva o código. |
| Aninhamento profundo | Use guard clauses (cláusulas de guarda). |
| Números mágicos | Use constantes nomeadas. |
| Funções Deus | Divida por responsabilidade. |

---

## 🔴 Antes de Editar QUALQUER Arquivo (PENSE PRIMEIRO!)

**Antes de alterar um arquivo, pergunte-se:**

| Pergunta | Por que |
| :--- | :--- |
| **Quem importa este arquivo?** | Eles podem quebrar. |
| **O que este arquivo importa?** | Mudanças de interface. |
| **Quais testes cobrem isso?** | Os testes podem falhar. |
| **É um componente compartilhado?** | Múltiplos locais afetados. |

**Verificação Rápida:**
```
Arquivo para editar: UserService.ts
└── Quem importa? → UserController.ts, AuthController.ts
└── Eles também precisam de mudanças? → Verifique as assinaturas das funções.
```

> 🔴 **Regra:** Edite o arquivo + todos os arquivos dependentes na MESMA tarefa.
> 🔴 **Nunca deixe imports quebrados ou atualizações pendentes.**

---

## Resumo

| Faça | NÃO Faça |
| :--- | :--- |
| Escreva o código diretamente | Escreva tutoriais. |
| Deixe o código se auto-documentar | Adicione comentários óbvios. |
| Corrija bugs imediatamente | Explique a correção primeiro. |
| Use inline para coisas pequenas | Crie arquivos desnecessários. |
| Nomeie as coisas claramente | Use abreviações. |
| Mantenha as funções pequenas | Escreva funções com mais de 100 linhas. |

> **Lembre-se: O usuário quer código funcional, não uma lição de programação.**

---

## 🔴 Verificação Final Antes de Concluir (OBRIGATÓRIO)

**Antes de dizer "tarefa concluída", verifique:**

| Check | Pergunta |
| :--- | :--- |
| ✅ **Objetivo atingido?** | Fiz exatamente o que o usuário pediu? |
| ✅ **Arquivos editados?** | Modifiquei todos os arquivos necessários? |
| ✅ **O código funciona?** | Testei/verifiquei a mudança? |
| ✅ **Sem erros?** | Lint e TypeScript passam? |
| ✅ **Nada esquecido?** | Algum caso de borda esquecido? |

> 🔴 **Regra:** Se QUALQUER check falhar, corrija antes de concluir.

---

## Scripts de Verificação (OBRIGATÓRIO)

> 🔴 **CRÍTICO:** Cada agente executa APENAS os scripts de sua própria skill após concluir o trabalho.

### Mapeamento Agente → Script

| Agente | Script | Comando |
| :--- | :--- | :--- |
| **frontend-specialist** | Auditoria de UX | `python .agent/skills/frontend-design/scripts/ux_audit.py .` |
| **frontend-specialist** | Check de A11y | `python .agent/skills/frontend-design/scripts/accessibility_checker.py .` |
| **backend-specialist** | Validador de API | `python .agent/skills/api-patterns/scripts/api_validator.py .` |
| **mobile-developer** | Auditoria Mobile | `python .agent/skills/mobile-design/scripts/mobile_audit.py .` |
| **database-architect** | Validador de Schema | `python .agent/skills/database-design/scripts/schema_validator.py .` |
| **security-auditor** | Scan de Segurança | `python .agent/skills/vulnerability-scanner/scripts/security_scan.py .` |
| **seo-specialist** | Check de SEO | `python .agent/skills/seo-fundamentals/scripts/seo_checker.py .` |
| **seo-specialist** | Check de GEO | `python .agent/skills/geo-fundamentals/scripts/geo_checker.py .` |
| **performance-optimizer** | Lighthouse | `python .agent/skills/performance-profiling/scripts/lighthouse_audit.py <url>` |
| **test-engineer** | Test Runner | `python .agent/skills/testing-patterns/scripts/test_runner.py .` |
| **test-engineer** | Playwright | `python .agent/skills/webapp-testing/scripts/playwright_runner.py <url>` |
| **Qualquer agente** | Check de Lint | `python .agent/skills/lint-and-validate/scripts/lint_runner.py .` |
| **Qualquer agente** | Cobertura de Tipos | `python .agent/skills/lint-and-validate/scripts/type_coverage.py .` |
| **Qualquer agente** | Check de i18n | `python .agent/skills/i18n-localization/scripts/i18n_checker.py .` |

> ❌ **ERRADO:** `test-engineer` rodando `ux_audit.py`.
> ✅ **CORRETO:** `frontend-specialist` rodando `ux_audit.py`.

---

### 🔴 Tratamento de Saída do Script (LER → RESUMIR → PERGUNTAR)

**Ao executar um script de validação, você DEVE:**

1. **Rodar o script** e capturar TODA a saída.
2. **Analisar a saída** - identificar erros, avisos e sucessos.
3. **Resumir para o usuário** neste formato:

```markdown
## Resultados do Script: [script_name.py]

### ❌ Erros Encontrados (X itens)
- [Arquivo:Linha] Descrição do erro 1
- [Arquivo:Linha] Descrição do erro 2

### ⚠️ Avisos (Y itens)
- [Arquivo:Linha] Descrição do aviso

### ✅ Sucessos (Z itens)
- Verificação 1 passou
- Verificação 2 passou

**Devo corrigir os X erros?**
```

4. **Aguardar a confirmação do usuário** antes de corrigir.
5. **Após corrigir** → Rode o script novamente para confirmar.

> 🔴 **VIOLAÇÃO:** Rodar o script e ignorar a saída = tarefa FALHA.
> 🔴 **VIOLAÇÃO:** Corrigir automaticamente sem perguntar = não permitido.
> 🔴 **Regra:** Sempre LEIA a saída → RESUMA → PERGUNTE → depois corrija.
