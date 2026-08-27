---
title: "Clusterização Hierárquica Aglomerativa aplicada ao mercado de\r

  FIIs"
tags:
  - nivel/avancado
author: Guilherme Matos; Ana Beatriz; Jonathan Pereira; Gabriela Saito
---
## 1. Introdução


O mercado brasileiro de Fundos de Investimento Imobiliário (FIIs) é convencionalmente segmen tado por tipo de ativo, fundos de papel, de tijolo, logísticos, de shoppings, de lajes corporativas. Essa classificação responde à pergunta “o que o fundo possui em carteira?” e é útil para com preender o negócio subjacente, mas é ineficiente quanto à pergunta que de fato importa para a gestão de risco de um portfólio: como o fundo se comporta quando os juros sobem, quando a inflação acelera, quando o crédito aperta? 

A limitação é mais do que teórica. Dois fundos de um mesmo segmento podem exibir per fis de risco opostos, um com contratos longos, inadimplência nula e baixa alavancagem; outro com vacância elevada, estrutura de capital alavancada e alta sensibilidade à política monetária. Tratá-los como intercambiáveis para fins de diversificação é uma ilusão, a diversificação setorial não equivale à diversificação de risco. Um investidor que distribui suas posições por diversos segmentos distintos pode, sem perceber, concentrar quase toda a sua exposição em um único perfil de risco. 

Este trabalho propõe uma alternativa orientada por dados. Em vez de partir de rótulos seto riais definidos a priori, aplica-se aprendizado não supervisionado, especificamente, a clusteriza ção hierárquica aglomerativa (HAC), sobre uma matriz quantamental que combina indicadores microeconômicos (P/VPA, LTV, vacância, inadimplência, Dividend Yield) com sensibilidades macroeconômicas (betas ao CDI, ao IPCA e ao IMA-B). O objetivo é revelar a estrutura latente de risco do mercado, deixando que os próprios dados determinem quais fundos são genuinamente semelhantes em termos de exposição. 

Da análise emergem três contribuições. Primeiro, uma taxonomia empírica de dez arquétipos de risco, cada um com identidade econômica clara e ancorada no perfil observado dos fundos que o compõem. Segundo, uma validação multifacetada dessa taxonomia por reprodutibilidade, coesão interna e coerência econômica, que distingue os agrupamentos reais de eventuais artefatos do algoritmo. Terceiro, a operacionalização do modelo em um dashboard interativo, que converte a taxonomia em um instrumento de diagnóstico de carteiras. O resultado central é, ele próprio, contraintuitivo: a maior parte do mercado converge para um único arquétipo de risco médio, evidência empírica de que a variedade aparente de FIIs encobre uma homogeneidade estrutural considerável.


## 2. Trabalhos Relacionados

A ideia de inferir a organização de um mercado a partir da estrutura de dependência entre seus ativos — em vez de impor categorias definidas a priori — tem raízes na econofísica. O trabalho seminal de Mantegna [1] mostrou que a matriz de correlação entre os retornos das ações, uma vez convertida em uma distância métrica, dá origem a uma árvore hierárquica (a árvore geradora mínima e o espaço ultramétrico associado) cuja topologia revela uma taxonomia econômica significativa. Esse resultado inaugurou um programa de pesquisa que passou a tratar 1 o mercado como um sistema complexo dotado de estrutura latente, recuperável diretamente dos dados. 

A linha foi consolidada pelos trabalhos subsequentes do mesmo grupo. Bonanno et al. [2] estenderam a abordagem para redes de ações, mostrando que informação econômica relevante pode ser extraída de matrizes de correlação ruidosas e que a topologia dessas redes permite, inclu sive, falsear modelos de mercado amplamente utilizados ao comparar mercados reais e artificiais. Tumminello et al. [3] generalizaram a árvore geradora mínima com o Planar Maximally Filte red Graph (PMFG), um grafo que retém mais ligações que a árvore preservando a planaridade, oferecendo um filtro mais rico da informação contida na matriz de correlação. O fio condutor dessa tradição é que a estrutura hierárquica/de rede da matriz de correlação carrega informação econômica, e não apenas ruído estatístico. 

