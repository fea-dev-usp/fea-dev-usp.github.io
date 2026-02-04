---
title: "Otimização de Portfólio com Stable\rTail-Adjusted Return Ratio, Volatilidade\rDinâmica e Simulação Estocástica de Monte\rCarlo"
tags:
  - nivel/intermediario
  - trilha/finquant
---
_**Autores:** Leandro Santos · Tales Rafael Morales Pino · Victor Hugo Mendes Braga

# Resumo 

Este projeto apresenta um framework de otimização e validação de portfólios
financeiros baseado em medidas de risco de cauda, uma espécie de "seguro"para
momentos de estresse no mercado. Partindo da evidência empírica de que retornos
financeiros não seguem distribuições normais, propõe-se uma metodologia que subs-
titui a variância pela perda extrema esperada (Conditional Value-at-Risk – CVaR).
O risco é modelado por meio de uma matriz de covariância dinâmica estimada via
Exponentially Weighted Moving Average (EWMA), enquanto a distribuição dos re-
tornos é capturada por simulações de Monte Carlo com choques oriundos de uma
distribuição t-Student. A alocação é avaliada por métricas risco-retorno sensíveis à
cauda, com ênfase no Starr Ratio, e validada por procedimentos formais de backtes-
ting. Os resultados evidenciam ganhos de robustez em relação a abordagens clássicas
baseadas em média-variância.

# Introdução

A teoria moderna de portfólios, desde Markowitz (1952), fundamenta-se na hipótese de
normalidade dos retornos e na variância como medida adequada de risco. Contudo, evidências empíricas acumuladas indicam que séries financeiras apresentam assimetria, excesso
de curtose e volatilidade condicional, fenômenos incompatíveis com a distribuição normal.

Essas características implicam subestimação sistemática do risco extremo quando se
utiliza a variância como métrica central. Em resposta a essas limitações, este trabalho
propõe um arcabouço alternativo de gestão de risco e alocação de ativos, centrado em
medidas de cauda e em simulação estocástica.

O objetivo do artigo é apresentar, de forma integrada, um pipeline computacional
composto por três etapas: (i) estimação da matriz de covariância dinâmica via EWMA;
(ii) simulação de cenários de retornos por Monte Carlo com distribuição t-Student e
avaliação do portfólio por métricas de cauda, em especial o Starr Ratio; e (iii) validação
do modelo por meio de backtesting.

# Fundamentação Teórica

## Risco de Cauda e Limitações da Variância

A variância penaliza simetricamente desvios positivos e negativos em relação à média e
ignora explicitamente a severidade das perdas extremas. Em distribuições leptocúrticas,
eventos de grande magnitude ocorrem com frequência muito superior à prevista pela
normal, tornando a variância uma medida insuficiente de risco.

O CVaR, definido como a esperança condicional das perdas que excedem um deter-
minado quantil, emerge como alternativa consistente, convexa e coerente. Essa medida
captura diretamente o risco associado aos piores cenários, alinhando-se melhor ao pro-
blema econômico enfrentado por gestores e investidores.

Nesse sentido, o VaR falha por não ser subaditivo, podendo indicar que uma carteira
diversificada é mais arriscada que a soma de seus ativos isolados em distribuições de
perdas extremas. Já o CVaR funciona porque é uma medida de risco coerente que captura
a magnitude das perdas além do ponto de corte, garantindo que a diversificação sempre
seja refletida como uma redução de risco.

## Volatilidade Condicional e Clustering

Outro fato estilizado relevante é o agrupamento temporal da volatilidade. Períodos de alta
variância tendem a ser seguidos por períodos igualmente voláteis. Modelos que assumem
variância constante falham em capturar essa dinâmica.

O método EWMA, consagrado na prática de mercado, modela a volatilidade como
um processo recursivo, atribuindo maior peso às observações mais recentes e permitindo
rápida adaptação a choques de mercado.

# Metodologia

## Dados e Transformações

Os retornos são definidos como log-retornos, de modo a garantir aditividade temporal.
Utilizam-se preços ajustados, evitando distorções decorrentes de dividendos, splits ou
eventos corporativos. Assume-se, para fins de modelagem, liquidez perfeita e ausência de
custos de transação.

## Descrição do Motor de Risco e da Base de Ativos

A execução do motor de risco, documentada no script **motor_risco.py**, baseia-se em um
conjunto diversificado de ativos negociados na B3, selecionados com o objetivo de repre-
sentar diferentes vetores da economia nacional e global. A carteira de estudo compreende
os seguintes tickers:

