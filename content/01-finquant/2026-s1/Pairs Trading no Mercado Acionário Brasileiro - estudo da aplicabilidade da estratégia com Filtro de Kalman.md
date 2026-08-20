---
tags:
  - nivel/avancado
  - trilha/finquant
title: |-
  Pairs Trading no Mercado Acionário Brasileiro -
  estudo da aplicabilidade da estratégia com Filtro
  de Kalman
---
_**Autores: Jayni Bitencourt Lima e Victor Braga**_

_**Repositório: [link](https://github.com/Jaynilima/Grupo4)**_
# 1. Objetivo do projeto

## 1.1 Objetivo geral 

A lógica do projeto parte da ideia de que algumas ações podem apresentar relações estatísticas relevantes ao longo do tempo, seja por pertencerem a setores semelhantes, por responderem a fatores econômicos comuns ou por apresentarem trajetórias históricas próximas. Nesse sentido, o projeto busca analisar se a estratégia de pairs trading pode ser aplicada ao mercado brasileiro a partir de dados históricos da B3 extraídos do Economatica. 
A estratégia consiste em identificar ações líquidas que apresentaram comportamento semelhante no passado, validar se esses pares possuem relação estatística de equilíbrio por meio da cointegração e, posteriormente, acompanhar dinamicamente o spread entre os ativos com o Filtro de Kalman. A partir disso, o estudo busca verificar se afastamentos anormais entre os preços relativos dos pares tendem a se corrigir ao longo do tempo. 

Com isso, pretende-se avaliar se esses desvios temporários podem gerar oportunidades de operação long-short, por meio da compra do ativo relativamente barato e da venda do ativo relativamente caro, apostando na convergência posterior da relação. Por fim, o projeto busca transformar esse comportamento estatístico em uma regra quantitativa de decisão, capaz de gerar sinais de entrada e saída e permitir a avaliação da performance financeira da estratégia por meio de backtest.

## 1.2 Objetivos específicos

1) Identificar e tratar uma base histórica de ações da B3, utilizando dados extraídos do Economatica, com preços ajustados, volume financeiro, quantidade de negócios, ISIN, ticker, situação CVM e classificação setorial.

2) Criar um identificador consistente para os ativos, priorizando o uso do ISIN quando disponível, a fim de reduzir problemas causados por mudanças de ticker e evitar que o mesmo papel seja tratado como ativos diferentes ao longo do tempo. 

3) Selecionar dinamicamente os ativos líquidos da B3 em janelas móveis, considerando cobertura mínima de dados, volume financeiro mediano e quantidade mediana de negócios, de forma a construir um universo elegível coerente para a formação dos pares.

4) Formar pares candidatos a partir da metodologia de distância mínima, identificando ativos com trajetórias normalizadas historicamente semelhantes dentro de cada janela de formação. 

5) Aplicar teste de cointegração aos pares pré-selecionados por distância mínima, com o objetivo de verificar se existe uma relação estatística de equilíbrio entre os preços dos ativos e reduzir o risco de selecionar pares com falsa reversão. 

6) Selecionar, em cada janela, os pares mais relevantes estatisticamente, considerando o menor p-valor de cointegração e a menor distância histórica como critérios de ordenação. 

7) Construir o spread dos pares selecionados e avaliar se seus desvios podem ser interpretados como oportunidades de pairs trading, respondendo à pergunta: a partir de qual nível de z-score o afastamento deixa de ser uma oscilação normal e passa a representar um possível sinal de operação? 

8) Aplicar o Filtro de Kalman para estimar dinamicamente a relação entre os ativos de cada par, substituindo o hedge ratio fixo por um beta variável ao longo do tempo. 

9) Gerar sinais quantitativos de entrada e saída a partir do z-score dinâmico do spread, definindo quando a estratégia deve abrir uma posição comprada no ativo relativamente barato e vendida no ativo relativamente caro, e quando deve encerrar a operação.

10) Avaliar o comportamento de convergência dos spreads, analisando se os pares tendem a retornar ao equilíbrio após os desvios, quanto tempo levam para normalizar e em quais situações continuam se afastando em vez de convergir.

11) Realizar o backtest da estratégia, simulando operações com regras definidas de entrada, saída por convergência, stop por divergência, stop por tempo e custos operacionais.

12) Avaliar o desempenho financeiro e o risco da estratégia, respondendo a questões como: a estratégia gera resultado líquido positivo? O retorno depende de poucas operações muito lucrativas ou é distribuído de forma mais consistente? Qual é o impacto das perdas e dos custos sobre a performance final? 

13) Analisar métricas de performance da estratégia, incluindo PnL total, PnL médio por operação, win rate, Sharpe anualizado, máximo drawdown, profit factor, payoff ratio e duração média dos trades. 

14) Comparar o desempenho da estratégia entre diferentes setores e combinações setoriais da B3, verificando se pares do mesmo setor, de setores diferentes ou de determinados grupos econômicos apresentam melhor potencial de reversão e performance

15) Construir uma estrutura de monitoramento futuro, em que pares previamente validados possam ser acompanhados ao longo do tempo e gerar sinais quando o z-score indicar afastamento relevante em relação ao equilíbrio estimado pelo modelo.

# 2. O que é Pairs Trading

## 2.1 Base Teórica

Pairs trading é uma estratégia de arbitragem estatística que opera sobre a relação de preços entre dois ativos com vínculo econômico comprovado. A ideia central é simples: se dois ativos compartilham os mesmos fundamentos — mesmo setor, mesma cadeia produtiva, mesma empresa em classes diferentes — seus preços tendem a se mover juntos ao longo do tempo. Quando, por alguma razão momentânea, essa relação se rompe e os preços se afastam mais do que o histórico indica como normal, a estratégia aposta na convergência: compra-se o ativo que ficou "barato" e vende-se simultaneamente o ativo que ficou "caro", esperando que o equilíbrio se restabeleça. 

Essa estrutura de operação, compra de um ativo e venda de outro ao mesmo tempo, é o que a torna market-neutral: o retorno não depende se o mercado sobe ou cai, mas exclusivamente de o spread entre os dois ativos voltar ao seu padrão histórico. Uma queda geral do mercado, por exemplo, afeta os dois ativos de forma semelhante e não compromete a operação.

O critério estatístico que sustenta a estratégia é a cointegração: dois ativos são cointegrados quando, apesar de cada preço individualmente ser imprevisível (seguindo um passeio aleatório), a diferença entre eles é estacionária — oscila em torno de uma média com variância estável. É essa propriedade que garante que o spread tem de voltar, no sentido estatístico, e que distingue pairs trading de uma aposta direcional.

A literatura (Gatev et al., 2006; Vidyamurthy, 2004) classifica os vínculos econômicos válidos em seis categorias: 

(i) Mesma empresa, classes diferentes — ações ON e PN da mesma companhia compartilham o mesmo fluxo de caixa e diferem apenas em direitos políticos. Ex.: PETR3/PETR4, GGBR3/GGBR4. 

(ii) Holding e controlada — o valor da holding deriva da participação na controlada, com desconto historicamente estável. Ex.: BRAP4/VALE3, ITSA4/ITUB4. 

(iii) Mesmo setor e modelo de negócio — concorrentes sujeitos aos mesmos drivers de demanda, custos e regulação. Ex.: ITUB4/BBDC4 (bancos), JBSS3/MRFG3 (frigoríficos), ASAI3/CRFB3 (atacarejo).

(iv) Mesma cadeia produtiva — empresas em elos diferentes da mesma cadeia, expostas ao mesmo ciclo. Ex.: VALE3/CSNA3 (minério-aço), SUZB3/KLBN11 (papelcelulose). 

(v) Fator macro comum — ativos cuja relação vem de exposição compartilhada a um driver externo (câmbio, juros, commodity). Ex.: exportadoras dolarizadas; empresas alavancadas sensíveis à Selic.

(vi) Arbitragem direta — mesmo ativo em mercados diferentes (ações ON na B3 vs. ADRs na NYSE).

# 2.2 Histórico de Uso

A estratégia de pairs trading foi formalizada por Gatev, Goetzmann e Rouwenhorst (2006), mas já era praticada por desks quantitativos desde os anos 1980, com destaque para o grupo de Morgan Stanley liderado por Nunzio Tartaglia. O arcabouço estatístico que sustenta a estratégia — a teoria da cointegração — foi desenvolvido por Engle e Granger (1987), rendendo-lhes o Prêmio Nobel de Economia em 2003. 

No Brasil, a pesquisa empírica sobre pairs trading na B3 ainda é escassa em comparação com o mercado americano. O ambiente brasileiro apresenta características que tornam o tema particularmente interessante: a existência estrutural de pares ON/PN da mesma empresa (ex.: PETR3/PETR4), a relação holding controlada em grandes conglomerados (ex.: ITSA4/ITUB4), e setores com poucas empresas de capital aberto operando em condições quase idênticas (energia elétrica, bancos, frigoríficos). Esses fatores criam vínculos econômicos persistentes que são candidatos naturais à cointegração de longo prazo.

