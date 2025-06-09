# Predição de Renda com o Dataset "Adult"

Este projeto de *Machine Learning* utiliza o [Adult Dataset](https://archive.ics.uci.edu/dataset/2/adult) para construir e avaliar modelos de classificação capazes de prever se a renda anual de um indivíduo excede $50.000.
---

## Objetivo

O objetivo principal é classificar indivíduos em duas categorias de renda com base em seus atributos socioeconômicos:

-   **>50K**: Renda anual maior que $50.000.
-   **<=50K**: Renda anual menor ou igual a $50.000.

A variável alvo do projeto é a coluna `income`.

---

## Dataset: Atributos

O dataset é composto pelos seguintes atributos:

-   **age**: Idade do indivíduo.
-   **workclass**: Classe de trabalho (ex: `Private`, `Self-emp-not-inc`, `Local-gov`).
-   **fnlwgt**: "Final weight" - uma estimativa do número de pessoas que a entrada representa.
-   **education**: Nível de educação (ex: `Bachelors`, `HS-grad`, `Masters`).
-   **education-num**: Representação numérica do nível de educação.
-   **marital-status**: Estado civil.
-   **occupation**: Ocupação (ex: `Tech-support`, `Craft-repair`, `Sales`).
-   **relationship**: Relacionamento familiar.
-   **race**: Raça.
-   **sex**: Sexo.
-   **capital-gain**: Ganho de capital.
-   **capital-loss**: Perda de capital.
-   **hours-per-week**: Horas trabalhadas por semana.
-   **native-country**: País de origem.

---

## Tecnologias Utilizadas

-   Python
-   Pandas
-   NumPy
-   Scikit-learn
-   Seaborn & Matplotlib
-   TensorFlow & Keras
-   XGBoost
-   ucimlrepo

---

## Metodologia

1.  **Limpeza e Análise Inicial**:
    * Os valores nulos (`NaN`) nas colunas `workclass` e `occupation` foram preenchidos com a moda (valor mais frequente) de cada respectiva coluna.
    * Registros com valores nulos na coluna `native-country` foram removidos.
    * A variável alvo `income` teve seus valores inconsistentes (ex: `<=50K.` e `>50K.`) padronizados para `<=50K` e `>50K`.
    * Foi realizada uma análise gráfica para visualizar a distribuição da variável alvo.

2.  **Pré-processamento**:
    * A variável alvo `income` foi convertida para um formato binário (`0` para `<=50K` e `1` para `>50K`).
    * As variáveis categóricas (`workclass`, `education`, `marital-status`, etc.) foram transformadas em formato numérico utilizando a técnica de **One-Hot Encoding** através do `ColumnTransformer` da Scikit-learn.

3.  **Treinamento e Avaliação**:
    * O dataset foi dividido em conjuntos de **treino (70%)** e **teste (30%)**.
    * Foram treinados e avaliados 7 modelos de classificação diferentes.
    * Para cada modelo, a performance foi medida pela **acurácia** e pela **matriz de confusão**.

---

## Modelos e Resultados

Os seguintes modelos foram implementados e comparados:

| Modelo | Acurácia (Teste) | Acurácia (Validação Cruzada) |
| :--- | :---: | :---: |
| Regressão Logística | 83.54% | 83.44% |
| K-Nearest Neighbors (KNN) | 82.78% | 79.21% |
| Árvore de Decisão | 85.60% | 85.82% |
| Random Forest | 85.71% | 85.82% |
| Support Vector Machine (SVC) | 85.06% | 80.03% |
| **XGBoost** | **87.11%** | **87.39%** |
| Rede Neural | 79.87% | N/A |

O modelo **XGBoost** apresentou a maior acurácia tanto no conjunto de teste quanto na validação cruzada, destacando-se como a solução mais eficaz para este problema de classificação.
