---
title: Deep Markovian Trader
tags:
  - nivel/avancado
  - trilha/finquant
---
# 0. Introdução


![[deep-markovian-logo.png]]

## 0.1 Explicação do Nome

“Deep Markovian Trader” faz referência aos elementos principais da estratégia: “Deep” refere-se ao uso de Deep Learning, “Markovian” à modelagem por cadeias de Markov, e “Trader” à natureza da estratégia, focada em operações de Long & Short.

## 0.2 Explicação Lógica Estratégia

A estratégia avalia, para cada período e para cada ação do S&P500, a volatilidade condicional das ações, utilizando um modelo inspirado no MSGARCH. Com base nessa métrica, seleciona-se, a cada ciclo, as 50 ações com as menores volatilidades condicionais. Em seguida, um modelo LSTM é treinado, levando em consideração indicadores técnicos, para prever os retornos das ações no próximo período. Tais previsões são ordenadas em ordem decrescente, e com base nessa classificação, as ações são distribuídas em percentis, com a compra das ações no primeiro percentil e a venda das que se encontram no último percentil.

## 0.3 Características

|**Campo**|**Valor**|
|---|---|
|**Tipo de Estratégia:**|Trade|
|**Classe de Ativos:**|Ações|
|**Universo:**|S&P 500|
|**Média Trades por Mês:**|10|
|**Holding Period:**|30|
|**Qual Plataforma Testou a Estratégia:**|Python|
|**Benchmark Estratégia:**|S&P 500|

# 1. Introdução

A ideia da estratégia de investimento apresentada aqui nasceu de discussões em nossos grupos de estudo, especificamente em duas ocasiões. A primeira delas foi uma conversa sobre o livro O Homem que Decifrou o Mercado: Como Jim Simons Criou a Revolução Quant, que descreve como um dos turning points do fundo Medallion ocorreu quando começaram a aplicar técnicas de machine learning para predição. Esse insight nos levou a refletir sobre como estratégias de investimento podem ser aprimoradas com o uso de algoritmos de machine learning. A segunda discussão que inspirou essa estratégia foi sobre o paper Can we forecast better in periods of low uncertainty? The role of technical indicators, o qual sugere que indicadores técnicos tendem a funcionar melhor em períodos de baixa volatilidade. Com essas inspirações, formulamos a hipótese de que, ao focar em períodos de baixa volatilidade, poderíamos usar modelos de machine learning, treinados com indicadores técnicos, para prever tendências de forma mais precisa.

# 2. Estratégia

Nossa estratégia de investimento é baseada em dois pilares principais: a modelagem da volatilidade condicional das ações do S&P500, que é influenciada pelos retornos anteriores, pela persistência da volatilidade e pela transição entre regimes de mercado (alta ou baixa volatilidade), e a previsão dos preços para ações identificadas com menor volatilidade condicional, utilizando modelos de machine learning treinados com indicadores técnicos para capturar padrões de comportamento em períodos de baixa incerteza. Primeiramente, abordaremos o modelo de volatilidade condicional, seguido pela metodologia de previsão de preços. Para exemplificar, utilizaremos as ações da Coca-Cola Company e do JPMorgan em um gráfico que mostra como nosso modelo captura a volatilidade condicional. Em seguida, usaremos as ações do JPMorgan para ilustrar, também com um gráfico, como o modelo realiza previsões. Ao final, detalharemos a execução da estratégia. Para a modelagem da volatilidade condicional, utilizamos um modelo fundamentado no modelo MSGARCH (Markov Switching GARCH), que combina a estrutura de mudanças de regime com o modelo GARCH tradicional. Esse modelo se adapta a diferentes estados de volatilidade, identificando períodos de alta e baixa volatilidade ao alternar entre regimes por meio de uma cadeia de Markov. Dentro de cada regime, o GARCH modela a volatilidade, acomodando dependências temporais e capturando agrupamentos de volatilidade. Essa abordagem permite ao modelo responder a transições dinâmicas na volatilidade dos ativos, sendo essencial para selecionar ações com baixa volatilidade, um elemento crucial da nossa estratégia.

![[deep-markovian-volatilidade.png]]