## 2.3 Importância para o mercado financeiro

Pairs trading é relevante por múltiplas razões. Como estratégia marketneutral, gera retorno independente da direção geral do mercado, o que a torna atraente para gestão de risco em carteiras de ações. Do ponto de vista de eficiência de mercado, a estratégia contribui para acelerar a convergência de preços de ativos com fundamentos comuns, reduzindo distorções temporárias. Para analistas e gestores quantitativos, ela oferece um método rigoroso de formalizar relações econômicas já conhecidas informalmente — como o desconto estrutural de uma holding frente à sua controlada — e transformá-las em regras operacionais testáveis. 

No contexto brasileiro, a estratégia também serve como instrumento de análise comparativa entre setores: diferentes segmentos da B3 apresentam graus distintos de cointegração, e mapear essas diferenças permite compreender melhor a estrutura de dependência do mercado acionário nacional.

# 3. Metodologia

A metodologia do projeto foi construída a partir de uma adaptação da abordagem clássica de pairs trading apresentada por Gatev, Goetzmann e Rouwenhorst no artigo “Pairs Trading: Performance of a Relative-Value Arbitrage Rule”. O artigo testa uma estratégia de relative value arbitrage em ações, partindo da ideia de que dois ativos com trajetórias historicamente semelhantes podem apresentar desvios temporários de preço e, posteriormente, convergir. A estratégia original forma pares com base na menor distância entre séries de preços normalizadas e opera quando os preços divergem além de um limite estatístico, normalmente dois desvios-padrão, encerrando a posição quando há convergência. 

No artigo, a metodologia possui duas etapas principais: um período de formação, no qual os pares são selecionados, e um período de negociação, no qual a estratégia é testada. Durante a formação, os autores filtram ações líquidas, constroem um índice de retorno acumulado para cada ação e escolhem os pares pela menor soma dos desvios quadráticos entre as séries normalizadas. Depois, no período de negociação, abrem posições long-short quando os preços divergem e encerram quando há convergência.

O presente projeto utiliza essa lógica como ponto de partida, mas realiza adaptações importantes para aumentar o rigor estatístico e adequar a estratégia ao mercado brasileiro, além de adaptar ao período realizado, com novas formas mais rigorosas de formação dos pares. Em vez de formar pares apenas pela distância mínima, utilizamos a distância mínima como pré-filtro (para deixar o projeto mais leve) e, em seguida, aplicamos teste de cointegração para verificar se existe evidência estatística de relação de equilíbrio entre os ativos. Além disso, substituímos o hedge ratio fixo por um hedge ratio dinâmico estimado por Filtro de Kalman, permitindo que a relação entre os ativos varie ao longo do tempo.

A metodologia foi organizada em seis notebooks:]

1. tratamento dos dados brutos; 
2. junção com informações cadastrais e setoriais; 
3. seleção dinâmica dos ativos líquidos; 
4. formação dos pares por distância mínima e cointegração; 
5. estimação dinâmica com Filtro de Kalman; 
6. backtest da estratégia

## 3.1 Fonte de dados e base metodológico

### 3.1.1 Dados utilizados

A base principal do projeto foi extraída do Economatica, contendo dados históricos de ações negociadas na B3. Foram utilizados preços ajustados, volume financeiro, quantidade de negócios, ticker, ISIN, situação CVM e classificação setorial dos ativos.

O uso de preços ajustados é essencial porque eventos como dividendos, desdobramentos, grupamentos e outros proventos podem alterar artificialmente o preço de uma ação. Como a estratégia depende da comparação entre trajetórias de preços, trabalhar com preços não ajustados poderia gerar falsos desvios e comprometer a formação dos pares. 

A base cadastral e setorial também foi extraída do Economatica. Ela foi usada para complementar os dados de preço com informações como ISIN, nome da empresa, classe da ação, situação CVM, setor, subsetor e segmento Bovespa. Essas informações foram importantes para criar um identificador mais robusto dos papéis e permitir análises posteriores por setor ou combinação setorial.

### 3.2.1 Artigo base e adaptação metodológica

O artigo de Gatev, Goetzmann e Rouwenhorst é uma das principais referências em pairs trading. Nele, os autores procuram ações que andaram juntas no passado, selecionando pares pela menor distância entre séries normalizadas. A ideia central é que, se duas ações foram historicamente próximas em termos relativos, uma divergência temporária entre elas pode representar uma oportunidade de arbitragem estatística. 

A distância utilizada no artigo pode ser representada como:

$$
D_{ij} = \sum_{t=1}^{T} \left( P^{norm}_{i,t} - P^{norm}_{j,t} \right)^2
$$

$P^{norm}_{i,t}$ é o preço normalizado do ativo $i$ no tempo $t$, e $D_{ij}$ representa a distância histórica entre os ativos $i$ e $j$.

Quanto menor a distância, mais semelhantes foram as trajetórias dos dois ativos no período de formação.

Neste projeto, essa abordagem foi adaptada. A distância mínima não foi usada como critério final de seleção, mas sim como um filtro inicial para reduzir o universo de pares. Em seguida, os pares pré-selecionados foram submetidos ao teste de cointegração. Essa alteração foi feita porque duas séries podem ter trajetórias parecidas durante um período sem necessariamente possuírem uma relação estatística de equilíbrio. A cointegração ajuda a reduzir o risco de selecionar pares com falsa reversão.

### 3.2.3 Uso do Filtro de Kalman

Após a formação dos pares, o modelo utiliza Filtro de Kalman para estimar dinamicamente a relação entre os dois ativos. Em uma abordagem tradicional com regressão linear simples, a relação entre os ativos seria estimada por um beta fixo:

$$ \log(P_{1,t}) = \alpha + \beta 
\log(P_{2,t}) + \varepsilon_t $$

Nesse caso, o beta é único para toda a janela analisada. Porém, em mercados financeiros, a relação entre dois ativos pode mudar ao longo do tempo em função de eventos corporativos, mudanças de liquidez, alterações macroeconômicas, choques setoriais ou mudanças estruturais no mercado. Por isso, o projeto utiliza uma versão dinâmica dessa relação:

$$ \log(P_{1,t}) = \alpha_t + \beta_t \log(P_{2,t}) + \varepsilon_t $$

Nessa formulação, αt e βt variam ao longo do tempo. O beta dinâmico estimado pelo Kalman funciona como hedge ratio variável do par, permitindo que a estratégia ajuste a proporção entre os ativos conforme a relação estatística entre eles evolui. O resíduo da equação é interpretado como o spread dinâmico.

$$ spread_t = \log(P_{1,t}) - \alpha_t - \beta_t \log(P_{2,t}) $$

Esse spread é a variável central da estratégia. Quando ele se afasta muito de seu comportamento esperado, o modelo entende que há uma possível divergência temporária entre os ativos. A partir dele, calcula-se o z-score:

$$ z_t = \frac{spread_t - \mu_{spread}}{\sigma_{spread}} $$

No caso do Kalman, o z-score pode ser calculado usando a inovação do modelo e sua variância estimada. A lógica é a mesma, que é medir o quanto o spread está distante do padrão esperado.

## 3.2 Tratamento dos dados do Economatica (notebook 1)

### 3.2.1 Padronizaçãoe limpeza da base bruta

O primeiro notebook teve como objetivo transformar a base bruta extraída do Economatica em uma base organizada, consistente e adequada para análise quantitativa. 

A base original veio em formato CSV e possuía grande volume de observações. Por isso, após o tratamento inicial, os dados foram salvos em formato Parquet, que é mais eficiente para leitura e armazenamento. Essa escolha melhora o desempenho dos notebooks seguintes, principalmente porque o projeto trabalha com séries históricas extensas e múltiplos ativos. 

Foram padronizados os nomes das colunas, removendo espaços, acentos, barras e caracteres especiais. Essa etapa não é apenas estética: ela reduz a chance de erros no código e garante consistência na manipulação dos dados. 

Também foram convertidas as colunas de data e variáveis numéricas. A data foi transformada para formato temporal, permitindo ordenação cronológica e construção de janelas móveis. As colunas de preço, volume financeiro e quantidade de negócios foram convertidas para formato numérico, com tratamento de valores inválidos.

### 3.2.2 Uso de preços ajustados

A variável principal de preço utilizada foi o fechamento ajustado. Essa escolha é fundamental em um estudo de séries temporais de ações, porque o preço ajustado corrige eventos corporativos que alteram mecanicamente o preço da ação. 

Se fossem usados preços não ajustados, uma queda causada por pagamento de dividendos ou desdobramento poderia ser interpretada como movimento econômico real. Isso distorce o cálculo de retornos, a normalização das séries, a distância entre os ativos, o teste de cointegração e o backtest. Portanto, o fechamento ajustado foi usado como referência para todas as etapas posteriores

