# Referência de Tipografia Mobile

> Escala tipográfica, fontes do sistema, Dynamic Type, acessibilidade e tipografia em modo escuro.
> **Falhas tipográficas são a causa número 1 de apps mobile ilegíveis.**

---

## 1. Fundamentos de Tipografia Mobile

### Por que a tipografia mobile é diferente
- **Distância de visão**: 30-40cm no mobile vs 50-70cm no desktop.
- **Viewport**: Estreito e vertical.
- **Ambiente**: Variável (luz do sol, movimento).
- **Controle do Usuário**: O usuário pode aumentar o tamanho da fonte no sistema.

### Regras de Ouro
- **Tamanho mínimo do corpo**: 16px (14pt/14sp).
- **Comprimento de linha**: 40-60 caracteres (evita que o olho se perca).
- **Altura de linha (Line Height)**: 1.4 a 1.6 (mais generoso que no web).
- **Contraste**: Mínimo 4.5:1 (WCAG AA).

---

## 2. Fontes do Sistema

- **iOS (San Francisco / SF Pro)**: Ajuste óptico automático, excelente legibilidade e suporte a Dynamic Type.
- **Android (Roboto)**: Otimizada para telas, suporte a múltiplos pesos e variados idiomas.
- **Dica**: Use fontes do sistema sempre que a eficiência de leitura for prioridade ou quando quiser que o app pareça "nativo".

---

## 3. Escala Tipográfica

Use sempre uma escala modular para manter a harmonia visual:
- **Major Second (1.125)**: Para UIs densas.
- **Major Third (1.250)**: Equilibrado e comum.
- **Exemplo (base 16px)**: 12px, 14px, 16px, 20px, 25px, 31px, 39px.

---

## 4. Dynamic Type / Escalonamento (OBRIGATÓRIO)

### iOS
Sempre use estilos semânticos (`.body`, `.headline`, `.title`) em vez de tamanhos fixos. Isso permite que o app respeite as configurações de acessibilidade do usuário.

### Android
**SEMPRE** use `sp` (scale-independent pixels) para texto. `dp` não escala com a preferência do usuário e quebrará a acessibilidade. Teste o app com o escalonamento em 200%.

---

## 5. Acessibilidade Tipográfica

### Tamanhos Mínimos
- **Corpo do texto**: 16pt/sp.
- **Texto secundário**: 13-14pt/sp.
- **Legendas**: 12pt/sp.
- **BOTÃO**: 14-16pt/sp.
- **JAMAIS** use nada menor que 11pt/sp.

---

## 6. Tipografia em Modo Escuro

- **Evite Branco Puro**: #FFFFFF sobre #000000 causa ofuscamento. Use tons de cinza muito claro (#E0E0E0).
- **Peso (Weight)**: O texto claro sobre fundo escuro parece mais fino. Considere usar um peso maior (Medium em vez de Regular) no modo escuro.

---

## 7. Anti-Padrões de Tipografia

- ❌ **Tamanhos fixos**: Ignora a acessibilidade do sistema.
- ❌ **Contraste baixo**: Cinza claro sobre branco é invisível sob o sol.
- ❌ **Linhas muito longas**: Cansativo de ler.
- ❌ **Altura de linha apertada**: Texto parece "amontoado".

---

## 8. Performance

- **Limite de fontes**: Use no máximo 2-3 arquivos de fonte para evitar lentidão no carregamento.
- **Subset**: Inclua apenas os caracteres necessários (Latin).
- **WOFF2**: Melhor formato para compressão.

---

## 9. Checklist de Tipografia

- [ ] Corpo do texto ≥ 16px/pt/sp?
- [ ] Line height ≥ 1.4?
- [ ] Comprimento de linha ≤ 60 caracteres?
- [ ] Testou com Dynamic Type habilitado (iOS)?
- [ ] Testou com fonte em 200% (Android)?
- [ ] Contraste no modo escuro validado?

---

> **Lembre-se:** Se o usuário não consegue ler seu texto, seu app está quebrado. Tipografia não é decoração — é a interface primária. Teste em dispositivos reais e em condições reais de uso.
