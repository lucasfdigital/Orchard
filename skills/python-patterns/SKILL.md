---
name: python-patterns
description: Princípios de desenvolvimento em Python e tomada de decisão. Seleção de framework, padrões assíncronos, type hints, estrutura do projeto. Ensina a pensar, não a copiar.
allowed-tools: Read, Write, Edit, Glob, Grep
---

# Padrões de Python

> Princípios de desenvolvimento e tomada de decisão em Python para 2025.
> **Aprenda a PENSAR, não a memorizar padrões.**

---

## ⚠️ Como Usar Esta Skill

Esta skill ensina **princípios de tomada de decisão**, não código fixo para copiar.

- PERGUNTE ao usuário a preferência de framework quando não estiver claro.
- Escolha async vs sync baseado no CONTEXTO.
- Não use o mesmo framework para tudo por padrão.

---

## 1. Seleção de Framework (2025)

### Árvore de Decisão

```
O que você está construindo?
│
├── API-first / Microsserviços
│   └── FastAPI (async, moderno, rápido)
│
├── Web Full-stack / CMS / Admin
│   └── Django (batteries-included - "pilhas incluídas")
│
├── Simples / Script / Aprendizado
│   └── Flask (mínimo, flexível)
│
├── Servir APIs de IA/ML
│   └── FastAPI (Pydantic, async, uvicorn)
│
└── Workers de segundo plano (Background workers)
    └── Celery + qualquer framework
```

### Princípios de Comparação

| Fator | FastAPI | Django | Flask |
| :--- | :--- | :--- | :--- |
| **Ideal para** | APIs, microsserviços | Full-stack, CMS | Simples, aprendizado |
| **Async** | Nativo | Django 5.0+ | Via extensões |
| **Admin** | Manual | Integrado | Via extensões |
| **ORM** | Escolha o seu | Django ORM | Escolha o seu |
| **Curva de aprendizado** | Baixa | Média | Baixa |

### Perguntas de Seleção a Fazer:
1. É apenas uma API ou é full-stack?
2. Precisa de interface administrativa?
3. A equipe está familiarizada com async?
4. Existe infraestrutura já estabelecida?

---

## 2. Decisão Async vs Sync

### Quando usar Async

```
async def é melhor quando:
├── Operações vinculadas a I/O (I/O-bound: banco de dados, HTTP, arquivos)
├── Muitas conexões simultâneas
├── Funcionalidades em tempo real
├── Comunicação entre microsserviços
└── FastAPI/Starlette/Django ASGI
```

### Quando usar Sync

```
def (sync) é melhor quando:
├── Operações vinculadas a CPU (CPU-bound)
├── Scripts simples
├── Base de código legada
├── Equipe não familiarizada com async
└── Bibliotecas bloqueantes (sem versão async)
```

### A Regra de Ouro

```
I/O-bound → async (esperando por algo externo)
CPU-bound → sync + multiprocessing (processamento pesado)

Não:
├── Misture sync e async sem cuidado
├── Use bibliotecas sync em código async
└── Force async para trabalho de CPU
```

---

## 3. Estratégia de Type Hints

### Quando Tipar

```
Sempre tipe:
├── Parâmetros de função
├── Tipos de retorno
├── Atributos de classe
├── APIs públicas

Pode pular:
├── Variáveis locais (deixe a inferência trabalhar)
├── Scripts de uso único
├── Testes (geralmente)
```

### Pydantic para Validação

```
Quando usar Pydantic:
├── Modelos de requisição/resposta de API
├── Configurações/settings
├── Validação de dados
├── Serialização

Benefícios:
├── Validação em tempo de execução (runtime)
├── Schema JSON gerado automaticamente
├── Integração nativa com FastAPI
└── Mensagens de erro claras
```

---

## 4. Princípios de Estrutura de Projeto

### Seleção de Estrutura

```
Projeto Pequeno / Script:
├── main.py
├── utils.py
└── requirements.txt

API Média:
├── app/
│   ├── __init__.py
│   ├── main.py
│   ├── models/
│   ├── routes/
│   ├── services/
│   └── schemas/
├── tests/
└── pyproject.toml

Aplicação Grande:
├── src/
│   └── myapp/
│       ├── core/
│       ├── api/
│       ├── services/
│       ├── models/
│       └── ...
├── tests/
└── pyproject.toml
```

---

## 5. Princípios de Django (2025)

### Django Async (Django 5.0+)

```
O Django suporta async em:
├── Views assíncronas
├── Middleware assíncrono
├── ORM assíncrono (limitado)
└── Implantação ASGI

Quando usar async no Django:
├── Chamadas de API externas
├── WebSocket (Channels)
├── Views de alta concorrência
├── Disparo de tarefas em segundo plano
```

