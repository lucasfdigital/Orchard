---
name: powershell-windows
description: Padrões de PowerShell no Windows. Armadilhas críticas, sintaxe de operadores, tratamento de erros.
allowed-tools: Read, Write, Edit, Glob, Grep, Bash
---

# Padrões de PowerShell no Windows

> Padrões críticos e armadilhas para o PowerShell no Windows.

---

## 1. Regras de Sintaxe de Operadores

### CRÍTICO: Parênteses Obrigatórios

| ❌ Errado | ✅ Correto |
| :--- | :--- |
| `if (Test-Path "a" -or Test-Path "b")` | `if ((Test-Path "a") -or (Test-Path "b"))` |
| `if (Get-Item $x -and $y -eq 5)` | `if ((Get-Item $x) -and ($y -eq 5))` |

**Regra:** Cada chamada de cmdlet DEVE estar entre parênteses ao usar operadores lógicos.

---

## 2. Restrição de Unicode/Emoji

### CRÍTICO: Não use Unicode em Scripts

| Propósito | ❌ NÃO Use | ✅ Use |
| :--- | :--- | :--- |
| Sucesso | ✅ ✓ | [OK] [+] |
| Erro | ❌ ✗ 🔴 | [!] [X] |
| Aviso | ⚠️ 🟡 | [*] [WARN] |
| Info | ℹ️ 🔵 | [i] [INFO] |
| Progresso | ⏳ | [...] |

**Regra:** Use apenas caracteres ASCII em scripts PowerShell.

---

## 3. Padrões de Verificação de Nulo

### Sempre verifique antes de acessar

| ❌ Errado | ✅ Correto |
| :--- | :--- |
| `$array.Count -gt 0` | `$array -and $array.Count -gt 0` |
| `$text.Length` | `if ($text) { $text.Length }` |

---

## 4. Interpolação de String

### Expressões Complexas

| ❌ Errado | ✅ Correto |
| :--- | :--- |
| `"Value: $($obj.prop.sub)"` | Armazene em uma variável primeiro |

**Padrão:**
```powershell
$value = $obj.prop.sub
Write-Output "Value: $value"
```

---

## 5. Tratamento de Erros

### ErrorActionPreference

| Valor | Uso |
| :--- | :--- |
| Stop | Desenvolvimento (falha rápida) |
| Continue | Scripts de produção |
| SilentlyContinue | Quando erros são esperados |

### Padrão Try/Catch

- Não use `return` dentro do bloco `try`.
- Use `finally` para limpeza (cleanup).
- Retorne após o `try/catch`.

---

## 6. Caminhos de Arquivo (File Paths)

### Regras de Caminhos no Windows

| Padrão | Uso |
| :--- | :--- |
| Caminho literal | `C:\Users\User\file.txt` |
| Caminho de variável | `Join-Path $env:USERPROFILE "file.txt"` |
| Caminho relativo | `Join-Path $ScriptDir "data"` |

**Regra:** Use `Join-Path` para segurança entre plataformas.

---

## 7. Operações com Array

### Padrões Corretos

| Operação | Sintaxe |
| :--- | :--- |
| Array vazio | `$array = @()` |
| Adicionar item | `$array += $item` |
| ArrayList add | `$list.Add($item) | Out-Null` |

---

## 8. Operações com JSON

### CRÍTICO: Parâmetro de Profundidade (Depth)

| ❌ Errado | ✅ Correto |
| :--- | :--- |
| `ConvertTo-Json` | `ConvertTo-Json -Depth 10` |

**Regra:** Sempre especifique o `-Depth` para objetos aninhados.

### Operações de Arquivo

| Operação | Padrão |
| :--- | :--- |
| Leitura | `Get-Content "file.json" -Raw | ConvertFrom-Json` |
| Escrita | `$data | ConvertTo-Json -Depth 10 | Out-File "file.json" -Encoding UTF8` |

---

## 9. Erros Comuns

| Mensagem de Erro | Causa | Correção |
| :--- | :--- | :--- |
| "parameter 'or'" | Falta de parênteses | Envolva os cmdlets em () |
| "Unexpected token" | Caractere Unicode | Use apenas ASCII |
| "Cannot find property" | Objeto nulo | Verifique se é nulo primeiro |
| "Cannot convert" | Incompatibilidade de tipo | Use .ToString() |

---

## 10. Template de Script

```powershell
# Modo estrito
Set-StrictMode -Version Latest
$ErrorActionPreference = "Continue"

# Caminhos
$ScriptDir = Split-Path -Parent $MyInvocation.MyCommand.Path

# Principal
try {
    # Lógica aqui
    Write-Output "[OK] Pronto"
    exit 0
}
catch {
    Write-Warning "Erro: $_"
    exit 1
}
```

---

> **Lembre-se:** O PowerShell possui regras de sintaxe únicas. Parênteses, uso apenas de ASCII e verificações de nulo não são negociáveis.
