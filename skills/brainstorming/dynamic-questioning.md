# Geração Dinâmica de Perguntas

> **PRINCÍPIO:** Perguntas não são sobre coletar dados — elas são sobre **revelar consequências arquiteturais**.
>
> Cada pergunta deve se conectar a uma decisão de implementação concreta que afeta o custo, a complexidade ou o cronograma.

---

## 🧠 Princípios Centrais

### 1. Perguntas Revelam Consequências

Uma boa pergunta não é "Qual cor você deseja?", mas sim:

```markdown
❌ RUIM: "Qual método de autenticação?"
✅ BOM: "Os usuários devem se cadastrar com e-mail/senha ou login social?

   Impacto:
   - E-mail/Senha → Necessita de redefinição de senha, hashing, infraestrutura de 2FA
   - Social → Provedores OAuth, mapeamento de perfil de usuário, menos controle

   Trade-off: Segurança vs. Tempo de desenvolvimento vs. Fricção do usuário"
```

### 2. Contexto Antes do Conteúdo

Primeiro, entenda **onde** esta solicitação se encaixa:

| Contexto | Foco da Pergunta |
| :--- | :--- |
| **Greenfield** (novo projeto) | Decisões de fundação: stack, hospedagem, escala |
| **Adição de Funcionalidade** | Pontos de integração, padrões existentes, mudanças que quebram (breaking changes) |
| **Refatoração** | Por que refatorar? Performance? Manutenibilidade? O que está quebrado? |
| **Debug** | Sintomas → Causa raiz → Caminho de reprodução |

### 3. Perguntas Mínimas Viáveis

**PRINCÍPIO:** Cada pergunta deve eliminar uma bifurcação no caminho de implementação.

```
Antes da Pergunta:
├── Caminho A: Fazer X (5 min)
├── Caminho B: Fazer Y (15 min)
└── Caminho C: Fazer Z (1 hora)

Depois da Pergunta:
└── Caminho Confirmado: Fazer X (5 min)
```

Se uma pergunta não reduz os caminhos de implementação → **DELETE-A**.

### 4. Perguntas Geram Dados, Não Suposições

```markdown
❌ SUPOSIÇÃO: "O usuário provavelmente quer Stripe para pagamentos"
✅ PERGUNTA: "Qual provedor de pagamento se adapta melhor às suas necessidades?

   Stripe → Melhor documentação, 2.9% + $0.30, focado nos EUA
   LemonSqueezy → Merchant of Record, 5% + $0.50, taxas globais
   Paddle → Preços complexos, lida com IVA da UE, foco em Enterprise"
```

---

## 📋 Algoritmo de Geração de Perguntas

```
INPUT: Solicitação do usuário + Contexto (greenfield/feature/refactor/debug)
│
├── PASSO 1: Analisar a Solicitação
│   ├── Extrair domínio (ecommerce, auth, realtime, cms, etc.)
│   ├── Extrair funcionalidades (explícitas e implícitas)
│   └── Extrair indicadores de escala (usuários, volume de dados, frequência)
│
├── PASSO 2: Identificar Pontos de Decisão
│   ├── O que DEVE ser decidido antes de codar? (bloqueio)
│   ├── O que PODE ser decidido depois? (adiável)
│   └── O que tem IMPACTO ARQUITETURAL? (alto impacto)
│
├── PASSO 3: Gerar Perguntas (Ordem de Prioridade)
│   ├── P0: Decisões bloqueadoras (não é possível prosseguir sem resposta)
│   ├── P1: Alto impacto (afeta >30% da implementação)
│   ├── P2: Médio impacto (afeta funcionalidades específicas)
│   └── P3: Opcionais (casos de borda, otimização)
│
└── PASSO 4: Formatar Cada Pergunta
    ├── O quê: Pergunta clara
    ├── Por quê: Impacto na implementação
    ├── Opções: Trade-offs (não apenas A vs B)
    └── Padrão (Default): O que acontece se o usuário não responder
```

