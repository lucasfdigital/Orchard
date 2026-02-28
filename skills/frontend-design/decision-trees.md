# Árvores de Decisão & Templates de Contexto

> PENSAMENTO de design baseado no contexto, não em soluções fixas.
> **Estes são GUIAS de decisão, não templates para copiar e colar.**
> **Para princípios de psicologia de UX (Hick's, Fitts', etc.), consulte:** [ux-psychology.md](ux-psychology.md)

---

## ⚠️ Como Usar Este Arquivo

Este arquivo ajuda você a DECIDIR, não a copiar.

- Árvores de decisão → Ajudam você a PENSAR nas opções.
- Templates → Mostram ESTRUTURA e PRINCÍPIOS, não valores exatos.
- **Sempre pergunte sobre as preferências do usuário** antes de aplicar.
- **Gere paletas novas** baseadas no contexto, não copie códigos hexadecimais.
- **Aplique as leis de UX** do arquivo `ux-psychology.md` para validar as decisões.

---

## 1. Árvore de Decisão Mestre

```
┌─────────────────────────────────────────────────────────────┐
│                     O QUE VOCÊ ESTÁ CONSTRUINDO?            │
└─────────────────────────────────────────────────────────────┘
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
        ▼                     ▼                     ▼
    E-COMMERCE            SaaS/APP              CONTEÚDO
    - Páginas de produto  - Dashboard           - Blog
    - Checkout            - Ferramentas         - Portfólio
    - Catálogo            - Admin               - Landing Page
        │                     │                     │
        ▼                     ▼                     ▼
    PRINCÍPIOS:           PRINCÍPIOS:           PRINCÍPIOS:
    - Confiança           - Funcionalidade      - Storytelling
    - Ação                - Clareza             - Emoção
    - Urgência            - Eficiência          - Criatividade
```

---

## 2. Árvore de Decisão de Público

### Quem é o seu usuário-alvo?

```
PÚBLICO-ALVO
      │
      ├── Geração Z (18-25)
      │   ├── Cores: Ousadas, vibrantes, combinações inesperadas
      │   ├── Tipografia: Grande, expressiva, variável
      │   ├── Layout: Mobile-first, vertical, fragmentado (snackable)
      │   ├── Efeitos: Movimento, gamificação, interativo
      │   └── Abordagem: Autêntica, rápida, sem "clima corporativo"
      │
      ├── Millennials (26-41)
      │   ├── Cores: Atenuadas (muted), terrosas, sofisticadas
      │   ├── Tipografia: Limpa, legível, funcional
      │   ├── Layout: Responsivo, baseado em cards, organizado
      │   ├── Efeitos: Sutis, apenas quando necessário
      │   └── Abordagem: Focada em valores, transparente, sustentável
      │
      ├── Geração X (42-57)
      │   ├── Cores: Profissionais, confiáveis, conservadoras
      │   ├── Tipografia: Familiar, clara, direta
      │   ├── Layout: Hierarquia tradicional, previsível
      │   ├── Efeitos: Mínimos, feedback funcional
      │   └── Abordagem: Direta, eficiente, confiável
      │
      ├── Boomers (58+)
      │   ├── Cores: Alto contraste, simples, claras
      │   ├── Tipografia: Tamanhos grandes, alta legibilidade
      │   ├── Layout: Simples, linear, sem excesso de informação
      │   ├── Efeitos: Nenhum ou muito mínimos
      │   └── Abordagem: Clara, detalhada, confiável
      │
      └── B2B / Enterprise
          ├── Cores: Paleta profissional, tons atenuados
          ├── Tipografia: Limpa, focada em dados, fácil de escanear
          ├── Layout: Baseado em grids, organizado, eficiente
          ├── Efeitos: Profissionais, sutis
          └── Abordagem: Especialista, focada na solução, guiada por ROI
```

---

## 3. Árvore de Decisão de Seleção de Cores

### Em vez de códigos hex fixos, use este processo:

