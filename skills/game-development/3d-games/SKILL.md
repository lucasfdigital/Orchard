---
name: 3d-games
description: Princípios de desenvolvimento de jogos 3D. Renderização, shaders, física e câmeras.
allowed-tools: Read, Write, Edit, Glob, Grep
---

# Desenvolvimento de Jogos 3D

> Princípios para sistemas de jogos 3D.

---

## 1. Pipeline de Renderização

### Estágios

```
1. Processamento de Vértices → Transformar geometria
2. Rasterização → Converter para pixels
3. Processamento de Fragmentos → Colorir pixels
4. Saída (Output) → Para a tela
```

### Princípios de Otimização

| Técnica | Propósito |
| :--- | :--- |
| **Frustum culling** | Não renderizar o que está fora da tela |
| **Occlusion culling** | Não renderizar o que está escondido |
| **LOD** | Menos detalhes à distância |
| **Batching** | Combinar chamadas de desenho (draw calls) |

---

## 2. Princípios de Shaders

### Tipos de Shader

| Tipo | Propósito |
| :--- | :--- |
| **Vertex** | Posição, normais |
| **Fragment/Pixel** | Cor, iluminação |
| **Compute** | Computação geral |

### Quando Escrever Shaders Customizados

- Efeitos especiais (água, fogo, portais)
- Renderização estilizada (toon, sketch)
- Otimização de performance
- Identidade visual única

---

## 3. Física 3D

### Formas de Colisão (Collision Shapes)

| Forma | Caso de Uso |
| :--- | :--- |
| **Box (Caixa)** | Prédios, caixotes |
| **Esfera** | Bolas, verificações rápidas |
| **Cápsula** | Personagens |
| **Mesh** | Terrenos (custoso) |

### Princípios

- Colisores simples, visuais complexos
- Filtragem baseada em camadas (layers)
- Raycasting para linha de visão (line-of-sight)

---

## 4. Sistemas de Câmera

### Tipos de Câmera

| Tipo | Uso |
| :--- | :--- |
| **Terceira pessoa** | Ação, aventura |
| **Primeira pessoa** | Imersivo, FPS |
| **Isométrica** | Estratégia, RPG |
| **Orbital** | Inspeção, editores |

### Sensação da Câmera (Camera Feel)

- Seguimento suave (lerp)
- Evitar colisão com obstáculos
- Look-ahead para movimento
- Mudanças de FOV para sensação de velocidade

---

## 5. Iluminação

### Tipos de Luz

| Tipo | Uso |
| :--- | :--- |
| **Direcional** | Sol, lua |
| **Point** | Lâmpadas, tochas |
| **Spot** | Lanterna, holofote |
| **Ambiente** | Iluminação base |

### Considerações de Performance

- Sombras em tempo real são custosas
- "Bake" (assar) sempre que possível
- Shadow cascades para mundos grandes

---

## 6. Nível de Detalhe (LOD)

### Estratégia de LOD

| Distância | Modelo |
| :--- | :--- |
| Perto | Detalhe total |
| Médio | 50% de triângulos |
| Longe | 25% ou billboard |

---

## 7. Anti-Padrões

| ❌ Não Faça | ✅ Faça |
| :--- | :--- |
| Mesh colliders em todo lugar | Formas simples |
| Sombras em tempo real no mobile | Sombras "baked" ou de projeção (blob) |
| Um único LOD para todas as distâncias | LOD baseado em distância |
| Shaders não otimizados | Faça profiling e simplifique |

---

> **Lembre-se:** 3D é sobre ilusão. Crie a impressão de detalhe, não o detalhe em si.
