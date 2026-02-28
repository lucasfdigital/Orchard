---
name: multiplayer
description: Princípios de desenvolvimento de jogos multiplayer. Arquitetura, rede e sincronização.
allowed-tools: Read, Write, Edit, Glob, Grep, Bash
---

# Desenvolvimento de Jogos Multiplayer

> Arquitetura de rede e princípios de sincronização.

---

## 1. Seleção de Arquitetura

### Árvore de Decisão

```
Qual tipo de multiplayer?
│
├── Competitivo / Tempo Real
│   └── Servidor Dedicado (autoritativo)
│
├── Cooperativo / Casual
│   └── Baseado em Host (um jogador é o servidor)
│
├── Baseado em Turnos
│   └── Cliente-servidor (simples)
│
└── Massivo (MMO)
    └── Servidores distribuídos
```

### Comparação

| Arquitetura | Latência | Custo | Segurança |
| :--- | :--- | :--- | :--- |
| **Dedicado** | Baixa | Alto | Forte |
| **P2P** | Variável | Baixo | Fraca |
| **Baseado em Host**| Média | Baixo | Média |

---

## 2. Princípios de Sincronização

### Estado vs Entrada (State vs Input)

| Abordagem | O que sincronizar | Melhor para |
| :--- | :--- | :--- |
| **Sincronia de Estado**| Estado do jogo | Simples, poucos objetos |
| **Sincronia de Entrada**| Entradas do jogador | Jogos de ação |
| **Híbrido** | Ambos | A maioria dos jogos |

### Compensação de Lag

| Técnica | Propósito |
| :--- | :--- |
| **Predição (Prediction)** | Cliente prevê o servidor |
| **Interpolação** | Suavizar jogadores remotos |
| **Reconciliação** | Corrigir erros de predição |
| **Compensação de Lag** | "Rewind" para detecção de acerto |

---

## 3. Otimização de Rede

### Redução de Largura de Banda (Bandwidth)

| Técnica | Ganho |
| :--- | :--- |
| **Compressão Delta** | Enviar apenas as mudanças |
| **Quantização** | Reduzir precisão |
| **Prioridade** | Dados importantes primeiro |
| **Área de Interesse** | Apenas entidades próximas |

### Taxas de Atualização (Update Rates)

| Tipo | Taxa |
| :--- | :--- |
| Posição | 20-60 Hz |
| Vida (Health) | Quando mudar |
| Inventário | Quando mudar |
| Chat | Ao enviar |

---

## 4. Princípios de Segurança

### Autoridade do Servidor

```
Cliente: "Eu acertei o inimigo"
Servidor: Validar → o projétil realmente atingiu?
         → o jogador estava em estado válido?
         → o tempo entre as ações era possível?
```

### Anti-Cheat

| Trapaça (Cheat) | Prevenção |
| :--- | :--- |
| Speed hack | Servidor valida movimento |
| Aimbot | Servidor valida linha de visão |
| Dupagem de Itens | Servidor é dono do inventário |
| Wall hack | Não envie dados de objetos ocultos |

---

## 5. Matchmaking (Pareamento)

### Considerações

| Fator | Impacto |
| :--- | :--- |
| **Habilidade (Skill)** | Partidas justas |
| **Latência** | Conexão jogável |
| **Tempo de espera** | Paciência do jogador |
| **Tamanho do grupo** | Jogo em equipe |

---

## 6. Anti-Padrões

| ❌ Não Faça | ✅ Faça |
| :--- | :--- |
| Confiar no cliente | O servidor é a autoridade |
| Enviar tudo | Envie apenas o necessário |
| Ignorar a latência | Projete considerando 100-200ms |
| Sincar posições exatas | Use interpolação/predição |

---

> **Lembre-se:** Nunca confie no cliente. O servidor é a fonte da verdade.
