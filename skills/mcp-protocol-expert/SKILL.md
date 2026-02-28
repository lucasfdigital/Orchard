---
name: mcp-protocol-expert
description: Especialista em Model Context Protocol (MCP). Fornece diretrizes para construção de servidores MCP, integração de ferramentas, recursos e prompts via protocolo padronizado. Use ao desenvolver conectores de IA, servidores de contexto ou integrar ferramentas externas ao Antigravity.
allowed-tools: Read, Write, Edit, Bash
version: 1.0
priority: HIGH
---

# MCP Protocol Expert - Integração Universal de Contexto

> **SKILL DE CONECTIVIDADE** - Padronize como a IA interage com o mundo externo através do **Model Context Protocol**.

---

## Princípios MCP

| Conceito | Descrição |
| :--- | :--- |
| **Resources** | Dados estáticos ou dinâmicos que a IA pode ler (Arquivos, DBs, APIs). |
| **Tools** | Funções executáveis que a IA pode chamar para realizar ações no mundo real. |
| **Prompts** | Modelos de instruções pré-definidos para guiar o comportamento da IA. |
| **Transparência** | Todo dado passado via MCP deve ser auditável e seguro. |

---

## Arquitetura de Servidor MCP

| Componente | Padrão Orchard |
| :--- | :--- |
| **Transport** | Use `stdio` para conexões locais rápidas ou `sse` para web. |
| **SDK** | Dê preferência ao SDK oficial (TypeScript/Python). |
| **Capabilities** | Declare explicitamente o que o servidor pode fazer (Logging, Sampling). |
| **Segurança** | Valide todos os inputs recebidos via Tool Calling. |

---

## Implementação de Tools

| Regra | Descrição |
| :--- | :--- |
| **Schema JSON** | Use schemas rigorosos para descrever argumentos das ferramentas. |
| **Idempotência** | Ferramentas de leitura devem ser seguras (read-only). |
| **Tratamento de Erro** | Retorne mensagens de erro úteis para a IA entender o que falhou. |
| **Timeout** | Implemente timeouts rigorosos para evitar loops infinitos. |

---

## Gerenciamento de Resources

| Padrão | Aplicação |
| :--- | :--- |
| **URI Templates** | Use URIs padronizadas para identificar recursos (ex: `postgres://db/table`). |
| **MIME Types** | Sempre declare o tipo de conteúdo (text/plain, application/json). |
| **Caching** | Implemente estratégias de cache para recursos que não mudam frequentemente. |

---

## Anti-Padrões MCP (NÃO FAÇA)

| ❌ Padrão | ✅ Correção |
| :--- | :--- |
| Tool com 50 argumentos | Divida em ferramentas menores e específicas. |
| Resource sem URI | Use o padrão `protocolo://caminho`. |
| Erro "Silent" | Retorne o erro técnico para o modelo tentar outra abordagem. |
| Permissão total | Use scoped permissions para cada servidor MCP. |

---

## 🔴 Verificação de Segurança (CRÍTICO)

**Antes de expor um servidor MCP, verifique:**

1. **Vazamento de Path:** O servidor pode acessar arquivos fora do diretório permitido?
2. **Injeção de Comando:** O input da IA é passado diretamente para o shell? (PROIBIDO)
3. **Exposição de Segredos:** API Keys estão no código ou no ambiente seguro?

---

> 🔴 **"Um servidor MCP mal configurado é uma porta aberta no seu sistema. Valide tudo."**

*Conectando o Orchard ao futuro. Licença MIT.*
