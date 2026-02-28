---
name: frontend-design
description: Design thinking e tomada de decisão para UI web. Use ao projetar componentes, layouts, esquemas de cores, tipografia ou criar interfaces estéticas. Ensina princípios, não valores fixos.
allowed-tools: Read, Write, Edit, Glob, Grep, Bash
---

# Sistema de Design Frontend

> **Filosofia:** Cada pixel tem um propósito. A moderação é um luxo. A psicologia do usuário impulsiona as decisões.
> **Princípio Central:** PENSE, não memorize. PERGUNTE, não presuma.

---

## 🎯 Regra de Leitura Seletiva (OBRIGATÓRIO)

**Leia os arquivos OBRIGATÓRIOS sempre, os OPCIONAIS apenas quando necessário:**

| Arquivo | Status | Quando Ler |
| :--- | :--- | :--- |
| [ux-psychology.md](ux-psychology.md) | 🔴 **OBRIGATÓRIO** | Leia sempre primeiro! |
| [color-system.md](color-system.md) | ⚪ Opcional | Decisões de cor/paleta |
| [typography-system.md](typography-system.md) | ⚪ Opcional | Seleção/combinação de fontes |
| [visual-effects.md](visual-effects.md) | ⚪ Opcional | Glassmorphism, sombras, gradientes |
| [animation-guide.md](animation-guide.md) | ⚪ Opcional | Quando precisar de animação |
| [motion-graphics.md](motion-graphics.md) | ⚪ Opcional | Lottie, GSAP, 3D |
| [decision-trees.md](decision-trees.md) | ⚪ Opcional | Templates de contexto |

> 🔴 **ux-psychology.md = LEIA SEMPRE. Outros = apenas se relevante.**

---

## 🔧 Scripts de Runtime

**Execute estes para auditorias (não leia, apenas rode):**

| Script | Propósito | Uso |
| :--- | :--- | :--- |
| `scripts/ux_audit.py` | Auditoria de Psicologia de UX e Acessibilidade | `python scripts/ux_audit.py <caminho_do_projeto>` |

---

## ⚠️ CRÍTICO: PERGUNTE ANTES DE ASSUMIR (OBRIGATÓRIO)

> **PARE! Se a solicitação do usuário for aberta, NÃO use os seus padrões favoritos.**

### Quando o Prompt do Usuário for Vago, PERGUNTE:

**Cor não especificada?** Pergunte:
> "Qual paleta de cores você prefere? (azul/verde/laranja/neutro/outra?)"

**Estilo não especificado?** Pergunte: 
> "Qual estilo você está buscando? (minimalista/ousado/retrô/futurista/orgânico?)"

**Layout não especificado?** Pergunte:
> "Você tem alguma preferência de layout? (coluna única/grid/assimétrico/largura total?)"

### ⛔ TENDÊNCIAS PADRÃO A EVITAR (ANTI-"PORTO SEGURO"):

| Tendência Padrão da IA | Por que é Ruim | Pense em Vez Disso |
| :--- | :--- | :--- |
| **Bento Grids (Clichê Moderno)** | Usado em todos os designs de IA | Por que este conteúdo PRECISA de um grid? |
| **Hero Split (Esquerda/Direita)** | Previsível e entediante | Que tal Tipografia Massiva ou Narrativa Vertical? |
| **Gradientes Mesh/Aurora** | O background preguiçoso "moderno" | Qual seria uma combinação de cores radical? |
| **Glassmorphism** | Ideia de IA para "premium" | Que tal cores sólidas, flat e de alto contraste? |
| **Ciano Profundo / Azul Fintech** | Refúgio seguro devido à proibição do roxo| Por que não Vermelho, Preto ou Verde Neon? |
| **"Orquestrar / Empoderar"** | Copywriting gerado por IA | Como um humano diria isso? |
| Fundo escuro + brilho neon | Superutilizado, "cara de IA" | O que a MARCA realmente precisa? |
| **Tudo arredondado** | Genérico/Seguro | Onde posso usar bordas afiadas e brutalistas? |