Uma segunda tradição traduz essa estrutura hierárquica em decisões de construção de car teira. López de Prado [4] propôs o Hierarchical Risk Parity (HRP), argumentando que matrizes de correlação carecem da noção de hierarquia, nelas, todo ativo é substituto potencial de qual quer outro e que substituir essa estrutura plana por uma árvore produz alocações mais estáveis sem exigir a inversão da matriz de covariância. Raffinot [5] avançou nessa direção com o Hierar chical Clustering-based Asset Allocation (HCAA), empregando o linkage de Ward e selecionando explicitamente o número de grupos por meio de um índice estatístico, justamente para superar uma limitação do HRP: a de ignorar a forma do dendrograma ao alocar capital. No âmbito da prática de mercado, a mesma intuição aparece no Cluster Risk Parity de Varadi e Kapler [7], que combina clusterização com contribuição de risco igual dentro e entre grupos, evitando o agrupamento setorial manual. 

No mercado brasileiro, a aplicação dessas técnicas ainda é incipiente. Reis et al. [6] realiza ram uma comparação out-of-sample do HRP contra estratégias tradicionais de alocação na B3, concluindo que o método é, em geral, competitivo com as demais abordagens e supera o índice de mercado, um indício de que a estrutura hierárquica é informativa também no contexto nacional.

## 3. Metodologia

A estrutura de risco do mercado foi inferida por aprendizado não supervisionado, sem rótulos definidos a priori. Optou-se pela clusterização hierárquica aglomerativa (HAC) por três moti vos: (i) o método não exige a especificação prévia do número de grupos, que pode ser decidido posteriormente a partir da hierarquia de fusões, (ii) produz uma hierarquia completa, represen tável em um dendrograma, que torna explícita a proximidade relativa entre os grupos, e (iii) é determinístico não depende de inicialização aleatória, o que garante reprodutibilidade exata dos resultados.

### 3.1 Padronização

As oito features da Tabela 1 possuem escalas heterogêneas: o Dividend Yield mensal varia entre 0 e cerca de 0,04, enquanto o LTV pode atingir a unidade. Aplicada diretamente sobre os valores brutos, a distância euclidiana seria dominada pelas variáveis de maior magnitude não por serem mais informativas, mas apenas por assumirem números maiores. Para neutralizar esse efeito, cada feature foi padronizada pelo escore Z, subtraindo-se a média e dividindo-se pelo desvio padrão:

$$
z_{ij} = \frac{x_{ij} - \mu_j}{\sigma_j}
$$

onde xij é o valor da feature j para o fundo i, e µj e σj são, respectivamente, a média e o desvio padrão dessa feature na base. Após a transformação, todas as variáveis contribuem com peso equivalente para o cálculo das distâncias.

### 3.2 Distância e critério de linkage

Sobre a matriz padronizada, calculou-se a distância euclidiana entre cada par de fundos no espaço de oito dimensões:

$$d(a,b) = \sqrt{\sum_{j=1}^{8} (z_{aj} - z_{bj})^2}$$
Fundos com perfis semelhantes, mesma vacância, mesma sensibilidade ao CDI, mesmo P/VPA apresentam distância pequena e são agrupados cedo na hierarquia. A formação dos grupos seguiu o critério de Ward, que a cada passo funde o par de grupos cuja união provoca o menor aumento na variância interna total. Formalmente, o custo de fundir os grupos A e B é:


$$\Delta(A, B) = \frac{n_A n_B}{n_A + n_B} \|\bar{z}_A - \bar{z}_B\|^2$$

em que zA e zB são os centróides dos grupos e nA, nB seus tamanhos. O método de Ward tende a produzir grupos compactos e de tamanho relativamente equilibrado, sendo apropriado para dados contínuos padronizados. Partindo de 213 grupos unitários, o algoritmo realiza 212 fusões sucessivas até restar um único grupo, gerando a hierarquia completa representada no dendrograma.

### 3.3 Seleção do número de grupos