### 3.2.3 Tratamento de observações inválidas 

Foram removidas observações sem data, sem ticker ou sem preço de fechamento ajustado. Também foram excluídos preços menores ou iguais a zero, pois não possuem interpretação econômica válida e impedem o uso de logaritmos.

A limpeza nesta etapa foi propositalmente restrita a problemas de consistência básica. Não foram aplicados filtros de liquidez no Notebook 01, porque a seleção de liquidez foi feita de forma dinâmica posteriormente. Essa separação evita eliminar ativos com base em critérios fixos antes de observar sua liquidez em cada janela.

### 3.2.4 Organização da base tratada

Ao final, a base foi organizada com informações essenciais para o restante do projeto: ticker, data, ativo, preços ajustados, volume financeiro, quantidade de negócios e quantidade de títulos. A saída do Notebook 01 foi a base tratada de preços, que serviu como entrada para a etapa seguinte.

# 3.3 Junção da base de preços com informações cadastrais e setoriais (notebook 2)

### 3.3.1 Objetivo da etapa

O segundo notebook teve como objetivo enriquecer a base de preços com informações cadastrais e setoriais dos ativos. Essa etapa foi necessária porque o ticker, sozinho, não é um identificador suficientemente robusto para um estudo histórico longo. 

Ao longo do tempo, uma empresa pode alterar seu ticker, diferentes classes de ações podem coexistir e alguns ativos podem ser cancelados. Por isso, a identificação dos papéis precisava ser feita com cuidado para evitar que o mesmo ativo fosse tratado como ativos diferentes ou que ativos diferentes fossem tratados como um único ativo. Por esse motivo, foi necessário a criação de uma nova forma para denominar os ativos, o “id_papel”, baseado no ISIN de cada ativo, caso o ISIN fosse ausente, o Ticker era usado normalmente.

### 3.3.2  Tratamento dos valores faltantes 

Um ponto crítico desta etapa foi o tratamento de valores faltantes. Na exportação do Economatica, alguns campos vazios apareciam como hífen (-).

Para o pandas, esse hífen não é automaticamente reconhecido como valor nulo, mas sim como texto. Esse detalhe é metodologicamente importante porque, se o ISIN ausente fosse mantido como -, vários ativos diferentes poderiam receber o mesmo identificador. Por isso, antes de criar o identificador do papel, os valores “-”, strings vazias e textos como nan foram convertidos para NaN. 

Essa correção garante que dados faltantes sejam corretamente interpretados como nulos e evita a criação de identificadores artificiais.

### 3.3.3 Criação do identificados do papel

A principal variável criada neste notebook foi o id_papel. A regra adotada foi de usar o ISIN se estiver disponível, caso não esteja, usar o Ticker. 

O uso do ISIN foi priorizado porque ele identifica o papel de forma mais estável do que o ticker. O ticker é um código de negociação e pode mudar ao longo do tempo, enquanto o ISIN tende a representar de forma mais consistente o instrumento financeiro. 

Essa escolha reduz o risco de tratar uma mudança de ticker como se fosse um novo ativo. Quando o ISIN não estava disponível, o ticker foi usado como alternativa, evitando perda desnecessária de observações. 

### 3.3.4 Junção com a base de preços 

Após o tratamento da base cadastral, as informações de ISIN, nome, classe, situação CVM, setor, subsetor e segmento foram adicionadas à base de preços. A junção permitiu que cada observação diária de preço carregasse também informações cadastrais e setoriais. Isso foi importante por dois motivos.

Primeiro, porque a formação e o backtest dos pares deveriam ser feitos com uma identificação consistente dos ativos. Segundo, porque as informações setoriais seriam preservadas para análises posteriores, como verificar se os pares selecionados pertencem ao mesmo setor ou a setores diferentes.

### 3.3.5 Tratamento de duplicidades

Depois da criação do “id_papel”, foram verificadas duplicidades por papel e data, para garantir que cada papel tivesse apenas uma observação por dia. 

Quando havia duplicidade, a regra metodológica foi manter a observação com maior volume financeiro. A justificativa é que, em caso de conflito, a observação com maior volume tende a representar melhor a negociação principal daquele papel naquele dia. 

A saída do Notebook 02 foi a base dados_economatica_B3_com_setores, e formato parquet, contendo preços ajustados, informações de liquidez, identificador do papel e dados setoriais.

## 3.4 Seleção dinâmica dos ativos líquidos 

### 3.4.1 Objetivo da etapa 

O terceiro notebook teve como objetivo construir um universo de ativos líquidos ao longo do tempo.Um par pode parecer estatisticamente adequado, mas ser inviável economicamente se um ou ambos os ativos apresentarem baixa liquidez. Baixa liquidez aumenta custos de transação, slippage, dificuldade de execução e risco de distorção nos preços observados. 

Por isso, antes da formação dos pares, foi criada uma base histórica de ativos possíveis por liquidez

### 3.4.2 Janelas móveis de formação

A seleção de liquidez foi feita em janelas móveis mensais. Cada janela considerou os últimos 504 pregões, aproximadamente dois anos de dados. 
A escolha de 504 pregões busca equilibrar duas necessidades. Por um lado, a janela precisa ser longa o suficiente para avaliar a liquidez típica dos ativos com estabilidade. Por outro lado, ela não pode ser tão longa a ponto de incorporar informações muito antigas que já não representam a condição atual do ativo. 

A janela móvel mensal permite que o universo líquido seja atualizado ao longo do tempo. Isso evita selecionar ativos com base na amostra completa e reduz o risco de look-ahead bias, pois a liquidez de cada mês é calculada apenas com informações disponíveis até aquele momento.

### 3.4.3 Critério de cobertura

Para cada ativo em cada janela, foi calculada a cobertura de dados, com cobertura mínima de 80%. Assim, um ativo só poderia entrar no universo líquido se tivesse preço disponível em pelo menos 80% dos pregões da janela.

### 3.4.4 Critério de volume e negócios 

Além da cobertura, foram utilizados dois indicadores de liquidez: 

- volume financeiro mediano; 
- quantidade mediana de negócios. 

A mediana foi escolhida em vez da média porque é menos sensível a eventos extremos. Em mercados financeiros, um ativo pode apresentar volume muito alto em poucos dias devido a notícias, rebalanceamentos de índice ou eventos corporativos. A média poderia superestimar a liquidez típica do ativo. 

Inicialmente, foram mantidos ativos com volume financeiro mediano positivo e quantidade mediana de negócios positiva. Em seguida, para evitar a inclusão de ativos com liquidez residual, foi removido o quartil inferior de liquidez dentro de cada janela

Esse filtro por percentil é mais adequado do que um corte fixo em reais, porque a liquidez do mercado muda ao longo do tempo. Um volume considerado alto em 2012 pode ser pouco representativo em 2024. Ao usar percentis dentro de cada janela, o critério se adapta ao nível de liquidez de cada período.

### 3.4.5 Score de liquidez

Depois dos filtros mínimos, os ativos foram ranqueados por volume financeiro mediano e quantidade mediana de negócios. Foi criado um score de liquidez:

$$
\text{Score\_Liquidez}_i = \text{Rank}(\text{Volume}_i) + \text{Rank}(\text{Negócios}_i)
$$

Quanto menor o score, mais líquido é o ativo, pois ele combina boa posição em volume financeiro e em quantidade de negócios. 

Esse score foi usado para ordenar os ativos, mas não para restringir rigidamente o universo a um número fixo, como top 100 ou top 150. A decisão de não impor um corte fixo foi importante para preservar um universo amplo e evitar excluir ativos relevantes em determinados períodos ou setores.

### 3.4.6 Resultado de seleção de liquidez

A saída do Notebook 03 foi a base liquidez_historica.parquet. Cada linha representa um ativo líquido em uma determinada janela mensal. 

Essa base define o universo elegível para a formação dos pares no Notebook

## 3.5 Formção dos pares por distância mínima e cointegração 

### 3.5.1 Objetivo da etapa

O quarto notebook teve como objetivo selecionar, em cada janela, os pares de ativos que seriam posteriormente modelados pelo Filtro de Kalman. A formação dos pares foi feita em duas etapas: 

7. pré-seleção por distância mínima; 
8. validação por cointegração. 

Essa combinação foi escolhida para equilibrar viabilidade computacional e rigor estatístico. A distância mínima reduz o número de pares candidatos, enquanto a cointegração verifica se existe uma relação estatística de equilíbrio entre os ativos

### 3.5.2 Construção das séries normalizadas 

Para cada janela, foram selecionados os ativos líquidos definidos no Notebook 03. Em seguida, os preços ajustados desses ativos foram normalizados. A normalização foi feita dividindo o preço de cada ativo pelo primeiro preço válido da janela:

$$
P_{i,t}^{norm} = \frac{P_{i,t}}{P_{i,0}}
$$

em que : 

- $P_{i,t}$ é o preço ajustado do ativo $i$ no tempo $t$;