> 🔴 **"Cada estrutura 'segura' que você escolhe te deixa um passo mais perto de um template genérico. CORRA RISCOS."**

---

## 1. Análise de Restrições (SEMPRE PRIMEIRO)

Antes de qualquer trabalho de design, RESPONDA ESTAS perguntas ou PERGUNTE AO USUÁRIO:

| Restrição | Pergunta | Por que isso importa |
| :--- | :--- | :--- |
| **Cronograma** | Quanto tempo temos? | Determina a complexidade |
| **Conteúdo** | Pronto ou placeholder? | Afeta a flexibilidade do layout |
| **Marca** | Existem diretrizes? | Pode ditar cores/fontes |
| **Tecnologia** | Qual stack? | Afeta as possibilidades técnicas |
| **Público** | Quem exatamente? | Direciona todas as decisões visuais |

### Público → Abordagem de Design

| Público | O que considerar |
| :--- | :--- |
| **Geração Z** | Ousado, rápido, mobile-first, autêntico |
| **Millennials** | Limpo, minimalista, focado em valores |
| **Geração X** | Familiar, confiável, claro |
| **Boomers** | Legível, alto contraste, simples |
| **B2B** | Profissional, focado em dados, confiança |
| **Luxo** | Elegância contida, espaço em branco |

---

## 2. Princípios de Psicologia de UX

### Leis Fundamentais (Internalize estas)

| Lei | Princípio | Aplicação |
| :--- | :--- | :--- |
| **Lei de Hick** | Mais escolhas = decisões mais lentas | Limite opções, use divulgação progressiva |
| **Lei de Fitts** | Maior + mais perto = mais fácil de clicar | Dimensione os CTAs apropriadamente |
| **Lei de Miller** | ~7 itens na memória de trabalho | Agrupe o conteúdo em blocos |
| **Von Restorff** | Diferente = memorável | Torne os CTAs visualmente distintos |
| **Posição Serial** | Primeiro/último são mais lembrados | Info chave no início/final |

### Níveis de Design Emocional

```
VISCERAL (instante)  → Primeira impressão: cores, imagens, sensação geral
COMPORTAMENTAL (uso) → Ao usar: velocidade, feedback, eficiência
REFLEXIVO (memória)  → Depois: "Gosto do que isso diz sobre mim"
```

### Construção de Confiança

- Indicadores de segurança em ações sensíveis.
- Prova social onde for relevante.
- Acesso claro a contato/suporte.
- Design consistente e profissional.
- Políticas transparentes.

---

## 3. Princípios de Layout

### Proporção Áurea (φ = 1.618)

```
Use para harmonia proporcional:
├── Conteúdo : Sidebar = aproximadamente 62% : 38%
├── Tamanho de cada título = anterior × 1.618 (para escala dramática)
├── Espaçamento pode seguir: sm → md → lg (cada um × 1.618)
```

### Conceito de Grid de 8 Pontos

```
Todo o espaçamento e dimensionamento em múltiplos de 8:
├── Apertado: 4px (meio passo para micro)
├── Pequeno: 8px
├── Médio: 16px
├── Grande: 24px, 32px
├── XL: 48px, 64px, 80px
└── Ajuste com base na densidade do conteúdo
```

### Princípios Chave de Dimensionamento

| Elemento | Consideração |
| :--- | :--- |
| **Alvos de toque** | Tamanho mínimo confortável para toque |
| **Botões** | Altura baseada na hierarquia de importância |
| **Inputs** | Corresponder à altura do botão para alinhamento |
| **Cards** | Espaçamento consistente, com respiro |
| **Largura de leitura**| 45-75 caracteres é o ideal |

---

## 4. Princípios de Cor

### Regra 60-30-10

```
60% → Primária/Fundo (base calma e neutra)
30% → Secundária (áreas de suporte)
10% → Destaque/Accent (CTAs, realces, atenção)
```

### Psicologia das Cores (Para Tomada de Decisão)

