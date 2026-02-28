# Referência de Psicologia de UX

> Mergulho profundo em leis de UX, design emocional, construção de confiança e psicologia comportamental.

---

## 1. Leis Centrais de UX

### Lei de Hick

**Princípio:** O tempo para tomar uma decisão aumenta logaritmicamente com o número de escolhas.

```
Tempo de Decisão = a + b × log₂(n + 1)
Onde n = número de escolhas
```

**Aplicação:**
- Navegação: Máximo de 5 a 7 itens de nível superior.
- Formulários: Quebre em etapas (divulgação progressiva - progressive disclosure).
- Opções: Use seleções padrão (defaults) quando possível.
- Filtros: Priorize os mais usados, esconda os avançados.

---

### Lei de Fitts

**Princípio:** O tempo para atingir um alvo é uma função da distância e do tamanho do alvo.

```
MT = a + b × log₂(1 + D/W)
Onde D = distância, W = largura
```

**Aplicação:**
- CTAs: Torne os botões primários maiores (mínimo 44px de altura).
- Alvos de toque: Mínimo de 44×44px no mobile.
- Posicionamento: Ações importantes próximas à posição natural do cursor.
- Cantos: "Cantos mágicos" (borda infinita = fácil de acertar).

---

### Lei de Miller

**Princípio:** A pessoa média consegue reter 7±2 itens na memória de trabalho.

**Aplicação:**
- Listas: Agrupe em blocos de 5 a 7 itens.
- Navegação: Máximo de 7 itens no menu.
- Conteúdo: Quebre conteúdos longos com títulos.
- Números de telefone: 555-123-4567 (agrupado).

---

### Efeito Von Restorff (Efeito de Isolamento)

**Princípio:** Um item que se destaca tem mais probabilidade de ser lembrado.

**Aplicação:**
- Botões de CTA: Cor distinta de outros elementos.
- Preços: Destaque o plano recomendado.
- Info importante: Diferenciação visual.
- Novas funcionalidades: Selo (badge) ou destaque (callout).

---

### Efeito de Posição Serial

**Princípio:** Itens no início (primazia) e no fim (recência) de uma lista são mais bem lembrados.

**Aplicação:**
- Navegação: Itens mais importantes primeiro e por último.
- Listas: Informações chave no topo e no final.
- Formulários: Campos mais críticos no início.
- CTAs: Repita no topo e no final de páginas longas.

---

### Lei de Jakob

**Princípio:** Os usuários passam a maior parte do tempo em outros sites. Eles preferem que seu site funcione da mesma maneira que todos os outros sites que eles já conhecem.

**Aplicação:**
- **Padrões:** Use posicionamento padrão para barras de busca e carrinhos.
- **Modelos Mentais:** Aproveite ícones familiares (ex: lupa para busca).
- **Vocabulário:** Use "Entrar" (Log In) em vez de "Acessar o Portal".
- **Layout:** Mantenha o logo no topo à esquerda para navegação "Início".
- **Interação:** Deslizar para a direita para voltar/próximo deve parecer nativo.

---

### Lei de Tesler (Conservação da Complexidade)

**Princípio:** Para qualquer sistema, existe uma certa quantidade de complexidade que não pode ser reduzida, apenas deslocada do usuário para o software.

**Aplicação:**
- **Backend:** Deixe o sistema lidar com a formatação (ex: moeda).
- **Detecção:** Detecte automaticamente o tipo de cartão ou a cidade via CEP.
- **Automação:** Pré-preencha dados de usuários recorrentes.
- **Personalização:** Mostre apenas campos relevantes com base em respostas anteriores.

---

### Lei de Parkinson

**Princípio:** Qualquer tarefa se expandirá até que todo o tempo disponível seja gasto.

**Aplicação:**
- **Eficiência:** Use "Salvamento automático" para reduzir o tempo de conclusão da tarefa.
- **Velocidade:** Limite os passos em um funil de conversão.
- **Feedback:** Validação em tempo real para evitar que usuários percam tempo com erros.

---

### Limite de Doherty (Doherty Threshold)

