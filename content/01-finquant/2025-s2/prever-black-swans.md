---
title: Robô Kairos
tags:
  - trilha/finquant
  - nivel/avancado
---
_**Autores:** David Leati · Felipe Santana · Gustavo Katsuo Tsutsui_

<div style="text-align: center;">

  <img src="image-removebg-preview.png" width="100">

</div>

## Explicação do Nome: 
O nome vem da filosofia grega e representa o “momento certo”, o instante oportuno em que agir faz toda a diferença. A ideia é usar Inteligência Artificial justamente para identificar esses momentos excepcionais no mercado: em vez de reagir a qualquer oscilação de preço ou indicador, o robô busca reconhecer mudanças de regime e anomalias fortes no índice de IA, ele passa a agir apenas quando acredita que o contexto oferece uma oportunidade verdadeiramente assimétrica.
## Explicação Lógica da Estratégia:
É uma estratégia de detecção de anomalias de cauda aplicada a um universo temático de IA (AI-15), utilizando dados de mercado de alta frequência. Ela se baseia em um LSTM Autoencoder treinado em dados intra-diários de 1 minuto, em períodos considerados “normais”, com o objetivo de apreender a dinâmica típica do mercado em regime não-crítico. A partir desse modelo, é calculado para cada janela de tempo um erro de reconstrução, que é convertido em um sinal de anomalia por meio de um limiar (threshold) dinâmico, ajustado com janelas móveis longas para se adaptar ao regime de volatilidade. Em seguida, um filtro de histerese temporal agrupa sinais próximos no tempo, reduzindo ruídos e concentrando a atividade do robô em poucos eventos robustos de estresse. Esses eventos são então mapeados para o universo AI-15, composto por 15 ações diretamente ligadas à temática de IA, gerando um sinal diário de anomalia sobre esse índice temático. Quando esse sinal indica uma anomalia forte e persistente, a estratégia ativa um hedge de risco de cauda sobre a exposição ao tema de IA, reduzindo o beta, montando posições mais defensivas ou comprando convexidade em índices amplos e volatilidade, com o objetivo de preservar capital em crises e capturar retornos assimétricos em grandes correções de mercado.

![[image-removebg-preview(3).png|300]]

### 1. Origem da Ideia
Nos últimos anos, foi-se observado uma verdadeira corrida pela Inteligência Artificial, empresas de IA, semicondutores e infraestrutura digital passaram a concentrar fluxo de capital, revisões de expectativa e uma valorização fortíssima em seus papéis. Esse movimento abriu uma forte reflexão: até que ponto essa valorização reflete fundamentos, é uma grande euforia do mercado ou mesmo uma bolha em formação? Em vez de analisar empresa a empresa, surgiu a vontade de construir uma forma sistemática de identificar quando o mercado de IA, como um todo, entra em um estado “diferente do normal” e usar esses períodos como gatilho para a tomada de risco.

Do lado conceitual, a ideia foi influenciada pela literatura acadêmica sobre anomalias de mercado e mudanças de regime, bem como pelas aplicações de Autoencoders em detecção de anomalias em outras áreas, como crédito, fraude e séries de sensores. A capacidade desses modelos em capturar padrões não lineares complexos foi um diferencial direto para sua escolha, tendo vista que ele preenche lagunas deixadas pelas abordagens econométricas tradicionais, uma vez que tendem a suavizar ou não enxergar padrões dos dados. A combinação entre esse contexto de mercado, marcado por possível euforia em torno de IA, e essas referências técnicas foi o que deu origem à proposta de trazer um modelo Autoencoder para o universo do índice de IA, com o objetivo de mapear quando o comportamento do mercado se afasta do seu padrão usual

### 2. Ideia de Investimento
A ideia central foi utilizar técnicas de Deep Learning para identificar regimes de mercado anômalos no universo de empresas de IA. Em um primeiro momento, formulamos a hipótese de que esses episódios de anomalia, detectados por um modelo do tipo LSTM Autoencoder, representariam exageros de preço e, portanto, abririam espaço para estratégias de reversão à média: sempre que o sinal de anomalia aparecesse, a posição recomendada seria vendida (short) no índice AI-15.

Nos testes históricos, essa hipótese não se confirmou e o desempenho foi negativo, o que nos levou a reavaliar a leitura econômica do sinal. A análise dos episódios marcados como “anômalos” revelou um padrão oposto ao imaginado, os picos de anomalia não antecediam quedas, mas ao início de movimentos fortes de alta, próximos a breakouts. Em outras palavras, o que interpretávamos como indício de estresse e futura correção estava, na prática, sinalizando pontos de aceleração de tendência.

