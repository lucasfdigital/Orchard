---
description: Início, parada e verificação de status do servidor de visualização. Gerenciamento de servidor de desenvolvimento local.
---

# /preview - Gerenciamento de Visualização

$ARGUMENTS

---

## Tarefa

Gerenciar o servidor de visualização: iniciar, parar, verificar status.

### Comandos

```
/preview           - Mostrar status atual
/preview start     - Iniciar servidor
/preview stop      - Parar servidor
/preview restart   - Reiniciar
/preview check     - Check de saúde
```

---

## Exemplos de Uso

### Iniciar Servidor
```
/preview start

Resposta:
🚀 Iniciando visualização...
   Porta: 3000
   Tipo: Next.js

✅ Visualização pronta!
   URL: http://localhost:3000
```

### Verificação de Status
```
/preview

Resposta:
=== Status da Visualização ===

🌐 URL: http://localhost:3000
📁 Projeto: C:/projects/meu-app
🏷️ Tipo: nextjs
💚 Saúde: OK
```

### Conflito de Porta
```
/preview start

Resposta:
⚠️ A porta 3000 está em uso.

Opções:
1. Iniciar na porta 3001
2. Fechar app na 3000
3. Especificar porta diferente

Qual delas? (padrão: 1)
```

---

## Técnico

A visualização automática usa o script `auto_preview.py`:

```bash
python .agent/scripts/auto_preview.py start [porta]
python .agent/scripts/auto_preview.py stop
python .agent/scripts/auto_preview.py status
```
