# Referência de Psicologia do Toque

> Mergulho profundo em interação por toque, Lei de Fitts para mobile, anatomia da thumb zone, psicologia de gestos e feedback tátil.
> **Este é o equivalente mobile do ux-psychology.md — CRÍTICO para todo trabalho mobile.**

---

## 1. Lei de Fitts para o Toque

### A Diferença Fundamental
No desktop, o cursor é um ponto preciso de 1px. No mobile, o "cursor" é um dedo com cerca de 7mm de diâmetro, o que o torna inerentemente impreciso. Além disso, o dedo oclui (cobre) o alvo durante o toque.

### Tamanhos Mínimos de Alvo
| Plataforma | Mínimo | Recomendado | Uso |
| :--- | :--- | :--- | :--- |
| **iOS (HIG)** | 44pt × 44pt | 48pt+ | Todos os elementos clicáveis |
| **Android (Material)** | 48dp × 48dp | 56dp+ | Todos os elementos clicáveis |
| **Ações Críticas** | - | 56-64px | CTAs principais, ações destrutivas |

**Regra**: O tamanho visual pode ser menor (ex: um ícone de 24px), mas a área de toque (hit area) **DEVE** ter no mínimo 44-48px via padding.

---

## 2. Anatomia da Thumb Zone (Zona do Polegar)

### Uso do Telefone com uma Mão
Pesquisas indicam que ~49% dos usuários seguram o telefone com apenas uma mão.
- **Zona de Fácil Alcance (Arco do Polegar)**: Parte inferior da tela. Coloque aqui os **CTAs PRINCIPAIS** e a Barra de Abas.
- **Zona de Alcance Médio**: Meio da tela. Adequada para conteúdo e ações secundárias.
- **Zona de Difícil Alcance**: Topo da tela. Coloque aqui ações pouco frequentes como Configurações, Perfil ou o botão de Voltar.

---

## 3. Psicologia do Toque vs Clique

- **Feedback Instantâneo**: No toque, a expectativa de resposta é de < 50ms. Se não houver uma mudança visual imediata, o usuário pensará que o app travou.
- **Problema do "Dedo Gordo"**: O feedback visual não deve aparecer apenas sob o dedo (onde fica escondido), mas sim de forma que o usuário perceba a ativação (ex: mudança de cor do botão inteiro).

---

## 4. Psicologia dos Gestos

### O Problema da Descoberta
Gestos são **INVISÍVEIS**. O usuário precisa descobrir ou lembrar que eles existem.
**Solução**: Sempre forneça uma alternativa visível (botão) para ações realizadas por gestos (ex: "swipe para deletar" deve ter um botão de "editar" ou "deletar" em algum lugar).

---

## 5. Padrões de Feedback Tátil (Haptics)

O feedback tátil proporciona uma sensação "premium" e confirmação de ações sem que o usuário precise olhar para a tela.
- **Sucesso**: Padrão de vibração suave (confirmação de tarefa).
- **Erro**: Padrão de vibração de alerta (erro ou ação inválida).
- **Seleção**: Vibração muito leve ao rolar listas ou trocar seleções.

---

## 6. Carga Cognitiva Mobile

- **Hick's Law**: Mais escolhas = decisões mais lentas. No mobile, isso é pior devido à tela pequena. Comece com 3-5 opções e use a "Divulgação Progressiva" (mostrar mais conforme solicitado).
- **Miller's Law**: No desktop lidamos com 7±2 itens. No mobile, reduza para **5±1** devido às constantes interrupções e distrações externas.

---

## 7. Acessibilidade de Toque

- **Espaçamento**: Além do tamanho do alvo (44px+), deve haver pelo menos 8px de distância entre alvos adjacentes para evitar toques acidentais.
- **Alternativas**: Gestos complexos (pinça, drag and drop) devem ter alternativas simples baseadas em toques únicos (taps).

---

## 8. Checklist de Psicologia do Toque

- [ ] Todos os alvos de toque têm no mínimo 44-48px?
- [ ] O CTA principal está na "thumb zone" (parte inferior)?
- [ ] Ações destrutivas estão fora do alcance fácil acidental?
- [ ] Existe alternativa visual para todos os gestos?
- [ ] Feedback tátil (haptics) presente nas ações importantes?
- [ ] Mudança visual imediata ocorre ao tocar em qualquer item?

---

> **Lembre-se:** Cada toque é uma conversa entre o usuário e o dispositivo. Faça com que pareça natural, responsivo e respeitoso com os dedos humanos — não apenas pontos precisos de um cursor.
