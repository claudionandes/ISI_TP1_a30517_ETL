## 🛠️ Ferramentas Utilizadas

| Fase | Ferramenta | Descrição |
|------|-------------|-----------|
| Extração | **JSON File (API simulada)** | Dados dos jogos armazenados localmente (`File_0.json`) |
| Transformação | **KNIME Analytics Platform** | ETL: leitura, filtragem, conversão, escrita e exportação de dados |
| Visualização | **Node-RED Dashboard** | Dashboard web com indicadores e filtros de pesquisa |

---

## ⚙️ ETL no KNIME

### 📂 Workflow principal: `workflow.knime`

O processo no KNIME implementa as seguintes etapas:

| Etapa | Descrição |
|-------|------------|
| **JSON Reader** | Leitura do ficheiro `File_0.json` com dados de jogos (Data, Equipas, Resultado). |
| **JSON to Table** | Conversão da estrutura JSON para tabela tabular. |
| **Column Filter / Constant Value** | Remoção de colunas desnecessárias e padronização de nomes. |
| **String Manipulation** | Correção de valores de texto (e.g., formatação de “Vitória de …”). |
| **CSV Writer / JSON Writer / SQL Writer** | Exportação do dataset tratado para a pasta `Jogos/` para uso no Node-RED. |

---

## 💻 Visualização no Node-RED

### 🧱 Estrutura do fluxo: `Dashboard.json`

O dashboard criado no Node-RED tem como objetivo apresentar indicadores e permitir filtragem dinâmica.

#### 📊 Funcionalidades implementadas:

| Função | Descrição |
|--------|------------|
| ✅ **Leitura do ficheiro JSON** | O fluxo lê o ficheiro `File_0.json` gerado pelo KNIME. |
| ✅ **Contador de Jogos** | Mostra o número total de jogos carregados. |
| ✅ **Tabela de Jogos** | Apresenta a lista de jogos com Data, Equipas e Resultado. |
| ✅ **Filtro por Nome da Equipa** | Campo de pesquisa que filtra a tabela em tempo real. |
| ✅ **Botão “Limpar”** | Restaura a tabela e limpa o campo de pesquisa. |

#### 🧩 Estrutura dos nós principais:
- **`File In`** → Lê o ficheiro JSON  
- **`JSON`** → Converte o conteúdo em objeto utilizável  
- **`Function (Lista de Jogos)`** → Gera tabela HTML com os dados  
- **`Function (Total de Jogos)`** → Conta o total de registos  
- **`Template (UI)`** → Exibe input de pesquisa e botões  
- **`Dashboard Text/Table`** → Mostra resultados formatados  

---

## 🖼️ Exemplo do Dashboard

**Indicadores principais:**
- Total de jogos: `25`
- Filtro de pesquisa por equipa (campo de texto)
- Botões uniformes “Pesquisar” e “Limpar”
- Tabela responsiva com colunas:
  - 🏠 Equipa Casa  
  - 🚩 Equipa Fora  
  - 🏆 Resultado  


---

## 🚀 Execução do Projeto

### ▶️ 1. KNIME
1️⃣ Abrir `workflow.knime`  
2️⃣ Executar os nós até ao **JSON Writer**  
3️⃣ Confirmar que os ficheiros `File_0.json` e export.sql foram exportados corretamente

### ▶️ 2. Node-RED
1️⃣ Importar o ficheiro `Dashboard.json`  
2️⃣ Ligar os nós e clicar em **Deploy**  
3️⃣ Aceder ao dashboard em: http://localhost:1880/ui

---

## 📊 Resultados e Conclusão

O sistema cumpre integralmente os requisitos do trabalho:
- ✅ Fluxo ETL completo implementado  
- ✅ Visualização interativa de dados  
- ✅ Filtros dinâmicos e exportação estruturada  

Demonstra o **domínio do ciclo ETL** e a **integração entre ferramentas open-source (KNIME + Node-RED)**.

---

## 🧾 Créditos
Projeto desenvolvido por **Cláudio Fernandes (A30517)**  
no âmbito da UC **Integração de Sistemas de Informação**  
**Licenciatura em Engenharia de Sistemas Informáticos – IPCA**

---

# ISI_TP1_a30517_ETL
ETL completo (KNIME + Node-RED)
