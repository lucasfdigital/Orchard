---
name: deployment-procedures
description: Princípios de implantação em produção e tomada de decisão. Workflows de implantação segura, estratégias de rollback e verificação. Ensina a pensar, não apenas scripts.
allowed-tools: Read, Glob, Grep, Bash
---

# Procedimentos de Implantação

> Princípios de implantação e tomada de decisão para lançamentos seguros em produção.
> **Aprenda a PENSAR, não a memorizar scripts.**

---

## ⚠️ Como Usar Esta Skill

Esta skill ensina **princípios de implantação**, não scripts bash para copiar.

- Cada implantação é única.
- Entenda o PORQUÊ por trás de cada passo.
- Adapte os procedimentos à sua plataforma.

---

## 1. Seleção de Plataforma

### Árvore de Decisão

```
O que você está implantando?
│
├── Site Estático / JAMstack
│   └── Vercel, Netlify, Cloudflare Pages
│
├── App Web Simples
│   ├── Gerenciado → Railway, Render, Fly.io
│   └── Controle  → VPS + PM2/Docker
│
├── Microsserviços
│   └── Orquestração de contêineres
│
└── Serverless
    └── Edge functions, Lambda
```

### Cada Plataforma tem Procedimentos Diferentes

| Plataforma | Método de Implantação |
| :--- | :--- |
| **Vercel/Netlify** | Git push, auto-deploy |
| **Railway/Render** | Git push ou CLI |
| **VPS + PM2** | SSH + passos manuais |
| **Docker** | Push de imagem + orquestração |
| **Kubernetes** | kubectl apply |

---

## 2. Princípios de Pré-Implantação

### As 4 Categorias de Verificação

| Categoria | O que verificar |
| :--- | :--- |
| **Qualidade do Código** | Testes passando, lint limpo, revisado |
| **Build** | Build de produção funciona, sem avisos |
| **Ambiente** | Variáveis de ambiente definidas, segredos atuais |
| **Segurança** | Backup feito, plano de rollback pronto |

### Checklist Pré-Implantação

- [ ] Todos os testes passando.
- [ ] Código revisado e aprovado.
- [ ] Build de produção bem-sucedido.
- [ ] Variáveis de ambiente verificadas.
- [ ] Migrações de banco de dados prontas (se houver).
- [ ] Plano de rollback documentado.
- [ ] Equipe notificada.
- [ ] Monitoramento pronto.

---

## 3. Princípios do Workflow de Implantação

### O Processo de 5 Fases

```
1. PREPARAR
   └── Verificar código, build, variáveis de ambiente

2. BACKUP
   └── Salvar o estado atual antes de mudar

3. IMPLANTAR (DEPLOY)
   └── Executar com o monitoramento aberto

4. VERIFICAR
   └── Check de saúde, logs, fluxos principais

5. CONFIRMAR ou REVERTER (ROLLBACK)
   └── Tudo certo? Confirme. Problemas? Reverte.
```

### Princípios das Fases

| Fase | Princípio |
| :--- | :--- |
| **Preparar** | Nunca implante código não testado. |
| **Backup** | Não há rollback sem backup. |
| **Implantar** | Observe acontecer, não vá embora. |
| **Verificar** | Confie, mas verifique. |
| **Confirmar** | Tenha o gatilho de rollback pronto. |

---

## 4. Verificação Pós-Implantação

### O que Verificar

| Check | Por que |
| :--- | :--- |
| **Endpoint de saúde** | O serviço está rodando |
| **Logs de erro** | Sem novos erros |
| **Fluxos principais** | Funcionalidades críticas funcionam |
| **Performance** | Tempos de resposta aceitáveis |

### Janela de Verificação

- **Primeiros 5 minutos**: Monitoramento ativo.
- **15 minutos**: Confirmar estabilidade.
- **1 hora**: Verificação final.
- **Próximo dia**: Revisar métricas.

---

## 5. Princípios de Rollback

### Quando Reverter (Rollback)

| Sintoma | Ação |
| :--- | :--- |
| Serviço fora do ar | Reverter imediatamente |
| Erros críticos | Reverter |
| Performance >50% degradada | Considerar reversão |
| Problemas menores | Corrigir pra frente (fix forward) se for rápido |

### Estratégia de Rollback por Plataforma

| Plataforma | Método de Rollback |
| :--- | :--- |
| **Vercel/Netlify** | Re-implantar commit anterior |
| **Railway/Render** | Reverter no dashboard |
| **VPS + PM2** | Restaurar backup, reiniciar |
| **Docker** | Tag de imagem anterior |
| **K8s** | kubectl rollout undo |

### Princípios de Rollback

1. **Velocidade sobre perfeição**: Reverta primeiro, depure depois.
2. **Não acumule erros**: Reversão única, não múltiplas mudanças.
3. **Comunique**: Informe a equipe sobre o que aconteceu.
4. **Post-mortem**: Entenda o motivo após a estabilização.

---

## 6. Implantação Zero-Downtime

### Estratégias

| Estratégia | Como Funciona |
| :--- | :--- |
| **Rolling** | Substitui as instâncias uma por uma |
| **Blue-Green** | Alterna o tráfego entre ambientes |
| **Canary** | Mudança gradual de tráfego |

### Princípios de Seleção

| Cenário | Estratégia |
| :--- | :--- |
| Lançamento padrão | Rolling |
| Mudança de alto risco | Blue-green (reversão fácil) |
| Necessidade de validação | Canary (teste com tráfego real) |

---

## 7. Procedimentos de Emergência

### Prioridade de Serviço Fora do Ar

1. **Avaliar**: Qual é o sintoma?
2. **Correção rápida**: Reinicie se não estiver claro.
3. **Reverter**: Se reiniciar não ajudar.
4. **Investigar**: Após a estabilização.

### Ordem de Investigação

| Check | Problemas Comuns |
| :--- | :--- |
| **Logs** | Erros, exceções |
| **Recursos** | Disco cheio, memória |
| **Rede** | DNS, firewall |
| **Dependências** | Banco de dados, APIs |

---

## 8. Anti-Padrões

| ❌ NÃO Faça | ✅ Faça |
| :--- | :--- |
| Implantar na sexta-feira | Implantar no início da semana |
| Apressar a implantação | Siga o processo |
| Pular o staging | Sempre teste primeiro |
| Implantar sem backup | Backup antes de implantar |
| Sair logo após implantar | Monitore por 15+ min |
| Múltiplas mudanças de uma vez | Uma mudança por vez |

---

## 9. Checklist de Decisão

Antes de implantar:

- [ ] **Procedimento adequado para a plataforma?**
- [ ] **Estratégia de backup pronta?**
- [ ] **Plano de rollback documentado?**
- [ ] **Monitoramento configurado?**
- [ ] **Equipe notificada?**
- [ ] **Tempo para monitorar depois?**

---

## 10. Melhores Práticas

1. **Implantações pequenas e frequentes** em vez de grandes lançamentos.
2. **Feature flags** para mudanças arriscadas.
3. **Automatize** passos repetitivos.
4. **Documente** cada implantação.
5. **Revise** o que deu errado após problemas.
6. **Teste o rollback** antes de precisar dele.

---

> **Lembre-se:** Toda implantação é um risco. Minimize o risco através da preparação, não da velocidade.
