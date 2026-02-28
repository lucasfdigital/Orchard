# Padrões de Autenticação

> Escolha o padrão de autenticação baseado no caso de uso.

## Guia de Seleção

| Padrão | Ideal Para |
| :--- | :--- |
| **JWT** | Stateless (sem estado), microsserviços |
| **Sessão (Session)** | Web tradicional, simples |
| **OAuth 2.0** | Integração com terceiros |
| **API Keys** | Servidor-para-servidor, APIs públicas |
| **Passkey** | Passwordless (sem senha) moderno (2025+) |

## Princípios de JWT

```
Importante:
├── Sempre verifique a assinatura
├── Verifique a expiração
├── Inclua claims mínimas
├── Use expiração curta + refresh tokens
└── Nunca armazene dados sensíveis no JWT
```
