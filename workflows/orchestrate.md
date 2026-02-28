---
description: Coordena múltiplos agentes para tarefas complexas. Use para análise de múltiplas perspectivas, revisões abrangentes ou tarefas que exigem experiência em diferentes domínios.
---

# Orquestração de Múltiplos Agentes

Você está agora no **MODO DE ORQUESTRAÇÃO**. Sua tarefa: coordenar agentes especializados para resolver este problema complexo.

## Tarefa para Orquestrar
$ARGUMENTS

---

## 🔴 CRÍTICO: Requisito Mínimo de Agentes

> ⚠️ **ORQUESTRAÇÃO = MÍNIMO DE 3 AGENTES DIFERENTES**
> 
> Se você usar menos de 3 agentes, você NÃO está orquestrando - está apenas delegando.
> 
> **Validação antes da conclusão:**
> - Conte os agentes invocados.
> - Se `agent_count < 3` → PARE e invoque mais agentes.
> - Agente único = FALHA na orquestração.

### Matriz de Seleção de Agente

| Tipo de Tarefa | Agentes OBRIGATÓRIOS (mínimo) |
| :--- | :--- |
| **Página Web** | frontend-specialist, backend-specialist, test-engineer |
| **API** | backend-specialist, security-auditor, test-engineer |
| **UI/Design** | frontend-specialist, seo-specialist, performance-optimizer |
| **Banco de Dados** | database-architect, backend-specialist, security-auditor |
| **Full Stack** | project-planner, frontend-specialist, backend-specialist, devops-engineer |
| **Debug** | debugger, explorer-agent, test-engineer |
| **Segurança** | security-auditor, penetration-tester, devops-engineer |

---

## Pré-vôo: Verificação de Modo

| Modo Atual | Tipo de Tarefa | Ação |
| :--- | :--- | :--- |
| **plan** | Qualquer | ✅ Prossiga com a abordagem de planejamento primeiro |
| **edit** | Execução simples | ✅ Prossiga diretamente |
| **edit** | Complexa/Vários arquivos | ⚠️ Pergunte: "Esta tarefa exige planejamento. Mudar para o modo plan?" |
| **ask** | Qualquer | ⚠️ Pergunte: "Pronto para orquestrar. Mudar para o modo edit ou plan?" |

---

## 🔴 ORQUESTRAÇÃO EM 2 FASES ESTRITAS

### FASE 1: PLANEJAMENTO (Sequencial - SEM agentes paralelos)

| Passo | Agente | Ação |
| :--- | :--- | :--- |
| 1 | `project-planner` | Criar docs/PLAN.md |
| 2 | (opcional) `explorer-agent` | Descoberta da codebase, se necessário |

> 🔴 **SEM OUTROS AGENTES durante o planejamento!** Apenas project-planner e explorer-agent.

### ⏸️ CHECKPOINT: Aprovação do Usuário

```
Após o término do PLAN.md, PERGUNTE:

"✅ Plano criado: docs/PLAN.md

Você aprova? (S/N)
- S: Iniciar implementação
- N: Vou revisar o plano"
```

> 🔴 **NÃO prossiga para a Fase 2 sem aprovação explícita do usuário!**

### FASE 2: IMPLEMENTAÇÃO (Agentes paralelos após aprovação)

| Grupo Paralelo | Agentes |
| :--- | :--- |
| Fundação | `database-architect`, `security-auditor` |
| Core | `backend-specialist`, `frontend-specialist` |
| Polimento | `test-engineer`, `devops-engineer` |

> ✅ Após a aprovação do usuário, invoque múltiplos agentes em PARALELO.

## Agentes Disponíveis (17 no total)

| Agente | Domínio | Quando Usar |
| :--- | :--- | :--- |
| `project-planner` | Planejamento | Decomposição de tarefas, PLAN.md |
| `explorer-agent` | Descoberta | Mapeamento da codebase |
| `frontend-specialist` | UI/UX | React, Vue, CSS, HTML |
| `backend-specialist` | Servidor | API, Node.js, Python |
| `database-architect` | Dados | SQL, NoSQL, Schema |
| `security-auditor` | Segurança | Vulnerabilidades, Auth |
| `penetration-tester` | Segurança | Testes ativos |
| `test-engineer` | Testes | Unidade, E2E, Cobertura |
| `devops-engineer` | Ops | CI/CD, Docker, Deploy |
| `mobile-developer` | Mobile | React Native, Flutter |
| `performance-optimizer` | Velocidade | Lighthouse, Profiling |
| `seo-specialist` | SEO | Meta, Schema, Rankings |
| `documentation-writer` | Docs | README, docs de API |
| `debugger` | Debug | Análise de erros |
| `game-developer` | Jogos | Unity, Godot |
| `orchestrator` | Meta | Coordenação |

---

