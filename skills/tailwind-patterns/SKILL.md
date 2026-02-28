---
name: tailwind-patterns
description: Princípios do Tailwind CSS v4. Configuração baseada em CSS, container queries, padrões modernos e arquitetura de design tokens.
allowed-tools: Read, Write, Edit, Glob, Grep
---

# Padrões do Tailwind CSS (v4 - 2025)

> CSS utilitário moderno com configuração nativa em CSS.

---

## 1. Arquitetura do Tailwind v4

### O que mudou em relação à v3

| v3 (Legado) | v4 (Atual) |
| :--- | :--- |
| `tailwind.config.js` | Diretiva `@theme` baseada em CSS |
| Plugin PostCSS | Engine Oxide (10x mais rápida) |
| Modo JIT | Nativo, sempre ativo |
| Sistema de plugins | Recursos nativos do CSS |
| Diretiva `@apply` | Ainda funciona, mas desencorajada |

### Conceitos Centrais da v4

| Conceito | Descrição |
| :--- | :--- |
| **CSS-first** | Configuração no CSS, não no JavaScript |
| **Engine Oxide** | Compilador baseado em Rust, muito mais rápido |
| **Nesting Nativo** | Nesting de CSS sem necessidade de PostCSS |
| **Variáveis CSS** | Todos os tokens expostos como variáveis `--*` |

---

## 2. Configuração Baseada em CSS

### Definição de Tema

```css
@theme {
  /* Cores - use nomes semânticos */
  --color-primary: oklch(0.7 0.15 250);
  --color-surface: oklch(0.98 0 0);
  --color-surface-dark: oklch(0.15 0 0);
  
  /* Escala de espaçamento */
  --spacing-xs: 0.25rem;
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;
  --spacing-lg: 2rem;
  
  /* Tipografia */
  --font-sans: 'Inter', system-ui, sans-serif;
  --font-mono: 'JetBrains Mono', monospace;
}
```

### Quando Estender vs Sobrescrever (Override)

| Ação | Quando Usar |
| :--- | :--- |
| **Estender** | Adicionar novos valores junto aos padrões |
| **Sobrescrever** | Substituir a escala padrão inteiramente |
| **Tokens Semânticos** | Nomenclatura específica do projeto (primary (primária), surface (superfície)) |

---

## 3. Container Queries (Nativo na v4)

### Breakpoint vs Container

| Tipo | Responde a |
| :--- | :--- |
| **Breakpoint** (`md:`) | Largura da viewport |
| **Container** (`@container`) | Largura do elemento pai |

### Uso de Container Queries

| Padrão | Classes |
| :--- | :--- |
| Definir container | `@container` no elemento pai |
| Breakpoint de container | `@sm:`, `@md:`, `@lg:` nos elementos filhos |
| Containers nomeados | `@container/card` para especificidade |

### Quando Usar

| Cenário | O que usar |
| :--- | :--- |
| Layouts em nível de página | Breakpoints da viewport |
| Responsividade em nível de componente | Container queries |
| Componentes reutilizáveis | Container queries (independentes de contexto) |

---

## 4. Design Responsivo

### Sistema de Breakpoints

| Prefixo | Largura Mínima | Alvo |
| :--- | :--- | :--- |
| (nenhum) | 0px | Base Mobile-first |
| `sm:` | 640px | Celular grande / tablet pequeno |
| `md:` | 768px | Tablet |
| `lg:` | 1024px | Laptop |
| `xl:` | 1280px | Desktop |
| `2xl:` | 1536px | Desktop grande |

### Princípio Mobile-First

1. Escreva os estilos mobile primeiro (sem prefixo).
2. Adicione sobrescrições para telas maiores com prefixos.
3. Exemplo: `w-full md:w-1/2 lg:w-1/3`

---

## 5. Modo Escuro (Dark Mode)

### Estratégias de Configuração

| Método | Comportamento | Quando Usar |
| :--- | :--- | :--- |
| `class` | A classe `.dark` alterna o tema | Troca manual de tema (switcher) |
| `media` | Segue a preferência do sistema | Sem controle do usuário |
| `selector` | Seletor customizado (v4) | Temas complexos |

### Padrão de Modo Escuro

| Elemento | Claro (Light) | Escuro (Dark) |
| :--- | :--- | :--- |
| Fundo (Background) | `bg-white` | `dark:bg-zinc-900` |
| Texto | `text-zinc-900` | `dark:text-zinc-100` |
| Bordas | `border-zinc-200` | `dark:border-zinc-700` |

