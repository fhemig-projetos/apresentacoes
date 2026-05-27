# Automação de Demandas Judiciais

## RH+ Simples | DIGEPE - FHEMIG

---

# O Desafio Atual

- **Cenário:** Alto volume de processos judiciais na unidade FHEMIG/DIGEPE.
- **Gargalo:** Elevado tempo gasto na triagem manual.
- **Impacto:** Acúmulo de demandas e lentidão na análise por sobrecarga operacional.

---

# Premissa Técnica Crítica

## "Operação em Background"

- **O Problema:** Abrir o processo manualmente no SEI altera o status (de vermelho para preto).
- **A Solução:** A automação utilizar a **API e Datalake do SEI** para extrair dados sem "tocar" na fila visual do técnico.
- **Resultado:** Organização preservada e cronologia de recebimento intacta.

---

<section data-auto-animate>

# Fluxo da Automação

</section>

<section data-auto-animate>

<div class="mermaid">
flowchart LR
    A(Listagem de Processos da unidade DIGEPE<br><br><strong>Datalake SEI</strong>) --> B(Geração de Links Externos<br><br><strong>API SEI</strong>)
    B --> C(Extração de Documentos<br><br><strong>Python + Playwright</strong>)
    C --> D[(Armazenamento de Dados<br><br><strong>Azure PostgreSQL</strong>)]
    D --> E(Geração Automatizada de Planilhas<br><br><strong>Python + Pandas</strong>)
    E --> F(Distribuição para Técnicos<br><br><strong>Microsoft Graph API</strong>)
</div>

</section>

---

# Stack Tecnológica

- **Linguagem:** Python (Playwright + Pandas)
- **Hospedagem:** VM Linux dedicada (Azure)
- **Persistência:** Azure Database for PostgreSQL
- **Integração:** Microsoft Graph API (M365)

---

# Pleitos Técnicos (TI FHEMIG)

- **Ambiente:** Provisionamento de VM e Banco de Dados.
- **API da Microsoft:** Registro da aplicação no Entra ID (geração de Client ID) com as devidas permissões.
- **Envio de e-mails de forma impessoal:** Azure Communication Services.

--

## Solicitação de perfil com acesso ao Painel dos serviços Azure
- Perfil com privilégios de **administração delegada** diretamente no painel do Microsoft Azure.
- Perfil capaz de **Registrar Aplicação e criar VMs**.
- **Agilidade e autonomia** para o desenvolvimento do projeto.
- **Governança Preservada**: O Azure permite o uso de RBAC (Role-Based Access Control).

> Em benchmarking com a TI da SEPLAG, foi demonstrado que é possível criar perfis com acesso a apenas determinados serviços dentro do Painel Admin Azure.

--

## Viabilidade Financeira

- **Cota Mensal Azure (FHEMIG):** ~ R$ 65.912,00 em créditos azure.
- **Consumo do MVP:** ~ R$ 2.000,00 
- **Impacto:** Apenas **3%** do orçamento mensal disponível.
- **Estimativas**: Pricing público da Microsoft e contrato FHEMIG/Microsoft.

> O contrato corporativo do Estado garante custos efetivos ainda menores. 

--

## Detalhamento dos custos
- **VM Linux**:  R$ 576,24
- **Azure Database for PostgreSQL**: R$ 1331,75 + R$ 1,50 x total GB contratados
    - Serviço de backup já incluso
- **Microsoft Graph API**: sem custos (tanto o registro da aplicação, quanto a realização das requisições)

--

## Benchmarking SEPLAG
- Benchmarking realizado junto à Diretoria de Desenvolvimento Tecnológico (SEPLAG/MG)
- **Benchmarking SEPLAG:**
  - **18 sistemas completos** (Homologação e Produção).
  - Bancos de dados hospedados nas próprias VMs.
  - Múltiplos ambientes de automação operando simultaneamente.
  - **Custo Total da Diretoria (SEPLAG):** ~ R$ 18.000,00/mês.

---

# Pleitos Institucionais (SEPLAG)

| Recurso | Finalidade |
| --- | --- |
| **API SOAP SEI** | Geração de links externos e construção da árvore processual |
| **Datalake SEI** | Extração e monitoramento massivo de processos SEI |
| **Datalake SISAP** | Cruzamento com dados funcionais |

> E-mail para solicitação dos acessos já encaminhado e ofícios para solicitação já elaborados **(aguardando validação)**.

---

# Perspectivas de Evolução

- **Inteligência Artificial:** Análise semântica e sugestão de minutas.
- **Integração SISAP:** Respostas instruídas automaticamente com dados funcionais.
- **Automação Ativa:** Construção dos documentos da árvore processual e tramitação dos Processos via API SEI.

---

# Dúvidas?

## Equipe RH+ Simples | DIGEPE - FHEMIG



<!-- Liberações junto à TI
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

Escrever sobre a necessidade das liberações de acesso junto à SEPLAG -->