Para a previsão dos retornos, empregamos redes neurais LSTM (Long Short-Term Memory) pela sua capacidade de capturar padrões temporais complexos. Redes LSTM são uma variação das redes neurais recorrentes com uma estrutura específica de “portas” que controlam o fluxo de informações, permitindo que a rede selecione e esqueça dados conforme necessário. Esse mecanismo é essencial para dados financeiros, pois distingue padrões relevantes e ignora ruídos, resultando em previsões mais robustas. Por esses motivos, a LSTM é classificada como um dos melhores modelos para previsão e análise de preços de ativos de renda variável, como as ações do S&P500 (Obthong et al, 2020). Cada modelo LSTM é treinado individualmente para cada ação, visando prever o preço dessas ações no próximo período, utilizando como features os retornos logarítmicos, o volume de negociação e uma série de indicadores técnicos, como: 

- **Bandas de Bollinger:** Identificação de reversões de tendência com base na volatilidade em torno da média móvel dos preços. 
- **RSI (Índice de Força Relativa):** Identificação de condições de sobrecompra ou sobrevenda, fornecendo insights sobre o momentum. 
- **ATR (Average True Range):** Cálculo da volatilidade média, útil para capturar oscilações de preço. 
- **Momentum (MOM):** Indicação da velocidade e direção das mudanças de preço, destacando a intensidade dos movimentos. 
- **VIX:** Como indicador de sentimento de mercado, o VIX oferece uma medida da volatilidade esperada, sendo um reflexo das expectativas econômicas.

![[deep-markovian-trader-valorprevisto-preco.png]]

Para implementar nossa estratégia, obtivemos os dados de ações, índices e títulos públicos utilizando a biblioteca Yahoo Finance, e acessamos a lista mais recente de tickers do S&P500 disponível na Wikipedia para coletar os símbolos de cada ação do índice. Com esses dados, aplicamos o modelo inspirado no MSGARCH que desenvolvemos para modelar a volatilidade condicional de cada ação em cada período analisado. Com base na volatilidade condicional modelada, escolhemos para negociação em cada período apenas ações com probabilidade superior a 90% de estarem em regime de baixa volatilidade; caso nenhuma atenda a esse critério, não realizamos operações no período. Para as ações escolhidas, aplicamos o modelo LSTM desenvolvido para prever os retornos do próximo período. Em seguida, para cada ação, calculamos a diferença entre o último e o primeiro retorno previsto, obtendo assim o retorno total de cada uma no período considerado. Em seguida, ordenamos esses retornos totais de forma decrescente e aplicamos nossa regra de investimento: compramos as ações no primeiro percentil dessa diferença ordenada e vendemos aquelas no último percentil.

# 3. Backtest e Resultados

O backtest da estratégia foi desenvolvido em Python 3.14, utilizando bibliotecas como Pandas, yfinance, Numpy e Math. Para realizar o backtest, foram utilizados dataframes contendo os retornos mensais (correspondentes a 20 pregões) previstos pelo modelo LSTM para cada uma das ações selecionadas com base no filtro de volatilidade condicional MSGARCH. Em cada período, os retornos previstos foram ordenados, e as posições compradas foram atribuídas às ações no primeiro percentil, enquanto as posições vendidas foram atribuídas às ações do último percentil. O retorno de cada período foi calculado fazendo a média da média dos retornos das posições compradas com a média dos retornos das posições vendidas. A seguir, apresentamos uma análise dos resultados por meio de gráficos.

![[deep-markovian-trader-retorno-acumulado.png]]

O gráfico acima apresenta a trajetória do retorno acumulado da nossa estratégia comparado ao S&P500. A linha azul, representando a nossa estratégia, mostra crescimento consistente ao longo do tempo, superando o desempenho do índice de mercado, indicado pela linha vermelha. Essa superioridade reflete a eficácia da nossa abordagem. A crescente distância entre as duas linhas evidencia a geração de alfa acumulado, indicando que a estratégia captura oportunidades de valor de forma sustentável. Por fim, vale ressaltar o uso da escala logarítmica no cálculo dos retornos.

![[deep-markovian-trader-retornos-mensais.png]]

