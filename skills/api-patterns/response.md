# Princípios de Formato de Resposta

> Consistência é a chave - escolha um formato e siga-o.

## Padrões Comuns

```
Escolha um:
├── Padrão Envelope ({ success, data, error })
├── Dados Diretos (apenas retorne o recurso)
└── HAL/JSON:API (hipermídia)
```

## Resposta de Erro

```
Inclua:
├── Código de erro (para tratamento programático)
├── Mensagem do usuário (para exibição)
├── Detalhes (para depuração, erros em nível de campo)
├── Request ID (ID da requisição para suporte)
└── NÃO inclua detalhes internos (segurança!)
```

## Tipos de Paginação

| Tipo | Ideal Para | Trade-offs |
| :--- | :--- | :--- |
| **Offset** | Simples, permite saltos | Performance em datasets grandes |
| **Cursor** | Datasets grandes | Não permite saltar para uma página |
| **Keyset** | Crítico em performance | Requer chave ordenável |

### Perguntas para Seleção

1. Qual é o tamanho do dataset?
2. Os usuários precisam saltar para páginas específicas?
3. Os dados mudam com frequência?