- PETR4.SA (Petrobras);
- VALE3.SA (Vale);
- ITUB4.SA (Itaú Unibanco);
-  LREN3.SA (Lojas Renner);
*  WEGE3.SA (WEG);
- AXIA3.SA

O período de análise compreende o intervalo de 01/01/2015 a 30/12/2025. Os anos
iniciais, de 2015 a 2017, são utilizados como uma janela de warm-up para a calibração
dos parâmetros de risco e para a inicialização da matriz EWMA.

O backtest propriamente dito é conduzido de forma walk-forward, com rebalancea-
mento mensal, iniciando-se em 01/01/2018. Essa abordagem permite avaliar o desem-
penho da estratégia em diferentes regimes de mercado, incluindo períodos de elevada vo-
latilidade, como a crise de 2020, bem como as instabilidades políticas e macroeconômicas
subsequentes

# Estimação da Matriz de Covariância EWMA

A matriz de covariância condicional $\Sigma_t$ é estimada segundo o esquema EWMA:

$$
\Sigma_t = \lambda \Sigma_{t-1} + (1 - \lambda)\, r_{t-1} r_{t-1}^{\top},
\tag{1}
$$

onde $\lambda \in (0,1)$ é o fator de decaimento e $r_t$ representa o vetor de retornos no tempo $t$.
Este procedimento permite capturar mudanças rápidas no regime de risco e preserva a estrutura de correlação entre os ativos.

# Simulação de Monte Carlo

Com base na matriz $\Sigma_t$, realiza-se uma decomposição de Cholesky, garantindo a preservação das correlações observadas. Choques aleatórios são então gerados a partir de uma distribuição t-Student com graus de liberdade finitos, refletindo a presença de caudas pesadas.

A partir desses choques, constroem-se trajetórias simuladas de retornos em um horizonte fixo. Para cada trajetória, calcula-se o retorno do portfólio e obtém-se a distribuição empírica de perdas.

Diferente das abordagens simplistas que utilizam choques gaussianos, este *framework* emprega uma simulação de Monte Carlo com 10.000 cenários baseados na distribuição t-Student com 5 graus de liberdade.$^{1}$ A escolha é estratégica para o mercado brasileiro, pois confere às caudas da distribuição uma espessura que reflete a realidade de ativos de risco, onde perdas de 3 ou 4 desvios padrão ocorrem com frequência muito superior à prevista pela distribuição normal.$^{3}$ Este parâmetro assegura que o CVaR calculado seja conservador e realista, evitando que o otimizador assuma posições excessivamente agressivas baseadas em uma falsa percepção de segurança estatística.$^{1}$

# Avaliação por Starr Ratio

A relação risco-retorno do portfólio é avaliada por meio do *Starr Ratio*, definido como:

$$
\text{Starr Ratio} = \frac{\mathbb{E}[R_p]}{\text{CVaR}^*_{\alpha}(R_p)},
\tag{2}
$$

onde $\mathbb{E}[R_p]$ é o retorno esperado do portfólio e $\text{CVaR}^*_{\alpha}$ representa o CVaR ao nível de confiança $\alpha$. Essa métrica privilegia estratégias que oferecem maior retorno esperado por unidade de risco extremo assumido.

# Backtesting e Validação

A validação do modelo é conduzida por meio de backtesting em janelas móveis. Para cada
período, o risco estimado ex-ante é comparado às perdas realizadas ex-post.

Adota-se um critério de exceções, no qual se contabiliza o número de vezes em que
a perda observada supera o quantil de risco estimado. A frequência de exceções é então
confrontada com os limites teóricos esperados, permitindo classificar o desempenho do
modelo em zonas de aceitação, alerta ou rejeição.

Esse procedimento fornece uma avaliação objetiva da capacidade preditiva do modelo
e de sua adequação para uso prático em gestão de risco.

# Resultados da Simulação: Análise da Distribuição de Retornos 

A análise visual do primeiro gráfico, vide figura 1, intitulado "Distribuição de Retornos
do Portfólio", fornece uma visão clara do perfil de risco-retorno gerado pelos cenários de
t-Student. O histograma revela uma concentração de massa em torno da média, mas com
uma dispersão significativa para os extremos negativos, característica típica das séries
financeiras simuladas sob regimes de caudas pesadas.

# Métricas de Risco de Cauda

Os valores extraídos diretamente da imagem indicam uma realidade rigorosa para a gestão
de ativos:

-  Retorno Médio Simulado: −0, 3968%
- CVaR 95% Simulado: −15, 2602%

