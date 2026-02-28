# Seleção de ORM (2025)

> Escolha o ORM baseado na implantação e nas necessidades de DX (Experiência do Desenvolvedor).

## Árvore de Decisão

```
Qual é o contexto?
│
├── Implantação no Edge / Tamanho do bundle importa
│   └── Drizzle (menor tamanho, estilo próximo ao SQL)
│
├── Melhor DX / Schema-first
│   └── Prisma (migrações, studio)
│
├── Controle máximo
│   └── SQL Puro com query builder
│
└── Ecossistema Python
    └── SQLAlchemy 2.0 (suporte a async)
```

## Comparação

| ORM | Ideal Para | Trade-offs |
| :--- | :--- | :--- |
| **Drizzle** | Edge, TypeScript | Mais novo, menos exemplos |
| **Prisma** | DX, gerenciamento de schema | Mais pesado, não pronto para edge |
| **Kysely** | SQL builder com segurança de tipos | Migrações manuais |
| **SQL Puro** | Queries complexas, controle | Segurança de tipos manual |
