---
description: Exibe o status do agente e do projeto. Acompanhamento de progresso e painel de status.
---

# /status - Mostrar Status

$ARGUMENTS

---

## Tarefa

Mostrar o status atual do projeto e dos agentes.

### O Que Mostra

1. **Informações do Projeto**
   - Nome e caminho do projeto.
   - Tech stack.
   - Funcionalidades atuais.

2. **Painel de Status dos Agentes**
   - Quais agentes estão rodando.
   - Quais tarefas foram concluídas.
   - Trabalho pendente.

3. **Estatísticas de Arquivos**
   - Contagem de arquivos criados.
   - Contagem de arquivos modificados.

4. **Status de Visualização (Preview)**
   - Se o servidor está rodando.
   - URL.
   - Check de saúde.

---

## Exemplo de Saída

```
=== Status do Projeto ===

📁 Projeto: meu-ecommerce
📂 Caminho: C:/projects/meu-ecommerce
🏷️ Tipo: nextjs-ecommerce
📊 Status: ativo

🔧 Tech Stack:
   Framework: next.js
   Banco de Dados: postgresql
   Auth: clerk
   Pagamento: stripe

✅ Funcionalidades (5):
   • listagem-de-produtos
   • carrinho
   • checkout
   • auth-de-usuario
   • historico-de-pedidos

⏳ Pendente (2):
   • painel-admin
   • notificacoes-por-email

📄 Arquivos: 73 criados, 12 modificados

=== Status dos Agentes ===

✅ database-architect → Concluído
✅ backend-specialist → Concluído
🔄 frontend-specialist → Componentes do dashboard (60%)
⏳ test-engineer → Aguardando

=== Visualização ===

🌐 URL: http://localhost:3000
💚 Saúde: OK
```

---

## Técnico

O status usa estes scripts:
- `python .agent/scripts/session_manager.py status`
- `python .agent/scripts/auto_preview.py status`
