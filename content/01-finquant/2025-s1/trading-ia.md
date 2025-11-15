---
title: Estratégias de trading com python
tags:
  - trilha/finquant
  - nivel/avancado
---
_**Autores:** Ana Beatriz Zaparoli · David Leati · Eduardo Lud · Tiago Toledo_
## Introdução

O mercado de criptoativos revolucionou o cenário financeiro com sua natureza digital e descentralizada. Caracterizado por sua constante evolução e alta volatilidade, ele apresenta tanto oportunidades quanto desafios significativos para os investidores. A dificuldade em prever movimentos de preços e identificar momentos ideais de entrada e saída é um problema persistente, que impede muitos participantes de maximizar seus retornos e gerenciar riscos de forma eficaz.

A volatilidade, embora possa gerar ganhos substanciais se as negociações forem feitas no momento certo — o que no jargão cripto é conhecido como _“buy the dip”_ (comprar na baixa) e _“taking profit_” (realizar lucro) — , também pode resultar em perdas significativas se não for gerenciada adequadamente. Vender na baixa e comprar na alta são exemplos clássicos de operações prejudiciais. Essa característica intrínseca do mercado cripto não pode ser ignorada no desenvolvimento de estratégias de investimento.

![[projeto-tiago-1.jpg]]

Nesse contexto dinâmico, o desenvolvimento de estratégias de trading robustas e adaptáveis é crucial. A busca por métodos que possam explorar as ineficiências do mercado, ao mesmo tempo em que mitigam os riscos inerentes, motiva a criação de abordagens inovadoras. Nosso projeto se insere nessa lacuna, buscando desenvolver e comparar duas estratégias distintas para negociação de criptomoedas, visando não apenas a rentabilidade, mas também a resiliência em cenários voláteis.

Neste artigo, compartilhamos o processo de construção de uma estratégia de trading de criptomoedas usando duas abordagens distintas. A primeira é uma estratégia de _pair trading_, que se baseia na exploração de relações de longo prazo entre ativos correlacionados, assumindo que desvios temporários tendem a se corrigir. A segunda abordagem utiliza um modelo de _machine learning_, focado na previsão de retornos e na geração de sinais operacionais. Ambas as estratégias foram desenvolvidas e testadas com dados reais da Binance, utilizando a linguagem Python e bibliotecas de código aberto. Nosso objetivo central foi criar uma estrutura flexível de simulação e otimização que permitisse testar diferentes parâmetros e maximizar o desempenho ajustado ao risco, utilizando o retorno/índice de Sharpe como métrica principal de avaliação, e analisar a viabilidade prática de sua implementação no ambiente volátil das criptomoedas.

## Datasets utilizados

Foram utilizados dados históricos de diversos criptoativos, com séries de preços de fechamento em intervalos de 1 hora até 1 dia, abrangendo um período de 48 meses (2020–2024). A coleta foi realizada por meio da API da Binance, principal exchange global, que desde 2017 mantém a liderança em volume diário de negociação de criptomoedas.

Os arquivos .CSV utilizados seguem este padrão:

● timestamp (em milissegundos)

● open (preço de abertura)

● high (preço máximo naquele candlestick)

● low (preço mínimo naquele candlestick)

● close (preço de fechamento)

```python
from binance.client import Client  
import pandas as pd  
  
# A chave da API não é necessária para pegar dados históricos  
client = Client(api_key='', api_secret='')  
  
# Função para pegar dados históricos de velas  
def get_historical_klines(symbol, interval, start_str=None, end_str=None):  
    return client.get_historical_klines(symbol, interval, start_str, end_str)  
  
symbol = 'BTCUSDT'  
begin_symbols = ['BTC', 'WBTC', 'BNB', 'ETH', 'SOL', 'ADA', 'XRP']  
end_symbol = 'USDT'  
  
interval = Client.KLINE_INTERVAL_1DAY #5MINUTE, 1HOUR, 1DAY, etc  
start_str = '20 Jul, 2023'  
end_str = '20 Jul, 2025'  
  
klines = get_historical_klines(symbol, interval, start_str, end_str)  
  
# Converte os dados para um DataFrame do Pandas  
df = pd.DataFrame(klines,   
                    columns=['timestamp', 'open', 'high', 'low', 'close', 'volume',  
                            #'close_time', 'quote_asset_volume', 'number_of_trades',  
                            #'taker_buy_base_asset_volume', 'taker_buy_quote_asset_volume',  
                            #'ignore'  
                            ] )  
  
# Converte o timestamp para um formato legível  
df['timestamp'] = pd.to_datetime(df['timestamp'], unit='ms')  
  
# Salva o DataFrame em um arquivo CSV  
df.to_csv(f'fechamentos/{symbol}_{interval}_data.csv', index=False)
```

## Escolha das criptomoedas

