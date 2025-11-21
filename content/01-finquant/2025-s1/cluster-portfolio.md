---
title: Otimização de Carteira via Clustering
tags:
  - trilha/finquant
  - nivel/intermediario
---
_**Autores:** Felipe Santana · Gabriel Graciano · Rodrigo Menin_
## Introdução

A criação de portfólios de investimentos, atualmente, baseia-se em métodos fundamentalistas ou técnicos. No entanto, em ambos os métodos, reconhece-se a importância da diversificação de uma carteira de investimentos como uma forma de reduzir risco. Nesse contexto, e considerando também limites de capital, atenção e necessidade de alocação sistemática, o presente projeto busca estudar métodos quantitativos no gerenciamento de uma carteira de ações no mercado brasileiro.

Especificamente, investigou-se o seguinte problema proposto: dado um capital inicial **C** e uma restrição de **k** ações a serem selecionadas, qual alocação maximizaria o **Sharpe Ratio** futuro? Ainda, agrupar previamente ações por similaridade (usando clusterização) melhoraria a relação risco-retorno se comparado à simples seleção das **k** melhores baseado em indicadores?

Como ponto de partida ao questionamento proposto, assume-se, baseado em pesquisas da literatura realizadas em outros mercados, a hipótese de que **métodos de clusterização** por **indicadores fundamentalistas** aproximam empresas com perfis de risco e resultados semelhantes no mesmo cluster e, por conseguinte, separam empresas com baixa similaridade em clusters distintos. A partir dessa separação, a escolha de um representante por grupo, junto da otimização de pesos, geraria **maior diversificação** e maximizaria o Sharpe Ratio da carteira. Como forma de comparar a efetividade da estratégia de investimento proposta, realizou-se, também, a execução de **backtesting**.

Para a realização do projeto, obtiveram-se dados de indicadores fundamentalistas dos últimos 5 anos de todas as empresas selecionadas pelo algoritmo. Em seguida, realizou-se pré-processamento dos dados em ambiente Python que eliminou empresas com dados insuficientes, tratou valores faltantes, ajustou desdobramentos e eventos societários e normalizou variáveis geradas a partir dos indicadores, o que garantiu, ao final, uma seleção sólida de empresas para uso no algoritmo de clusterização.

O **K-means**, método de aprendizado não supervisionado escolhido, se caracteriza por sua rapidez, escalabilidade e necessidade de poucos hiperparâmetros. O algoritmo particiona o conjunto de dados em **k clusters** e atribui cada observação ao centróide mais próximo. Em seguida, cada centróide é recalculado como a média dos vetores das observações do cluster. Esse processo, então, se repete até a ocorrência de convergência.

## Dados

A análise exploratória dos dados desenvolvida neste estudo baseia-se em três fontes consolidadas de informações financeiras: as **séries históricas de preços das empresas listadas**, disponibilizadas pela própria B3, e os indicadores fundamentalistas compilados em planilhas a partir das plataformas **Economática** e **Fundamentei**. A escolha delas se justifica por sua ampla adoção no meio acadêmico e profissional, sendo reconhecidas como fontes confiáveis e consolidadas para estudos que relacionam fundamentos econômico-financeiros e variáveis de mercado.

As séries da B3 foram coletadas diretamente dos arquivos de cotações históricas da bolsa, que incluem **preços de abertura, fechamento, máxima, mínima e volume negociado**. Esses registros constituem a principal referência oficial para a análise da dinâmica dos preços de ações no mercado brasileiro.

Por sua vez, as plataformas Economática e Fundamentei forneceram uma base estruturada de indicadores fundamentalistas e de desempenho das empresas analisadas. Foram incluídos indicadores de rentabilidade, sendo eles: **margem líquida (ML)**, **margem bruta (MB)**, **margem EBIT**, **margem EBITDA**, **retorno sobre ativos (ROA)**, **retorno sobre patrimônio líquido (ROE)**, **margem de fluxo de caixa operacional (FCO)** e **retorno sobre capital investido (ROIC)**. O período de análise foi definido de forma a maximizar a disponibilidade de dados, abrangendo, sempre que possível, **informações trimestrais de 2020 a 2024**.