---

## 🎯 Bancos de Perguntas Específicos por Domínio

### E-Commerce

| Pergunta | Por Que Importa | Trade-offs |
| :--- | :--- | :--- |
| **Vendedor único ou Multi-vendedor?** | Multi-vendedor → Lógica de comissão, dashboards de vendedores, pagamentos divididos | +Receita, -Complexidade |
| **Rastreamento de Inventário?** | Precisa de tabelas de estoque, lógica de reserva, alertas de estoque baixo | +Precisão, -Tempo de desenvolvimento |
| **Produtos Digitais ou Físicos?** | Digital → Links de download, sem envio | Físico → APIs de frete, rastreamento |
| **Assinatura ou Compra Única?** | Assinatura → Faturamento recorrente, dunning, prorrogação | +Receita, -Complexidade |

### Autenticação

| Pergunta | Por Que Importa | Trade-offs |
| :--- | :--- | :--- |
| **Login Social Necessário?** | Provedores OAuth vs. infraestrutura de redefinição de senha | +UX, -Controle |
| **Permissões Baseadas em Role (RBAC)?** | Tabelas de RBAC, aplicação de políticas, UI de admin | +Segurança, -Tempo de desenvolvimento |
| **2FA Obrigatório?** | Infraestrutura TOTP/SMI, códigos de backup, fluxo de recuperação | +Segurança, -Fricção de UX |
| **Verificação de E-mail?** | Tokens de verificação, serviço de e-mail, lógica de reenvio | +Segurança, -Fricção no cadastro |

### Tempo Real

| Pergunta | Por Que Importa | Trade-offs |
| :--- | :--- | :--- |
| **WebSocket ou Polling?** | WS → Escalonamento do servidor, gerenciamento de conexão | Polling → Mais simples, maior latência |
| **Usuários Simultâneos Esperados?** | <100 → Um servidor, >1k → Redis pub/sub, >10k → infra especializada | +Escala, -Complexidade |
| **Persistência de Mensagem?** | Tabelas de histórico, custos de armazenamento, paginação | +UX, -Armazenamento |
| **Efêmero ou Durável?** | Efêmero → Em memória, Durável → Escrita no BD antes de emitir | +Confiabilidade, -Latência |

### Conteúdo/CMS

| Pergunta | Por Que Importa | Trade-offs |
| :--- | :--- | :--- |
| **Rich Text ou Markdown?** | Rich Text → Sanitização, riscos de XSS | Markdown → Simples, sem WYSIWYG |
| **Workflow de Rascunho/Publicação?** | Campo de status, tarefas agendadas, versionamento | +Controle, -Complexidade |
| **Gerenciamento de Mídia?** | Endpoints de upload, armazenamento, otimização | +Funcionalidades, -Tempo de desenvolvimento |
| **Multi-idioma?** | Tabelas de i18n, UI de tradução, lógica de fallback | +Alcance, -Complexidade |

---

## 📐 Template de Pergunta Dinâmica

```markdown
Com base na sua solicitação de [DOMÍNIO] [FUNCIONALIDADE]:

## 🔴 CRÍTICO (Decisões Bloqueadoras)

### 1. **[PONTO DE DECISÃO]**

**Pergunta:** [Pergunta clara e específica]

**Por Que Isso Importa:**
- [Explicar consequência arquitetural]
- [Afeta: custo / complexidade / cronograma / escala]

**Opções:**
| Opção | Prós | Contras | Ideal Para |
| :--- | :--- | :--- | :--- |
| A | [Vantagem] | [Desvantagem] | [Caso de uso] |
| B | [Vantagem] | [Desvantagem] | [Caso de uso] |

**Se Não Especificado:** [Escolha padrão + justificativa]

---

## 🟡 ALTO IMPACTO (Afeta a Implementação)

### 2. **[PONTO DE DECISÃO]**
[Mesmo formato]

---

## 🟢 OPCIONAIS (Casos de Borda)

### 3. **[PONTO DE DECISÃO]**
[Mesmo formato]
```

