---
name: webapp-testing
description: Princípios de teste de aplicações web. E2E, Playwright, estratégias de auditoria profunda.
allowed-tools: Read, Write, Edit, Glob, Grep, Bash
---

# Teste de Aplicações Web

> Descubra e teste tudo. Não deixe nenhuma rota sem teste.

---

## 🔧 Scripts de Runtime

**Execute estes para testes de navegador automatizados:**

| Script | Propósito | Uso |
| :--- | :--- | :--- |
| `scripts/playwright_runner.py` | Teste de navegador básico | `python scripts/playwright_runner.py https://exemplo.com` |
| | Com captura de tela | `python scripts/playwright_runner.py <url> --screenshot` |
| | Verificação de acessibilidade | `python scripts/playwright_runner.py <url> --a11y` |

**Requer:** `pip install playwright && playwright install chromium`

---

## 1. Abordagem de Auditoria Profunda

### Descoberta Primeiro

| Alvo | Como Encontrar |
| :--- | :--- |
| Rotas | Escanear `app/`, `pages/`, arquivos de roteador |
| Endpoints de API | Buscar (grep) por métodos HTTP |
| Componentes | Encontrar diretórios de componentes |
| Funcionalidades | Ler a documentação |

### Teste Sistemático

1. **Mapear** - Listar todas as rotas/APIs.
2. **Escanear** - Verificar se elas respondem.
3. **Testar** - Cobrir os caminhos críticos.

---

## 2. Pirâmide de Testes para Web

```
        /\          E2E (Poucos)
       /  \         Fluxos críticos do usuário
      /----\
     /      \       Integração (Alguns)
    /--------\      API, fluxo de dados
   /          \
  /------------\    Componente (Muitos)
                    Peças individuais da UI
```

---

## 3. Princípios de Teste E2E

### O que Testar

| Prioridade | Testes |
| :--- | :--- |
| 1 | Fluxos de usuário ("happy path") |
| 2 | Fluxos de autenticação |
| 3 | Ações críticas de negócio |
| 4 | Tratamento de erros |

### Melhores Práticas de E2E

| Prática | Por que |
| :--- | :--- |
| Usar `data-testid` | Seletores estáveis |
| Esperar por elementos | Evitar testes instáveis (flaky) |
| Estado limpo | Testes independentes |
| Evitar detalhes de implementação | Testar o comportamento do usuário |

---

## 4. Princípios do Playwright

### Conceitos Centrais

| Conceito | Uso |
| :--- | :--- |
| Page Object Model | Encapsular a lógica da página |
| Fixtures | Configuração de teste reutilizável |
| Assertions | Espera automática integrada (auto-wait) |
| Trace Viewer | Depurar falhas |

### Configuração

| Configuração | Recomendação |
| :--- | :--- |
| Retentativas (Retries) | 2 no CI |
| Rastro (Trace) | `on-first-retry` |
| Capturas de tela | `on-failure` |
| Vídeo | `retain-on-failure` |

---

## 5. Testes Visuais

### Quando Usar

| Cenário | Valor |
| :--- | :--- |
| Sistema de Design | Alto |
| Páginas de Marketing | Alto |
| Biblioteca de Componentes| Médio |
| Conteúdo Dinâmico | Baixo |

### Estratégia

- Capturas de tela de base (baseline).
- Comparar em mudanças.
- Revisar diferenças visuais (diffs).
- Atualizar mudanças intencionais.

---

## 6. Princípios de Teste de API

### Áreas de Cobertura

| Área | Testes |
| :--- | :--- |
| Status codes | 200, 400, 404, 500 |
| Formato da resposta | Corresponde ao schema |
| Mensagens de erro | Amigáveis ao usuário |
| Casos de borda | Vazio, grande, caracteres especiais |

---

## 7. Organização de Testes

### Estrutura de Arquivos

```
tests/
├── e2e/           # Fluxos completos de usuário
├── integration/   # API, dados
├── component/     # Unidades de UI
└── fixtures/      # Dados compartilhados
```

### Convenção de Nomenclatura

| Padrão | Exemplo |
| :--- | :--- |
| Baseado em feature | `login.spec.ts` |
| Descritivo | `usuario-pode-fazer-checkout.spec.ts` |

---

## 8. Integração com CI

### Passos do Pipeline

1. Instalar dependências.
2. Instalar navegadores.
3. Executar testes.
4. Fazer upload de artefatos (traces, screenshots).

### Paralelização

| Estratégia | Uso |
| :--- | :--- |
| Por arquivo | Padrão do Playwright |
| Sharding | Suítes grandes |
| Workers | Múltiplos navegadores |

---

## 9. Anti-Padrões

| ❌ NÃO Faça | ✅ Faça |
| :--- | :--- |
| Testar a implementação | Testar o comportamento |
| Esperas manuais (hardcode)| Use auto-wait |
| Pular a limpeza | Isole os testes |
| Ignorar testes instáveis | Corrija a causa raiz |

---

> **Lembre-se:** Testes E2E são caros. Use-os apenas para caminhos críticos.
