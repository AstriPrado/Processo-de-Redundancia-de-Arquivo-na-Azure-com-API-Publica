
# 🔗 Processos de Redundância de Arquivos na Azure com API IBGE

Este projeto tem como objetivo demonstrar um processo de redundância de arquivos na Azure, utilizando o Azure Data Factory para extrair dados da API pública do IBGE e armazená-los no Azure Blob Storage.

## 🏗️ Arquitetura da Solução
- **Azure Data Factory**
  - Linked Service REST (Conexão com API IBGE)
  - Linked Service Blob Storage (Armazenamento)
  - Pipeline de cópia de dados
  - Dataset de Origem (API - JSON) *(inline no pipeline)*
  - Dataset de Destino (Blob Storage - JSON) *(inline no pipeline)*

---

## 🛠️ Etapas do Projeto

### 1️⃣ Criação do Linked Service de Origem (API IBGE)
- Configuração da conexão com a API pública do IBGE utilizando o conector **REST**.
- Definição da URL base da API que fornece os dados do **IPCA (Índice de Preços ao Consumidor Amplo)**.
- Este Linked Service será usado no Dataset de origem dentro do pipeline.

![Imagem - Linked Service de Origem](LINK IMAGEM 1)

![Imagem - Linked Service de Origem](LINK IMAGEM 2)

---

### 2️⃣ Criação do Linked Service de Destino (Blob Storage)
- Criação da conexão com o **Azure Blob Storage**, utilizado como repositório para armazenar os dados extraídos da API.
- Configuração do acesso utilizando a **String de Conexão** da Storage Account.

![Imagem - Linked Service de Destino](IMG/imagem3.png)

![Imagem - Linked Service de Destino](IMG/imagem4.png)

---

### 3️⃣ Criação do Pipeline
- Criação do pipeline no **Azure Data Factory**, responsável por orquestrar o processo de extração e carga dos dados.
- Utilização da atividade **Copy Data**, que será configurada com os datasets de origem e destino.

![Imagem - Linked Service de Destino](IMG/imagem 5.png)

---

### 4️⃣ Criação do Dataset de Origem (dentro do Pipeline)
- Dataset configurado diretamente dentro da atividade **Copy Data**.
- Conectado ao **Linked Service REST (API IBGE)**, utilizando o endpoint da API que retorna os dados do IPCA dos últimos 12 meses.
- Definido no formato **JSON**.

![Imagem - Linked Service de Destino](IMG/imagem6.png)

![Imagem - Linked Service de Destino](IMG/imagem7.png)

---

### 5️⃣ Criação do Dataset de Destino (dentro do Pipeline)
- Dataset criado dentro da atividade **Copy Data**.
- Aponta para o **Linked Service do Blob Storage**, definindo:
  - Container de armazenamento.
  - Formato de saída dos dados: **JSON**.

![Imagem - Linked Service de Destino](IMG/imagem8.png)

![Imagem - Linked Service de Destino](IMG/imagem9.png)

![Imagem - Linked Service de Destino](IMG/imagem_destino_container.png)
---

### 6️⃣ Execução do Pipeline
- Validação e execução do pipeline no modo **Debug**, seguida de publicação.
- Após a execução, os dados são gravados no Blob Storage no formato JSON.
- Verificação no Blob Storage para confirmar a criação correta dos arquivos e a integridade dos dados.

![Imagem - Linked Service de Destino](IMG/imagem10.png)

---

## 📄 Resultado
O arquivo JSON gerado contém os dados do IPCA (variação mensal) dos últimos 12 meses, extraídos da API do IBGE e armazenados no Azure Blob Storage.

![Imagem - Linked Service de Destino](IMG/imagem12.png)

## 🚀 Tecnologias Utilizadas
- Azure Data Factory
- Azure Blob Storage
- API pública do IBGE (IPCA)
- Formato de dados: JSON

---

## ✍️ Autor
Astri 🚀