```
QUAL EMOÇÃO/AÇÃO VOCÊ DESEJA?
            │
            ├── Confiança & Segurança
            │   └── Considere: Família do azul, neutros profissionais
            │       → PERGUNTE ao usuário sobre preferência de tom específico
            │
            ├── Crescimento & Saúde
            │   └── Considere: Família do verde, tons naturais
            │       → PERGUNTE se o foco é eco/natureza/bem-estar
            │
            ├── Urgência & Ação
            │   └── Considere: Cores quentes (laranja/vermelho) como DESTAQUE (ACCENTS)
            │       → Use com moderação, PERGUNTE se é apropriado
            │
            ├── Luxo & Premium
            │   └── Considere: Escuros profundos, metálicos, paleta contida
            │       → PERGUNTE sobre o posicionamento da marca
            │
            ├── Criativo & Lúdico
            │   └── Considere: Multi-colorido, combinações inesperadas
            │       → PERGUNTE sobre a personalidade da marca
            │
            └── Calmo & Minimalista
                └── Considere: Neutros com um único acento (accent)
                    → PERGUNTE qual cor de destaque combina com a marca
```

---

## 4. Árvore de Decisão de Tipografia

```
QUAL É O TIPO DE CONTEÚDO?
          │
          ├── Pesado em Dados (Dashboard, SaaS)
          │   ├── Estilo: Sans-serif, clara, compacta
          │   ├── Escala: Razão mais apertada (1.125-1.2)
          │   └── Prioridade: Escaneabilidade, densidade
          │
          ├── Editorial (Blog, Revista)
          │   ├── Estilo: Título Serif + Corpo Sans funciona bem
          │   ├── Escala: Mais dramática (1.333+)
          │   └── Prioridade: Conforto de leitura, hierarquia
          │
          ├── Tecnologia Moderna (Startup, Marketing de SaaS)
          │   ├── Estilo: Sans geométrica ou humanista
          │   ├── Escala: Equilibrada (1.25)
          │   └── Prioridade: Sensação moderna, clareza
          │
          ├── Luxo (Moda, Premium)
          │   ├── Estilo: Serif elegante ou Sans fina
          │   ├── Escala: Dramática (1.5-1.618)
          │   └── Prioridade: Sofisticação, espaço em branco
          │
          └── Lúdico (Crianças, Jogos, Casual)
              ├── Estilo: Fontes arredondadas e amigáveis
              ├── Escala: Variada, expressiva
              └── Prioridade: Diversão, acessível, legível
```

---

## 5. Diretrizes de E-commerce {#e-commerce}

### Princípios Chave (Não são regras fixas)
- **Confiança primeiro:** Como você mostrará segurança?
- **Orientado à ação:** Onde estão os CTAs?
- **Escaneável:** Os usuários conseguem comparar rapidamente?

### Pensamento sobre Cores:
```
E-commerce tipicamente precisa de:
├── Cor de confiança (frequentemente família do azul) → PERGUNTE preferência
├── Fundo limpo (branco/neutro) → depende da marca
├── Acento de ação (para CTAs, promoções) → depende do nível de urgência
├── Semântica de sucesso/erro → convenções padrão funcionam
└── Integração da marca → PERGUNTE sobre cores existentes
```

### Princípios de Layout:
```
┌────────────────────────────────────────────────────┐
│  HEADER: Marca + Busca + Carrinho                  │
│  (Mantenha as ações essenciais visíveis)           │
├────────────────────────────────────────────────────┤
│  ZONA DE CONFIANÇA: Por que confiar neste site?     │
│  (Frete, devoluções, segurança - se aplicável)     │
├────────────────────────────────────────────────────┤
│  HERO: Mensagem ou oferta principal                │
│  (CTA claro, foco único)                           │
├────────────────────────────────────────────────────┤
│  CATEGORIAS: Navegação fácil                       │
│  (Visual, filtrável, escaneável)                   │
├────────────────────────────────────────────────────┤
│  PRODUTOS: Comparação fácil                        │
│  (Preço, avaliação, ações rápidas visíveis)        │
├────────────────────────────────────────────────────┤
│  PROVA SOCIAL: Por que outros confiam              │
│  (Avaliações, depoimentos - se disponível)         │
├────────────────────────────────────────────────────┤
│  FOOTER: Todos os detalhes                         │
│  (Políticas, contato, selos de confiança)          │
└────────────────────────────────────────────────────┘
```

---

## 6. Diretrizes de Dashboard SaaS {#saas}

