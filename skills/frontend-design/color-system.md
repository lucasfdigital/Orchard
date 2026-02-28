# Referência do Sistema de Cores

> Princípios da teoria das cores, processo de seleção e diretrizes para tomada de decisão.
> **Não use códigos hexadecimais decorados — aprenda a PENSAR na cor.**

---

## 1. Fundamentos da Teoria das Cores

### O Círculo Cromático (Color Wheel)

```
                    AMARELO
                       │
           Amarelo-    │    Amarelo-
            Verde      │    Laranja
               ╲       │       ╱
                ╲      │      ╱
     VERDE ──────────── ● ──────────── LARANJA
                ╱      │      ╲
               ╱       │       ╲
             Azul-     │     Vermelho-
             Verde     │     Laranja
                       │
                    VERMELHO
                       │
                      ROXO
                    ╱       ╲
               Azul-         Vermelho-
               Roxo          Roxo
                    ╲       ╱
                      AZUL
```

### Relações de Cores

| Esquema | Como Criar | Quando Usar |
| :--- | :--- | :--- |
| **Monocromático** | Escolha UM matiz, varie apenas brilho/saturação | Minimalista, profissional, coeso |
| **Análogo** | Escolha 2-3 matizes ADJACENTES no círculo | Harmonioso, calmo, inspirado na natureza|
| **Complementar** | Escolha matizes OPOSTOS no círculo | Alto contraste, vibrante, atenção |
| **Complementar Dividido**| Base + 2 cores adjacentes à complementar | Dinâmico, porém equilibrado |
| **Triádico** | 3 matizes EQUIDISTANTES no círculo | Vibrante, lúdico, criativo |

### Como Escolher um Esquema:
1. **Qual é o clima (mood) do projeto?** Calmo → Análogo. Ousado → Complementar.
2. **Quantas cores são necessárias?** Mínimo → Monocromático. Complexo → Triádico.
3. **Quem é o público?** Conservador → Monocromático. Jovem → Triádico.

---

## 2. A Regra 60-30-10

### Princípio de Distribuição
```
┌─────────────────────────────────────────────────┐
│                                                 │
│     60% PRIMÁRIA (Fundo, áreas grandes)         │
│     → Deve ser neutra ou calmante               │
│     → Carrega o tom geral                       │
│                                                 │
├────────────────────────────────────┬────────────┤
│                                    │            │
│   30% SECUNDÁRIA                   │ 10% ACENTO │
│   (Cards, seções, headers)         │ (CTAs,     │
│   → Suporta sem dominar            │ destaques) │
│                                    │ → Atrai a  │
│                                    │   atenção  │
└────────────────────────────────────┴────────────┘
```

### Padrão de Implementação
```css
:root {
  /* 60% - Escolha baseada no modo claro/escuro e no clima (mood) */
  --color-bg: /* neutra: branco, off-white ou cinza escuro */
  --color-surface: /* ligeiramente diferente do fundo (bg) */
  
  /* 30% - Escolha baseada na marca ou contexto */
  --color-secondary: /* versão atenuada (muted) da primária ou neutra */
  
  /* 10% - Escolha baseada na ação/emoção desejada */
  --color-accent: /* vibrante, atrai a atenção (acento/destaque) */
}
```

---

## 3. Psicologia das Cores - Significado e Seleção

### Como Escolher Baseado no Contexto

| Se o Projeto é... | Considere Estes Matizes | Por que |
| :--- | :--- | :--- |
| **Finanças, Tech, Saúde** | Azuis, Teals | Confiança, estabilidade, calma |
| **Eco, Bem-estar, Natureza** | Verdes, Tons Terrosos | Crescimento, saúde, orgânico |
| **Comida, Energia, Jovem** | Laranja, Amarelo, Quentes| Apetite, excitação, calor |
| **Luxo, Beleza, Criativo** | Deep Teal, Dourado, Preto | Sofisticação, premium |
| **Urgência, Vendas, Alertas** | Vermelho, Laranja | Ação, atenção, paixão |

### Associações Emocionais (Para Tomada de Decisão)

| Família de Matiz | Associações Positivas | Cuidados |
| :--- | :--- | :--- |
| **Azul** | Confiança, calma, profissional | Pode parecer frio, corporativo |
| **Verde** | Crescimento, natureza, sucesso | Pode parecer chato se usado em excesso |
| **Vermelho** | Paixão, urgência, energia | Alta excitação, use com moderação |
| **Laranja** | Calor, amigável, criativo | Pode parecer barato se muito saturado |
| **Roxo** | ⚠️ **PROIBIDO** - IAs usam demais! | Use Deep Teal/Marrom/Esmeralda em vez |
| **Amarelo** | Otimismo, atenção, feliz | Difícil de ler, use como destaque (accent)|
| **Preto** | Elegância, poder, moderno | Pode parecer pesado |
| **Branco** | Limpo, minimalista, aberto | Pode parecer estéril |

---

## 4. Princípios de Geração de Paletas