Comparando os retornos mensais da nossa estratégia, representados pela linha azul, com os do S&P500, indicados pela linha vermelha, a primeira revela menor vulnerabilidade a quedas acentuadas, especialmente em períodos de alta volatilidade, como no início de 2020, durante a pandemia. Esse comportamento destaca a resiliência da nossa estratégia, que sofre menos em momentos de crise de mercado, reforçando sua robustez em situações de estresse e oscilações bruscas. Além disso, a nossa estratégia frequentemente supera o índice em meses de alta, capturando movimentos positivos de forma expressiva. Isso evidencia que o modelo LSTM identifica oportunidades de crescimento nos ativos selecionados, especialmente em períodos de tendência positiva. Ao focar em ações de menor volatilidade condicional, a estratégia não só minimiza perdas em períodos de crise, mas também aproveita momentos de alta, contribuindo para o desempenho acumulado superior ao observado anteriormente.

![[deep-markovian-trader.png]]

O gráfico **"Histograma dos Retornos Mensais da Estratégia com Curva Normal Ajustada"** mostra a distribuição dos retornos mensais da estratégia em forma de barras azuis, acompanhada de uma curva normal ajustada em vermelho. Esse histograma nos permite visualizar a frequência com que diferentes faixas de retornos ocorrem e comparar essa distribuição com a forma de uma curva normal. A assimetria de 0,44 indica uma leve inclinação à direita, sugerindo maior frequência de retornos acima da média, o que reforça a tendência positiva da estratégia. Com uma curtose de 0,94, a distribuição é ligeiramente achatada, apontando para uma menor incidência de valores extremos e reforçando a estabilidade da estratégia. Esses resultados destacam um perfil de retornos consistentes, com viés positivo e volatilidade controlada.

![[deep-markovian-trader-retornosmensais-sp500.png]]

O gráfico **“Retornos Mensais da Estratégia vs. Retornos Mensais do S&P500 Index”** reforça a resiliência e superioridade da nossa estratégia. A barra azul, representando nossos retornos, destaca menor vulnerabilidade a quedas acentuadas, especialmente em períodos de alta volatilidade, como no início de 2020. Além disso, a estratégia apresenta um retorno médio mensal expressivo de 10,15%, muito superior ao S&P500 (0,93%), aliado a um desvio padrão menor (3,61% contra 5,55%), o que evidencia não apenas um desempenho superior, mas também maior consistência e menor exposição a oscilações extremas. No aspecto de drawdown, enquanto o máximo da nossa estratégia permaneceu em zero, indicando ausência de perdas acumuladas significativas, o S&P500 enfrentou drawdowns acentuados em períodos de crise, refletindo maior instabilidade e exposição a riscos de mercado.

![[deep-markovian-trader-retornos-mensais-sp5002.png]]

No gráfico, **"Relação entre os Retornos Mensais da Estratégia e os Retornos Mensais do S&P500 Index"**, ilustramos a correlação entre os retornos mensais da nossa estratégia e os do S&P500, por meio de um gráfico de dispersão. A linha de tendência, praticamente horizontal, sugere uma baixa correlação entre os resultados da nossa estratégia e os movimentos do mercado representados pelo S&P500. Essa independência é um diferencial valioso, pois indica que a nossa estratégia é capaz de gerar retornos de forma relativamente autônoma em relação ao mercado.

![[deep-markovian-trader-var.png]]

Aqui apresentamos o Valor em Risco (VaR) e o Valor em Risco Condicional (CVaR) da estratégia com um nível de confiança de 95%. Esses indicadores refletem o risco potencial de perda em diferentes cenários. O VaR representa a perda máxima esperada em 95% dos casos, enquanto o CVaR indica a média das perdas que ultrapassam o VaR, fornecendo uma medida do risco em eventos mais extremos. Observando o gráfico, vemos que os valores de VaR e CVaR flutuam pouco ao longo do tempo, mas a média fixa de ambos é próxima de: 3,55 para o VaR e 3,35 para o CVaR. A proximidade entre esses valores sugere que, quando ocorrem perdas além do esperado, elas não são muito diferentes do que o limite previsto pelo VaR. Isso indica que a estratégia consegue controlar bem as perdas e que eventos extremos não geram impactos significativamente maiores.

![[deep-markovian-trader-sharpe.png]]