- $P_{i,0}$ é o primeiro preço válido do ativo na janela.

Essa transformação faz com que todos os ativos comecem a janela em 1. Assim, a comparação passa a ser entre trajetórias relativas, e não entre preços nominais. Isso é importante porque uma ação que custa R$ 5 e outra que custa R$ 80, por exemplo, podem ter comportamentos relativos semelhantes, mesmo com preços absolutos muito diferentes.

### 3.5.3 Distância mínima como pré-filtro

Após a normalização, foi calculada a distância entre cada par possível de ativos:

$$
D_{ij} = \sum_{t=1}^{T} \left( P^{norm}_{i,t} - P^{norm}_{j,t} \right)^2
$$

Quanto menor o valor de $D_{ij}$, mais próximas foram as trajetórias normalizadas dos ativos i e j durante a janela. 

A distância mínima foi usada como pré-filtro, não como critério final. Em cada janela, foram mantidos os pares com menores distâncias para posterior teste de cointegração. 

Esse procedimento reduz o esforço computacional. Sem o pré-filtro, seria necessário testar cointegração para todas as combinações possíveis de ativos líquidos. Como o número de pares cresce rapidamente com o tamanho do universo, a distância mínima torna a etapa estatística mais eficiente.

### 3.5.4 Teste de cointegração 

Depois da pré-seleção por distância, os pares candidatos foram submetidos ao teste de cointegração de Engle-Granger. 

A cointegração é importante porque duas séries podem se mover de forma parecida por um período sem que exista uma relação de equilíbrio entre elas. A distância mínima captura semelhança de trajetória, mas não garante reversão estatística do spread. 

A ideia da cointegração é verificar se uma combinação linear entre os preços dos dois ativos é estacionária. Em termos simplificados, avaliamos se existe uma relação do tipo:

$$\log(P_{1,t}) = \alpha + \beta \log(P_{2,t}) + \varepsilon_t$$

em que o resíduo et deve apresentar comportamento estacionário. 

Se o resíduo for estacionário, entende-se que os ativos possuem uma relação de equilíbrio de longo prazo. Isso é desejável em pairs trading porque a estratégia depende da expectativa de que desvios temporários sejam corrigidos. Foram aprovados apenas pares com p-valor menor ou igual a 5%

### 3.5.5 OLS na formação

Durante a formação dos pares, foi estimada uma regressão OLS para obter parâmetros iniciais da relação entre os ativos:

$$\log(P_{1,t}) = \alpha_{OLS} + \beta_{OLS} \log(P_{2,t}) + \varepsilon_t$$

Esses parâmetros não foram tratados como o modelo final da estratégia. Eles serviram apenas como referência da janela de formação e como possível ponto inicial para a modelagem dinâmica posterior.

O spread da formação foi calculado como:

$$spread_t^{OLS} = \log(P_{1,t}) - \alpha_{OLS} - \beta_{OLS} \log(P_{2,t})$$

A média e o desvio-padrão desse spread foram armazenados para caracterizar o par e apoiar a etapa seguinte.

### 3.5.6 Seleção dos 2o pares por janela 

Após o teste de cointegração, os pares aprovados foram ordenados prioritariamente pelo menor p-valor de cointegração e, em seguida, pela menor distância. A lógica foi:

- menor p-valor indica evidência estatística mais forte de cointegração;

- menor distância indica maior semelhança histórica entre as trajetórias.

Em cada janela, foram selecionados até 20 pares. 

A decisão de trabalhar com 20 pares segue a tradição do artigo-base, que analisa carteiras com os 20 melhores pares, e também permite controlar o tamanho da carteira para a etapa de modelagem e backtest.

### 3.5.7 Decisão de não restringir por setor

A formação principal dos pares não foi restrita por setor. Essa decisão foi tomada porque uma restrição setorial poderia excluir relações estatísticas relevantes entre ativos de setores diferentes. 

Em mercados como a B3, ativos de setores distintos podem compartilhar fatores econômicos comuns, como commodities, juros, câmbio, inflação, crédito ou ciclo econômico. Por exemplo, empresas de energia, mineração, siderurgia e petróleo podem ser afetadas por choques macroeconômicos semelhantes.

Ao não restringir os pares por setor, a metodologia permite que os dados indiquem quais relações são estatisticamente relevantes. As informações setoriais foram preservadas para análise posterior, permitindo avaliar se os pares selecionados pertencem ao mesmo setor, a setores diferentes ou a determinadas combinações setoriais.

### 3.5.8 Resultados da formação dos pares 

A saída do Notebook 04 foi a base `pares_top20_cointegracao.parquet`, contendo os pares selecionados por janela, seus rankings, p-valores de cointegração, distâncias, parâmetros OLS da formação e informações setoriais. 

Essa base foi usada como entrada do Notebook 05.

## 3.6 Modelo com Filtro de Kalman (notebook 5)

### 3.6.1 Objetivo da etapa 

O quinto notebook teve como objetivo aplicar o Filtro de Kalman aos pares formados no Notebook 04. 

No projeto, o Filtro de Kalman foi utilizado para estimar de forma dinâmica a relação entre os dois ativos de cada par. A ideia central é que o comportamento do ativo 1 pode ser explicado, em parte, pelo comportamento do ativo 2, mas essa relação não é fixa ao longo do tempo. Isso é importante porque, em uma estratégia de pairs trading, o hedge ratio determina a proporção relativa entre os ativos no spread. Se essa proporção muda ao longo do tempo e o modelo não se ajusta, os sinais podem ficar distorcidos. 

Usar esse filtro é importante porque mesmo que dois papéis sejam cointegrados em uma janela de formação, choques de mercado, mudanças de liquidez, alterações macroeconômicas ou eventos específicos das empresas podem modificar temporariamente a relação entre eles. O Kalman permite que o modelo se ajuste gradualmente a essas mudanças, em vez de manter um beta fixo durante todo o período.

# 3.6.2 Relação dinâmica entre os ativos 

O modelo considera que a relação entre os dois ativos do par segue:
$$

\log(P_{1,t}) = \alpha_t + \beta_t \log(P_{2,t}) + \varepsilon_t

$$
em que:

- $\alpha_t$ é o intercepto dinâmico;
- $\beta_t$ é o hedge ratio dinâmico;
- $\varepsilon_t$ é o resíduo ou spread dinâmico.

A diferença em relação ao OLS tradicional é que alpha e beta não são fixos. Eles são atualizados ao longo do tempo conforme novas observações de preço aparecem.

#### 3.6.3 Estrutura do Filtro de Kalman

O modelo define um vetor de estado:

$$

\theta_t = \begin{bmatrix} \alpha_t \\ \beta_t \end{bmatrix}

$$

A equação de observação é:

$$

y_t = F_t \theta_t + \varepsilon_t

$$

em que:

$$

y_t = \log(P_{1,t})

$$

$$

F_t = \begin{bmatrix} 1 & \log(P_{2,t}) \end{bmatrix}

$$

Ao substituir esses termos na equação mencionada no tópico anterior, temos:

$$

\log(P_{1,t}) = \begin{bmatrix} 1 & \log(P_{2,t}) \end{bmatrix} \begin{bmatrix} \alpha_t \\ \beta_t \end{bmatrix} + \varepsilon_t

$$

A multiplicação matricial resulta exatamente na equação original. Portanto, essa forma matricial não muda o significado econômico do modelo. Ela apenas organiza a estimação para que o Filtro de Kalman consiga atualizar $\alpha_t$ e $\beta_t$ ao longo do tempo.

Na prática, a cada nova observação de preço, o Kalman realiza duas etapas principais. Primeiro, ele faz uma previsão da relação entre os ativos com base nos parâmetros estimados até o período anterior. Segundo, faz uma atualização dos parâmetros com base no erro observado.

A inovação do modelo é:

$$

\nu_t = y_t - F_t \hat{\theta}_{t|t-1}

$$

Essa inovação representa a diferença entre o valor observado do ativo 1 e o valor estimado pelo modelo. No contexto da estratégia, ela é interpretada como o spread dinâmico.
#### 3.6.4 Estrutura do Filtro de Kalman

O spread dinâmico é dado por:

$$

spread_t^{Kalman} = \log(P_{1,t}) - \alpha_t - \beta_t \log(P_{2,t})

$$

O z-score mede o afastamento padronizado desse spread. De forma geral:

$$

z_t = \frac{spread_t}{\sigma_t}

$$

em que $\sigma_t$ representa a incerteza estimada do spread ou da inovação.

A interpretação é:

- $z_t > 0$: o ativo 1 está acima do valor esperado em relação ao ativo 2;

- $z_t < 0$: o ativo 1 está abaixo do valor esperado em relação ao ativo 2;

- valores extremos indicam possíveis oportunidades de reversão.

#### 3.6.5 Geração dos sinais

Os sinais foram definidos a partir do z-score dinâmico. Quando $z_t$ é maior ou igual a 2, o modelo interpreta que o ativo 1 está caro em relação ao ativo 2. Nesse caso, a posição indicada é Short para ativo 1 e Long para ativo 2.

