---
name: nodejs-best-practices
description: Princípios de desenvolvimento em Node.js e tomada de decisão. Seleção de framework, padrões assíncronos, segurança e arquitetura. Ensina a pensar, não a copiar.
allowed-tools: Read, Write, Edit, Glob, Grep
---

# Melhores Práticas de Node.js

> Princípios e tomada de decisão para o desenvolvimento em Node.js em 2025.
> **Aprenda a PENSAR, não a memorizar padrões de código.**

---

## ⚠️ Como Usar Esta Skill

Esta skill ensina **princípios de tomada de decisão**, não código fixo para copiar.

- PERGUNTE ao usuário as preferências quando não estiver claro.
- Escolha o framework/padrão baseado no CONTEXTO.
- Não use a mesma solução para tudo.

---

## 1. Seleção de Framework (2025)

### Árvore de Decisão

```
O que você está construindo?
│
├── Edge/Serverless (Cloudflare, Vercel)
│   └── Hono (zero-dependency, cold starts ultra rápidos)
│
├── API de Alta Performance
│   └── Fastify (2-3x mais rápido que o Express)
│
├── Familiaridade Enterprise/Equipe
│   └── NestJS (estruturado, DI, decoradores)
│
├── Legado/Estável/Ecossistema Máximo
│   └── Express (maduro, maior número de middlewares)
│
└── Full-stack com frontend
    └── API Routes do Next.js ou tRPC
```

### Princípios de Comparação

| Fator | Hono | Fastify | Express |
| :--- | :--- | :--- | :--- |
| **Ideal para** | Edge, serverless | Performance | Legado, aprendizado |
| **Cold start** | Mais rápido | Rápido | Moderado |
| **Ecossistema** | Em crescimento | Bom | O maior |
| **TypeScript** | Nativo | Excelente | Bom |
| **Curva de aprendizado** | Baixa | Média | Baixa |

### Perguntas de Seleção a Fazer:
1. Qual é o alvo da implantação (deployment target)?
2. O tempo de cold start é crítico?
3. A equipe já possui experiência prévia?
4. Existe código legado para manter?

---

## 2. Considerações de Runtime (2025)

### TypeScript Nativo

```
Node.js 22+: --experimental-strip-types
├── Execute arquivos .ts diretamente
├── Sem necessidade de etapa de build para projetos simples
└── Considere para: scripts, APIs simples
```

### Decisão do Sistema de Módulos

```
ESM (import/export)
├── Padrão moderno
├── Melhor tree-shaking
├── Carregamento de módulos assíncrono
└── Use para: novos projetos

CommonJS (require)
├── Compatibilidade com legado
├── Maior suporte de pacotes npm
└── Use para: bases de código existentes, alguns casos de borda
```

### Seleção de Runtime

| Runtime | Ideal Para |
| :--- | :--- |
| **Node.js** | Propósito geral, maior ecossistema |
| **Bun** | Performance, bundler integrado |
| **Deno** | Foco em segurança, TypeScript integrado |

---

## 3. Princípios de Arquitetura

### Conceito de Estrutura em Camadas

```
Fluxo de Requisição:
│
├── Camada de Controle/Rotas (Controller/Route Layer)
│   ├── Lida com especificidades do HTTP
│   ├── Validação de entrada no limite
│   └── Chama a camada de serviço
│
├── Camada de Serviço (Service Layer)
│   ├── Lógica de negócio
│   ├── Agnóstica a framework
│   └── Chama a camada de repositório
│
└── Camada de Repositório (Repository Layer)
    ├── Apenas acesso a dados
    ├── Consultas ao banco de dados
    └── Interações com ORM
```

### Por que isso importa:
- **Testabilidade**: Simule (mock) as camadas de forma independente.
- **Flexibilidade**: Troque o banco de dados sem tocar na lógica de negócio.
- **Clareza**: Cada camada tem uma responsabilidade única.

---

## 4. Princípios de Tratamento de Erros

### Tratamento de Erros Centralizado

```
Padrão:
├── Crie classes de erro customizadas
├── Lance (throw) de qualquer camada
├── Capture no nível superior (middleware)
└── Formate uma resposta consistente
```

### Filosofia de Resposta de Erro

```
O Cliente recebe:
├── Status HTTP apropriado
├── Código de erro para tratamento programático
├── Mensagem amigável para o usuário
└── NENHUM detalhe interno (segurança!)

Os Logs recebem:
├── Stack trace completo
├── Contexto da requisição
├── ID do usuário (se aplicável)
└── Carimbo de data/hora (timestamp)
```

