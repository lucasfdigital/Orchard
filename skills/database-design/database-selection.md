# Seleção de Banco de Dados (2025)

> Escolha o banco de dados baseado no contexto, não no padrão.

## Árvore de Decisão

```
Quais são os seus requisitos?
│
├── Recursos relacionais totais necessários
│   ├── Auto-hospedado (Self-hosted) → PostgreSQL
│   └── Serverless → Neon, Supabase
│
├── Implantação no Edge / Latência ultra-baixa
│   └── Turso (SQLite no edge)
│
├── IA / Busca vetorial (Vector search)
│   └── PostgreSQL + pgvector
│
├── Simples / Incorporado / Local
│   └── SQLite
│
└── Distribuição Global
    └── PlanetScale, CockroachDB, Turso
```

## Comparação

| Banco de Dados | Ideal Para | Trade-offs |
| :--- | :--- | :--- |
| **PostgreSQL** | Recursos completos, queries complexas | Requer hospedagem |
| **Neon** | PG Serverless, branching | Complexidade do PG |
| **Turso** | Edge, baixa latência | Limitações do SQLite |
| **SQLite** | Simples, incorporado, local | Apenas um escritor (single-writer) |
| **PlanetScale** | MySQL, escala global | Sem chaves estrangeiras (foreign keys) |

## Perguntas a Fazer

1. Qual é o ambiente de implantação?
2. Quão complexas são as queries?
3. Edge/Serverless é importante?
4. Busca vetorial é necessária?
5. Distribuição global é requisito?
