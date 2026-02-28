# Princípios de REST

> Design de API baseado em recursos - substantivos, não verbos.

## Regras de Nomenclatura de Recursos

```
Princípios:
├── Use SUBSTANTIVOS, não verbos (recursos, não ações)
├── Use formas no PLURAL (/users em vez de /user)
├── Use letras minúsculas com hifens (/user-profiles)
├── Use aninhamento para relacionamentos (/users/123/posts)
└── Mantenha-o raso (máximo de 3 níveis de profundidade)
```

## Seleção de Métodos HTTP

| Método | Propósito | Idempotente? | Com Body? |
| :--- | :--- | :--- | :--- |
| **GET** | Ler recurso(s) | Sim | Não |
| **POST** | Criar novo recurso | Não | Sim |
| **PUT** | Substituir o recurso inteiro | Sim | Sim |
| **PATCH** | Atualização parcial | Não | Sim |
| **DELETE** | Remover recurso | Sim | Não |

## Seleção de Status Code

| Situação | Código | Por que |
| :--- | :--- | :--- |
| Sucesso (leitura) | 200 | Sucesso padrão |
| Criado | 201 | Novo recurso criado |
| Sem conteúdo | 204 | Sucesso, nada a retornar |
| Bad request | 400 | Requisição malformada |
| não autorizado | 401 | Autenticação ausente/inválida |
| Proibido | 403 | Autenticação válida, sem permissão |
| Não encontrado | 404 | O recurso não existe |
| Conflito | 409 | Conflito de estado (duplicado) |
| Erro de validação | 422 | Sintaxe válida, dados inválidos |
| Limite de taxa | 429 | Muitas requisições |
| Erro do servidor | 500 | Erro nosso |
