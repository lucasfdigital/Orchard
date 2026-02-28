---
name: red-team-tactics
description: Princípios de táticas de Red Team baseados no MITRE ATT&CK. Fases de ataque, evasão de detecção, relatórios.
allowed-tools: Read, Glob, Grep
---

# Táticas de Red Team

> Princípios de simulação de adversários baseados no framework MITRE ATT&CK.

---

## 1. Fases do MITRE ATT&CK

### Ciclo de Vida do Ataque

```
RECONHECIMENTO → ACESSO INICIAL → EXECUÇÃO → PERSISTÊNCIA
       ↓              ↓              ↓            ↓
 ESCALADA PRIV  → EVASÃO DEFESA  → ACESSO CRED  → DESCOBERTA
       ↓              ↓              ↓            ↓
 MOV LATERAL    → COLETA        →   C2   → EXFILTRAÇÃO → IMPACTO
```

### Objetivos da Fase

| Fase | Objetivo |
| :--- | :--- |
| **Reconhecimento (Recon)** | Mapear a superfície de ataque |
| **Acesso Inicial** | Obter o primeiro ponto de apoio |
| **Execução** | Rodar código no alvo |
| **Persistência** | Sobreviver a reinicializações |
| **Escalada de Privilégios** | Obter acesso admin/root |
| **Evasão de Defesa** | Evitar detecção |
| **Acesso a Credenciais** | Coletar credenciais |
| **Descoberta** | Mapear a rede interna |
| **Movimentação Lateral** | Espalhar-se para outros sistemas |
| **Coleta** | Reunir dados do alvo |
| **C2 (Comando e Controle)** | Manter o canal de comando |
| **Exfiltração** | Extrair dados |

---

## 2. Princípios de Reconhecimento

### Passivo vs Ativo

| Tipo | Trade-off (Equilíbrio) |
| :--- | :--- |
| **Passivo** | Sem contato com o alvo, informação limitada |
| **Ativo** | Contato direto, maior risco de detecção |

### Alvos de Informação

| Categoria | Valor |
| :--- | :--- |
| Stack de tecnologia | Seleção do vetor de ataque |
| Informações de funcionários | Engenharia social |
| Faixas de rede | Escopo de escaneamento |
| Terceiros | Ataque na cadeia de suprimentos |

---

## 3. Vetores de Acesso Inicial

### Critérios de Seleção

| Vetor | Quando Usar |
| :--- | :--- |
| **Phishing** | Alvo humano, acesso a e-mail |
| **Exploits públicos** | Serviços vulneráveis expostos |
| **Credenciais válidas** | Vazadas ou quebradas por força bruta |
| **Cadeia de suprimentos** | Acesso através de terceiros |

---

## 4. Princípios de Escalação de Privilégios

### Alvos Windows

| Verificação | Oportunidade |
| :--- | :--- |
| Caminhos de serviço sem aspas | Escrever no caminho (path) |
| Permissões de serviço fracas | Modificar o serviço |
| Privilégios de token | Abusar de SeDebug, etc. |
| Credenciais armazenadas | Coleta |

### Alvos Linux

| Verificação | Oportunidade |
| :--- | :--- |
| Binários SUID | Executar como proprietário |
| Má configuração do Sudo | Execução de comandos |
| Vulnerabilidades de Kernel | Exploits de Kernel |
| Cron jobs | Scripts graváveis |

---

## 5. Princípios de Evasão de Defesa

### Técnicas Principais

| Técnica | Propósito |
| :--- | :--- |
| LOLBins | Usar ferramentas legítimas |
| Ofuscação | Esconder código malicioso |
| Timestomping | Esconder modificações de arquivos |
| Limpeza de logs | Remover evidências |

### Segurança Operacional (OpSec)

- Trabalhe durante o horário comercial.
- Imite padrões de tráfego legítimos.
- Use canais criptografados.
- Misture-se com o comportamento normal do sistema.

---

## 6. Princípios de Movimentação Lateral

### Tipos de Credenciais

| Tipo | Uso |
| :--- | :--- |
| Senha | Autenticação padrão |
| Hash | Pass-the-hash |
| Ticket | Pass-the-ticket |
| Certificado | Autenticação por certificado |

### Caminhos de Movimentação

- Compartilhamentos administrativos.
- Serviços remotos (RDP, SSH, WinRM).
- Exploração de serviços internos.

---

## 7. Ataques ao Active Directory

### Categorias de Ataque

| Ataque | Alvo |
| :--- | :--- |
| Kerberoasting | Senhas de contas de serviço |
| AS-REP Roasting | Contas sem pré-autenticação |
| DCSync | Credenciais do domínio |
| Golden Ticket | Acesso persistente ao domínio |

---

## 8. Princípios de Relatórios

### Narrativa do Ataque

Documente toda a cadeia de ataque:
1. Como o acesso inicial foi obtido.
2. Quais técnicas foram utilizadas.
3. Quais objetivos foram alcançados.
4. Onde a detecção falhou.

### Lacunas de Detecção

Para cada técnica bem-sucedida:
- O que deveria ter detectado?
- Por que a detecção não funcionou?
- Como melhorar a detecção.

---

## 9. Limites Éticos

### Sempre

- Fique dentro do escopo definido.
- Minimize o impacto nos sistemas.
- Reporte imediatamente se encontrar uma ameaça real (não simulada).
- Documente todas as ações.

### Nunca

- Destrua dados de produção.
- Cause negação de serviço (DoS), a menos que definido no escopo.
- Acesse além da prova de conceito necessária.
- Retenha dados sensíveis após o término.

---

## 10. Anti-Padrões

| ❌ NÃO Faça | ✅ Faça |
| :--- | :--- |
| Pressa para exploração | Siga a metodologia |
| Causa de danos | Minimize o impacto |
| Pular relatórios | Documente tudo |
| Ignorar o escopo | Fique dentro dos limites |

---

> **Lembre-se:** O Red Team simula atacantes para melhorar as defesas, não para causar danos.