A HAC produz a hierarquia, mas não determina em que altura cortá-la, a escolha do número de grupos k que foi feita usando métodos conhecidos da literatura de Machine Learning. Para fundamentá-la, avaliaram-se três índices de validação interna para k variando de 2 a 12. 

A variância intra-cluster agregada (WCV) mede a dispersão interna somada sobre todos os grupos,

$$\text{WCV} = \sum_{c=1}^{k} \sum_{j=1}^{8} \operatorname{Var}(z_{\cdot j} \mid c)$$

servindo como referência de compacidade: quanto menor, mais homogêneos os grupos interna mente. 

O coeficiente de Silhouette avalia, para cada ponto i, o quanto ele está mais próximo do próprio grupo do que do grupo vizinho mais próximo:

$$s(i) = \frac{b(i) - a(i)}{\max\{a(i), b(i)\}}$$

onde a(i) é a distância média de i aos demais pontos de seu grupo e b(i) a distância média ao grupo vizinho mais próximo. O índice global é a média de s(i) sobre todos os pontos, variando de −1 a +1, valores próximos de +1 indicam grupos coesos e bem separados. 

O índice de Davies-Bouldin (DB) compara, para cada par de grupos, a soma de suas dispersões internas com a distância entre seus centróides, retendo o pior caso de cada grupo:

$$\text{DB} = \frac{1}{k} \sum_{i=1}^{k} \max_{j \neq i} \frac{s_i + s_j}{d(c_i, c_j)}$$

em que si é a dispersão média interna do grupo i e d(ci,cj) a distância entre os centróides. O índice é não negativo e, ao contrário do Silhouette, é tanto melhor quanto menor. 

Esses índices podem divergir, sobretudo na presença de grupos extremos cuja forte separação distorce médias globais. Nesses casos, a decisão sobre k combina as evidências quantitativas com a interpretabilidade econômica dos grupos resultantes, critério detalhado, com os valores obtidos.

### 3.4 Estratégia em dois estágios

A heterogeneidade do mercado de FIIs impõe um obstáculo a qualquer corte único da hierarquia. Alguns fundos apresentam características tão extremas, como inadimplência próxima de 100%, vacância de metade da área, alavancagem dezenas de vezes superior à mediana, que o algoritmo os isola nas primeiras divisões, antes de conseguir diferenciar o grande bloco mainstream. Um único valor de k tenderia, portanto, a separar bem os extremos e a deixar a maioria dos fundos indistinta em um só grupo. 

Para contornar esse efeito, adotou-se uma estratégia em dois estágios. No primeiro, a HAC é aplicada sobre os 213 fundos, isolando os grupos de comportamento extremo e delimitando o bloco mainstream. No segundo, a HAC é reaplicada exclusivamente sobre esse bloco, com uma nova padronização Z-score calculada dentro do subconjunto. A repadronização interna é o necessária, pois ao recalcular as escalas no contexto restrito do mainstream, diferenças que eram desprezíveis na escala global tornam-se relevantes, permitindo ao algoritmo distinguir subgru pos antes invisíveis. A taxonomia final resulta da união dos grupos extremos, identificados no primeiro estágio, com os subgrupos do mainstream, revelados no segundo.

## 4. Construção e Tratamento da Base de Dados

A matriz que alimenta o modelo de clusterização é quantamental, combina variáveis microe conômicas que descrevem a estrutura contábil e operacional de cada fundo com sensibilidades macroeconômicas que descrevem como o retorno de cada fundo reage a choques de juros, inflação e juro real. As duas dimensões são construídas em pipelines independentes e unidas ao final. Esta seção documenta a construção de cada bloco, as decisões de tratamento e os filtros aplicados até a obtenção da base definitiva de 213 FIIs descritos por oito features.

### 4.1 Base microeconômica

O bloco microeconômico foi extraído dos informes regulatórios periódicos dos FIIs publicados pela CVM, combinando os informes mensais (ativo e passivo, complemento e dados gerais) com o informe trimestral de desempenho dos imóveis. Para cada fundo, isolou-se a observação mais recente disponível, que no caso, é de Dezembro de 2025, em cada periodicidade, de modo a representar uma “fotografia” atual de seus fundamentos. 