---

## 6. Padrões de Layout Modernos

### Padrões de Flexbox

| Padrão | Classes |
| :--- | :--- |
| Centralizar (ambos os eixos) | `flex items-center justify-center` |
| Pilha vertical | `flex flex-col gap-4` |
| Linha horizontal | `flex gap-4` |
| Espaço entre (Space between) | `flex justify-between items-center` |
| Grid com wrap | `flex flex-wrap gap-4` |

### Padrões de Grid

| Padrão | Classes |
| :--- | :--- |
| Auto-fit responsivo | `grid grid-cols-[repeat(auto-fit,minmax(250px,1fr))]` |
| Assimétrico (Bento) | `grid grid-cols-3 grid-rows-2` com spans |
| Layout com sidebar | `grid grid-cols-[auto_1fr]` |

> **Nota:** Prefira layouts assimétricos/Bento em vez de grids simétricos de 3 colunas.

---

## 7. Sistema de Cores Moderno

### OKLCH vs RGB/HSL

| Formato | Vantagem |
| :--- | :--- |
| **OKLCH** | Perceptualmente uniforme, melhor para design |
| **HSL** | Matiz/saturação intuitiva |
| **RGB** | Compatibilidade com legado |

### Arquitetura de Tokens de Cor

| Camada | Exemplo | Propósito |
| :--- | :--- | :--- |
| **Primitivo** | `--blue-500` | Valores de cor brutos |
| **Semântico** | `--color-primary` | Nomenclatura baseada no propósito |
| **Componente** | `--button-bg` | Específico do componente |

---

## 8. Sistema de Tipografia

### Padrão de Font Stack

| Tipo | Recomendado |
| :--- | :--- |
| Sans | `'Inter', 'SF Pro', system-ui, sans-serif` |
| Mono | `'JetBrains Mono', 'Fira Code', monospace` |
| Display | `'Outfit', 'Poppins', sans-serif` |

### Escala de Tipografia

| Classe | Tamanho | Uso |
| :--- | :--- | :--- |
| `text-xs` | 0.75rem | Rótulos, legendas |
| `text-sm` | 0.875rem | Texto secundário |
| `text-base` | 1rem | Texto do corpo |
| `text-lg` | 1.125rem | Texto de destaque (Lead) |
| `text-xl`+ | 1.25rem+ | Títulos |

---

## 9. Animações e Transições

### Animações Integradas

| Classe | Efeito |
| :--- | :--- |
| `animate-spin` | Rotação contínua |
| `animate-ping` | Pulso de atenção |
| `animate-pulse` | Pulso de opacidade sutil |
| `animate-bounce` | Efeito saltitante |

### Padrões de Transição

| Padrão | Classes |
| :--- | :--- |
| Todas as propriedades | `transition-all duration-200` |
| Específico | `transition-colors duration-150` |
| Com easing | `ease-out` ou `ease-in-out` |
| Efeito de hover | `hover:scale-105 transition-transform` |

---

## 10. Extração de Componentes

### Quando Extrair

| Sinal | Ação |
| :--- | :--- |
| Mesmas classes 3+ vezes | Extrair componente |
| Variantes de estado complexas | Extrair componente |
| Elemento do sistema de design | Extrair + Documentar |

### Métodos de Extração

| Método | Quando Usar |
| :--- | :--- |
| **Componente React/Vue** | Dinâmico, requer JS |
| **@apply no CSS** | Estático, sem necessidade de JS |
| **Design tokens** | Valores reutilizáveis |

---

## 11. Anti-Padrões

| NÃO FAÇA | FAÇA |
| :--- | :--- |
| Valores arbitrários em todo lugar | Use a escala do sistema de design |
| `!important` | Corrija a especificidade corretamente |
| Inline `style=` | Use utilitários |
| Duplicar listas longas de classes| Extrair componente |
| Misturar config v3 com v4 | Migre totalmente para CSS-first |
| Usar `@apply` excessivamente | Prefira componentes |

---

## 12. Princípios de Performance

| Princípio | Implementação |
| :--- | :--- |
| **Remover não utilizado (Purge)**| Automático na v4 |
| **Evitar dinamismo** | Sem classes em strings de template |
| **Usar Oxide** | Padrão na v4, 10x mais rápido |
| **Cachear builds** | Cache em CI/CD |

---

> **Lembre-se:** O Tailwind v4 é focado em CSS (CSS-first). Utilize variáveis CSS, container queries e recursos nativos. O arquivo de configuração agora é opcional.