Quando $z_t$ é menor ou igual a $-2$, o modelo interpreta que o ativo 1 está barato em relação ao ativo 2. Nesse caso, a posição indicada é Short para ativo 2 e Long para ativo 1. Quando o z-score está dentro desse intervalo, a posição permanece neutra.

A saída do Notebook 05 foi a base `modelo_kalman_sinais.parquet`, contendo, para cada par e data de teste:

- alpha dinâmico;

- beta dinâmico;

- spread dinâmico;

- z-score dinâmico;

- sinal de trading;

- informações do par e da janela.

Essa base foi usada como entrada para o backtest.

### 3.7 Backtest (notebook 06)

#### 3.7.1 Objetivo da etapa

O sexto notebook teve como objetivo avaliar economicamente a estratégia construída nos notebooks anteriores.

Até o Notebook 05, o projeto havia identificado pares, estimado suas relações dinâmicas e gerado sinais. O backtest transforma esses sinais em operações simuladas e calcula o resultado financeiro da estratégia.

Essa etapa é essencial porque uma relação estatística entre ativos não garante, por si só, uma estratégia lucrativa. É necessário avaliar se os sinais geram retornos positivos após considerar regras de entrada, saída, stop e custos operacionais.

#### 3.7.2 Regras de entrada e saída

No backtest, as operações foram abertas a partir dos sinais gerados pelo z-score dinâmico do Filtro de Kalman. A lógica é que, quando o spread entre os dois ativos se afasta muito do seu comportamento esperado, pode existir uma oportunidade de reversão à média.

A entrada ocorre quando o z-score atinge um nível extremo. Quando o z-score está muito positivo, o modelo interpreta que o ativo 1 está relativamente caro em relação ao ativo 2. Nesse caso, a estratégia abre uma posição vendida no ativo 1 e comprada no ativo 2, esperando que o spread volte a cair. Quando o z-score está muito negativo, o modelo interpreta que o ativo 1 está relativamente barato em relação ao ativo 2. Nesse caso, a estratégia abre uma posição comprada no ativo 1 e vendida no ativo 2, esperando que o spread volte a subir.

As saídas foram definidas por três critérios. O primeiro é a saída por convergência, que acontece quando o z-score retorna para uma região próxima do equilíbrio. Nesse caso, entende-se que o desvio relativo entre os ativos foi corrigido, então a operação é encerrada.

O segundo critério é o stop por divergência. Ele ocorre quando, em vez de convergir, o spread continua se afastando do equilíbrio. Essa regra serve para limitar perdas quando a relação entre os ativos se deteriora ou quando o sinal inicial não se confirma.

O terceiro critério é o stop por tempo. Caso a posição permaneça aberta por muitos pregões sem convergir nem atingir o stop de divergência, ela é encerrada automaticamente. Essa regra evita que a estratégia mantenha posições indefinidamente em pares que deixaram de apresentar reversão no período analisado.

Além disso, caso uma posição ainda estivesse aberta no fim da janela de teste, ela foi encerrada na última data disponível daquela janela. Isso garante que cada operação seja avaliada dentro do período correto, sem carregar posições para fora da janela definida na metodologia.

#### 3.7.3 Cálculo do retorno do trade

O retorno de cada ativo foi calculado com diferenças de log-preços:

$$

r_1 = \log(P_{1,sa\acute{\imath}da}) - \log(P_{1,entrada})

$$

$$

r_2 = \log(P_{2,sa\acute{\imath}da}) - \log(P_{2,entrada})

$$

O retorno do spread foi calculado usando o beta de entrada:

$$
r_{spread} = r_1 - \beta_{\text{entrada}}^{\,r_2}
$$

Quando a posição é comprada no ativo 1 e vendida no ativo 2, o retorno da operação segue diretamente o retorno do spread. Quando a posição é vendida no ativo 1 e comprada no ativo 2, o sinal do retorno é invertido, porque a estratégia ganha quando o spread cai.

O beta utilizado foi o beta estimado pelo Kalman no momento de entrada da operação. Isso mantém coerência com a proposta do modelo, que utiliza hedge ratio dinâmico em vez de uma relação fixa entre os ativos.

#### 3.7.4 Custos operacionais

O backtest também considerou custos operacionais. Essa etapa é importante porque uma estratégia pode parecer lucrativa antes dos custos, mas deixar de ser atrativa quando são considerados custos de corretagem, emolumentos e impactos de execução.

Foi adotado um custo em basis points, unidade comum em finanças para representar pequenas porcentagens. No modelo, considerou-se um custo de 10 bps por lado da operação, equivalente a 0,10%. Como cada trade possui entrada e saída, o custo total considerado foi de aproximadamente 0,20% por operação.

O resultado líquido foi calculado subtraindo esse custo do resultado bruto da operação. Assim, a análise final reflete uma estimativa mais realista da performance da estratégia.

#### 3.7.4 Construção da curva de resultado

Depois de calcular o resultado de cada trade, o PnL líquido foi atribuído à data de saída da operação. Em dias sem encerramento de trades, o resultado diário foi considerado igual a zero.

A partir disso, foi construída a curva acumulada da estratégia, somando os resultados líquidos ao longo do tempo. Essa curva permite visualizar a evolução do desempenho da estratégia e identificar períodos de ganho, perda ou estabilidade.

Também foi calculado o drawdown, que mede a queda da curva acumulada em relação ao seu pico anterior. Essa métrica é importante porque mostra a pior perda acumulada sofrida pela estratégia durante o período analisado.

#### 3.7.5 Métricas de performance

Após a simulação dos trades, foram calculadas métricas gerais para avaliar a qualidade da estratégia.

As principais métricas foram número total de trades, win rate, PnL total, PnL médio por operação, volatilidade diária, Sharpe anualizado, máximo drawdown, profit factor, payoff ratio e duração média dos trades.

O win rate mede a proporção de operações lucrativas em relação ao total de operações. Ele ajuda a entender a frequência de acerto da estratégia, mas não deve ser analisado sozinho, porque uma estratégia pode acertar muitas vezes e ainda assim perder dinheiro se as perdas forem muito maiores que os ganhos.

O PnL total mostra o resultado líquido acumulado da estratégia. O PnL médio mostra o resultado médio por trade. Essas métricas ajudam a avaliar o retorno absoluto gerado pelo modelo.

O Sharpe anualizado foi utilizado para avaliar o retorno ajustado ao risco. Ele compara o retorno médio da estratégia com sua volatilidade, permitindo entender se o retorno obtido compensa o risco assumido.

O máximo drawdown indica a maior perda acumulada em relação a um pico anterior da curva. Essa métrica é importante para avaliar o risco de queda e a estabilidade da estratégia.

O profit factor compara o total ganho nas operações vencedoras com o total perdido nas operações perdedoras. Já o payoff ratio compara o ganho médio dos trades vencedores com a perda média dos trades perdedores.

Por fim, a duração média dos trades indica por quanto tempo, em média, as posições permaneceram abertas. Essa informação ajuda a entender se a estratégia é mais curta e frequente ou se depende de operações mais longas.

#### 3.7.6 Análises segmentadas

Além das métricas gerais, foi realizada uma análise dos resultados por diferentes agrupamentos.

A análise por par permite identificar quais pares contribuíram mais para o resultado total e quais tiveram pior desempenho. Isso é importante para verificar se a estratégia dependeu de poucos pares específicos ou se o retorno foi distribuído entre várias relações.

A análise por ano permite observar se a estratégia foi consistente ao longo do tempo ou se o desempenho ficou concentrado em períodos específicos. Esse ponto é relevante porque uma estratégia robusta deve apresentar comportamento razoavelmente estável em diferentes contextos de mercado.

A análise por setor e por combinação setorial foi incluída porque a formação dos pares não foi restrita a ativos do mesmo setor. Assim, depois do backtest, foi possível verificar quais setores ou combinações de setores apresentaram melhor desempenho.

Por fim, a análise por razão de saída mostra se os trades foram encerrados principalmente por convergência, por stop de divergência, por stop de tempo ou pelo fim da janela. Essa análise ajuda a entender se a estratégia está funcionando como esperado. Em uma estratégia de reversão à média, espera-se que uma parcela relevante das saídas ocorra por convergência.

#### 3.7.7 Resultado da etapa

A saída do Notebook 06 foi uma base com todos os trades simulados, contendo informações como data de entrada, data de saída, ativos negociados, direção da posição, beta de entrada, z-score de entrada e saída, PnL bruto, PnL líquido e razão de encerramento da operação.

Também foram salvas tabelas de métricas gerais e métricas segmentadas por par, ano, setor, combinação setorial e razão de saída.

Essa etapa permitiu transformar o modelo estatístico em uma simulação econômica da estratégia, possibilitando avaliar não apenas se os pares apresentaram relação estatística, mas se essa relação poderia gerar resultado financeiro em uma estratégia de pairs trading.

