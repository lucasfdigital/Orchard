# Padrões de Teste Mobile

> **O teste mobile NÃO é igual ao teste web. Diferentes restrições, diferentes estratégias.**
> Este arquivo ensina QUANDO usar cada abordagem de teste e PORQUÊ.

---

## 🧠 MENTALIDADE DE TESTE MOBILE

```
O teste mobile difere da web:
├── Dispositivos reais importam (emuladores escondem bugs)
├── Diferenças de plataforma (comportamento iOS vs Android)
├── Condições de rede variam drasticamente
├── Bateria/performance sob estresse
├── Ciclo de vida do app (fundo, encerrado, restaurado)
├── Permissões e diálogos do sistema
└── Interações por toque vs cliques
```

---

## 🚫 ANTI-PADRÕES DE TESTE MOBILE DA IA

| ❌ Padrão da IA | Por que está errado | ✅ Correto para Mobile |
| :--- | :--- | :--- |
| Testar apenas com Jest | Ignora a camada nativa | Jest + E2E no dispositivo |
| Padrões do Enzyme | Obsoleto, focado em web | React Native Testing Library |
| E2E baseado em navegador | Não testa recursos nativos | Detox / Maestro |
| Mockar tudo | Perde bugs de integração | Teste em dispositivo real |
| Ignorar testes de plataforma | iOS/Android diferem | Casos específicos por SO |

---

## 1. Seleção de Ferramentas de Teste

### Árvore de Decisão
- **Funções puras e lógica**: Jest (Unitários).
- **Componentes isolados**: RNTL (React Native) ou `flutter_test` (Flutter).
- **Fluxos completos de usuário**: **Detox** (rápido e confiável para RN) ou **Maestro** (YAML, cross-platform).
- **Performance e Memória**: **Flashlight** (RN) ou Flutter DevTools.

---

## 2. Pirâmide de Testes para Mobile

```
                    ┌───────────────┐
                    │  Testes E2E   │  10%
                    │ (Disp. Real)  │  Lentos, caros, ESSENCIAIS
                    ├───────────────┤
                    │   Integração  │  20%
                    │  (Componente) │  Fluxo + contexto
                    ├───────────────┤
                    │  Componente   │  30%
                    │   (Isolado)   │  UI isolada
                    ├───────────────┤
                    │   Unitários   │  40%
                    │    (Jest)     │  Lógica pura
                    └───────────────┘
```

> 🔴 **Se você tem 90% de cobertura unitária e 0% de E2E, você está testando as coisas erradas.**

---

## 3. Testes Específicos de Plataforma

| Área | Comportamento iOS | Comportamento Android | Testar Ambos? |
| :--- | :--- | :--- | :--- |
| **Voltar** | Edge swipe (borda) | Botão voltar do sistema | ✅ SIM |
| **Permissões** | Pergunta uma vez | Pergunta sempre + rascunho | ✅ SIM |
| **Teclado** | Aparência diferente | Comportamento diferente | ✅ SIM |
| **Deep links** | Universal Links | App Links | ✅ SIM |

---

## 4. Testes Offline e de Rede

### Cenários para Testar
- **Iniciar app offline**: Deve mostrar dados cacheados ou mensagem amigável.
- **Ficar offline durante uma ação**: A ação deve ir para a fila, não ser perdida.
- **Voltar online**: A fila deve sincronizar sem duplicatas.
- **Rede lenta (2G)**: Verificar estados de loading e timeouts.

---

## 5. Testes de Acessibilidade

- **Rótulos**: Todos os elementos interativos têm `accessibilityLabel`.
- **Alvos de Toque**: Mínimo 44x44pt (iOS) / 48x48dp (Android).
- **Leitores de Tela**: Ative o VoiceOver ou TalkBack e tente navegar em todo o app sem olhar para a tela.

---

## 📝 CHECKLIST DE TESTE MOBILE

### Antes do PR
- [ ] Testes unitários para nova lógica.
- [ ] Testes de componente para nova UI.
- [ ] Sem `console.log` nos testes.

### Antes do Lançamento
- [ ] E2E em dispositivo iOS real.
- [ ] E2E em dispositivo Android real.
- [ ] Testado em dispositivo de baixo desempenho (low-end).
- [ ] Cenários offline verificados.
- [ ] Acessibilidade validada.

---

> **Lembre-se:** Um bom teste mobile é testar as coisas CERTAS, não TUDO. Um teste E2E instável é pior do que nenhum teste. Um teste unitário que falha e pega um bug vale mais que 100 testes triviais que passam.
