---
name: pc-games
description: Princípios de desenvolvimento de jogos para PC e consoles. Seleção de engines, recursos de plataforma e estratégias de otimização.
allowed-tools: Read, Write, Edit, Glob, Grep
---

# Desenvolvimento de Jogos para PC/Consoles

> Seleção de engines e princípios específicos de plataforma.

---

## 1. Seleção de Engine

### Árvore de Decisão

```
O que você está construindo?
│
├── Jogo 2D
│   ├── Open source é importante? → Godot
│   └── Grande equipe/assets? → Unity
│
├── Jogo 3D
│   ├── Qualidade visual AAA? → Unreal
│   ├── Prioridade multiplataforma? → Unity
│   └── Indie/open source? → Godot 4
│
└── Necessidades Específicas
    ├── Performance DOTS? → Unity
    ├── Nanite/Lumen? → Unreal
    └── Leveza? → Godot
```

### Comparação

| Fator | Unity 6 | Godot 4 | Unreal 5 |
| :--- | :--- | :--- | :--- |
| **2D** | Bom | Excelente | Limitado |
| **3D** | Bom | Bom | Excelente |
| **Aprendizado** | Médio | Fácil | Difícil |
| **Custo** | Partilha de receita | Grátis | 5% após $1M |
| **Equipe** | Qualquer | Solo a Médio | Médio a Grande |

---

## 2. Recursos de Plataforma

### Integração com Steam

| Recurso | Propósito |
| :--- | :--- |
| Conquistas (Achievements) | Objetivos do jogador |
| Cloud Saves | Progresso entre dispositivos |
| Placar (Leaderboards) | Competição |
| Workshop | Mods de usuários |
| Rich Presence | Mostrar status dentro do jogo |

### Requisitos de Console

| Plataforma | Certificação |
| :--- | :--- |
| PlayStation | Conformidade TRC |
| Xbox | Conformidade XR |
| Nintendo | Lotcheck |

---

## 3. Suporte a Controles (Controllers)

### Abstração de Entrada (Input)

```
Mapeie AÇÕES, não botões:
- "confirmar" → A (Xbox), X (PS), B (Nintendo)
- "cancelar"  → B (Xbox), O (PS), A (Nintendo)
```

### Feedback Háptico (Vibração)

| Intensidade | Uso |
| :--- | :--- |
| Leve | Feedback de UI |
| Média | Impactos |
| Forte | Eventos principais |

---

## 4. Otimização de Performance

### Profiling Primeiro

| Engine | Ferramenta |
| :--- | :--- |
| Unity | Janela de Profiler |
| Godot | Depurador → Profiler |
| Unreal | Unreal Insights |

### Gargalos Comuns

| Gargalo | Solução |
| :--- | :--- |
| Draw calls | Batching, atlases |
| Picos de GC | Object pooling |
| Física | Colisores mais simples |
| Shaders | Shaders de LOD |

---

## 5. Princípios Específicos de Engine

### Unity 6

- **DOTS** para sistemas onde a performance é crítica
- **Burst compiler** para caminhos de execução intensos (hot paths)
- **Addressables** para streaming de assets

### Godot 4

- **GDScript** para iteração rápida
- **C#** para lógica complexa
- **Sinais** para desacoplamento de sistemas

### Unreal 5

- **Blueprint** para designers
- **C++** para performance pura
- **Nanite** para ambientes de alta contagem de polígonos
- **Lumen** para iluminação dinâmica

---

## 6. Anti-Padrões

| ❌ Não Faça | ✅ Faça |
| :--- | :--- |
| Escolher engine pelo hype | Escolher pelas necessidades do projeto |
| Ignorar diretrizes da plataforma | Estudar requisitos de certificação |
| Fixar botões (hardcode) | Abstrair para ações |
| Pular o profiling | Perfilize cedo e com frequência |

---

> **Lembre-se:** A engine é uma ferramenta. Domine os princípios e adapte-se a qualquer uma.