**Princípio:** A produtividade dispara quando um computador e seus usuários interagem em um ritmo (<400ms) que garante que nenhum dos dois tenha que esperar pelo outro.

**Aplicação:**
- **Feedback:** Use pistas visuais imediatas para cliques.
- **Carregamento:** Use skeleton screens para performance perceptível.
- **Otimismo:** Atualize a UI antes da resposta do servidor (Optimistic UI).
- **Movimento:** Use micro-animações para mascarar pequenos atrasos.

---

### Lei de Postel (Princípio da Robustez)

**Princípio:** Seja conservador no que você faz, seja liberal no que você aceita dos outros.

**Aplicação:**
- **Tratamento de Erros:** Não aponte erro por um espaço ou hífen faltando.
- **Formatação:** Aceite datas em DD/MM/AAAA ou MM/DD/AAAA.
- **Busca:** Aceite erros de digitação e forneça sugestões de "Você quis dizer...?".

---

### Navalha de Occam (Occam’s Razor)

**Princípio:** Entre hipóteses concorrentes que explicam igualmente bem, a que tiver menos suposições deve ser selecionada. A solução mais simples é geralmente a melhor.

**Aplicação:**
- **Lógica:** Remova cliques desnecessários.
- **Visual:** Use apenas a quantidade de fontes/cores estritamente necessária.
- **Cópia (Copy):** Use o texto mais curto possível para transmitir o significado.

---

## 2. Percepção Visual (Princípios de Gestalt)

### Lei da Proximidade

**Princípio:** Objetos que estão próximos uns dos outros tendem a ser agrupados.

**Aplicação:**
- **Agrupamento:** Mantenha os rótulos (labels) fisicamente próximos aos campos de entrada.
- **Espaçamento:** Margens maiores entre blocos de conteúdo não relacionados.
- **Formulários:** Agrupe campos de Endereço, separe-os dos campos de Cartão de Crédito.

---

### Lei da Semelhança

**Princípio:** O olho humano tende a perceber elementos similares em um design como uma imagem completa, forma ou grupo, mesmo que esses elementos estejam separados.

**Aplicação:**
- **Consistência:** Cores consistentes para todos os links clicáveis.
- **Iconografia:** Todos os ícones de um conjunto devem ter o mesmo peso de traço.
- **Botões:** Mesma forma/tamanho para botões com a mesma importância.

---

### Lei da Região Comum (Common Region)

**Princípio:** Elementos tendem a ser percebidos em grupos se compartilharem uma área com uma borda claramente definida.

**Aplicação:**
- **Containerização:** Use cards para agrupar imagens e títulos.
- **Bordas:** Use linhas para separar a barra lateral do feed principal.
- **Modais:** Use uma caixa distinta para separar pop-ups da página.

---

### Lei da Conectividade Uniforme (Uniform Connectedness)

**Princípio:** Elementos que estão conectados visualmente (ex: via linhas, setas) são percebidos como mais relacionados do que elementos sem conexão.

**Aplicação:**
- **Fluxo:** Use linhas para conectar as etapas de um assistente de progresso (wizard).
- **Menus:** Dropdowns que "tocam" ou se conectam ao botão pai.
- **Hierarquia:** Estruturas em árvore para diretórios de arquivos.

---

### Lei de Prägnanz (Simplicidade)

**Princípio:** As pessoas perceberão e interpretarão imagens ambíguas ou complexas da forma mais simples possível, pois é a interpretação que exige o menor esforço cognitivo.

**Aplicação:**
- **Clareza:** Use ícones geométricos claros para navegação.
- **Redução:** Remova texturas 3D ou sombras desnecessárias.
- **Formas:** Prefira retângulos/círculos padrão em vez de polígonos complexos.

---

### Lei de Figura/Fundo (Figure/Ground)

**Princípio:** O olho diferencia um objeto da área ao redor. Uma forma, silhueta ou contorno é percebido como figura (objeto), enquanto a área ao redor é percebido como fundo.

**Aplicação:**
- **Foco:** Use sobreposições (scrims) para modais destacarem o conteúdo.
- **Profundidade:** Sombras projetadas (drop shadows) para sugerir que a "figura" está acima do "fundo".
- **Desfoque (Blur):** Use desfoque de fundo para enfatizar o texto em primeiro plano.

