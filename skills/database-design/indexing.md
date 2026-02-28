# Princípios de Indexação

> Quando e como criar índices de forma eficaz.

## Quando Criar Índices

```
Indexe estes:
├── Colunas em cláusulas WHERE
├── Colunas em condições de JOIN
├── Colunas em ORDER BY
├── Colunas de chave estrangeira (Foreign key)
└── Restrições de Unicidade (Unique constraints)

Não indexe em excesso:
├── Tabelas com muita escrita (insersões mais lentas)
├── Colunas de baixa cardinalidade
├── Colunas raramente consultadas
```

## Seleção de Tipo de Índice

| Tipo | Use Para |
| :--- | :--- |
| **B-tree** | Propósito geral, igualdade e intervalo (range) |
| **Hash** | Apenas igualdade, mais rápido |
| **GIN** | JSONB, arrays, texto completo (full-text) |
| **GiST** | Geometria, tipos de intervalo |
| **HNSW/IVFFlat** | Similaridade vetorial (pgvector) |

## Princípios de Índice Composto (Composite Index)

```
A ordem importa para índices compostos:
├── Colunas de igualdade primeiro
├── Colunas de intervalo (range) por último
├── Colunas mais seletivas primeiro
└── Corresponder ao padrão da query
```
