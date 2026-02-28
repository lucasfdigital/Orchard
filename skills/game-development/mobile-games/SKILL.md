---
name: mobile-games
description: Princípios de desenvolvimento de jogos mobile. Entrada por toque, bateria, performance e lojas de aplicativos.
allowed-tools: Read, Write, Edit, Glob, Grep
---

# Desenvolvimento de Jogos Mobile

> Restrições de plataforma e princípios de otimização.

---

## 1. Considerações sobre a Plataforma

### Restrições Chave

| Restrição | Estratégia |
| :--- | :--- |
| **Entrada por toque** | Áreas de toque grandes, gestos |
| **Bateria** | Limitar uso de CPU/GPU |
| **Térmico** | Reduzir performance quando aquecido |
| **Tamanho da tela** | UI responsiva |
| **Interrupções** | Pausar ao ir para o background |

---

## 2. Princípios de Entrada por Toque

### Toque vs Controle

| Toque | Desktop / Consoles |
| :--- | :--- |
| Impreciso | Preciso |
| Oclui a tela (dedo na frente) | Sem oclusão |
| Botões limitados | Muitos botões |
| Gestos disponíveis | Botões / alavancas |

### Melhores Práticas

- Alvo de toque mínimo: 44x44 points
- Feedback visual imediato ao tocar
- Evitar requisitos de tempo (timing) ultra precisos
- Suportar tanto o modo Retrato (Portrait) quanto Paisagem (Landscape)

---

## 3. Metas de Performance

### Gerenciamento Térmico

| Ação | Gatilho |
| :--- | :--- |
| Reduzir qualidade | Dispositivo morno |
| Limitar FPS | Dispositivo quente |
| Pausar efeitos | Temperatura crítica |

### Otimização de Bateria

- 30 FPS costuma ser suficiente
- Colocar em "sleep" quando pausado
- Minimizar uso de GPS / rede
- Modo escuro economiza bateria em telas OLED

---

## 4. Requisitos das Lojas (App Stores)

### iOS (App Store)

| Requisito | Nota |
| :--- | :--- |
| Rótulos de privacidade | Obrigatório |
| Exclusão de conta | Se houver criação de conta |
| Screenshots | Para todos os tamanhos de dispositivo |

### Android (Google Play)

| Requisito | Nota |
| :--- | :--- |
| API Alvo | SDK do ano vigente |
| 64-bit | Obrigatório |
| App bundles | Recomendado |

---

## 5. Modelos de Monetização

| Modelo | Melhor Para |
| :--- | :--- |
| **Premium** | Jogos de alta qualidade, público fiel |
| **Grátis + IAP** | Casuais, baseados em progressão |
| **Anúncios** | Hyper-casual, alto volume |
| **Assinatura** | Atualizações frequentes, multiplayer |

---

## 6. Anti-Padrões

| ❌ Não Faça | ✅ Faça |
| :--- | :--- |
| Controles de desktop no mobile | Projete para o toque |
| Ignorar drenagem de bateria | Monitore o térmico |
| Forçar modo paisagem | Suporte a preferência do jogador |
| Rede sempre ativa | Use cache e sincronia |

---

> **Lembre-se:** Mobile é a plataforma mais restrita. Respeite a bateria e a atenção do usuário.
