# Skills do Orchard

> **Guia para criar e usar Skills no Kit Orchard**

---

## 📋 Visão Geral

Embora os modelos base do Orchard (como o Gemini) sejam poderosos generalistas, eles não conhecem o contexto específico do seu projeto ou os padrões da sua equipe. Carregar cada regra ou ferramenta na janela de contexto do agente leva ao "tool bloat" (excesso de ferramentas), custos mais altos, latência e confusão.

As **Skills do Orchard** resolvem isso através da **Divulgação Progressiva**. Uma Skill é um pacote de conhecimento especializado que permanece dormente até ser necessário. Esta informação é carregada no contexto do agente apenas quando sua solicitação específica corresponde à descrição da skill.

---

## 📁 Estrutura e Escopo

Skills são pacotes baseados em pastas. Você pode definir estes escopos com base nas suas necessidades:

| Escopo | Caminho | Descrição |
| :--- | :--- | :--- |
| **Workspace** | `<workspace-root>/.agent/skills/` | Disponível apenas em um projeto específico |

### Estrutura de Diretório da Skill

```
minha-skill/
├── SKILL.md      # (Obrigatório) Metadados e instruções
├── scripts/      # (Opcional) Scripts Python ou Bash
├── referências/  # (Opcional) Texto, documentação, templates
└── assets/       # (Opcional) Imagens ou logos
```

---

## 🔍 Exemplo 1: Skill de Code Review

Esta é uma skill apenas de instrução; você só precisa criar o arquivo `SKILL.md`.

### Passo 1: Criar o diretório

```bash
mkdir -p .agent/skills/code-review
```

### Passo 2: Criar o SKILL.md

```markdown
---
name: code-review
description: Revisa alterações de código em busca de bugs, problemas de estilo e melhores práticas. Use ao revisar PRs ou verificar a qualidade do código.
---

# Skill de Code Review

Ao revisar o código, siga estes passos:

## Checklist de revisão

1. **Correção**: O código faz o que deveria fazer?
2. **Casos de borda**: As condições de erro são tratadas?
3. **Estilo**: Segue as convenções do projeto?
4. **Performance**: Existem ineficiências óbvias?

## Como fornecer feedback

- Seja específico sobre o que precisa mudar
- Explique o porquê, não apenas o quê
- Sugira alternativas quando possível
```

> **Nota**: O arquivo `SKILL.md` contém metadados (nome, descrição) no topo, seguidos pelas instruções. O agente lerá apenas os metadados e carregará as instruções completas apenas quando necessário.

### Teste-o

Crie um arquivo `demo_bad_code.py`:

```python
import time

def get_user_data(users, id):
    # Encontrar usuário por ID
    for u in users:
        if u['id'] == id:
            return u
    return None

def process_payments(items):
    total = 0
    for i in items:
        # Calcular imposto
        tax = i['price'] * 0.1
        total = total + i['price'] + tax
        time.sleep(0.1)  # Simular chamada de rede lenta
    return total

def run_batch():
    users = [{'id': 1, 'name': 'Alice'}, {'id': 2, 'name': 'Bob'}]
    items = [{'price': 10}, {'price': 20}, {'price': 100}]

    u = get_user_data(users, 3)
    print("Usuário encontrado: " + u['name'])  # Vai quebrar se for None

    print("Total: " + str(process_payments(items)))

if __name__ == "__main__":
    run_batch()
```

**Prompt**: `revise o arquivo @demo_bad_code.py`

O Agente identificará automaticamente a skill `code-review`, carregará as informações e seguirá as instruções.

---

## 📄 Exemplo 2: Skill de Header de Licença

Esta skill usa um arquivo de referência no diretório `resources/` (ou `referências/`).

### Passo 1: Criar o diretório

```bash
mkdir -p .agent/skills/license-header-adder/resources
```

### Passo 2: Criar o arquivo de template

**`.agent/skills/license-header-adder/resources/HEADER.txt`**:

```
/*
 * Copyright (c) 2026 YOUR_COMPANY_NAME LLC.
 * Todos os direitos reservados.
 * Este código é proprietário e confidencial.
 */
```

### Passo 3: Criar o SKILL.md

**`.agent/skills/license-header-adder/SKILL.md`**:

```markdown
---
name: license-header-adder
description: Adiciona o cabeçalho de licença corporativa padrão a novos arquivos fonte.
---

# Adicionador de Header de Licença

Esta skill garante que todos os novos arquivos fonte tenham o cabeçalho de copyright correto.

## Instruções

1. **Ler o Template**: Ler o conteúdo de `resources/HEADER.txt`.
2. **Aplicar ao Arquivo**: Ao criar um novo arquivo, insira este conteúdo exato no início.
3. **Adaptar Sintaxe**:
   - Para linguagens estilo C (Java, TS), mantenha o bloco `/* */`.
   - Para Python/Shell, converta para comentários `#`.
```

### Teste-o

**Prompt**: `Crie um novo script Python chamado data_processor.py que imprima 'Olá Mundo'.`

O Agente lerá o template, converterá os comentários para o estilo Python e o adicionará automaticamente ao topo do arquivo.

---

## 🎯 Conclusão

Ao criar Skills, você transforma um modelo de IA geral em um especialista para o seu projeto:

- ✅ Sistematize as melhores práticas
- ✅ Adira às regras de revisão de código
- ✅ Adicione cabeçalhos de licença automaticamente
- ✅ O Agente sabe automaticamente como trabalhar com sua equipe

Em vez de lembrar constantemente a IA para "lembrar de adicionar a licença" ou "corrigir o formato do commit", agora o Agente fará isso automaticamente!