| Se você precisa de... | Considere Matizes | Evite |
| :--- | :--- | :--- |
| Confiança, calma | Família dos Azuis | Vermelhos agressivos |
| Crescimento, natureza | Família dos Verdes | Cinzas industriais |
| Energia, urgência | Laranja, Vermelho | Azuis passivos |
| Luxo, criatividade | Teal Profundo, Ouro, Esmeralda| Brilhantes com aspecto barato |
| Limpo, minimalista | Neutros | Cores esmagadoras |

### Processo de Seleção

1. **Qual é a indústria?** (estreita as opções).
2. **Qual é a emoção?** (escolhe a primária).
3. **Modo claro ou escuro?** (define a base).
4. **PERGUNTE AO USUÁRIO** se não especificado.

Para teoria das cores detalhada: [color-system.md](color-system.md)

---

## 5. Princípios de Tipografia

### Seleção de Escala

| Tipo de Conteúdo | Razão de Escala | Sensação |
| :--- | :--- | :--- |
| UI Densa | 1.125-1.2 | Compacto, eficiente |
| Web Geral | 1.25 | Equilibrado (mais comum) |
| Editorial | 1.333 | Legível, espaçoso |
| Hero/Display | 1.5-1.618 | Impacto dramático |

### Conceito de Combinação (Pairing)

```
Contraste + Harmonia:
├── DIFERENTE o suficiente para hierarquia
├── SEMELHANTE o suficiente para coesão
└── Geralmente: display + neutro, ou serif + sans
```

### Regras de Legibilidade

- **Comprimento da linha**: 45-75 caracteres ideal.
- **Altura da linha (line-height)**: 1.4-1.6 para corpo de texto.
- **Contraste**: Verifique os requisitos WCAG.
- **Tamanho**: 16px+ para corpo de texto na web.

Para tipografia detalhada: [typography-system.md](typography-system.md)

---

## 6. Princípios de Efeitos Visuais

### Glassmorphism (Quando Apropriado)

```
Propriedades chave:
├── Fundo semi-transparente
├── Backdrop blur (desfoque de fundo)
├── Borda sutil para definição
└── ⚠️ AVISO: Glassmorphism padrão azul/branco é um clichê moderno. Use de forma radical ou não use.
```

### Hierarquia de Sombras

```
Conceito de Elevação:
├── Elementos mais altos = sombras maiores
├── Y-offset > X-offset (luz vindo de cima)
├── Múltiplas camadas = mais realista
└── Modo Escuro: pode precisar de brilho (glow) em vez de sombra
```

### Uso de Gradientes

```
Gradientes Harmoniosos:
├── Cores adjacentes no círculo (análogas)
├── OU mesmo matiz, luminosidade diferente
├── Evite pares complementares gritantes
├── 🚫 SEM Gradientes Mesh/Aurora (bolhas flutuantes)
└── VARIE radicalmente de projeto para projeto
```

Para guia completo de efeitos: [visual-effects.md](visual-effects.md)

---

## 7. Princípios de Animação

### Conceito de Tempo (Timing)

```
Duração baseada em:
├── Distância (mais longe = mais longo)
├── Tamanho (maior = mais lento)
├── Importância (crítico = claro)
└── Contexto (urgente = rápido, luxo = lento)
```

### Seleção de Easing

| Ação | Easing | Por que |
| :--- | :--- | :--- |
| Entrando | Ease-out | Desacelerar, acomodar-se |
| Saindo | Ease-in | Acelerar, sair |
| Ênfase | Ease-in-out | Suave, deliberado |
| Divertido | Bounce | Divertido, energético |

### Performance

- Anime apenas `transform` e `opacity`.
- Respeite a preferência `prefers-reduced-motion`.
- Teste em dispositivos de baixo desempenho.

Para padrões de animação: [animation-guide.md](animation-guide.md), para avançado: [motion-graphics.md](motion-graphics.md)

---

## 8. Checklist do "Fator Uau"

### Indicadores Premium

- [ ] Espaço em branco generoso (luxo = espaço para respirar).
- [ ] Profundidade e dimensão sutis.
- [ ] Animações suaves e com propósito.
- [ ] Atenção aos detalhes (alinhamento, consistência).
- [ ] Ritmo visual coeso.
- [ ] Elementos customizados (não apenas padrões).