A seleção das moedas utilizadas na estratégia foi baseada em seu **valor de mercado (_Market Cap_)**. Assim, foram escolhidas as 13 maiores criptomoedas nesse critério. Em seguida, para a estratégia de arbitragem, realizou-se o teste de cointegração entre todos os pares possíveis, a fim de identificar aqueles mais adequados para a formação das estratégias de negociação. Já para o modelo de _machine learning_, os dados foram acrescidos com variáveis derivadas como: retornos, médias móveis, volatilidade histórica, etc.

![[projeto-tiago-2.jpg]]

## Análise exploratória dos dados (estatísticas e gráficos)

Para compreender as análises e gráficos apresentados a seguir, é importante inicialmente observar o comportamento histórico dos valores das criptomoedas selecionadas. Abaixo, são exibidos, como exemplo, os gráficos de duas das moedas que se mostraram cointegradas após uma análise de correlação histórica.

![[projeto-tiago-3.jpg]]

Abaixo, apresenta-se a análise do crescimento do capital inicial da estratégia. O gráfico correspondente ilustra a evolução percentual tanto dos ativos quanto da estratégia de trading no período entre 05/01/2025 e 20/07/2025.

![[projeto-tiago-4.jpg]]

>[!info]
>Observa-se que o capital inicial da estratégia obteve um crescimento aproximado de **40%** ao final da simulação, enquanto os ativos individualmente apresentaram variações bem mais modestas: cerca de **3%** para o Ativo 1 e praticamente **0%** para o Ativo 2

## O que é trading?

O trading é a compra e venda de ativos financeiros com o objetivo de lucrar com flutuações de curto e médio prazo. Exemplos mais comuns de ativos negociados utilizando essa prática são ações, criptomoedas, moedas estrangeiras e commodities.

Como funciona:  
O trader (pessoa que pratica trading) tenta prever o movimento futuro do ativo para abrir posições. Caso acredite que vá subir, ele abre uma posição de compra _(“long”_), e caso acredite que vá cair, ele abre uma posição de venda (_“short”_).

## Tipo de trading:

Existem vários tipos e estratégias de trading, os principais são:

**1. Day Trade:** é o ato de comprar e vender ativos no mesmo dia, ou seja, a posição é aberta e fechada no mesmo dia, buscando lucrar com pequenas variações diárias.

**2. Scalper Trade:** é uma estratégia derivada do _Day Trade_, porém o intervalo de negociações é muito mais curto (segundos ou minutos) e com uma frequência muito maior, com o objetivo de obter pequenos lucros com dezenas ou centenas de operações diárias.

**3. Swing Trade:** é o ato de manter posições por períodos maiores, como dias ou semanas, aproveitando movimentos maiores de mercado, porém ainda em curto.

**4. Position Trade:** é uma estratégia que busca obter lucros com operações de médio prazo, seguindo as tendências do mercado. As posições podem durar semanas, meses ou até alguns anos, porém ainda mantendo o foco a médio prazo.

Ferramentas e análises: Para tomar as decisões, os traders utilizam principalmente 2 tipos de análises:

**1. Análise Técnica:** é o estudo de gráficos de preços e indicadores quantitativos para identificar padrões e prever os movimentos futuros. Sendo mais comum em trades de curto prazo.

**2. Análise Fundamentalista:** é a avaliação da saúde da empresa e do setor, analisando fatores qualitativos, macroeconômicos e notícias do mercado para a tomada de decisão. É mais comum em trades de médio e longo prazo.
## Estratégia de Pair Trading:

A arbitragem estatística, ou _pair trading_, é uma estratégia que busca explorar relações históricas entre dois ativos que apresentam alta correlação ou, sendo um pouco mais específico, séries coestacionárias ou cointegradas.

![[projeto-tiago-5.jpg]]

>[!info]
>Como ilustrado na imagem, durante o período observado, o par de ativos 1 e 2 tende a retornar ao spread médio histórico

A lógica é simples: quando dois ativos se movem juntos ao longo do tempo, desvios temporários nessa relação tendem a se corrigir no longo prazo. Se essa relação for apenas baseada em correlação, os desvios podem ser espúrios; já no caso de séries cointegradas, existe uma base estatística mais sólida que sugere que eventuais afastamentos tendem a se corrigir. Assim, o trader vende o ativo que está relativamente “caro” e compra o que está “barato”, esperando que ambos retornem ao equilíbrio histórico.

No contexto de criptomoedas, essa abordagem pode, por exemplo, aproveitar diferenças momentâneas entre pares como **BTC/BNB.** Em muitos casos, a verificação da **cointegração** é ainda mais relevante do que a correlação, já que séries de preços normalmente não são estacionárias individualmente, mas podem formar uma combinação linear estacionária, caracterizando cointegração.

![[projeto-tiago-7.jpg]]

>[!info]
>A fim de curiosidade, esta figura mostra que a cointegração só permaneceu como condição verdadeira para os pares BNBxLTC durante um período de poucos meses, valendo lembrar que a estratégia de pair trading só ocorre quando estes dois ativos estiverem cointegrados

