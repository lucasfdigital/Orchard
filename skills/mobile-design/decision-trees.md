# Árvores de Decisão Mobile

> Seleção de framework, gerenciamento de estado, estratégia de armazenamento e decisões baseadas em contexto.
> **Estes são GUIAS de PENSAMENTO, não respostas para copiar e colar.**

---

## 1. Seleção de Framework

### Árvore de Decisão Mestre

```
O QUE VOCÊ ESTÁ CONSTRUINDO?
        │
        ├── Precisa de atualizações OTA sem revisão da app store?
        │   │
        │   ├── Sim → React Native + Expo
        │   │         ├── Expo Go para desenvolvimento
        │   │         ├── EAS Update para OTA em produção
        │   │         └── Ideal para: iteração rápida, equipes web
        │   │
        │   └── Não → Continue ▼
        │
        ├── Precisa de UI customizada pixel-perfect em ambas as plataformas?
        │   │
        │   ├── Sim → Flutter
        │   │         ├── Engine de renderização próprio
        │   │         ├── UI idêntica para iOS + Android
        │   │         └── Ideal para: apps visuais, foco na marca
        │   │
        │   └── Não → Continue ▼
        │
        ├── Recursos nativos pesados (ARKit, HealthKit, sensores específicos)?
        │   │
        │   ├── Apenas iOS → SwiftUI / UIKit
        │   │              └── Capacidade nativa máxima
        │   │
        │   ├── Apenas Android → Kotlin + Jetpack Compose
        │   │                  └── Capacidade nativa máxima
        │   │
        │   └── Ambos → Considere nativo com lógica compartilhada
        │              └── Kotlin Multiplatform (KMP) para compartilhamento
        │
        ├── Equipe web existente + codebase em TypeScript?
        │   │
        │   └── Sim → React Native
        │             ├── Paradigma familiar para devs React
        │             ├── Compartilhamento de código com web (limitado)
        │             └── Ecossistema vasto
        │
        └── Empresa com equipe de Flutter existente?
            │
            └── Sim → Flutter
                      └── Aproveita a expertise existente
```

---

## 2. Seleção de Gerenciamento de Estado

### Decisão para React Native

```
QUAL É A COMPLEXIDADE DO SEU ESTADO?
        │
        ├── App simples, poucas telas, estado compartilhado mínimo
        │   │
        │   └── Zustand (ou apenas useState/Context)
        │       ├── Boilerplate mínimo
        │       ├── Fácil de entender
        │       └── Escala bem para médio porte
        │
        ├── Principalmente dados do servidor (orientado à API)
        │   │
        │   └── TanStack Query (React Query) + Zustand
        │       ├── Query para o estado do servidor
        │       ├── Zustand para o estado da UI
        │       └── Excelente cache e refetching
        │
        ├── App complexo com muitas funcionalidades
        │   │
        │   └── Redux Toolkit + RTK Query
        │       ├── Previsível, fácil de depurar
        │       ├── RTK Query para a API
        │       └── Ideal para equipes grandes
        │
        └── Necessidade de estado atômico e granular
            │
            └── Jotai
                ├── Baseado em átomos (como Recoil)
                ├── Minimiza re-renders
                └── Bom para estado derivado
```

---

## 3. Seleção de Padrão de Navegação

```
QUANTOS DESTINOS DE NÍVEL SUPERIOR?
        │
        ├── 2 destinos
        │   └── Considere: Abas superiores ou apenas stack
        │
        ├── 3-5 destinos (importância igual)
        │   └── ✅ Barra de Abas / Navegação Inferior (Bottom Nav)
        │       ├── Padrão mais comum
        │       └── Descoberta fácil
        │
        ├── 5+ destinos
        │   │
        │   ├── Todos importantes → Navegação por Menu (Drawer)
        │   │                   └── Escondido, mas permite muitas opções
        │   │
        │   └── Alguns menos importantes → Híbrido Barra de Abas + Drawer
```

---

## 4. Seleção de Estratégia de Armazenamento

```
QUAL TIPO DE DADOS?
        │
        ├── Sensíveis (tokens, senhas, chaves)
        │   │
        │   └── ✅ Armazenamento Seguro (Secure Storage)
        │       ├── iOS: Keychain
        │       ├── Android: EncryptedSharedPreferences
        │       └── RN: expo-secure-store / react-native-keychain
        │
        ├── Preferências do usuário (configurações, tema)
        │   │
        │   └── ✅ Armazenamento Chave-Valor
        │       ├── iOS: UserDefaults
        │       ├── Android: SharedPreferences
        │       └── RN: AsyncStorage / MMKV
        │
        ├── Dados estruturados (entidades, relacionamentos)
        │   │
        │   └── ✅ Banco de Dados
        │       ├── SQLite (expo-sqlite, sqflite)
        │       ├── Realm (NoSQL, reativo)
        │       └── WatermelonDB (grandes datasets)
        │
        ├── Arquivos grandes (imagens, documentos)
        │   │
        │   └── ✅ Sistema de Arquivos (File System)
        │       ├── iOS: Diretório Documents / Caches
        │       ├── Android: Armazenamento Interno/Externo
```

