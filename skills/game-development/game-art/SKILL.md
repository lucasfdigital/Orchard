---
name: game-art
description: Princípios de arte para jogos. Seleção de estilo visual, pipeline de assets e workflow de animação.
allowed-tools: Read, Glob, Grep
---

# Princípios de Arte para Jogos

> Design thinking visual para jogos - seleção de estilo, pipelines de assets e direção de arte.

---

## 1. Seleção de Estilo de Arte

### Árvore de Decisão

```
Qual sensação o jogo deve evocar?
│
├── Nostálgico / Retrô
│   ├── Paleta limitada? → Pixel Art
│   └── Sensação de desenho à mão? → Vetorial / Estilo Flash
│
├── Realista / Imersivo
│   ├── Alto orçamento? → PBR 3D
│   └── Realismo estilizado? → Texturas pintadas à mão
│
├── Acessível / Casual
│   ├── Formas limpas? → Flat / Minimalista
│   └── Sensação suave? → Gradientes / Sombras suaves
│
└── Único / Experimental
    └── Definir guia de estilo customizado
```

### Matriz de Comparação de Estilos

| Estilo | Velocidade de Produção | Barreira de Entrada | Escalabilidade | Melhor Para |
| :--- | :--- | :--- | :--- | :--- |
| **Pixel Art** | Média | Média | Difícil de contratar | Indie, retrô |
| **Vetor/Flat** | Rápida | Baixa | Fácil | Mobile, casual |
| **Pintado à mão** | Lenta | Alta | Média | Fantasia, estilizado |
| **PBR 3D** | Lenta | Alta | Pipeline AAA | Jogos realistas |
| **Low-poly** | Rápida | Média | Fácil | Indie 3D |
| **Cel-shaded** | Média | Média | Média | Anime, desenho animado |

---

## 2. Decisões de Pipeline de Assets

### Pipeline 2D

| Fase | Opções de Ferramentas | Resultado (Output) |
| :--- | :--- | :--- |
| **Conceito** | Papel, Procreate, Photoshop | Folha de referência (Ref sheet) |
| **Criação** | Aseprite, Photoshop, Krita | Sprites individuais |
| **Atlas** | TexturePacker, Aseprite | Folha de sprites (Spritesheet) |
| **Animação** | Spine, DragonBones, Quadro a quadro | Dados de animação |
| **Integração** | Importação na Engine | Assets prontos para o jogo |

### Pipeline 3D

| Fase | Opções de Ferramentas | Resultado (Output) |
| :--- | :--- | :--- |
| **Conceito** | Arte 2D, Blockout | Referência |
| **Modelagem** | Blender, Maya, 3ds Max | Mesh high-poly |
| **Retopologia** | Blender, ZBrush | Mesh pronta para o jogo |
| **UV/Textura** | Substance Painter, Blender | Mapas de textura |
| **Rigging** | Blender, Maya | Rig esquelético |
| **Animação** | Blender, Maya, Mixamo | Clipes de animação |
| **Exportação** | FBX, glTF | Pronto para a Engine |

---

## 3. Decisões de Teoria das Cores

### Seleção de Paleta

| Objetivo | Estratégia | Exemplo |
| :--- | :--- | :--- |
| **Harmonia** | Complementar ou análoga | Jogos de natureza |
| **Contraste** | Diferenças de alta saturação | Jogos de ação |
| **Clima (Mood)** | Temperatura quente/fria | Terror, aconchegante (cozy) |
| **Legibilidade** | Contraste de valor sobre matiz | Clareza de gameplay |

### Princípios de Cores

- **Hierarquia:** Elementos importantes devem se destacar
- **Consistência:** Mesmo objeto = mesma família de cores
- **Contexto:** Cores são lidas de forma diferente em diferentes fundos
- **Acessibilidade:** Não dependa apenas da cor para comunicar algo

---

## 4. Princípios de Animação

### Os 12 Princípios (Aplicados a Jogos)

| Princípio | Aplicação no Jogo |
| :--- | :--- |
| **Squash & Stretch** | Arcos de pulo, impactos |
| **Antecipação** | Preparação antes de um ataque |
| **Encenação (Staging)** | Silhuetas claras |
| **Siga Adiantado (Follow-through)** | Cabelo, capas após o movimento |
| **Slow in/out** | Suavização em transições (easing) |
| **Arcos** | Caminhos de movimento naturais |
| **Ação Secundária** | Respiração, piscar de olhos |
| **Timing** | Contagem de quadros = peso/velocidade |
| **Exagero** | Legível de longa distância |
| **Apelo (Appeal)** | Design memorável |

### Diretrizes de Contagem de Quadros (Frames)

| Tipo de Ação | Quadros Típicos | Sensação |
| :--- | :--- | :--- |
| Respiração (Idle) | 4-8 | Sutil |
| Ciclo de caminhada | 6-12 | Suave |
| Ciclo de corrida | 4-8 | Energético |
| Ataque | 3-6 | Ágil (Snappy) |
| Morte | 8-16 | Dramático |

---

## 5. Decisões de Resolução e Escala

### Resolução 2D por Plataforma

| Plataforma | Resolução Base | Escala de Sprite |
| :--- | :--- | :--- |
| Mobile | 1080p | Personagens de 64-128px |
| Desktop | 1080p-4K | Personagens de 128-256px |
| Pixel art | 320x180 a 640x360 | Personagens de 16-32px |

### Regra de Consistência

Escolha uma unidade base e mantenha-a:
- Pixel art: Trabalhe em 1x, aumente a escala (nunca diminua)
- Arte HD: Defina o DPI, mantenha a proporção
- 3D: 1 unidade = 1 metro (padrão da indústria)

---

## 6. Organização de Assets

### Convenção de Nomenclatura

```
[tipo]_[objeto]_[variante]_[estado].[ext]

Exemplos:
spr_player_idle_01.png
tex_stone_wall_normal.png
mesh_tree_oak_lod2.fbx
```

### Princípio de Estrutura de Pastas

```
assets/
├── characters/
│   ├── player/
│   └── enemies/
├── environment/
│   ├── props/
│   └── tiles/
├── ui/
├── effects/
└── audio/
```

---

## 7. Anti-Padrões

| ❌ Não Faça | ✅ Faça |
| :--- | :--- |
| Misturar estilos aleatoriamente | Definir e seguir um guia de estilo |
| Trabalhar apenas na resolução final | Criar na resolução de origem (source) |
| Ignorar a legibilidade da silhueta | Testar na distância de gameplay |
| Detalhar demais o fundo | Focar o detalhe na área do jogador |
| Pular testes de cores | Testar no dispositivo de destino |

---

> **Lembre-se:** A arte serve ao gameplay. Se não ajuda o jogador, é apenas decoração.