![[projeto-tiago-8.jpg]]

>[!info]
>Outra coisa interessante de se analisar é que quando usamos janelas muito curtas de cointegração (menos de 120 dias) começamos a ter problemas com falsos positivos (períodos cointegrados de poucos dias). Então é vital usar janelas de tempo bem definidas e que de fato encapsulem os comportamentos da série.

A execução prática envolve três etapas principais:

- **Identificação do par** — seleção de ativos com alta correlação histórica e liquidez adequada;
- **Modelagem da relação** — cálculo de métricas como _spread_ e z-score para identificar desvios estatisticamente relevantes;
- **Operação e reversão** — abertura simultânea de posições opostas (_long/short_)(comprado/vendido) quando o desvio ultrapassa um limite predefinido e fechamento quando a relação retorna ao padrão.  
    O objetivo é obter lucro mesmo em mercados laterais, já que o ganho não depende da direção geral dos preços, mas sim da convergência do par. Essa característica torna o _pair trading_ atrativo em ambientes voláteis e incertos, como o das criptomoedas.

```python
def gerar_sinais(df, zscore_compra_e_venda, zscore_encerrar_posicao, janela, taxa=0.0001):  
    series1 = df['Ativo1']  
    series2 = df['Ativo2']  
  
    limite_superior =zscore_compra_e_venda  
    limite_inferior = -zscore_compra_e_venda  
  
    spread = calcular_spread(series1, series2)  
    rolling_mean, rolling_std, zscore = calcular_zscore(spread, janela) #Zscore com janela movel  
    media_movel_ativo1, media_movel_ativo2, ativo1_std, ativo2_std = calcular_media_ativos(series1, series2, janela) #media movel do ativo 1 e 2  
  
    nomes_posicoes = ["neutro", "compra_1_vende_2", "vende_1_compra_2"]  
    posicao = nomes_posicoes[0]  
  
      
    sinais_compra_e_venda = []  
  
    for i in range(len(df)):  
        linha_df = df.iloc[i]  
  
        if zscore.iloc[i] > limite_superior:  
            posicao = nomes_posicoes[2] #entra vendido no ativo 1 e comprado no 2  
        if zscore.iloc[i] < limite_inferior:  
            posicao = nomes_posicoes[1] #entra comprado no ativo 1 e vendido no 2  
  
  
        if (-zscore_encerrar_posicao < zscore.iloc[i] < zscore_encerrar_posicao):  
            posicao = nomes_posicoes[0] #posicao mantem neutra ou encerra posicao anterior  
  
        sinais_compra_e_venda.append(posicao)  
  
      
    df_sinais.to_excel('resultados/estrategia.xlsx', index=False)  
  
    return df_sinais
```

Para entender a estratégia, o gráfico mais importante é o **z-score do spread**, que é basicamente o spread normalizado entre os dois ativos. Calculamos como: **ativo 1 (normalizado) − ativo 2 (normalizado)**.

- Quando o z-score está **positivo e acima do limite**, a estratégia **vende o ativo 1 e compra o ativo 2**.
- Quando o z-score está **negativo e abaixo do limite**, faz-se o inverso: **compra o ativo 1 e vende o ativo 2**.

![[projeto-tiago-9.jpg]]

>[!info]
>Esta imagem ilustra o código acima, em que, dependendo do z-score, assumimos uma posição e encerramos na expectativa de reversão a média histórica.

O objetivo é obter lucro mesmo em mercados laterais, já que o ganho não depende da direção geral dos preços, mas sim da convergência do par. Mas um dos grandes problemas é que em num ambiente volátil e incerto como o das criptomoedas, relações de cointegração podem facilmente ser quebradas e os pares que antes deveriam convergir acabam se afastando cada vez mais.

E, como mostrado anteriormente, a estratégia somente irá operar em momentos de cointegração, mesmo assim, ao trabalhar com múltiplas moedas, temos muitas oportunidades ao longo do tempo.

![[projeto-tiago-10.jpg]]

>[!info]
>Esta simulação de 2020 a 2025, por exemplo, contou com cerca de 12 moedas, totalizando 66 pares, e, em média, operava com cerca de 3,5 posições abertas simultaneamente.

## Estratégia de Machine Learning:

A estratégia baseada em _Machine Learning_ no Python consiste no uso de modelos de aprendizado supervisionado para prever a direção futura do preço da criptomoeda e, a partir dessas previsões, abrir posições de forma automática. O processo envolve alimentar o modelo com dados históricos do mercado, incluindo preços e indicadores técnicos, para que ele identifique padrões e relações entre variáveis que precedem movimentos específicos do ativo. A partir disso, o modelo é capaz de gerar previsões para novos dados em tempo real, possibilitando decisões de compra ou venda com base em probabilidade e não apenas em regras fixas.

