# Descoberta de Contexto

> Antes de sugerir qualquer arquitetura, reúna o contexto.

## Hierarquia de Perguntas (Pergunte ao usuário PRIMEIRO)

1. **Escala**
   - Quantos usuários? (10, 1K, 100K, 1M+)
   - Volume de dados? (MB, GB, TB)
   - Taxa de transação? (por segundo/minuto)

2. **Equipe**
   - Desenvolvedor solo ou equipe?
   - Tamanho da equipe e especialidade?
   - Distribuída ou local?

3. **Cronograma**
   - MVP/Protótipo ou produto de longo prazo?
   - Pressão pelo tempo de lançamento (time to market)?

4. **Domínio**
   - Pesado em CRUD ou lógica de negócio complexa?
   - Requisitos de tempo real?
   - Conformidade (Compliance)/regulamentações?

5. **Restrições**
   - Limitações de orçamento?
   - Sistemas legados para integrar?
   - Preferências de stack tecnológica?

## Matriz de Classificação de Projeto

```
                    MVP              SaaS           Enterprise
┌─────────────────────────────────────────────────────────────┐
│ Escala       │ <1K           │ 1K-100K      │ 100K+        │
│ Equipe       │ Solo          │ 2-10         │ 10+          │
│ Cronograma   │ Rápido (semanas)│ Médio (meses)│ Longo (anos) │
│ Arquitetura  │ Simples       │ Modular      │ Distribuída  │
│ Padrões      │ Mínimo        │ Seletivo     │ Abrangente   │
│ Exemplo      │ Next.js API   │ NestJS       │ Microsserviços│
└─────────────────────────────────────────────────────────────┘
```
