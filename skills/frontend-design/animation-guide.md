# Diretrizes de Animação

> Princípios de animação e psicologia do timing — aprenda a decidir, não a copiar.
> **Não há durações fixas para memorizar — entenda o que afeta o tempo.**

---

## 1. Princípios de Duração

### O Que Afeta o Timing

```
Fatores que determinam a velocidade da animação:
├── DISTÂNCIA: Trajetória maior = duração maior
├── TAMANHO: Elementos maiores = animações mais lentas
├── COMPLEXIDADE: Complexo = processamento mais lento
├── IMPORTÂNCIA: Ações críticas = feedback claro
└── CONTEXTO: Urgente = rápido, luxuoso = lento
```

### Faixas de Duração por Propósito

| Propósito | Faixa | Por que |
| :--- | :--- | :--- |
| Feedback instantâneo | 50-100ms | Abaixo do limite de percepção |
| Micro-interações | 100-200ms | Rápido, mas perceptível |
| Transições padrão | 200-300ms | Ritmo confortável |
| Animações complexas | 300-500ms | Tempo para acompanhar |
| Transições de página | 400-600ms | Passagem suave |
| **Efeitos Wow/Premium** | 800ms+ | Dramático, orgânico (spring-based), em camadas |

### Escolhendo a Duração

Pergunte-se:
1. Qual a distância que o elemento está percorrendo?
2. Quão importante é notar essa mudança?
3. O usuário está esperando ou isso é algo em segundo plano?

---

## 2. Princípios de Easing

### O Que o Easing Faz

```
Easing = como a velocidade muda ao longo do tempo
├── Linear: velocidade constante (mecânico, robótico)
├── Ease-out: início rápido, fim lento (entrada natural)
├── Ease-in: início lento, fim rápido (saída natural)
└── Ease-in-out: lento em ambas as extremidades (suave, deliberado)
```

### Quando Usar Cada Um

| Easing | Ideal Para | Sensação |
| :--- | :--- | :--- |
| **Ease-out** | Elementos entrando | Chegando, acomodando-se |
| **Ease-in** | Elementos saindo | Partindo, saindo |
| **Ease-in-out** | Ênfase, loops | Deliberado, suave |
| **Linear** | Movimento contínuo | Mecânico, constante |
| **Bounce/Elastic** | UI lúdica | Divertido, energético |

### O Padrão

```css
/* Entrando na visualização = ease-out (desacelera) */
.enter {
  animation-timing-function: ease-out;
}

/* Saindo da visualização = ease-in (acelera) */
.exit {
  animation-timing-function: ease-in;
}

/* Contínuo = ease-in-out */
.continuous {
  animation-timing-function: ease-in-out;
}
```

---

## 3. Princípios de Micro-Interação

### O Que Faz uma Boa Micro-Interação

```
Propósito das micro-interações:
├── FEEDBACK: Confirmar que a ação ocorreu
├── ORIENTAÇÃO: Mostrar o que é possível
├── STATUS: Indicar o estado atual
└── DELEITE: Pequenos momentos de alegria
```

### Estados de Botão

```
Hover → mudança visual leve (elevação, cor, escala)
Active → sensação de pressionado (escala menor, mudança de sombra)
Focus → indicador claro (contorno, anel)
Loading → indicador de progresso (spinner, skeleton)
Success → confirmação (check, cor)
```

### Princípios

1. **Responda imediatamente** (abaixo de 100ms de percepção).
2. **Corresponda à ação** (pressionar = `scale(0.95)`, hover = `translateY(-4px) + glow`).
3. **Seja ousado, mas suave** (Sensação de trabalho profissional).
4. **Seja consistente** (mesmas ações = mesmo feedback).

---

## 4. Princípios de Estados de Carregamento

### Tipos por Contexto

| Situação | Abordagem |
| :--- | :--- |
| Carga rápida (<1s) | Nenhum indicador necessário |
| Média (1-3s) | Spinner ou animação simples |
| Longa (3s+) | Barra de progresso ou skeleton |
| Duração desconhecida | Indicador indeterminado |

### Skeleton Screens

```
Propósito: Reduzir o tempo de espera percebido
├── Mostrar o formato do layout imediatamente
├── Animar sutilmente (shimmer, pulso)
├── Substituir pelo conteúdo quando pronto
└── Parece mais rápido que um spinner
```

### Indicadores de Progresso

```
Quando mostrar o progresso:
├── Ação iniciada pelo usuário
├── Uploads/downloads de arquivos
├── Processos de múltiplas etapas
└── Operações longas

Quando NÃO é necessário:
├── Operações muito rápidas
├── Tarefas em segundo plano
└── Carregamentos iniciais de página (skeleton é melhor)
```

---

## 5. Princípios de Transições de Página

### Estratégia de Transição

```
Regra simples: saia rápido, entre mais devagar
├── Conteúdo de saída desaparece (fade) rapidamente
├── Conteúdo de entrada anima para dentro
└── Evita que "tudo se mova ao mesmo tempo"
```