---

### Lei do Ponto Focal (Focal Point)

**Princípio:** O que se destacar visualmente irá capturar e prender a atenção do espectador primeiro.

**Aplicação:**
- **Entrada:** Coloque a proposta de valor primária no ponto focal.
- **Cor:** Use uma "Cor de Ação" de alta vibração contra uma UI neutra.
- **Tamanho:** A estatística mais importante deve ter a maior fonte.
- **Tipografia:** Use pesos em negrito (bold) para cabeçalhos.

---

## 3. Vieses Cognitivos & Comportamento

### Efeito Zeigarnik

**Princípio:** As pessoas lembram-se melhor de tarefas não concluídas ou interrompidas do que de tarefas concluídas.

**Aplicação:**
- **Gamificação:** Use barras de "Perfil 60% completo".
- **Engajamento:** Mostre o próximo módulo em um caminho de aprendizado.
- **Retenção:** Exiba uma lista de "Afazeres" de funcionalidades ainda não exploradas.

---

### Efeito de Gradiente de Meta (Goal Gradient Effect)

**Princípio:** A tendência de se aproximar de uma meta aumenta com a proximidade da mesma.

**Aplicação:**
- **Progresso:** Divida um formulário de 10 campos em duas etapas de 5 campos.
- **Feedback:** Celebre marcos na metade de uma tarefa.
- **Motivação:** Mostre ao usuário quão perto ele está de uma recompensa/status.

---

### Regra do Pico-Fim (Peak-End Rule)

**Princípio:** As pessoas julgam uma experiência em grande parte com base em como se sentiram no seu pico (o ponto mais intenso) e no seu fim, em vez da soma total ou média de cada momento.

**Aplicação:**
- **Sucesso:** Torne a tela de "Pedido Confirmado" memorável.
- **Deleite:** Adicione confetes ou uma animação única no ponto de valor.
- **Error Handling:** Transforme uma página 404 em uma interação divertida e útil.

---

### Efeito Estética-Usabilidade

**Princípio:** Os usuários costumam perceber um design esteticamente agradável como um design mais utilizável.

**Aplicação:**
- **Confiança:** Visuais de alta fidelidade ganham "crédito de confiança" para bugs menores.
- **Engajamento:** Interfaces bonitas mantêm os usuários explorando por mais tempo.
- **Paciência:** Usuários são mais tolerantes com tempos de carregamento se a UI for atraente.

---

### Viés de Ancoragem (Anchoring Bias)

**Princípio:** Os usuários dependem fortemente da primeira informação oferecida (a "âncora") ao tomar decisões.

**Aplicação:**
- **Preços:** Mostre o preço original riscado.
- **Níveis (Tiers):** Coloque o plano "Enterprise" mais caro na extrema esquerda.
- **Destaque:** Marque o plano "Mais Popular" como a primeira recomendação.

---

### Prova Social (Social Proof)

**Princípio:** As pessoas copiam as ações dos outros na tentativa de adotar um comportamento em uma determinada situação.

**Aplicação:**
- **Validação:** Exiba "Junte-se a mais de 50.000 pessoas".
- **Avaliações:** Classificações por estrelas e depoimentos de clientes verificados.
- **Logos:** Seção "Confiado por" exibindo marcas parceiras.

---

### Princípio da Escassez (Scarcity Principle)

**Princípio:** Os seres humanos atribuem um valor mais alto a um objeto que é escasso e um valor mais baixo àqueles que estão em abundância.

**Aplicação:**
- **Urgência:** "Restam apenas 2 itens em estoque".
- **Tempo:** Cronômetros de contagem regressiva para promoções.
- **Acesso:** Betas apenas para convidados ou níveis exclusivos.

---

### Viés de Autoridade

**Princípio:** A tendência de atribuir maior precisão à opinião de uma figura de autoridade e ser mais influenciado por essa opinião.

