# Projeto de Machine Learning: Previsão de Ruído de Aerofólio (NASA) 

Este repositório contém a solução para um desafio de machine learning (Parte I) como parte de um processo seletivo. O objetivo é desenvolver um modelo de regressão supervisionada para prever o nível de pressão sonora (em decibéis) de aerofólios da NASA, com base em medições de testes realizados em túnel de vento.

O problema é tratado como uma tarefa de **regressão**, pois a variável alvo (`scaled-sound-pressure`) é um valor numérico contínuo.

## Dataset: NASA Airfoil Self-Noise

O dataset (`nasa.csv`) contém 1503 registros e 6 colunas, obtidos de testes em túnel de vento.

* **Features (Variáveis Preditoras):**
    1.  `frequency` (Frequência, em Hertz)
    2.  `attack-angle` (Ângulo de ataque, em graus)
    3.  `chord-length` (Comprimento da corda, em metros)
    4.  `free-stream-velocity` (Velocidade do fluxo livre, em metros por segundo)
    5.  `suction-side-displacement-thickness` (Espessura de deslocamento do lado da sucção, em metros)
* **Alvo (Variável Dependente):**
    1.  `scaled-sound-pressure` (Nível de pressão sonora, em decibéis)

## Metodologia e Workflow

O projeto foi estruturado seguindo as boas práticas de um pipeline de Machine Learning:

1.  **Carregamento e Exploração:** Os dados foram carregados e inspecionados para entender sua estrutura, tipos de dados e estatísticas descritivas. Foi verificado que não havia dados nulos.
2.  **Definição do Problema:** Identificado como um problema de **regressão supervisionada**.
3.  **Divisão dos Dados:** O dataset foi dividido em conjuntos de **treinamento (75%)** e **teste (25%)**, utilizando `train_test_split`.
4.  **Pré-processamento e Preparação:**
    * **Normalização (Opcional):** Foi aplicado o `StandardScaler` para garantir que todas as features ficassem na mesma escala, melhorando o desempenho do modelo.
    * **Seleção de Atributos (Obrigatório):** Foi utilizado o `SelectKBest` com `f_regression` para selecionar as `k=4` features com maior correlação estatística com a variável alvo.
5.  **Treinamento do Modelo:** Foi escolhido o `RandomForestRegressor` da biblioteca `scikit-learn`, um algoritmo robusto que lida bem com relações não lineares. O modelo foi treinado (`.fit()`) usando **apenas** a base de treino.
6.  **Avaliação:** O modelo treinado foi usado para fazer predições na base de teste (dados nunca vistos). O desempenho foi avaliado com as seguintes métricas de regressão:
    * **R² (R-squared):** ~0.913
    * **MAE (Mean Absolute Error):** ~2.15 dB
    * **RMSE (Root Mean Squared Error):** ~2.70 dB
7.  **Visualização:** Foi gerado um gráfico de dispersão (Real vs. Previsto) para analisar visualmente a acurácia das predições.

## Tecnologias Utilizadas

* **Python 3**
* **Google Colab** (Jupyter Notebook)
* **Pandas:** Para manipulação e análise de dados.
* **Numpy:** Para operações numéricas.
* **Scikit-learn:** Para pré-processamento (`StandardScaler`, `SelectKBest`), divisão (`train_test_split`), modelagem (`RandomForestRegressor`) e avaliação (`r2_score`, `mean_absolute_error`).
* **Matplotlib:** Para visualização de dados.

## ▶️ Como Executar

Este notebook foi desenvolvido no Google Colab e utiliza o Google Drive para carregar o dataset.

1.  **Pré-requisito:** Faça o upload do arquivo `nasa.csv` para uma pasta no seu Google Drive (o código assume o caminho `/content/drive/MyDrive/nasa/nasa.csv`).
2.  Abra o arquivo `seu_nome_desafio_parte1.ipynb` no Google Colab.
3.  Se necessário, ajuste a variável `path` na célula de "Carregar o dataset" para corresponder ao local do arquivo no seu Drive.
4.  Execute
