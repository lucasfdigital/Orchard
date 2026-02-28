---
name: testing-patterns
description: Padrões e princípios de teste. Estratégias de testes unitários, de integração e mocking.
allowed-tools: Read, Write, Edit, Glob, Grep, Bash
---

# Padrões de Teste

> Princípios para suítes de teste confiáveis.

---

## 1. Pirâmide de Testes

```
        /\          E2E (Poucos)
       /  \         Fluxos críticos
      /----\
     /      \       Integração (Alguns)
    /--------\      API, consultas ao BD
   /          \
  /------------\    Unitários (Muitos)
                    Funções, classes
```

---

## 2. Padrão AAA

| Passo | Propósito |
| :--- | :--- |
| **Arrange (Organizar)**| Configurar os dados do teste |
| **Act (Agir)** | Executar o código sendo testado |
| **Assert (Afirmar)** | Verificar o resultado |

---

## 3. Seleção do Tipo de Teste

### Quando Usar Cada Um

| Tipo | Ideal Para | Velocidade |
| :--- | :--- | :--- |
| **Unitário** | Funções puras, lógica | Rápido (<50ms) |
| **Integração** | API, BD, serviços | Médio |
| **E2E** | Fluxos críticos do usuário| Lento |

---

## 4. Princípios de Testes Unitários

### Bons Testes Unitários

| Princípio | Significado |
| :--- | :--- |
| Rápido | < 100ms cada |
| Isolado | Sem dependências externas |
| Repetível | Mesmo resultado sempre |
| Auto-verificável | Sem necessidade de verificação manual |
| Oportuno | Escrito junto com o código |

### O que Testar Unitariamente

| Testar | NÃO Testar |
| :--- | :--- |
| Lógica de negócio | Código do framework |
| Casos de borda | Bibliotecas de terceiros |
| Tratamento de erros | Getters simples |

---

## 5. Princípios de Testes de Integração

### O que Testar

| Área | Foco |
| :--- | :--- |
| Endpoints de API | Requisição/Resposta |
| Banco de Dados | Consultas, transações |
| Serviços externos | Contratos |

### Setup/Teardown (Configuração/Limpeza)

| Fase | Ação |
| :--- | :--- |
| Before All (Antes de tudo) | Conectar recursos |
| Before Each (Antes de cada) | Resetar estado |
| After Each (Depois de cada) | Limpar |
| After All (Depois de tudo) | Desconectar |

---

## 6. Princípios de Mocking

### Quando Usar Mock

| Usar Mock | NÃO Usar Mock |
| :--- | :--- |
| APIs externas | O próprio código sendo testado |
| Banco de Dados (unitário) | Dependências simples |
| Tempo/Aleatório | Funções puras |
| Rede | Armazenamentos em memória |

### Tipos de Mock (Dublês de Teste)

| Tipo | Uso |
| :--- | :--- |
| Stub | Retorna valores fixos |
| Spy | Rastreia chamadas |
| Mock | Define expectativas |
| Fake | Implementação simplificada |

---

## 7. Organização de Testes

### Nomenclatura

| Padrão | Exemplo |
| :--- | :--- |
| Should behavior (Deveria) | "should return error when..." |
| When condition (Quando) | "when user not found..." |
| Given-when-then (Dado-quando-então)| "given X, when Y, then Z" |

### Agrupamento

| Nível | Uso |
| :--- | :--- |
| describe | Agrupar testes relacionados |
| it/test | Caso individual |
| beforeEach | Configuração comum |

---

## 8. Dados de Teste

### Estratégias

| Abordagem | Uso |
| :--- | :--- |
| Factories | Gerar dados de teste |
| Fixtures | Conjuntos de dados pré-definidos |
| Builders | Criação fluida de objetos |

### Princípios

- Use dados realistas.
- Aleatorize valores não essenciais (faker).
- Compartilhe fixtures comuns.
- Mantenha os dados minimalistas.

---

## 9. Melhores Práticas

| Prática | Por que |
| :--- | :--- |
| Um assert por teste | Motivo de falha claro |
| Testes independentes | Sem dependência de ordem |
| Testes rápidos | Executar frequentemente |
| Nomes descritivos | Auto-documentados |
| Limpeza (Clean up) | Evitar efeitos colaterais |

---

## 10. Anti-padrões

| ❌ NÃO Faça | ✅ Faça |
| :--- | :--- |
| Testar implementação | Testar comportamento |
| Código de teste duplicado | Use factories |
| Setup de teste complexo | Simplifique ou divida |
| Ignorar testes instáveis (flaky)| Corrija a causa raiz |
| Pular a limpeza | Resete o estado |

---

> **Lembre-se:** Testes são documentação. Se alguém não conseguir entender o que o código faz através dos testes, reescreva-os.
