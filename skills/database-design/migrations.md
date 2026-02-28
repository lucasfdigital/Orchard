# Princípios de Migração

> Estratégia de migração segura para mudanças com zero downtime.

## Estratégia de Migração Segura

```
Para mudanças com zero downtime:
│
├── Adicionar coluna
│   └── Adicionar como nullable → preencher dados (backfill) → adicionar NOT NULL
│
├── Remover coluna
│   └── Parar de usar → fazer deploy → remover coluna
│
├── Adicionar índice
│   └── CREATE INDEX CONCURRENTLY (não bloqueia a tabela)
│
└── Renomear coluna
    └── Adicionar nova → migrar dados → fazer deploy → excluir a antiga
```

## Filosofia de Migração

- Nunca faça mudanças que quebram o sistema em um único passo.
- Teste as migrações em uma cópia dos dados primeiro.
- Tenha sempre um plano de rollback.
- Execute em transação quando possível.

## Bancos de Dados Serverless

### Neon (PostgreSQL Serverless)

| Recurso | Benefício |
| :--- | :--- |
| Escalar até zero | Economia de custos |
| Branching instantâneo | Dev/Preview |
| PostgreSQL Completo | Compatibilidade |
| Auto-escalonamento | Lida com picos de tráfego |

### Turso (SQLite no Edge)

| Recurso | Benefício |
| :--- | :--- |
| Localizações no Edge | Latência ultra-baixa |
| Compatível com SQLite | Simples |
| Camada gratuita generosa| Custo |
| Distribuição Global | Performance |
