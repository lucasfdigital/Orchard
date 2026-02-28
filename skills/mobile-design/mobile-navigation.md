# Referência de Navegação Mobile

> Padrões de navegação, deep linking, tratamento do botão voltar e decisões de aba/pilha/drawer.
> **A navegação é o esqueleto do seu app — se errar aqui, nada parecerá correto.**

---

## 1. Árvore de Decisão de Seleção de Navegação

```
QUAL O TIPO DE APP?
        │
        ├── 3-5 seções principais (importância igual)
        │   └── ✅ Barra de Abas / Navegação Inferior (Bottom Nav)
        │       Exemplos: Redes Sociais, E-commerce, Utilitários
        │
        ├── Conteúdo hierárquico profundo (detalhar)
        │   └── ✅ Navegação por Pilha (Stack Navigation)
        │       Exemplos: Configurações, pastas de E-mail
        │
        ├── Muitos destinos (>5 principais)
        │   └── ✅ Navegação por Menu (Drawer)
        │       Exemplos: Gmail, apps corporativos complexos
        │
        ├── Fluxo linear único
        │   └── ✅ Apenas Pilha (assistente/onboarding)
        │       Exemplos: Checkout, fluxo de configuração
        │
        └── Tablet / Dobrável
            └── ✅ Navegação Lateral (Navigation Rail) + Lista-Detalhe
                Exemplos: Mail, Notas no iPad
```

---

## 2. Navegação por Barra de Abas (Tab Bar)

### Melhores Práticas de Tab Bar
- **Capacidade**: Máximo de 5 itens.
- **Rótulos**: Sempre mostre rótulos de texto junto aos ícones (acessibilidade).
- **Preservação de Estado**: **REGRA DE OURO**: Cada aba deve manter seu próprio histórico de navegação. Se o usuário estiver no meio de um processo na Aba A, mudar para a Aba B e voltar para a Aba A, ele deve estar onde parou, não na raiz da aba.

---

## 3. Navegação por Pilha (Stack Navigation)

### Conceitos Centrais
- **Push**: Adiciona uma tela ao topo da pilha.
- **Pop**: Remove a tela do topo (voltar).
- **Replace**: Substitui a tela atual por uma nova.
- **Reset**: Limpa a pilha e define uma nova raiz (root).

### Tratamento do Botão Voltar
- **iOS**: Deslizar da borda esquerda (edge swipe) é o padrão do sistema.
- **Android**: Botão/gesto de voltar do sistema. Android 14+ suporta o "Predictive Back".
- **Regra**: O botão voltar **SEMPRE** volta um nível na pilha. Nunca use para outros propósitos.

---

## 4. Navegação por Menu Lateral (Drawer)

### Quando Usar
- Mais de 5 destinos principais.
- Destinos acessados com menos frequência.
- Apps complexos onde a marca ou info do usuário precisam estar na navegação.
- Tablets onde o menu pode ficar permanentemente visível.

---

## 5. Navegação Modal

### Modal vs Push
- **Push (Pilha)**: Transição horizontal. Faz parte da hierarquia. "Entrar em detalhes".
- **Modal**: Transição vertical (sobe de baixo). Tarefa separada. "Foco na tarefa" (ex: Criar post, Configurações rápidas).

---

## 6. Deep Linking

### Por que Deep Links desde o Dia 1?
- Permite navegação via notificações push.
- Compartilhamento de conteúdo (ex: enviar link de um produto).
- Campanhas de marketing e integração com widgets.
- **Dica**: O caminho da URL deve espelhar o caminho da navegação: `myapp://home/product/123`.

---

## 7. Persistência do Estado de Navegação

O que **DEVE** persistir: aba selecionada, posição de rolagem, rascunhos de formulários e a pilha de navegação recente. Desta forma, se o app for fechado pelo sistema, o usuário volta exatamente para onde estava.

---

## 8. Animações de Transição

Use os padrões nativos da plataforma sempre que possível para garantir a sensação de "fluidez nativa".
- **iOS**: Push desliza da direita, Modal sobe de baixo.
- **Android**: Push tem fade + deslize sutil.
- **Shared Element Transitions**: Use para conectar elementos visualmente entre as telas (ex: a imagem do card expandindo para a imagem do detalhe).

---

## 9. Anti-Padrões de Navegação

- ❌ **Botão voltar inconsistente**: O usuário fica confuso e não sabe para onde voltará.
- ❌ **Navegação escondida**: Funcionalidades que o usuário não encontra.
- ❌ **Pilha de navegação muito profunda**: Mais de 4 níveis sem trilha de navegação (breadcrumbs).
- ❌ **Resetar a aba ao selecioná-la**: Perder o progresso do usuário ao mudar de aba.

---

## 10. Checklist de Navegação

- [ ] Tipo de navegação principal escolhido?
- [ ] Deep links planejados para cada tela importante?
- [ ] Estado das abas é preservado?
- [ ] Botão voltar funciona como esperado em todas as telas?
- [ ] Transições modais vs push usadas corretamente?
- [ ] Testou o "Predictive Back" (Android 14+)?

---

> **Lembre-se:** A navegação é invisível quando bem feita. Os usuários não devem pensar em COMO chegar a algum lugar — eles simplesmente chegam. Se eles notarem a navegação, algo está errado.