Diante disso, a estratégia foi pivotada. Mantivemos a ideia de usar o sinal de anomalia como marcador de mudança de regime, mas invertendo a interpretação: a anomalia deixa de ser vista como alerta de reversão e passa a ser tratada como gatilho de momentum. A tese final foi se comprar a anomalia, isto é, tomar posição comprada no AI-15 justamente quando o modelo indica que o mercado se afastou de forma excepcional do seu comportamento usual.
### 3. Universo e Dados
O universo de investimento da estratégia é o Índice AI-15, construído a partir de 15 empresas globais ligadas à Inteligência Artificial, semicondutores e infraestrutura digital (por exemplo, NVDA, MSFT, GOOGL, AMZN, PLTR, AMD, TSM, AVGO, TSLA, META, entre outras). Os dados de preços ajustados e volumes dessas empresas foram obtidos via a API do yfinance e por um banco de dados do Kaggle. Eles estão em frequência diária, sendo a partir da data inicial de 2017, garantindo uma janela suficientemente para caracterizar um regime “normal” de treinamento e um período recente para teste fora da amostra.

Além das séries das componentes do AI-15, foram incorporadas variáveis de contexto de mercado (como o S&P 500 e a taxa de juros soberana de 10 anos dos EUA) e informações de fundamentos (lucro por ação, EPS, das empresas do índice). A partir dessas informações, foram construídos vetores de features diários que procuram capturar diferentes dimensões da dinâmica do índice: (i) preço e retorno, incluindo retornos em múltiplos horizontes e distâncias em relação a médias móveis, para descrever direção e magnitude dos movimentos; (ii) volatilidade e risco, com volatilidade realizada em janelas distintas, amplitudes intradiárias e medidas relacionadas a drawdowns, permitindo discriminar regimes mais calmos de fases de estresse; (iii) liquidez e fluxo, derivadas de volume e volume relativo à média recente, refletindo a intensidade do fluxo de negociação; (iv) variáveis de contexto, baseadas no comportamento do mercado amplo e da curva de juros, para diferenciar choques específicos do setor de IA de movimentos macro mais difusos; e (v) fundamentos, via trajetória de EPS, como proxy da tendência de lucros das componentes ao longo do tempo.

No pré-processamento, as séries foram alinhadas em um calendário único, observações duplicadas foram removidas, dias com falhas relevantes de dados foram descartados e lacunas pontuais em variáveis de contexto foram tratadas com métodos conservadores de imputação (como forward fill em séries de índices e taxas). Em seguida, todas as variáveis numéricas foram normalizadas com StandardScaler, de modo que cada feature passasse a ter média aproximadamente zero e desvio-padrão unitário no período de referência. Esse escalonamento garante que nenhuma dimensão domine o treinamento do modelo de IA apenas por diferenças de escala e torna o problema de otimização mais estável ao longo das épocas de treinamento do LSTM Autoencoder.
### 4. Regra de Investimento
A estratégia é implementada de forma totalmente sistemática, em frequência diária, sobre o índice de empresas de IA (AI-15). O modelo de Deep Learning não gera diretamente ordens de compra ou venda. Ele produz apenas um escore de anomalia, a partir do qual a regra de trade é definida. A construção desse sinal começa com uma série temporal multivariada $x_t \in \mathbb{R}^d$, composta por retornos, medidas de volatilidade e variáveis de microestrutura do índice em frequência intradiária, previamente normalizadas. Essa série é segmentada em janelas deslizantes de comprimento $L = 30$ observações, de modo que cada janela $X_t = (x_{t-L+1}, \ldots, x_t)$ representa a trajetória recente do índice.

Sobre essas janelas, treinamos um LSTM Autoencoder com dimensão oculta igual a $64$ em um período considerado “normal” do mercado, anterior ao início da janela de teste. O modelo aprende a reconstruir janelas típicas desse regime. No período de operação, para cada nova janela $X_t$, o autoencoder gera uma reconstrução $\hat X_t$. O Erro de Reconstrução da janela é definido como a média do erro quadrático entre entrada e saída:

$$
ER_t = \frac{1}{L d} \sum_{i=1}^{L} \sum_{j=1}^{d} \bigl(x_{t-L+i,j} - \hat x_{t-L+i,j}\bigr)^2.
$$

