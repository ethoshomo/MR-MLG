# Análise de Contagem de Espirros: Modelos de Regressão (GLM)

Este repositório, de autoria de Carlos Filipe de Castro Lemos, contém a resolução da **Avaliação 2** da disciplina **SME0823 - Modelos de Regressão e Aprendizado Supervisionado II**, ministrada pela professora Cibele Russo no ICMC-USP. O projeto foca na modelagem estatística de dados de contagem do número de espirros em datasets gerados artificialmente.

## 📋 Sobre o Projeto

O objetivo principal deste estudo é investigar os fatores associados à frequência diária de espirros (`nsneeze`) em relação à concentração de pólen e variáveis comportamentais/demográficas. O fluxo de trabalho envolve desde a análise exploratória até a comparação de modelos lineares generalizados (GLM) para dados de contagem.

**Principais etapas da análise:**

1.  Análise Exploratória de Dados (EDA).
2.  Ajuste de Modelo de Poisson.
3.  Diagnóstico de Superdispersão (Overdispersion).
4.  Ajuste e comparação com Modelo Binomial Negativo.
5.  Análise de Efeitos Marginais e Predição.

## 🚀 Tecnologias Utilizadas

O projeto foi desenvolvido em **Python** utilizando as seguintes bibliotecas para análise estatística e visualização de dados:

  * **[Pandas](https://pandas.pydata.org/)** & **[NumPy](https://numpy.org/)**: Manipulação e processamento de dados.
  * **[Statsmodels](https://www.statsmodels.org/)**: Ajuste de modelos GLM (Poisson, Binomial Negativo) e testes estatísticos.
  * **[Matplotlib](https://matplotlib.org/)** & **[Seaborn](https://seaborn.pydata.org/)**: Visualização de dados (Heatmaps, Boxplots, Envelopes Simulados).
  * **[Scikit-Learn](https://scikit-learn.org/)**: Métricas de avaliação (MSE, MAE) e divisão de dados.
  * **[SciPy](https://scipy.org/)**: Funções estatísticas auxiliares.

## 📊 Metodologia e Resultados

### 1\. Exploração dos Dados

Identificou-se que a variável resposta (`nsneeze`) possui uma distribuição assimétrica com cauda longa e presença de *outliers*, características típicas de dados de contagem que sugerem superdispersão.

### 2\. Modelagem: Poisson vs. Binomial Negativo

  * **Modelo Poisson:** Foi o ponto de partida, utilizando função de ligação logarítmica. No entanto, diagnósticos (Deviance/DF \> 1 e Envelopes Simulados) confirmaram a presença severa de **superdispersão**, tornando o modelo inadequado (subestimativa dos erros-padrão).
  * **Modelo Binomial Negativo:** Ajustado para capturar a variância extra dos dados.
      * **AIC:** Reduziu de \~9906 (Poisson) para \~7711 (Binomial Negativo).
      * **Diagnóstico:** Os resíduos se mantiveram dentro das bandas de confiança de 95% nos gráficos de envelope.

### 3\. Principais Insights

Com base nos efeitos marginais do modelo final (Binomial Negativo):

  * **Pólen (`pollen`):** Principal fator de aumento dos espirros.
  * **Anti-histamínicos (`antihist`):** Fator de proteção significativo, reduzindo drasticamente a contagem esperada de espirros (\~9.4 espirros a menos em média).
  * **Álcool (`alcohol`) e Tabagismo (`smoker`):** Atuam como agravantes, aumentando a contagem esperada.

## 📂 Estrutura do Repositório

```bash
├── SME0823_Avaliação_2.ipynb   # Notebook principal com código e análises
├── sneeze1.csv                 # Dataset utilizado (ID USP final 0)
└── README.md                   # Documentação do projeto
```

## 🔧 Como Executar

Para reproduzir as análises, certifique-se de ter o Python instalado e execute:

1.  Clone o repositório:
    ```bash
    git clone https://github.com/ethoshomo/MR-MLG.git
    ```
2.  Instale as dependências:
    ```bash
    pip install pandas numpy matplotlib seaborn statsmodels scikit-learn scipy
    ```
3.  Execute o Jupyter Notebook:
    ```bash
    jupyter notebook SME0823_Avaliação_2.ipynb
    ```

-----

*Este projeto foi desenvolvido para fins acadêmicos.*