O modelo final adotado nesta análise foi o _XGBoost_ (_eXtreme Gradient Boosting_), selecionado por sua alta capacidade de lidar com múltiplas features, robustez frente a dados ruidosos e velocidade de processamento mesmo em bases extensas. Embora tenham sido avaliados outros modelos, como o MLP (_Multi-Layer Perceptron_) e o LSTM (_Long Short-Term Memory_), estes não foram escolhidos devido à maior complexidade de implementação e à demanda por recursos computacionais mais avançados para testes de maior escala.

Para a construção dessa estratégia foram usados, majoritariamente, as seguintes tecnologias:

- **XGBoost (xgboost):** O **XGBoost** (e_Xtreme Gradient Boosting_) é o modelo de classificação central da nossa estratégia. Ele se destaca por sua alta performance e eficiência, sendo capaz de estimar a probabilidade de um movimento de alta ou baixa com grande precisão. O modelo funciona construindo uma série de árvores de decisão de forma sequencial. Cada nova árvore é treinada para corrigir os erros das árvores anteriores, resultando em um modelo final extremamente robusto e capaz de identificar padrões complexos nos dados financeiros. Sua eficácia e velocidade de processamento o tornam uma escolha popular e confiável para esta análise.
- **MAPIE (mapie):** O MAPIE (_Model Agnostic Prediction Interval_) é um framework que implementa o conceito de previsão conformada (_conformal prediction_). Ele nos permite adicionar uma camada de confiabilidade estatística às previsões do modelo, independentemente do tipo de modelo que estamos usando. Em vez de simplesmente prever se o preço vai subir ou descer, o MAPIE fornece um conjunto de previsão que indica o quão confiável é a previsão. Para cada previsão, o MAPIE cria um conjunto que tem uma probabilidade garantida (por exemplo, 90%) de conter o resultado real. Nossa estratégia só considera sinais quando o MAPIE indica alta certeza, ou seja, um conjunto de previsão contendo apenas uma opção, como {False,True} para subir ou {True,False} para baixar. Sinais de incerteza, como {False, False} ou {True, True}, são descartados, o que é crucial para evitar operações de alto risco.
- **Médias Móveis Simples (SMAs):** As SMAs são utilizadas como um filtro de tendência, atuando como um complemento à previsão do modelo. Nessa estratégia são utilizadas duas SMAs, sendo uma de longo prazo e outra de curto prazo (calculada sobre a de longo prazo, sendo ⅕ dela). O modelo só abre posição quando o preço atual está acima do SMA longo e só fecha quando o preço está abaixo do SMA curto. Esses valores de períodos são modificados de acordo com a moeda analisada, visando o melhor desempenho. Moedas mais voláteis possuem um período menor, pois são mais sensíveis às tendências de mercado (ex: Solana), enquanto moedas menos voláteis possuem um período maior, já que são menos sensíveis (ex: Bitcoin).
- **Aquisição de Dados — API Binance (python-binance):** Para garantir a qualidade e a padronização dos dados, a coleta de informações de OHLCV (abertura, máxima, mínima, fechamento e volume) é feita diretamente da API oficial da Binance.

## Passo a Passo da Estratégia de Machine Learning

O desenvolvimento da estratégia segue um processo bem definido, com etapas lógicas e sequenciais:

1. **Coleta de Dados (API da Binance):** Definimos o ativo e o _timeframe_ (por exemplo, BTCUSDT, 1h) e baixamos os dados via API. Os dados já chegam formatados e sem erros, porém como garantia ocorre a verificação quando os dados são lidos.
2. **Construção de Features:** Esta é uma das etapas mais importantes, nela definimos o que o modelo vai receber para aprender o que define os movimentos de mercado e tentar prevê-lo. O conjunto de features, derivados de indicadores técnicos e outras métricas, inclui:

- **Retorno e Volatilidade:** retorno simples, assimetria dos retornos, curtose dos retornos, volatilidade, retorno acumulado e volatilidade realizada.
- **Volume:** fluxo de dinheiro de Chaikin, saldo de volumes, oscilador de volume e linha de acumulação/distribuição.
- **Osciladores e Momentum:** indicador Williams %R, índice de momentum e oscilador estocástico.
- **Médias e Tendência:** índice de convergência e divergência de médias móveis (MACD), índice direcional médio (ADX) e médias móveis exponenciais.
- **Bandas de Volatilidade:** bandas de Bollinger, incluindo limite superior, limite inferior, largura das bandas e posição do preço dentro das bandas.
- **Outros Indicadores:** índice de força relativa (RSI), faixa verdadeira média (ATR) e o indicador parabólico SAR.
- **Defasagens Temporais:** versões atrasadas de todos os indicadores, permitindo que o modelo capture o comportamento recente do mercado.
- **Horizontes de Tempo:** todos os indicadores são calculados em diferentes prazos, abrangendo curto, médio e longo prazo.