Este resultado é fundamental para a fundamentação dos resultados. Embora o re-
torno médio nos cenários simulados seja levemente negativo (−0, 3968%), o CV aR de
−15, 2602% alerta que, no pior cenário médio (os 5% piores casos), a perda esperada é de
aproximadamente quinze vezes a magnitude do retorno médio.

Em uma distribuição normal, a distância entre o V aR e o CV aR seria muito menor;
aqui, a profundidade do CV aR reflete os choques da distribuição t-Student. O otimi-
zador, ao buscar o máximo Starr Ratio, tenta encontrar os pesos que minimizam esse
impacto de −15, 2602% em relação ao retorno esperado, privilegiando ativos que apresen-
tem uma "defesa"mais robusta nas caudas, ou seja, ativos cujas correlações não explodam
simultaneamente durante quedas sistêmicas.

A linha verde vertical no gráfico marca o retorno médio próximo ao zero, enquanto
a linha vermelha tracejada atua como o "escudo"do gestor, delimitando a fronteira de
estresse. A existência de barras de frequência no histograma muito além da marca de
−20% (long tails) confirma a eficácia do uso da t-Student em capturar cenários de pânico
de mercado que seriam ignorados por modelos de média-variância tradicionais.

# Desempenho Histórico e Backtesting: Estratégia Starr Ratio vs Ibovespa

Os resultados empíricos da execução do código são consolidados no segundo conjunto de
gráficos, vide figura 2, que apresenta o "Retorno Acumulado"e o "Drawdown"desde 2018
até o início de 2026. A análise destes dados permite concluir que a estratégia baseada no
Starr Ratio obteve uma vitória expressiva sobre o índice de referência

# Evolução Patrimonial e Geração de Alpha

A curva de patrimônio da "Starr Ratio Strat"(linha azul sólida) exibe uma trajetória de
crescimento consistente, descolando-se positivamente do Ibovespa (linha roxa tracejada)
logo no início do período.

- Retorno Acumulado da Estratégia: Ao final do período (2026), a estratégia
atinge um patamar próximo de 280% de retorno acumulado.
- Retorno Acumulado do Ibovespa: No mesmo intervalo, o índice benchmark
encerra o período próximo aos 100%.
- Alpha Estimado: A estratégia gerou um Alpha absoluto de aproximadamente 180
pontos percentuais sobre o mercado em oito anos.

Este desempenho é notável por ocorrer em um mercado lateralizado e volátil como o
brasileiro. O gráfico mostra que a estratégia conseguiu capturar ciclos de alta com maior
eficiência do que o índice ponderado por valor de mercado. Enquanto o Ibovespa enfrentou
dificuldades para superar patamares históricos entre 2021 e 2024, a carteira otimizada via
CV aR manteve uma inclinação positiva, sugerindo que a reotimização baseada no Starr
Ratio foi capaz de rotacionar os pesos para ativos com melhor momento e menor risco de
cauda dinâmico.

# Resiliência e Gestão de Crises

Um ponto de inflexão crítico visível no gráfico é o crash causado pela pandemia de COVID-
19 em março de 2020. Ambos os ativos sofreram quedas violentas, mas o comportamento
subsequente é o que valida o framework.

1. A Queda: A estratégia Starr Ratio e o Ibovespa atingiram drawdowns profundos,
na casa de −50%, demonstrando que em momentos de correlação unitária, nenhuma
métrica de alocação protege totalmente o capital.
2. A Recuperação: A estratégia (blue-line) iniciou uma recuperação vertical muito
mais ágil que a do benchmark. Ao final de 2020, a estratégia já havia recuperado o
patamar pré-crise e iniciado novas máximas, enquanto o Ibovespa ainda lutava para
estabilizar-se.

Isso se deve à capacidade do modelo EWMA de recalcular a volatilidade instantânea
e à simulação t-Student que, após o choque, passou a precificar cenários de cauda ainda
mais severos, forçando o otimizador a uma alocação mais eficiente para o novo regime de
risco.

# Análise de Drawdown e Risco Realizado

O painel inferior detalha as quedas a partir do pico (Drawdown). A comparação entre a
área azul (Estratégia) e a linha roxa (Ibov) revela insights profundos sobre a gestão de
risco do projeto.

## Perfil de Perda Máxima

Observa-se que, em períodos normais de mercado (2018-2019 e 2023-2025), o drawdown
da estratégia tendeu a ser mais raso do que o do Ibovespa. A estratégia frequentemente
retornava ao patamar de 0% de queda (novas máximas históricas) com maior velocidade
do que o índice.

