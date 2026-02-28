# Referência do Sistema de Tipografia

> Princípios de tipografia e tomada de decisão — aprenda a pensar, não a memorizar.
> **Não há nomes ou tamanhos de fonte fixos — entenda o sistema.**

---

## 1. Princípios de Escala Modular

### O que é uma Escala Modular?

```
Uma relação matemática entre tamanhos de fonte:
├── Escolha um tamanho BASE (geralmente o texto do corpo)
├── Escolha uma RAZÃO (multiplicador)
└── Gere todos os tamanhos usando: base × razão^n
```

### Razões Comuns e Quando Usar

| Razão | Valor | Sensação | Ideal Para |
| :--- | :--- | :--- | :--- |
| Segunda Menor | 1.067 | Muito sutil | UI densa, telas pequenas |
| Segunda Maior | 1.125 | Sutil | Interfaces compactas |
| Terça Menor | 1.2 | Confortável | Apps mobile, cards |
| Terça Maior | 1.25 | Equilibrada | Web em geral (mais comum) |
| Quarta Perfeita | 1.333 | Perceptível | Editorial, blogs |
| Quinta Perfeita | 1.5 | Dramática | Títulos, marketing |
| Razão Áurea | 1.618 | Impacto máximo | Seções Hero, display |

### Escolhendo o Tamanho Base

| Contexto | Faixa de Tamanho Base | Por que |
| :--- | :--- | :--- |
| Mobile-first | 16-18px | Legibilidade em telas pequenas |
| Desktop app | 14-16px | Densidade de informação |
| Editorial | 18-21px | Conforto para leitura longa |
| Foco em acessibilidade| 18px+ | Mais fácil de ler |

---

## 2. Princípios de Combinação de Fontes (Pairing)

### O que faz as fontes funcionarem juntas

```
Contraste + Harmonia:
├── Diferentes o SUFICIENTE para criar hierarquia
├── Semelhantes o SUFICIENTE para parecerem coesas
└── Geralmente: serif + sans, ou display + neutra
```

### Estratégias de Combinação (Pairing)

| Estratégia | Como | Resultado |
| :--- | :--- | :--- |
| **Contraste** | Título Serif + Corpo Sans | Sensação clássica, editorial |
| **Mesma Família** | Uma fonte variável, diferentes pesos| Coeso, moderno |
| **Mesmo Designer** | Fontes da mesma fundição (foundry)| Proporções frequentemente harmoniosas|
| **Mesma Era** | Fontes do mesmo período histórico | Consistência histórica |

### O que observar

```
Ao combinar, compare:
├── x-height (altura das letras minúsculas)
├── Largura da letra (estreita vs larga)
├── Contraste de traço (variação fino/grosso)
└── Clima geral (formal vs casual)
```

---

## 3. Princípios de Altura de Linha (Line Height)

### A Relação

```
A altura da linha depende de:
├── Tamanho da fonte (texto maior = menos line height necessário)
├── Comprimento da linha (linhas longas = mais line height)
├── Design da fonte (algumas fontes precisam de mais espaço)
└── Tipo de conteúdo (títulos vs corpo)
```

### Diretrizes por Contexto

| Tipo de Conteúdo | Faixa de Line Height | Por que |
| :--- | :--- | :--- |
| **Títulos** | 1.1 - 1.3 | Linhas curtas, deseja-se compacto |
| **Corpo de texto** | 1.4 - 1.6 | Leitura confortável |
| **Conteúdo longo** | 1.6 - 1.8 | Legibilidade máxima |
| **Elementos de UI** | 1.2 - 1.4 | Eficiência de espaço |

---

## 4. Princípios de Comprimento de Linha (Line Length)

### Largura de Leitura Ideal

```
O ponto ideal: 45-75 caracteres por linha
├── < 45: Muito truncado, quebra o fluxo
├── 45-75: Leitura confortável
├── > 75: Cansaço no rastreamento visual
```

---

## 5. Princípios de Tipografia Responsiva

### O Problema

```
Tamanhos fixos não escalam bem:
├── Tamanho desktop fica grande demais no mobile
├── Tamanho mobile fica pequeno demais no desktop
└── Saltos em breakpoints parecem bruscos
```

### Tipografia Fluida (clamp)

```css
/* Sintaxe: clamp(MÍNIMO, PREFERIDO, MÁXIMO) */
font-size: clamp(
  TAMANHO_MINIMO,
  CALCULO_FLUIDO,
  TAMANHO_MAXIMO
);

/* CALCULO_FLUIDO tipicamente: 
   base + unidade relativa à viewport */
```

---

## 6. Princípios de Peso e Ênfase

### Uso Semântico de Pesos (Weights)

| Faixa de Peso | Nome | Use Para |
| :--- | :--- | :--- |
| 300-400 | Light/Normal | Corpo de texto, parágrafos |
| 500 | Medium | Ênfase sutil |
| 600 | Semibold | Subtítulos, labels |
| 700 | Bold | Títulos, ênfase forte |
| 800-900 | Heavy/Black | Display, texto Hero |

---

## 7. Espaçamento de Letras (Tracking)

### Princípios

```
Texto grande (títulos): tracking mais fechado
├── As letras são grandes, os espaços parecem maiores
└── Um leve tracking negativo fica melhor

Texto pequeno (corpo): normal ou ligeiramente mais largo
├── Melhora a legibilidade em tamanhos pequenos
└── Nunca negativo para o texto do corpo

CAIXA ALTA (ALL CAPS): sempre tracking mais largo
├── Letras maiúsculas carecem de ascendentes/descendentes
└── Precisam de mais espaço para parecerem corretas
```

---

## 8. Princípios de Hierarquia

### Hierarquia Visual através da Tipografia

```
Maneiras de criar hierarquia:
├── TAMANHO (mais óbvio)
├── PESO (negrito se destaca)
├── COR (níveis de contraste)
├── ESPAÇAMENTO (margens separam seções)
└── POSIÇÃO (topo = importante)
```

---

## 9. Psicologia da Legibilidade

### Leitura em Padrão F (F-Pattern)

```
Usuários escaneiam em padrão F:
├── Através do topo (primeira linha)
├── Para baixo no lado esquerdo
├── Através novamente (subtítulo)
└── Continua para baixo à esquerda
```

**Implicação**: Informações importantes à esquerda e nos títulos.

---

## 10. Checklist de Seleção de Tipografia

Antes de finalizar a tipografia:

- [ ] **Perguntou as preferências de fonte do usuário?**
- [ ] **Considerou a marca/contexto?**
- [ ] **Selecionou a razão de escala apropriada?**
- [ ] **Limitou-se a 2-3 famílias de fontes?**
- [ ] **Testou a legibilidade em todos os tamanhos?**
- [ ] **Verificou o comprimento da linha (45-75ch)?**
- [ ] **Verificou o contraste para acessibilidade?**
- [ ] **Diferente do seu último projeto?**

### Anti-Padrões

- ❌ Usar as mesmas fontes em cada projeto.
- ❌ Muitas famílias de fontes diferentes.
- ❌ Ignorar a legibilidade em prol do estilo.
- ❌ Tamanhos fixos sem responsividade.
- ❌ Fontes decorativas para o texto do corpo.

---

> **Lembre-se**: Tipografia é sobre clareza de comunicação. Escolha baseada nas necessidades do conteúdo e do público, não em preferência pessoal.
