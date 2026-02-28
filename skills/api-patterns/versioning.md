# Estratégias de Versionamento

> Planeje a evolução da API desde o primeiro dia.

## Fatores de Decisão

| Estratégia | Implementação | Trade-offs |
| :--- | :--- | :--- |
| **URI** | /v1/users | Claro, fácil para caching |
| **Header** | Accept-Version: 1 | URLs mais limpas, descoberta difícil |
| **Query** | ?version=1 | Fácil de adicionar, desorganizado |
| **Nenhuma** | Evoluir com cuidado | Melhor para interna, arriscado para pública |

## Filosofia de Versionamento

```
Considere:
├── API pública? → Versão na URI
├── Apenas interna? → Pode não precisar de versionamento
├── GraphQL? → Tipicamente sem versões (evolua o schema)
├── tRPC? → Os tipos garantem a compatibilidade
```
