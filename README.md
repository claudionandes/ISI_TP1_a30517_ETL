# ISI_TP1_a30517_ETL  
Processo ETL completo com KNIME e Node-RED

---

## Ferramentas Utilizadas

| Fase | Ferramenta | Descrição |
|------|-------------|-----------|
| Extração | API SportMonks Football | Fonte de dados sobre jogos, equipas e resultados |
| Transformação | KNIME Analytics Platform | Implementação do processo ETL (extração, limpeza, normalização e exportação) |
| Visualização | Node-RED Dashboard | Apresentação dinâmica dos dados com filtros e indicadores |

---

## Processo ETL no KNIME

O workflow desenvolvido no KNIME executa as três fases principais do processo ETL:

| Etapa | Descrição |
|-------|------------|
| Extract | Extração de dados da API SportMonks através dos nós API Token, GET Request, JSON Path e Ungroup. |
| Transform | Limpeza e normalização dos dados com uso de expressões regulares, manipulação de texto e padronização de datas. |
| Load | Exportação dos resultados tratados para os formatos JSON, XML e CSV, garantindo interoperabilidade com o Node-RED. |

Cada execução gera ficheiros de saída na pasta `data/Jogos/`, utilizados pelo dashboard.

---

## Visualização no Node-RED

O dashboard criado no Node-RED lê o ficheiro JSON exportado pelo KNIME e apresenta os jogos com filtros e indicadores.
=======
### 🧱 Estrutura do fluxo: `Dashboard.json`

O dashboard criado no Node-RED tem como objetivo apresentar indicadores e permitir filtragem dinâmica.

#### 📊 Funcionalidades implementadas:

| Função | Descrição |
|--------|------------|
| Leitura do ficheiro JSON | Importa os dados mais recentes. |
| Filtro por Equipa | Permite pesquisar jogos por nome da equipa. |
| Contador de Jogos | Mostra o número total de registos encontrados. |
| Tabela de Jogos | Lista dinâmica com Data, Equipa Casa, Equipa Fora e Resultado. |

O fluxo é composto pelos nós File In, JSON, Function, Template (UI) e Dashboard Table/Text.

---

## Execução do Projeto

### KNIME
1. Abrir `workflow.knime`  
2. Executar até aos nós de exportação  
3. Confirmar a criação dos ficheiros `JSON_0.json`, `XML_0.xml` e `CSV_Jogos.csv`
=======
**Indicadores principais:**
- Total de jogos: `25`
- Filtro de pesquisa por equipa (campo de texto)
- Botões uniformes “Pesquisar” e “Limpar”
- Tabela responsiva com colunas:
  - 🏠 Equipa Casa  
  - 🚩 Equipa Fora  
  - 🏆 Resultado  

### Node-RED
1. Importar o fluxo `ETL_Futebol_Dashboard.json`  
2. Ligar e clicar em Deploy  
3. Aceder em: `http://localhost:1880/ui`

---

## Resultados

O sistema cumpre os objetivos do trabalho:
- Pipeline ETL completo e automatizado  
- Dados transformados e validados  
- Visualização interativa com filtros e indicadores  
- Integração entre KNIME e Node-RED validada com sucesso  

---

## Autor

Projeto desenvolvido por **Cláudio Fernandes (A30517)**  
Unidade Curricular: Integração de Sistemas de Informação  
Licenciatura em Engenharia de Sistemas Informáticos – IPCA