---

## 4. Visão Geral dos Resultados

O backtest da estratégia de pairs trading foi executado com metodologia *walk-forward* bienal, na qual os parâmetros são estimados em janelas de dois anos (formação) e aplicados nos dois anos seguintes (trading), sem qualquer vazamento de informação futura. Ao longo de 14 anos — de 2012 a 2025 — foram realizados 1.047 trades em 7 ciclos bienais, cobrindo dezenas de pares de ações da B3 selecionados por cointegração estatística e rastreados via Filtro de Kalman adaptativo.

As métricas consolidadas do período completo são apresentadas abaixo:

| Trades | Win Rate | Sharpe | MadDD (log-spread) | Duração Média |
| ------ | -------- | ------ | ------------------ | ------------- |
| 1.047  | 53,9%    | 0,24   | -2,049             | 4,8           |

O Sharpe de 0,24 reflete uma estratégia com retorno ajustado a risco modesto no agregado. Contudo, como demonstram os gráficos a seguir, esse número oculta uma heterogeneidade temporal relevante: os ciclos de 2014 a 2019 entregaram Sharpe acima de 1,0, enquanto os ciclos mais recentes (2022–2025) apresentaram deterioração significativa, pressionando o indicador consolidado.

### 4.2 Análise dos Gráficos do Backtest

#### Gráfico 1 — PnL Acumulado Walk-Forward

![[bt_01_retorno_acumulado.png]]

Este gráfico é o painel central do backtest. O eixo vertical mede o PnL acumulado em unidades de log-spread (cada unidade equivale, grosso modo, a 100% de retorno absoluto no spread), e o eixo horizontal percorre os 14 anos de simulação. As faixas verticais alternadas (C1–C7) delimitam os sete ciclos bienais de trading.

A curva revela três fases distintas:

**2012:** queda inicial de ~0,76 unidades, reflexo de um primeiro ciclo em que os parâmetros calibrados no período 2010–2011 não se transferiram bem para o mercado de 2012, possivelmente pela mudança de regime associada ao fim do ciclo de alta de commodities.

**2013–2024:** trajetória predominantemente ascendente, com ganho acumulado de aproximadamente 5,5 unidades de log-spread. O crescimento é mais acelerado entre 2013 e 2020, período em que a estratégia capturou consistentemente a reversão à média dos spreads.

**2024–2026:** reversão da tendência e erosão de parte dos ganhos. A curva perde aproximadamente 1,5 unidade a partir do pico, sinalizando que os pares cointegrados nos ciclos recentes perderam parte da estabilidade estrutural observada anteriormente.

O painel inferior detalha o drawdown corrente em cada data. O drawdown máximo histórico foi de −2,049 log-spread, registrado no período 2025–2026. Este valor deve ser interpretado como o custo máximo de capital já sofrido pela estratégia em uma única sequência de perdas desde o último pico.

#### Gráfico 2 — Sharpe por Par Out-of-Sample

![[bt_02_sharpe_pares.png]]

O gráfico de barras horizontais classifica os pares pelo Sharpe Ratio anualizado calculado exclusivamente no período de trading (out-of-sample). A linha tracejada verde marca o limiar Sharpe = 1, considerado o mínimo aceitável para estratégias sistemáticas em gestão de recursos.

Os destaques são:

**AXIA3 × AXIA6 (Sharpe 45,87):** par com vínculos estruturais muito fortes — provavelmente classes distintas da mesma empresa ou instrumentos equivalentes — o que gerou spreads altamente estacionários e convergências rápidas.

**GRND3 × KROT11 (Sharpe 35,82) e VIVT3 × VIVT4 (Sharpe 31,94):** ambos com relações econômicas sólidas (mesmo emissor em diferentes classes), confirmando que pares ON/PN da mesma empresa são candidatos naturais de alta qualidade.

**LAME4 × RENT3, BBDC3 × IGTA3, ALSC3 × IGTA3:** pares do setor de consumo cíclico e financeiro com Sharpe acima de 20, indicando que o segmento de varejo/shoppings apresentou spreads previsíveis no período amostral.

Os demais pares do ranking, com Sharpe entre 7 e 20, também superam amplamente o limiar de referência, mostrando que uma seleção criteriosa dos pares com base em cointegração e ranking de distância é capaz de filtrar candidatos de alta qualidade.

É importante ressaltar que esses valores de Sharpe são calculados por par individualmente, sem considerar correlação entre os trades simultâneos. Na prática de portfólio, o Sharpe conjunto será menor dado que múltiplos pares podem estar abertos ao mesmo tempo.

#### Gráfico 3 — Distribuição de Retornos por Trade

![[Pasted image 20260820174726.png]]

O painel esquerdo exibe o histograma do PnL líquido de cada trade, com assimetria (Skew) de 1,60 e curtose (Kurt) de 20,62. O painel direito mostra a distribuição da duração dos trades em pregões, com média de 4,8 dias.

Interpretação das principais características:

**Assimetria positiva (Skew = 1,60):** os retornos positivos têm cauda mais longa do que os negativos, ou seja, ganhos individuais excepcionalmente grandes são mais comuns do que perdas excepcionais. Esta é uma característica favorável: a estratégia 'corre os ganhos e corta as perdas', mesmo que de forma não intencional pelo stop de divergência.

**Curtose elevada (Kurt = 20,62):** a distribuição tem caudas muito mais pesadas do que a normal. Isso significa que eventos extremos (tanto positivos quanto negativos) ocorrem com frequência bem acima do esperado por uma distribuição gaussiana. Este é um sinal de que os modelos de risco baseados em normal subestimam o risco real.

**Média do PnL = 0,0027 log-spread por trade:** valor positivo, porém muito próximo de zero. O resultado agregado decorre de um grande número de trades com ganhos modestos, compensando as perdas eventuais.

**Duração média de 4,8 pregões:** a estratégia é de curto prazo — a maioria das posições se encerra em 1 a 5 dias, o que limita a exposição ao risco de mercado mas também implica alto custo de giro (impacto de custos de corretagem e bid-ask spread).

#### Gráfico 4 — Drawdown Histórico

![[Pasted image 20260820174814.png]]

O gráfico de drawdown amplia o painel inferior do Gráfico 1, permitindo análise mais detalhada dos períodos de deterioração do capital. A área vermelha representa o afastamento percentual (em log-spread) em relação ao pico histórico mais recente.

Os principais episódios de drawdown identificados são:

**2012–2013:** primeiro drawdown relevante (~−1,0), reflexo das dificuldades do ciclo inicial de calibração e do ajuste do modelo ao regime de mercado brasileiro pós-crise de 2008.

**2015–2016:** drawdown de ~−1,0, coincidindo com o período de elevada volatilidade política e econômica (crise fiscal, impeachment), que perturbou temporariamente a relação de cointegração de vários pares.

**2018–2019:** queda abrupta para ~−1,3, associada à eleição presidencial de 2018 e aos choques de câmbio que afetaram a estrutura de correlações de setores exportadores.

**2020:** drawdown mais profundo até então (~−1,75), durante o choque do COVID-19, quando os spreads ampliaram de forma anormal e o stop de divergência foi acionado em muitos pares antes da subsequente recuperação.

**2024–2026:** o drawdown mais severo do histórico, atingindo −2,049 — o máximo da série —, sinalizando que o regime de mercado dos últimos dois anos foi particularmente adverso para a estratégia de reversão à média.

A recorrência e a profundidade crescente dos drawdowns nos ciclos mais recentes é um indicador de que os relacionamentos de cointegração identificados no treinamento estão se tornando menos estáveis no período de trading, possivelmente por conta da maior dispersão e menor liquidez de alguns pares após 2022.

#### Gráfico 5 — Performance por Ano de Trading

![[Pasted image 20260820174921.png]]

Este painel duplo permite avaliar a consistência anual da estratégia. O gráfico de barras à esquerda apresenta o PnL líquido total por ano de execução dos trades; o gráfico à direita mostra a taxa de acerto (Win Rate) correspondente.

Análise ano a ano:

**2012 (−0,76 | Win Rate 57%):** o único ano com Win Rate acima de 55% e PnL negativo. Isso revela que, embora a maioria dos trades tenha sido vencedora, as perdas dos trades perdedores foram proporcionalmente muito maiores — efeito de um payoff ratio desfavorável neste ciclo inicial.

**2013 (+0,75 | 78%):** melhor Win Rate de toda a série. O par TOYB3×TOYB4 (renomeado posteriormente) concentrou grande parte dos ganhos, beneficiado por forte convergência pós-distorção no primeiro semestre.

**2014 (+0,12 | 55%) e 2015 (+0,79 | 47%):** contraste interessante — 2014 tem taxa de acerto maior mas ganho menor, enquanto 2015 tem menos da metade de trades vencedores mas PnL quase sete vezes maior. Isso indica que os trades perdedores de 2015 eram pequenos (stop rápido) e os vencedores, mais expressivos.