### A partir de uma Cor Única (Método HSL)

Em vez de memorizar códigos hex, aprenda a **manipular o HSL**:

```
HSL = Hue (Matiz), Saturation (Saturação), Lightness (Brilho)

Hue (0-360): A família da cor
  0/360 = Vermelho
  60 = Amarelo
  120 = Verde
  180 = Ciano
  240 = Azul
  300 = Roxo

Saturação (0-100%): Intensidade da cor
  Baixa = Atenuada (muted), sofisticada
  Alta = Vibrante, energética

Brilho (0-100%): Claridade
  0% = Preto
  50% = Cor pura
  100% = Branco
```

### Gerando uma Paleta Completa

Dada QUALQUER cor base, crie uma escala:

```
Escala de Brilho (Lightness):
  50  (mais clara) → L: 97%
  100              → L: 94%
  200              → L: 86%
  300              → L: 74%
  400              → L: 66%
  500 (base)       → L: 50-60%
  600              → L: 48%
  700              → L: 38%
  800              → L: 30%
  900 (mais escura) → L: 20%
```

---

## 5. Guia de Seleção Baseada no Contexto

### Em vez de copiar paletas, siga este processo:

**Passo 1: Identificar o Contexto**
```
Qual tipo de projeto?
├── E-commerce → Precisa de equilíbrio entre confiança + urgência
├── SaaS/Dashboard → Necessita de baixa fadiga visual, foco em dados
├── Saúde/Bem-estar → Necessita de sensação calma e natural
├── Luxo/Premium → Precisa de elegância discreta
├── Criativo/Portfólio → Precisa de personalidade, ser memorável
└── Outro → PERGUNTE ao usuário
```

**Passo 2: Selecionar a Família de Matiz Primária**
```
Baseado no contexto, escolha UMA:
- Família Azul (confiança)
- Família Verde (crescimento)
- Família Quente (energia)
- Família Neutra (elegança)
- OU pergunte a preferência do usuário
```

**Passo 3: Decidir o Modo Claro/Escuro (Light/Dark Mode)**
```
Considere:
- Preferência do usuário?
- Padrão da indústria?
- Tipo de conteúdo? (conteúdo denso em texto = luz preferida)
- Hora de uso? (app noturno = opção escura)
```

---

## 6. Princípios de Dark Mode

### Regras Chave (Sem códigos fixos)

1. **Nunca use preto puro** → Use um cinza muito escuro com um leve matiz da marca.
2. **Nunca use texto em branco puro** → Use brilho (lightness) entre 87-92%.
3. **Reduza a saturação** → Cores vibrantes cansam os olhos no modo escuro.
4. **Elevação = Brilho** → Elementos que estão "por cima" devem ser ligeiramente mais claros.

---

## 7. Diretrizes de Acessibilidade

### Requisitos de Contraste (WCAG)

| Nível | Texto Normal | Texto Grande |
| :--- | :--- | :--- |
| AA (mínimo) | 4.5:1 | 3:1 |
| AAA (aprimorado)| 7:1 | 4.5:1 |

### Padronagens Seguras

| Caso de Uso | Diretriz |
| :--- | :--- |
| **Texto em fundo claro** | Use brilho (lightness) de 35% ou menos |
| **Texto em fundo escuro** | Use brilho (lightness) de 85% ou mais |
| **Primário no branco** | Garanta uma variante escura o suficiente |
| **Botões** | Alto contraste entre fundo e texto |

---

## 8. Checklist de Seleção de Cores

Antes de finalizar qualquer escolha de cor, verifique:

- [ ] **Perguntou a preferência do usuário?** (se não especificado)
- [ ] **Corresponde ao contexto do projeto?** (indústria, público)
- [ ] **Segue a regra 60-30-10?** (distribuição adequada)
- [ ] **Em conformidade com a WCAG?** (contraste verificado)
- [ ] **Funciona em ambos os modos?** (se o modo escuro for necessário)
- [ ] **NÃO é apenas o seu padrão/favorito?** (verificação de variedade)
- [ ] **Diferente do último projeto?** (evite repetição)

---

## 9. Anti-Padrões a Evitar

### ❌ NÃO FAÇA:
- Copiar os mesmos códigos hexadecimais em cada projeto.
- Usar roxo/violeta por padrão (tendência de IA).
- Usar modo escuro + neon por padrão (tendência de IA).
- Usar fundos em preto puro (#000000).
- Usar texto em branco puro (#FFFFFF) sobre fundo escuro.
- Ignorar o contexto da indústria do usuário.
- Deixar de perguntar a preferência do usuário.

### ✅ FAÇA:
- Gere uma paleta nova para cada projeto.
- Pergunte ao usuário sobre preferências de cor.
- Considere a indústria e o público.
- Use HSL para uma manipulação flexível.
- Teste o contraste e a acessibilidade.
- Ofereça opções de modo claro E escuro.

---

> **Lembre-se**: Cores são decisões, não padrões. Cada projeto merece uma seleção cuidadosa baseada em seu contexto único.