## Protocolo de Orquestração

### Passo 1: Analisar Domínios da Tarefa
Identifique TODOS os domínios que esta tarefa toca:
```
□ Segurança     → security-auditor, penetration-tester
□ Backend/API  → backend-specialist
□ Frontend/UI  → frontend-specialist
□ Banco de Dados→ database-architect
□ Testes       → test-engineer
□ DevOps       → devops-engineer
□ Mobile       → mobile-developer
□ Performance  → performance-optimizer
□ SEO          → seo-specialist
□ Planejamento → project-planner
```

### Passo 2: Detecção de Fase

| Se o Plano Existe | Ação |
| :--- | :--- |
| NÃO existe `docs/PLAN.md` | → Vá para a FASE 1 (apenas planejamento) |
| SIM existe `docs/PLAN.md` + aprovado | → Vá para a FASE 2 (implementação) |

### Passo 3: Executar Com Base na Fase

**FASE 1 (Planejamento):**
```
Use o agente project-planner para criar o PLAN.md.
→ PARE após o plano ser criado.
→ PEÇA a aprovação do usuário.
```

**FASE 2 (Implementação - após aprovação):**
```
Invoque agentes em PARALELO:
Use o agente frontend-specialist para [tarefa]
Use o agente backend-specialist para [tarefa]
Use o agente test-engineer para [tarefa]
```

**🔴 CRÍTICO: Passagem de Contexto (OBRIGATÓRIO)**

Ao invocar QUALQUER subagente, você DEVE incluir:

1. **Pedido Original do Usuário**: Texto completo do que o usuário pediu.
2. **Decisões Tomadas**: Todas as respostas do usuário às perguntas Socráticas.
3. **Trabalho dos Agentes Anteriores**: Resumo do que os agentes anteriores fizeram.
4. **Estado Atual do Plano**: Se existirem arquivos de plano no workspace, inclua-os.

**Exemplo com contexto COMPLETO:**
```
Use o agente project-planner para criar o PLAN.md:

**CONTEXTO:**
- Pedido do Usuário: "Uma plataforma social para estudantes, usando dados fictícios"
- Decisões: Tech=Vue 3, Layout=Grid Widgets, Auth=Mock, Design=Jovial e dinâmico
- Trabalho Anterior: O orquestrador fez 6 perguntas, o usuário escolheu todas as opções
- Plano Atual: playful-roaming-dream.md existe no workspace com a estrutura inicial

**TAREFA:** Criar PLAN.md detalhado com base nas decisões ACIMA. NÃO infira o nome da pasta.
```

> ⚠️ **VIOLAÇÃO:** Invocar subagente sem contexto completo = o subagente fará suposições erradas!


### Passo 4: Verificação (OBRIGATÓRIO)
O ÚLTIMO agente deve executar os scripts de verificação apropriados:
```bash
python .agent/skills/vulnerability-scanner/scripts/security_scan.py .
python .agent/skills/lint-and-validate/scripts/lint_runner.py .
```

### Passo 5: Sintetizar Resultados
Combine todas as saídas dos agentes em um relatório unificado.

---

## Formato de Saída

```markdown
## 🎼 Relatório de Orquestração

### Tarefa
[Resumo da tarefa original]

### Modo
[Modo atual do Agente Orchard: plan/edit/ask]

### Agentes Invocados (MÍNIMO 3)
| # | Agente | Área de Foco | Status |
| :--- | :--- | :--- | :--- |
| 1 | project-planner | Decomposição de tarefas | ✅ |
| 2 | frontend-specialist | Implementação de UI | ✅ |
| 3 | test-engineer | Scripts de verificação | ✅ |

### Scripts de Verificação Executados
- [x] security_scan.py → Passou/Falhou
- [x] lint_runner.py → Passou/Falhou

### Descobertas Principais
1. **[Agente 1]**: Descoberta
2. **[Agente 2]**: Descoberta
3. **[Agente 3]**: Descoberta

### Entregas
- [ ] PLAN.md criado
- [ ] Código implementado
- [ ] Testes passando
- [ ] Scripts verificados

### Resumo
[Um parágrafo sintetizando todo o trabalho dos agentes]
```

---

## 🔴 SAÍDA FINAL (EXIT GATE)

Antes de concluir a orquestração, verifique:

1. ✅ **Contagem de Agentes:** `invoked_agents >= 3`
2. ✅ **Scripts Executados:** Pelo menos `security_scan.py` foi executado.
3. ✅ **Relatório Gerado:** Relatório de Orquestração com todos os agentes listados.

> **Se qualquer check falhar → NÃO marque a orquestração como completa. Invoque mais agentes ou execute scripts.**

---

**Inicie a orquestração agora. Selecione 3+ agentes, execute sequencialmente, execute scripts de verificação, sintetize os resultados.**
