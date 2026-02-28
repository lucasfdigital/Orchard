# Pensamento de Design Mobile

> **Este arquivo evita que a IA use padrões memorizados e força o pensamento genuíno.**
> Mecanismos para prevenir comportamentos padrão de treinamento de IA no desenvolvimento mobile.
> **O equivalente mobile da abordagem de decomposição de layout do frontend.**

---

## 🧠 PROTOCOLO DE PENSAMENTO MOBILE PROFUNDO

### Este processo é obrigatório antes de cada projeto mobile

```
┌─────────────────────────────────────────────────────────────────┐
│                    PENSAMENTO MOBILE PROFUNDO                   │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  1️⃣ ANÁLISE DE CONTEXTO                                         │
│     └── Quais são minhas suposições para este projeto?          │
│         └── QUESTIONE estas suposições                          │
│                                                                 │
│  2️⃣ ANÁLISE ANTI-PADRÃO                                         │
│     └── Estou aplicando um padrão decorado?                     │
│         └── Este padrão é REALMENTE o melhor para ESTE projeto? │
│                                                                 │
│  3️⃣ DECOMPOSIÇÃO DE PLATAFORMA                                  │
│     └── Pensei no iOS e Android separadamente?                  │
│         └── Quais são os padrões específicos de cada plataforma?│
│                                                                 │
│  4️⃣ QUEBRA DE INTERAÇÃO POR TOQUE                              │
│     └── Analisei cada interação individualmente?                │
│         └── Apliquei a Lei de Fitts e a Thumb Zone?             │
│                                                                 │
│  5️⃣ ANÁLISE DE IMPACTO EM PERFORMANCE                           │
│     └── Considerei o impacto de cada componente?                │
│         └── A solução padrão é performática?                    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🚫 PADRÕES MOBILE DA IA (LISTA DE PROIBIÇÕES)

### É PROIBIDO usar estes padrões automaticamente!

Os padrões a seguir são "atalhos" que as IAs aprenderam. Antes de usar qualquer um deles, **QUESTIONE-OS e CONSIDERE ALTERNATIVAS!**

```
┌─────────────────────────────────────────────────────────────────┐
│                 🚫 PORTO SEGURO DA IA MOBILE                    │
│           (Padrões Padrão - Nunca Use Sem Questionar)           │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  PADRÕES DE NAVEGAÇÃO:                                          │
│  ├── Barra de abas para todo projeto (Um drawer seria melhor?)  │
│  ├── 5 abas fixas (3 seriam suficientes? Para 6+, drawer?)      │
│  ├── Aba "Home" na esquerda (O comportamento do usuário diz o quê?)│
│  └── Menu hambúrguer (Já está datado?)                          │
│                                                                 │
│  PADRÕES DE GERENCIAMENTO DE ESTADO:                            │
│  ├── Redux em tudo (Zustand/Jotai é suficiente?)                │
│  ├── Estado global para tudo (Estado local não basta?)          │
│  ├── Inferno de Context Providers (Baseado em átomos é melhor?)  │
│  └── BLoC para todo projeto Flutter (Riverpod é mais moderno?)   │
│                                                                 │
│  PADRÕES DE LISTA:                                              │
│  ├── FlatList como padrão (FlashList é mais performático?)      │
│  ├── windowSize=21 (Realmente necessário?)                      │
│  ├── removeClippedSubviews (Sempre?)                            │
│  └── ListView.builder (ListView.separated é melhor?)            │
│                                                                 │
│  PADRÕES DE UI:                                                 │
│  ├── FAB no canto inferior direito (Esquerda é mais acessível?) │
│  ├── Pull-to-refresh em toda lista (Precisa mesmo em tudo?)     │
│  ├── Swipe para deletar da esquerda (Direita é melhor?)         │
│  └── Bottom sheet para todo modal (Tela cheia seria melhor?)    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🔍 DECOMPOSIÇÃO DE COMPONENTES (OBRIGATÓRIO)