**3. Divisão Temporal dos Dados (K-Fold Cross Validation):** Para que o modelo aprenda padrões temporais de forma mais robusta e sua performance seja avaliada de maneira mais precisa em vários cenários de mercado, utilizamos a validação cruzada temporal (_Time Series K-Fold Cross Validation_). Nessa abordagem, os dados são divididos em “k” partições, sempre respeitando a ordem cronológica, algo crucial em análise de séries temporais.

O treino ocorre conforme a imagem abaixo:

![[projeto-tiago-11.jpg]]

4. **Treinamento do Modelo (XGBoost):** O modelo é treinado para prever a probabilidade de alta/baixa. Seus **hiperparâmetros** são ajustados para otimizar o desempenho do modelo. Os principais são:

- **n_estimators:** Define o número de árvores de decisão a serem construídas. Um valor maior geralmente melhora o desempenho, mas pode aumentar o tempo de treinamento.
- l**earning_rate**: Controla o quão rapidamente o modelo aprende. Valores menores tornam o processo mais lento, mas podem levar a uma solução mais robusta.
- **max_depth:** Limita a profundidade de cada árvore, ajudando a controlar o _overfitting_.
- **subsample:** A porcentagem de amostras usadas para treinar cada árvore. Ajuda a reduzir a variância do modelo.
- **colsample_bytree:** A porcentagem de features (colunas) usadas para treinar cada árvore, também auxiliando no controle do _overfitting_.
- **gamma:** Define o ganho mínimo necessário para a realização de uma nova partição em uma folha da árvore.
- **reg_lambda e reg_alpha:** São parâmetros de regularização que penalizam a complexidade do modelo, prevenindo o overfitting.
- **early_stopping_rounds:** Permite parar o treinamento se o desempenho no conjunto de validação não melhorar por um certo número de rodadas, economizando tempo e evitando o _overfitting_.
- **scale_pos_weight:** Ajuda a lidar com classes desbalanceadas (usado para equilibrar o modelo durante períodos de mudanças unilaterais).

**5. Estimativa de Incerteza (MAPIE):** Após o treinamento, o modelo é ajustado pelo MAPIE, que gera o conjunto de previsão e permite filtrar os sinais de baixa confiança. O MAPIE funciona de forma agnóstica ao modelo, o que significa que pode ser aplicado a qualquer classificador. A biblioteca usa uma técnica de validação no conjunto de calibração para determinar o tamanho ideal do conjunto de previsão. Esse processo garante que o conjunto gerado para cada nova previsão contenha o valor real com um nível de confiança especificado, tornando as decisões de trading mais seguras.

**6. Filtro de Tendência (SMAs):** As médias móveis são calculadas para atuar como um filtro adicional, garantindo que as operações estejam alinhadas com a tendência de longo prazo do mercado.

**7. Geração de Sinais e Regras de Execução:** Com base nas previsões do XGBoost, nos conjuntos do MAPIE e nos filtros das SMAs, os sinais operacionais são convertidos em decisões de compra, venda ou de manter a posição. Os custos de _fee_ também são considerados nesta etapa.

**8. Backtesting:** A estratégia é simulada em dados históricos que o modelo nunca viu, e seu desempenho é medido utilizando esses mesmos dados não vistos. As métricas de **_accuracy, precision, recall_, F1, AUC-ROC** e o retorno acumulado são comparados com a estratégia de _buy and hold_ para avaliar sua eficácia.

9.**Simulação Fora da Amostra (“dados não vistos”):** Uma simulação final é realizada em um período de dados subsequente ao _backtest_ para validar a robustez e a consistência dos resultados. Nessa etapa o modelo não é treinado novamente, como ocorre durante a etapa de validação cruzada.

**10. Monitoramento e Registro:** Por fim, todas as operações e resultados são registrados. É um passo crucial para acompanhar o desempenho da estratégia e identificar a necessidade de recalibrar o modelo ao longo do tempo.

## Avaliação de risco e métricas de desempenho

Para assegurar uma análise completa e rigorosa da performance das nossas estratégias de trading algorítmico, implementamos um conjunto robusto de métricas de desempenho e risco. A simples avaliação do retorno bruto não é suficiente para determinar a eficácia de uma estratégia em um mercado tão volátil quanto o de criptoativos. Por isso, a combinação de indicadores se tornou essencial para proporcionar uma visão mais realista e abrangente sobre a viabilidade e a robustez das abordagens propostas, especialmente ao comparar a estratégia de pair trading com o modelo de machine learning.

A avaliação das estratégias foi realizada com base em indicadores amplamente reconhecidos no campo de finanças quantitativas, focando na combinação de retornos com a exposição ao risco.

