# Princípios de GraphQL

> Consultas flexíveis para dados complexos e interconectados.

## Quando Usar

```
✅ Boa opção:
├── Dados complexos e interconectados
├── Múltiplas plataformas frontend
├── Clientes que precisam de consultas flexíveis
├── Requisitos de dados em evolução
└── Quando for importante reduzir o over-fetching

❌ Opção ruim:
├── Operações simples de CRUD
├── Pesado em upload de arquivos
├── Quando o caching do HTTP for importante
├── Equipe não familiarizada com GraphQL
```

## Princípios de Design de Schema

```
Princípios:
├── Pense em grafos, não em endpoints
├── Projete para evolução (sem versões)
├── Use "connections" para paginação
├── Seja específico com os tipos (não use um "data" genérico)
└── Lide com nulidade (nullability) com atenção
```

## Considerações de Segurança

```
Proteja-se contra:
├── Ataques de profundidade de query → Defina profundidade máxima
├── Complexidade de query → Calcule o custo
├── Abuso de lote (batching) → Limite o tamanho do lote
├── Introspecção (Introspection) → Desative em produção
```