- Estabilidade: Durante o período de 2021 a 2022, o Ibovespa enfrentou um draw-
down persistente e profundo (em torno de −25% a −30%). No mesmo período, a
Starr Ratio Strat manteve seus drawdowns contidos em níveis menos severos.
-  Gestão Ativa de Risco: O fato de o drawdown da estratégia ser menor em janelas
de "mercado de lado"comprova que a substituição da variância pelo CV aR impede
que a carteira fique excessivamente exposta a ativos com risco de cauda oculto.

![[Pasted image 20260203210801.png]]

>[!info]
>Figura 1: Distribuição dos retornos simulados do portfólio ótimo.
>

 ![[Pasted image 20260203211052.png]]

>[!info]
>Figura 2: Retorno acumulado e drawdown da estratégia baseada no Starr Ratio.
# Conclusão

Este trabalho apresentou a implementação e avaliação de um algoritmo de alocação de
ativos baseado no Starr Ratio, utilizando volatilidade dinâmica (EWMA) e simulação de
Monte Carlo com distribuição t-Student. A estratégia Long Only foi testada contra o
Ibovespa entre 2018 e 2026.

A análise dos resultados aponta para um trade-off claro entre agressividade na recu-
peração e exposição a riscos de cauda:

1. Performance vs. Risco Sistêmico: Embora o retorno acumulado da estratégia
(279,3%) tenha superado o benchmark (101,6%), o modelo não ofereceu imunidade
contra choques sistêmicos. O drawdown máximo de -50,2% em março de 2020 —
superior ao do próprio Ibovespa (-46,8%) — evidencia que a otimização via CVaR,
quando aplicada a um universo restrito de ativos, não elimina a correlação unitária
em momentos de pânico. O Alpha gerado deve ser interpretado, portanto, como
fruto de uma seleção de ativos mais eficiente na retomada, e não de uma proteção
absoluta na queda.
2. Sensibilidade do EWMA: O uso do decaimento exponencial provou ser uma
"faca de dois gumes". Se por um lado a rápida adaptação da matriz de covariância
permitiu uma recuperação acelerada pós-crise (reduzindo o tempo sob d’água), por
outro, a dependência da volatilidade recente torna o modelo reativo. O sinal atual de
retorno esperado negativo (-0,34%) confirma essa característica: o algoritmo projeta
a inércia do movimento recente de baixa, sugerindo uma alocação defensiva não por
previsão macroeconômica, mas por persistência estatística dos dados.
3. Limitações da Concentração: A performance superior veio acompanhada de
uma volatilidade idiossincrática elevada. A restrição a apenas seis ativos (no teste
original) amplificou os movimentos de cauda, tanto positivos quanto negativos. Em
um cenário real de gestão, a ausência de custos de transação no backtest e a con-
centração da carteira poderiam reduzir a aderência desses resultados.

Em suma, o framework demonstrou ser uma ferramenta robusta para classificação e
seleção de ativos (Stock Picking quantitativo), superando a média de mercado no longo
prazo. Contudo, seus resultados reforçam que métodos estatísticos de otimização de cauda
não substituem a necessidade de diversificação ampla para mitigação de riscos estruturais.
Referências

[1] ARAÚJO, Lucas Machado Braga de. Composição de fundo de fundos
multimercado: otimização de carteira pelo método de média – CVaR.
4. Dissertação (Mestrado em Finanças e Economia Empresarial) – Es-
cola de Economia de São Paulo, Fundação Getulio Vargas, São Paulo, 2009.
Disponível em: https://repositorio.fgv.br/server/api/core/bitstreams/
5a873973-a11a-42e9-a63b-b97ab7da3857/content. Acesso em: 31 jan. 2026.

[2] J.P. MORGAN. RiskMetrics™ — Technical Document. 4. ed. Nova York: J.P.
Morgan/Reuters, 2001.
9

[3] KOUAISSAH, Noureddine; HOCINE, Amin. Forecasting systemic risk in portfolio
selection: The role of technical trading rules. Journal of Forecasting, [S. l.], v.
40, n. 4, p. 708-729, jul. 2021. Disponível em: https://www.researchgate.net/
publication/347136569. Acesso em: 31 jan. 2026.

[4] ROCKAFELLAR, R. Tyrrell; URYASEV, Stanislav. Optimization of conditional
value-at-risk. Journal of Risk, [S. l.], v. 2, n. 3, p. 21-41, 2000. Disponível em: https:
//sites.math.washington.edu/~rtr/papers/rtr179-CVaR1.pdf. Acesso em: 31
jan. 2026.