A partir dessas fontes, derivaram-se as variáveis de risco contábil e operacional. A alavanca gem foi medida pelo Loan-to-Value, LTV = Passivo Total/Ativo Total, o Dividend Yield mensal e o valor patrimonial por cota (VPA) vieram diretamente do informe de complemento. O risco físico foi calculado em duas variáveis: a vacância, calculada como média ponderada pela área de cada imóvel do fundo, e não como média simples, para que galpões e lajes de maior porte pesem proporcionalmente ao espaço que representam, e a inadimplência média da carteira. Fundos de papel (CRI), que por natureza não possuem ativos físicos e não reportam vacância nem ina dimplência, tiveram essas variáveis preenchidas com zero, refletindo a ausência efetiva de risco operacional físico. 

Sobre a matriz resultante aplicou-se uma sequência de filtros de consistência baseados em regras de negócio, destinados a remover erros de base e anomalias contábeis sem descartar casos economicamente válidos. Foram retidos apenas os fundos com 0 ≤ LTV ≤ 1,5 (o teto admite distress severo, em que o passivo supera o ativo, mas exclui valores impossíveis), 0 ≤ DY ≤ 5% ao mês (eliminando amortizações atípicas e ajustes contábeis) e VPA estritamente positivo dentro de escala comercial plausível. Em seguida, os fundos foram conciliados com o universo efetivamente negociado na B3, o ticker de cada fundo foi extraído do código ISIN reportado à CVMe cruzado com a lista de fundos listados, garantindo que apenas FIIs com cotação em bolsa permanecessem. Por fim, removeram-se os fundos com vacância igual ou superior a 95%, casos de falência operacional cujo perfil distorceria a definição dos grupos. 

Também houveram casos de fundos nos relarórios reportados à CVM, que caracterizavam fundos de family office, que não são comercializados em bolsa e servem apenas como fundos privados familiares. Esses casos, também foram filtrados no cruzados dos dados com a base efetiva da B3.

### 4.2 Base macroeconômica: betas ortogonais

O bloco macroeconômico caracteriza a sensibilidade de cada fundo a três fatores de risco sis têmico: a política monetária (CDI), o choque de inflação (IPCA) e o choque de juro real (re presentado pelo IMA-B). As séries diárias foram agregadas em frequência mensal, o CDI por capitalização composta do mês, o IPCA pela taxa mensal e o IMA-B pelo retorno do índice. 

**Ortogonalização dos fatores.** Os três fatores macroeconômicos são, por construção, forte mente correlacionados, uma elevação do CDI tipicamente acompanha movimentos de inflação e da curva de juros reais. Estimar a sensibilidade de um fundo a esses fatores brutos produziria coeficientes contaminados por multicolinearidade, impossibilitando a leitura econômica isolada de cada exposição. Para contornar esse problema, os fatores foram ortogonalizados sequencial mente, ao estilo de Gram-Schmidt, por meio de regressões auxiliares: o choque puro de inflação (u1) é o resíduo da regressão do IPCA sobre o CDI, e o choque puro de juro real (u2) é o resíduo da regressão do IMA-B sobre o CDI e o IPCA:


$$u_1 = \text{IPCA} - (\hat{\gamma}_0 + \hat{\gamma}_1 \text{CDI})$$
$$u_2 = \text{IMA-B} - (\hat{\delta}_0 + \hat{\delta}_1 \text{CDI} + \hat{\delta}_2 \text{IPCA})$$

Os vetores resultantes {CDI, u1, u2} são mutuamente não correlacionados propriedade veri ficada empiricamente, com correlações cruzadas próximas de zero, de modo que cada um isola uma dimensão de risco distinta e interpretável.

**Estimação dos betas.** Para cada FII do universo de 377 fundos com histórico em bolsa, baixaram-se os retornos mensais ajustados no período de janeiro de 2020 a dezembro de 2025, o limite superior fixo evita qualquer vazamento de informação futura. As sensibilidades foram então estimadas por mínimos quadrados ordinários (OLS), regredindo o retorno de cada fundo sobre os três fatores ortogonais:

$$r_{i,t} = \alpha_i + \beta_i^{\text{CDI}} \text{CDI}_t + \beta_i^{\text{IPCA}} u_{1,t} + \beta_i^{\text{IMA-B}} u_{2,t} + \varepsilon_{i,t}$$

Exigiu-se um mínimo de 24 observações mensais continuas para a inclusão de um fundo, descartando se fundos recém-listados sem histórico suficiente para uma estimativa confiável.

**Filtro de outliers nos betas.** Sobre os coeficientes estimados aplicou-se um filtro baseado em escore Z robusto, construído a partir da mediana e do desvio absoluto mediano (MAD) em vez da média e do desvio padrão, evitando que os próprios outliers contaminem a estatística que os deveria detectar. Um fundo foi removido quando apresentou beta absurdo (|z| > 10 em qualquer fator) ou quando combinou desvio moderado (|z| > 5) com série histórica curta (menos de 48 meses), critério que preserva fundos de histórico longo ainda que moderadamente atípicos.

### 4.3 Matriz quantamental e base final

Os dois blocos foram unidos por inner join sobre o ticker, retendo apenas os fundos presentes simultaneamente na base micro e na matriz de betas, isto é, fundos com fundamentos contábeis consistentes e histórico de mercado suficiente para a estimação macroeconômica. Em seguida, descartaram-se as colunas de metadados das regressões (interceptos, estatísticas t, p-valores, R2 e demais indicadores de ajuste), que servem ao diagnóstico mas não constituem features do modelo. 

A última variável, o múltiplo de mercado P/VPA, foi obtida dividindo-se o preço de fe chamento de dezembro de 2025 de cada cota pelo respectivo valor patrimonial, em seguida, as variáveis de tamanho absoluto (ativo, patrimônio líquido e passivo) e o VPA bruto foram re movidos, preservando apenas o múltiplo relativo. Os fundos sem cotação disponível na data de referência (sete casos) foram eliminados por ausência de P/VPA. 

O resultado é a base definitiva submetida à clusterização: 213 FIIs descritos por oito features (Tabela 1), padronizadas e mutuamente complementares, cobrindo as dimensões de risco contábil, operacional, de mercado e macroeconômica. Como passo final, já no âmbito da modelagem, dois fundos com P/VPA extremo (superior a quatro vezes a mediana) e Dividend Yield nulo, indicativos de fundos em estruturação ou com precificação irregular, foram removidos, evitando que o algoritmo gastasse cortes separando casos anômalos em vez de revelar a estrutura do mercado.

![[Pasted image 20260827135441.png]]

![[Pasted image 20260827135449.png]]

## 5. Resultados

A clusterização hierárquica aglomerativa (HAC), aplicada sobre a base padronizada de 213 FIIs descritos por oito features quantamentais, revelou uma estrutura de risco em dois níveis, um nível macro, que isola grupos de comportamento extremo, e um nível interno, que diferencia o grande bloco mainstream do mercado. Esta seção apresenta os agrupamentos obtidos, a validação de sua coesão e a implicação econômica central do modelo.

### 5.1 Estrutura macro: quatro grupos

A seleção do número de clusters foi orientada por três métricas complementares Within-Cluster Variance (WCV), Silhouette e Davies-Bouldin (DB) avaliadas para k de 2 a 12 (Tabela 2). O Silhouette isolado favorecia k = 2, mas esse comportamento é um artefato da própria heterogenei dade do mercado. Os grupos de situação extrema são tão distintos do restante que o algoritmo os separa antes de diferenciar o mainstream, distorcendo métricas globais sensíveis a outliers. A decisão por k = 4 apoia-se em dois critérios mais robustos, o índice Davies-Bouldin atinge mínimo local em k = 4 (1,23), e, sobretudo, é nesse corte que os grupos minoritários adquirem identidade econômica imediata e interpretável.

![[Pasted image 20260827135521.png]]

O corte em k = 4 produziu um grupo dominante de 190 fundos (mainstream) e três grupos minoritários, cada um definido por uma única dimensão de risco em nível crítico: 

