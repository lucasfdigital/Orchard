---
name: 2d-games
description: Princípios de desenvolvimento de jogos 2D. Sprites, tilemaps, física e câmera.
allowed-tools: Read, Write, Edit, Glob, Grep
---

# Desenvolvimento de Jogos 2D

> Princípios para sistemas de jogos 2D.

---

## 1. Sistemas de Sprites

### Organização de Sprites

| Componente | Propósito |
| :--- | :--- |
| **Atlas** | Combina texturas, reduz chamadas de desenho (draw calls) |
| **Animação** | Sequências de quadros (frames) |
| **Pivô (Pivot)** | Origem de rotação/escala |
| **Camadas (Layering)** | Controle de ordem Z |

### Princípios de Animação

- Taxa de quadros: 8-24 FPS típico
- Squash e stretch (esmagar e esticar) para impacto
- Antecipação antes da ação
- Follow-through (continuidade) após a ação

---

## 2. Design de Tilemap

### Considerações sobre Tiles

| Fator | Recomendação |
| :--- | :--- |
| **Tamanho** | 16x16, 32x32, 64x64 |
| **Auto-tiling** | Use para terrenos |
| **Colisão** | Formas simplificadas |

### Camadas (Layers)

| Camada | Conteúdo |
| :--- | :--- |
| Background | Cenário não interativo |
| Terreno | Chão onde se pode caminhar |
| Props | Objetos interativos |
| Foreground | Overlay de paralaxe |

---

## 3. Física 2D

### Formas de Colisão (Collision Shapes)

| Forma | Caso de Uso |
| :--- | :--- |
| Box (Caixa) | Objetos retangulares |
| Círculo | Bolas, arredondados |
| Cápsula | Personagens |
| Polígono | Formas complexas |

### Considerações de Física

- Pixel-perfect vs baseado em física
- Timestep fixo para consistência
- Camadas para filtragem

---

## 4. Sistemas de Câmera

### Tipos de Câmera

| Tipo | Uso |
| :--- | :--- |
| **Follow** | Seguir o jogador |
| **Look-ahead** | Antecipar movimento |
| **Multi-target** | Dois jogadores |
| **Baseada em salas** | Estilo Metroidvania |

### Screen Shake (Tremor de Tela)

- Curta duração (50-200ms)
- Intensidade decrescente
- Use com moderação

---

## 5. Padrões de Gênero

### Plataforma (Platformer)

- Coyote time (tolerância após sair da borda)
- Jump buffering (buffer de salto)
- Altura de salto variável

### Top-down (Visão de Cima)

- Movimento livre ou em 8 direções
- Baseado em mira ou mira automática
- Considere rotação ou não

---

## 6. Anti-Padrões

| ❌ Não Faça | ✅ Faça |
| :--- | :--- |
| Texturas separadas | Use atlases |
| Formas de colisão complexas | Colisão simplificada |
| Câmera instável | Suavização no seguimento (smooth follow) |
| Pixel-perfect na física | Escolha uma abordagem |

---

> **Lembre-se:** 2D é sobre clareza. Cada pixel deve se comunicar.
