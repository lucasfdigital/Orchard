# Princípios de Limite de Taxa (Rate Limiting)

> Proteja sua API contra abusos e sobrecarga.

## Por que limitar a taxa?

```
Proteja-se contra:
├── Ataques de força bruta (Brute force)
├── Exaustão de recursos
├── Custos excessivos (se for pago por uso)
└── Uso injusto (monopolização)
```

## Seleção de Estratégia

| Tipo | Como | Quando |
| :--- | :--- | :--- |
| **Token bucket** | Permite picos, recarrega com o tempo | Maioria das APIs |
| **Sliding window** | Distribuição suave | Limites rigorosos |
| **Fixed window** | Contadores simples por janela | Necessidades básicas |

## Headers de Resposta

```
Inclua nos headers:
├── X-RateLimit-Limit (máximo de requisições)
├── X-RateLimit-Remaining (requisições restantes)
├── X-RateLimit-Reset (quando o limite reseta)
└── Retorne 429 quando o limite for excedido
```