Na etapa de pré-processamento, a fim de garantir a robustez e a confiabilidade da análise, minimizando vieses introduzidos por dados ausentes, foram filtradas apenas as empresas que apresentaram mais **95%** de presença durante esse período; as que não atenderam a esse requisito foram retiradas.

Os dados da B3 passaram por limpeza de valores faltantes, ajustes decorrentes de eventos societários (fusões, incorporações e deslistagens), recálculo de desdobramentos (via biblioteca **yfinance**) e padronização de datas, assegurando consistência e continuidade nas séries de preços e retornos. No caso da Economática e da Fundamentei, além do processo anterior, foram selecionados apenas os indicadores mais relevantes para o objetivo do estudo, priorizando séries longas e comparáveis, além de uma segmentação entre empresas de setores financeiros e não financeiros.

Por fim, todos os dados foram exportados para o ambiente **Python** e organizados em **DataFrames**, possibilitando a construção de uma matriz que integrou as cotações históricas com os indicadores fundamentalistas. Essa base consolidada serviu de fundamento empírico para a aplicação do método de **clusterização** e a execução do **backtesting**.
## Metodologia

Com o objetivo de aplicar os conhecimentos adquiridos sobre tratamento, criação e processamento de dados, bem como sobre mercados financeiros e modelagem, este trabalho propõe a implementação de uma **estratégia quantitativa** baseada em **clusterização** e na **teoria moderna de portfólios**. A fim de avaliar a eficiência dessa análise, foi realizado um backtest considerando cenários divergentes no período de **2019 a 2024**. Para isso, este trabalho parte de duas hipóteses principais:

1. **Quanto menos semelhantes** forem as empresas em seus indicadores, **menor tende a ser a volatilidade idiossincrática** de suas ações.
2. **As informações refletidas no preço** das ações coincidem com aquelas apresentadas nas demonstrações de resultado das empresas.

A primeira hipótese implicaria em uma **sistemática redução (portfólios)** ou **concentração (em certos grupos)** da volatilidade medida. Já a segunda, teria-se uma distribuição de pesos altamente enviesada à ação do subgrupo mais distante da origem e/ou convergência das alocações a uma mesma região.

Na calibragem da estratégia, o número de subgrupos a serem criados foi decidido empiricamente com testes exploratórios no primeiro período da base de dados, assim este sendo excluído dos testes de hipóteses.

Dos vieses intrínsecos a cada fonte de informação, tratou-se com a normalização de valores, exclusão de omissos, condensamento de indicadores e recortes sucessivos na amostra. Além disso, para combater o **viés de agrupamento** gerado pelo diferente porte das empresas presentes no mercado de ações, todo grupo de informações usado no algoritmo de cluster foi **normalizado**, ou seja, tiveram suas médias e variâncias convertidas em uma distribuição normal padrão. Ainda, cada tratamento foi feito de maneira separada de dados futuros para que esses não desloquem os indicadores das distribuições dos dados em uso, o que indicaria um **viés ao futuro**. Por fim, os dados que crescem proporcionalmente com o giro das empresas, e que são adimensionais, foram convertidos em **margens** adotando intervalos padrões de (0, 1].

Ademais, os valores faltantes em séries históricas de preços foram preenchidos de forma adaptativa ao contexto de utilização. Para o cálculo dos retornos, eles foram interpolados linearmente de modo que sua derivada fosse constante e, no caso do cálculo de montante, o preço foi preenchido retroativamente.