Esses erros por janela são então agregados em base diária, resultando em uma série $ER^{\text{dia}}_t$ que mede “quão anômalo” foi o comportamento do índice em cada dia do período de teste. A distribuição de $ER^{\text{dia}}_t$ no período de referência é utilizada para calibrar um limiar fixo $\tau$; no modelo campeão, esse limiar corresponde aproximadamente ao percentil $95$ dos erros diários, de modo que dias com $ER^{\text{dia}}_t > \tau$ são classificados como anomalias fortes.

A partir desse sinal, definimos a regra de posição. Denotando por $P_t \in \{0,1\}$ o estado de posição no final do dia $t$ ($0 =$ fora, $1 =$ comprado) e por $w$ a fração de capital alocada em uma posição cheia (no nosso caso, $w = 0{,}9$), a estratégia opera apenas em dois modos: totalmente fora do mercado ou aproximadamente $90\%$ comprada no AI-15, sem alavancagem e sem posições vendidas. No fechamento de cada dia $t$, computa-se o erro de reconstrução diário $ER_t$ com base apenas em informações disponíveis até aquele momento e verifica-se se ele supera o limiar $\tau$. Se $P_t = 0$ (não há posição aberta) e $ER_t > \tau$, o dia é classificado como anômalo e gera-se um sinal de entrada. A execução ocorre em $t+1$, quando é aberta uma posição comprada no índice com peso $w$, passando o estado para $P_{t+1} = 1$. Enquanto $P_t = 1$, recalculamos $ER_t$ diariamente. Quando o erro retorna à região considerada normal, isto é, $ER_t \le \tau$, gera-se um sinal de saída, e em $t+1$ a posição é integralmente encerrada, retornando a $P_{t+1} = 0$. Em termos compactos, a regra resume-se a comprar o AI-15 em $D+1$ sempre que o erro de reconstrução de hoje excede o limiar de anomalia e estamos fora do mercado, e zerar a posição em $D+1$ sempre que o erro volta abaixo desse limiar enquanto estamos comprados.
### 5. Resultados
#### Gráfico 1 

![[Imagem do WhatsApp de 2025-11-04 à(s) 23.01.31_1a712059.jpg]]

  
O gráfico 1 oferece uma validação visual direta da tese de investimento. Nele, o eixo esquerdo mostra o preço do Índice AI-15 (linha cinza), enquanto o eixo direito exibe o sinal de IA, medido pelo erro de reconstrução do Autoencoder (linha vermelha). A linha verde tracejada representa o limiar de anomalia, definido como o percentil 95 da distribuição histórica do erro de reconstrução e utilizado como gatilho de compra.

Observa-se que os principais picos do sinal vermelho acima do limiar verde, os momentos em que a IA enxerga o regime atual como “anomalia”, não antecedem movimentos de queda, mas se concentram justamente nas fases de forte aceleração da tendência de alta do índice. Em outras palavras, o alto erro de reconstrução não está capturando um estado de “pânico” ou reversão iminente, e sim um regime de momentum extremo, no qual o mercado se afasta do padrão considerado “normal” pelo modelo. Ao configurar a estratégia para comprar nesses episódios de anomalia (em vez de vender, como na formulação original), o portfólio passa a “surfar” esses ralis de momentum, o que se reflete no resultado agregado do backtest (+33,27%).
#### Tabela 1 

| Teste | Limiar (Percentil) | Retorno Total | Drawdown Máx. | Sharpe Ratio |
| ----- | ------------------ | ------------- | ------------- | ------------ |
| 3.A   | 0,90 (Agressivo)   | +38,83%       | 13,63%        | 0,784        |
| 2.A   | 0,95 (Campeão)     | +33,27%       | 2,18%         | 0,916        |
| 3.B   | 0,98 (Conservador) | +6,73%        | 2,03%         | 0,417        |
  
A Tabela 1 resume o efeito da escolha do limiar de anomalia na relação risco–retorno da estratégia.  
O teste 3.A (0,90) representa uma configuração mais agressiva: o limiar mais baixo gera mais sinais, resultando no maior retorno total da amostra (+38,83%), porém ao custo de um drawdown máximo significativamente mais elevado (13,63%) e de um Sharpe Ratio inferior ao do modelo campeão. Já o teste 3.B (0,98) é excessivamente conservador: o limiar muito alto filtra quase todos os eventos, reduzindo o risco, mas também o potencial de ganho, com retorno total modesto (+6,73%) e eficiência de risco relativamente baixa (Sharpe 0,417).

