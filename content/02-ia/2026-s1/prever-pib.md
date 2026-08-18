---
tags:
  - trilha/ia
  - nivel/avancado
title: Previsão de Atividade Econômica (IBC-Br) via Stacking Ensemble
---
_**Autores:** David Leati · Lucas Terra_

**_Repositório:_** [link](https://github.com/lsterra/dev_ensina_ia_grupo3)
# 1.**Introdução e Contextualização**

Este projeto tem como objetivo desenvolver um modelo preditivo robusto para o IBC-Br (Índice de Atividade Econômica do Banco Central), amplamente utilizado pelo mercado financeiro e acadêmico como *proxy* mensal de alta frequência para o Produto Interno Bruto (PIB) brasileiro. Dada a defasagem temporal na divulgação do PIB oficial trimestral (IBGE), o IBC-Br atua como um termômetro ágil, essencial para a tomada de decisão em política monetária e alocação de ativos.

A abordagem adotada fundamenta-se em técnicas de Machine Learning supervisionado, com foco na construção de um **Stacking Ensemble**. Esta estratégia combina previsões de múltiplos modelos heterogêneos para mitigar a variância do erro e ampliar a capacidade de generalização fora da amostra (*out-of-sample*). A metodologia inspira-se no estudo de Micheletti (2024), avançando na literatura ao implementar um meta-learner com restrições de não-negatividade (NNLS) e rigorosos testes de estacionariedade.

# 2. **Engenharia de Dados e Metodologia**

## 2.1 **Fonte e Tratamento Inicial**

A base de dados utilizada neste estudo foi compilada através da plataforma **Macrodados**, um sistema agregador de informações econômicas e financeiras. A amostra compreende séries temporais mensais extraídas de fontes primárias oficiais, notadamente o Banco Central do Brasil (BCB), o Instituto Brasileiro de Geografia e Estatística (IBGE), a Fundação Getúlio Vargas (FGV) e a B3.

O processamento inicial dos dados brutos (*dados\_macro\_bruto.xlsx*) foi executado através de um *pipeline* dedicado (pipeline.py), responsável pela limpeza dos dados, tratamento de *outliers* e preenchimento de valores ausentes (*imputation*),

assegurando a continuidade e a integridade das séries temporais antes da etapa de modelagem.

## 2.2 **Feature Engineering (Engenharia de Atributos)**

Para capturar a complexidade estrutural da economia brasileira, foram geradas novas variáveis explicativas fundamentadas na teoria econômica:

* **Juro Real:** Diferença entre a taxa Selic e a inflação (IPCA), mensurando o custo real do capital.  
  * **Termos de Troca:** Relação entre preços de exportação e importação (ou taxa de câmbio), indicando a riqueza relativa do país frente ao exterior.  
    * **Hiatos do Produto:** Diferença entre o nível atual do IBC-Br e suas tendências de longo prazo (médias móveis de 12 e 24 meses), sinalizando o aquecimento ou ociosidade da economia.  
    * **Volatilidade Financeira:** Desvio padrão móvel do Dólar e do Ibovespa (em janelas de 3 e 6 meses) como *proxy* para a incerteza de mercado.  
    * **Defasagens (*Lags*):** Variáveis defasadas em 3 e 12 meses para capturar a inércia inflacionária e os ciclos sazonais da atividade.

## 2.3 **Transformação e Estacionariedade**

Modelos de regressão linear e de árvores performam melhor ou exigem séries estacionárias (com média e variância constantes no tempo). Para tal, aplicou-se um protocolo de transformação específico por tipo de variável:

* **Diferenciação (*Diff*):** Aplicada a taxas percentuais (ex: Selic, Juro Real).

  * **Log-retorno (*Pct Change*):** Aplicado a índices de preços e de atividade para normalizar a escala e estabilizar a variância.  
    * **Preservação de Nível:** Variáveis estruturais como "Hiatos" e "Balança de Empregos" foram mantidas em nível, conforme a teoria econômica sugere estacionariedade ou relevância direta de sua magnitude.

## 2.4 **Seleção de Features via Teste ADF**

A seleção de variáveis foi conduzida de forma automatizada (módulo feature\_selection.py), utilizando o **Teste Augmented Dickey-Fuller (ADF)** como critério rigoroso de filtragem para evitar regressões espúrias — fenômeno onde o modelo detecta falsas correlações entre variáveis que possuem tendências estocásticas comuns, mas sem causalidade real.

O teste ADF verifica a presença de raiz unitária na série temporal. Adotou-se um nível de significância de 5% (alpha \= 0.05).

* **Critério de Decisão:** Se o p-valor calculado for menor que 0.05, rejeita-se a hipótese nula de raiz unitária, confirmando estatisticamente que a série é estacionária.

### **Resultado da Filtragem:**

O algoritmo avaliou as 100 *features* geradas na etapa de engenharia. Destas, 15 variáveis falharam no teste (p-valor \> 0.05), incluindo agregados monetários em nível (M1) e tendências de longo prazo, sendo descartadas. Restaram **85 variáveis explicativas** comprovadamente estacionárias para o treinamento dos modelos.

## 2.5 **Arquitetura dos Modelos Base**

A implementação utilizou as bibliotecas *Scikit-Learn* e *XGBoost*, com reprodutibilidade garantida pela fixação da semente aleatória (random\_state=42). A calibração de cada algoritmo envolveu otimização de hiperparâmetros via *GridSearchCV* com validação cruzada temporal (*TimeSeriesSplit*). O sistema adotou uma lógica adaptativa: busca em grade para janelas com amostras suficientes e parâmetros conservadores para janelas iniciais curtas, visando evitar o overfitting.

As configurações específicas exploradas foram:

1. **Random Forest Regressor:** Otimização do número de árvores (150, 200\) e

   controle de profundidade (*max\_depth*: 5, 7). Utilizou-se a raiz quadrada das

   *features* em cada divisão para descorrelacionar as árvores.

2. **Gradient Boosting Regressor:** Foco em taxas de aprendizado lentas (*learning\_rate*: 0.01, 0.05) combinadas com subamostragem estocástica (0.7) e árvores rasas.  
3. **ElasticNet:** Regularização híbrida, explorando penalidades (*alpha*) e taxas de mistura (*l1\_ratio*) para transitar entre a seleção de variáveis (Lasso) e a redução de coeficientes (Ridge).  
4. **XGBoost (XGB):** Implementado com paralelismo e regularização adicional via amostragem de colunas por árvore (*colsample\_bytree*: 0.7).

## 2.6 **Estratégia de Validação e Stacking (Meta-Learner)**

A estrutura de treinamento foi desenhada para mitigar o risco de vazamento de dados (*data leakage*), replicando o cenário real de previsão econômica.

**Protocolo de Janela Expansiva (*Expanding Window*):**

O pipeline implementou um *loop* iterativo de validação:

1. **Inicialização:** Treino com janela mínima de 48 meses.

2. **Ciclo de Previsão:** O modelo é treinado com dados de t\_0 até t\_n-1 para prever t\_n.  
3. **Padronização Isolada:** O *StandardScaler* é ajustado apenas nos dados de treino da janela corrente, impedindo que estatísticas futuras contaminem o passado.  
4. **Expansão:** O dado real é incorporado e a janela avança em um mês.

### **Construção do Meta-Learner via NNLS:**

Para combinar as previsões dos modelos base, adotou-se o método de *Blending*

otimizado via **Non-Negative Least Squares (NNLS)**. Diferente de uma regressão

linear comum, o NNLS restringe os pesos para serem estritamente positivos.

* **Interpretação Econômica:** Isso garante que um modelo só receba peso se contribuir positivamente para a redução do erro. Modelos redundantes ou de baixa performance têm seus pesos zerados matematicamente, funcionando como um mecanismo automático de seleção de modelos (Ensemble Seletivo).

# 3. **Análise de Resultados**

## 3.1 **Performance Preditiva e Benchmark**

A avaliação de desempenho utilizou o erro no nível do índice IBC-Br. Como *benchmark* de linha de base, adotou-se o Modelo Naive, que obteve um RMSE de **3.58**.

O modelo **Stacking Ensemble** superou consistentemente o benchmark e os modelos individuais na maioria dos cenários. No horizonte de 1 mês, o modelo atingiu um **MAPE de 1.86%** e um **RMSE de 2.48**, situando-se na faixa de alta precisão para previsões macroeconômicas.

| Horizont e   | Ensemble (Stacking) | Random Forest | Gradient Boosting | XGBoost  | p-valor DM (Ensemble vs RF) |
| :----------- | :------------------ | :------------ | :---------------- | :------- | :-------------------------- |
| **1 Mês**    | 2.48                | 2.61          | 2.53              | **2.43** | 0.0004                      |
| **3 Meses**  | **2.37**            | 2.56          | 2.42              | 2.41     | 0.0011                      |
| 6 Meses      | 2.77                | 2.95          | 2.79              | 2.79     | 0.0100                      |
| **12 Meses** | **2.41**            | 2.59          | 2.44              | 2.43     | 0.0014                      |

## 3.2 **Sazonalidade e Horizontes Longos**

Um fenômeno relevante é observado na comparação entre os horizontes de 6 e 12 meses. O erro do modelo aumentou no horizonte de 6 meses (RMSE 2.77), mas reduziu-se significativamente no horizonte de 12 meses (RMSE 2.41).

Este comportamento explica-se pela natureza da série do IBC-Br utilizada (sem ajuste sazonal). No horizonte de 6 meses, o modelo enfrenta a dificuldade de projetar meses de alta atividade utilizando defasagens de meses de baixa atividade (sazonalidade invertida). Já em 12 meses, os algoritmos capturam a forte autocorrelação anual da economia, onde o padrão de um mês no ano anterior serve como um preditor robusto para o mesmo mês no ano corrente.

## 3.3 **Análise de Resíduos e Choques Exógenos**

A análise dos resíduos demonstrou que os maiores erros de previsão não decorrem de falhas sistemáticas do modelo, mas sim de choques exógenos imprevisíveis (Cisnes Negros).

| Data (Mês/Ano) | Erro Absoluto (IBC-Br) | Evento Macroeconômico          | Justificativa Econômica	do Resíduo                                                                 |
| :------------- | :--------------------- | :----------------------------- | :------------------------------------------------------------------------------------------------- |
| Abril/2020     | 11,19                  | Início da Pandemia (COVID-19)  | Choque exógeno inédito com paralisação abrupta do setor de serviços (lockdowns).                   |
| **Março/2010** | 9,11                   | Retomada em "V" (Pós-Subprime) | Crescimento econômico acelerado por fortes estímulos fiscais e monetários do governo.              |
| **Março/2023** | 7,18                   | Super	Safra Agrícola           | Safra recorde de soja que impulsionou o PIB acima das projeções baseadas	em indústria/serviços.    |
| **Maio/2018**  | 6,42                   | Greve	dos Caminhoneiros        | Choque negativo de oferta devido à paralisação logística nacional, quebrando a tendência da série. |
| **Março/2022** | 6,24                   | Reabertura	e Guerra da Ucrânia | Choque	inicial	de commodities da guerra.                                                           |

Destacam-se os desvios em **Abril/2020** (Início da Pandemia/Lockdowns) e **Maio/2018** (Greve dos Caminhoneiros). Nesses episódios de quebra estrutural, a inércia histórica perde poder preditivo, evidenciando que modelos estatísticos devem ser complementados pela análise qualitativa em períodos de crise.

## 3.4 **Validação Estatística (Teste Diebold-Mariano)**

Para atestar a robustez dos resultados, aplicou-se o teste de Diebold-Mariano. Os resultados rejeitaram a hipótese nula de igualdade preditiva entre o Ensemble e o Random Forest com um p-valor de **0.0004** (confiança \> 99,9%), comprovando a superioridade estatística da abordagem de Stacking. Em relação ao Gradient Boosting, houve empate técnico, sugerindo que o Ensemble atua principalmente como um redutor de variância e risco.

# 4. **Conclusão**

O estudo atingiu seu objetivo principal de desenvolver um sistema de *nowcasting* para a atividade econômica brasileira (IBC-Br) utilizando técnicas avançadas de Machine Learning. O modelo final (*Stacking Ensemble*) demonstrou alta capacidade preditiva, registrando um **MAPE de 1.86%** e um RMSE de **2.41** no horizonte de 12 meses. Mais importante, o modelo superou com ampla margem o *benchmark* ingênuo (Modelo Naive, RMSE 3.58), comprovando que a estrutura proposta é capaz de extrair sinais complexos das variáveis macroeconômicas e não apenas replicar a inércia da série.

A validação estatística via teste de **Diebold-Mariano** forneceu robustez aos achados. Com um p-valor de **0.0004**, rejeitou-se a hipótese nula de equivalência entre o Ensemble e o Random Forest, confirmando a superioridade da estratégia de

empilhamento. Em relação ao Gradient Boosting, observou-se um empate técnico estatístico, sugerindo que o ganho do Ensemble reside na **redução de variância** e na proteção contra o risco de especificação de um único modelo, atuando como um "seguro" contra instabilidades.

Do ponto de vista econômico, a análise revelou dois comportamentos cruciais:

1. **Sazonalidade e Horizontes:** O modelo capturou com precisão a forte autocorrelação anual da economia brasileira, apresentando erros menores no horizonte de 12 meses (RMSE 2.41) do que no de 6 meses (RMSE 2.77), contornando a ausência de ajuste sazonal na série bruta.  
2. **Limitações em Choques Exógenos:** A análise de resíduos identificou que os maiores erros de previsão coincidem estritamente com eventos de quebra estrutural ("Cisnes Negros"), como a Greve dos Caminhoneiros (2018) e o início da Pandemia de COVID-19 (2020). Isso evidencia que, embora o algoritmo seja eficaz em condições normais de mercado, ele deve ser complementado pela análise qualitativa em cenários de crise inédita.

   Por fim, ao contrastar estes resultados com a literatura recente, especificamente

**Micheletti (2024)**, este trabalho apresenta contribuições metodológicas relevantes:

* **Evolução do Meta-Learner:** Diferente da abordagem de Regressão Linear utilizada por Micheletti, que pode resultar em *overfitting* por permitir pesos negativos, a implementação do **Non-Negative Least Squares (NNLS)** garantiu que o Ensemble atribuísse pesos nulos a modelos ineficientes (como o ElasticNet), assegurando uma performance sempre igual ou superior ao melhor modelo base.  
  * **Rigor no Pré-Processamento:** A filtragem sistemática via teste **ADF (Augmented Dickey-Fuller)** eliminou ruídos de tendências estocásticas, prevenindo regressões espúrias que frequentemente inflacionam métricas em estudos de séries temporais.

Conclui-se, portanto, que a arquitetura de *Stacking Ensemble* proposta, quando fundamentada em rigor estatístico e engenharia de dados econômica, consolida-se como uma ferramenta robusta e competitiva para o acompanhamento da atividade econômica brasileira.