**2015–2019:** série de 5 anos consecutivos com PnL positivo, os maiores ganhos anuais sendo 2015 (+0,79), 2016 (+0,80), 2019 (+0,69) e 2018 (+0,54). Este é o período áureo da estratégia, com os ciclos bienais 2014–2017 entregando Sharpe acima de 1,5.

**2020 (+0,23) e 2021 (+0,17):** ganhos reduzidos em contexto de pandemia. O choque de 2020 gerou muitos stops de divergência, e 2021 foi um ano de recuperação gradual dos spreads.

**2022 (+0,45):** recuperação relevante, puxada por pares do setor financeiro que apresentaram boa convergência no período pós-pandemia.

**2023 (−0,59 | 40%):** segundo pior ano da série, com Win Rate abaixo de 50% pela primeira vez desde 2015. Coincide com o ciclo de formação 2020–2021, em que a pandemia pode ter introduzido relações espúrias de cointegração.

**2024 (+0,07 | 57%):** recuperação marginal com Win Rate aceitável mas PnL quase nulo.

**2025 (−0,95 | 38%):** pior ano da série em termos de PnL e Win Rate. O ciclo de formação 2022–2023 parece ter capturado pares cujos spreads se tornaram não estacionários no período de trading, resultando em sequência de stops de divergência.

#### Gráfico 6 — Diagnóstico de Distribuição dos Z-Scores Kalman

![[Pasted image 20260820174955.png]]

Este gráfico avalia a qualidade estatística dos spreads gerados pelo Filtro de Kalman durante o período de trading — ou seja, o quanto os z-scores se comportam como esperado por um processo estacionário com distribuição aproximadamente normal.

**Painel esquerdo — Skewness:**

39% dos pares apresentam $|skew| > 0{,}5$, indicando assimetria relevante na série de z-scores. Para que a estratégia funcione simetricamente em posições long e short, o ideal seria que os z-scores fossem distribuídos de forma aproximadamente simétrica em torno de zero.

A média de skewness entre os pares é −0,05, praticamente nula no agregado, o que sugere que a assimetria não tem viés sistemático em uma direção específica. Pares individuais com skewness extrema (abaixo de −4 ou acima de +3) merecem atenção especial na seleção.

**Painel direito — Curtose:**

65% dos pares têm curtose > 3 (distribuição leptocúrtica, caudas pesadas). Isso confirma que os spreads, embora cointegrados, ocasionalmente sofrem distorções temporárias de grande magnitude — justamente os eventos que acionam os stops de divergência.

A curtose média de 3,41 é modestamente acima de 3 (normal), mas alguns pares apresentam curtose acima de 40, revelando comportamento extremo concentrado em eventos pontuais (resultados corporativos, crises setoriais, suspensões de negociação).

Este diagnóstico recomenda cautela na aplicação de regras de risco baseadas em distribuições normais para alocar capital entre os pares.

#### Gráfico 7 — Razões de Saída dos Trades

![[Pasted image 20260820175100.png]]

O gráfico de barras segmenta os 1.047 trades pelos três critérios de encerramento definidos nas regras da estratégia: convergência do spread para a média ($|z| \leq 0{,}5$), stop por divergência excessiva ($|z| \geq 3$) e stop por tempo (posição aberta por mais de 30 pregões).

**Distribuição observada:**

**Convergência:** 598 trades (57,1%) — saídas onde o spread retornou à média como esperado. Este grupo concentra os ganhos da estratégia.

**Stop por divergência:** 435 trades (41,5%) — saídas forçadas quando o spread continuou se afastando além do limiar de −3 desvios-padrão. Este percentual é elevado e representa o principal vetor de perdas.

**Stop por tempo:** apenas 14 trades (1,3%) — situações em que a posição foi mantida por 30 pregões sem atingir nenhum dos outros critérios de saída.

A proporção de 41,5% de stops por divergência é o dado mais preocupante deste painel. Em uma estratégia de reversão à média bem calibrada, o esperado é que a maior parte das saídas ocorra por convergência. O alto volume de stops sugere que parte dos pares selecionados apresentou comportamento de 'trending spread' no período de trading — ou seja, o spread continuou se afastando ao invés de reverter, sinalizando possível quebra da relação de cointegração. Este fenômeno é mais pronunciado nos ciclos mais recentes (2022–2025).

#### Gráfico 8 — Performance por Ciclo Bienal

![[Pasted image 20260820175155.png]]

Este gráfico decompõe os 14 anos de backtest nos sete ciclos bienais, permitindo avaliar se o regime de mercado de cada período favorece ou prejudica a estratégia. O eixo x indica o período de trading (out-of-sample), não o de formação.

| Ciclo de trading | Sharpe | Win Rate | Observação                                                                                                           |
| ---------------- | ------ | -------- | -------------------------------------------------------------------------------------------------------------------- |
| 2012-2013        | -0,007 | 63,6%    | formação 2010–2011 — ciclo inicial com pouco histórico; Sharpe quase nulo mas Win Rate elevado                       |
| 2014-2015        | 1,31   | 49,1%    | bom desempenho apesar de Win Rate abaixo de 50%, puxado pelo payoff favorável                                        |
| 2016-2017        | 1,87   | 65,0%    | melhor ciclo da série — mercado estável pósimpeachment e retomada econômica favoreceram reversão à média             |
| 2018-2019        | 1,49   | 50,0%    | ciclo positivo mesmo com igual divisão entre vencedores e perdedores, indicando payoff ratio elevado                 |
| 2020-2021        | 0,32   | 54,0%    | ciclo positivo mas reduzido — pandemia gerou muitos stops de divergência antes da recuperação dos spreads            |
| 2022-2023        | -0,13  | 44,5%    | ciclo ligeiramente negativo — Win Rate cai abaixo de 50% pela primeira vez; início da deterioração estrutural        |
| 2024-2025        | -1,64  | 46,6%    | pior ciclo da série — Sharpe fortemente negativo, com spreads divergindo consistentemente após abertura das posições |

O padrão de degradação é nítido: os quatro primeiros ciclos de trading (2012–2019) foram consistentemente positivos, enquanto os últimos dois (2022–2025) foram negativos. A Win Rate não apresenta uma tendência tão clara quanto o Sharpe, oscilando em torno de 50%, o que sugere que o problema está mais no tamanho das perdas (stops de divergência profundos) do que na proporção de trades perdedores.

### 4.3 Análise de Performance por Setor

A tabela abaixo consolida os resultados dos trades agrupados pelo setor do primeiro ativo do par, ordenados pelo PnL total. Esta análise permite identificar quais segmentos da B3 apresentaram relações de cointegração mais estáveis e lucrativas ao longo do período.

| Setor               | Trades | Win Rate | Sharpe | PnL Total |
| ------------------- | ------ | -------- | ------ | --------- |
| Comunicações        | 13     | 76,6%    | 7,79   | +0,356    |
| Financeiro          | 235    | 57,0%    | 1,15   | +1,904    |
| Bens industriais    | 126    | 54,0%    | 1,32   | +1,473    |
| Materiais Básicos   | 69     | 56,9%    | 0,91   | +0,130    |
| Consumo Não Cíclico | 11     | 45,5%    | 0,65   | +0,033    |
| Consumo Cíclico     | 433    | 51,3%    | -0,18  | -0,369    |
| Utilidade Pública   | 155    | 52,9%    | -1,19  | -0,809    |

**Destaques setoriais:**

**Comunicações:** melhor Sharpe do grupo (7,79), com Win Rate de 76,9%. O pequeno número de trades (13) concentra pares como VIVT3×VIVT4 e TIMS3×VIVT4, estruturas ON/PN ou concorrentes diretos no setor de telecomunicações, com spreads altamente previsíveis.

**Financeiro e Bens Industriais:** os dois setores com maior volume de trades e PnL absoluto positivo. O setor financeiro se beneficia da existência de pares como ITSA4×ITUB4, SANB11×SANB4 e BRSR6×SANB4, todos com vínculos holding-controlada ou concorrência direta.

**Consumo Cíclico:** com 433 trades — o maior volume —, o setor entrega PnL ligeiramente negativo (−0,369). A heterogeneidade dos pares neste setor (varejistas, construtoras, shoppings) parece resultar em cointegração mais instável.

**Utilidade Pública:** segundo pior resultado (−0,809 PnL, Sharpe −1,19). Apesar de ser um setor de negócios estáveis, a regulação tarifária periódica e os choques hídricos criam rupturas temporárias nas relações de cointegração, gerando sequências de stops.

---

## 5. Análise Crítica da Estratégia Quantitativa

Os resultados do backtest permitem avaliar tanto os méritos quanto as limitações da metodologia adotada. A análise a seguir aponta os principais pontos críticos, organizados por dimensão.

### 5.1 Instabilidade estrutural dos pares ao longo do tempo

