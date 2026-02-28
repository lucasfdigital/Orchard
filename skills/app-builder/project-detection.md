# Detecção de Tipo de Projeto

> Analisar as solicitações do usuário para determinar o tipo e o template do projeto.

## Matriz de Palavras-Chave

| Palavras-Chave | Tipo de Projeto | Template |
| :--- | :--- | :--- |
| blog, post, artigo | Blog | astro-static |
| e-commerce, produto, carrinho, pagamento | E-commerce | nextjs-saas |
| dashboard, painel, gerenciamento | Painel de Admin | nextjs-fullstack |
| api, backend, serviço, rest | Serviço de API | express-api |
| python, fastapi, django | API Python | python-fastapi |
| mobile, android, ios, react native | App Mobile (RN) | react-native-app |
| flutter, dart | App Mobile (Flutter) | flutter-app |
| portfólio, pessoal, cv | Portfólio | nextjs-static |
| crm, cliente, vendas | CRM | nextjs-fullstack |
| saas, assinatura (subscription), stripe | SaaS | nextjs-saas |
| landing, promocional, marketing | Landing Page | nextjs-static |
| docs, documentação | Documentação | astro-static |
| extensão, plugin, chrome | Extensão de Navegador | chrome-extension |
| desktop, electron | App Desktop | electron-desktop |
| cli, linha de comando, terminal | Ferramenta CLI | cli-tool |
| monorepo, workspace | Monorepo | monorepo-turborepo |

## Processo de Detecção

```
1. Tokenizar a solicitação do usuário
2. Extrair palavras-chave
3. Determinar o tipo de projeto
4. Detectar informações ausentes → encaminhar para o conversation-manager
5. Sugerir stack tecnológica
```
