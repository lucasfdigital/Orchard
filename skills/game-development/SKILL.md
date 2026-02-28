---
name: game-development
description: Orquestrador de desenvolvimento de jogos. Direciona para skills específicas por plataforma baseadas nas necessidades do projeto.
allowed-tools: Read, Write, Edit, Glob, Grep, Bash
---

# Desenvolvimento de Jogos

> **Skill de Orquestração** que fornece princípios fundamentais e direciona para sub-skills especializadas.

---

## Quando Usar Esta Skill

Você está trabalhando em um projeto de desenvolvimento de jogos. Esta skill ensina os PRINCÍPIOS do desenvolvimento de jogos e direciona você para a sub-skill correta baseada no contexto.

---

## Roteamento de Sub-Skills

### Seleção de Plataforma

| Se o jogo visa... | Use a Sub-Skill |
| :--- | :--- |
| Navegadores web (HTML5, WebGL) | `game-development/web-games` |
| Mobile (iOS, Android) | `game-development/mobile-games` |
| PC (Steam, Desktop) | `game-development/pc-games` |
| Headsets VR/AR | `game-development/vr-ar` |

### Seleção de Dimensão

| Se o jogo é... | Use a Sub-Skill |
| :--- | :--- |
| 2D (sprites, tilemaps) | `game-development/2d-games` |
| 3D (meshes, shaders) | `game-development/3d-games` |

### Áreas de Especialidade

| Se você precisa de... | Use a Sub-Skill |
| :--- | :--- |
| GDD, balanceamento, psicologia do jogador | `game-development/game-design` |
| Multiplayer, rede | `game-development/multiplayer` |
| Estilo visual, pipeline de assets, animação | `game-development/game-art` |
| Design de som, música, áudio adaptativo | `game-development/game-audio` |

---

## Princípios Centrais (Todas as Plataformas)

### 1. O Game Loop

Todo jogo, independentemente da plataforma, segue este padrão:

```
ENTRADA (INPUT) → Ler as ações do jogador
ATUALIZAÇÃO     → Processar a lógica do jogo (fixed timestep)
RENDERIZAÇÃO    → Desenhar o quadro (interpolado)
```

**Regra do Timestep Fixo (Fixed Timestep):**
- Física/Lógica: Taxa fixa (ex: 50Hz).
- Renderização: O mais rápido possível.
- Interpolar entre estados para visuais suaves.

---

### 2. Matriz de Seleção de Padrões

| Padrão | Use Quando | Exemplo |
| :--- | :--- | :--- |
| **Máquina de Estados (State Machine)** | 3-5 estados discretos | Jogador: Idle→Walk→Jump |
| **Object Pooling** | Spawn/Destroy frequentes | Balas, partículas |
| **Observador/Eventos** | Comunicação entre sistemas | Vida (Health) → atualizações de UI |
| **ECS** | Milhares de entidades similares | Unidades de RTS, partículas |
| **Command** | Desfazer, replay, rede | Gravação de entrada |
| **Behavior Tree** | Decisões complexas de IA| IA de inimigo |

**Regra de Decisão:** Comece com Máquina de Estados. Adicione ECS apenas quando a performance exigir.

---

### 3. Abstração de Entrada (Input)

Abstraia a entrada em AÇÕES, não teclas brutas:

```
"jump"  → Espaço, Gamepad A, Toque na tela
"move"  → WASD, Analógico esquerdo, Joystick virtual
```

**Por quê:** Permite multi-plataforma e controles remapeáveis.

---

### 4. Orçamento de Performance (60 FPS = 16.67ms)

| Sistema | Orçamento (Budget) |
| :--- | :--- |
| Entrada (Input) | 1ms |
| Física | 3ms |
| IA | 2ms |
| Lógica do Jogo | 4ms |
| Renderização | 5ms |
| Margem (Buffer) | 1.67ms |

**Prioridade de Otimização:**
1. Algoritmo (O(n²) → O(n log n)).
2. Batching (reduzir chamadas de desenho).
3. Pooling (evitar picos de Garbage Collector).
4. LOD (Level of Detail - detalhe por distância).
5. Culling (pular o que está invisível).

---

### 5. Seleção de IA por Complexidade

| Tipo de IA | Complexidade | Use Quando |
| :--- | :--- | :--- |
| **FSM** | Simples | 3-5 estados, comportamento previsível |
| **Behavior Tree** | Média | Modular, amigável para designers |
| **GOAP** | Alta | Emergente, baseado em planejamento |
| **IA de Utilidade** | Alta | Decisões baseadas em pontuação (scoring) |

---

### 6. Estratégia de Colisão

| Tipo | Ideal Para |
| :--- | :--- |
| **AABB** | Retângulos, verificações rápidas |
| **Círculo** | Objetos redondos, baixo custo |
| **Spatial Hash** | Muitos objetos de tamanho similar |
| **Quadtree** | Mundos grandes, tamanhos variados |

---

## Anti-Padrões (Universais)

| NÃO FAÇA | FAÇA |
| :--- | :--- |
| Atualizar tudo a cada quadro | Use eventos, dirty flags |
| Criar objetos em loops críticos (hot loops) | Use Object Pooling |
| Não cachear nada | Cacheie referências |
| Otimizar sem fazer profiling | Faça o profiling primeiro |
| Misturar entrada com lógica | Abstraia a camada de entrada |

---

## Exemplos de Roteamento

### Exemplo 1: "Quero fazer um plataforma 2D baseado em navegador"
→ Comece com `game-development/web-games` para seleção de framework.
→ Depois `game-development/2d-games` para padrões de sprites/tilemaps.
→ Referencie `game-development/game-design` para level design.

### Exemplo 2: "Jogo de puzzle mobile para iOS e Android"
→ Comece com `game-development/mobile-games` para entrada por toque e lojas.
→ Use `game-development/game-design` para o balanceamento do puzzle.

### Exemplo 3: "Shooter multiplayer em VR"
→ `game-development/vr-ar` para conforto e imersão.
→ `game-development/3d-games` para renderização.
→ `game-development/multiplayer` para rede.

---

> **Lembre-se:** Ótimos jogos vêm da iteração, não da perfeição. Prototipe rápido, depois refine.
