# Princípios de Design de Schema

> Normalização, chaves primárias, timestamps, relacionamentos.

## Decisão de Normalização

```
Quando normalizar (tabelas separadas):
├── Os dados se repetem em várias linhas
├── As atualizações exigiriam múltiplas mudanças
├── Os relacionamentos são claros
└── Os padrões de consulta (query) se beneficiam

Quando desnormalizar (incorporar/duplicar):
├── Performance de leitura é crítica
├── Os dados raramente mudam
├── Os dados são sempre buscados juntos
└── Queries mais simples são necessárias
```

## Seleção de Chave Primária (Primary Key)

| Tipo | Use Quando |
| :--- | :--- |
| **UUID** | Sistemas distribuídos, segurança |
| **ULID** | UUID + ordenável por tempo |
| **Auto-increment**| Aplicativos simples, banco de dados único |
| **Chave Natural** | Raramente (significado de negócio) |

## Estratégia de Timestamp

```
Para cada tabela:
├── created_at → Quando foi criado
├── updated_at → Última modificação
└── deleted_at → Soft delete (se necessário)

Use TIMESTAMPTZ (com fuso horário), não TIMESTAMP
```

## Tipos de Relacionamento

| Tipo | Quando | Implementação |
| :--- | :--- | :--- |
| **Um-para-Um** | Extensão de dados | Tabela separada com FK |
| **Um-para-Muitos** | Pai-Filhos | FK na tabela filha |
| **Muitos-para-Muitos**| Ambas as partes têm muitos| Tabela de junção (Junction table) |

## Foreign Key ON DELETE

```
├── CASCADE → Excluir os filhos junto com o pai
├── SET NULL → Os filhos tornam-se órfãos (nulos)
├── RESTRICT → Impede a exclusão se existirem filhos
└── SET DEFAULT → Os filhos recebem um valor padrão
```