Para os valores faltantes nos indicadores das empresas, empresas sem indicadores publicados na data padrão foram **descartadas** para a simplificação da distribuição de pesos, fixando a data do processo. Por outro lado, as empresas que não publicaram ou tiveram seus indicadores indisponíveis em trimestres pontuais foram **retiradas dinamicamente** do universo de escolhas para o respectivo trimestre.

Com isso, as carteiras otimizadas em um grupo que apresentaram **retorno esperado negativo** têm a opção de **deixar o dinheiro não investido**, consequência necessária para manter lógica a subdivisão do universo inteiro em subgrupos. Ainda, supondo que para um universo de ações ser completo necessita-se de ter pelo menos metade das empresas com valor esperado menor que o do mercado em geral. Uma consequência disso com a subdivisão do mercado é a possível existência de um grupo em que todas as empresas possuam retornos negativos.

## Backtest

O backtest foi implementado em períodos de **três meses**, durante o período de **2020 a 2024**, e com informações retroativas com o mesmo período, assim não havendo sobreposição de teste, inferência e estratégia.

O algoritmo de **clusterização** foi utilizado como forma de **restringir** o universo de possibilidades a serem otimizadas. Para isso, foram empregados indicadores financeiros derivados de dados públicos divulgados trimestralmente pelas empresas do mercado brasileiro, com base nos **Demonstrativos de Resultados (DRE)** e nos **Fluxos de Caixa**. A calibração do modelo resultou na formação de **três grupos**, número definido a partir dos testes empíricos do **método do cotovelo** e da **silhueta**.

![[../../imagens/projeto-cluster-portfolio/projeto-cluster-portfolio-1.png]]

>[!info]
>A análise visual desses métodos indicou que o teste do cotovelo delimitou a escolha entre **três e oito** clusters


![[../../imagens/projeto-cluster-portfolio/projeto-cluster-portfolio-7.png]]

>[!info]
>Enquanto o teste da silhueta mostrou que as pontuações entre **quatro e sete** permaneceram no mesmo patamar

Assim, a decisão final pela divisão em **três clusters** foi alcançada por meio do algoritmo **K-Means**, implementado na biblioteca **Scikit-learn**.

Assim, nomeados os três subgrupos do universo máximo de **133 empresas**, foi criada uma **carteira fictícia** para cada um, de forma a **maximizar o Sharpe Ratio realizado** no período dos últimos três meses. Isso se deu através do algoritmo de alocação de carteiras via biblioteca do Python **PyPortfolioOpt (pypfopt)**, uma vez que ela busca uma solução ótima entre a **matriz de correlação** das ações e seus **retornos esperados** (dos últimos 3 meses). E, finalmente, uma carteira com seus pesos distribuídos entre as empresas que tiveram **melhor performance em cada subgrupo** é criada como ponto de comparação.

A seguinte análise de performance visa responder e comparar tanto os desempenhos **intergrupos**, como entre cada grupo e a **carteira limitada a 3 ações**.

## Resultados

O backtest foi realizado considerando todos os trimestres de **2020 a 2024**. Nesse período, a carteira principal selecionou ao todo **29 ações**. Para destacar a relevância das escolhas, priorizou-se analisar as ações mais **recorrentes ao longo do tempo**, em vez das que tiveram **maior peso médio** em períodos isolados. Isso porque houve momentos em que a carteira concentrou peso **excessivo em uma única ação**, que depois acabou não retornando mais ao portfólio, o que poderia **distorcer a análise**.

![[../../imagens/projeto-cluster-portfolio/projeto-cluster-portfolio-9.png]]


As ações que mais se destacaram no portfólio, tanto pela **frequência** quanto pelo **peso médio**, podem ser organizadas e descritas principalmente pelos seguintes setores e suas características:

### (1) Consumo Não Cíclico