• Crédito Distressed (3 FIIs): inadimplência média de 80,6%, com rendimentos compro metidos (DY nulo); 

• Alavancagem Extrema (7 FIIs): LTV médio de 53,4%, contra mediana de 1,5% na base, indicando exposição elevada ao risco de refinanciamento; 

• Imóvel Degradado (13 FIIs): vacância média de 50,6%, com βIPCA negativo, consistente com ativos físicos que perdem valor real sob pressão econômica.

### 5.2 Subdivisão do grupo mainstream

O grupo de 190 fundos apresentava perfis aparentemente homogêneos na escala global. Para revelar sua estrutura interna, o HAC foi reaplicado exclusivamente sobre esse subconjunto, com padronização Z-score própria, procedimento que torna relevantes diferenças que eram pequenas no contexto dos 213 fundos. O critério Davies-Bouldin apontou k = 7 como corte mais adequado (1,21), gerando sete subgrupos com perfis econômicos distintos (Tabela 3).

### 5.3 Taxonomia final de risco

A combinação do HAC principal (k = 4) com o subclustering interno (k = 7) produziu uma taxonomia de dez arquétipos de risco mutuamente distintos (Tabela 3). Cada rótulo não é  descritivo a priori, mas decorre da feature dominante de cada grupo, a nomeação econômica está ancorada no perfil empírico observado.

![[Pasted image 20260827135630.png]]

### 5.4 Validação dos agrupamentos

A validade do modelo foi verificada por três vias. 

**Reprodutibilidade.** Por ser baseado em linkage de Ward sobre distância euclidiana, proce dimento determinístico, sem inicialização aleatória, o pipeline é integralmente reprodutível, a reexecução independente do código sobre a mesma base recupera os tamanhos de cluster e a atribuição de arquétipo idênticos nos 213 fundos. 

**Coesão interna.** Paraconfirmar que os grupos são estatisticamente reais e não baldes residuais mediu-se o desvio padrão médio interno de cada arquétipo na escala original (Tabela 4). O resultado é conclusivo, o Core Conservador, com 125 fundos, é o grupo mais coeso de toda a base (0,034), mais homogêneo que arquétipos de apenas 2 ou 3 fundos. O padrão crescente de dispersão também é economicamente coerente: os grupos de stress (Crédito Distressed, Imóvel Degradado) são internamente mais heterogêneos porque o que os une é o nível de estresse, não a estrutura, cada fundo chegou ao estresse por um caminho distinto.

![[Pasted image 20260827135714.png]]


**Coerência econômica.** Cada rótulo foi confrontado com a evidência no perfil médio do grupo, e todos se sustentam: o Crédito Distressed apresenta de fato 80,6% de inadimplência, o CRI IPCA+ exibe o maior βIPCA da base (0,081), o Duration Longo, o βCDI mais negativo (−0,061), o Income Premium, DY de 2,7% com P/VPA acima de 1,0. A taxonomia, portanto, não é um artefato numérico, mas uma leitura interpretável da estrutura de risco dos fundos.

### 5.5 Implicação central

O resultado mais relevante do modelo é empírico e contraintuitivo: 59% do mercado converge para um único arquétipo (Core Conservador), com perfis de risco estruturalmente equivalen tes. Isso significa que diversificação setorial não equivale a diversificação de risco. Um portfólio composto por fundos de segmentos distintos, lajes, logística, papel, shoppings, pode, na prática, concentrar a maior parte de suas posições em um mesmo arquétipo, sem oferecer a proteção que a aparência de variedade sugere. A taxonomia funciona, assim, como uma matriz de substituição de risco: dentro de um mesmo arquétipo, os fundos são intercambiáveis em termos de exposição, entre arquétipos, são genuinamente diversificadores.

## 6. Aplicação: dashboard de diagnóstico de risco

Para tornar a taxonomia operacional, os resultados foram materializados em um dashboard inte rativo, desenvolvido em Streamlit. O objetivo é converter a estrutura latente revelada pelo HAC em um instrumento de decisão,que permita que o investidor examinar fundos individualmente, diagnosticar a diversificação real de sua carteira e inspecionar a própria validade do modelo. A ferramenta organiza-se em quatro módulos.

