# Referência de Performance Mobile

> Mergulho profundo em otimização de React Native e Flutter, animações a 60fps, gerenciamento de memória e considerações de bateria.
> **Este arquivo cobre a área número 1 onde o código gerado por IA geralmente FALHA.**

---

## 1. A Mentalidade de Performance Mobile

### Orçamento de Performance (Performance Budget)
Cada quadro (frame) deve ser completado em:
- **60fps → 16.67ms por quadro** (Alvo padrão)
- **120fps → 8.33ms por quadro** (Dispositivos ProMotion/High-refresh)

Se o seu código levar mais tempo: ocorre o "frame drop", resultando em uma rolagem travada (janky) e o usuário perceberá o app como lento ou quebrado.

---

## 2. Performance em React Native

### 🚫 O Erro #1 da IA: ScrollView para Listas
**NUNCA** use `ScrollView` com `.map()` para listas longas. Isso renderiza TODOS os itens imediatamente, explode a memória e trava a rolagem.
**SEMPRE** use `FlatList` ou `FlashList`.

### Checklist de Otimização de FlatList
- [ ] **Memoize** o componente do item com `React.memo`.
- [ ] Use `useCallback` para a função `renderItem`.
- [ ] Use um `keyExtractor` estável (NUNCA use o índice).
- [ ] Forneça `getItemLayout` para itens de altura fixa (evita cálculo de layout assíncrono).
- [ ] Configure `removeClippedSubviews={true}` para economizar memória de itens fora da tela.

### Performance de Animação
Use sempre `useNativeDriver: true`. Isso envia a animação para a thread nativa, garantindo 60fps mesmo se a thread de JS estiver ocupada.
**Nota**: O driver nativo suporta apenas `transform` e `opacity`. Para animações complexas, use a biblioteca **Reanimated 3**.

---

## 3. Performance em Flutter

### 🚫 O Erro #1 da IA: Uso excessivo de setState
O `setState` reconstrói toda a árvore de widgets abaixo dele.
**Soluções**:
- Use o construtor `const` em TODOS os widgets que não dependem de estado.
- Use `ValueListenableBuilder` para reconstruções cirúrgicas.
- No Riverpod, use `.select()` para observar apenas as propriedades necessárias da state.

### Otimização de Imagens
Use `CachedNetworkImage` e defina `memCacheWidth/Height`. Isso evita decodificar imagens em resolução total na memória, o que é a causa principal de crashes por OOM (Out of Memory).

---

## 4. Performance de Animação (Ambas as Plataformas)

| Tipo de Animação | Duração | Easing |
| :--- | :--- | :--- |
| Micro-interação | 100-200ms | ease-out |
| Transição Padrão | 200-300ms | ease-out |
| Transição de Página | 300-400ms | ease-in-out |

**Regra de Ouro**: Anime apenas `transform` e `opacity`. Qualquer outra coisa causa recalculo de layout (muito lento).

---

## 5. Gerenciamento de Memória

A memória de uma imagem = `largura` × `altura` × 4 bytes (RGBA).
Uma imagem 4K consome ~33MB. Dez dessas imagens podem fechar seu app.
**SEMPRE** redimensione imagens para o tamanho de exibição.

---

## 6. Otimização de Bateria

- **Telas OLED**: Pixels pretos (#000000) estão DESLIGADOS. Use preto verdadeiro no modo escuro para economizar bateria.
- **Rede**: Agrupe requisições (batch) e use cache agressivamente para evitar ligar o rádio do celular repetidamente.
- **Localização**: Evite GPS contínuo se não for estritamente necessário.

---

## 7. Performance de Rede

Adote a arquitetura **Offline-First**:
1. Leia do cache PRIMEIRO (UI Instantânea).
2. Busque na rede em segundo plano.
3. Atualize o cache e a UI.

---

## 8. Testes de Performance

| Métrica | Alvo | Ferramenta |
| :--- | :--- | :--- |
| **Taxa de quadros** | ≥ 60fps | Performance Overlay |
| **Início a frio** | < 2s | Cronometragem manual |
| **Memória** | Estável | Profiler (Android Studio/Xcode) |

**IMPORTANTE**: Nunca confie apenas no simulador. Teste sempre em um dispositivo Android de entrada (low-end) e em um iPhone mais antigo.

---

> **Lembre-se:** Performance não é um "extra" — é a qualidade base. Um app lento é um app quebrado. Teste no pior dispositivo que seus usuários possuem, não no melhor que você tem.
