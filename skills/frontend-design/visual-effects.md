# Referência de Efeitos Visuais

> Princípios e técnicas de efeitos CSS modernos — aprenda os conceitos, crie variações.
> **Não há valores fixos para copiar — entenda os padrões.**

---

## 1. Princípios de Glassmorphism

### O que faz o Glassmorphism funcionar

```
Propriedades Chave:
├── Fundo semitransparente (não sólido)
├── Backdrop blur (efeito de vidro fosco)
├── Borda sutil (para definição)
└── Frequentemente: sombra leve para profundidade
```

### O Padrão (Personalize os valores)

```css
.glass {
  /* Transparência: ajuste a opacidade baseado na legibilidade do conteúdo */
  background: rgba(R, G, B, OPACIDADE);
  /* OPACIDADE: 0.1-0.3 para fundo escuro, 0.5-0.8 para fundo claro */
  
  /* Blur: maior = mais fosco */
  backdrop-filter: blur(QUANTIDADE);
  /* QUANTIDADE: 8-12px sutil, 16-24px forte */
  
  /* Borda: define as arestas */
  border: 1px solid rgba(255, 255, 255, OPACIDADE);
  /* OPACIDADE: 0.1-0.3 tipicamente */
}
```

### Quando Usar Glassmorphism
- ✅ Sobre fundos coloridos ou com imagens.
- ✅ Modais, sobreposições (overlays), cards.
- ✅ Barras de navegação com conteúdo rolando por trás.
- ❌ Conteúdo com muito texto (problemas de legibilidade).
- ❌ Fundos simples e sólidos (sem propósito).

---

## 2. Princípios de Neomorphism

### O que faz o Neomorphism funcionar

```
Conceito Chave: Elementos suaves e extrudados usando sombras DUPLAS
├── Sombra clara (direção da fonte de luz)
├── Sombra escura (direção oposta)
└── O fundo deve ser o mesmo (mesma cor)
```

### Aviso de Acessibilidade
⚠️ **Baixo contraste** — use com moderação, garanta limites claros.

---

## 3. Princípios de Hierarquia de Sombras

### Conceito: Sombras Indicam Elevação

```
Maior elevação = sombra maior
├── Nível 0: Sem sombra (plano na superfície)
├── Nível 1: Sombra sutil (levemente levantado)
├── Nível 2: Sombra média (cards, botões)
├── Nível 3: Sombra grande (modais, dropdowns)
└── Nível 4: Sombra profunda (elementos flutuantes)
```

### Princípios para Sombras Naturais

1. **Y-offset maior que o X** (luz vem de cima).
2. **Baixa opacidade** (5-15% para sutil, 15-25% para pronunciado).
3. **Múltiplas camadas** para realismo (ambiente + direta).
4. **O desfoque (blur) escala com o offset** (offset maior = blur maior).

---

## 4. Princípios de Gradientes

### Tipos e Quando Usar

| Tipo | Padrão | Caso de Uso |
| :--- | :--- | :--- |
| **Linear** | Cor A → Cor B ao longo de uma linha | Fundos, botões, cabeçalhos |
| **Radial** | Centro → para fora | Destaques, pontos focais |
| **Cônico** | Ao redor do centro | Gráficos de pizza, efeitos criativos |

### Criando Gradientes Harmoniosos

```
Regras de Gradiente:
├── Use cores ADJACENTES no círculo cromático (análogas)
├── Ou o mesmo matiz com brilhos diferentes
├── Evite complementares (pode parecer agressivo)
└── Adicione paradas intermediárias para transições suaves
```

### Mesh Gradients (Gradientes de Malha)

```
Múltiplos gradientes radiais sobrepostos:
├── Cada um em uma posição diferente
├── Cada um com desvanecimento transparente
├── **Obrigatório para o fator "Uau" em seções Hero**
└── Cria um efeito orgânico e colorido (Busque por: "Aurora Gradient CSS")
```

---

## 5. Princípios de Efeitos de Borda

### Bordas em Gradiente
Técnica: Pseudo-elemento com fundo em gradiente onde o elemento tem um padding igual à largura da borda.

### Bordas Animadas
Técnica: Gradiente rotativo ou varredura cônica (conic sweep) usando pseudo-elementos e animações de rotação.

---

## 6. Princípios de Efeitos de Brilho (Glow)

### Brilho de Texto
Use múltiplas camadas de `text-shadow` com diferentes níveis de desfoque (blur).

### Brilho de Elemento
Use múltiplas camadas de `box-shadow` combinando com a cor do elemento para um brilho realista.

---

## 7. Técnicas de Sobreposição (Overlay)

### Sobreposição de Gradiente em Imagens
Propósito: Melhorar a legibilidade do texto sobre imagens.
Padrão: Gradiente de transparente para opaco posicionado onde o texto aparecerá.

---

## 8. Técnicas Modernas de CSS

### Container Queries
O componente responde ao SEU próprio recipiente, não à viewport. Ideal para componentes modulares e reutilizáveis.

### Seletor :has()
Estilização baseada nos filhos: "Pai que possui o filho X". Habilita padrões anteriormente impossíveis.

---

## 9. Princípios de Performance

### Propriedades Aceleradas por GPU

```
BARATO para animar (GPU):
├── transform (translate, scale, rotate)
└── opacity

CARO para animar (CPU):
├── width, height
├── top, left, right, bottom
├── margin, padding
└── box-shadow (recalcula o layout)
```

---

## 10. Checklist de Seleção de Efeitos

Antes de aplicar qualquer efeito:

- [ ] **Serve a um propósito?** (não é apenas decoração).
- [ ] **É apropriado para o contexto?** (marca, público).
- [ ] **Você variou em relação a projetos anteriores?** (evite repetição).
- [ ] **É acessível?** (contraste, sensibilidade ao movimento).
- [ ] **É performático?** (especialmente no mobile).
- [ ] **Perguntou a preferência do usuário?**

### Anti-Padrões

- ❌ Glassmorphism em cada elemento (fica kitsch).
- ❌ Escuro + neon como padrão (aparência preguiçosa de IA).
- ❌ **Designs estáticos/flat sem profundidade (FALHA).**
- ❌ Efeitos que prejudicam a legibilidade.
- ❌ Animações sem propósito.

---

> **Lembre-se**: Efeitos aprimoram o significado. Escolha com base no propósito e no contexto, não apenas porque "parece legal".
