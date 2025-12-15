# Projeto de Machine Learning: Previsão de Custos Médicos Individuais

## Objetivo do Projeto

Este projeto tem como objetivo construir um modelo de Machine Learning de **Regressão** capaz de prever os custos médicos individuais (`charges`) cobrados pelo seguro de saúde, utilizando características demográficas e de estilo de vida dos beneficiários.

O principal desafio é lidar com a distribuição assimétrica da variável alvo e garantir que o modelo seja robusto e interpretável.

## Dataset

O dataset utilizado, `insurance.csv`, contém 1338 registros e 7 variáveis:

| Variável | Descrição | Tipo |
| :--- | :--- | :--- |
| `age` | Idade do beneficiário principal. | Numérica |
| `sex` | Gênero do contratante de seguros. | Categórica |
| `bmi` | Índice de Massa Corporal. | Numérica |
| `children` | Número de dependentes cobertos pelo seguro. | Numérica |
| `smoker` | Se a pessoa é fumante (`yes` ou `no`). | Categórica |
| `region` | Região residencial do beneficiário (4 regiões). | Categórica |
| **`charges`** | **Valor do custo médico individual (Variável Alvo)**. | Numérica |

## Metodologia 

### 1. Análise Exploratória de Dados (EDA)

* Verificação de valores ausentes (o dataset se mostrou limpo, sem nulos).
* Análise de distribuição das variáveis, identificando a forte **assimetria da variável alvo (`charges`)**.
* Identificação do impacto do status de `smoker` como o principal fator de custo.

### 2. Pré-processamento e Feature Engineering

1.  **Codificação de Variáveis Categóricas:** Utilizado **One-Hot Encoding** para transformar as colunas `sex`, `smoker` e `region` em variáveis binárias.
2.  **Feature Scaling (Padronização):** Aplicado o **`StandardScaler`** (Padronização Z-score) nas variáveis numéricas (`age`, `bmi`, `children`) para garantir que nenhuma feature domine o treinamento devido à sua magnitude.
3.  **Transformação da Variável Alvo:** Aplicada a **transformação logarítmica** ($\log(y)$) na variável `charges` do conjunto de Treinamento para normalizar sua distribuição e melhorar o desempenho dos modelos lineares.


### 3. Modelagem e Avaliação
Para encontrar o modelo mais eficiente, foram testados e comparados diversos algoritmos de Regressão:

* Regressão Linear 
* 

O **`Pipeline`** do scikit-learn foi utilizado para encapsular todas as etapas de pré-processamento e o modelo, prevenindo *data leakage*.

### 4. Ajuste Fino e Interpretabilidade

* O modelo de melhor desempenho foi otimizado usando **Grid Search Cross-Validation ($\text{GridSearchCV}$)** para encontrar os hiperparâmetros ideais.
* **Importância de Features:** Após a otimização, foi realizada a análise de Importância de Features para explicar como o modelo chega às suas previsões e quais fatores são mais relevantes.
* **Métricas de Avaliação:** RMSE (Root Mean Squared Error), MAE (Mean Absolute Error) e $R^2$ foram usados para avaliar a performance no conjunto de Teste. Todas as métricas foram calculadas na escala original (dólar) após o `Inverse Transform` (exponencial) das previsões.

## Resultados

| Modelo | MAE (Mean Absolute Error) | RMSE (Root Mean Squared Error) | $R^2$ (Coeficiente de Det.) |
| :--- | :--- | :--- | :--- |
| **[Melhor Modelo, ex: Random Forest]** | **[Preencher com seu valor MAE]** | **[Preencher com seu valor RMSE]** | **[Preencher com seu valor R²]** |

### Interpretação do Resultado

* O **[Melhor Modelo]** demonstrou a melhor capacidade preditiva.
* O MAE de **[Preencher com seu valor MAE]** significa que, em média, o nosso modelo erra a previsão do custo médico por essa quantia em dólar.
* O fator **`smoker`** foi consistentemente a variável mais importante para a determinação dos custos.

## Tecnologias Utilizadas

O projeto foi desenvolvido em Python e utiliza as seguintes bibliotecas:

* `pandas`
* `numpy`
* `matplotlib` e `seaborn` (para EDA)
* `scikit-learn` (para pré-processamento, pipeline, modelos e métricas)

---
Desafio do Módulo de Machine Learning com Python - Fase 2. Pós Tech em Data Analytics (FIAP)