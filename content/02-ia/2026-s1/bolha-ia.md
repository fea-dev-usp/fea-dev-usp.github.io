---
title: AI Boom vs Bolha Dot-com
tags:
  - nivel/intermediario
  - trilha/ia
---
_**Autores:** Guilherme Matos · Jonathan Pereira · Marco Antonio_

**_Repositório:_** [link](https://github.com/GuilhermeMP-prog/Dev.ensinaG4)

# Resumo

Este estudo investiga se a atual onda de valorização associada à inteligência artificial (IA) apresenta características de integração sistêmica distintas daquelas observadas durante a bolha das empresas de tecnologia no início dos anos 2000. Para isso, compara-se o comportamento da NVIDIA (NVDA) no período 2021–2025 com o da Cisco Systems (CSCO) entre 1999–2001, utilizando métodos não paramétricos, análise de causalidade temporal e decomposição fatorial. Inicialmente, testes de permutação de Monte Carlo avaliam a significância das correlações entre empresas ligadas à IA e setores fundamentais da economia real, filtrando relações espúrias. Em seguida, testes de causalidade de Granger investigam precedência temporal entre retornos de empresas tecnológicas e ETFs setoriais. Métricas de risco extremo, como Value at Risk (VaR) e Conditional Value at Risk (CVaR), quantificam a severidade das caudas negativas, enquanto correlações móveis permitem observar a evolução temporal do co-movimento entre tecnologia e setores produtivos. Por fim, a Análise de Componentes Principais (PCA) identifica fatores comuns de risco e a contribuição relativa de cada setor para a variância sistêmica. Os resultados indicam que empresas associadas à IA apresentam correlações estatisticamente significativas e persistentes com múltiplos setores da economia, além de evidências de precedência temporal em relação a segmentos industriais e de consumo. Em contraste, a Cisco exibiu padrões de correlação mais instáveis e menor integração com a base produtiva durante o período da bolha dot-com. A PCA reforça essa distinção ao mostrar maior participação de setores reais, como energia e indústria, no principal fator comum contemporâneo. Em conjunto, as evidências são consistentes com a hipótese de que a IA está mais integrada à estrutura econômica do que o ciclo tecnológico anterior.

# 1. Introdução

O mercado financeiro norte-americano experienciou, nas últimas três décadas, duas ondas tecnológicas de magnitude transformadora, a revolução da internet no final dos anos 1990 e a emergência da inteligência artificial generativa a partir de 2022. Esta pesquisa propõe uma análise histórico-comparativa entre os dois períodos, utilizando a Cisco Systems (CSCO) como proxy representativo da bolha dot-com (1999-2000) e a NVIDIA Corporation (NVDA) como proxy do atual ciclo de inteligência artificial (2021-2025), investigando se a IA contemporânea tem se comportado como um possível driver sistêmico do mercado.

## 1.1  Contexto Macro: A Dimensão Energética e o Debate Acadêmico

Diferente da revolução da internet, que se manifestou primordialmente em camadas de software e serviços, o ciclo atual da IA impõe uma demanda sem intensa sobre a infraestrutura física. Algumas projeções recentes sugerem crescimento substancial do consumo de energia associado à expansão da IA, refletindo uma transição que ancora na valorização tecnológica em ativos de energia e hardware. Este cenário intensifica o debate acadêmico sobre a natureza do crescimento atual. Alinhado à tese de Shiller, R. J. (2000), críticos argumentam que o mercado exibe sinais de uma bolha especulativa clássica.

O caso da Cisco Systems oferece um precedente historicamente relevante, pois após atingir o ápice em 2000, a empresa enfrentou uma desvalorização de 78%, evidenciando o risco de projeções de crescimento que superam a capacidade de absorção econômica real. Em contrapartida, economistas como Acemoglu, D. (2025) oferecem uma visão mais matizada. Embora cético quanto à magnitude imediata dos ganhos de produtividade, estimando que apenas uma fração das tarefas humanas será efetivamente automatizada na próxima década, o debate gira em torno de se a IA representa uma "tecnologia de propósito geral" que, apesar do hype, está construindo a infraestrutura essencial para o próximo século, de forma diferente do isolamento setorial das dot-com.

## 1.2 Pergunta Central e Hipótese de Trabalho

A análise setorial do período 2021-2025 sugere um padrão de transmissão fundamentalmente distinto do observado na bolha dot-com. Enquanto o setor de tecnologia (XLK) lidera a valorização, observa-se uma correlação positiva substancial com setores tradicionalmente não-tecnológicos, como Indústria (XLI) e Consumo Discricionário (XLY). Esta aparente diferença estrutural motiva a questão central desta pesquisa: a inteligência artificial representa um driver sistêmico genuíno do mercado contemporâneo, ou constitui um fenômeno setorialmente isolado com potencial de reversão análogo ao precedente histórico?

![[Pasted image 20260203212139.png]]

## 1.3 Dinâmica Intrasetorial

A distinção entre os dois ciclos se torna ainda mais evidente na análise da dinâmica corporativa. A partir de 1995, a Cisco Systems emerge como símbolo máximo da revolução da internet, com trajetória de preço altamente concentrada em um único pico especulativo entre 1999 e 2000, em forte contraste com o comportamento bem mais contido de Microsoft e Oracle no mesmo período. Esse padrão ajuda a caracterizar a bolha das dot-com como fenômeno centrado em um campeão setorial isolado, cuja valorização extrema não se propagou de forma homogênea para o restante do ecossistema corporativo.

![[Pasted image 20260203212223.png]]

A comparação entre CSCO no auge da bolha das dot com e o ecossistema atual de empresas ligadas à inteligência artificial revela uma mudança qualitativa na forma como inovações tecnológicas se refletem nos preços de ativos. No final da década de 1990, a Cisco concentrou sozinha a narrativa de “espinha dorsal da internet”, acumulando valorização mais de quarenta vezes superior ao ponto de partida entre 1995 e o pico de março de 2000, enquanto o S&P 500 avançava de forma muito mais moderada no mesmo intervalo. Esse descolamento extremo entre a trajetória da empresa e o índice sugere um episódio de exuberância específica, em que o mercado atribuía a uma única ação um papel quase exclusivo de representante do futuro digital, sem difusão proporcional dos ganhos para o restante do mercado.

![[Pasted image 20260203212257.png]]


No ciclo atual de inteligência artificial, a dinâmica é mais distribuída: embora a trajetória da NVIDIA seja explosiva, com múltiplas ondas de valorização entre 2023 e 2025, outras empresas do ecossistema de IA, como Broadcom (AVGO), Palantir (PLTR), Microsoft (MSFT), Oracle (ORCL) e IBM, também exibem tendências de alta consistentes, ainda que em magnitudes distintas. A trajetória acumulada de retorno entre 2021 e 2026 mostra que a NVDA se destaca como líder absoluta em valorização, mas a alta não é isolada. Ações como AVGO e PLTR também exibem múltiplos de preço muito acima do S&P 500, enquanto AAPL, MSFT, ORCL e IBM apresentam desempenho superior ao índice em diferentes graus. Em vez de um único “superativo” desconectado, observa-se um sistema de empresas interconectadas por relações de fornecimento de hardware, software, serviços em nuvem e investimentos cruzados, como sintetizado no diagrama de fluxos de capital entre NVIDIA, OpenAI, Microsoft e demais players do ecossistema.

![[Pasted image 20260203212314.png]]

Esse contraste micro entre o papel isolado de CSCO na bolha da internet e o papel nodal, porém não exclusivo, de NVDA no ciclo de IA é central para a hipótese deste trabalho. A inteligência artificial pode não se limitar a um episódio de valorização concentrada em um único ativo, como observado com a Cisco, mas ser um sistema de empresas interdependentes com potencial de atuar como driver mais amplo do mercado, ao invés de um episódio puramente setorial e concentrado.

## 1.4 O Precedente Histórico: A Bolha das Dot-Com (1997-2000)

![[Pasted image 20260203212405.png]]

A análise do S&P 500 entre 1970 e 2025 revela que o período 1997-2000 representa uma anomalia histórica de magnitude comparável apenas à crise de 2008 e à pandemia de 2020 em termos de volatilidade e deslocamento de preços. A análise setorial do período (1999-2007) demonstra que o setor de tecnologia apresentou um comportamento dramaticamente desacoplado dos demais setores da economia, sugerindo que a valorização tecnológica constituía um fenômeno predominantemente especulativo, com limitada transmissão para os fundamentos econômicos reais.

![[Pasted image 20260203212419.png]]

![[Pasted image 20260203212425.png]]


## 1.5 O Ciclo Atual: Inteligência Artificial Generativa (2022-2025)

![[Pasted image 20260203212514.png]]

O lançamento do ChatGPT em novembro de 2022 inaugurou um novo ciclo de valorização tecnológica centrado em empresas de inteligência artificial, com a NVIDIA Corporation assumindo uma posição análoga à ocupada pela Cisco duas décadas antes.

![[Pasted image 20260203212523.png]]


Entre janeiro de 2023 e janeiro de 2025, a NVDA valorizou aproximadamente 800%, atingindo uma capitalização de mercado superior a US$ 3 trilhões. Contudo, a integração da narrativa de IA aos fundamentos econômicos amplos sugere que estamos diante de um fenômeno de integração sistêmica, o que fundamenta a necessidade de investigar os canais de transmissão de risco propostos nesta pesquisa.

![[Pasted image 20260203212531.png]]


# Metodologia

A investigação empírica é estruturada em torno de uma análise comparativa de séries temporais, com o objetivo de identificar, quantificar e interpretar a natureza da interconexão dinâmica e do risco sistêmico em dois regimes tecnológicos distintos, a bolha dot-com do final dos anos 1990 e o ciclo contemporâneo associado à infraestrutura de inteligência artificial.

Foram utilizados retornos diários de preços de fechamento ajustados de dez ativos representativos, coletados automaticamente por meio da API do Yahoo Finance (biblioteca _yfinance_). O painel contemporâneo cobre o período de 2021 a 2025 e inclui cinco líderes do ecossistema de inteligência artificial, NVIDIA (semicondutores), Microsoft e Apple (plataformas), Palantir (analytics e software corporativo) e Broadcom (infraestrutura de chips), confrontados com cinco ETFs setoriais amplamente utilizados como proxies da economia real, financeiro (XLF), industrial (XLI), energia (XLE), consumo discricionário (XLY) e saúde (XLV).

Para fins de contraste histórico, replica-se a mesma estrutura metodológica no período crítico da bolha dot-com (1999–2001), utilizando Cisco Systems e Microsoft como proxies tecnológicos daquele regime, em conjunto com os mesmos ETFs setoriais disponíveis a partir de 1998. Os retornos são calculados como variações percentuais diárias, o que incorpora ajustes para dividendos e splits, assegurando comparabilidade temporal e consistência estatística entre os períodos analisados.

## Teste de Significância de Correlação: Permutação Monte Carlo

A validação estatística das correlações observadas baseia-se em testes de permutação Monte Carlo, executados com 10.000 reamostragens independentes para cada par de ativos. Sob a hipótese nula de ausência de relação estatística, a permutação aleatória de uma das séries temporais preserva sua distribuição marginal, mas destrói qualquer dependência temporal ou contemporânea entre os ativos.

A estatística de teste é definida como a fração das simulações que produzem uma correlação absoluta maior ou igual à observada empiricamente, resultando em um _p-valor_ empírico não- paramétrico. Essa abordagem reduz a dependência de pressupostos paramétricos fortes, linearidade ou homocedasticidade, frequentemente violados em séries financeiras de alta frequência. Os resultados são sintetizados por meio de matrizes de significância visualizadas em _heatmaps_ bicolores, nos quais apenas correlações estatisticamente significativas são destacadas, filtrando co-movimentos induzidos por ruído aleatório. Como validação externa, a análise de permutação é estendida à relação entre NVIDIA e Bitcoin (proxy de risco especulativo global), bem como ao Ibovespa (proxy de mercados emergentes). A significância estatística observada nesses pares reforça a interpretação da inteligência artificial como fator de risco transversal, conectando tecnologia, criptoativos e mercados periféricos.

## Causalidade Dinâmica: Teste de Granger Bidirecional

Antes de qualquer inferência causal, todas as séries temporais são submetidas ao teste Augmented Dickey-Fuller (ADF), rejeitando-se, de forma consistente, a hipótese de raiz unitária. A estacionariedade das séries é condição necessária para a validade do teste de causalidade de Granger, mitigando o risco de pseudocausalidades espúrias.

A análise aplica testes de causalidade de Granger bidirecionais com cinco defasagens, correspondentes aproximadamente a uma semana de negociação. Para maior robustez, emprega-se dupla validação estatística: (i) o teste F sequencial tradicional e (ii) o teste de razão de verossimilhança em modelos autorregressivos vetoriais (VAR). A evidência de causalidade é classificada de forma graduada, distinguindo independência, causalidade unidirecional e causalidade provável, conforme a consistência entre os métodos.

## Risco Extremo e Dinâmica de Cauda

A severidade do risco de cauda é quantificada por métricas atuariais não paramétricas amplamente consolidadas na literatura financeira. O Value at Risk a 95% (VaR 95%) identifica o limiar dos 5% piores retornos diários, enquanto o Conditional Value at Risk (CVaR 95% ou _Expected Shortfall_) mensura a perda média condicional além desse limiar, oferecendo uma medida mais informativa da exposição ao downside extremo.

Para o período da bolha dot-com, as estimativas de CVaR da Cisco são obtidas por meio de bootstrap histórico com 1.000 reamostragens, permitindo a construção de intervalos de confiança empíricos e a avaliação explícita da incerteza associada às perdas extremas. Essa abordagem é particularmente adequada para amostras finitas e distribuições assimétricas.

## Estrutura Fatorial: Análise de Componentes Principais (PCA)

Por fim, utiliza-se a Análise de Componentes Principais (PCA) para decompor a matriz de covariância dos retornos padronizados (média zero e variância unitária), identificando fatores latentes comuns ordenados por variância explicada. O primeiro componente principal (PC1) é interpretado como o fator de risco sistêmico dominante do conjunto analisado, enquanto os _loadings_ refletem a contribuição relativa de cada ativo para esse fator. _Scree plots_ ilustram a hierarquia dos componentes, e gráficos de _loadings_ diferenciam ativos de IA e setores tradicionais, permitindo a identificação clara dos vetores sistêmicos.

## Discussão

### 1. Valuation

![[Pasted image 20260203212728.png]]

A análise cross-sectional dos 50 maiores componentes do S&P 500 reforça essa leitura de que o ciclo atual é menos isolado e mais integrado ao tecido corporativo. No gráfico de retorno acumulado desde 2021 versus lucro por ação (EPS), empresas do ecossistema de IA, especialmente NVDA, AVGO e PLTR, situam-se na região superior da distribuição, combinando múltiplos de valorização muito acima da mediana do índice com níveis de lucro que, embora não expliquem sozinhos o movimento de preço, não são negligenciáveis. Ao destacar essas empresas em relação às demais, observa-se que a “fronteira de performance” do S&P 500 no período recente é dominada por nomes ligados direta ou indiretamente à IA, ao passo que companhias tradicionais com EPS elevado, como bancos e industriais maduros, apresentam retornos acumulados bem mais modestos. Em conjunto, esses resultados sugerem que, ao contrário da trajetória altamente concentrada da Cisco em 2000, a inteligência artificial hoje atua como vetor de reprecificação transversal dentro do índice, redefinindo tanto a hierarquia de desempenho entre os blue chips quanto a forma como o mercado remunera crescimento esperado versus resultados correntes.

![[Pasted image 20260203212819.png]]

Os gráficos de valuation ajudam a comparar a bolha da internet e o ciclo atual de IA, pois permitem separar exagero de preço de geração efetiva de lucros. A primeira evidência é que, embora o mercado pague múltiplos elevados por várias empresas associadas à inteligência artificial, a situação não é homogênea, pois o ranking de P/E mostra um grupo restrito com prêmios extremos, liderado por Palantir, Tesla e algumas fabricantes de chips, enquanto a maioria das blue chips, inclusive parte relevante do setor de tecnologia, é negociada em faixas bem mais moderadas, próximas ou levemente acima da média histórica do S&P 500 indicada pela linha pontilhada verde. Os múltiplos mais elevados parecem concentrar-se em empresas diversas, em vez de caracterizar um regime de euforia generalizada como em 1999 e 2000.

![[Pasted image 20260203212834.png]]

A decomposição entre “realidade” (lucro absoluto) e “risco” (P/E) torna essa distinção ainda mais clara. Em março de 2000, a Cisco gerava aproximadamente 2,7 bilhões de dólares em lucro anual e era negociada a cerca de 205 vezes esse resultado, múltiplo tipicamente associado a períodos de bolha. Ao contrastar esse nível com a Nvidia atual, observa-se um salto de ordem de magnitude na geração de caixa, algo próximo de 100 bilhões de dólares anuais, acompanhado de um múltiplo de lucro significativamente menor que o da Cisco em 2000, ainda elevado, mas compatível com uma empresa que combina crescimento acelerado com lucratividade excepcional. A situação de Palantir é o oposto, lucro ainda modesto e múltiplo acima da faixa de 400 vezes, superiores aos múltiplos observados para a Cisco no auge de 2000, o que indica alta sensibilidade a revisões de expectativa. Em síntese, enquanto a liderança de CSCO na virada do milênio se apoiava em lucro relativamente pequeno sustentando valuation extremado, o ciclo de IA é dual, há um núcleo de empresas com lucros robustos que justificam parte relevante do prêmio de preço, e uma periferia especulativa em que a precificação se aproxima, ou mesmo supera, os níveis de bolha observados no passado.

![[Pasted image 20260203212844.png]]

A análise conjunta de retorno recente, volatilidade implícita e posição relativa de puts e calls oferece evidência importante sobre a forma como o mercado precifica o risco no ecossistema de IA. No plano Performance × Sentimento, o eixo horizontal captura o put/call ratio agregado de cada ativo, medida de aversão ao risco, em que valores mais altos indicam maior demanda por proteção via opções de venda, enquanto o eixo vertical reporta o retorno em 90 dias, aproximando o investidor marginal que operou o rally recente. O tamanho das bolhas reflete a volatilidade implícita (IV) e a coloração sintetiza o “medo” embutido nas opções, tons mais quentes associam-se a IV mais elevada, logo maior prêmio exigido pelo mercado para carregar risco direcional.

A configuração atual revela um ecossistema claramente segmentado entre ativos com menor demanda relativa por proteção e ativos com maior prêmio de risco implícito. Microsoft e Apple combinam retornos em 90 dias modestos ou ligeiramente positivos com put/call ratio inferior a 0,75 e volatilidade implícita na faixa de 30%,40%, sugerindo postura relativamente confortável dos investidores em relação a estas big techs consolidadas. Em contraste, Palantir, Broadcom e Nvidia ocupam quadrante de alto retorno recente e put/call ratio próximo ou acima de 0,90, com volatilidade implícita entre 67% e 94%, sinalizando assimetria de risco percebida, o mercado atribui simultaneamente expectativas de crescimento elevadas e maior incerteza quanto à distribuição de retornos. Palantir, em particular, combina forte performance recente com o maior nível de IV da amostra (acima de 90%), coerente com os múltiplos de P/E extremamente elevados identificados na seção anterior e reforçando a leitura de que parte do ciclo de IA ocorre em terreno especulativo.


Do ponto de vista integrado, o conjunto dessas evidências sugere que a inteligência artificial opera hoje como um fator de risco com duas camadas. Na camada de base, grandes plataformas como Microsoft e Apple absorvem a narrativa de IA com volatilidade relativamente controlada, funcionando quase como “carregadores narrativos” do tema dentro do S&P 500. Na camada superior, nomes como Nvidia, Palantir e Broadcom concentram tanto a convexidade de retorno quanto o risco de cauda, com estruturas de opções que indicam disposição do mercado em pagar caro por proteção, ao mesmo tempo em que mantém posições compradas expressivas. Essa assimetria entre núcleo estável e periferia altamente opcional reforça que a IA já atua como driver relevante do mercado como um todo, mas o faz através de um mix de fundamentos sólidos em algumas empresas e de precificação extremamente sensível a revisões de expectativa em outras, o que torna crucial incorporar métricas de volatilidade implícita e de sentimento às análises puramente baseadas em preço e lucro.

Os dados confirmam que o ecossistema de IA se organiza em dois blocos distintos. PLTR e AVGO exibem os maiores retornos em 90 dias, em torno de 21% e 22%, combinados a put/call ratio muito elevado (PLTR 0.96; AVGO 1.03), o que indica forte demanda simultânea por exposição direcional e por proteção, típica de ativos percebidos como oportunidades de crescimento com risco de cauda relevante. NVDA apresenta retorno positivo mais moderado (8,6%), mas ainda com put/call ratio elevado (0.87) e volatilidade implícita muito alta (0.77), reforçando seu papel como principal “veículo narrativo” do tema IA. ORCL se destaca pelo contraste, retorno negativo de -15,6% com put/call ratio alto (0.94) e IV intermediária (0.55), configurando um caso mais clássico de narrativa pressionada, em que o mercado aumenta proteção após uma fase de underperformance.

No outro extremo, AAPL e MSFT compõem o núcleo defensivo do grupo. Ambas apresentam put/call ratios bem abaixo de 0.70, sinalizando menor apetite por hedge, com volatilidades implícitas contidas (0.40 e 0.31, respectivamente) e trajetórias de preço coerentes com blue chips consolidadas; mesmo quando o retorno em 90 dias é levemente negativo, como no caso de MSFT (-3,2%), o mercado não reage com o mesmo nível de “medo” observado em nomes mais especulativos. IBM ocupa posição intermediária curiosa, tem o maior retorno em 90 dias de toda a amostra (26,5%) com put/call ratio relativamente baixo (0.83) e IV moderada (0.42), sugerindo reprecificação positiva ainda não acompanhada por forte procura por proteção, possivelmente por ser percebida como case de IA mais tardio e menos binário do que NVDA ou PLTR. Essa assimetria entre núcleo estável (MSFT, AAPL, IBM) e periferia altamente opcional (PLTR, AVGO, NVDA), agora explícita também em termos de open interest, com NVDA concentrando, isoladamente, mais contratos em aberto do que qualquer outro nome da amostra, reforça a leitura de que a IA funciona hoje como um fator de risco em duas camadas, uma base sistêmica relativamente ancorada em lucros e outra, altamente alavancada via derivativos, que concentra a principal parte do risco de correção abrupta.

### 2. Permutação

O código implementado fornece uma validação das relações entre ativos de inteligência artificial e o benchmark de mercado. A matriz de correlação revela relações positivas e substanciais entre todos os ativos analisados e o S&P 500, com coeficientes variando entre 0,45 (IBM) e 0,71 (MSFT), indicando influência ao índice. A matriz adjacente de significância confirma que todas essas correlações são estatisticamente diferentes de zero com p-valores inferiores a 0,001, rejeitando a hipótese nula de independência para toda a amostra.

### 2.1 Análise Intrasetorial

![[Pasted image 20260203212936.png]]

O teste de permutação eleva a análise a um nível de robustez superior, simulando 10.000 distribuições nulas via embaralhamento dos retornos do SP&500 e calculando a proporção de correlações simuladas que excedem, em valor absoluto, a correlação observada na realidade. Essa análise é particularmente relevante no contexto histórico da comparação com a bolha dot-com. Se Cisco operava em regime de correlação isolada com o mercado durante 1999 e 2000, o padrão atual de comovimento significativo e robusto entre múltiplos ativos de IA e SP&500 sugere transmissão sistêmica mais ampla do que no ciclo anterior. O código permite escalabilidade para qualquer conjunto de ativos e fornecendo evidência visual para comunicação científica. A ausência de qualquer ativo com p-valor superior a 0,001 no método é consistente com a hipótese de que ativos ligados à IA exercem papel relevante na dinâmica recente do mercado, integrando-se ao tecido do mercado de forma mais orgânica e estatisticamente verificável do que seu predecessor (CSCO) das décadas passadas.

O teste de permutação oferece explicação visual intuitiva sobre a significância das correlações observadas. Para cada par ativo-SPY, simulam-se 10.000 "mundos sem relação" embaralhando completamente os retornos do benchmark e recalculando correlações com o ativo analisado. Os histogramas cinza representam essa distribuição nula empírica, em 99,9% dos casos, correlações ficam confinadas entre -0,4 e +0,4. A linha vermelha (correlação real) localiza-se consistentemente na cauda extrema direita, para NVDA (r=+0,67), MSFT (r=+0,71), AAPL (r=+0,68) e PLTR (r=+0,53), indicando que tais níveis de sincronização seriam altamente improváveis sob a hipótese de independência.

![[Pasted image 20260203213023.png]]


Os resultados de correlação via permutação entre NVDA e ativos não americanos acrescentam uma dimensão importante de contágio global à tese. A relação estatisticamente significativa com o Bitcoin(r≈0,19; p≈0,0000) indica que choques em ativos de “hipercrescimento” e alta convexidade retornam um componente comum de apetite ao risco, pois quando o mercado global abraça narrativas de inovação extrema, tanto NVDA quanto BTC tendem a se mover na mesma direção, ainda que com intensidade distinta. Embora a magnitude da correlação seja moderada, o fato de a estatística permanecer na cauda extrema da distribuição nula reforça que não se trata de ruído, mas de um canal de sentimento especulativo compartilhado que conecta infraestrutura de IA e criptoativos.

A correlação, também significativa, com o Ibovespa (r≈0,14; p≈0,0000) revela que o ciclo de IA nos Estados Unidos já transborda para mercados emergentes, inclusive o brasileiro, ainda que de forma mais amortecida. NVDA pode funcionar como proxy global de “risco tecnológico” e de expectativas quanto à produtividade futura, de modo que choques positivos na ação tendem a coincidir com janelas de fortalecimento do índice brasileiro, seja por melhora no humor global, seja por fluxo de capitais buscando beta em bolsas estrangeiras. A combinação de correlações moderadas, porém estatisticamente robustas com Bitcoin e Ibovespa, consolida o argumento de que a IA não é apenas um fenômeno setorial americano, ela passou a integrar o fator de risco global que liga ativos de fronteira tecnológica, criptoativos e mercados emergentes em um mesmo regime de apetite ou aversão ao risco.

### 3. Matriz de Veracidade & Correlações

A matriz de veracidade integra correlações observadas entre as principais empresas de IA e ossete setores fundamentais da economia real, representados por ETFs, filtrando relações estatisticamente significativas via teste de permutação Monte Carlo com 10.000 simulações por par. Células verdes codificam correlações positivas robustas, enquanto células brancas sinalizam ruído estatístico.

![[Pasted image 20260203213116.png]]


As matrizes reportam as correlações contemporâneas entre empresas líderes de IA e setores fundamentais da economia real, bem como seus equivalentes durante a bolha dot-com. Observa-se que, no período atual, os ativos de IA exibem correlações moderadas e estatisticamente significativas com os setores Industrial e de Consumo, sugerindo integração funcional com cadeias produtivas e demanda final. Em contraste, os vínculos com Energia, Materiais e Utilities permanecem limitados.

![[Pasted image 20260203213137.png]]


No episódio dot-com, embora Cisco e Microsoft apresentassem correlações comparáveis com setores tradicionais, destaca-se a ausência quase total de co-movimento com Energia, evidenciando a natureza predominantemente financeira e especulativa daquele ciclo. Assim, embora os níveis médios de correlação não diferenciem drasticamente os dois regimes, a distribuição setorial das relações sugere que a atual onda de IA se insere de forma mais orgânica na economia real, hipótese que será aprofundada por meio de análises dinâmicas de correlação móvel e causalidade temporal.

O método da correlação móvel filtra ruído de curto prazo enquanto captura evolução temporal, oferecendo evidência sequencial de que IA opera como uma infraestrutura.

![[Pasted image 20260203213147.png]]


A Broadcom apresenta correlações móveis persistentemente positivas com os setores industrial (XLI), consumo discricionário (XLY) e financeiro (XLF), frequentemente situadas entre 0,5 e 0,8, com longos períodos de significância estatística. Esse padrão sugere que o desempenho da AVGO está fortemente sincronizado com segmentos ligados à atividade produtiva e à intermediação financeira, coerente com seu papel como fornecedora de semicondutores e infraestrutura crítica.

Em contraste, a correlação com o setor de energia (XLE) permanece mais volátil e de menor magnitude, alternando entre significância e não significância ao longo do tempo. Esse resultado indica que, embora a AVGO participe do ecossistema de hardware essencial à expansão tecnológica, sua transmissão de choques para a base energética da economia ocorre de forma indireta e não estrutural. A NVIDIA exibe o padrão mais robusto e abrangente de integração setorial. As correlações móveis com os setores industrial e de consumo atingem patamares elevados e persistentes, frequentemente entre 0,7 e 0,9, permanecendo estatisticamente significativas durante grande parte do período analisado. Esse comportamento indica forte co-movimento entre o valor de mercado da NVDA e ao ciclo econômico, indo além de um fenômeno restrito ao setor de tecnologia.

A relação com o setor financeiro também se mostra relevante, ainda que mais cíclica, refletindo possivelmente o canal de expectativas, financiamento e reprecificação de risco associado à expansão da IA. Já o setor de energia apresenta correlação positiva, porém mais instável, com períodos prolongados próximos de zero ou estatisticamente não significativos, indicando que a conexão entre NVDA e energia, embora existente, não se manifesta como um vínculo linear contínuo ao longo do tempo. A Palantir apresenta um padrão distinto, caracterizado por correlações moderadas e intermitentes. As relações com indústria e consumo são positivas, porém menos intensas e menos persistentes do que as observadas para NVDA e AVGO. Em contrapartida, a correlação com energia exibe picos episódicos, sugerindo que a integração da PLTR com setores físicos ocorre de maneira mais contingente, possivelmente associada a contratos específicos, ciclos governamentais ou eventos exógenos.

Em conjunto, os resultados da correlação móvel indicam que os ativos de IA não operam de forma homogênea como vetores de risco sistêmico. Enquanto a NVIDIA apresenta um padrão de integração amplo e persistente com múltiplos setores da economia real, compatível com uma infraestrutura tecnológica central, a Broadcom ocupa uma posição intermediária, e a Palantir manifesta conexões mais episódicas e seletivas.

![[Pasted image 20260203213207.png]]


A Cisco apresenta correlação positiva relevante com o setor industrial, com média de aproximadamente 0,37 e significância em cerca de 63% das janelas. Contudo, o comportamento é oscilatório, alternando períodos de forte sincronização com quedas abruptas para níveis próximos de zero ou mesmo negativos. Essa instabilidade indica que o comovimento não se sustentava como um vínculo estrutural contínuo, mas sim como fases de entusiasmo cíclico associadas ao pico do investimento em tecnologia de rede.

Nos setores de consumo discricionário e financeiro, as correlações médias (≈0,35 e ≈0,34, respectivamente) sugerem algum grau de associação, porém a persistência estatística é limitada (56% e 47% das janelas significativas). Após o pico da bolha em março de 2000 (linha vertical), observa- se uma quebra clara na estrutura de comovimento, com as correlações se aproximando de zero e perdendo significância durante grande parte do período de ajuste. Esse comportamento é compatível com um ativo cuja valorização estava ligada a um ciclo específico de expectativas tecnológicas, mas que não permaneceu acoplado de forma estável ao ciclo econômico amplo quando o regime de mercado se deteriorou. O caso mais emblemático é o setor de energia. A correlação média entre CSCO e XLE é praticamente nula (≈0,03) e estatisticamente significativa em poucas janelas. A série oscila ao redor de zero durante praticamente todo o período, indicando ausência de integração sistemática entre a dinâmica da Cisco e um setor físico fundamental da economia. Esse resultado reforça a interpretação de que, mesmo no auge da bolha, a Cisco operava predominantemente como um ativo de tecnologia e telecomunicações, sem transmissão consistente de choques para setores ligados à infraestrutura material.

### 4. Causalidade Dinâmica: Teste de Granger Bidirecional

Correlação não implica causalidade, essa é uma das afirmações mais importantes da estatística. As correlações calculadas deram uma primeira amostra do potencial de influência, porém ao utilizar o Teste de Causalidade de Granger, o teste permite avaliar relações de precedência temporal.

#### Tabela 1 - Teste de Estacionariedade (ADF)

| **_Série_** | **_ADF Statistic_** | **_p-value_** | **_Ordem de Integração_** |
| ----------- | ------------------- | ------------- | ------------------------- |
| _NVDA_      | _-12.27_            | _0.000_       | _I(0)_                    |
| _XLE_       | _-21.83_            | _0.000_       | _I(0)_                    |
| _XLF_       | _-14.22_            | _0.000_       | _I(0)_                    |
| _XLI_       | _-13.11_            | _0.000_       | _I(0)_                    |

_Todas as séries rejeitam a hipótese nula de raiz unitária ao nível de 1%._

####  Tabela 2 - Teste de Causalidade de Granger

| **_Direção_** | **_Método 1 (GC) p-val_** | **_Método 2 (VAR-LR)_**<br><br>**_p-val_** | **_Evidência_** |
| ------------- | ------------------------- | ------------------------------------------ | --------------- |
| _NVDA → XLF_  | _0.192_                   | _1.000_                                    | _Não_           |
| _XLF → NVDA_  | _0.452_                   | _1.000_                                    | _Não_           |
| _NVDA → XLI_  | _0.040_                   | _1.000_                                    | _Parcial_       |
| _XLI → NVDA_  | _0.334_                   | _1.000_                                    | _Não_           |
| _NVDA → XLE_  | _0.011_                   | _1.000_                                    | _Parcial_       |
| _XLE → NVDA_  | _0.200_                   | _1.000_                                    | _Não_           |

O teste de causalidade de Granger bidirecional, 5 defasagens diárias, validado por meio do teste F tradicional de Granger e do teste de Razão de Verossimilhança em um modelo VAR, constitui o núcleo econométrico da análise, permitindo identificar mecanismos de precedência temporal entre a NVDA e os principais ETFs setoriais. Antes da estimação, todas as séries foram submetidas ao teste Augmented Dickey–Fuller, rejeitando fortemente a hipótese nula de raiz unitária, estatísticas ADF entre −12 e −21; p < 0,001 para todas as variáveis, confirmando estacionariedade em nível e assegurando a validade econométrica do procedimento de Granger.

A análise preliminar de correlação contemporânea indicou apenas comovimento fraco entre NVDA e os setores (ρ = 0,21 para Energia; ρ = 0,44 para Industrial; ρ = 0,27 para Financeiro), sugerindo que relações estáticas não capturam adequadamente a estrutura dinâmica dos dados. Os resultados do teste de Granger apontam evidência parcial de causalidade unidirecional da NVDA para os setores Industrial (p = 0,040, teste F) e Energia (p = 0,011, teste F). Embora o teste de Razão de Verossimilhança no VAR não confirme significância estatística nessas relações, a rejeição consistente no método tradicional sugere que retornos defasados da NVDA contêm informação preditiva incremental para setores economicamente sensíveis. Não foi detectada causalidade reversa (p > 0,20 em todos os casos), enquanto o setor Financeiro permaneceu estatisticamente independente da NVDA em ambas as direções.

É fundamental ressaltar que esses resultados devem ser interpretados como precedência informacional e não causalidade econômica estrutural. A relação observada entre NVDA e Energia, apesar da baixa correlação, reflete provavelmente a exposição comum a condições macroeconômicas, pois períodos de expansão elevam simultaneamente a demanda por energia, como atividade industrial e data centers, influenciando investimentos em infraestrutura de IA, produzindo padrões temporais capturados pelo teste de Granger sem implicar um canal causal direto entre os setores.

Em contraste com bolhas tecnológicas históricas, como a Cisco no período da dot-com, o ciclo atual associado à IA apresenta integração persistente com setores da economia real e liderança preditiva mensurável em segmentos produtivos, em vez de volatilidade puramente especulativa. Os resultados são compatíveis com a hipótese de que empresas de IA apresentam maior integração com setores da economia real do que no episódio dot-com Do ponto de vista de risco sistêmico e política econômica, a influência preditiva da NVDA sobre os setores Industrial e Energético indica que choques na oferta de semicondutores ou na dinâmica de investimentos em IA podem antecipar movimentos relevantes na economia produtiva. A ausência de causalidade com o setor Financeiro sugere transmissão limitada para riscos bancários diretos. Assim, os resultados reforçam o papel da IA como fator macroeconômico relevante, cujas flutuações precedem movimentos em setores cíclicos tradicionais.

De forma geral, a evidência contribui para a literatura ao documentar vínculos de precedência temporal entre ativos de infraestrutura digital de fronteira e setores econômicos clássicos sob condições plenamente estacionárias, uma configuração empírica relativamente rara em estudos financeiros de alta frequência.

**Aplicando Granger para PLTR** 

#### Tabela 3 - Teste de Estacionariedade (ADF)

| **_Série_** | **_Estatística ADF_** | **_p-valor_** | **_Ordem de Integração_** |
| ----------- | --------------------- | ------------- | ------------------------- |
| _PLTR_      | _-15.94*_             | _0.000_       | _I(0)_                    |
| _XLE_       | _-21.83_              | _0.000_       | _I(0)_                    |
| _XLF_       | _-14.22_              | _0.000_       | _I(0)_                    |
| _XLI_       | _-13.11_              | _0.000_       | _I(0)_                    |

Os resultados do teste Augmented Dickey–Fuller indicam rejeição da hipótese nula de raiz unitária para todas as séries analisadas, incluindo PLTR e os ETFs setoriais. As estatísticas altamente negativas e os p-valores próximos de zero confirmam que todas as variáveis são estacionárias em nível (I(0)), garantindo a validade econométrica dos testes de causalidade de Granger subsequentes e afastando o risco de relações espúrias decorrentes de tendências estocásticas.

####  Tabela 4 - Teste de Causalidade de Granger (PLTR vs Setores)

| **Direção**  | **p-valor (F-Test)** | **p-valor (VAR-LR)** | **Evidência**              |
| ------------ | -------------------- | -------------------- | -------------------------- |
| _PLTR → XLF_ | _0.329_              | _1.000_              | _Não_                      |
| _XLF → PLTR_ | _0.109_              | _1.000_              | _Não_                      |
| _PLTR → XLI_ | _0.509_              | _1.000_              | _Não_                      |
| _XLI → PLTR_ | _0.081_              | _1.000_              | _Não_                      |
| _PLTR → XLE_ | _0.403_              | _1.000_              | _Não_                      |
| _XLE → PLTR_ | _0.015_              | _1.000_              | _Parcial_<br><br>_(fraca)_ |

Apesar da correlação moderada entre NVDA e PLTR, os testes de causalidade de Granger não indicam precedência temporal em nenhuma direção. Isso evidencia que ambas as ações respondem simultaneamente a fatores comuns de mercado, sem que uma contenha informação preditiva relevante sobre a outra. O resultado reforça a distinção entre dependência contemporânea e causalidade dinâmica.

Os resultados sugerem que a ausência de causalidade de Granger entre NVDA e PLTR não decorre de independência econômica, mas sim da exposição conjunta a fatores macroeconômicos comuns, como ciclos de demanda agregada e investimento tecnológico, que geram co-movimento contemporâneo sem precedência temporal clara. A causalidade marginal observada de Energia (XLE) para PLTR deve ser interpretada com cautela, podendo refletir tanto a sensibilidade da firma a custos energéticos quanto o papel do setor de energia como proxy do ciclo macroeconômico, e não necessariamente um canal estrutural direto. Em conjunto, os resultados indicam que NVDA e PLTR não apresentam relação hierárquica de liderança temporal entre si, atuando como vetores tecnológicos paralelos inseridos em cadeias produtivas reais, sensíveis a choques macroeconômicos comuns, mas sem evidência de subordinação dinâmica direta.

### 5. Risco Extremo e Dinâmica de Volatilidade[

![[Pasted image 20260203213823.png]]

#### Tabela 6 - Métricas de Risco de Cauda (Retornos Diários, nível 95%)

| **_Ativo_**                 | **_VaR 95%_** | **_CVaR 95%_** | **_Gap_**<br><br>**_(CVaR−VaR)_** | **_Máx._**<br><br>**_Drawdown_** |
| --------------------------- | ------------- | -------------- | --------------------------------- | -------------------------------- |
| _NVDA_<br><br>_(2023–2026)_ | _−4,69%_      | _−6,98%_       | _−2,29%_                          | _−36,9%_                         |
| _PLTR_<br><br>_(2023–2026)_ | _−5,14%_      | _−8,04%_       | _−2,90%_                          | _−40,6%_                         |
| _CSCO_<br><br>_(1999–2001)_ | _−5,5%_       | _−8,48%_       | _−2,98%_                          | _−89.3%_                         |

A Tabela sintetiza as métricas de risco extremo estimadas para ativos representativos de dois regimes históricos distintos, a bolha dot-com (Cisco) e o ciclo contemporâneo associado à infraestrutura de inteligência artificial (NVIDIA e Palantir). As estimativas de VaR 95% capturam o limite inferior esperado nos 5% piores retornos diários, enquanto o CVaR 95% (Expected Shortfall) mensura a severidade média condicional além desse limiar, oferecendo uma medida mais robusta da exposição à cauda esquerda. Observa-se que todos os ativos apresentam gaps substanciais entre CVaR e VaR, variando entre −2,29 p.p. (NVDA), −2,90 p.p. (PLTR) e −2,98 p.p. (CSCO), evidenciando comportamento típico de distribuições com caudas pesadas, típico de ativos altamente dependentes de narrativa e nas quais as perdas extremas superam significativamente o limite indicado pelo quantil de risco tradicional.

![[Pasted image 20260203213937.png]]

Em termos comparativos, a Cisco apresenta o CVaR diário mais severo (−8,48%), corroborado por drawdown histórico superior a −85%, refletindo um colapso abrupto característico de bolha especulativa concentrada. Contudo, apesar da magnitude extrema, esse risco mostrou-se predominantemente idiossincrático e sem evidência de transmissão dinâmica persistente para outros setores econômicos, conforme validado anteriormente pelos testes de causalidade. Em contraste, NVDA e PLTR exibem CVaRs igualmente elevados (−6,98% e −8,04%), embora associados a drawdowns menos profundos no período recente. A distinção crítica reside na natureza sistêmica contemporânea desses ativos. Enquanto a Cisco representava um episódio especulativo amplamente dissociado dos fundamentos macroprodutivos, NVIDIA e Palantir atuam como vetores tecnológicos inseridos em cadeias econômicas reais, cujos impactos se manifestam em dependências dinâmicas setoriais detectadas pelos testes de causalidade de Granger.

![[Pasted image 20260203213946.png]]

Dessa forma, a evidência sugere uma transição estrutural no perfil de risco: de perdas extremas localizadas e especulativas no período dot-com para um regime contemporâneo de risco de cauda ainda elevado, porém potencialmente mais relevante em alcance macroeconômico, dada sua capacidade de propagação transversal por setores produtivos estratégicos. Tal resultado é consistente com a interpretação de que ativos ligados à IA estão integrados a cadeias econômicas amplas, ampliando a relevância sistêmica de seus choques

### 6. Estrutura Fatorial: Análise de Componentes Principais (PCA)

A Análise de Componentes Principais (PCA) foi empregada com o objetivo de identificar fatores comuns de covariância contemporânea entre ativos ligados à infraestrutura de inteligência artificial e setores representativos da economia real. O procedimento foi conduzido sobre retornos diários padronizados, garantindo que a decomposição refletisse a estrutura de correlação, e não diferenças de escala ou volatilidade individual.

![[Pasted image 20260203214036.png]]

Os resultados indicam que o primeiro componente principal (PC1) explica aproximadamente 48,9% da variância total do conjunto de ativos analisados, caracterizando-se como um fator sistêmico dominante. Tal magnitude sugere elevada integração entre os mercados tecnológicos e setores macroeconômicos no período recente.

A análise dos loadings do PC1 revela que o setor de Energia (XLE) apresenta o maior peso individual no fator comum, seguido por setores cíclicos e, em menor magnitude, por empresas diretamente associadas à infraestrutura de inteligência artificial, como NVIDIA e Palantir. Esse padrão indica que variações no setor energético estão fortemente alinhadas às flutuações do fator sistêmico contemporâneo, atuando como um importante proxy do risco agregado.

Do ponto de vista econômico, essa evidência é consistente com a interpretação de que o atual ciclo tecnológico, diferentemente da bolha dot-com, encontra-se profundamente ancorado em restrições físicas e produtivas, em especial na disponibilidade e no custo de energia. Embora o PCA não permita inferências causais, a elevada exposição do setor energético ao fator comum sugere que choques nesse segmento tendem a se propagar de forma transversal para ativos de tecnologia intensivos em infraestrutura.

# Conclusão

Os resultados obtidos não permitem afirmar que o atual ciclo de valorização tecnológica esteja isento de riscos especulativos. Pelo contrário, as métricas de risco extremo revelam que ativos associados à IA exibem elevada sensibilidade a choques adversos, com perdas médias severas em cenários de estresse. No entanto, diferentemente do episódio da bolha dot-com, as evidências sugerem que o movimento contemporâneo ocorre em um ambiente de maior interconexão entre tecnologia e setores produtivos tradicionais.

A presença de correlações robustas e persistentes, associada a indícios de precedência temporal em testes de Granger, aponta para um regime de co-movimento mais profundo entre empresas de IA e a economia real. A decomposição fatorial via PCA reforça essa interpretação ao indicar que parte relevante da variância comum está associada a setores de base física, como energia e indústria, sugerindo que a expansão tecnológica atual está ligada a restrições e demandas infraestruturais concretas.

Assim, embora elementos de exuberância possam estar presentes, a dinâmica observada é mais compatível com um processo de difusão tecnológica de caráter sistêmico do que com um episódio isolado de especulação concentrada. Pesquisas futuras podem aprofundar essa análise incorporando dados macroeconômicos, medidas de investimento real e séries de consumo energético, permitindo avaliar com maior precisão o vínculo entre inovação digital e capacidade produtiva.

# Referências

[5] SHILLER, Robert J. _Irrational Exuberance_. Princeton: Princeton University Press, 2000.

[6] ACEMOGLU, Daron. The simple macroeconomics of AI. _Economic Policy_, [S. l.], v. 40, n. 121, p. 13–58, 2025.