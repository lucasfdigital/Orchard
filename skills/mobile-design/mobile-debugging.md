# Guia de Depuração Mobile

> **Pare de depurar apenas com console.log()!**
> Aplicativos mobile têm camadas nativas complexas. Logs de texto não são suficientes.
> **Este arquivo ensina estratégias eficazes de depuração mobile.**

---

## 🧠 MENTALIDADE DE DEPURAÇÃO MOBILE

```
Depuração Web:        Depuração Mobile:
┌──────────────┐    ┌──────────────┐
│  Navegador   │    │  JS Bridge   │
│  DevTools    │    │  UI Nativa   │
│  Aba Network │    │  GPU/Memória │
│              │    │  Threads     │
└──────────────┘    └──────────────┘
```

**Principais Diferenças:**
1.  **Camada Nativa:** O código JS parece correto, mas o app fecha? Provavelmente é algo nativo (Java/Obj-C).
2.  **Implantação:** Você não pode simplesmente dar um "refresh". O estado se perde ou fica travado.
3.  **Rede:** SSL Pinning e configurações de proxy são mais difíceis.
4.  **Logs do Dispositivo:** `adb logcat` e `Console.app` são a sua única verdade.

---

## 🚫 ANTI-PADRÕES DE DEPURAÇÃO DA IA

| ❌ Padrão da IA | ✅ Correto para Mobile |
| :--- | :--- |
| "Adicione console.logs" | Use Flipper / Reactotron |
| "Verifique a aba network" | Use Charles Proxy / Proxyman |
| "Funciona no simulador" | **Teste no Dispositivo Real** (bugs de hardware) |
| "Reinstale o node_modules" | **Limpe o Build Nativo** (cache do Gradle/Pod) |
| Ignorar logs nativos | Leia o `logcat` / logs do Xcode |

---

## 1. O Conjunto de Ferramentas

### ⚡ React Native & Expo
- **Reactotron**: State/API/Redux. Ótimo para o lado JS.
- **Flipper**: Layout/Network/DB. Ponte Nativa + JS.
- **Expo Tools**: Inspetor de elementos. Checks rápidos de UI.

### 🛠️ Camada Nativa (Mergulho Profundo)
- **Logcat (Android)**: `adb logcat`. Essencial para crashes nativos e ANRs.
- **Console (iOS)**: via Xcode. Exceções nativas e memória.
- **Layout Inspector**: Android Studio / Xcode. Para bugs de hierarquia de UI.

---

## 2. Workflows de Depuração Comuns

### 🕵️ "O App acabou de fechar" (Tela Vermelha vs Fechamento para a Home)

**Cenário A: Tela Vermelha (Erro de JS)**
- **Causa**: Undefined is not an object, erro de importação.
- **Correção**: Leia o stack trace na tela. Geralmente é claro.

**Cenário B: Fechamento Inesperado / Crash para a Home (Erro Nativo)**
- **Causa**: Falha em módulo nativo, falta de memória (OOM), uso de permissão não declarada.
- **Ferramentas**:
    - **Android**: `adb logcat *:E` (Filtra apenas erros).
    - **iOS**: Abra o Xcode → Window → Devices → View Device Logs.

> **💡 Dica Profissional**: Se o app fecha imediatamente ao abrir, é quase 100% um erro de configuração nativa (`Info.plist`, `AndroidManifest.xml`).

---

## 3. Pesadelos Específicos por Plataforma

### Android
- **Falha de Sincronia do Gradle**: Geralmente incompatibilidade de versão do Java ou classes duplicadas.
- **Rede no Emulador**: O `localhost` do emulador é `10.0.2.2`, NÃO `127.0.0.1`.
- **Builds Cacheados**: `./gradlew clean` é seu melhor amigo.

### iOS
- **Problemas de Pod**: `pod deintegrate && pod install`.
- **Erros de Assinatura (Signing)**: Verifique o Team ID e o Bundle Identifier.
- **Cache**: Xcode → Product → Clean Build Folder.

---

## 📝 CHECKLIST DE DEPURAÇÃO

- [ ] **É um crash de JS ou Nativo?** (Tela vermelha ou fechamento total?)
- [ ] **Você limpou o build (clean build)?** (Caches nativos são agressivos)
- [ ] **Está em um dispositivo real?** (Simuladores escondem problemas de simultaneidade)
- [ ] **Verificou os logs nativos?** (Não apenas a saída do terminal)

---

> **Lembre-se:** Se o JavaScript parece perfeito mas o app falha, olhe mais de perto para o lado Nativo.
