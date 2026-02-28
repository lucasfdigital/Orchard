# Diretrizes da Plataforma Android

> Fundamentos do Material Design 3, convenções de design Android, tipografia Roboto e padrões nativos.
> **Leia este arquivo ao construir para dispositivos Android.**

---

## 1. Filosofia do Material Design 3 (M3)

### Princípios Core
- **Material como Metáfora**: Superfícies existem em um espaço 3D; luz e sombra definem a hierarquia.
- **Design Adaptativo**: Responde às capacidades do dispositivo e funciona em todos os formatos de tela.
- **Cor Dinâmica**: O sistema gera a paleta de cores a partir do papel de parede (wallpaper) do usuário.
- **Acessível por Padrão**: Grandes alvos de toque, hierarquia clara e cores semânticas.

---

## 2. Tipografia Android

### Família de Fontes Roboto
- **Roboto**: Padrão sans-serif do sistema.
- **sp (Scale-independent Pixels)**: **REGRA**: SEMPRE use `sp` para texto. Ele escala automaticamente com a preferência de tamanho de fonte do usuário.
- **Hierarquia**:
    - **Display**: Para textos hero e splash screens.
    - **Headline**: Títulos de página e seções.
    - **Title**: Diálogos, cards e listas.
    - **Body**: Conteúdo principal.
    - **Label**: Botões, chips e badges.

---

## 3. Sistema de Cores Material

### Cor Dinâmica (Material You)
No Android 12+, o app adapta sua cor primária, secundária e terciária com base no wallpaper do usuário. Implemente isso para que o app tenha um toque personalizado e integrado ao sistema.

### Temas e Elevação
- **Modo Escuro**: O fundo padrão é `#121212`, não preto puro.
- **Elevação**: No Material 3, a elevação é representada por uma sobreposição de cor (tint) mais clara — quanto mais alto o componente, mais clara é a superfície.

---

## 4. Layout e Espaçamento Android

### Grid de 8dp
O Android usa uma grade base de **8dp**. Todo espaçamento deve ser múltiplo de 8:
- **8dp / 16dp / 24dp**: Espaçamentos padrão.
- **4dp**: Meio passo, usado para espaçamentos internos muito próximos.
- **Margens**: 16dp para celulares (compact) e 24dp para tablets.

---

## 5. Padrões de Navegação Android

| Componente | Uso |
| :--- | :--- |
| **Bottom Navigation** | 3 a 5 destinos principais na parte inferior. |
| **Navigation Rail** | Barra vertical lateral para tablets e dobráveis. |
| **Drawer** | Menu lateral escondido para muitos destinos. |
| **Top App Bar** | Título e ações da tela no topo. |

### Botão Voltar (Back)
O Android fornece navegação de voltar via sistema (gesto ou botão). Seu app deve:
- Respeitar a pilha (pop stack) corretamente.
- Suportar animações de "Predictive Back" (Android 14+).
- **Nunca** sequestrar o gesto de voltar para outros fins.

---

## 6. Componentes Material

- **Botões**: Filled (Principal), Tonal (Secundário), Outlined (Terciário) e Text (Baixo foco).
- **FAB (Floating Action Button)**: Botão flutuante para a ação principal da tela. Geralmente no canto inferior direito.
- **Cards**: Superfícies com raio de canto de 12dp.
- **Chips**: Para filtros, tags ou sugestões dinâmicas (altura padrão 32dp).

---

## 7. Padrões Específicos do Android

- **Snackbars**: Mensagens curtas na parte inferior que desaparecem sozinhas.
- **Bottom Sheets**: Superfícies que deslizam de baixo para cima (Modal ou Standalone).
- **Ripple Effect**: **OBRIGATÓRIO**. Todo elemento tocável deve mostrar o efeito de "onda" ao ser pressionado.
- **Pull to Refresh**: Use o indicador circular do Material que puxa o conteúdo para baixo.

---

## 8. Acessibilidade Android

- **TalkBack**: Cada elemento interativo precisa de um `contentDescription` claro.
- **Alvo de Toque**: Mínimo de **48dp × 48dp**, mesmo que o ícone seja menor.
- **Escalabilidade**: Teste sua UI com o tamanho de fonte no máximo (200%).

---

## 9. Checklist Android

- [ ] Usando componentes do Material Design 3?
- [ ] Alvos de toque têm no mínimo 48dp?
- [ ] Efeito Ripple presente em todos os itens clicáveis?
- [ ] Suporte a Cores Dinâmicas implementado?
- [ ] Botão voltar do sistema funciona corretamente?
- [ ] Testado no TalkBack?
- [ ] Layout adaptado para diferentes tamanhos de tela?

---

> **Lembre-se:** Usuários Android esperam o Material Design. Designs customizados que ignoram os padrões Material parecem estranhos e "quebrados". Use os componentes Material como sua fundação e customize com propósito.
