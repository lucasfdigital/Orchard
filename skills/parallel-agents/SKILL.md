---
name: parallel-agents
description: Padrões de orquestração multi-agente. Use quando múltiplas tarefas independentes podem ser executadas com diferentes conhecimentos de domínio ou quando uma análise abrangente exige múltiplas perspectivas.
allowed-tools: Read, Glob, Grep
---

# Agentes Paralelos Nativos

> Orquestração através da Ferramenta de Agentes nativa do Orchard.

## Visão Geral

Esta skill habilita a coordenação de múltiplos agentes especializados através do sistema de agentes nativo do Orchard. Diferente de scripts externos, esta abordagem mantém toda a orquestração sob o controle do Orchard.

## Quando Usar Orquestração

✅ **Bom para:**
- Tarefas complexas que exigem múltiplos domínios de especialidade.
- Análise de código sob as perspectivas de segurança, performance e qualidade.
- Revisões abrangentes (arquitetura + segurança + testes).
- Implementação de funcionalidades que precisam de trabalho em backend + frontend + banco de dados.

❌ **Não indicado para:**
- Tarefas simples de domínio único.
- Correções rápidas ou pequenas mudanças.
- Tarefas onde um único agente é suficiente.

---

## Invocação de Agente Nativo

### Agente Único
```
Use o agente security-auditor para revisar a autenticação.
```

### Cadeia Sequencial
```
Primeiro, use o explorer-agent para descobrir a estrutura do projeto.
Depois, use o backend-specialist para revisar os endpoints da API.
Finalmente, use o test-engineer para identificar lacunas de teste.
```

### Com Passagem de Contexto
```
Use o frontend-specialist para analisar os componentes React.
Com base nessas descobertas, peça ao test-engineer para gerar testes de componente.
```

### Retomar Trabalho Anterior
```
Retome o agente [agentId] e continue com os requisitos adicionais.
```

---

## Padrões de Orquestração

### Padrão 1: Análise Abrangente
```
Agentes: explorer-agent → [agentes-de-dominio] → síntese

1. explorer-agent: Mapear a estrutura da base de código.
2. security-auditor: Postura de segurança.
3. backend-specialist: Qualidade da API.
4. frontend-specialist: Padrões de UI/UX.
5. test-engineer: Cobertura de testes.
6. Sintetizar todas as descobertas.
```

### Padrão 2: Revisão de Funcionalidade
```
Agentes: agentes-de-dominio-afetados → test-engineer

1. Identificar os domínios afetados (backend? frontend? ambos?).
2. Invocar os agentes de domínio relevantes.
3. test-engineer verifica as mudanças.
4. Sintetizar recomendações.
```

### Padrão 3: Auditoria de Segurança
```
Agentes: security-auditor → penetration-tester → síntese

1. security-auditor: Revisão de configuração e código.
2. penetration-tester: Testes ativos de vulnerabilidade.
3. Sintetizar com remediação priorizada.
```

---

## Agentes Disponíveis

| Agente | Especialidade | Frases de Gatilho |
| :--- | :--- | :--- |
| `orchestrator` | Coordenação | "abrangente", "múltiplas perspectivas" |
| `security-auditor` | Segurança | "segurança", "auth", "vulnerabilidades" |
| `penetration-tester` | Testes de Segurança | "pentest", "red team", "exploit" |
| `backend-specialist` | Backend | "API", "servidor", "Node.js", "Express" |
| `frontend-specialist` | Frontend | "React", "UI", "componentes", "Next.js" |
| `test-engineer` | Testes | "testes", "cobertura", "TDD" |
| `devops-engineer` | DevOps | "deploy", "CI/CD", "infraestrutura" |
| `database-architect` | Banco de Dados | "schema", "Prisma", "migrações" |
| `mobile-developer` | Mobile | "React Native", "Flutter", "mobile" |
| `api-designer` | Design de API | "REST", "GraphQL", "OpenAPI" |
| `debugger` | Depuração | "bug", "erro", "não funciona" |
| `explorer-agent` | Descoberta | "explorar", "mapear", "estrutura" |
| `documentation-writer`| Documentação | "escrever docs", "criar README", "gerar docs de API" |
| `performance-optimizer`| Performance | "lento", "otimizar", "profiling" |
| `project-planner` | Planejamento | "plano", "roadmap", "marcos (milestones)" |
| `seo-specialist` | SEO | "SEO", "meta tags", "ranking de busca" |
| `game-developer` | Desenvolvimento de Jogos| "jogo", "Unity", "Godot", "Phaser" |

---

## Agentes Nativos do Orchard

Estes trabalham em conjunto com os agentes customizados:

| Agente | Modelo | Propósito |
| :--- | :--- | :--- |
| **Explore** | Haiku | Busca rápida na base de código (apenas leitura). |
| **Plan** | Sonnet | Pesquisa durante o modo de plano. |
| **General-purpose** | Sonnet | Modificações complexas de múltiplas etapas. |

Use o **Explore** para buscas rápidas e os **agentes customizados** para especialidade de domínio.

---

## Protocolo de Síntese

Após todos os agentes concluírem, sintetize:

```markdown
## Síntese de Orquestração

### Resumo da Tarefa
[O que foi realizado]

### Contribuições dos Agentes
| Agente | Descoberta |
| :--- | :--- |
| security-auditor | Encontrou X |
| backend-specialist | Identificou Y |

### Recomendações Consolidadas
1. **Crítico**: [Problema do Agente A]
2. **Importante**: [Problema do Agente B]
3. **Desejável**: [Melhoria do Agente C]

### Itens de Ação
- [ ] Corrigir problema crítico de segurança
- [ ] Refatorar endpoint da API
- [ ] Adicionar testes ausentes
```

---

## Melhores Práticas

1. **Agentes disponíveis** - 17 agentes especializados podem ser orquestrados.
2. **Ordem lógica** - Descoberta → Análise → Implementação → Teste.
3. **Compartilhar contexto** - Passe as descobertas relevantes para os agentes subsequentes.
4. **Síntese única** - Um relatório unificado, não resultados separados.
5. **Verificar mudanças** - Sempre inclua o `test-engineer` para modificações de código.

---

## Principais Benefícios

- ✅ **Sessão única** - Todos os agentes compartilham o contexto.
- ✅ **Controlado por IA** - O Claude orquestra de forma autônoma.
- ✅ **Integração nativa** - Funciona com os agentes nativos Explore e Plan.
- ✅ **Suporte a retomada** - Pode continuar o trabalho de um agente anterior.
- ✅ **Passagem de contexto** - As descobertas fluem entre os agentes.