### Realize esta análise para cada tela antes de codar:

```
TELA: [Nome da Tela]
├── AÇÃO PRIMÁRIA: [Qual a ação principal?]
│   └── Está na thumb zone? [Sim/Não → Por quê?]
│
├── ALVOS DE TOQUE: [Todos os elementos clicáveis]
│   ├── [Elemento 1]: [Tamanho]pt → Suficiente?
│   └── Espaçamento: [Gap]pt → Risco de toque acidental?
│
├── CONTEÚDO ROLÁVEL:
│   ├── É uma lista? → FlatList/FlashList [Por que esta escolha?]
│   ├── Quantidade de itens: ~[N] → Consideração de performance?
│   └── Altura fixa? → getItemLayout é necessário?
│
├── REQUISITOS DE ESTADO:
│   ├── Estado local é suficiente?
│   └── Preciso subir o estado (lift state) ou usar global? [Por quê?]
│
├── DIFERENÇAS DE PLATAFORMA:
│   ├── iOS: [Algo diferente necessário?]
│   └── Android: [Algo diferente necessário?]
│
├── CONSIDERAÇÃO OFFLINE:
│   ├── Esta tela deve funcionar offline?
│   └── Estratégia de cache: [Sim/Não/Qual?]
│
└── IMPACTO EM PERFORMANCE:
    ├── Algum componente pesado?
    ├── Memoização necessária?
```

---

## 🎯 MATRIZ DE QUESTIONAMENTO DE PADRÕES

Questione cada suposição automática:
- **Navegação**: "Vou usar barra de abas" → Quantos destinos? 3? 6+? iPad compatível?
- **Estado**: "Vou usar Redux" → Quão complexo é o app? Zustand ou TanStack bastam?
- **Listas**: "Vou de FlatList" → Performance é crítica? FlashList é opção?
- **UI**: "Modal bottom sheet" → Quanto conteúdo tem? Tela cheia cabe melhor?

---

## 🧪 TESTE ANTI-MEMORIZAÇÃO

- □ Escolhi esta solução "porque sempre faço assim"?
- □ Este é um padrão excessivamente comum em dados de treinamento?
- □ Escrevi esta solução automaticamente sem pensar?
- □ Pensei de forma específica para cada plataforma (iOS/Android)?
- □ Considerei o impacto em memória e bateria?

---

## 🔄 QUEBRA DE INTERAÇÃO

Antes de adicionar qualquer gesto:
1. **Descoberta**: Como o usuário saberá que este gesto existe? Tem um botão alternativo? (OBRIGATÓRIO).
2. **Convenção**: O que este gesto significa no iOS vs Android?
3. **Acessibilidade**: Usuários com deficiência motora conseguem realizar? Tem alternativa via VoiceOver/TalkBack?
4. **Conflito**: Conflita com gestos do sistema (edge swipe)?

---

## 🎭 ESPÍRITO EM VEZ DE CHECKLIST

| ❌ Auto-engano | ✅ Avaliação Honesta |
| :--- | :--- |
| "Alvo de toque tem 44px" (mas na borda difícil) | "O usuário consegue atingir com uma mão?" |
| "Usei FlatList" (mas sem memoizar) | "A rolagem está fluida (60fps)?" |
| "Nav específica por plataforma" (só mudou ícone) | "O iOS parece iOS e o Android parece Android?" |

---

## 📝 COMPROMISSO DE DESIGN MOBILE (Início de Projeto)

```
Project: _______________
Platform: iOS / Android / Ambos

1. Padrão que NÃO vou usar automaticamente neste projeto:
   └── _______________
2. Foco específico neste contexto:
   └── _______________
3. Diferenças entre plataformas que irei implementar:
   └── iOS: _______________ / Android: _______________
4. Área que irei otimizar especificamente para performance:
   └── _______________
```

---

> **Lembre-se:** Se você escolheu uma solução "porque é como sempre é feito", você escolheu SEM PENSAR. Cada projeto é único. **PENSE, depois code.**
