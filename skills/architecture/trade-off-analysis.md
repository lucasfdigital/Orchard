# Análise de Trade-off & ADR

> Documente cada decisão arquitetural com seus trade-offs.

---

## Estrutura de Decisão (Decision Framework)

Para CADA componente arquitetural, documente:

```markdown
## Registro de Decisão Arquitetural (ADR)

### Contexto
- **Problema**: [Qual problema estamos resolvendo?]
- **Restrições**: [Tamanho da equipe, escala, cronograma, orçamento]

### Opções Consideradas

| Opção | Prós | Contras | Complexidade | Quando é Válida |
| :--- | :--- | :--- | :--- | :--- |
| Opção A | Benefício 1 | Custo 1 | Baixa | [Condições] |
| Opção B | Benefício 2 | Custo 2 | Alta | [Condições] |

### Decisão
**Escolhida**: [Opção B]

### Justificativa (Rationale)
1. [Razão 1 - vinculada às restrições]
2. [Razão 2 - vinculada aos requisitos]

### Trade-offs Aceitos
- [O que estamos abrindo mão]
- [Por que isso é aceitável]

### Consequências
- **Positivas**: [Benefícios que ganhamos]
- **Negativas**: [Custos/riscos que aceitamos]
- **Mitigação**: [Como lidaremos com os pontos negativos]

### Gatilho de Revisão
- [Quando reconsiderar esta decisão]
```

---

## Template de ADR

```markdown
# ADR-[XXX]: [Título da Decisão]

## Status
Proposta | Aceita | Depreciada | Substituída por [ADR-YYY]

## Contexto
[Qual problema? Quais restrições?]

## Decisão
[O que escolhemos - seja específico]

## Justificativa
[Por que - relacione com requisitos e restrições]

## Trade-offs
[Do que estamos abrindo mão - seja honesto]

## Consequências
- **Positivas**: [Benefícios]
- **Negativas**: [Custos]
- **Mitigação**: [Como lidar com os custos]
```

---

## Armazenamento de ADR

```
docs/
└── architecture/
    ├── adr-001-usar-nextjs.md
    ├── adr-002-postgresql-em-vez-de-mongodb.md
    └── adr-003-adotar-padrao-repository.md
```
