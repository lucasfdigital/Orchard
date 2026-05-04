---
name: skill-generator
description: Gerador de novas Skills para o Kit Antigravidade. Use ao criar, estruturar ou refatorar skills de agentes. Ativado por palavras-chave como "crie uma skill", "nova skill", "adicione skill", "gere skill".
allowed-tools: Read, Write, Edit, Glob, Grep
version: 1.0.0
---

# Skill Generator — Fábrica de Skills do Kit Antigravidade

> **Propósito:** Guiar a criação de Skills novas de forma padronizada, coerente e integrada ao ecossistema de agentes existente.

---

## 🗺️ Navegação Rápida

| Seção | Quando Usar |
| :--- | :--- |
| [Protocolo Socrático](#-protocolo-socrático-obrigatório) | Sempre — antes de criar qualquer skill |
| [Anatomia de uma Skill](#-anatomia-de-uma-skill) | Para entender a estrutura obrigatória |
| [Frontmatter YAML](#-frontmatter-yaml) | Para escrever os metadados corretamente |
| [Seções Obrigatórias](#-seções-obrigatórias-do-skillmd) | Para estruturar o corpo da skill |
| [Arquivos Complementares](#-arquivos-complementares-opcionais) | Para decidir o que criar além do SKILL.md |
| [Integração com Agentes](#-integração-com-agentes) | Para registrar a skill em um agente |
| [Checklist Final](#-checklist-final-de-qualidade) | Antes de declarar a skill pronta |
| [Anti-padrões](#-anti-padrões) | Para evitar erros comuns |
| [Exemplos](#-exemplos-de-referência) | Para consultar skills bem escritas |

---

## 🛑 PROTOCOLO SOCRÁTICO (OBRIGATÓRIO)

**Antes de criar qualquer skill, PARE e responda estas perguntas:**

### Perguntas de Descoberta (faça ao usuário se não estiverem claras)

```
P1 — PROPÓSITO: O que esta skill ensina ou capacita o agente a fazer?
     → Qual é o VERBO principal? (revisar / gerar / auditar / planejar / detectar...)

P2 — ATIVAÇÃO: Quando exatamente esta skill deve ser carregada?
     → Quais palavras-chave ou contextos disparam ela?

P3 — ESCOPO: Esta skill ensina PRINCÍPIOS ou executa AÇÕES?
     → Apenas instrução? Ou também scripts/templates/referências?

P4 — AGENTE: Qual agente vai usar esta skill?
     → Deve ser adicionada ao campo `skills:` do frontmatter do agente?

P5 — SOBREPOSIÇÃO: Já existe skill similar? (verifique .agent/skills/)
     → Se sim, deve estender a existente ou criar nova?
```

> 🔴 **NÃO crie a skill sem ter clareza sobre P1 e P2 no mínimo.**

---

## 📁 Anatomia de uma Skill

```
.agent/skills/
└── nome-da-skill/           ← kebab-case, descritivo
    ├── SKILL.md             ← OBRIGATÓRIO: Frontmatter + instruções
    ├── scripts/             ← OPCIONAL: Scripts Python/Bash executáveis
    │   └── nome_script.py
    ├── references/          ← OPCIONAL: Documentação, templates, specs
    │   └── guia.md
    └── assets/              ← OPCIONAL: Imagens, exemplos visuais
        └── exemplo.png
```

### Regra de Escopo Mínimo

> **Crie apenas o que for necessário.** Uma skill simples é APENAS `SKILL.md`.
> Adicione `scripts/`, `references/` e `assets/` **somente se** forem ativamente referenciados no SKILL.md.

---

## 📝 Frontmatter YAML

O frontmatter é a identidade da skill. **Cada campo tem um propósito específico:**

```yaml
---
name: nome-da-skill                          # kebab-case; deve ser único no ecossistema
description: >                               # Descrição de 1-2 linhas para o sistema de roteamento.
  O que esta skill faz. Palavras-chave de ativação embutidas aqui.
  Use ao [contexto específico]. Ativado por: "palavra1", "palavra2".
version: 1.0.0                               # Semântico: MAJOR.MINOR.PATCH
allowed-tools: Read, Write, Edit, Glob, Grep # Apenas as ferramentas necessárias
---
```

### Regras do Frontmatter

| Campo | Obrigatório | Regra |
| :--- | :--- | :--- |
| `name` | ✅ Sim | kebab-case, único, sem espaços |
| `description` | ✅ Sim | Inclua palavras-chave de ativação. Máx. 3 linhas. |
| `version` | ✅ Sim | Comece em `1.0.0` |
| `allowed-tools` | ⚠️ Recomendado | Princípio do menor privilégio |

### Boas Descrições vs. Ruins

```
❌ RUIM: "Skill para frontend."
✅ BOM:  "Design thinking e tomada de decisão para UI web. Use ao projetar
          componentes, layouts, esquemas de cores ou criar interfaces estéticas.
          Ativado por: 'UI', 'componente', 'estilizar', 'design', 'layout'."
```

---

## 📋 Seções Obrigatórias do SKILL.md

### Estrutura Mínima Obrigatória

```markdown
---
[frontmatter yaml]
---

# [Nome Legível da Skill]

> Propósito em 1 linha: O que esta skill capacita?

---

## Quando Usar

[Lista de situações que ativam esta skill]

---

## Princípios / Instruções

[Corpo principal da skill — veja padrões abaixo]

---

## Anti-Padrões (EVITE)

[O que NÃO fazer — essencial para prevenir comportamento genérico]
```

### Padrões de Corpo por Tipo de Skill

#### Tipo A — Skill de PRINCÍPIOS (ensina como pensar)

```markdown
## Princípio Central

> Declare a filosofia que guia esta skill em 1 frase.

## Processo de Decisão

Quando [contexto], siga este fluxo:

1. [Passo 1] → Resultado esperado
2. [Passo 2] → Resultado esperado
3. [Passo 3] → Resultado esperado

## Árvore de Decisão

| Situação | Decisão | Por quê |
| :--- | :--- | :--- |
| [caso A] | [ação] | [razão] |
| [caso B] | [ação] | [razão] |

## Anti-Padrões (EVITE)

| Anti-Padrão | Por quê é ruim |
| :--- | :--- |
| [problema] | [consequência] |
```

#### Tipo B — Skill de EXECUÇÃO (realiza ações concretas)

```markdown
## Pré-requisitos

- [O que deve existir antes]

## Protocolo de Execução

### Passo 1: [Nome do Passo]
[Instruções específicas]
→ Verificação: [Como confirmar que funcionou]

### Passo 2: [Nome do Passo]
[Instruções específicas]
→ Verificação: [Como confirmar que funcionou]

## Formato de Saída (OBRIGATÓRIO)

[Template exato da saída esperada]

## Anti-Padrões (EVITE)

| Anti-Padrão | Por quê é ruim |
| :--- | :--- |
| [problema] | [consequência] |
```

#### Tipo C — Skill de ORQUESTRAÇÃO (coordena múltiplas skills/agentes)

```markdown
## Mapa de Conteúdo

| Arquivo | Descrição | Quando Ler |
| :--- | :--- | :--- |
| `references/guia.md` | [o que contém] | [quando carregar] |

## Regra de Leitura Seletiva

**Leia APENAS os arquivos relevantes para a solicitação.**

## Protocolo de Coordenação

[Como esta skill orquestra os recursos]

## Agentes Relacionados

| Agente | Papel |
| :--- | :--- |
| `nome-agente` | [responsabilidade] |
```

---

## 📦 Arquivos Complementares (Opcionais)

### Quando criar `scripts/`

Crie scripts apenas se a skill requer **execução de código** (auditorias, validações, análises):

```python
# Padrão de script de skill
#!/usr/bin/env python3
"""
[nome-da-skill] — [descrição em uma linha]
Uso: python scripts/nome_script.py [argumentos]
"""

import sys
import argparse

def main():
    parser = argparse.ArgumentParser(description="[descrição]")
    parser.add_argument("target", help="Caminho alvo")
    args = parser.parse_args()
    
    # Lógica principal
    results = run_analysis(args.target)
    report(results)

if __name__ == "__main__":
    main()
```

> 🔴 **Regra de scripts:** Sempre incluam `--help`, saída legível, e exit code 0 (sucesso) / 1 (falha).

### Quando criar `references/`

Crie arquivos de referência quando a skill precisa consultar:
- Templates de código / output
- Checklists extensos
- Especificações técnicas externas
- Bancos de perguntas dinâmicas

### Quando criar `assets/`

Apenas se a skill documenta padrões visuais (ex: design systems, mobile).

---

## 🔗 Integração com Agentes

Após criar a skill, registre-a no agente que deve usá-la:

### Passo 1: Identificar o Agente

| Se a skill é sobre... | Adicionar ao agente |
| :--- | :--- |
| UI/UX/CSS/Layout | `frontend-specialist` |
| API/Server/DB | `backend-specialist` |
| Mobile | `mobile-developer` |
| Segurança/Vulnerabilidades | `security-auditor` |
| Testes/QA | `test-engineer` |
| Planejamento/Tasks | `project-planner` |
| Multi-domínio | `orchestrator` |
| Infraestrutura | `devops-engineer` |

### Passo 2: Adicionar ao Frontmatter do Agente

```yaml
# Antes:
skills: clean-code, react-best-practices

# Depois:
skills: clean-code, react-best-practices, nome-da-nova-skill
```

### Passo 3: Verificar a Descrição no Roteamento

Confirme que a `description` da skill contém palavras-chave que o `intelligent-routing` pode detectar.

---

## ✅ Checklist Final de Qualidade

Antes de declarar a skill pronta, verifique **cada item**:

### Estrutura
- [ ] Diretório em `.agent/skills/nome-da-skill/`
- [ ] `SKILL.md` existe com frontmatter válido
- [ ] `name` em kebab-case e único no ecossistema
- [ ] `description` contém palavras-chave de ativação

### Conteúdo
- [ ] Propósito da skill declarado na primeira linha
- [ ] Seção "Quando Usar" presente
- [ ] Instrução principal clara (princípios OU processo OU orquestração)
- [ ] Seção "Anti-Padrões" presente
- [ ] NÃO usa templates genéricos copiados de outra skill

### Integração
- [ ] Adicionada ao `skills:` do agente relevante (se aplicável)
- [ ] Palavras-chave na description são detectáveis pelo `intelligent-routing`
- [ ] Skills dependentes referenciadas por nome exato

### Qualidade
- [ ] Ensina PRINCÍPIOS, não apenas lista regras
- [ ] Cada instrução explica o PORQUÊ, não apenas o O QUÊ
- [ ] Anti-padrões específicos (não genéricos)
- [ ] Não repete conteúdo de outra skill existente

---

## 🚫 Anti-Padrões

| Anti-Padrão | Por quê é ruim | Correção |
| :--- | :--- | :--- |
| **Skill de lista de regras** | Não ensina a pensar, apenas a obedecer | Adicione "Por quê" a cada regra |
| **Description vaga** | O roteamento não a ativa | Inclua palavras-chave de disparo explícitas |
| **Copiar estrutura de outra skill** | Gera skills genéricas | Adapte ao domínio específico |
| **Criar scripts desnecessários** | Complexidade sem valor | Crie scripts só se forem referenciados |
| **Sem seção de Anti-Padrões** | O agente não sabe o que evitar | Sempre inclua |
| **Skill muito ampla** | Não carrega no contexto certo | Separe em skills menores e focadas |
| **Skill muito estreita** | Não reutilizável | Generalize para o domínio, não para um caso |
| **Nome com espaços ou maiúsculas** | Quebra o roteamento | Use sempre kebab-case |

---

## 📚 Exemplos de Referência

Consulte estas skills como modelo ao criar novas:

| Skill | Tipo | Por que é um bom exemplo |
| :--- | :--- | :--- |
| `brainstorming` | Princípios + Processo | Clara separação entre quando usar e como usar |
| `plan-writing` | Execução + Templates | Princípios bem declarados, anti-padrões úteis |
| `intelligent-routing` | Orquestração | Mapa de conteúdo, árvore de decisão, exemplos |
| `frontend-design` | Princípios profundos | Ensina a pensar, não apenas regras |
| `app-builder` | Orquestração | Mapa de leitura seletiva com tabela clara |

> 🔴 **Leia ao menos 1 skill de referência antes de escrever a nova.**

---

## 🚀 Fluxo de Criação Rápida

```
1. PERGUNTAS   → Responda o Protocolo Socrático
2. TIPO        → Princípios / Execução / Orquestração?
3. ESTRUTURA   → Crie o diretório e SKILL.md
4. FRONTMATTER → name, description (com keywords), version, allowed-tools
5. CORPO       → Use o padrão do tipo escolhido
6. EXTRAS      → scripts/ references/ assets/ apenas se necessários
7. INTEGRAÇÃO  → Adicione ao agente relevante
8. CHECKLIST   → Valide todos os itens antes de finalizar
```

---

## Quando Usar Esta Skill

- Ao criar uma **nova skill** do zero
- Ao **refatorar** uma skill existente que não está sendo ativada corretamente
- Ao **auditar** o ecossistema de skills em busca de lacunas ou sobreposições
- Ao **padronizar** skills criadas de forma ad-hoc