---

## 🔄 Questionamento Iterativo

### Primeira Passagem (3-5 Perguntas)
Foco em **decisões bloqueadoras**. Não prossiga sem as respostas.

### Segunda Passagem (Após Implementação Inicial)
À medida que os padrões surgem, pergunte:
- "Esta funcionalidade implica [X]. Devemos lidar com [caso de borda] agora ou adiar?"
- "Estamos usando o [Padrão A]. A [Funcionalidade B] deve seguir o mesmo padrão?"

### Terceira Passagem (Otimização)
Quando a funcionalidade estiver funcionando:
- "Gargalo de performance em [X]. Otimizar agora ou está aceitável por enquanto?"
- "Refatorar [Y] para manutenibilidade ou entregar como está?"

---

## 🎭 Exemplo: Geração Completa de Perguntas

```
SOLICITAÇÃO DO USUÁRIO: "Construir um clone do Instagram"

PASSO 1: Analisar
├── Domínio: Rede Social
├── Funcionalidades: Compartilhamento de fotos, engajamento (likes/comentários), perfis de usuário
├── Implicado: Feed, sistema de seguimento, autenticação
└── Escala: Potencialmente alta (apps sociais podem viralizar)

PASSO 2: Pontos de Decisão
├── Bloqueadores: Estratégia de armazenamento, método de autenticação, tipo de feed
├── Alto impacto: Notificações em tempo real, complexidade do modelo de dados
└── Adiáveis: Analytics, busca avançada, reels/vídeo

PASSO 3: Gerar Perguntas (Prioridade)

P0 (Bloqueadores):
1. Estratégia de Armazenamento → Afeta arquitetura, custo, velocidade
2. Algoritmo de Feed → Afeta queries de banco de dados, complexidade
3. Método de Autenticação → Afeta tempo de dev, UX, segurança

P1 (Alto Impacto):
4. Notificações em Tempo Real → WebSocket vs Polling
5. Processamento de Mídia → Otimização no lado do cliente vs servidor

P2 (Adiáveis):
6. Story/Reels → Aumento de escopo considerável, adiar para v2
7. DM/Chat → Subsistema separado, adiar para v2

PASSO 4: Formatar Saída
```

---

## 📊 Saída Gerada (Exemplo)