---

## 5. Seleção de Estratégia Offline

```
QUAL O GRAU DE IMPORTÂNCIA DO OFFLINE?
        │
        ├── Desejável (funciona quando possível)
        │   │
        │   └── Cache dos últimos dados + mostrar dados antigos (stale)
        │       ├── Implementação simples
        │       ├── TanStack Query com staleTime
        │       └── Mostrar timestamp de "última atualização"
        │
        ├── Essencial (funcionalidade core offline)
        │   │
        │   └── Arquitetura Offline-first
        │       ├── Banco de dados local como fonte da verdade
        │       ├── Sincronia com o servidor quando online
        │       ├── Estratégia de resolução de conflitos
        │       └── Fila (queue) de ações para sincronia posterior
```

---

## 6. Seleção de Padrão de Autenticação

```
QUAL TIPO DE AUTH É NECESSÁRIO?
        │
        ├── E-mail/senha simples
        │   │
        │   └── Baseado em Token (JWT)
        │       ├── Armazenar refresh token de forma segura
        │       ├── Access token em memória
        │       └── Fluxo de silent refresh
        │
        ├── Login social (Google, Apple, etc.)
        │   │
        │   └── OAuth 2.0 + PKCE
        │       ├── Usar SDKs da plataforma
        │       ├── Callback via Deep link
        │       └── Apple Sign-In obrigatório para iOS
        │
        └── Biométrico (FaceID, impressão digital)
            │
            └── Auth local + token seguro
                ├── Biometria desbloqueia o token armazenado
                ├── Não substitui a auth do servidor
                └── Fallback para PIN/senha
```

---

## 7. Templates por Tipo de Projeto

### App de E-Commerce
- **Framework**: React Native + Expo (OTA para preços).
- **Navegação**: Barra de abas (Início, Busca, Carrinho, Conta).
- **Estado**: TanStack Query (produtos) + Zustand (carrinho).
- **Armazenamento**: SecureStore (auth) + SQLite (cache de carrinho).

### App Social/Conteúdo
- **Framework**: React Native ou Flutter.
- **Navegação**: Barra de abas (Feed, Busca, Criar, Notificações, Perfil).
- **Estado**: TanStack Query (feed) + Zustand (UI).
- **Armazenamento**: SQLite (cache de feed, rascunhos).

---

## 8. Checklist de Decisão

Antes de iniciar QUALQUER projeto:
- [ ] Plataformas-alvo definidas (iOS/Android/Ambos)?
- [ ] Framework selecionado com base nos critérios?
- [ ] Abordagem de gerenciamento de estado escolhida?
- [ ] Padrão de navegação selecionado?
- [ ] Estratégia de armazenamento para cada tipo de dado?
- [ ] Requisitos offline definidos?
- [ ] Fluxo de Auth desenhado?
- [ ] Deep linking planejado desde o início?

---

## 9. Decisões de Anti-Padrão

| Anti-Padrão | Por que é ruim | Abordagem Melhor |
| :--- | :--- | :--- |
| **Redux para app simples** | Excesso total (overkill) | Zustand ou Context |
| **Nativo para MVP** | Desenvolvimento lento | MVP Multi-plataforma |
| **Drawer para 3 seções** | Navegação escondida | Barra de abas |
| **AsyncStorage para tokens**| Inseguro | Secure Store / Keychain |
| **Ignorar o offline** | Quebra no metrô/elevador | Planeje desde o início |

---

## 10. Referência Rápida

### Escolha Rápida de Framework
- Precisa de OTA? → React Native + Expo.
- UI idêntica? → Flutter.
- Performance máxima? → Nativo.
- Equipe Web? → React Native.
- Protótipo rápido? → Expo.

### Escolha Rápida de Estado
- App simples? → Zustand / Provider.
- Focado em servidor? → TanStack Query / Riverpod.
- Enterprise? → Redux / BLoC.

### Escolha Rápida de Armazenamento
- Segredos/Tokens? → Secure Store / Keychain.
- Configurações? → AsyncStorage / UserDefaults.
- Dados estruturados? → SQLite.
