# Padrões de Backend Mobile

> **Este arquivo cobre padrões de backend/API ESPECÍFICOS para clientes mobile.**
> Padrões genéricos de backend estão em `nodejs-best-practices` e `api-patterns`.
> **O backend mobile NÃO é igual ao backend web. Diferentes restrições, diferentes padrões.**

---

## 🧠 MENTALIDADE DE BACKEND MOBILE

```
Clientes mobile são DIFERENTES de clientes web:
├── Rede instável (2G, metrô, elevador)
├── Restrições de bateria (minimizar despertares/wake-ups)
├── Armazenamento limitado (não dá para cachear tudo)
├── Sessões interrompidas (chamadas, notificações)
├── Diversidade de dispositivos (de antigos a flagships)
└── Atualizações de binários são lentas (revisão da App Store)
```

**Seu backend deve compensar TODAS essas variáveis.**

---

## 🚫 ANTI-PADRÕES DE BACKEND MOBILE DA IA

### Estes são erros comuns cometidos quando backends mobile são construídos:

| ❌ Padrão da IA | Por que está errado | ✅ Correto para Mobile |
| :--- | :--- | :--- |
| Mesma API para web e mobile | Mobile precisa de respostas compactas | Endpoints separados ou seleção de campos |
| Respostas de objetos completos | Desperdiça largura de banda e bateria | Respostas parciais, paginação |
| Sem consideração offline | O app trava sem rede | Design offline-first, filas de sincronia |
| WebSocket para tudo | Drena a bateria | Push notifications + fallback para polling |
| Sem versionamento de app | Não pode forçar atualizações | Headers de versão, check de versão mínima |
| Erros genéricos | Usuários não conseguem resolver | Códigos específicos + ações de recuperação |
| Auth baseada em sessão | Apps reiniciam frequentemente | Baseada em token com refresh |

---

## 1. Notificações Push

### Tipos de Push

| Tipo | Caso de Uso | O que o Usuário vê |
| :--- | :--- | :--- |
| **Exibição (Display)** | Nova mensagem, atualização de pedido | Banner de notificação |
| **Silencioso (Silent)** | Sincronia de fundo, atualização de conteúdo| Nada (acontece em segundo plano) |
| **Dados (Data)** | Tratamento personalizado pelo app | Depende da lógica do app |

### Anti-Padrões
- ❌ **JAMAIS** envie dados sensíveis no push. O push diz "Nova mensagem", o app busca o conteúdo.
- ✅ **SEMPRE** gerencie o ciclo de vida do token: o app registra → envia ao backend → o backend limpa tokens inválidos.

---

## 2. Sincronização Offline e Resolução de Conflitos

### Estratégias de Resolução de Conflitos

| Estratégia | Como funciona | Melhor para |
| :--- | :--- | :--- |
| **Last-write-wins** | O timestamp mais recente sobrescreve | Dados simples, usuário único |
| **Server-wins** | O servidor é sempre autoritativo | Transações críticas |
| **Client-wins** | Mudanças offline são prioridade | Apps com foco total em offline |
| **Merge** | Combina as mudanças campo a campo | Documentos, conteúdo rico |
| **CRDT** | Matematicamente livre de conflitos | Colaboração em tempo real |

---

## 3. Otimização de API Mobile

### Técnicas de Redução de Resposta
- **Seleção de campos**: `?fields=id,name,thumbnail`. Economiza 30-70%.
- **Paginação**: Use baseada em **Cursor** para mobile (evita duplicatas se novos itens forem adicionados).
- **Delta Sync**: Envie apenas os registros alterados desde um determinado timestamp.
- **Requisições em Lote (Batch)**: Reduza o número de viagens (round trips).

---

## 4. Versionamento de App

O backend deve expor um endpoint de `/api/app-config` que retorna a `minimum_version` e a `latest_version`. O app compara sua versão atual e pode forçar uma atualização se estiver abaixo da mínima.

---

## 5. Autenticação para Mobile

### Estratégia de Tokens
- **Access Token**: Curta duração, em memória.
- **Refresh Token**: Longa duração, no **SecureStore/Keychain**.
- **Autenticação Silenciosa**: Se o Access Token expirar e houver um Refresh Token válido, o app renova sem que o usuário perceba.

---

## 6. Tratamento de Erros para Mobile

O formato de erro deve incluir um código, uma `user_message` (legível para o usuário) e, se possível, uma `action` (ex: navegar para a tela de pagamento se o cartão foi recusado).

---

## 7. Tratamento de Mídia e Binários

### Otimização de Imagens
- O servidor (ou CDN) deve redimensionar imagens conforme a necessidade do client: `/images/id?w=400&q=80`.
- Use WebP para Android e HEIC/JPEG para iOS.

---

## 8. Segurança para Mobile

- **Atestação de Dispositivo**: Use Play Integrity (Android) ou DeviceCheck (iOS) para garantir que não é um robô/emulador.
- **Assinatura de Requisição**: HMAC para evitar adulteração de dados.
- **Rate Limiting**: Baseie no ID do dispositivo, não apenas no IP.

---

## 9. Monitoramento e Analytics

Headers obrigatórios em cada requisição mobile:
- `X-App-Version`, `X-Platform` (ios|android), `X-OS-Version`, `X-Device-Model`, `X-Device-ID`, `Accept-Language`.

---

## 📝 CHECKLIST DE BACKEND MOBILE

### No Design da API
- [ ] Requisitos específicos mobile identificados?
- [ ] Estratégia de sincronia e offline planejada?
- [ ] Respostas o menores possíveis?
- [ ] Paginação baseada em cursor?

### Autenticação e Versão
- [ ] Refresh token implementado?
- [ ] Endpoint de check de versão pronto?
- [ ] Mecanismo de atualização forçada?

---

> **Lembre-se:** O backend mobile deve ser resiliente a redes ruins, respeitar a vida da bateria e lidar com sessões interrompidas graciosamente. Forneça caminhos claros para recuperação de erros e capacidades offline significativas.