O gráfico **"Sharpe Ratio da Estratégia vs. Sharpe Ratio do S&P500 ao longo do tempo"** compara o desempenho ajustado ao risco de nossa estratégia (linha azul) com o do S&P500 (linha verde). O Sharpe Ratio mais alto indica uma relação mais eficiente entre retorno e risco, e a linha azul consistentemente acima da verde reflete um desempenho superior da nossa estratégia. Com uma média de 3,96, significativamente superior ao 0,30 do S&P500, a estratégia demonstra sua capacidade de gerar retornos muito mais altos para o mesmo nível de risco. Isso evidencia que nossa abordagem aproveita melhor o risco assumido, entregando resultados mais eficientes em comparação ao benchmark.

![[deep-markovian-trader-margem-erro.png|304]]

A tabela ao lado apresenta um intervalo de erro da previsão, isto é, o quanto o retorno real divergiu do retorno previsto pela LSTM, cujos valores vieram das seis vezes que testamos a rede neural. Observando a tabela, podemos calcular que mais de 85% dos ativos tiveram seus preços previstos com um erro de no máximo 5%. Além disso, não há a presença de outliers com uma alta margem de erro, reforçando a robustez do nosso modelo.

# 4.Conclusão 

Com base nos resultados obtidos, a estratégia apresentou uma performance satisfatória, superando consistentemente o benchmark, com retornos sólidos e menor risco. Essa combinação de desempenho superior e controle de risco é promissora, mas exige uma análise criteriosa para garantir que os fatores que sustentam esses resultados sejam devidamente compreendidos, justificados e sustentáveis ao longo do tempo. Um aspecto crítico identificado é a variabilidade intrínseca às previsões geradas pela rede neural LSTM, devido à inicialização aleatória de seus pesos e ao possível uso do algoritmo gradiente descendente estocástico. Esse comportamento pode gerar variações nos retornos previstos, tornando assim essencial a otimização da configuração da rede para melhorar a estabilidade e reduzir a incerteza nos resultados. Além disso, devido às nossas limitações de poder computacional, não conseguimos gerar um número elevado de amostras das previsões da rede, o que seria crucial para alcançar resultados mais robustos e consistentes. A tabela a seguir ilustra o efeito mencionado, mostrando o Retorno Long/Short (em porcentagem)  associado à previsão número i da LSTM desenvolvida.

![[deep-markovian-trader-conclusion1.png]]

![[deep-markovian-trader-conclusion2.png]]

Adicionalmente, recomenda-se a implementação do modelo MSGARCH no Python, como já disponível em R, para aprimorar o filtro de volatilidade condicional e proporcionar uma análise mais robusta da dinâmica de risco. A otimização dos parâmetros da rede neural e do modelo como um todo (variável setup) também é essencial para refinar ainda mais a precisão das previsões e potencializar os resultados. Embora os retornos observados até o momento sejam promissores, é essencial compreender os fatores que geram retornos de tamanha magnitude com alta consistência. Portanto, recomenda-se fortemente realizar estudos adicionais sobre a metodologia, a fim de consolidar uma base mais sólida para a estratégia, aumentando assim a sua robustez. Além disso, é importante destacar que a estratégia negocia um número pequeno de ações a cada período, o que pode representar um risco significativo, especialmente em termos de liquidez e diversificação. Essa característica deve ser monitorada e ajustada conforme necessário para garantir um equilíbrio adequado entre risco e retorno. Acreditamos que, ao abordar e resolver os problemas mencionados, poderemos desenvolver uma estratégia altamente promissora, não apenas pelos retornos obtidos, mas também pela sua robustez e capacidade de adaptação a diferentes cenários de mercado.

# 5. Referências Bibliográficas 

Zuckerman, G. (2006). O homem que decifrou o mercado: Como Jim Simons criou a revolução quant. Alta Books. 

Ferrer Fernández, M., Henry, Ó., Pybis, S., & Stamatogiannis, M. P. (2023). Can we forecast better in periods of low uncertainty? The role of technical indicators. Journal of Empirical Finance, 71, 112. j.jempfin.2022.12.014 

M. Obthong, N. Tantisantiwong, W. Jeamwatthanachai, and G. Wills, "A Survey on Machine Learning for Stock Price Prediction: Algorithms and Techniques," in Proceedings of the 2nd International Conference on Finance, Economics, Management and IT Business (FEMIB), Southampton, UK, 2020.