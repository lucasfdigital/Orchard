# Referência de Padrões Arquiteturais

> Referência rápida para padrões comuns com orientações de uso.

## Padrões de Acesso a Dados (Data Access)

| Padrão | Quando Usar | Quando NÃO Usar | Complexidade |
| :--- | :--- | :--- | :--- |
| **Active Record** | CRUD simples, prototipagem rápida | Consultas complexas, múltiplas fontes | Baixa |
| **Repository** | Necessidade de testes, múltiplas fontes | CRUD simples, banco de dados único | Média |
| **Unit of Work** | Transações complexas | Operações simples | Alta |
| **Data Mapper** | Domínio complexo, performance | CRUD simples, desenvolvimento rápido | Alta |

## Padrões de Lógica de Domínio (Domain Logic)

| Padrão | Quando Usar | Quando NÃO Usar | Complexidade |
| :--- | :--- | :--- | :--- |
| **Transaction Script** | CRUD simples, procedural | Regras de negócio complexas | Baixa |
| **Table Module** | Lógica baseada em registros | Necessidade de comportamento rico | Baixa |
| **Domain Model** | Lógica de negócio complexa | CRUD simples | Média |
| **DDD (Completo)** | Domínio complexo, especialistas de domínio | Domínio simples, sem especialistas | Alta |

## Padrões de Sistemas Distribuídos

| Padrão | Quando Usar | Quando NÃO Usar | Complexidade |
| :--- | :--- | :--- | :--- |
| **Monolito Modular** | Equipes pequenas, limites incertos | Contextos claros, escalas diferentes | Média |
| **Microsserviços** | Escalas diferentes, equipes grandes | Equipes pequenas, domínio simples | Muito Alta |
| **Orientado a Eventos** | Tempo real, acoplamento fraco | Workflows simples, consistência forte | Alta |
| **CQRS** | Desempenho de leitura/escrita diverge | CRUD simples, mesmo modelo | Alta |
| **Saga** | Transações distribuídas | Banco de dados único, ACID simples | Alta |

## Padrões de API

| Padrão | Quando Usar | Quando NÃO Usar | Complexidade |
| :--- | :--- | :--- | :--- |
| **REST** | CRUD padrão, recursos | Tempo real, consultas complexas | Baixa |
| **GraphQL** | Consultas flexíveis, múltiplos clientes| CRUD simples, necessidade de caching | Média |
| **gRPC** | Serviços internos, performance | APIs públicas, clientes de navegador | Média |
| **WebSocket** | Atualizações em tempo real | Requisição/resposta simples | Média |

---

## Princípio da Simplicidade

**"Comece simples, adicione complexidade apenas quando a necessidade for comprovada."**

- Você sempre pode adicionar padrões depois.
- Remover complexidade é MUITO mais difícil do que adicioná-la.
- Na dúvida, escolha a opção mais simples.