### Melhores Práticas de Django

```
Design de Model:
├── Models gordos, views magras ("Fat models, thin views")
├── Use managers para consultas comuns
├── Classes base abstratas para campos compartilhados

Views:
├── Baseadas em classe (CBV) para CRUD complexo
├── Baseadas em função (FBV) para endpoints simples
├── Use viewsets com o Django REST Framework (DRF)

Consultas (Queries):
├── select_related() para Chaves Estrangeiras (FKs)
├── prefetch_related() para Muitos-para-Muitos (M2M)
├── Evite consultas N+1
└── Use .only() para campos específicos
```

---

## 6. Princípios de FastAPI

### async def vs def no FastAPI

```
Use async def quando:
├── Estiver usando drivers de banco de dados async
├── Fizer chamadas HTTP assíncronas
├── Operações vinculadas a I/O
├── Quiser lidar com concorrência

Use def quando:
├── Operações forem bloqueantes
├── Drivers de banco de dados forem sync
├── Trabalho vinculado a CPU
└── O FastAPI rodará no threadpool automaticamente
```

### Injeção de Dependência

```
Use dependências para:
├── Sessões de banco de dados
├── Usuário atual / Autenticação
├── Configuração
├── Recursos compartilhados

Benefícios:
├── Testabilidade (facilita o mock de dependências)
├── Separação clara de responsabilidades
├── Limpeza automática (yield)
```

---

## 7. Tarefas em Segundo Plano (Background Tasks)

### Guia de Seleção

| Solução | Ideal Para |
| :--- | :--- |
| **BackgroundTasks** | Tarefas simples, dentro do mesmo processo |
| **Celery** | Workflows complexos e distribuídos |
| **ARQ** | Async, baseado em Redis |
| **RQ** | Fila Redis simples |
| **Dramatiq** | Baseado em atores, mais simples que o Celery |

### Quando Usar Cada Um

```
BackgroundTasks (FastAPI):
├── Operações rápidas
├── Sem necessidade de persistência
├── Disparar e esquecer (fire-and-forget)
└── Mesmo processo

Celery/ARQ:
├── Tarefas de longa duração
├── Necessidade de lógica de repetição (retry)
├── Workers distribuídos
├── Fila persistente
└── Workflows complexos
```

---

## 8. Princípios de Tratamento de Erros

### Estratégia de Exceção

```
No FastAPI:
├── Crie classes de exceção customizadas
├── Registre handlers de exceção
├── Retorne um formato de erro consistente
└── Logue sem expor detalhes internos

Padrão:
├── Lance exceções de domínio nos services
├── Capture e transforme nos handlers
└── O cliente recebe uma resposta de erro limpa
```

---

## 9. Princípios de Teste

### Estratégia de Teste

| Tipo | Propósito | Ferramentas |
| :--- | :--- | :--- |
| **Unitário** | Lógica de negócio | pytest |
| **Integração** | Endpoints de API | pytest + httpx/TestClient |
| **E2E** | Workflows completos | pytest + Banco de Dados |

### Testes Assíncronos

```python
# Use pytest-asyncio para testes assíncronos

import pytest
from httpx import AsyncClient

@pytest.mark.asyncio
async def test_endpoint():
    async with AsyncClient(app=app, base_url="http://test") as client:
        response = await client.get("/users")
        assert response.status_code == 200
```

---

## 10. Checklist de Decisão

Antes de implementar:

- [ ] **Perguntou ao usuário sobre a preferência de framework?**
- [ ] **Escolheu o framework para ESTE contexto?** (não apenas o padrão)
- [ ] **Decidiu entre async vs sync?**
- [ ] **Planejou a estratégia de type hints?**
- [ ] **Definiu a estrutura do projeto?**
- [ ] **Planejou o tratamento de erros?**
- [ ] **Considerou tarefas em segundo plano?**

---

## 11. Anti-Padrões a Evitar

### ❌ NÃO FAÇA:
- Usar Django por padrão para APIs simples (FastAPI pode ser melhor).
- Usar bibliotecas sync em código async.
- Pular type hints em APIs públicas.
- Colocar lógica de negócio em rotas/views.
- Ignorar consultas N+1.
- Misturar async e sync sem critério.

### ✅ FAÇA:
- Escolha o framework baseado no contexto.
- Pergunte sobre requisitos assíncronos.
- Use Pydantic para validação.
- Separe as responsabilidades (routes → services → repos).
- Teste os caminhos críticos.

---

> **Lembre-se**: Padrões de Python são sobre a tomada de decisão para o SEU contexto específico. Não copie código — pense no que serve melhor para a sua aplicação.
