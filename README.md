# 📊 Dashboard Executivo: Inteligência de Risco e Rentabilidade de Crédito

Este projeto apresenta uma solução de ponta a ponta (End-to-End) em Data Science e Business Intelligence para o setor financeiro. O objetivo é transcender a análise reativa de inadimplência, incorporando Machine Learning para prever o risco de crédito e otimizar a rentabilidade das safras.

---

## 🏗️ Arquitetura da Solução

A arquitetura foi projetada simulando um ambiente corporativo real de alta complexidade, garantindo o isolamento dos dados de produção e a retroalimentação automatizada das predições:

1. **Coleta e Armazenamento (SQL Server):** Restauração de um banco de dados legado a partir de um arquivo `.bak`. Para preservar o ERP em produção, foi gerado um banco de dados "clone" (Staging).
2. **Engenharia de Dados (Stored Procedures):** A atualização dos dados nativos e a ingestão dos resultados preditivos no banco clone são feitas de forma automatizada por *Stored Procedures* dedicadas.
3. **Analytics e Machine Learning (Python):** Extração dos dados do SQL Server, pré-processamento, balanceamento da variável alvo com SMOTE e treinamento de um algoritmo `RandomForestClassifier` para calcular a probabilidade de inadimplência.
4. **Modelagem e BI (Power BI):** Conexão direta com o banco clone, modelagem *Star Schema* e utilização avançada de DAX para gerar métricas financeiras dinâmicas.

---

## 📈 Métricas Estratégicas (KPIs)

⚠️ **Nota:** A implementação técnica detalhada, as Colunas Calculadas e todas as fórmulas em linguagem DAX podem ser consultadas e auditadas diretamente no arquivo `.pbix` disponibilizado neste repositório.

A inteligência do painel é guiada por KPIs que traduzem o risco estatístico em impacto financeiro:

* **Total Financiado:** O montante financeiro bruto liberado pela instituição nas operações de crédito.
* **Saldo Devedor (EAD - *Exposure at Default*):** O risco real, calculando o valor financeiro ainda exposto ao calote após o desconto da proporção de parcelas já amortizadas.
* **Valor em Risco Alto:** Volume financeiro atrelado exclusivamente a contratos classificados com alta probabilidade de calote pelo modelo preditivo.
* **Perda Esperada (*Expected Loss*):** A tradução financeira do modelo de Inteligência Artificial, cruzando o valor exposto com a probabilidade estatística de calote.
* **Lucro Líquido Estimado:** A métrica final de viabilidade. Subtrai a Perda Esperada da receita de juros projetada, validando se o prêmio de risco cobrado cobre o risco previsto.

---

## 📁 Estrutura do Repositório

* `database/`: Contém o arquivo `.bak` original do SQL Server, permitindo a restauração do ERP simulado localmente.
* `scripts/`: Códigos SQL das *Stored Procedures* utilizadas para atualização do banco clone.
* `notebooks/Modelo_Preditivo.ipynb`: Código fonte em Python (EDA, tratamento, SMOTE e Random Forest). **Nota:** Todas as dependências e bibliotecas necessárias para a execução do modelo estão documentadas e disponíveis na primeira célula de código deste notebook.
* `dashboard/`: Arquivo `.pbix` com o dashboard interativo construído no Power BI.
* `img/`: Capturas de tela (screenshots) das páginas principais do Dashboard.

---

## 🚀 Como Reproduzir o Projeto

1. Faça o clone deste repositório.
2. Restaure o arquivo `.bak` no seu ambiente Microsoft SQL Server local.
3. Execute as *Stored Procedures* disponíveis na pasta `scripts/`.
4. Instale as dependências do Python. (Consulte a primeira célula do notebook `Modelo_Preditivo.ipynb` para visualizar todas as bibliotecas exigidas).
5. Execute o notebook `Modelo_Preditivo.ipynb` para gerar as novas predições e atualizar o banco de dados.
6. Abra o arquivo `.pbix` no Power BI Desktop e atualize as credenciais da fonte de dados para o seu servidor SQL local.

---

**Autor:** Victor de Oliveira Ernesto da Silva