O teste 2.A (0,95) se destaca como ponto de equilíbrio: mantém um retorno substancial (+33,27%) com drawdown máximo muito contido (2,18%) e o melhor Sharpe Ratio da comparação (0,916). Isso indica que o percentil 0,95 é um limiar suficientemente alto para focar apenas em anomalias realmente extremas, mas ainda frequente o bastante para gerar ganho econômico relevante, sendo, portanto, adotado como limiar ótimo da estratégia.
#### Tabela 2

| Teste | Seq_Length   | Retorno Total | Drawdown Máx. | Sharpe Ratio |
| ----- | ------------ | ------------- | ------------- | ------------ |
| 4.A   | 15 (Curto)   | +12,23%       | 11,10%        | 0,537        |
| 2.A   | 30 (Campeão) | +33,27%       | 2,18%         | 0,916        |
| 4.B   | 60 (Longo)   | -10,55%       | 21,05%        | -1,181       |

A Tabela 2 analisa o impacto do comprimento da janela temporal (Seq_Length) na performance da estratégia.

No teste 4.A, com 15 dias, o modelo passa a reagir de forma muito sensível às variações de curto prazo: o retorno total é positivo (+12,23%), mas o drawdown máximo é elevado (11,10%) e o Sharpe Ratio (0,537) é bem inferior ao do modelo campeão. Em termos práticos, a memória curta torna o sinal mais “ruidoso”, gerando mais operações e maior exposição a falsos positivos.

No extremo oposto, o teste 4.B, com 60 dias, produz um modelo excessivamente “lento”. A janela longa suaviza demais as mudanças de regime: o sinal deixa de reagir a transições relevantes e a estratégia passa a apresentar retorno negativo (-10,55%) com drawdown expressivo (21,05%) e Sharpe fortemente negativo (-1,181).

O teste 2.A, com 30 dias, se destaca como ponto ótimo de memória. Essa configuração entrega o maior retorno total (+33,27%), combinado a drawdown muito baixo (2,18%) e Sharpe 0,916, superando com folga as alternativas. Ou seja, 30 dias fornecem memória suficiente para o modelo capturar a estrutura de regime sem se tornar lento a ponto de perder as oportunidades de anomalia – equilibrando estabilidade do sinal e capacidade de resposta.
#### Tabela 3

| Teste | Hidden_Dim     | Retorno Total | Drawdown Máx. | Sharpe Ratio |
| ----- | -------------- | ------------- | ------------- | ------------ |
| 5.A   | 32 (Simples)   | +14,68%       | 6,56%         | 1,113        |
| 2.A   | 64 (Campeão)   | +33,27%       | 2,18%         | 0,916        |
| 5.B   | 128 (Complexo) | +23,36%       | 3,56%         | 1,022        |

A Tabela 3 avalia o efeito da complexidade do modelo – medida pela dimensão oculta (Hidden_Dim) do LSTM Autoencoder – sobre o desempenho da estratégia.

O teste 5.A (32 neurônios) representa a configuração mais simples. Ela produz um Sharpe Ratio elevado (1,113), o que indica boa eficiência de risco, mas com retorno total relativamente baixo (+14,68%) e drawdown máximo de 6,56%. Em termos de capacidade, o modelo tende a ser mais conservador: captura parte dos episódios de anomalia, porém com menor intensidade de ganho, sugerindo um certo subajuste (capacidade limitada para representar padrões mais complexos do regime de mercado).

No outro extremo, o teste 5.B (128 neurônios) aumenta significativamente a capacidade da rede. O desempenho melhora em relação ao modelo simples – retorno total de +23,36%, drawdown máximo de 3,56% e Sharpe 1,022 – mas não atinge o mesmo nível de retorno do modelo campeão. A complexidade adicional não se traduz em ganho proporcional e traz, em tese, maior risco de sobreajuste, pois a rede passa a ter muitos parâmetros para o tamanho da amostra disponível.

A configuração 2.A (64 neurônios) se destaca como compromisso ótimo entre simplicidade e capacidade de representação. Ela entrega o maior retorno total da comparação (+33,27%), combinando isso com o menor drawdown máximo (2,18%) e um Sharpe Ratio ainda robusto (0,916). Ou seja, mesmo não sendo o modelo com Sharpe absoluto mais alto, é o que oferece melhor relação lucro x risco absoluto, com a trajetória de patrimônio mais atraente do ponto de vista de gestão (ganho expressivo e quedas muito contidas).

