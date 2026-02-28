---
name: server-management
description: Princípios de gerenciamento de servidor e tomada de decisão. Gerenciamento de processos, estratégia de monitoramento e decisões de escalonamento. Ensina a pensar, não comandos.
allowed-tools: Read, Write, Edit, Glob, Grep, Bash
---

# Gerenciamento de Servidor

> Princípios de gerenciamento de servidor para operações em produção.
> **Aprenda a PENSAR, não a memorizar comandos.**

---

## 1. Princípios de Gerenciamento de Processos

### Seleção de Ferramentas

| Cenário | Ferramenta |
| :--- | :--- |
| **App Node.js** | PM2 (clustering, recarregamento) |
| **Qualquer app** | systemd (nativo do Linux) |
| **Containers** | Docker/Podman |
| **Orquestração** | Kubernetes, Docker Swarm |

### Objetivos do Gerenciamento de Processos

| Objetivo | O que significa |
| :--- | :--- |
| **Reiniciar em caso de falha**| Recuperação automática |
| **Recarregamento sem downtime**| Sem interrupção do serviço |
| **Clustering** | Usar todos os núcleos da CPU |
| **Persistência** | Sobreviver à reinicialização do servidor |

---

## 2. Princípios de Monitoramento

### O que Monitorar

| Categoria | Métricas Chave |
| :--- | :--- |
| **Disponibilidade** | Uptime, health checks |
| **Performance** | Tempo de resposta, throughput |
| **Erros** | Taxa de erro, tipos de erro |
| **Recursos** | CPU, memória, disco |

### Estratégia de Gravidade de Alerta

| Nível | Resposta |
| :--- | :--- |
| **Crítico** | Ação imediata |
| **Aviso (Warning)** | Investigar em breve |
| **Info** | Revisar diariamente |

### Seleção de Ferramentas de Monitoramento

| Necessidade | Opções |
| :--- | :--- |
| Simples/Gratuito | Métricas do PM2, htop |
| Observabilidade total | Grafana, Datadog |
| Rastreamento de erros (Error tracking)| Sentry |
| Uptime | UptimeRobot, Pingdom |

---

## 3. Princípios de Gerenciamento de Logs

### Estratégia de Log

| Tipo de Log | Propósito |
| :--- | :--- |
| **Logs da aplicação** | Depuração, auditoria |
| **Logs de acesso** | Análise de tráfego |
| **Logs de erro** | Detecção de problemas |

### Princípios de Log

1. **Rotacionar logs** para evitar que o disco fique cheio.
2. **Logging estruturado** (JSON) para facilitar a análise.
3. **Níveis apropriados** (error/warn/info/debug).
4. **Sem dados sensíveis** nos logs.

---

## 4. Decisões de Escalonamento (Scaling)

### Quando Escalar

| Sintoma | Solução |
| :--- | :--- |
| CPU alta | Adicionar instâncias (horizontal) |
| Memória alta | Aumentar RAM ou corrigir vazamento |
| Resposta lenta | Fazer profiling primeiro, depois escalar |
| Picos de tráfego | Auto-scaling |

### Estratégia de Escalonamento

| Tipo | Quando Usar |
| :--- | :--- |
| **Vertical** | Correção rápida, instância única |
| **Horizontal** | Sustentável, distribuído |
| **Automático (Auto)**| Tráfego variável |

---

## 5. Princípios de Health Check

### O que Constitui um Estado Saudável

| Verificação | Significado |
| :--- | :--- |
| **HTTP 200** | Serviço respondendo |
| **Banco de dados conectado**| Dados acessíveis |
| **Dependências OK** | Serviços externos alcançáveis |
| **Recursos OK** | CPU/memória não exauridos |

### Implementação de Health Check

- Simples: Apenas retorna 200.
- Profundo: Verifica todas as dependências.
- Escolha com base nas necessidades do balanceador de carga.

---

## 6. Princípios de Segurança

| Área | Princípio |
| :--- | :--- |
| **Acesso** | Apenas chaves SSH, sem senhas |
| **Firewall** | Apenas as portas necessárias abertas |
| **Atualizações** | Patches de segurança regulares |
| **Segredos** | Variáveis de ambiente, não arquivos |
| **Auditoria** | Log de acessos e mudanças |

---

## 7. Prioridade na Resolução de Problemas (Troubleshooting)

Quando algo está errado:

1. **Verifique se está rodando** (status do processo).
2. **Verifique os logs** (mensagens de erro).
3. **Verifique os recursos** (disco, memória, CPU).
4. **Verifique a rede** (portas, DNS).
5. **Verifique as dependências** (banco de dados, APIs).

---

## 8. Anti-Padrões

| ❌ NÃO Faça | ✅ Faça |
| :--- | :--- |
| Rodar como root | Usar um usuário não-root |
| Ignorar logs | Configurar rotação de logs |
| Pular o monitoramento | Monitorar desde o primeiro dia |
| Reinicializações manuais | Configurar reinicialização automática |
| Sem backups | Agenda regular de backups |

---

> **Lembre-se:** Um servidor bem gerenciado é entediante. Esse é o objetivo.
