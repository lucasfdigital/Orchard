---
name: web-games
description: Princípios de desenvolvimento de jogos para navegador web. Seleção de framework, WebGPU, otimização, PWA.
allowed-tools: Read, Write, Edit, Glob, Grep
---

# Desenvolvimento de Jogos para Navegador Web

> Seleção de framework e princípios específicos para navegadores.

---

## 1. Seleção de Framework

### Árvore de Decisão

```
Qual o tipo de jogo?
│
├── Jogo 2D
│   ├── Recursos completos de motor de jogo (game engine)? → Phaser
│   └── Poder de renderização bruto? → PixiJS
│
├── Jogo 3D
│   ├── Motor completo (física, XR)? → Babylon.js
│   └── Focado em renderização? → Three.js
│
└── Híbrido / Canvas
    └── Customizado → Canvas bruto/WebGL
```

### Comparação (2025)

| Framework | Tipo | Melhor Para |
|-----------|------|----------|
| **Phaser 4** | 2D | Recursos completos de jogo |
| **PixiJS 8** | 2D | Renderização, UI |
| **Three.js** | 3D | Visualizações, peso-leve |
| **Babylon.js 7** | 3D | Motor completo, XR |

---

## 2. Adoção WebGPU

### Suporte de Navegador (2025)

| Navegador | Suporte |
|---------|---------|
| Chrome | ✅ Desde v113 |
| Edge | ✅ Desde v113 |
| Firefox | ✅ Desde v131 |
| Safari | ✅ Desde 18.0 |
| **Total** | **~73%** global |

### Decisão

- **Novos projetos**: Use WebGPU com fallback para WebGL
- **Suporte legado**: Comece com WebGL
- **Detecção de funcionalidade**: Verifique `navigator.gpu`

---

## 3. Princípios de Performance

### Restrições do Navegador

| Restrição | Estratégia |
|------------|----------|
| Sem acesso a arquivos locais | Empacotamento de assets (bundling), CDN |
| Limitação de abas em segundo plano| Pause quando oculto |
| Limites de dados móveis | Comprima assets |
| Autoplay de áudio | Exija interação do usuário |

### Prioridade de Otimização

1. **Compressão de assets** - KTX2, Draco, WebP
2. **Carregamento preguiçoso (Lazy loading)** - Carregue sob demanda
3. **Pooling de objetos** - Evite Coleta de Lixo (GC - Garbage Collection)
4. **Agrupamento de chamadas de desenho (Draw call batching)** - Reduza mudanças de estado
5. **Web Workers** - Descarregue a computação pesada (offload)

---

## 4. Estratégia de Assets

### Formatos de Compressão

| Tipo | Formato |
|------|--------|
| Texturas | KTX2 + Basis Universal |
| Áudio | WebM/Opus (fallback: MP3) |
| Modelos 3D | glTF + Draco/Meshopt |

### Estratégia de Carregamento

| Fase | Carregamento |
|-------|------|
| Inicialização (Startup)| Assets centrais, <2MB |
| Gameplay | Transmita (Stream) sob demanda |
| Segundo Plano (Background)| Pré-carregue (Prefetch) o próximo nível |

---

## 5. PWA para Jogos

### Benefícios

- Jogo offline
- Instalar na tela inicial
- Modo tela cheia
- Notificações push

### Requisitos

- Service worker para cache
- Manifesto do aplicativo web (Web app manifest)
- HTTPS

---

## 6. Manipulação de Áudio

### Requisitos do Navegador

- O contexto de áudio requer interação do usuário
- Crie o AudioContext no primeiro clique/toque
- Retome o contexto se estiver suspenso

### Melhores Práticas

- Use a Web Audio API
- Faça pool das fontes de áudio
- Pré-carregue sons comuns
- Comprima com WebM/Opus

---

## 7. Anti-Padrões

| ❌ Não Faça | ✅ Faça |
|----------|-------|
| Carregar todos os assets antecipadamente | Carregamento progressivo |
| Ignorar a visibilidade da aba | Pausar quando oculta |
| Bloquear no carregamento de áudio | Carregamento preguiçoso (lazy load) de áudio |
| Pular a compressão | Comprimir tudo |
| Assumir conexão rápida | Lidar com redes lentas |

---

> **Lembre-se:** O navegador é a plataforma mais acessível. Respeite as suas restrições.