![[Pasted image 20260827135824.png]]
Figura 2: Visão macro do mercado: distribuição dos arquétipos e mapa de risco. A identidade de cor é fixa por arquétipo em todos os gráficos.

### 6.1 Visão macro

O primeiro módulo apresenta a fotografia agregada do mercado: a distribuição dos 213 fundos pelos dez arquétipos e um mapa de risco que posiciona cada FII no espaço de features, colorido por arquétipo (Figura 2). Adota-se uma paleta de cores fixa e semanticamente carregada, tons neutros para o perfil de risco médio e acentos quentes para os grupos de estresse, de modo que a leitura visual seja consistente entre todas as telas.

### 6.2 Exploração individual e validação por co-movimento

O segundo módulo permite consultar um fundo específico, exibindo suas features, o arquétipo atribuído e a comparação com os pares do mesmo grupo. Como camada adicional, traça-se a série de preços do fundo e a média de seus pares, ambas reescaladas para a base 100. Esse recurso cumpre duplo papel, contextualiza o desempenho histórico e, mais importante, funciona como validação visual do modelo, se a clusterização captura risco estrutural, fundos de um mesmo arquétipo devem co-mover, ainda que pertençam a setores diferentes. Divergências acentuadas, por sua vez, sinalizam casos dignos de inspeção. 

### 6.3 Diagnóstico de carteira 

O terceiro módulo é a aplicação direta da implicação central. O usuário informa os fundos que detém, e a ferramenta decompõe a carteira por arquétipo, evidenciando a eventual concentração de risco oculta sob a aparência de diversificação setorial. Para sintetizar essa informação em um único indicador, propõe-se um score de diversificação baseado na entropia de Shannon da distribuição por arquétipo, normalizado pelo número total de arquétipos K

$$S = \frac{H(p)}{\ln K} \times 100, \qquad H(p) = -\sum_{i=1}^{K} p_i \ln p_i$$

onde pi é a fração da carteira alocada no arquétipo i e K = 10. O escore varia de S = 0, quando todos os fundos pertencem a um único arquétipo (diversificação de risco nula, ainda que o número de fundos seja elevado), a S = 100, quando a carteira se distribui uniformemente pelos dez arquétipos. Complementarmente, o módulo identifica as dimensões de risco não cobertas, distinguindo arquétipos diversificadores ausentes, que poderiam complementar a carteira, dos perfis de estresse, cuja ausência é, em geral, desejável.

![[Pasted image 20260827135945.png]]
Figura 3: Diagnóstico de carteira: composição por arquétipo, escore de diversificação e dimensões de risco não cobertas.

### 6.4 Transparência do modelo

O quarto módulo expõe a própria construção do modelo, em nome da transparência metodológica, a estrutura em dois estágios (isolamento dos extremos seguido de subclustering do mainstream), as métricas de seleção de k e a tabela de coesão interna recalculada em tempo real a partir dos dados. Registra-se explicitamente que os três grupos extremos possuem fronteiras nítidas e elevada robustez, ao passo que os sete subgrupos do mainstream resultam de uma separação mais gradual, distinção que confere ao usuário uma leitura honesta do grau de confiança associado a cada arquétipo.

### 6.5 Síntese

Em conjunto, os quatro módulos transformam um resultado de natureza cross-sectional, uma taxonomia estática de risco, em um fluxo de decisão: do panorama de mercado, à inspeção do fundo, ao diagnóstico da carteira própria, à auditoria do modelo. A contribuição prática não está em recomendar ativos, mas em tornar mensurável e visível um risco que a segmentação setorial convencional mantém oculto. 

## 7 Limitações 

As conclusões deste trabalho devem ser lidas à luz de algumas limitações, que ao mesmo tempo delimitam seu alcance e apontam extensões naturais. 

