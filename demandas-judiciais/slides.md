# Automação de Demandas Judiciais

## RH+ Simples | DIGEPE - FHEMIG

---

# O Desafio Atual

- **Cenário:** Alto volume de processos judiciais (**Série 1080**) na unidade FHEMIG/DIGEPE.
- **Gargalo:** Elevado tempo gasto na triagem manual.
- **Impacto:** Acúmulo de demandas e lentidão na análise de mérito por sobrecarga operacional.

---

# Premissa Técnica Crítica

## "Operação em Background"

- **O Problema:** Abrir o processo manualmente no SEI altera o status (de vermelho para preto).
- **A Solução:** A automação utiliza a **API e Datalake** para extrair dados sem "tocar" na fila visual do técnico.
- **Resultado:** Organização preservada e cronologia de recebimento intacta.

---

<section data-auto-animate>

# Fluxo da Automação (MVP)

<div class="mermaid">
flowchart LR
    A[Datalake SEI] --> B[API SEI]
    B --> C[Webscraping]
    C --> D[(PostgreSQL)]
    D --> E[Graph API]
    E --> F[SharePoint/Email]
</div>

</section>

---

# Arquitetura Proposta

1. **Identificação:** Captura em lote via Datalake.
2. **Extração:** Geração de link externo via API.
3. **Tratamento:** Armazenamento estruturado na Azure.
4. **Entrega:** Planilha automatizada no SharePoint da equipe.

---

## Stack Tecnológica

- **Linguagem:** Python (Playwright + Pandas)
- **Hospedagem:** VM Linux dedicada (Azure)
- **Persistência:** Azure Database for PostgreSQL
- **Integração:** Microsoft Graph API (M365)

---

# Viabilidade Financeira

- **Cota Mensal Azure (FHEMIG):** ~ R$ 65.912,00
- **Consumo do MVP:** ~ R$ 2.000,00
- **Impacto:** Apenas **3%** do orçamento mensal disponível.

---

# Pleitos Institucionais (SEPLAG)

| Recurso | Finalidade |
| --- | --- |
| **API SOAP SEI** | Geração de links externos e árvore processual |
| **Datalake SEI** | Monitoramento massivo de processos 1080 |
| **Datalake SISAP** | Cruzamento com dados funcionais (Fase 2) |

---

# Pleitos Técnicos (TI FHEMIG)

- **Infraestrutura:** Provisionamento de VM e Banco de Dados.
- **Identidade:** Registro no Entra ID (Client ID).
- **Mensageria:** Liberação de Azure Communication Services.
- **Segurança:** Configuração de Firewall para IPs de homologação.

---

# Perspectivas de Evolução

- **Inteligência Artificial:** Análise semântica e sugestão de minutas em Markdown.
- **Integração SISAP:** Respostas instruídas automaticamente com dados funcionais.
- **Automação Ativa:** Tramitação e assinatura via API SEI.

---

# Conclusão

> "A tecnologia liberta o técnico da burocracia para que ele possa exercer sua expertise na análise."

---

# Dúvidas?

## Equipe RH+ Simples | DIGEPE - FHEMIG

Liberações junto à TI
1. Infraestrutura de Hospedagem e Banco de Dados (Ecossistema Azure)
Provisionamento de Máquina Virtual (VM)
Serviço de Banco de Dados

2. Autenticação, Registro e Permissões (Microsoft Entra ID / Graph API)
Registro da Aplicação e Geração de Credenciais
Concessão de Permissões (Sharepoint e Outlook)
(registro de communications services)

3. Solicitação de perfil com privilégios de administração delegada diretamente no painel do Microsoft Azure para a equipe desenvolvedora.
Perfil capaz de Registrar Aplicação e criar VMs
Agilidade e Autonomia para o desenvolvimento do projeto
Governança Preservada (O Azure permite o uso de RBAC (Role-Based Access Control))

Realidade da SEPLAG: 18 sistemas, incluindo ambiente de homologação para cada um, além de diversas automações; aproximadamente custo total de 18.000r. 

Mesma realidade contratual que a da FHEMIG (consumo de créditos azure).

Pedir os prints de custo das VMs e o custo total.
Pedir o contrato.

Reescrever o fluxo 

Escrever sobre a necessidade das liberações de acesso junto à SEPLAG