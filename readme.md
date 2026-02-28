# 🍎 The Orchard
### AI Agent templates with Skills, Agents, and Workflows

O Orchard é um ecossistema de elite para o **Antigravity**, fornecendo um "conselho de especialistas" completo para o seu workspace. Diferente de modelos generalistas, o Orchard traz personas especializadas com conhecimento profundo de domínio, 100% localizado em Português.

---

## ⚡ Instalação Rápida (Windows)

Abra o PowerShell na raiz do seu projeto e cole o comando abaixo para instalar o ecossistema completo na sua pasta `.agent`:

```powershell
git clone https://github.com/lucasfdigital/Orchard.git .agent
```

---

## 🧱 O que está incluído

| Componente | Qtd | Descrição |
| :--- | :--- | :--- |
| **Agentes** | 27 | Personas especializadas em diversas verticais. |
| **Skills** | 40 | Módulos de conhecimento e padrões de indústria. |
| **Workflows** | 13 | Comandos `/` automatizados para tarefas complexas. |
| **Regras** | 1 | Protocolo mestre `GEMINI.md` para orquestração. |

---

## 🤖 Como funciona (Roteamento Inteligente)

Você não precisa decorar os comandos ou nomes dos agentes. O Orchard utiliza o protocolo de **Roteamento Inteligente** para detectar sua necessidade automaticamente.

**Exemplo:**
- **Você:** "Preciso configurar um pipeline de CI/CD para meu app Next.js"
- **Orchard:** 🤖 *Aplicando conhecimento de `@devops-engineer` + `@frontend-specialist`...*

---

## 👥 Agentes Especialistas

O Orchard oferece um conselho completo dividido por áreas de atuação:

### 🏗️ Coordenação e Estratégia
| Agente | Especialidade |
| :--- | :--- |
| **`@orchestrator`** | Maestro do sistema. Coordena múltiplos agentes. |
| **`@project-planner`** | Especialista em metodologia de 4 fases e roadmaps. |
| **`@product-owner`** | Gestão de backlog, MVPs e histórias de usuário. |
| **`@product-manager`** | Visão do produto e sucesso do usuário. |

### 💻 Engenharia e Tech
| Agente | Especialidade |
| :--- | :--- |
| **`@frontend-specialist`** | Especialista em React/Next.js e UI/UX. |
| **`@backend-specialist`** | APIs, lógica de servidor e sistemas distribuídos. |
| **`@ai-application-engineer`**| Integração de LLMs, RAG e Agentes inteligentes. |
| **`@cloud-native-architect`**| Infraestrutura, K8s, Multi-cloud e GitOps. |
| **`@mobile-developer`** | Desenvolvimento nativo (React Native/Flutter). |
| **`@database-architect`** | Modelagem de dados, queries e performance. |
| **`@data-engineer`** | Modern Data Stack (Polars, DuckDB, dbt) e Pipelines. |
| **`@game-developer`** | Mecânicas, física e motores de jogos. |
| **`@devops-engineer`** | Infraestrutura, Docker, CI/CD e Cloud. |

### ⚡ Qualidade e Performance
| Agente | Especialidade |
| :--- | :--- |
| **`@debugger`** | Investigação sistemática de causas raízes e bugs. |
| **`@test-engineer`** | Cobertura de testes (Unit, Integration, E2E). |
| **`@performance-optimizer`** | Otimização de recursos e Core Web Vitals. |
| **`@qa-automation-engineer`**| Automação de QA e pipelines de teste. |

### 🛡️ Segurança (Red & Blue Team)
| Agente | Especialidade |
| :--- | :--- |
| **`@security-auditor`** | Auditoria defensiva e conformidade de segurança. |
| **`@penetration-tester`** | Segurança ofensiva, exploits e vulnerabilidades. |

### 📈 Negócios e Marketing
| Agente | Especialidade |
| :--- | :--- |
| **`@marketing-specialist`** | Conversão, ads e estratégias de crescimento. |
| **`@creative-writer`** | Storytelling e criação de conteúdo de marca. |
| **`@seo-specialist`** | SEO tradicional e GEO (AI Search Engine Optimization). |
| **`@sales-ops`** | Operações de CRM, forecasts e eficiência de vendas. |
| **`@revops-specialist`** | Alinhamento de Vendas, Marketing e Customer Success. |
| **`@documentation-writer`**| Documentação técnica para humanos e IAs. |

### 🔍 Pesquisa e Legado
| Agente | Especialidade |
| :--- | :--- |
| **`@explorer-agent`** | Coleta de contexto em bases de código desconhecidas. |
| **`@code-archaeologist`** | Análise de código legado e dívida técnica. |

---

## 📦 Skills e Conhecimento (Módulos)

As Skills fornecem ao Antigravity padrões e diretrizes de nível sênior:

**💻 Tech & Frameworks**
- `nextjs-react-expert`: Padrões modernos de frontend.
- `nodejs-best-practices`: Escalabilidade e segurança em Node.
- `python-patterns`: Design patterns e async no Python.
- `rust-pro`: Segurança de memória e performance.
- `tailwind-patterns`: Estilização atômica e design systems.
- `mcp-protocol-expert`: Integração universal via Model Context Protocol.

**🏗️ Arquitetura & Banco de Dados**
- `api-patterns`: REST, GraphQL e documentação OpenAPI.
- `database-design`: PostgreSQL, NoSQL e estratégias de índice.
- `iac-patterns`: Infraestrutura como Código (Terraform, Pulumi).
- `architecture`: Princípios de Clean Architecture e Microservices.

**🕹️ Game Development**
- `game-development`: Orquestrador mestre.
- `2d-games` / `3d-games` / `multiplayer` / `vr-ar` / `web-games`.
- `game-design` / `game-art` / `game-audio`.

**🚀 DevOps & Produtividade**
- `deployment-procedures`: Release management seguro.
- `server-management`: Nix, Bash, Linux e monitoramento.
- `powershell-windows`: Automação em ambiente Windows.
- `testing-patterns`: TDD, BDD e pirâmide de testes.
- `data-pipelining-modern`: Modern Data Stack (Polars, DuckDB, dbt).

**📈 Marketing & SEO**
- `seo-fundamentals`: E-E-A-T e Core Web Vitals.
- `geo-fundamentals`: Otimização para mecanismos de Generative AI.
- `i18n-localization`: Internacionalização e suporte RTL.

---

## ⚡ Workflows (Comandos /)

Invoque automações complexas diretamente no chat:
- `/plan`: Criação de roadmaps e quebra de tarefas.
- `/debug`: Investigação sistemática de erros.
- `/create`: Scaffold de novas aplicações e componentes.
- `/ui-ux-pro-max`: Design de interfaces com foco em conversão.
- `/test`: Geração automática de suítes de teste.
- `/deploy`: Pipeline de lançamento em produção.
- `/audit`: Auditoria completa de saúde (Segurança, Lint, Perf).
- `/refactor`: Limpeza sistemática de dívida técnica.

---

## ⚠️ Nota sobre o .gitignore

Para que o Antigravity indexe corretamente o Orchard:
1. Certifique-se de que a pasta `.agent/` **NÃO** esteja no seu `.gitignore`.
2. Para ocultar os arquivos do seu commit de código pessoal, use: `.git/info/exclude`.

---

## 🤝 Contribuição

O Orchard é um ecossistema comunitário. Cultive conosco!

---
*Cultivando inovação no projeto Orchard. Licença MIT.*