A **SLC Agrícola** se destacou como a ação **mais relevante** do portfólio, atingindo o **maior peso médio (83%)**. O setor de consumo não cíclico, representado pelo **agronegócio**, possui forte **resiliência a crises internas**, dado seu alinhamento com a demanda externa por **commodities agrícolas** (soja, milho e algodão). Esse desempenho mostra que o modelo captou a relevância estrutural do agronegócio brasileiro como pilar de **rentabilidade estável**.

### (2) Comunicações

A presença de **VIVT3**, com o **segundo maior peso médio (62%)**, indica a importância do setor de **telecomunicações** no portfólio. Empresas desse setor apresentam **receitas recorrentes**, **geração de caixa robusta** e **políticas consistentes de dividendos**. 

### (3) Materiais Básicos

A **Vale (VALE3)** se consolidou como peça-chave, refletindo a relevância dos **ciclos de valorização do minério de ferro** e a exposição da empresa ao **mercado externo**, especialmente à **China**. A **Rani (RANI3)**, do setor de **papel e celulose**, captou a **demanda crescente por embalagens**, impulsionada pela **expansão do e-commerce**. Já a **Unipar (UNIP6)**, voltada ao setor **petroquímico**, evidencia a atratividade de **nichos industriais** ligados à cadeia química.

### (4) Bens Industriais

A **WEG (WEGE3)** destacou-se como representante de **bens industriais**. A empresa combina **forte expansão internacional**, **margens consistentes** e **inovação tecnológica**, atributos valorizados pelo modelo. Por outro lado, a **São Carlos (SCAR3)**, voltada à **gestão de imóveis corporativos**, reflete uma inserção mais específica dentro do setor, trazendo exposição ao **mercado imobiliário de alto padrão**, o que **diversifica o portfólio** em relação aos demais industriais.

### (5) Consumo Cíclico

O setor de consumo cíclico foi representado por três companhias de segmentos distintos. A **Technos (TECN3)** adicionou um ativo de **menor capitalização**, refletindo oportunidades de curto prazo no **varejo de acessórios**. A **Vulcabras (VULC3)**, com marcas esportivas de renome, esteve associada à **retomada do consumo doméstico**. A **Whirlpool (WHRL4)**, multinacional de eletrodomésticos, reforçou a exposição a **bens duráveis**, geralmente mais sensíveis ao **ciclo econômico**. O conjunto sugere que o algoritmo explorou **nichos de consumo** em diferentes fases do ciclo de renda.

De forma geral, a carteira apresentou **diversidade setorial**, com predominância de setores ligados à **rentabilidade estrutural**. Isso reforça o objetivo central do projeto: empregar a **clusterização** não apenas para identificar padrões de escolha, mas também uma tentativa de **ampliar a diversificação e de se reduzir riscos**.

Outro ponto relevante diz respeito à **dinâmica temporal dos pesos atribuídos**. Não basta analisar quais ações foram selecionadas, mas também **quando** e com **qual intensidade** participaram da carteira. 

![[../../imagens/projeto-cluster-portfolio/projeto-cluster-portfolio-3.png]]

>[!info]
>A leitura visual mostra que houve uma concentração a um único ativo por período de forma **sistêmica**, justamente pela escolha do critério de **Sharp Ratio**. O algoritimo acabou não fazendo uma boa distribuição de pesos, concentrando o peso do portfólio em cada período em uma única ação somente. Diante desse fato, será mostrado mais adiante, que isso acabou comprometendo a intenção inicial de reduzir riscos sistêmicos e de potencializar o retorno esperado.

Ademais, pode-se observar que o modelo tem ativos como **VIVT3**, **VALE3** e **WEGE3** aparecendo em **múltiplos períodos** distintos, sugerindo que eles são “candidatos” recorrentes a compor a carteira. Suas características de **rentabilidade estrutural** são consistentemente capturadas pelo modelo em diferentes contextos de mercado. Em contrapartida, ações como **RANI3**, **TECN3** ou **WHRL4**, que aparecem de forma mais esporádica, representam **apostas mais táticas** e surgem como **oportunistas**, selecionadas quando seus fundamentos se destacam em um trimestre específico.