**Aplicação:**
- **Especialismo:** Use "Verificado por Especialistas" ou fotos profissionais.
- **Certificações:** Selos de confiança (SSL, ISO, HIPAA).
- **Mídia:** Logos de "Como visto no TechCrunch/Forbes".

---

### Aversão à Perda (Loss Aversion)

**Princípio:** As pessoas geralmente preferem evitar perdas a adquirir ganhos equivalentes. É melhor não perder R$5 do que encontrar R$5.

**Aplicação:**
- **Mensagens:** "Não perca seu desconto".
- **Testes:** "Seu teste gratuito está terminando — mantenha seus dados agora".
- **Fidelidade:** "Você ganhou 500 pontos — não deixe que eles expirem".

---

### Efeito do Falso Consenso

**Princípio:** As pessoas tendem a superestimar o quanto suas próprias opiniões, crenças e hábitos são normais e típicos dos outros.

**Aplicação:**
- **Testes:** Você não é o usuário — teste com públicos-alvo reais.
- **Pesquisa:** Use dados qualitativos (entrevistas) e quantitativos (analytics).
- **Objetividade:** Use mapas de calor (heatmaps) para ver o comportamento real do usuário.

---

### Maldição do Conhecimento

**Princípio:** Um viés cognitivo que ocorre quando um indivíduo, ao se comunicar com outros, assume inconscientemente que eles têm a base necessária para entender.

**Aplicação:**
- **Copy:** Evite jargões e use linguagem clara e simples.
- **Onboarding:** Tutoriais que assumem que o usuário não sabe nada.
- **Estrutura:** Divulgação progressiva (progressive disclosure) para esconder configurações avançadas.

---

### Efeito de Degrau (Foot-in-the-Door)

**Princípio:** Os usuários se comprometem com tarefas grandes se começarem com as pequenas.

**Aplicação:**
- **Funil:** Peça o e-mail antes de pedir o cartão de crédito.
- **Engajamento:** Peça uma preferência (ex: "Modo Escuro?") antes do registro.
- **Pesquisa:** Comece com uma pergunta simples de "Sim/Não".

---

## 4. Design Emocional (Don Norman)

### Três Níveis de Processamento

```
┌─────────────────────────────────────────────────────────────┐
│  VISCERAL (Cérebro Primitivo)                               │
│  ────────────────────────────                               │
│  • Reação imediata e automática                             │
│  • Primeiras impressões (primeiros 50ms)                    │
│  • Estética: cores, formas, imagens                         │
│  • "Uau, isso parece lindo!"                                │
├─────────────────────────────────────────────────────────────┤
│  COMPORTAMENTAL (Cérebro Funcional)                         │
│  ──────────────────────────────────                         │
│  • Usabilidade e função                                     │
│  • Prazer no uso eficaz                                      │
│  • Performance, confiabilidade, facilidade                  │
│  • "Isso funciona exatamente como eu esperava!"             │
├─────────────────────────────────────────────────────────────┤
│  REFLEXIVO (Cérebro Consciente)                              │
│  ──────────────────────────────                             │
│  • Pensamento consciente e significado                       │
│  • Identidade pessoal e valores                             │
│  • Memória de longo prazo e fidelidade                      │
│  • "Esta marca representa quem eu sou"                      │
└─────────────────────────────────────────────────────────────┘
```

---

## 5. Sistema de Construção de Confiança

### Categorias de Sinais de Confiança

| Categoria | Elementos | Implementação |
| :--- | :--- | :--- |
| **Segurança** | SSL, selos, criptografia | Cadeado visível, logos de segurança em forms|
| **Prova Social** | Avaliações, depoimentos, logos| Estrelas, fotos de clientes, logos de marcas |
| **Transparência** | Políticas, preços, contato | Links claros, sem taxas ocultas, endereço real|
| **Profissional** | Qualidade do design, consistência| Sem links quebrados, branding consistente |
| **Autoridade** | Certificações, prêmios, mídia | "Como visto em...", certificações da indústria|

---

> **Lembre-se**: A psicologia de UX não é sobre manipulação, mas sobre entender o comportamento humano para criar experiências que pareçam naturais, intuitivas e gratificantes para o usuário.
