# Scaffolding de Projeto (Estruturação)

> Estrutura de diretórios e arquivos principais para novos projetos.

---

## Estrutura Full-Stack Next.js (Otimizada 2025)

```
nome-do-projeto/
├── src/
│   ├── app/                        # Apenas rotas (camada fina)
│   │   ├── layout.tsx
│   │   ├── page.tsx
│   │   ├── globals.css
│   │   ├── (auth)/                 # Grupo de rotas - páginas de autenticação
│   │   │   ├── login/page.tsx
│   │   │   └── register/page.tsx
│   │   ├── (dashboard)/            # Grupo de rotas - layout do dashboard
│   │   │   ├── layout.tsx
│   │   │   └── page.tsx
│   │   └── api/
│   │       └── [resource]/route.ts
│   │
│   ├── features/                   # Módulos baseados em funcionalidades
│   │   ├── auth/
│   │   │   ├── components/
│   │   │   ├── hooks/
│   │   │   ├── actions.ts          # Server Actions
│   │   │   ├── queries.ts          # Busca de dados (Data fetching)
│   │   │   └── types.ts
│   │   ├── products/
│   │   │   ├── components/
│   │   │   ├── actions.ts
│   │   │   └── queries.ts
│   │   └── cart/
│   │       └── ...
│   │
│   ├── shared/                     # Utilitários compartilhados
│   │   ├── components/ui/          # Componentes de UI reutilizáveis
│   │   ├── lib/                    # Utils, helpers
│   │   └── hooks/                  # Hooks globais
│   │
│   └── server/                     # Código exclusivo do servidor (Server-only)
│       ├── db/                     # Cliente do banco de dados (Prisma)
│       ├── auth/                   # Configuração de autenticação
│       └── services/               # Integrações de APIs externas
│
├── prisma/
│   ├── schema.prisma
│   ├── migrations/
│   └── seed.ts
│
├── public/
├── .env.example
├── .env.local
├── package.json
├── tailwind.config.ts
├── tsconfig.json
└── README.md
```

---

## Princípios de Estrutura

| Princípio | Implementação |
| :--- | :--- |
| **Isolamento de Feature**| Cada funcionalidade em `features/` com seus próprios componentes, hooks e ações |
| **Separação Server/Client**| Código exclusivo do servidor em `server/`, evita importações acidentais no cliente |
| **Rotas Finas** | `app/` apenas para roteamento, a lógica reside em `features/` |
| **Grupos de Rotas** | `(groupName)/` para compartilhamento de layout sem impacto na URL |
| **Código Compartilhado** | `shared/` para UI e utilitários verdadeiramente reutilizáveis |

---

## Arquivos Principais

| Arquivo | Propósito |
| :--- | :--- |
| `package.json` | Dependências |
| `tsconfig.json` | TypeScript + apelidos de caminho (`@/features/*`) |
| `tailwind.config.ts` | Configuração do Tailwind |
| `.env.example` | Template de variáveis de ambiente |
| `README.md` | Documentação do projeto |
| `.gitignore` | Regras de exclusão do Git |
| `prisma/schema.prisma` | Schema do banco de dados |

---

## Apelidos de Caminho (Path Aliases - tsconfig.json)

```json
{
  "compilerOptions": {
    "paths": {
      "@/*": ["./src/*"],
      "@/features/*": ["./src/features/*"],
      "@/shared/*": ["./src/shared/*"],
      "@/server/*": ["./src/server/*"]
    }
  }
}
```

---

## Quando Usar O Quê

| Necessidade | Localização |
| :--- | :--- |
| Nova página/rota | `app/(grupo)/page.tsx` |
| Componente de feature | `features/[nome]/components/` |
| Server action | `features/[nome]/actions.ts` |
| Busca de dados (Data fetch)| `features/[nome]/queries.ts` |
| Botão/input reutilizável | `shared/components/ui/` |
| Consulta ao banco de dados| `server/db/` |
| Chamada de API externa | `server/services/` |
