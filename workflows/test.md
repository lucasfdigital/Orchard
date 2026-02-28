---
description: Comando de geração e execução de testes. Cria e executa testes para o código.
---

# /test - Geração e Execução de Testes

$ARGUMENTS

---

## Propósito

Este comando gera testes, executa testes existentes ou verifica a cobertura de testes.

---

## Subcomandos

```
/test                - Executar todos os testes
/test [arquivo/recurso] - Gerar testes para um alvo específico
/test coverage       - Mostrar relatório de cobertura de testes
/test watch          - Executar testes no modo de observação (watch mode)
```

---

## Comportamento

### Gerar Testes

Ao ser solicitado para testar um arquivo ou funcionalidade:

1. **Analisar o código**
   - Identificar funções e métodos.
   - Encontrar casos de borda (edge cases).
   - Detectar dependências para mockar (simular).

2. **Gerar casos de teste**
   - Testes de caminho feliz (happy path).
   - Casos de erro.
   - Casos de borda.
   - Testes de integração (se necessário).

3. **Escrever testes**
   - Usar o framework de teste do projeto (Jest, Vitest, etc.).
   - Seguir os padrões de teste existentes.
   - Mockar dependências externas.

---

## Formato de Saída

### Para Geração de Teste

```markdown
## 🧪 Testes: [Alvo]

### Plano de Teste
| Caso de Teste | Tipo | Cobertura |
| :--- | :--- | :--- |
| Deve criar usuário | Unidade | Caminho feliz |
| Deve rejeitar e-mail inválido | Unidade | Validação |
| Deve tratar erro de banco de dados | Unidade | Caso de erro |

### Testes Gerados

`tests/[arquivo].test.ts`

[Bloco de código com os testes]

---

Execute com: `npm test`
```

### Para Execução de Teste

```
🧪 Executando testes...

✅ auth.test.ts (5 passaram)
✅ user.test.ts (8 passaram)
❌ order.test.ts (2 passaram, 1 falhou)

Falhou:
  ✗ should calculate total with discount
    Esperado: 90
    Recebido: 100

Total: 15 testes (14 passaram, 1 falhou)
```

---

## Exemplos

```
/test src/services/auth.service.ts
/test user registration flow
/test coverage
/test fix failed tests
```

---

## Padrões de Teste

### Estrutura de Teste Unitário

```typescript
describe('AuthService', () => {
  describe('login', () => {
    it('deve retornar token para credenciais válidas', async () => {
      // Arrange (Organizar)
      const credentials = { email: 'test@test.com', password: 'pass123' };
      
      // Act (Agir)
      const result = await authService.login(credentials);
      
      // Assert (Validar)
      expect(result.token).toBeDefined();
    });

    it('deve lançar erro para senha inválida', async () => {
      // Arrange (Organizar)
      const credentials = { email: 'test@test.com', password: 'wrong' };
      
      // Act (Agir) & Assert (Validar)
      await expect(authService.login(credentials)).rejects.toThrow('Invalid credentials');
    });
  });
});
```

---

## Princípios Chave

- **Teste o comportamento, não a implementação.**
- **Uma asserção por teste** (quando prático).
- **Nomes de teste descritivos.**
- **Padrão Arrange-Act-Assert.**
- **Mockar dependências externas.**