```
Com base na sua solicitação de clone do Instagram:

## 🔴 DECISÕES CRÍTICAS (Não é possível prosseguir sem respostas)

### 1. **Estratégia de Armazenamento de Fotos**

**Pergunta:** Onde as fotos dos usuários serão armazenadas e servidas?

**Por Que Isso Importa:**
- Afeta: Custos mensais de hospedagem, velocidade de carregamento da página, complexidade de CDN
- Apps sociais de alto volume: 1000 usuários × 10 fotos × 2MB = 20GB de armazenamento

**Opções:**
| Opção | Custo | Velocidade | Complexidade | Ideal Para |
| :--- | :--- | :--- | :--- | :--- |
| **Cloudinary** | $89/mês (25GB) | Rápida (CDN) | Baixa | MVP, lançamento rápido |
| **AWS S3 + CloudFront** | $0.023/GB | Rápida (CDN) | Média | Produção, custo otimizado |
| **Supabase Storage** | Camada gratuita 1GB | Média | Baixa | Escala pequena, simples |
| **Armazenamento Local** | Custo do servidor | Lenta | Baixa | Apenas desenvolvimento |

**Se Não Especificado:** Cloudinary (equilibrado para MVP)

---

### 2. **Escolha de Algoritmo de Feed**

**Pergunta:** Como deve funcionar o feed principal?

**Por Que Isso Importa:**
- Afeta: Complexidade de query de banco de dados, estratégia de caching, tempo de desenvolvimento
- Feeds algorítmicos requerem infraestrutura de ML, sinais de ranking

**Opções:**
| Opção | Complexidade | Impacto no BD | Ideal Para |
| :--- | :--- | :--- | :--- |
| **Cronológico** | Baixa | Query simples | Estágio inicial, transparência |
| **Apenas Seguidores** | Média | JOIN com paginação | Maioria das redes sociais |
| **Algorítmico** | Alta | Tabelas de feed pré-computadas | Concorrente do Instagram |

**Se Não Especificado:** Apenas Seguidores (equilibrado para app social)

---

### 3. **Abordagem de Autenticação**

**Pergunta:** Como os usuários se cadastram e fazem login?

**Por Que Isso Importa:**
- Afeta: Tempo de desenvolvimento (2-5 horas), postura de segurança, fricção de UX

**Opções:**
| Opção | Tempo Dev | Segurança | UX | Ideal Para |
| :--- | :--- | :--- | :--- | :--- |
| **E-mail/Senha** | 4-5 hrs | Alta (com 2FA) | Média | Necessidade de controle total |
| **Apenas Social** | 1-2 hrs | Depende do provedor | Suave | B2C, lançamento rápido |
| **Magic Link** | 2-3 hrs | Média | Muito suave | Foco em segurança |
| **Clerk/Auth0** | 1 hr | Alta | Suave | Rápido para o mercado |

**Se Não Especificado:** Clerk (mais rápido para MVP)

---

## 🟡 ALTO IMPACTO (Afeta Arquitetura)

### 4. **Notificações em Tempo Real**

**Pergunta:** Os usuários precisam de notificações instantâneas para curtidas/comentários?

**Por Que Isso Importa:**
- WebSocket adiciona complexidade de infraestrutura (Redis pub/sub para escala)
- Polling é mais simples, mas tem maior latência

**Opções:**
| Opção | Complexidade | Custo de Escala | Ideal Para |
| :--- | :--- | :--- | :--- |
| **WebSocket + Redis** | Alta | $10+/mês | >1000 usuários simultâneos |
| **Polling (30s)** | Baixa | Queries de BD | <1000 usuários |
| **Sem Tempo Real** | Nenhuma | Nenhum | MVP, validar primeiro |

**Se Não Especificado:** Polling para MVP (adiar WebSocket até validação)

---

## 🟢 OPCIONAIS (Adiar para v2)

### 5. **Suporte a Vídeo/Reels**
- Alta complexidade (processamento de vídeo, infraestrutura de streaming)
- Recomendação: Lançar apenas com fotos, adicionar vídeo após validação.

### 6. **Mensagens Diretas (DMs)**
- Subsistema separado (infraestrutura de chat é diferente do feed)
- Recomendação: Usar Pusher/Stream para tempo real ou adiar inteiramente.

---

## 📋 Resumo

| Decisão | Recomendação | Se Alterado |
| :--- | :--- | :--- |
| Armazenamento | Cloudinary | +3 hrs configuração |
| Feed | Apenas Seguidores | +2 hrs otimização de query |
| Autenticação | Clerk | -3 hrs tempo de dev |
| Tempo Real | Polling | +5 hrs configuração WebSocket |
| Vídeo | Adiar para v2 | N/A |
| DM | Adiar para v2 | N/A |

**Tempo Estimado Total do MVP:** 15-20 horas com as recomendações acima
```

---

## 🎯 Recapitulação de Princípios

1. **Cada pergunta = Decisão arquitetural** → Não é coleta de dados.
2. **Exiba trade-offs** → Para que o usuário entenda as consequências.
3. **Priorize decisões bloqueadoras** → Aquelas sem as quais não é possível prosseguir.
4. **Forneça padrões (defaults)** → Se o usuário não responder, prosseguimos mesmo assim.
5. **Consciência de domínio** → Perguntas de e-commerce ≠ Perguntas de Auth ≠ Perguntas de Tempo Real.
6. **Iterativo** → Novas perguntas surgem à medida que padrões aparecem durante a implementação.
