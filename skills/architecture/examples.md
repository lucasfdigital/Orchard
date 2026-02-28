# Exemplos de Arquitetura

> Decisões de arquitetura do mundo real por tipo de projeto.

---

## Exemplo 1: MVP de E-commerce (Desenvolvedor Solo)

```yaml
Requisitos:
  - <1000 usuários inicialmente
  - Desenvolvedor solo
  - Rápido para o mercado (8 semanas)
  - Consciente sobre o orçamento

Decisões de Arquitetura:
  Estrutura do App: Monolito (mais simples para solo)
  Framework: Next.js (full-stack, rápido)
  Camada de Dados: Prisma direto (sem super-abstração)
  Autenticação: JWT (mais simples que OAuth)
  Pagamento: Stripe (solução hospedada)
  Banco de Dados: PostgreSQL (ACID para pedidos)

Trade-offs Aceitos:
  - Monolito → Não escala independentemente (a equipe não justifica isso ainda)
  - Sem Repositório → Menos testável (um CRUD simples não precisa disso)
  - JWT → Sem login social inicialmente (pode ser adicionado depois)

Caminho de Migração Futura:
  - Usuários > 10K → Extrair serviço de pagamento
  - Equipe > 3 → Adicionar padrão Repository (Repositório)
  - Login social solicitado → Adicionar OAuth
```

---

## Exemplo 2: Produto SaaS (5-10 Desenvolvedores)

```yaml
Requisitos:
  - 1K-100K usuários
  - 5-10 desenvolvedores
  - Longo prazo (12+ meses)
  - Múltiplos domínios (faturamento, usuários, core)

Decisões de Arquitetura:
  Estrutura do App: Monolito Modular (tamanho de equipe ideal)
  Framework: NestJS (modular por design)
  Camada de Dados: Padrão Repository (testabilidade, flexibilidade)
  Modelo de Domínio: DDD Parcial (entidades ricas)
  Autenticação: OAuth + JWT
  Caching: Redis
  Banco de Dados: PostgreSQL

Trade-offs Aceitos:
  - Monolito Modular → Algum acoplamento de módulos (microsserviços não justificados)
  - DDD Parcial → Sem agregados completos (sem especialistas de domínio)
  - RabbitMQ depois → Síncrono inicial (adicionar quando a necessidade for comprovada)

Caminho de Migração:
  - Equipe > 10 → Considerar microsserviços
  - Conflito de domínios → Extrair contextos delimitados (bounded contexts)
  - Problemas de performance de leitura → Adicionar CQRS
```

---

## Exemplo 3: Enterprise (100K+ Usuários)

```yaml
Requisitos:
  - 100K+ usuários
  - 10+ desenvolvedores
  - Múltiplos domínios de negócio
  - Diferentes necessidades de escalonamento
  - Disponibilidade 24/7

Decisões de Arquitetura:
  Estrutura do App: Microsserviços (escala independente)
  API Gateway: Kong/AWS API GW
  Modelo de Domínio: DDD Completo
  Consistência: Orientada a eventos (eventual OK)
  Barramento de Mensagens: Kafka
  Autenticação: OAuth + SAML (SSO corporativo)
  Banco de Dados: Poliglota (ferramenta certa para cada trabalho)
  CQRS: Serviços selecionados

Requisitos Operacionais:
  - Service mesh (Istio/Linkerd)
  - Rastreamento distribuído (Jaeger/Tempo)
  - Logging centralizado (ELK/Loki)
  - Circuit breakers (Resilience4j)
  - Kubernetes/Helm
```