### Seleção de Status Code

| Situação | Status | Quando |
| :--- | :--- | :--- |
| Entrada ruim | 400 | Cliente enviou dados inválidos |
| Sem autenticação | 401 | Credenciais ausentes ou inválidas |
| Sem permissão | 403 | Autenticação válida, mas não permitida |
| Não encontrado | 404 | O recurso não existe |
| Conflito | 409 | Conflito de estado ou duplicidade |
| Validação | 422 | Schema válido, mas regras de negócio falharam |
| Erro do servidor | 500 | Erro nosso, logue tudo |

---

## 5. Princípios de Padrões Assíncronos

### Quando Usar Cada Um

| Padrão | Use Quando |
| :--- | :--- |
| `async/await` | Operações assíncronas sequenciais |
| `Promise.all` | Operações independentes paralelas |
| `Promise.allSettled`| Paralelo onde algumas podem falhar |
| `Promise.race` | Timeout ou a primeira resposta vence |

### Consciência do Event Loop

```
I/O-bound (async ajuda):
├── Consultas ao banco de dados
├── Requisições HTTP
├── Sistema de arquivos
└── Operações de rede

CPU-bound (async não ajuda):
├── Operações de criptografia
├── Processamento de imagem
├── Cálculos complexos
└── → Use worker threads ou delegue o processamento
```

---

## 6. Princípios de Validação

### Valide nos Limites

```
Onde validar:
├── Ponto de entrada da API (body/params da requisição)
├── Antes de operações no banco de dados
├── Dados externos (respostas de API, uploads de arquivos)
└── Variáveis de ambiente (na inicialização)
```

### Seleção de Biblioteca de Validação

| Biblioteca | Ideal Para |
| :--- | :--- |
| **Zod** | Focada em TypeScript, inferência |
| **Valibot** | Bundle menor (tree-shakeable) |
| **ArkType** | Crítico em performance |
| **Yup** | Uso existente com formulários em React |

---

## 7. Princípios de Segurança

### Checklist de Segurança (Princípios)

- [ ] **Validação de entrada**: Todas as entradas validadas.
- [ ] **Consultas parametrizadas**: Sem concatenação de strings para SQL.
- [ ] **Hashing de senha**: bcrypt ou argon2.
- [ ] **Verificação de JWT**: Sempre verifique a assinatura e a expiração.
- [ ] **Rate limiting**: Proteja-se contra abusos.
- [ ] **Headers de segurança**: Helmet.js ou equivalente.
- [ ] **HTTPS**: Em todo lugar em produção.
- [ ] **CORS**: Configurado corretamente.
- [ ] **Segredos**: Apenas em variáveis de ambiente.
- [ ] **Dependências**: Auditadas regularmente.

---

## 8. Princípios de Teste

### Seleção da Estratégia de Teste

| Tipo | Propósito | Ferramentas |
| :--- | :--- | :--- |
| **Unitário** | Lógica de negócio | node:test, Vitest |
| **Integração** | Endpoints de API | Supertest |
| **E2E** | Fluxos completos | Playwright |

---

## 10. Anti-Padrões a Evitar

### ❌ NÃO FAÇA:
- Usar Express para novos projetos no edge (use Hono).
- Usar métodos síncronos em código de produção.
- Colocar lógica de negócio em controllers.
- Pular a validação de entrada.
- Codificar segredos no código (hardcode).
- Confiar em dados externos sem validação.
- Bloquear o event loop com trabalho de CPU pesado.

### ✅ FAÇA:
- Escolha o framework baseado no contexto.
- Pergunte ao usuário por preferências quando não estiver claro.
- Use arquitetura em camadas para projetos que tendem a crescer.
- Valide todas as entradas.
- Use variáveis de ambiente para segredos.
- Faça profiling antes de otimizar.

---

## 11. Checklist de Decisão

Antes de implementar:

- [ ] **Perguntou ao usuário sobre a preferência de stack?**
- [ ] **Escolheu o framework para ESTE contexto?** (não apenas o padrão)
- [ ] **Considerou o alvo de implantação (deployment target)?**
- [ ] **Planejou a estratégia de tratamento de erros?**
- [ ] **Identificou os pontos de validação?**
- [ ] **Considerou os requisitos de segurança?**

---

> **Lembre-se**: Melhores práticas em Node.js são sobre a tomada de decisão, não sobre memorizar padrões. Cada projeto merece uma consideração nova baseada em seus requisitos.
