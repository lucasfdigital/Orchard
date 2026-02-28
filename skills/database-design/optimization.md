# Otimização de Query

> Problema N+1, EXPLAIN ANALYZE, prioridades de otimização.

## Problema N+1

```
O que é N+1?
├── 1 query para buscar os registros pai
├── N queries para buscar os registros relacionados
└── Muito lento!

Soluções:
├── JOIN → Query única com todos os dados
├── Eager loading → ORM lida com o JOIN
├── DataLoader → Agrupamento (batch) e cache (GraphQL)
├── Subquery → Busca os relacionados em uma só query
```

## Mentalidade de Análise de Query

```
Antes de otimizar:
├── Use EXPLAIN ANALYZE na query
├── Procure por Seq Scan (escaneamento completo da tabela)
├── Verifique as linhas reais vs estimadas
└── Identifique índices ausentes
```

## Prioridades de Otimização

1. **Adicionar índices ausentes** (problema mais comum).
2. **Selecionar apenas as colunas necessárias** (não use `SELECT *`).
3. **Usar JOINs adequados** (evite subqueries quando possível).
4. **Limitar cedo** (paginação no nível do banco de dados).
5. **Cache** (quando apropriado).