Portanto, dinâmica da carteira **não é passiva**, no sentido de se comprar e segurar os ativos com os melhores fundamentos por longos períodos. Pelo contrário, é uma estratégia de **rotação quantitativa ativa**.

Esse comportamento dinâmico levanta a questão central: até que ponto a rotação ativa e a diversificação de setores se traduziram em **resultados financeiros concretos**? Para responder, é necessário observar a **rentabilidade acumulada e parcial** da carteira ao longo do intervalo de tempo.

![[../../imagens/projeto-cluster-portfolio/projeto-cluster-portfolio-6.png]]

>[!info]
>A análise de performance revela que essa dinâmica **não se traduziu em resultados sustentáveis**. O resultado final da estratégia ao longo dos cinco anos (**2020–2025**) foi um **prejuízo acumulado de 24%**. A trajetória até esse desfecho foi **extremamente volátil**: a carteira chegou a registrar ganhos **próximos de 40%** no início de **2023**, mas reverteu toda a valorização e **terminou em território negativo**. O percurso expôs o portfólio a um **risco elevado**, com um **drawdown inicial superior a 50%** no primeiro trimestre de **2020** e uma **curva de capital instável** ao longo do tempo.

O comportamento trimestral reforça essa leitura: a estratégia alternou trimestres de **ganhos expressivos (acima de 20%)** com **perdas acentuadas (superiores a -20%)**. Isso mostra que a **concentração** em poucas apostas de curto prazo, embora gerasse **picos de performance**, comprometeu a **consistência** dos resultados no horizonte de cinco anos.

A fins de exercício da estratégia, foi estipulado um **valor patrimonial inicial** de **R$ 100.000,00**. Esse valor serve como referência base para avaliar tanto o crescimento quanto as perdas ao longo do período, permitindo interpretar os movimentos patrimoniais em termos **relativos e absolutos**.

![[../../imagens/projeto-cluster-portfolio/projeto-cluster-portfolio-4.png]]

>[!info]
>A linha de preta de mostra a referência incial dos R$ 100.000,00 investidos incialmente. As barras vermelhas mostram os períodos que o portfólio ficou abaixo desse patamar e as barras verdes mostram os períodos que ficou acima. 

A evolução patrimonial evidencia algumas **lições centrais**. A trajetória foi caracterizada por **alta volatilidade**, refletindo **alocação de risco elevada** e exposição a oscilações significativas. A marca de **R$ 100 mil** atuou como **divisor de águas**: o patrimônio conseguiu superar e se manter acima por cerca de **1,5 ano**, mas acabou recuando, confirmando a resistência dessa faixa. O **drawdown** do primeiro trimestre de **2020** comprometeu fortemente a rentabilidade de longo prazo, revelando **falhas na gestão de risco**. 

Em suma, a trajetória patrimonial demonstra que, apesar do potencial identificado pelo modelo e das oportunidades de ganhos expressivos em períodos pontuais, a estratégia apresentou **consistência limitada** e **alta sensibilidade a choques de mercado**. A **falta de mecanismos robustos de controle de risco** e a **concentração elevada** em poucos ativos por trimestre impediram que os ganhos fossem preservados, resultando em uma **performance final significativamente inferior** ao pico alcançado.
## Análise de Risco

Como descrito anteriormente, o portfólio apresentou um **perfil de risco elevado**, devido à forte **concentração em poucos ativos** e à **alta convicção** nas escolhas da carteira. A fim de comprovar essa percepção, foram incluídas outras **métricas de risco** à análise, sendo elas o **VaR (Value at Risk)** e o **CVaR (Conditional Value at Risk)**.

O **VaR** estima a **perda máxima esperada** do portfólio em um horizonte de tempo definido, dado um **nível de confiança** específico. Diante disso, foi estimado um **VaR mensal com 95% de confiança** que indicou um resultado de **-15%**, ou seja, em **19 de 20 meses** do período de análise, as perdas **não devem ultrapassar -15%**.

