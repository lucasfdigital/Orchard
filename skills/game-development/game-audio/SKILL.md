---
name: game-audio
description: Princípios de áudio para jogos. Sound design, integração musical e sistemas de áudio adaptativo.
allowed-tools: Read, Glob, Grep
---

# Princípios de Áudio para Jogos

> Sound design e integração musical para experiências de jogo imersivas.

---

## 1. Sistema de Categorias de Áudio

### Definições de Categorias

| Categoria | Comportamento | Exemplos |
| :--- | :--- | :--- |
| **Música** | Loop, crossfade, ducking | BGM, música de combate |
| **SFX** | One-shot, posicionado em 3D | Passos, impactos |
| **Ambiente** | Loop, camadas de fundo | Vento, multidão, floresta |
| **UI** | Imediato, não-3D | Cliques de botão, notificações |
| **Voz** | Prioridade, gatilho de ducking | Diálogos, narrador |

### Hierarquia de Prioridade

```
Quando os sons competem pelos canais:

1. Voz (Mais alta - sempre audível)
2. SFX do Jogador (Feedback crítico)
3. SFX de Inimigos (Importante para o gameplay)
4. Música (Clima, mas pode sofrer ducking)
5. Ambiente (Mais baixa - pode ser descartada)
```

---

## 2. Decisões de Sound Design

### Abordagens de Criação de SFX

| Abordagem | Quando Usar | Trade-offs |
| :--- | :--- | :--- |
| **Gravação (Foley)** | Necessidades realistas | Alta qualidade, requer tempo |
| **Síntese** | Sci-fi, retrô, UI | Único, requer habilidade |
| **Bibliotecas/Samples**| Produção rápida | Sons comuns, licenciamento |
| **Camadas (Layering)** | Sons complexos | Melhores resultados, mais trabalho |

### Estrutura de Camadas (Layering)

| Camada | Propósito | Exemplo: Tiro de Arma |
| :--- | :--- | :--- |
| **Ataque** | Transiente inicial | Clique, estalo |
| **Corpo (Body)** | Caráter principal | "Boom", explosão |
| **Cauda (Tail)** | Decaimento, sala | Reverb, eco |
| **Sweetener** | "Tempero" especial | Cápsula caindo, mecânico |

---

## 3. Integração Musical

### Sistema de Estados da Música

```
Estado do Jogo → Resposta Musical
│
├── Menu → Tema calmo e em loop
├── Exploração → Ambiente, atmosférico
├── Combate Detectado → Transição para tensão
├── Combate Engajado → Música de batalha total
├── Vitória → Stinger + transição calma
├── Derrota → Stinger sombrio
└── Chefão (Boss) → Faixa única, múltiplas fases
```

### Técnicas de Transição

| Técnica | Quando Usar | Sensação |
| :--- | :--- | :--- |
| **Crossfade** | Mudança suave de clima | Gradual |
| **Stinger** | Evento imediato | Dramático |
| **Stem Mixing** | Intensidade dinâmica | Sem costuras (Seamless) |
| **Sincronia de Batida** | Gameplay rítmico | Musical |
| **Ponto de Fila (Queue)**| Próxima quebra natural | Limpo |

---

## 4. Decisões de Áudio Adaptativo

### Parâmetros de Intensidade

| Parâmetro | Afeta | Exemplo |
| :--- | :--- | :--- |
| **Nível de Ameaça** | Intensidade da música | Contagem de inimigos |
| **Vida (Health)** | Filtro, reverb | Vida baixa = som abafado |
| **Velocidade** | Tempo, energia | Velocidade de corrida/corrida |
| **Ambiente** | Reverb, EQ | Caverna vs Exterior |
| **Hora do Dia** | Clima, volume | Noite = mais silencioso |

### Vertical vs Horizontal

| Sistema | O que muda | Melhor Para |
| :--- | :--- | :--- |
| **Vertical (camadas)** | Adiciona/remove camadas | Escala de intensidade |
| **Horizontal (segmentos)**| Diferentes seções musicais | Mudanças de estado |
| **Combinado** | Ambos | Trilhas adaptativas AAA |

---

## 5. Decisões de Áudio 3D

### Espacialização

| Elemento | Posicionado em 3D? | Razão |
| :--- | :--- | :--- |
| Passos do jogador | Não (ou sutil) | Sempre audível |
| Passos do inimigo | Sim | Consciência direcional |
| Tiros | Sim | Consciência de combate |
| Música | Não | Clima, não-diegético |
| Zona de Ambiente | Sim (Área) | Ambiental |
| Sons de UI | Não | Feedback da interface |

### Comportamento de Distância

| Distância | Comportamento do Som |
| :--- | :--- |
| **Perto** | Volume total, frequência total |
| **Médio** | Queda de volume, corte de agudos |
| **Longe** | Volume baixo, filtro low-pass |
| **Máxima** | Silencioso ou sugestão de ambiente |

---

## 6. Considerações de Plataforma

### Seleção de Formato

| Plataforma | Formato Recomendado | Razão |
| :--- | :--- | :--- |
| PC | OGG Vorbis, WAV | Qualidade, sem licenciamento |
| Consoles | Específico da plataforma | Certificação |
| Mobile | MP3, AAC | Tamanho, compatibilidade |
| Web | WebM/Opus, fallback MP3 | Suporte de navegadores |

### Orçamento de Memória

| Tipo de Jogo | Orçamento de Áudio | Estratégia |
| :--- | :--- | :--- |
| Mobile casual | 10-50 MB | Comprimido, poucas variantes |
| PC indie | 100-500 MB | Foco em qualidade |
| AAA | 1+ GB | Qualidade total, muitas variantes |

---

## 7. Hierarquia de Mixagem

### Referência de Equilíbrio de Volume

| Categoria | Nível Relativo | Notas |
| :--- | :--- | :--- |
| **Voz** | 0 dB (Referência) | Sempre clara |
| **SFX do Jogador** | -3 a -6 dB | Proeminente mas não agressivo |
| **Música** | -6 a -12 dB | Fundação, abaixa para vozes |
| **SFX de Inimigos** | -6 a -9 dB | Importante mas não dominante |
| **Ambiente** | -12 a -18 dB | Fundo sutil |

### Regras de Ducking

| Quando | "Ducking" em quê? | Quantidade |
| :--- | :--- | :--- |
| Voz toca | Música, Ambiente | -6 a -9 dB |
| Explosão | Tudo exceto explosão | Queda breve |
| Menu abre | Áudio do gameplay | -3 a -6 dB |

---

## 8. Anti-Padrões

| ❌ Não Faça | ✅ Faça |
| :--- | :--- |
| Tocar o mesmo som repetido | Use variações (3-5 por som) |
| Volume máximo em tudo | Use a hierarquia de mixagem |
| Ignorar o silêncio | O silêncio cria contraste |
| Uma única faixa em loop | Forneça variedade e transições |
| Pular áudio no protótipo | Áudio temporário é importante |

---

> **Lembre-se:** 50% da experiência de um jogo é o áudio. Um jogo mudo perde metade da sua alma.