Por essa razão, a arquitetura com Hidden_Dim = 64 é adotada como Modelo Campeão: modelos mais simples (32 neurônios) são eficientes, mas pouco lucrativos em termos absolutos, enquanto modelos mais complexos (128 neurônios) aumentam a capacidade sem trazer um benefício claro de desempenho que justifique o custo adicional de complexidade.
#### Gráfico 2 
![[Imagem do WhatsApp de 2025-11-04 à(s) 22.45.09_f9169ca0.jpg]]

O Gráfico 2 apresenta a curva de patrimônio do Modelo Campeão (Seq_Length = 30, Hidden_Dim = 64, limiar = 0,95). A estratégia realiza poucos trades ao longo da amostra e, quando entra em operação, aloca aproximadamente 90% do capital em janelas bem definidas. 

Observa-se que essas janelas de exposição estão concentradas justamente nas fases de forte apreciação do índice, enquanto, nos períodos de oscilação lateral ou correção, o portfólio permanece majoritariamente em caixa. Como consequência, a curva de valor é relativamente suave, com retorno acumulado de +33,27%, drawdown máximo limitado a 2,18% e Sharpe Ratio anualizado de 0,916. 

Em conjunto, a baixa frequência operacional, a elevada taxa de acerto e a profundidade reduzida das quedas sugerem que o sinal de anomalia do modelo está sendo explorado de forma disciplinada e com controle efetivo de risco.
### 6. Processo de Backtest
No desenho e validação do backtest, adotamos cuidados específicos para mitigar dois riscos clássicos em modelos quantitativos: overfitting e viés de look-ahead.

Para o overfitting, realizamos uma bateria sistemática de experimentos variando tanto a dimensão do embedding (por exemplo, 64 vs. 128) quanto o comprimento da janela temporal de entrada (por exemplo, 30 vs. 60 passos). Os resultados, apresentados nas Tabelas 2 e 3, mostram de forma consistente que configurações mais complexas (Dim=128) ou com janelas mais longas (Seq=60) apresentaram desempenho inferior ao modelo selecionado (Seq=30, Dim=64). Essa evidência empírica indica que o modelo escolhido não é simplesmente um ajuste superespecífico aos dados de treino, mas sim um ponto de equilíbrio robusto entre capacidade de modelagem e generalização, reduzindo a probabilidade de overfitting.

Quanto ao viés de look-ahead, adotamos um cuidado metodológico rigoroso na implementação do pipeline de backtest. Em particular, o código foi depurado para garantir que, em cada dia D, apenas informações disponíveis até o fechamento de D-1 fossem usadas na geração do sinal de decisão. Durante esse processo, identificamos e corrigimos um bug crítico de alinhamento de datas no Backtrader, relacionado ao uso inconsistente de datetime.date versus datetime.datetime, que impedia a leitura correta do sinal no dia D. Após a correção, validamos que não há leitura antecipada de dados futuros e que o fluxo “dados → sinal → execução” respeita estritamente a causalidade temporal, assegurando um backtest metodologicamente sólido.
### 7. Conclusão
Os resultados obtidos ao longo do projeto são consistentes com a tese de “momentum de anomalia”. A evidência empírica mostra que os episódios em que o Erro de Reconstrução do LSTM Autoencoder atinge patamares extremos não antecedem movimentos de reversão, mas sim fases de aceleração de tendência no índice de IA. Em outras palavras, o sinal extraído do modelo funciona, na prática, como um indicador de ignição de regimes de alta, validando a mudança de interpretação em relação à hipótese inicial de reversão à média.

A configuração final – Seq_Length = 30, Hidden_Dim = 64, limiar no percentil 95 – apresentou desempenho superior em termos de retorno ajustado ao risco. No backtest, o Modelo Campeão entregou retorno acumulado de +33,27% com drawdown máximo de 2,18% e Sharpe Ratio anualizado de 0,916, mantendo exposição apenas em janelas de anomalia identificadas pelo modelo. A análise de sensibilidade dos hiperparâmetros (limiar, memória e complexidade) indica a existência de uma região estável de soluções próximas, o que reduz a probabilidade de overfitting a um único conjunto de parâmetros e confere robustez à estratégia.
#### Gráfico 3
![[Pasted image 20251211222845.png]]

