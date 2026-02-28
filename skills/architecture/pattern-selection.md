# Diretrizes de Seleção de Padrões

> Árvores de decisão para escolha de padrões arquiteturais.

## Árvore de Decisão Principal

```
INÍCIO: Qual é a sua preocupação PRINCIPAL?

┌─ Complexidade de Acesso a Dados?
│  ├─ ALTA (consultas complexas, necessidade de testes)
│  │  → Repository Pattern + Unit of Work
│  │  VALIDAR: A fonte de dados mudará com frequência?
│  │     ├─ SIM → O Repository vale a indireção
│  │     └─ NÃO → Considere o acesso direto via ORM simples
│  └─ BAIXA (CRUD simples, banco de dados único)
│     → ORM diretamente (Prisma, Drizzle)
│     Mais simples = Melhor, Mais Rápido
│
├─ Complexidade de Regras de Negócio?
│  ├─ ALTA (lógica de domínio, regras variam por contexto)
│  │  → Domain-Driven Design (DDD)
│  │  VALIDAR: Você possui especialistas de domínio na equipe?
│  │     ├─ SIM → DDD Completo (Aggregates, Value Objects)
│  │     └─ NÃO → DDD Parcial (entidades ricas, limites claros)
│  └─ BAIXA (principalmente CRUD, validação simples)
│     → Padrão Transaction Script
│     Mais simples = Melhor, Mais Rápido
│
├─ Necessidade de Escalonamento Independente?
│  ├─ SIM (diferentes componentes escalam de formas diferentes)
│  │  → Microsserviços VALEM a complexidade
│  │  REQUISITOS (TODOS devem ser verdadeiros):
│  │    - Limites de domínio claros
│  │    - Equipe > 10 desenvolvedores
│  │    - Diferentes necessidades de escala por serviço
│  │  SE NEM TODOS FOREM ATENDIDOS → Monolito Modular
│  └─ NÃO (tudo escala junto)
│     → Monolito Modular
│     Pode-se extrair serviços depois, quando a necessidade for comprovada
│
└─ Requisitos de Tempo Real?
   ├─ ALTA (atualizações imediatas, sincronia multi-usuário)
   │  → Arquitetura Orientada a Eventos (EDA)
   │  → Fila de Mensagens (RabbitMQ, Redis, Kafka)
   │  VALIDAR: Você consegue lidar com consistência eventual?
   │     ├─ SIM → Orientação a eventos é válida
   │     └─ NÃO → Síncrono com polling
   └─ BAIXA (consistência eventual é aceitável)
      → Síncrono (REST/GraphQL)
      Mais simples = Melhor, Mais Rápido
```

## As 3 Perguntas (Antes de QUALQUER Padrão)

1. **Problema Resolvido**: Qual problema ESPECÍFICO este padrão resolve?
2. **Alternativa Mais Simples**: Existe uma solução mais simples?
3. **Complexidade Adiada**: Podemos adicionar isso DEPOIS quando necessário?

## Sinais de Alerta (Anti-padrões)

| Padrão | Anti-padrão | Alternativa Mais Simples |
| :--- | :--- | :--- |
| Microsserviços | Divisão prematura | Comece com monolito, extraia depois |
| Clean/Hexagonal | Super-abstração | Concreto primeiro, interfaces depois |
| Event Sourcing | Super-engenharia | Log de auditoria (append-only) |
| CQRS | Complexidade desnecessária | Modelo único |
| Repository | YAGNI para CRUD simples | Acesso direto via ORM |