**Taxonomia de risco, não alocação de carteira.** A limitação mais relevante diz respeito ao que o trabalho deliberadamente não faz. A literatura de referência [4, 5] emprega a clusterização como etapa intermediária de uma estratégia de alocação, parte da matriz de covariância dos retornos, produz um vetor de pesos e o avalia out-of-sample. Aqui, ao contrário, a clusterização opera sobre uma matriz cross-sectional de features quantamentais e o produto final é uma clas sificação, não uma carteira ponderada. Implementar uma estratégia quantitativa análoga não era viável neste contexto, por três razões concretas. Primeiro, o objeto de entrada é distinto, a bissecção recursiva do HRP consome a matriz de covariância dos próprios ativos a ponderar, e não o espaço de features aqui clusterizado. Segundo, a taxonomia é uma fotografia em um único instante (fundamentos mais recentes e preços de dezembro de 2025), ao passo que um backtest confiável exige um painel temporal de retornos, janelas móveis e reestimação periódica dos gru pos, o que o pipeline em dois estágios, com rotulagem econômica manual dos arquétipos, não comporta de forma automática. Terceiro, o universo de FIIs impõe atritos severos a qualquer estratégia efetivamente negociável, o histórico curto de muitos fundos (a estimação dos betas já exigiu um mínimo de 24 meses, excluindo os recém-listados) e a baixa liquidez de boa parte do segmento fariam os custos de transação e o turnover dominarem o resultado, precisamente a fragilidade que Reis et al. [6] identificaram no HRP aplicado à B3, cujo turnover foi o mais alto entre as estratégias comparadas. Por isso, a avaliação de uma carteira foi deixada como extensão futura, e não como objetivo: a pergunta deste trabalho é classificatória, quais fundos compartilham perfil de risco, e não de otimização de pesos. 

**Natureza estática e dependência de regime.** Os betas macroeconômicos foram estimados sobre o período 2020–2025, marcado pela pandemia e por um ciclo de juros elevados, de modo que as sensibilidades estimadas podem não se sustentar sob outro regime monetário. A estabilidade dos arquétipos ao longo do tempo pode e tende a ser diferente dentro do Core Conservador. 

**Robustez heterogênea dos grupos.** Os três grupos extremos possuem fronteiras nítidas e elevada robustez; já os sete subgrupos do mainstream resultam de uma separação mais gradual (Silhouette em torno de 0,23), constituindo distinções de grau, e não fronteiras categóricas. Além disso, as métricas internas de seleção de k não foram unânimes, o Silhouette isolado favorecia k = 2, e a decisão final apoiou-se no índice Davies-Bouldin somado à interpretabilidade econômica. 

**Decisões de tratamento e de features.** A base final descreve um universo filtrado, a re moção de outliers e os cortes de consistência implicam que a taxonomia caracteriza o mercado mainstream tratado, não o universo bruto. A imputação de zero em vacância e inadimplência para os fundos de papel, e a medição do P/VPA em uma data única, são escolhas de modelagem que influenciam o resultado e poderiam ser objeto de análise de sensibilidade.

## Referências 

[1] Mantegna, R. N. (1999). Hierarchical structure in financial markets. The European Physical Journal B, 11(1), 193–197. 

[2] Bonanno, G., Caldarelli, G., Lillo, F., Miccichè, S., Vandewalle, N., & Mantegna, R. N. (2004). Networks of equities in financial markets. The European Physical Journal B, 38(2), 363–371. 

[3] Tumminello, M., Aste, T., Di Matteo, T., & Mantegna, R. N. (2005). A tool for filtering information in complex systems. Proceedings of the National Academy of Sciences, 102(30), 10421–10426. 

[4] López de Prado, M. (2016). Building diversified portfolios that outperform out-of-sample. The Journal of Portfolio Management, 42(4), 59–69. 

[5] Raffinot, T. (2017). Hierarchical clustering-based asset allocation. The Journal of Portfolio Management, 44(2), 89–99. 

[6] Reis, F., Sobreira, A., Trucíos, C., & Asrilhant, B. (2023). Using hierarchical risk parity in the Brazilian market: An out-of-sample analysis. Working paper. 

[7] Varadi, D., & Kapler, M. (2013). Cluster Risk Parity. CSSA Analytics e Systematic Investor (publicação de praticante online)