### Construtores de Confiança

- [ ] Sinais de segurança onde for apropriado.
- [ ] Prova social / depoimentos.
- [ ] Proposta de valor clara.
- [ ] Imagens profissionais.
- [ ] Linguagem de design consistente.

### Gatilhos Emocionais

- [ ] Hero que evoca a emoção pretendida.
- [ ] Elementos humanos (rostos, histórias).
- [ ] Indicadores de progresso/conquista.
- [ ] Momentos de deleite.

---

## 9. Anti-padrões (O que NÃO fazer)

### ❌ Indicadores de Design Preguiçoso

- Fuentes do sistema padrão sem consideração.
- Imagens de stock que não combinam.
- Espaçamento inconsistente.
- Muitas cores competindo.
- Paredes de texto sem hierarquia.
- Contraste inacessível.

### ❌ Padrões de Tendência de IA (EVITE!)

- **Mesmas cores em todos os projetos**.
- **Escuro + neon como padrão**.
- **Roxo/violeta em tudo (PROIBIÇÃO DO ROXO ✅)**.
- **Bento grids para landing pages simples**.
- **Gradientes Mesh e Efeitos de Brilho**.
- **Mesma estrutura de layout / Clone da Vercel**.
- **Não perguntar as preferências do usuário**.

### ❌ Dark Patterns (Antiético)

- Custos ocultos.
- Falsa urgência.
- Ações forçadas.
- UI enganosa.
- Confirmshaming (envergonhar o usuário na confirmação).

---

## 10. Resumo do Processo de Decisão

```
Para CADA tarefa de design:

1. RESTRIÇÕES
   └── Qual é o cronograma, marca, tecnologia, público?
   └── Se não estiver claro → PERGUNTE

2. CONTEÚDO
   └── Que conteúdo existe?
   └── Qual é a hierarquia?

3. DIREÇÃO DE ESTILO
   └── O que é apropriado para o contexto?
   └── Se não estiver claro → PERGUNTE (não use o padrão!)

4. EXECUÇÃO
   └── Aplique os princípios acima
   └── Verifique contra os anti-padrões

5. REVISÃO
   └── "Isso serve ao usuário?"
   └── "Isso é diferente dos meus padrões usuais?"
   └── "Eu teria orgulho disso?"
```

---

## Relatórios de Referência

Para orientações mais profundas em áreas específicas:

- [color-system.md](color-system.md) - Teoria das cores e processo de seleção.
- [typography-system.md](typography-system.md) - Combinação de fontes e decisões de escala.
- [visual-effects.md](visual-effects.md) - Princípios e técnicas de efeitos.
- [animation-guide.md](animation-guide.md) - Princípios de motion design.
- [motion-graphics.md](motion-graphics.md) - Avançado: Lottie, GSAP, SVG, 3D, Partículas.
- [decision-trees.md](decision-trees.md) - Templates específicos por contexto.
- [ux-psychology.md](ux-psychology.md) - Mergulho profundo na psicologia do usuário.

---

## Skills Relacionadas

| Skill | Quando Usar |
| :--- | :--- |
| **frontend-design** (esta) | Antes de codar - Aprenda princípios de design (cor, tipografia, psicologia de UX) |
| **[web-design-guidelines](../web-design-guidelines/SKILL.md)** | Depois de codar - Audite a acessibilidade, performance e melhores práticas |

## Workflow Pós-Design

Após implementar seu design, execute a auditoria:

```
1. DESIGN   → Leia os princípios de frontend-design ← VOCÊ ESTÁ AQUI
2. CODE     → Implemente o design
3. AUDIT    → Execute a revisão de web-design-guidelines
4. FIX      → Corrija as descobertas da auditoria
```

> **Próximo Passo:** Após codar, use a skill `web-design-guidelines` para auditar sua implementação em busca de acessibilidade, estados de foco, animações e problemas de performance.

---

> **Lembre-se:** Design é PENSAR, não copiar. Cada projeto merece uma consideração nova baseada em seu contexto e usuários únicos. **Evite o Porto Seguro do SaaS Moderno!**
