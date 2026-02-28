# Teste de Segurança de API

> Princípios para testar a segurança de APIs. OWASP API Top 10, autenticação, teste de autorização.

---

## OWASP API Security Top 10 (2023)

| Vulnerabilidade | Foco do Teste |
| :--- | :--- |
| **API1: BOLA** | Acessar recursos de outros usuários |
| **API2: Broken Auth** | JWT, sessão, credenciais |
| **API3: Property Auth** | Mass assignment, exposição de dados |
| **API4: Consumo de Recurso**| Limite de taxa (Rate limiting), DoS |
| **API5: Function Auth** | Endpoints de admin, bypass de roles |
| **API6: Fluxo de Negócio** | Abuso de lógica, automação |
| **API7: SSRF** | Acesso à rede interna |
| **API8: Má Configuração** | Endpoints de debug, CORS |
| **API9: Inventário** | Shadow APIs, versões antigas |
| **API10: Consumo Inseguro** | Confiança em APIs de terceiros |

---

## Teste de Autenticação

### Teste de JWT

| Verificação | O que testar |
| :--- | :--- |
| Algoritmo | Algoritmo "None", confusão de algoritmo |
| Segredo | Segredos fracos, força bruta |
| Claims | Expiração, emissor (issuer), audiência (audience) |
| Assinatura | Manipulação, injeção de chave |

### Teste de Sessão

| Verificação | O que testar |
| :--- | :--- |
| Geração | Previsibilidade |
| Armazenamento | Segurança no lado do cliente |
| Expiração | Aplicação de timeout |
| Invalidação | Eficácia do logout |

---

## Teste de Autorização

| Tipo de Teste | Abordagem |
| :--- | :--- |
| **Horizontal** | Acessar dados de usuários do mesmo nível |
| **Vertical** | Acessar funções de privilégio superior |
| **Contexto** | Acessar fora do escopo permitido |

### Teste de BOLA/IDOR

1. Identificar IDs de recursos nas requisições.
2. Capturar a requisição com a sessão do usuário A.
3. Re-executar (replay) com a sessão do usuário B.
4. Verificar se houve acesso não autorizado.

---

## Teste de Validação de Entrada

| Tipo de Injeção | Foco do Teste |
| :--- | :--- |
| SQL | Manipulação de query SQL |
| NoSQL | Queries em documentos |
| Comando | Comandos do sistema |
| LDAP | Consultas de diretório |

**Abordagem:** Teste todos os parâmetros, tente coerção de tipo (type coercion), teste os limites (boundaries), verifique as mensagens de erro.

---

## Teste de Limite de Taxa (Rate Limiting)

| Aspecto | Verificação |
| :--- | :--- |
| Existência | Existe algum limite? |
| Bypass | Headers, rotação de IP |
| Escopo | Por usuário, por IP, global |

**Técnicas de bypass:** X-Forwarded-For, diferentes métodos HTTP, variações de maiúsculas/minúsculas, versionamento de API.

---

## Segurança em GraphQL

| Teste | Foco |
| :--- | :--- |
| Introspecção | Divulgação do schema |
| Batching | DoS por query |
| Nesting | DoS baseado em profundidade |
| Autorização | Acesso em nível de campo |

---

## Checklist de Teste de Segurança

**Autenticação:**
- [ ] Testar bypass.
- [ ] Verificar força da credencial.
- [ ] Validar segurança do token.

**Autorização:**
- [ ] Testar BOLA/IDOR.
- [ ] Verificar escalada de privilégio.
- [ ] Validar acesso a funções.

**Entrada:**
- [ ] Testar todos os parâmetros.
- [ ] Verificar injeções.

**Configuração:**
- [ ] Verificar CORS.
- [ ] Validar headers.
- [ ] Testar tratamento de erro.

---

> **Lembre-se:** APIs são a espinha dorsal das aplicações modernas. Teste-as como os atacantes farão.