### Padrões Comuns

| Padrão | Quando Usar |
| :--- | :--- |
| **Fade** | Padrão seguro, funciona em qualquer lugar |
| **Slide** | Navegação sequencial (anterior/próximo) |
| **Scale** | Abrir/fechar modais |
| **Shared element** | Manter continuidade visual |

### Correspondência de Direção

```
Direção da navegação = direção da animação
├── Avançar → slide vindo da direita
├── Voltar → slide vindo da esquerda
├── Mais profundo → escala aumenta do centro
├── Voltar ao topo → escala diminui
```

---

## 6. Princípios de Animação de Scroll

### Revelação Progressiva

```
O conteúdo aparece conforme o usuário rola:
├── Reduz a carga cognitiva inicial
├── Recompensa a exploração
├── Não deve parecer lento ou travado
└── Opção de desativar (acessibilidade)
```

### Pontos de Gatilho (Trigger Points)

| Quando Disparar | Efeito |
| :--- | :--- |
| Logo ao entrar na viewport| Revelação padrão |
| Centralizado na viewport | Para ênfase |
| Parcialmente visível | Revelação antecipada |
| Totalmente visível | Gatilho tardio |

### Propriedades de Animação

- Fade in (opacidade)
- Slide up (transform)
- Scale (transform)
- Combinação dos itens acima

### Performance

- Use Intersection Observer.
- Anime apenas transform/opacidade.
- Reduza no mobile se necessário.

---

## 7. Princípios de Efeitos de Hover

### Correspondência de Efeito com a Ação

| Elemento | Efeito | Intenção |
| :--- | :--- | :--- |
| **Card clicável** | Elevação + sombra | "Isso é interativo" |
| **Botão** | Mudança de cor/brilho | "Pressione-me" |
| **Imagem** | Zoom/escala | "Ver mais de perto" |
| **Link** | Sublinhado/cor | "Navegue para aqui" |

### Princípios

1. **Sinalize a interatividade** - o hover mostra que é clicável.
2. **Não exagere** - mudanças sutis funcionam melhor.
3. **Corresponda à importância** - mudança maior = mais importante.
4. **Alternativas para toque** - o hover não funciona no mobile.

---

## 8. Princípios de Animação de Feedback

### Estados de Sucesso

```
Celebre apropriadamente:
├── Ação menor → check/cor sutil
├── Ação maior → animação mais pronunciada
├── Conclusão → animação satisfatória
└── Corresponda à personalidade da marca
```

### Estados de Erro

```
Atraia a atenção sem pânico:
├── Mudança de cor (vermelho semântico)
├── Animação de vibração (shake) (breve!)
├── Foco no campo de erro
└── Mensagens claras
```

### Timing

- Sucesso: ligeiramente mais longo (aproveite o momento).
- Erro: rápido (não atrase a ação).
- Carregamento: contínuo até completar.

---

## 9. Princípios de Performance

### O Que é "Barato" para Animar

```
Acelerado por GPU (RÁPIDO):
├── transform: translate, scale, rotate
└── opacity: 0 para 1

Intensivo para CPU (LENTO):
├── width, height
├── top, left, right, bottom
├── margin, padding
├── border-radius
└── box-shadow
```

### Estratégias de Otimização

1. **Anime transform/opacidade** sempre que possível.
2. **Evite gatilhos de layout** (mudanças de tamanho/posição).
3. **Use `will-change` com moderação** (dicas para o navegador).
4. **Teste em dispositivos de baixo desempenho** (não apenas na máquina de dev).

### Respeitando as Preferências do Usuário

```css
@media (prefers-reduced-motion: reduce) {
  /* Respeite esta preferência */
  /* Apenas animações essenciais */
  /* Reduza ou remova movimentos decorativos */
}
```

---

## 10. Checklist de Decisão de Animação

Antes de adicionar uma animação:

- [ ] **Existe um propósito?** (feedback/orientação/deleite)
- [ ] **O timing é apropriado?** (nem muito rápido nem muito lento)
- [ ] **Você escolheu o easing correto?** (entrada/saída/ênfase)
- [ ] **É performático?** (apenas transform/opacidade)
- [ ] **Testou com "reduced motion"?** (acessibilidade)
- [ ] **Está consistente com outras animações?** (mesma sensação de tempo)
- [ ] **Não usou apenas configurações padrão (default)?** (verificação de variedade)
- [ ] **Perguntou ao usuário sobre o estilo se não estiver claro?**

### Anti-Padrões

- ❌ Usar os mesmos valores de timing em cada projeto.
- ❌ Animação pela animação (sem propósito).
- ❌ Ignorar a preferência de `reduced-motion`.
- ❌ Animar propriedades caras (que exigem muito processamento).
- ❌ Muitas coisas animando ao mesmo tempo.
- ❌ Atrasos que frustram os usuários.

---

> **Lembre-se**: Animação é comunicação. Cada movimento deve ter significado e servir à experiência do usuário.
