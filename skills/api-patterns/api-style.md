# Seleção de Estilo de API (2025)

> REST vs GraphQL vs tRPC - Qual utilizar em cada situação?

## Árvore de Decisão

```
Quem são os consumidores da API?
│
├── API Pública / Múltiplas plataformas
│   └── REST + OpenAPI (maior compatibilidade)
│
├── Necessidades de dados complexas / Múltiplos frontends
│   └── GraphQL (consultas flexíveis)
│
├── Frontend e Backend em TypeScript (monorepo)
│   └── tRPC (segurança de tipos ponta a ponta)
│
├── Tempo Real / Orientado a Eventos
│   └── WebSocket + AsyncAPI
│
└── Microsserviços Internos
    └── gRPC (performance) ou REST (simplicidade)
```

## Comparação

| Fator | REST | GraphQL | tRPC |
| :--- | :--- | :--- | :--- |
| **Ideal para** | APIs Públicas | Apps Complexos | Monorepos TS |
| **Curva de aprendizado** | Baixa | Média | Baixa (se for TS) |
| **Over/Under fetching** | Comum | Resolvido | Resolvido |
| **Segurança de tipos** | Manual (OpenAPI) | Baseada em Schema | Automática |
| **Caching** | Nativo do HTTP | Complexo | Baseado no Cliente |

## Perguntas para Seleção

1. Quem são os consumidores da API?
2. O frontend é em TypeScript?
3. Quão complexas são as relações entre os dados?
4. O caching é crítico?
5. API pública ou interna?
