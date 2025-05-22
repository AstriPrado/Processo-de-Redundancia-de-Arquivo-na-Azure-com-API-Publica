
# 🚀 Processos de Redundância de Arquivos na Azure com API Pública (IBGE - IPCA)

## 🎯 Objetivo
Este projeto tem como objetivo demonstrar a criação de um processo de cópia de arquivo utilizando serviços na Azure. Através do **Azure Data Factory**, conectamos uma API pública do IBGE, extraímos dados do **IPCA (Índice de Preços ao Consumidor Amplo)** e armazenamos os dados em um **Blob Storage** no formato **JSON**.

---

## 🔗 Fonte dos Dados
- API Pública do IBGE — IPCA (Variação Mensal)  
→ [Documentação IBGE API](https://servicodados.ibge.gov.br/api/docs/agregados)  
→ Endpoint utilizado:  
`https://servicodados.ibge.gov.br/api/v3/agregados/1737/periodos/202305-202404/variaveis/63?localidades=N1[all]`

---

## 🏗️ Arquitetura da Solução
- **Azure Data Factory**
  - Linked Service REST (Conexão com API IBGE)
  - Linked Service Blob Storage (Armazenamento)
  - Dataset Origem (API - JSON)
  - Dataset Destino (Blob Storage - JSON)
  - Pipeline de cópia de dados

---

## 🔧 Etapas do Processo

### 1️⃣ Criação do Linked Service REST (API IBGE)
Configuração da conexão REST com a API pública do IBGE para acesso aos dados do IPCA.

![Imagem - Linked Service REST](INSIRA_LINK_DA_IMAGEM_AQUI)

---

### 2️⃣ Criação do Dataset de Origem (API IBGE)
Configuração do Dataset de origem utilizando o endpoint da API e o Linked Service REST.

![Imagem - Dataset de Origem](INSIRA_LINK_DA_IMAGEM_AQUI)

---

### 3️⃣ Criação do Linked Service Blob Storage
Configuração da conexão com o Blob Storage da Azure para armazenamento dos dados extraídos.

![Imagem - Linked Service Blob](INSIRA_LINK_DA_IMAGEM_AQUI)

---

### 4️⃣ Criação do Dataset de Destino (Blob Storage)
Configuração do Dataset de destino para receber os dados em formato JSON no Blob Storage.

![Imagem - Dataset de Destino](INSIRA_LINK_DA_IMAGEM_AQUI)

---

### 5️⃣ Criação e Execução do Pipeline (Copy Data)
Desenvolvimento do pipeline com a atividade de **Copy Data**, conexão entre o Dataset de origem (API) e o Dataset de destino (Blob Storage).

![Imagem - Pipeline](INSIRA_LINK_DA_IMAGEM_AQUI)

---

## 📦 Resultado
O arquivo JSON gerado contém os dados de variação mensal do IPCA nos últimos 12 meses, conforme exemplo abaixo:

```json
{
  "id": "63",
  "variavel": "IPCA - Variação mensal",
  "unidade": "%",
  "resultados": [
    {
      "series": [
        {
          "localidade": {
            "id": "1",
            "nivel": {
              "id": "N1",
              "nome": "Brasil"
            },
            "nome": "Brasil"
          },
          "serie": {
            "202305": "0.23",
            "202306": "-0.08",
            "202307": "0.12",
            "202308": "0.23",
            "202309": "0.26",
            "202310": "0.24",
            "202311": "0.28",
            "202312": "0.56",
            "202401": "0.42",
            "202402": "0.83",
            "202403": "0.16",
            "202404": "0.38"
          }
        }
      ]
    }
  ]
}
```

---

## 🏆 O que foi aprendido
- Como criar pipelines no Azure Data Factory.
- Conectar APIs públicas via REST no Data Factory.
- Armazenar dados no Azure Blob Storage.
- Princípios de processos de redundância de dados na nuvem.
- Manipulação de dados em formato JSON.

---

## 🚀 Próximos passos (opcional)
- Transformar o JSON em formato tabular no Power BI, Python ou Azure Data Flow.
- Automatizar a execução desse pipeline periodicamente.

---

## ✍️ Autor
- **Astri [Seu Sobrenome]**  
Analista de Dados | Business Intelligence | Especialista em Processos  

[LinkedIn](https://www.linkedin.com/) | [Portfólio](#) (se tiver)

---