- **Retorno Total/Acumulado:** Esta métrica fundamental quantifica o ganho percentual global obtido pela estratégia ao longo de todo o período de simulação. Ela reflete o crescimento do capital inicial e é um primeiro indicador do potencial de lucratividade da abordagem.
- **Volatilidade (Desvio Padrão dos Retornos):** A volatilidade mede o grau de flutuação dos retornos da estratégia. Um desvio padrão elevado indica maior dispersão dos retornos e, consequentemente, um risco maior. Sua análise é crucial em mercados de alta oscilação como o de criptoativos, pois revela a consistência dos ganhos e perdas diárias ou horárias.
- **_Drawdown_ (Rebaixamento Máximo):** O _drawdown_ é uma métrica crítica para a gestão de risco, indicando a maior queda percentual do pico de capital de uma estratégia até o ponto mais baixo subsequente, antes que um novo pico seja atingido. Ele quantifica a perda máxima que um investidor teria que suportar em um determinado momento, sendo um forte indicador da resiliência da estratégia em cenários de mercado adversos. Sua análise foi fundamental para compreender os riscos de perdas significativas inerentes a cada estratégia.
- **Índice de Sharpe:** Considerado uma das métricas mais importantes na avaliação de performance ajustada ao risco, o Índice de Sharpe calcula o retorno excedente da estratégia (acima de uma taxa de retorno livre de risco) por unidade de risco (volatilidade).
 $$
IS = \frac{R_A - r_f}{\sigma_A}
$$
**Onde:**
- $R_A$: Retorno da Estratégia
- $r_f$: Retorno do ativo livre de risco
- $\sigma_A$: Volatilidade da Estratégia


>[!info]
>Quanto maior o Índice de Sharpe, melhor é a relação entre o retorno gerado e o risco assumido. Essa métrica foi central para comparar a eficiência das estratégias de _pair trading_ e _machine learning_, permitindo identificar qual delas oferecia um desempenho superior considerando o nível de risco envolvido.

## Resultados da estratégia de Arbitragem:

O modelo de arbitragem, em sua forma inicial, mostrou-se altamente ineficiente para lidar com quebras na cointegração durante períodos de alta volatilidade. Em diversos momentos, acabou apostando em reversões que nunca ocorreram, resultando em retornos que variaram entre **-15% e -60%**. Como exemplo, uma simulação apresentou **drawdown de 50%** e retorno acumulado de **-28% em quatro anos**, evidenciando o risco excessivo da abordagem original.

![[projeto-tiago-12.jpg]]

>[!info]
>Inicialmente a estratégia assumia um risco gigantesco e tinha retorno negativo.

Para mitigar esses problemas, foram adicionados alguns filtros de segurança. Foram adotadas medidas que protegem contra **overtrading em spreads com muito ruído**, exigindo não apenas um desvio estatístico relevante (z-score), mas também uma **qualidade mínima do par** (alta correlação e baixa volatilidade do spread), reduzindo entradas em séries possivelmente espúrias. Além disso, utiliza um **filtro de RSI (**_Relative strength index_**)** para bloquear operações em situações de sobrecompra ou sobrevenda, o que evita entrar contra tendências muito fortes (como estava acontecendo anteriormente).

Por fim, obtivemos os seguintes resultados:

![[projeto-tiago-13.jpg]]

![[projeto-tiago-14.jpg]]

![[projeto-tiago-15.jpg]]

>[!info]
>Retorno final de apenas 2,5% do dia 01/01/2020 até 01/01/2025.

![[projeto-tiago-16.jpg]]

Mesmo com essas melhorias — que reduziram bastante o risco e eliminaram os retornos negativos — a estratégia continuou inconsistente, apresentando **drawdown de 12% e retorno acumulado de apenas 2,5%**. Alguns pares se beneficiaram significativamente, alcançando **mais de 120% de retorno**, enquanto muitos outros registraram resultados negativos. Isso mostra a limitação de um **modelo heurístico**, baseado em regras fixas como “comprar se o z-score cair abaixo de X e vender se voltar a Y”, que não se adapta sozinho às mudanças do mercado. Ainda mais em um mercado como o de criptomoedas, com **alta volatilidade e padrões imprevisíveis**, esse tipo de modelo tende a falhar, mostrando que são necessários ajustes mais sofisticados para lidar com essas condições.

## Resultados da estratégia de Machine Learning:

A estratégia de _Machine Learning_, de forma geral, apresentou um desempenho satisfatório. Mesmo com uma variação de desempenho significativa entre os ativos analisados, a abordagem provou seu valor ao superar consistentemente o benchmark de _“Buy_ & _Hold”_ em vários casos.

Foi feita análise com 13 criptomoedas diferentes, porém apenas as 8 a seguir tiveram resultados relevantes.

**Análise dos Sucessos:** O modelo foi extremamente eficaz para **Solana (SOL), Bitcoin Cash (BCH), Ripple (XRP) e Litecoin (LTC)**. Nestes casos, a estratégia não apenas entregou retornos acumulados superiores, mas também demonstrou uma melhor gestão de risco, mitigando as perdas durante períodos de baixa do mercado (_drawdowns_). O resultado para Solana foi o mais expressivo, com a estratégia gerando ganhos exponenciais em comparação com a abordagem passiva.

