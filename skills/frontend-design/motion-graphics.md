# Referência de Motion Graphics

> Técnicas avançadas de animação para experiências web premium — Lottie, GSAP, SVG, 3D, Partículas.
> **Aprenda os princípios, crie efeitos WOW.**

---

## 1. Animações Lottie

### O que é Lottie?

```
Animações vetoriais baseadas em JSON:
├── Exportadas do After Effects via Bodymovin
├── Leves (menores que GIF/vídeo)
├── Escalonáveis (vetoriais, sem pixelização)
├── Interativas (controle de reprodução, segmentos)
└── Multi-plataforma (web, iOS, Android, React Native)
```

### Quando Usar Lottie

| Caso de Uso | Por que Lottie? |
| :--- | :--- |
| **Animações de carregamento**| Com a marca, suaves, leves |
| **Estados vazios (Empty states)**| Ilustrações envolventes |
| **Fluxos de integração (Onboarding)**| Animações complexas de várias etapas |
| **Feedback de Sucesso/Erro** | Micro-interações encantadoras |
| **Ícones animados** | Consistentes em várias plataformas |

### Princípios

- Mantenha o arquivo abaixo de 100KB para performance.
- Use loop com moderação (evite distrações).
- Forneça fallback estático para `reduced-motion`.
- Faça lazy load dos arquivos de animação quando possível.

---

## 2. GSAP (GreenSock)

### O que torna o GSAP Diferente

```
Animação profissional baseada em linha do tempo (timeline):
├── Controle preciso sobre sequências
├── ScrollTrigger para animações baseadas em rolagem
├── MorphSVG para transições de formas
├── Easing baseado em física
└── Funciona com qualquer elemento DOM
```

### Conceitos Centrais

| Conceito | Propósito |
| :--- | :--- |
| **Tween** | Animação única de A para B |
| **Timeline** | Animações sequenciadas ou sobrepostas |
| **ScrollTrigger** | Posição do scroll controla a reprodução |
| **Stagger** | Efeito de cascata entre vários elementos |

### Quando Usar GSAP

- ✅ Animações sequenciadas complexas.
- ✅ Revelações acionadas por scroll.
- ✅ Necessidade de controle preciso de timing.
- ✅ Efeitos de morphing em SVG.
- ❌ Efeitos simples de hover/foco (use CSS).
- ❌ Mobile onde a performance é crítica (GSAP é mais pesado).

---

## 3. Animações SVG

### Tipos de Animação SVG

| Tipo | Técnica | Caso de Uso |
| :--- | :--- | :--- |
| **Desenho de Linha** | stroke-dashoffset | Revelação de logo, assinaturas |
| **Morph** | Interpolação de path | Transições de ícones |
| **Transform** | rotate, scale, translate | Ícones interativos |
| **Cor** | Transição de fill/stroke | Mudanças de estado |

### Quando Usar Animações SVG

- ✅ Revelações de logo, momentos de marca.
- ✅ Transições de estado de ícones (hamburger ↔ X).
- ✅ Infográficos, visualização de dados.
- ✅ Ilustrações interativas.
- ❌ Conteúdo fotorrealista (use vídeo).
- ❌ Cenas muito complexas (performance).

---

## 4. Transforms 3D em CSS

### Propriedades Centrais

```
Espaço 3D no CSS:
├── perspective: profundidade do campo 3D (típico 500-1500px)
├── transform-style: preserve-3d (habilita 3D nos filhos)
├── rotateX/Y/Z: rotação por eixo
├── translateZ: mover para perto/longe do observador
└── backface-visibility: mostrar/esconder o lado de trás
```

### Padrões 3D Comuns

| Padrão | Caso de Uso |
| :--- | :--- |
| **Card flip** | Revelações, flashcards, visualizações de produto |
| **Tilt no hover** | Cards interativos, profundidade 3D |
| **Camadas Parallax** | Seções Hero, rolagem imersiva |
| **Carrossel 3D** | Galerias de imagens, sliders |

---

## 5. Efeitos de Partículas

### Tipos de Sistemas de Partículas

| Tipo | Sensação | Caso de Uso |
| :--- | :--- | :--- |
| **Geométrico** | Tech, rede | SaaS, sites de tecnologia |
| **Confete** | Celebração | Momentos de sucesso |
| **Neve/Chuva** | Atmosférico | Sazonal, clima |
| **Poeira/Bokeh** | Onírico (Dreamy) | Fotografia, luxo |
| **Vaga-lumes** | Mágico | Jogos, fantasia |

### Princípios

- Padrão: 30-50 partículas (para não sobrecarregar).
- Movimento: lento, orgânico (velocidade 0.5-2).
- Opacidade: 0.3-0.6 (não deve competir com o conteúdo).
- Conexões: linhas sutis para sensação de "rede".
- ⚠️ Desative ou reduza no mobile.

---

## 6. Animações Baseadas em Scroll

### CSS Nativo (Moderno)

```
CSS Scroll Timelines:
├── animation-timeline: scroll() - scroll do documento
├── animation-timeline: view() - elemento na viewport
├── animation-range: limites de entrada/saída (entry/exit)
└── Não requer JavaScript
```

---

## 7. Princípios de Performance

### Animação em GPU vs CPU

```
BARATO (Acelerado por GPU):
├── transform (translate, scale, rotate)
├── opacity
└── filter (use com moderação)

CARO (Dispara reflow/layout):
├── width, height
├── top, left, right, bottom
├── padding, margin
└── box-shadow complexo
```

---

## 8. Árvore de Decisão de Motion Graphics

```
Que animação você precisa?
│
├── Animação de marca complexa?
│   └── Lottie (export do After Effects)
│
├── Sequenciada e acionada por scroll?
│   └── GSAP + ScrollTrigger
│
├── Animação de logo/ícone?
│   └── Animação SVG (stroke ou morph)
│
├── Efeito 3D interativo?
│   └── CSS 3D Transforms (simples) ou Three.js (complexo)
│
├── Fundo atmosférico?
│   └── tsParticles ou Canvas
│
└── Entrada/Hover simples?
    └── CSS @keyframes ou Framer Motion
```

---

## 9. Anti-Padrões

| ❌ Não faça | ✅ Faça |
| :--- | :--- |
| Animar tudo ao mesmo tempo | Use Stagger e sequenciamento |
| Usar bibliotecas pesadas para efeitos simples | Comece com CSS |
| Ignorar o reduced-motion | Sempre forneça um fallback |
| Bloquear a main thread | Otimize para 60fps |
| Mesmas partículas em cada projeto | Combine com a marca/contexto |
| Efeitos complexos no mobile | Use detecção de recursos |

---

## 10. Referência Rápida

| Efeito | Ferramenta | Performance |
| :--- | :--- | :--- |
| Spinner de load | CSS/Lottie | Leve |
| Revelação em cascata | GSAP/Framer | Média |
| Desenho de path SVG | CSS stroke | Leve |
| Flip de card 3D | CSS transforms| Leve |
| Fundo de partículas | tsParticles | Pesada |
| Parallax de scroll | GSAP ScrollTrigger| Média |
| Morphing de formas | GSAP MorphSVG | Média |

---

> **Lembre-se**: Motion graphics deve aprimorar, não distrair. Cada animação deve servir a um PROPÓSITO — feedback, orientação, deleite ou storytelling.
