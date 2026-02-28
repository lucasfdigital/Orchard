---
name: mobile-design
description: Design thinking mobile-first e tomada de decisão para apps iOS e Android. Interação por toque, padrões de performance, convenções de plataforma. Ensina princípios, não valores fixos. Use ao construir apps React Native, Flutter ou nativos.
allowed-tools: Read, Glob, Grep, Bash
---

# Sistema de Design Mobile

> **Filosofia:** Focado no toque. Consciente da bateria. Respeitoso com a plataforma. Capaz de operar offline.
> **Princípio Central:** Mobile NÃO é um desktop pequeno. PENSE nas restrições mobile, PERGUNTE a escolha da plataforma.

---

## 🔧 Scripts de Runtime

**Execute estes para validação (não leia, apenas rode):**

| Script | Propósito | Uso |
| :--- | :--- | :--- |
| `scripts/mobile_audit.py` | Auditoria de UX Mobile e Toque | `python scripts/mobile_audit.py <caminho_do_projeto>` |

---

## 🔴 OBRIGATÓRIO: Leia os Arquivos de Referência Antes de Trabalhar!

**⛔ NÃO inicie o desenvolvimento até ler os arquivos relevantes:**

### Universal (Leia Sempre)

| Arquivo | Conteúdo | Status |
| :--- | :--- | :--- |
| **[mobile-design-thinking.md](mobile-design-thinking.md)** | **⚠️ ANTI-MEMORIZAÇÃO: Força o pensamento, previne padrões de IA** | **⬜ CRÍTICO - PRIMEIRO** |
| **[touch-psychology.md](touch-psychology.md)** | **Lei de Fitts, gestos, haptics, thumb zone** | **⬜ CRÍTICO** |
| **[mobile-performance.md](mobile-performance.md)** | **Performance em RN/Flutter, 60fps, memória** | **⬜ CRÍTICO** |
| **[mobile-backend.md](mobile-backend.md)** | **Push notifications, sincronização offline, API mobile** | **⬜ CRÍTICO** |
| **[mobile-testing.md](mobile-testing.md)** | **Pirâmide de testes, E2E, específico por plataforma** | **⬜ CRÍTICO** |
| **[mobile-debugging.md](mobile-debugging.md)** | **Depuração Nativa vs JS, Flipper, Logcat** | **⬜ CRÍTICO** |
| [mobile-navigation.md](mobile-navigation.md) | Tab/Stack/Drawer, deep linking | ⬜ Leia |
| [mobile-typography.md](mobile-typography.md) | Fontes do sistema, Dynamic Type, a11y | ⬜ Leia |
| [mobile-color-system.md](mobile-color-system.md) | OLED, modo escuro, economia de bateria | ⬜ Leia |
| [decision-trees.md](decision-trees.md) | Seleção de framework/estado/armazenamento | ⬜ Leia |

> 🧠 **mobile-design-thinking.md é PRIORIDADE!** Este arquivo garante que a IA pense em vez de usar padrões memorizados.

### Específico por Plataforma (Leia com base no alvo)

| Plataforma | Arquivo | Conteúdo | Quando Ler |
| :--- | :--- | :--- | :--- |
| **iOS** | [platform-ios.md](platform-ios.md) | Human Interface Guidelines, SF Pro, padrões SwiftUI | Criando para iPhone/iPad |
| **Android** | [platform-android.md](platform-android.md) | Material Design 3, Roboto, padrões Compose | Criando para Android |
| **Cross-Platform**| Ambas acima | Pontos de divergência de plataforma | React Native / Flutter |

> 🔴 **Se estiver criando para iOS → Leia platform-ios.md PRIMEIRO!**
> 🔴 **Se estiver criando para Android → Leia platform-android.md PRIMEIRO!**
> 🔴 **Se for cross-platform → Leia AMBOS e aplique lógica condicional por plataforma!**

---

## ⚠️ CRÍTICO: PERGUNTE ANTES DE ASSUMIR (OBRIGATÓRIO)

> **PARE! Se a solicitação do usuário for aberta, NÃO use seus padrões favoritos.**

### Você DEVE perguntar se não for especificado:
- **Plataforma**: "iOS, Android ou ambos?"
- **Framework**: "React Native, Flutter ou nativo?"
- **Navegação**: "Barra de abas, drawer ou baseado em stack?"
- **Estado**: "Qual gerenciamento de estado? (Zustand/Redux/Riverpod/BLoC?)"
- **Offline**: "Precisa funcionar offline?"
- **Dispositivos**: "Apenas celular ou suporte a tablet?"

---

## ⛔ ANTI-PADRÕES MOBILE DA IA (LISTA DE PROIBIÇÕES)

#### Pecados de Performance
- ❌ **ScrollView para listas longas** → Renderiza tudo, a memória explode. Use `FlatList` / `FlashList`.
- ❌ **Função renderItem inline** → Causa re-renders. Use `useCallback` + `React.memo`.
- ❌ **Native driver: false** → Animações lentas. Use `true` sempre.
- ❌ **console.log em produção** → Bloqueia a execução. Remova antes do build.

#### Pecados de Toque/UX
- ❌ **Alvo de toque < 44px** → Impossível tocar com precisão.
- ❌ **Sem estado de carregamento/erro** → Usuário fica perdido sem feedback.
- ❌ **Ignorar convenções de plataforma** → iOS deve parecer iOS, Android deve parecer Android.

#### Pecados de Segurança
- ❌ **Token no AsyncStorage** → Inseguro. Use `SecureStore` / `Keychain`.
- ❌ **API keys no código** → Fácil de extrair. Use variáveis de ambiente.

---

## 📱 Matriz de Decisão de Plataforma

| Elemento | iOS | Android |
| :--- | :--- | :--- |
| **Fonte Primária** | SF Pro | Roboto |
| **Alvo Toque Mínimo** | 44pt × 44pt | 48dp × 48dp |
| **Navegação Voltar** | Edge swipe (borda) | Botão/gesto de sistema |
| **Ícones Tab** | SF Symbols | Material Symbols |
| **Progresso** | Spinner | Progresso linear |

---

## 🧠 Psicologia de UX Mobile (Referência Rápida)

### Lei de Fitts para Toque
- O dedo é impreciso (~7mm). Alvos DEVEM ter 44-48px.
- Ações importantes na **THUMB ZONE** (parte inferior da tela).

### Carga Cognitiva
- No mobile, o usuário é interrompido constantemente. Forneça uma tarefa por vez e salve o progresso.

---

## 📝 CHECKPOINT (OBRIGATÓRIO Antes de Qualquer Trabalho Mobile)

Antes de escrever qualquer código, preencha mentalmente (ou no chat):
1. **Plataforma**: [ iOS / Android / Ambos ]
2. **Framework**: [ React Native / Flutter / SwiftUI / Kotlin ]
3. **Arquivos Lidos**: [ Liste os arquivos de skill lidos ]
4. **3 Princípios que vou aplicar**: [ ... ]
5. **Anti-padrões que vou evitar**: [ ... ]

---

> **Lembre-se:** Usuários mobile são impacientes e usam dedos imprecisos em telas pequenas. Projete para as PIORES condições: rede ruim, uma mão, sol forte, bateria baixa. Se funcionar lá, funcionará em qualquer lugar.
