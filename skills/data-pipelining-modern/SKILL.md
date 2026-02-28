---
name: data-pipelining-modern
description: Engenharia de Dados Moderna. Diretrizes de alto desempenho para pipelines usando Polars, DuckDB, Apache Arrow e dbt. Use para ETL/ELT, modelagem dimensional e processamento de grandes volumes de dados.
allowed-tools: Read, Write, Edit, Bash
version: 1.0
priority: HIGH
---

# Data Pipelining Moderno - Alta Performance e Escalabilidade

> **SKILL DE DADOS** - Transforme dados em inteligência com **velocidade, precisão e baixo custo**.

---

## Princípios de Dados Orchard

| Princípio | Regra |
| :--- | :--- |
| **Idempotência** | Pipelines devem poder ser reexecutados sem duplicidade. |
| **Modelagem OBT** | One Big Table para performance em BI. |
| **Data Contracts** | Schemas definidos e validados entre Produtor e Consumidor. |
| **Colunar > Linha** | Parquet, Arrow e Polars para eficiência de leitura. |

---

## Stack Tecnológica Recomendada

| Ferramenta | Por que usar no Orchard? |
| :--- | :--- |
| **Polars** | Melhores benchmarks in-memory. Substitua o Pandas. |
| **DuckDB** | O "SQLite dos dados". Ideal para OLAP local e transformações leves. |
| **Apache Arrow** | Formato universal para zero-copy data exchange. |
| **dbt** | Módulos SQL, versionamento e documentação em um só lugar. |

---

## Padrões de Arquitetura (Medallion)

| Camada | Missão |
| :--- | :--- |
| **Bronze (Raw)** | Carregamento bruto da origem. Preserve o histórico. |
| **Silver (Cleaned)** | Desduplicação, normalização e tratamento de nulos. |
| **Gold (Business)** | Agregações, KPIs e visões de negócio (Data Marts). |

---

## Melhores Práticas de Performance

| Cenário | Estratégia Recomendada |
| :--- | :--- |
| **Processamento Local** | Use Polars `.lazy()` para otimização automática de queries. |
| **Dados que Excedem RAM** | Use DuckDB com leitura direta de arquivos Parquet em disco. |
| **Incremental Loading** | Carregue apenas os novos registros (`timestamp` da última carga). |
| **Partitioning** | Particione por Data/Ano no S3/GCS para queries rápidas. |

---

## Qualidade e Governança de Dados

| Ação | Ferramenta/Padrão |
| :--- | :--- |
| **Testes de Schema** | Use `pydantic` ou `pandera` para validar tipos e ranges. |
| **Data Lineage** | Mantenha o gráfico de dependência visual do dbt sempre atualizado. |
| **Documentação AI-ready** | Descreva cada coluna no YAML para que a IA possa analisar os dados. |
| **Anonymization** | Mascare PII (RG, CPF, Email) conforme a LGPD. |

---

## Anti-Padrões de Dados (NÃO FAÇA)

| ❌ Padrão | ✅ Correção |
| :--- | :--- |
| Processar tudo em Loop For | Use operações vetorizadas (Pandas/Polars). |
| Chamar API dentro do Loop | Faça chamadas em batch (em massa). |
| Usar CSV para Big Data | Use Parquet ou Avro para compressão e performance. |
| Senha hardcoded no script | Use variáveis de ambiente (.env). |

---

## 🏗️ Exemplo de Pipeline Polars (In-Memory)

```python
import polars as pl

def process_gold_layer():
    # Lazy evaluation = performance máxima
    df = pl.scan_parquet("silver/orders.parquet") \
        .filter(pl.col("status") == "delivered") \
        .group_by("customer_id") \
        .agg(pl.sum("total_amount").alias("lifetime_value")) \
        .collect() # Executa a query otimizada
    
    df.write_parquet("gold/customer_ltv.parquet")
```

---

> 🔴 **"Se o seu pipeline de dados demora mais que 30s para processar 1M de linhas, você precisa otimizar."**

*Transformando dados em valor no projeto Orchard. Licença MIT.*