A cointegração é uma propriedade estatística estimada em uma janela histórica, é uma invariante econômica permanente. O backtest evidencia que pares aprovados no teste ADF com p-value < 0,05 frequentemente perdem essa propriedade no ciclo seguinte — especialmente em períodos de ruptura macroeconômica (COVID-19, ciclo de juros pós-2021). A taxa de 41,5% de stops por divergência é a consequência direta dessa instabilidade. Uma abordagem mais robusta exigiria renovação contínua dos testes de integração durante o período de trading, e não apenas no início do ciclo bienal.

### 5.2 Custos de transação e liquidez

O modelo assume custo total de 0,20% (20 bps) por trade (ida e volta), sem modelar impacto de mercado ou bid-ask spread real. Para pares de menor liquidez, esse custo pode ser consideravelmente maior, o que eroderia o PnL médio de 0,27% por trade de forma substancial. Adicionalmente, o stop por divergência — que representa 41,5% das saídas — ocorre exatamente quando os spreads estão em sua máxima distância e o mercado tende a ser mais ilíquido, elevando o custo efetivo de encerramento.

### 5.3 Degradação do sinal Kalman nos ciclos recentes

O Filtro de Kalman adapta o beta dinamicamente, o que é uma vantagem sobre o OLS fixo. Contudo, em cenários de alta volatilidade ou quebra estrutural, o filtro pode convergir lentamente para o novo regime ou rastrear 'ruído' em vez de sinal. O diagnóstico do Gráfico 6 (65% dos pares com caudas pesadas) sugere que os z-scores gerados pelo Kalman não seguem a distribuição normal pressuposta pelo modelo, o que invalida parcialmente os limiares fixos de entrada ($|z| \geq 2$) e stop ($|z| \geq 3$). Limiares adaptados por volatilidade realizada ou por quantis empíricos poderiam ser mais apropriados.

### 5.4 Concentração setorial e de pares

O setor de Consumo Cíclico concentra 433 dos 1.047 trades (41%) e entrega PnL negativo (−0,369). Essa concentração, combinada com o resultado negativo do setor, distorce o resultado agregado. Uma abordagem de alocação com teto por setor ou por par evitaria essa concentração involuntária. Da mesma forma, os pares mais lucrativos (top-3 do Gráfico 2) concentram boa parte do alpha: remover esses três pares do histórico alteraria substancialmente as métricas consolidadas — sinal de alpha frágil e dependente de poucas posições.

### 5.5 Ausência de benchmark de mercado

O backtest não apresenta comparação formal com benchmarks relevantes (CDI, IBOVESPA, carteira 60/40). O retorno anualizado de +0,92% a.a. sobre o capital total parece pouco atrativo em termos absolutos, especialmente considerando que a taxa Selic brasileira ficou acima de 10% a.a. na maior parte do período. A comparação correta deveria incluir o retorno do caixa não alocado (CDI sobre 95% do capital) mais o alpha da estratégia, o que tornaria o resultado mais competitivo e a avaliação mais justa.

---

## 6. Ideias para continuação do projeto

### 6.1 Aprimoramento do backtest e aproximação com condições reais de mercado

Uma primeira continuação do projeto seria tornar o backtest mais próximo de uma operação real. Nesta versão, já foram considerados custos operacionais, regras de entrada, saída, stop por divergência e stop por tempo. Porém, em uma etapa futura, seria possível incorporar outras limitações práticas, como slippage, bid-ask spread, restrições de aluguel para venda descoberta, volume máximo negociável por ativo e impacto de mercado.

Além disso, seria interessante testar diferentes hipóteses de custo, comparando cenários conservador, intermediário e otimista. Isso permitiria avaliar se a estratégia continua viável mesmo em condições menos favoráveis de execução. Além disso, o backtest poderia ser expandido para analisar o turnover da carteira, a frequência de troca dos pares e o custo gerado por essa rotatividade.

Essa continuação ajudaria a responder se a estratégia é apenas estatisticamente promissora ou se também poderia ser operacionalmente aplicável no mercado brasileiro.

### 6.2 Testes de robustez e comparação entre metodologias

Outra possibilidade de continuação seria realizar testes de robustez para verificar se os resultados dependem muito dos parâmetros escolhidos. Por exemplo, poderiam ser testadas diferentes janelas de formação, diferentes quantidades de pares por janela, outros limites de z-score para entrada e saída, e diferentes critérios de liquidez.

Também seria relevante comparar a metodologia atual com alternativas. O projeto utilizou distância mínima como pré-filtro, cointegração como validação estatística e Filtro de Kalman para modelagem dinâmica. Em uma próxima etapa, essa abordagem poderia ser comparada com modelos que usam apenas distância mínima, apenas cointegração, OLS fixo ou diferentes configurações do Kalman.

Essa análise permitiria entender se o uso combinado de distância, cointegração e Kalman realmente melhora a qualidade dos pares e a performance da estratégia. Além disso, ajudaria a identificar quais parâmetros são mais sensíveis e quais escolhas metodológicas são mais robustas ao longo do tempo.

### 6.3 Análise aprofundada por setores, clusters e regimes de mercado

Uma terceira continuação seria aprofundar a análise dos resultados por setor, combinação setorial e regimes de mercado. Como a formação dos pares não foi restrita por setor, o projeto permite observar quais relações surgiram de forma estatística entre ativos da B3. A partir disso, seria possível investigar se pares do mesmo setor performam melhor do que pares de setores diferentes, ou se determinadas combinações setoriais apresentam maior estabilidade e potencial de reversão.

Além da análise setorial tradicional, o projeto poderia avançar para uma análise de clusters estatísticos, agrupando ativos com comportamentos semelhantes independentemente da classificação setorial oficial. Isso ajudaria a identificar relações que não aparecem apenas pela divisão de setores da B3, mas que surgem por exposição comum a fatores como commodities, juros, câmbio, ciclo econômico ou risco de mercado.

Também seria interessante separar os resultados por regimes de mercado, como períodos de crise, alta volatilidade, queda da bolsa, alta de juros ou valorização de commodities. Dessa forma, o presente projeto poderia investigar em quais contextos a estratégia de pairs trading funciona melhor e em quais momentos ela perde eficiência.
## 7. Conclusão

A estratégia de pairs trading com Filtro de Kalman demonstrou ser estatisticamente viável no mercado brasileiro entre 2014 e 2019, período em que entregou Sharpe superior a 1,0 em todos os ciclos bienais. Os pares com vínculos econômicos sólidos — ações ON/PN da mesma empresa, relações holding-controlada e concorrentes do mesmo nicho — foram os mais consistentes, confirmando que a fundamentação econômica é pré-requisito para estabilidade estatística de longo prazo (Vidyamurthy, 2004; Gatev et al., 2006).

A partir de 2022, a estratégia deteriorou: Sharpe negativo nos dois últimos ciclos, alto volume de stops por divergência (41,5%) e drawdown máximo de −2,049 log-spread em 2025–2026. Esse padrão sugere que o regime de mercado recente — marcado por aperto monetário global, instabilidade fiscal e maior dispersão setorial — comprometeu a estacionariedade dos spreads identificados nos ciclos de formação anteriores.

Para uso prático, a estratégia exige aprimoramentos: renovação contínua dos testes de cointegração durante o trading, limiares de entrada adaptados por volatilidade realizada, teto de concentração por setor e dimensionamento de risco por CVaR histórico. Incorporada como componente descorrelacionado em um portfólio diversificado — e não como estratégia isolada —, ela mantém potencial de adicionar valor ajustado a risco, desde que a seleção de pares seja continuamente revista conforme o regime de mercado evolui.

---

## 8. Referências Bibliográficas

ALEXANDER, C. Optimal hedging using cointegration. *Philosophical Transactions of the Royal Society of London A*, v. 357, n. 1758, p. 2039–2058, 1999.

DICKEY, D. A.; FULLER, W. A. Distribution of the estimators for autoregressive time series with a unit root. *Journal of the American Statistical Association*, v. 74, n. 366a, p. 427–431, 1979.

ENGLE, R. F.; GRANGER, C. W. J. Co-integration and error correction: representation, estimation, and testing. *Econometrica*, v. 55, n. 2, p. 251–276, 1987.

GATEV, E.; GOETZMANN, W. N.; ROUWENHORST, K. G. Pairs trading: performance of a relative-value arbitrage rule. *Review of Financial Studies*, v. 19, n. 3, p. 797–827, 2006.

HAMILTON, J. D. *Time Series Analysis*. Princeton: Princeton University Press, 1994.

KALMAN, R. E. A new approach to linear filtering and prediction problems. *Journal of Basic Engineering*, v. 82, n. 1, p. 35–45, 1960.

POLE, A. *Statistical Arbitrage: Algorithmic Trading Insights and Techniques*. Hoboken: Wiley, 2007.

VIDYAMURTHY, G. *Pairs Trading: Quantitative Methods and Analysis*. Hoboken: Wiley, 2004.








