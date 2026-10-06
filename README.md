# Banking Experience API - Mobile (SOAP)

API da camada **Experience** (canal mobile) do projeto de Mobile & Internet Banking do Standard Bank Angola, desenvolvida em **MuleSoft** com protocolo **SOAP**.
Denominada **ASE**.

Esta API expõe as funcionalidades do app mobile, simplificando e formatando as respostas vindas da [Process API](../banking-process-api-soap) para consumo direto pela aplicação.

```
[App Mobile] → [Experience Mobile API] → [Process API] → [System API] → [PostgreSQL]
                        ▲
                   (este projeto)
```

## Operações disponíveis

| Operação | Descrição |
|---|---|
| `viewDashboard` | Ecrã inicial: contas, saldos e últimos movimentos |
| `makeTransfer` | Realiza uma transferência imediata |
| `viewStatement` | Extrato da conta, categorizado |
| `viewSpendingInsights` | Insights de gastos (funcionalidade inovadora) |
| `blockOrUnblockCard` | Bloqueia/desbloqueia um cartão |

## Tecnologias

- MuleSoft (Mule Runtime 4.x)
- APIkit for SOAP (`mule-soapkit-module`)
- Web Service Consumer (consumo do Process API)
- Anypoint Studio

## Pré-requisitos

- Anypoint Studio instalado
- Process API publicada no Exchange (ou em execução localmente)
- Conta Anypoint Platform (mesma organização do projeto)

## Como executar localmente

1. Clone este repositório.
2. Abra o projeto no Anypoint Studio.
3. Confirme que o `Web Service Consumer` aponta para o endereço correto da Process API.
4. Clique com o botão direito no projeto → `Run As > Mule Application`.
5. O WSDL fica disponível em:
   ```
   http://localhost:8081/BankingExperienceAPIService/BankingExperiencePort?wsdl
   ```

## Testando

Recomenda-se o uso do **SoapUI**: `File > New SOAP Project`, colando a URL do WSDL (com `?wsdl`) em "Initial WSDL" — todas as operações são importadas automaticamente com requests de exemplo.

## Estrutura do projeto

```
src/main/
├── mule/                     # Flows do APIkit for SOAP (api-main + sub-flows)
├── resources/
│   ├── wsdl/                 # Contrato SOAP (contract-first)
│   │   └── banking-experience-mobile-api.wsdl
│   └── config-*.yaml
```

## Equipa

Projeto académico/prático - equipa de 3 pessoas, Anypoint Platform (mesma organização).
Responsável por esta API: **Sara Tuma**
