# Diretrizes da Plataforma iOS

> Fundamentos do Human Interface Guidelines (HIG), convenções de design iOS, tipografia SF Pro e padrões nativos.
> **Leia este arquivo ao construir para iPhones e iPads.**

---

## 1. Filosofia das Human Interface Guidelines (HIG)

### Princípios Core da Apple
- **Clareza (Clarity)**: O texto é legível em todos os tamanhos, os ícones são precisos e o foco está na funcionalidade.
- **Deferência (Deference)**: A UI ajuda as pessoas a entender e interagir com o conteúdo, nunca competindo com ele.
- **Profundidade (Depth)**: Camadas visuais distintas e transições transmitem hierarquia e auxiliam na compreensão.

### Valores de Design
- **Integridade Estética**: O design deve corresponder à função (um app de produtividade deve ser discreto).
- **Manipulação Direta**: O toque deve afetar o conteúdo diretamente (ex: arrastar para mover).
- **Feedback**: As ações devem ser sempre reconhecidas visualmente ou via haptics.

---

## 2. Tipografia iOS

### Família de Fontes SF Pro
- **SF Pro Text**: Para corpo de texto (menor que 20pt).
- **SF Pro Display**: Para títulos grandes (maior ou igual a 20pt).
- **Dynamic Type (OBRIGATÓRIO)**: O iOS escala o texto automaticamente com base nas configurações de acessibilidade do usuário. Use estilos semânticos como `.body`, `.headline` e `.largeTitle`.

---

## 3. Sistema de Cores iOS

### Cores Semânticas
Use cores semânticas para suporte automático ao Modo Escuro:
- **Cores de Texto**: `.label`, `.secondaryLabel`, `.tertiaryLabel`.
- **Cores de Fundo**: `.systemBackground`, `.secondarySystemBackground`.
- **Cores de Destaque**: Use os tons padrão do sistema (Blue, Green, Red, etc.) que se ajustam automaticamente entre os modos claro e escuro.

---

## 4. Layout e Espaçamento iOS

### Safe Areas
**REGRA**: Nunca coloque conteúdo interativo fora da Safe Area. Respeite o espaço do entalhe (notch), da Dynamic Island e do Home Indicator na parte inferior.

### Margens Padrão
- **Margem Horizontal**: 16pt da borda da tela.
- **Espaçamento Mínimo**: Múltiplos de 8pt são recomendados para manter a consistência.

---

## 5. Padrões de Navegação iOS

| Padrão | Uso |
| :--- | :--- |
| **Tab Bar** | 3 a 5 seções principais na parte inferior (altura 49pt). |
| **Navigation Bar** | Título centralizado e ações no topo (altura 44pt). |
| **Modal (Sheet)** | Tarefas focadas ou interrupções; desliza de baixo para cima. |
| **Edge Swipe** | Deslizar da borda esquerda para voltar (padrão do sistema). |

---

## 6. Componentes iOS

- **Botões**: Use os estilos nativos (Filled, Tinted, Gray, Plain). Mínimo de 44pt de altura para alvos de toque.
- **Listas e Tabelas**: Estilos `Plain`, `Grouped` ou `InsetGrouped` (o padrão moderno com cantos arredondados).
- **Segmented Controls**: Para alternar entre 2 a 5 visualizações relacionadas.

---

## 7. Padrões Específicos do iOS

- **Pull to Refresh**: Use o `UIRefreshControl` nativo (spinner de sistema).
- **Swipe Actions**: Deslizar para a esquerda em listas para ações destrutivas (vermelho) ou para a direita para ações construtivas.
- **Context Menus**: Ativados por pressão longa; mostram um preview do conteúdo e uma lista de ações.

---

## 8. SF Symbols

A biblioteca da Apple com mais de 5000 ícones.
- **Pesos**: Devem corresponder ao peso do texto (Regular, Bold, etc.).
- **Escalas**: Small, Medium e Large conforme o destaque necessário na UI.

---

## 9. Acessibilidade iOS

- **VoiceOver**: Cada elemento interativo precisa de um `accessibilityLabel` claro e um `accessibilityRole`.
- **Dynamic Type**: O app **DEVE** escalar graciosamente de xSmall até tamanhos de acessibilidade gigantes.
- **Reduce Motion**: Respeite a preferência de animações reduzidas do usuário.

---

## 10. Checklist iOS

- [ ] Usando SF Pro e SF Symbols?
- [ ] Suporte a Dynamic Type implementado corretamente?
- [ ] Safe Areas e Home Indicator respeitados?
- [ ] Gesto de voltar (edge swipe) funciona em todo o app?
- [ ] Alvos de toque têm no mínimo 44pt?
- [ ] Modo Escuro testado e validado?
- [ ] Keyboard avoidance (evitar que o teclado cubra inputs) funcionando?

---

> **Lembre-se:** Usuários iOS têm expectativas fortes. Desviar dos padrões HIG passa a sensação de app "quebrado". Na dúvida, use o componente nativo.
