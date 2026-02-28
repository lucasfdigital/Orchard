---
description: Adiciona ou atualiza funcionalidades em uma aplicação existente. Usado para desenvolvimento iterativo.
---

# /enhance - Atualizar Aplicação

$ARGUMENTS

---

## Tarefa

Este comando adiciona funcionalidades ou faz atualizações em uma aplicação existente.

### Passos:

1. **Entender o Estado Atual**
   - Carregar o estado do projeto com `python .agent/scripts/session_manager.py info`.
   - Entender as funcionalidades existentes e a tech stack.

2. **Planejar Mudanças**
   - Determinar o que será adicionado/alterado.
   - Detectar arquivos afetados.
   - Verificar dependências.

3. **Apresentar o Plano ao Usuário** (para grandes mudanças)
   ```
   "Para adicionar o painel administrativo:
   - Vou criar 15 novos arquivos.
   - Vou atualizar 8 arquivos.
   - Levará cerca de 10 minutos.
   
   Posso começar?"
   ```

4. **Aplicar**
   - Chamar os agentes relevantes.
   - Fazer as alterações.
   - Testar.

5. **Atualizar Visualização (Preview)**
   - Hot reload ou reiniciar.

---

## Exemplos de Uso

```
/enhance adicionar modo escuro
/enhance construir painel admin
/enhance integrar sistema de pagamento
/enhance adicionar funcionalidade de busca
/enhance editar página de perfil
/enhance tornar responsivo
```

---

## Atenção

- Obtenha aprovação para grandes mudanças.
- Avise sobre solicitações conflitantes (ex: "usar Firebase" quando o projeto usa PostgreSQL).
- Faça commit de cada alteração com git.