Já o **CVaR** calcula a **perda média nos piores cenários**, ou seja, quando a perda ultrapassa o valor estimado pelo VaR. No caso do portfólio analisado, essa métrica indicou uma **queda de -30%**, evidenciando a severidade das perdas em **eventos extremos**. Assim, enquanto o VaR estabelece um **limite de perda “esperado”**, o CVaR captura a **magnitude real das perdas** nos piores cenários, sendo especialmente relevante para estratégias **concentradas** ou com **retornos assimétricos**.

![[../../imagens/projeto-cluster-portfolio/projeto-cluster-portfolio-2.png]]

No caso do portfólio analisado, o VaR mensal de **-15%** confirma que a estratégia **assume risco elevado** de forma consistente, enquanto o CVaR de **-30%** evidencia que, quando o limite do VaR é ultrapassado, o **prejuízo médio esperado é substancial**. Os eventos históricos de **-50%**, **-31%** e **-18%** reforçam a materialização concreta desse risco, demonstrando que perdas severas **não** são meros acidentes, mas sim uma **característica estrutural** da carteira. O **drawdown máximo de 51%** registrado no início de **2020** confirma que o portfólio é vulnerável a **choques extremos**, resultado da **extrema concentração** de capital em poucos ativos.

Em síntese, os dados demonstram que a estratégia **não apresenta risco otimizado**, mas **risco concentrado**: o portfólio aposta em **retornos elevados**, mas paga caro em **perdas expressivas**. O **resultado final de -24%** evidencia que o prêmio de risco **não compensou** a magnitude das perdas, gerando **retorno ajustado ao risco negativo**.

## Limitações

Durante a execução do projeto, houveram **limitações relevantes** na **seleção de indicadores**, nas **especificidades de cada setor** e na **qualidade do banco de dados**.

Além disso, decorrentes de problemas de **acesso amplo de dados** inicialmente (sem acesso ao Economática por grande período do estudo), o período de **backtest** que pôde ser realizado foi de **2020 a 2024** — intervalo de tempo em que houve a **pandemia**, na qual muitos ativos sofreram desvalorização causada por **choque externo**. Assim, a carteira possui a sua **pior marca de rentabilidade** gerada nesse período, o que pode ter **enviesado negativamente** a performance geral.

Os indicadores utilizados são predominantemente de **rentabilidade**, decisão motivada pela **dificuldade de coleta sistemática** de outras métricas, como **liquidez** e **solvência** para todo o universo de empresas. Destaca-se, também, a **assimetria de aplicabilidade** dos indicadores entre diferentes setores: **giro de estoque**, por exemplo, é pertinente ao varejo, mas **não** a bancos ou empresas de tecnologia. Esse recorte presente no projeto favorece, então, setores com modelo de negócio melhor traduzidos em rentabilidade, como é o caso dos **bens industriais**, **materiais** e **consumo cíclico**, que foram os setores mais presentes como resultado da estratégia escolhida, e reduz a seleção de outros segmentos, como **empresas de tecnologia**.

Além disso, foram feitas as seguintes **hipóteses extras**, a fim de facilitar a execução do backtest:

- **Empresas não pagam dividendos**;
- A **taxa livre de risco** foi considerada **0**;
- **Todas as empresas da B3** têm **ações fracionadas**;
- **Não existem custos de transação**.

É válido citar também a **retirada de empresas do setor financeiro** da análise (bancos e seguradoras) por apresentarem uma **estrutura de balanço patrimonial diferente** dos outros setores. A razão dessa escolha se deu por essas empresas, por definição, **não apresentarem todos os indicadores de rentabilidade** escolhidos na análise.