À luz do benchmark definido no projeto o S&P 500, a estratégia não se propõe a substituir a exposição passiva ao índice, mas a atuar como um overlay tático. Enquanto o benchmark permanece continuamente alocado, absorvendo integralmente os ciclos de alta, lateralização e correção, o Kairos concentra risco apenas em janelas em que o sinal de anomalia indica um desvio excepcional em relação ao regime “normal”. Comparando o Gráfico 2, que apresenta a curva de patrimônio do Modelo Campeão, com o Gráfico 3, que mostra o preço do SPY em 2020 com as janelas de anomalia destacadas, observa-se que o índice sofre drawdowns muito mais profundos, enquanto a estratégia fica em caixa nos momentos de maior estresse e se expõe sobretudo nas fases de forte apreciação. Em termos qualitativos, o benchmark tende a capturar uma parcela maior das altas “de rotina”, mas ao custo de quedas acentuadas, já o Kairos entrega um caminho mais suave, com menor tempo médio em risco e drawdowns bem mais rasos, reforçando seu papel como gerador de alfa de regime em complemento à posição buy-and-hold no SPY.

Do ponto de vista de gestão de portfólio, os resultados sugerem que a estratégia pode ser considerada como candidato viável de alocação, especialmente como satélite em carteiras temáticas de tecnologia/IA ou como componente tático voltado a capturar movimentos de regime. Ainda assim, permanecem frentes relevantes de aprofundamento: (i) testar o modelo em outros universos de ativos (setores cíclicos, índices amplos, moedas e commodities) para avaliar a portabilidade da lógica de anomalia; (ii) incorporar explicitamente um filtro de regime de volatilidade, por exemplo: modulando o tamanho da posição em função da volatilidade implícita ou realizada, com o objetivo de otimizar o uso de capital em ambientes de estresse extremo e (iii) estender os testes para janelas de tempo adicionais e amostras fora do período de calibração, incluindo walk-forward e análises de estabilidade temporal.

Em síntese, a pesquisa indica que a combinação de um LSTM Autoencoder com uma regra disciplinada de entrada e saída baseada em anomalias de reconstrução gera um sinal economicamente significativo, com perfil de risco–retorno compatível com aplicação prática, desde que acompanhado de monitoramento contínuo e validação adicional em diferentes ciclos e mercados.
### IA Generativa
Utilizamos o Gemini, modelo de IA generativa do Google, como ferramenta de apoio técnico ao longo do desenvolvimento do projeto. Seu papel foi exclusivamente o de assistente, sem acesso direto ao nosso ambiente de execução, dados locais ou sistemas de produção. Toda a interação ocorreu por meio de prompts de texto, com a equipe responsável por executar o código, rodar experimentos, inspecionar logs e gráficos, e então retornar essas informações para análise da IA.

A aplicação da IA ocorreu em três etapas principais:

1. Depuração de código (programação) – suporte na identificação de bugs no pipeline de backtest. Em um caso específico, o Gemini ajudou a encontrar um erro de alinhamento de datas no Backtrader (uso incorreto de datetime.date versus datetime.datetime), que impedia a geração de operações, apesar do código aparentemente correto.
    
2. Otimização sistemática (pesquisa) – apoio no planejamento e organização de baterias de testes de hiperparâmetros para múltiplos modelos de Deep Learning, sugerindo combinações de parâmetros, estratégias de busca e critérios de comparação.
    
3. Estruturação de relatório (comunicação) – auxílio na organização textual dos resultados, na clareza da exposição metodológica e na redação de seções do relatório técnico, sempre a partir de insumos produzidos pela equipe (tabelas, métricas, gráficos).
    

Quanto às limitações, o modelo não tomou decisões autônomas nem substituiu o julgamento técnico da equipe. As respostas da IA dependeram da qualidade e precisão das informações fornecidas (código, erros, contexto dos experimentos), e todas as sugestões foram criticamente avaliadas antes de serem adotadas. Em síntese, a IA funcionou como um acelerador de pesquisa e desenvolvimento, otimizando o tempo de depuração e experimentação, mas a responsabilidade técnica, metodológica e interpretativa permaneceu integralmente com a equipe.  

![[noesis_5-removebg-preview.png|300]]

### Referências
[1] Li, Z. et al. (2021). "Anomaly Detection in Stock Market Data Using LSTM Autoencoders"

    Journal of Financial Data Science

[2] Zhou, Y. et al. (2020). "Early Warning of Financial Crises with Deep Autoencoders"

    Expert Systems with Applications

[3] Park, J. & Sohn, I. (2022). "Hybrid LSTM-VAE for Financial Crisis Prediction"

    IEEE Transactions on Neural Networks and Learning Systems

[4] Kingma, D. P. & Welling, M. (2014). "Auto-Encoding Variational Bayes"

    ICLR 2014

[5] Vaswani, A. et al. (2017). "Attention Is All You Need"

    NeurIPS 2017