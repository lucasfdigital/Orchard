---
description: Comando de implantação para lançamentos em produção. Verificações pré-voo e execução de implantação.
---

# /deploy - Implantação em Produção

$ARGUMENTS

---

## Propósito

Este comando lida com a implantação em produção com verificações pré-voo, execução de implantação e verificação.

---

## Subcomandos

```
/deploy            - Assistente de implantação interativo
/deploy check      - Executar apenas verificações pré-implantação
/deploy preview    - Implantar em ambiente de pré-visualização/staging
/deploy production - Implantar em produção
/deploy rollback   - Reverter para a versão anterior
```

---

## Checklist Pré-Implantação

Antes de qualquer implantação:

```markdown
## 🚀 Checklist Pré-Deploy

### Qualidade de Código
- [ ] Sem erros de TypeScript (`npx tsc --noEmit`)
- [ ] ESLint passando (`npx eslint .`)
- [ ] Todos os testes passando (`npm test`)

### Segurança
- [ ] Sem segredos codificados no código (hardcoded)
- [ ] Variáveis de ambiente documentadas
- [ ] Dependências auditadas (`npm audit`)

### Performance
- [ ] Tamanho do bundle aceitável
- [ ] Sem declarações console.log
- [ ] Imagens otimizadas

### Documentação
- [ ] README atualizado
- [ ] CHANGELOG atualizado
- [ ] Documentação de API atualizada

### Pronto para implantar? (s/n)
```

---

## Fluxo de Implantação

```
┌─────────────────┐
│  /deploy        │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Verificações   │
│  Pré-voo        │
└────────┬────────┘
         │
    Passou? ──Não──► Corrigir problemas
         │
        Sim
         │
         ▼
┌─────────────────┐
│  Build da       │
│  aplicação      │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Implantar na   │
│  plataforma     │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Check de saúde │
│  e verificação  │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  ✅ Concluído    │
└─────────────────┘
```

---

## Formato de Saída

### Implantação Bem-Sucedida

```markdown
## 🚀 Implantação Concluída

### Resumo
- **Versão:** v1.2.3
- **Ambiente:** produção
- **Duração:** 47 segundos
- **Plataforma:** Vercel

### URLs
- 🌐 Produção: https://app.exemplo.com
- 📊 Dashboard: https://vercel.com/project

### O que mudou
- Adicionada funcionalidade de perfil de usuário
- Corrigido bug no login
- Dependências atualizadas

### Check de Saúde
✅ API respondendo (200 OK)
✅ Banco de Dados conectado
✅ Todos os serviços saudáveis
```

### Falha na Implantação

```markdown
## ❌ Falha na Implantação

### Erro
Falha no build na etapa: Compilação TypeScript

### Detalhes
```
error TS2345: Argument of type 'string' is not assignable...
```

### Resolução
1. Corrija o erro de TypeScript em `src/services/user.ts:45`
2. Execute `npm run build` localmente para verificar
3. Tente `/deploy` novamente

### Rollback Disponível
A versão anterior (v1.2.2) ainda está ativa.
Execute `/deploy rollback` se necessário.
```

---

## Suporte a Plataformas

| Plataforma | Comando | Notas |
| :--- | :--- | :--- |
| Vercel | `vercel --prod` | Detectado automaticamente para Next.js |
| Railway | `railway up` | Requer CLI do Railway |
| Fly.io | `fly deploy` | Requer flyctl |
| Docker | `docker compose up -d` | Para hospedagem própria (self-hosted) |

---

## Exemplos

```
/deploy
/deploy check
/deploy preview
/deploy production --skip-tests
/deploy rollback
```