Na fase de **validação interna**, o número de clusters indicados como ideal variou entre **três e oito**. Imagina-se, no entanto, que a utilização de **oito clusters** poderia indicar **overfitting**. Por outro lado, a **carteira composta de apenas 3 ações** teve **problemas no manejo de risco** — visto seu universo reduzido de opções — tendo **quedas maiores** do que a carteira sem tais restrições.

## Conclusão 

O projeto demonstrou que a estratégia de **otimização via clusterização**, na forma como foi implementada, **não cumpriu o objetivo** inicial de **reduzir risco** e **maximizar o Sharpe Ratio**. A carteira resultante apresentou **desempenho volátil**, **forte concentração** em poucos ativos e um **resultado acumulado negativo**, evidenciando **falhas de gestão de risco**.

![[../../imagens/projeto-cluster-portfolio/projeto-cluster-portfolio-5.png]]

>[!info]
>Comparação entre a **rentabilidade acumulada** da nossa carteira principal com o **Ibovespa** e com a **carteira sem clusterizar**, que apenas pegava ações do universo inteiro com maior maior Sharpe Ratio no período. Podemos perceber o desempenho ficou bem aquém do esperado.

Apesar de ter identificado **setores relevantes** e capturado **momentos de alta rentabilidade**, a estratégia mostrou-se **inconsistente** no longo prazo. A **diversificação** prometida pela clusterização **não** se concretizou, já que a **alocação excessiva** em um ou dois papéis **anulou** os benefícios esperados, performando **pior** que a carteira na qual **não houve clusterização**.

O estudo deixa claro que a **simples aplicação de clusterização** não é suficiente para **construir um portfólio robusto**. É necessário incorporar **controles de risco explícitos**, **limites de exposição por ativo** e **métricas adicionais além do Sharpe Ratio**. Sem esses mecanismos, a estratégia tende a se comportar como **especulação de curto prazo**, sem entregar **retorno ajustado ao risco** de forma sustentável.

Assim, a principal contribuição do trabalho foi **evidenciar os limites** da abordagem testada. Para evoluir, recomenda-se **ampliar o conjunto de indicadores**, introduzir **técnicas de rebalanceamento periódico** e **adotar parâmetros de risco mais rigorosos**. Só com esses ajustes a **clusterização** poderá servir de base para uma **estratégia quantitativa consistente** no mercado brasileiro.

## Referências

 - LEÓN, Diego; ARAGÓN, Arbey; SANDOVAL, Javier; HERNÁNDEZ, Germán; ARÉVALO, Andrés; NIÑO, Jaime. **Clustering algorithms for risk-adjusted portfolio construction**. *Procedia Computer Science*, v. 108C, p. 1334-1343, 2017. Disponível em: <https://www.sciencedirect.com/science/article/pii/S187705091730772X>. Acesso em: 20 ago. 2025.
- CAMPBELL, Sean D. **A review of backtesting and backtesting procedures**. *Finance and Economics Discussion Series*, Washington: Board of Governors of the Federal Reserve System, n. 2005-21, Apr. 2005. Disponível em: <https://www.federalreserve.gov/pubs/feds/2005/200521/200521pap.pdf>. Acesso em: 20 ago. 2025.
- CHRISTOFFERSEN, Peter. **Backtesting**. Montreal: McGill University; Copenhagen Business School; CREATES, 2008. Disponível em: <https://ssrn.com/abstract=2044825>. Acesso em: 20 ago. 2025.
- BOLOS, Marcel-Ioan; RUSU, Ștefan; LEORDEANU, Marius; SABĂU-POPA, Claudia Diana; PERTICĂȘ, Diana Claudia; CRIȘAN, Mihai-Ioan. **K-means clustering for portfolio optimization: symmetry in risk–return tradeoff, liquidity, profitability, and solvency**. *Symmetry*, v. 17, n. 847, 2025. Disponível em: <https://www.mdpi.com/2073-8994/17/6/847>. Acesso em: 20 ago. 2025.