**Análise das Falhas:** Em contrapartida, o _backtest_ revelou uma clara ineficiência do modelo para **BNB e Cardano (ADA)**. Para estes ativos, a estratégia se mostrou excessivamente conservadora, falhando em capitalizar sobre os fortes ciclos de alta. Consequentemente, o retorno foi ínfimo quando comparado ao crescimento explosivo que teria sido obtido com o _“Buy_ & _Hold”_.

**Análise de Desempenho Misto:** Para os ativos de maior capitalização, **Bitcoin (BTC) e Ethereum (ETH)**, a estratégia apresentou um resultado misto. Embora tenha navegado de forma semelhante ao mercado durante a maior parte do tempo, não conseguiu estabelecer uma vantagem sustentável, ficando ligeiramente atrás do _“Buy_ & _Hold”_ no período final de validação.

**Conclusão dos Resultados:** Os resultados indicam que a viabilidade do modelo de _Machine Learning_ não é universal, mas sim dependente da adaptabilidade dos hiperparâmetros. As dinâmicas de mercado, volatilidade e padrões de preço de certos criptoativos foram mais bem decifradas pelo modelo, enquanto para outros, a complexidade ou a força da tendência tornaram a previsão ineficaz.

## **Análise individual:**

### 1. Bitcoin (BTCUSDT)

- **Análise:** O desempenho da estratégia e do _Buy_ & _Hold_ foram muito semelhantes durante a maior parte do período histórico. Em alguns momentos, a estratégia conseguiu reduzir perdas, mas em outros, não capturou totalmente as altas do mercado.
- **Veredito:** **Desempenho Misto/Inferior.** No período _“Out-of-Sample”_, a estratégia de _Buy_ & _Hold_ mostrou um retorno superior, indicando que, para o Bitcoin, o modelo não conseguiu gerar um alfa consistente e seria mais vantajoso apenas ter mantido o ativo.

![[projeto-tiago-17.jpg]]

![[projeto-tiago-18.jpg]]

### 2. Ethereum (ETHUSDT)

- **Análise:** Assim como no Bitcoin, a performance da estratégia para o Ethereum foi bastante próxima à do _Buy_ & _Hold_. A estratégia parece ter navegado um pouco melhor nos períodos de baixa, com _drawdowns_ (quedas) menos acentuados, mas também ficou atrás durante as fortes altas.
- **Veredito:** **Desempenho Misto/Inferior.** No período de teste final (_“Out-of-Sample”_), o _Buy_ & _Hold_ novamente superou a estratégia, que não conseguiu acompanhar o ímpeto do mercado.
 
![[projeto-tiago-19.jpg]]

![[projeto-tiago-20.jpg]]

### 3. Solana (SOLUSDT)

- **Análise:** Este é o caso de maior sucesso para o modelo. A estratégia superou massivamente o _Buy_ & _Hold_ durante quase todo o período, incluindo uma performance espetacular no período _“Out-of-Sample”_. O modelo conseguiu identificar e se beneficiar da forte tendência de alta da Solana de forma muito mais eficaz.
- **Veredito:** **Desempenho Muito Superior.** A estratégia gerou retornos exponencialmente maiores, provando ser extremamente eficaz para este ativo.

![[projeto-tiago-21.jpg]]

![[projeto-tiago-22.jpg]]

### 4. Ripple (XRPUSDT)

- **Análise:** A estratégia demonstrou uma clara vantagem sobre o _Buy_ & _Hold_. Ela conseguiu capturar os movimentos de alta e, crucialmente, proteger o capital durante as quedas e longos períodos de lateralização do XRP. O gráfico da estratégia é visivelmente mais suave e consistentemente ascendente.
- **Resultado:** **Desempenho Superior.** O modelo foi bem-sucedido, entregando retornos mais altos com uma aparente redução de risco em comparação com simplesmente manter o ativo.

![[projeto-tiago-23.jpg]]

![[projeto-tiago-24.jpg]]

### 5. Bitcoin Cash (BCHUSDT)

- **Análise:** A estratégia apresentou um resultado significativamente melhor que o _Buy_ & _Hold_. Enquanto o _Buy_ & _Hold_ teve um retorno modesto e volátil, a estratégia mostrou um crescimento muito mais robusto e consistente, especialmente a partir de 2023 e continuando no período _“Out-of-Sample”_.
- **Resultado:** **Desempenho Superior.** O modelo de _Machine Learning_ conseguiu extrair valor de forma consistente do BCH, superando com folga a estratégia passiva.

![[projeto-tiago-25.jpg]]

![[projeto-tiago-26.jpg]]

### 6. Litecoin (LTCUSDT)

- **Análise:** A estratégia se mostrou superior ao _Buy_ & _Hold_ na maior parte do tempo. O modelo foi particularmente eficaz em evitar as perdas profundas que o _Buy_ & _Hold_ sofreu entre meados de 2021 e o final de 2023. Embora não tenha capturado o pico máximo em 2021, a gestão de risco resultou em um retorno acumulado maior no final do período.
- **Resultado:** **Desempenho Superior.** A capacidade de mitigar perdas foi o grande diferencial, tornando a estratégia mais lucrativa a longo prazo.

