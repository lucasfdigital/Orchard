---
name: iac-patterns
description: Padrões de Infraestrutura como Código. Diretrizes para Terraform, Pulumi e CDK com foco em modularidade, segurança e GitOps. Use ao provisionar recursos em nuvens (AWS, GCP, Azure, Oracle).
allowed-tools: Read, Write, Edit, Bash
version: 1.0
priority: HIGH
---

# IaC Patterns - Infraestrutura Moderna como Software

> **SKILL DE INFRAESTRUTURA** - Trate sua nuvem como código: **versionável, testável e imutável**.

---

## Princípios IaC Orchard

| Princípio | Regra |
| :--- | :--- |
| **Idempotência** | O mesmo código deve resultar no mesmo estado, sempre. |
| **Imutabilidade** | Não remende servidores. Destrua e crie novos. |
| **Versionamento** | Cada mudança de infra deve ser um Pull Request (GitOps). |
| **Segurança** | Nenhum segredo (senhas, chaves) deve estar no código. |

---

## Padrões de Projeto (Terraform/HCL)

| Padrão | Aplicação |
| :--- | :--- |
| **Remote State** | Use S3/GCS ou Terraform Cloud para travar o estado. |
| **Modularity** | Crie módulos para recursos repetitivos (ex: `module-vpc`). |
| **Variables** | Use `variables.tf` para inputs e `outputs.tf` para outputs. |
| **Naming** | Use snake_case e nomes descritivos: `aws_instance.web_server`. |

---

## Melhores Práticas de Provedores

| Nuvem | Estratégia Recomendada |
| :--- | :--- |
| **AWS** | Use IAM Roles e Profiles em vez de Access Keys brutas. |
| **GCP** | Use Service Account Impersonation para CI/CD. |
| **Azure** | Use Managed Identities para segurança integrada. |
| **Cloudflare** | Proteja registros DNS e WAF via Terraform. |

---

## Segurança em IaC

| Ação | Ferramenta/Padrão |
| :--- | :--- |
| **Static Analysis** | Use `tfsec` ou `checkov` para encontrar brechas. |
| **Secret Management** | Integre com Vault ou HashiCorp Cloud. |
| **Lowest Privilege** | Aplique o princípio do menor privilégio em tudo. |
| **Audit Log** | Mantenha o CloudTrail ou similar ativo e auditável. |

---

## Anti-Padrões IaC (NÃO FAÇA)

| ❌ Padrão | ✅ Correção |
| :--- | :--- |
| Senhas em `variables` ou `tfvars` | Use Secret Managers ou Variáveis de Ambiente. |
| Recursos sem Tags | Use Tags obrigatórias para FinOps (Custo, Ambiente, Dono). |
| Hardcoding de IDs (VPC, Subnet) | Use `data sources` para buscar IDs dinamicamente. |
| `terraform.tfstate` no Git | Use backend remoto. **URGENTE**. |

---

## 🏗️ Estrutura de Pasta Recomendada

```
infra/
├── modules/ (Recursos reutilizáveis)
│   ├── network/
│   └── database/
├── environments/ (Configurações por ambiente)
│   ├── dev/
│   └── prod/
└── global/ (S3 bucket de estado, IAM compartilhado)
```

---

> 🔴 **"Se você clicou no botão 'Criar' no console da nuvem, você falhou com o Orchard."**

*Elevando a nuvem no projeto Orchard. Licença MIT.*