### Princípios Chave
- **Funcional primeiro:** Clareza dos dados sobre a decoração.
- **UI Calma:** Reduzir a carga cognitiva.
- **Consistente:** Padrões previsíveis.

### Pensamento sobre Cores:
```
Dashboards tipicamente precisam de:
├── Fundo: Claro OU Escuro (PERGUNTE a preferência)
├── Superfície (Surface): Leve contraste em relação ao fundo
├── Acento Primário: Para as ações principais
├── Cores de Dados: Semântica de sucesso/aviso/perigo
└── Atenuadas (Muted): Para informações secundárias
```

---

## 7. Diretrizes de Landing Page {#landing-page}

### Princípios Chave
- **Centrado no Hero:** A primeira impressão é a que mais conta.
- **Foco único:** Um CTA principal.
- **Emocional:** Conecte-se antes de vender.

### Pensamento sobre Cores:
```
Landing Pages tipicamente precisam de:
├── Primária da marca: Fundo do Hero ou acento (accent)
├── Secundária limpa: Maioria da página
├── Cor de CTA: Se destaca de todo o resto
├── Apoio: Para seções, depoimentos
└── PERGUNTE sobre as cores da marca primeiro!
```

### Princípios de Estrutura:
```
┌────────────────────────────────────────────────────┐
│  Navegação: Mínima, CTA visível                    │
├────────────────────────────────────────────────────┤
│  HERO: Gancho + Valor + CTA                        │
│  (Seção mais importante, maior impacto)            │
├────────────────────────────────────────────────────┤
│  PROBLEMA: Qual dor seu público tem?               │
├────────────────────────────────────────────────────┤
│  SOLUÇÃO: Como você resolve isso                   │
├────────────────────────────────────────────────────┤
│  PROVA: Por que acreditar em você?                  │
│  (Depoimentos, logos, estatísticas)               │
├────────────────────────────────────────────────────┤
│  COMO: Explicação simples do processo              │
├────────────────────────────────────────────────────┤
│  PREÇOS: Se aplicável                              │
├────────────────────────────────────────────────────┤
│  FAQ: Responder às objeções                        │
├────────────────────────────────────────────────────┤
│  CTA FINAL: Repetir a ação principal               │
└────────────────────────────────────────────────────┘
```

---

## 8. Diretrizes de Portfólio {#portfolio}

### Princípios Chave
- **Personalidade:** Mostre quem você é.
- **Foco no trabalho:** Deixe os projetos falarem.
- **Memorável:** Destaque-se dos templates comuns.

### Pensamento sobre Cores:
```
Portfólio é pessoal - muitas opções:
├── Minimalista: Neutros + um acento de assinatura
├── Ousado: Escolhas de cores inesperadas
├── Escuro (Dark): Sensação artística, temperamental (moody)
├── Claro (Light): Sensação limpa e profissional
└── PERGUNTE sobre a identidade pessoal da marca!
```

---

## 9. Checklists Pré-Design

### Antes de Iniciar QUALQUER Design

- [ ] **Público definido?** (exatamente quem).
- [ ] **Objetivo principal identificado?** (qual ação).
- [ ] **Restrições conhecidas?** (tempo, marca, tecnologia).
- [ ] **Conteúdo disponível?** (ou se placeholders são necessários).
- [ ] **Preferências do usuário perguntadas?** (cores, estilo, layout).

---

## 10. Estimativa de Complexidade

### Projetos Rápidos (Horas)
```
Landing page simples
Portfólio pequeno
Formulário básico
Componente único
```
→ Abordagem: Decisões mínimas, execução focada.

### Projetos Médios (Dias)
```
Site com múltiplas páginas
Dashboard com módulos
Categorias de E-commerce
Formulários complexos
```
→ Abordagem: Estabelecer tokens, componentes customizados.

### Projetos Grandes (Semanas)
```
Aplicação SaaS completa
Plataforma de E-commerce
Sistema de design customizado
Workflows complexos
```
→ Abordagem: Sistema de design completo, documentação, testes.

---

> **Lembre-se**: Estes templates mostram ESTRUTURA e processo de PENSAMENTO. Cada projeto precisa de cores, tipografia e decisões de estilo novas, baseadas em seu contexto único. PERGUNTE quando não estiver claro.