![[projeto-tiago-27.jpg]]

![[projeto-tiago-28.jpg]]

### 7. BNB (BNBUSDT)

- **Análise:** Este é um caso claro de falha do modelo. A estratégia de _Buy_ & _Hold_ para o BNB foi imensamente mais lucrativa. O modelo de _Machine Learning_ gerou um retorno quase irrelevante em comparação com a valorização explosiva do ativo.
- **Resultado:** **Desempenho Muito Inferior.** A estratégia falhou completamente em capturar o potencial de crescimento do BNB, tornando o _Buy_ & _Hold_ a escolha indiscutivelmente melhor.

![[projeto-tiago-29.jpg]]

![[projeto-tiago-30.jpg]]

### 8. Cardano (ADAUSDT)

- **Análise:** Semelhante ao BNB, a estratégia para Cardano teve um desempenho muito fraco. Ela não participou da gigantesca alta de 2021 e, desde então, gerou retornos mínimos. O _Buy_ & _Hold_, mesmo com sua alta volatilidade e quedas acentuadas, foi ordens de magnitude mais rentável.
- **Resultado:** **Desempenho Muito Inferior.** O modelo não foi eficaz para o ADA, e um investidor teria tido um resultado drasticamente melhor apenas mantendo a criptomoeda.

![[projeto-tiago-31.jpg]]

![[projeto-tiago-32.jpg]]

## Conclusão e possíveis melhorias no código:

Os resultados obtidos evidenciam diferenças importantes entre as abordagens testadas. A estratégia de arbitragem estatística (_pair trading_), apesar de se mostrar teoricamente robusta em contextos de cointegração, apresentou desempenho limitado na prática. No período analisado (4 anos), o retorno acumulado foi de apenas **2,5%**, refletindo a dificuldade de capturar ganhos consistentes em um mercado marcado por fortes tendências.

Um dos principais problemas observados foi justamente a incapacidade da estratégia em lidar com períodos prolongados de desvios que nunca retornaram à média histórica, o que comprometeu sua eficácia. Além disso, a definição de janelas de cointegração confiáveis mostrou-se um desafio: janelas curtas geraram inúmeros falsos positivos, enquanto janelas muito longas tornaram a estratégia pouco responsiva às mudanças do mercado.

Para mitigar essas limitações, algumas possíveis melhorias seriam:

- **Incorporação de métricas adicionais de risco** (como ATR — _Average True Range_) para calibrar tamanhos de posição e pontos de entrada/saída;
- **Implementação de _stop-loss_ e _take-profit_ dinâmicos**, de modo a evitar perdas excessivas quando as séries deixam de convergir;
- **Testes com diferentes metodologias de seleção de pares**, além da simples cointegração, como filtros baseados em liquidez e regime de volatilidade.

Já para o modelo de _Machine Learning_, para aumentar a robustez e a consistência da estratégia, o foco futuro deve ser em:

- **Identificação de Tendência:** Substituir indicadores simples (como médias móveis simples) por sistemas que analisem a força da tendência e o regime de mercado, entrando de forma mais robusta nas posições e evitando ruídos de mercado;
- **Aprimoramento do Modelo e das Features:** Enriquecer o modelo com dados mais preditivos, como métricas on-chain e análise de sentimento para aumentar a precisão das previsões;
- **Controle de Volatilidade:** Implementar um dimensionamento de posição dinâmico, ajustando o capital alocado em cada operação com base na volatilidade atual do mercado.

## Referências:
- [https://www.sciencedirect.com/science/article/abs/pii/S0275531920304050](https://www.sciencedirect.com/science/article/abs/pii/S0275531920304050?utm_source=chatgpt.com)
- [https://www.sciencedirect.com/science/article/pii/S1042443122000610](https://www.sciencedirect.com/science/article/pii/S1042443122000610)
- [https://youtu.be/Mj9Ml-HPqWI?si=0QHA0Vz2hsoQ81IQ](https://youtu.be/Mj9Ml-HPqWI?si=0QHA0Vz2hsoQ81IQ)
- [https://xgboost.readthedocs.io/en/stable/index.html](https://xgboost.readthedocs.io/en/stable/index.html)
- [https://medium.com/data-hackers/aplicando-previs%C3%A3o-conforme-em-modelos-de-classifica%C3%A7%C3%A3o-a26b2805ab0](https://medium.com/data-hackers/aplicando-previs%C3%A3o-conforme-em-modelos-de-classifica%C3%A7%C3%A3o-a26b2805ab0)
- [https://youtu.be/vV12dGe_Fho?si=GYACKbsWvtHXoEOq](https://youtu.be/vV12dGe_Fho?si=GYACKbsWvtHXoEOq)
- [https://arxiv.org/html/2306.08157v2](https://arxiv.org/html/2306.08157v2)

