---
name: vr-ar
description: Princípios de desenvolvimento de VR/AR. Conforto, interação e requisitos de performance.
allowed-tools: Read, Write, Edit, Glob, Grep
---

# Desenvolvimento de VR/AR

> Princípios para experiências imersivas.

---

## 1. Seleção de Plataforma

### Plataformas de VR (Realidade Virtual)

| Plataforma | Caso de Uso |
| :--- | :--- |
| **Quest** | Independente (Standalone), sem fios |
| **PCVR** | Alta fidelidade gráfica |
| **PSVR** | Mercado de consoles |
| **WebXR** | Baseado em navegador |

### Plataformas de AR (Realidade Aumentada)

| Plataforma | Caso de Uso |
| :--- | :--- |
| **ARKit** | Dispositivos iOS |
| **ARCore** | Dispositivos Android |
| **WebXR** | AR no navegador |
| **HoloLens** | Corporativo (Enterprise) |

---

## 2. Princípios de Conforto

### Prevenção de Enjoo (Motion Sickness)

| Causa | Solução |
| :--- | :--- |
| **Locomoção** | Teletransporte, giro em saltos (snap turn) |
| **Baixo FPS** | Manter 90 FPS estáveis |
| **Tremor de câmera** | Evitar ou minimizar ao máximo |
| **Aceleração rápida** | Movimento gradual |

### Configurações de Conforto

- Vinheta (Vignette) durante o movimento
- Giro em saltos (Snap) vs Giro suave (Smooth)
- Modos sentado vs em pé
- Calibração de altura

---

## 3. Requisitos de Performance

### Métricas Alvo

| Plataforma | FPS | Resolução |
| :--- | :--- | :--- |
| Quest 2 | 72-90 | 1832x1920 |
| Quest 3 | 90-120 | 2064x2208 |
| PCVR | 90 | 2160x2160+ |
| PSVR2 | 90-120 | 2000x2040 |

### Orçamento de Quadros (Frame Budget)

- VR exige tempos de quadro consistentes
- Um único quadro perdido = trepidação visível (judder)
- 90 FPS = Orçamento de 11.11ms por quadro

---

## 4. Princípios de Interação

### Interação com Controles

| Tipo | Uso |
| :--- | :--- |
| **Apontar e clicar** | UI, objetos distantes |
| **Agarrar (Grab)** | Manipulação |
| **Gestos** | Magia, ações especiais |
| **Físico** | Arremessar, golpear |

### Rastreamento de Mãos (Hand Tracking)

- Mais imersivo, porém menos preciso
- Bom para: social, casual
- Desafiador para: ação, precisão

---

## 5. Design Espacial

### Escala do Mundo

- 1 unidade = 1 metro (CRÍTICO)
- Objetos devem parecer ter o tamanho certo
- Teste com medidas reais do mundo físico

### Pistas de Profundidade (Depth Cues)

| Pista | Importância |
| :--- | :--- |
| Estéreo | Profundidade primária |
| Paralaxe de movimento| Secundária |
| Sombras | Aterramento (Grounding) |
| Oclusão | Camadas |

---

## 6. Anti-Padrões

| ❌ Não Faça | ✅ Faça |
| :--- | :--- |
| Mover a câmera sem o jogador | O jogador controla a câmera |
| Cair abaixo de 90 FPS | Mantenha a taxa de quadros |
| Usar texto minúsculo na UI | Use texto grande e legível |
| Ignorar o alcance do braço | Dimensione para o alcance do jogador |

---

> **Lembre-se:** Conforto não é opcional. Jogadores enjoados não jogam.
