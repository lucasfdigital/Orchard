---
description: Comando para criar nova aplicação. Aciona a skill App Builder e inicia um diálogo interativo com o usuário.
---

# /create - Criar Aplicação

$ARGUMENTS

---

## Tarefa

Este comando inicia um novo processo de criação de aplicação.

### Passos:

1. **Análise de Solicitação**
   - Entender o que o usuário deseja.
   - Se faltarem informações, use a skill `conversation-manager` para perguntar.

2. **Planejamento do Projeto**
   - Use o agente `project-planner` para a decomposição de tarefas.
   - Determine a stack técnica.
   - Planeje a estrutura de arquivos.
   - Crie o arquivo de plano e prossiga para a construção.

3. **Construção da Aplicação (Após Aprovação)**
   - Orquestre com a skill `app-builder`.
   - Coordine os agentes especialistas:
     - `database-architect` → Schema.
     - `backend-specialist` → API.
     - `frontend-specialist` → UI.

4. **Visualização (Preview)**
   - Inicie com `auto_preview.py` quando concluído.
   - Apresente a URL ao usuário.

---

## Exemplos de Uso

```
/create site de blog
/create app de e-commerce com listagem de produtos e carrinho
/create todo app
/create clone do Instagram
/create sistema de crm com gestão de clientes
```

---

## Antes de Começar

Se a solicitação não estiver clara, faça estas perguntas:
- Que tipo de aplicação?
- Quais são as funcionalidades básicas?
- Quem irá usá-la?

Use padrões (defaults), adicione detalhes depois.
