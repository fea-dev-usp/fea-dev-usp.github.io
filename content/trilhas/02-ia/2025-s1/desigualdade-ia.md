---
title: Desvendando Desigualdades em São Paulo Utilizando Inteligência Artificial
tags:
  - "#trilha/ia"
  - "#nivel/avancado"
---
_**Autores:** Felipe Bulgareli de Faria · Gustavo Katsuo Tsutsui · Thales Vieira Rodrigues_

## Lista de Figuras

- **Figura 1.** Dados concatenados  
- **Figura 2.** Identificação de valores nulos  
- **Figura 3.** Coeficiente de variação por indicador  
- **Figura 4.** Histogramas dos indicadores  
- **Figura 5.** Boxplot dos indicadores  
- **Figura 6.** Matriz de correlação entre indicadores  
- **Figura 7.** Dispersão: domicílios sem água vs. cobertura vegetal per capita  
- **Figura 8.** Dispersão: domicílios sem esgoto vs. cobertura vegetal per capita  
- **Figura 9.** Dispersão: domicílios sem esgoto vs. domicílios sem água  
- **Figura 10.** Dispersão: estabelecimentos formais vs. empregos formais  
- **Figura 11.** Dispersão: famílias (transferência de renda) vs. famílias em extrema pobreza  
- **Figura 12.** Dispersão: violência contra pessoas idosas vs. violência contra crianças e adolescentes  
- **Figura 13.** Dispersão: taxa de mortalidade infantil vs. proporção de gestantes adolescentes  
- **Figura 14.** Dispersão: taxa de mortalidade infantil vs. idade média ao morrer  
- **Figura 15.** Dispersão: proporção de gestantes adolescentes vs. idade média ao morrer  
- **Figura 16.** Dispersão: população em situação de rua vs. livros/serviços de leitura  
- **Figura 17.** Fluxograma do projeto  
- **Figura 18.** Tendência linear forte (alto R²)  
- **Figura 19.** Tendência linear fraca (baixo R²)  
- **Figura 20.** Visualização dos clusters (K-Means, k = 2)  
- **Figura 21.** Perfil comparativo (K-Means, k = 2)  
- **Figura 22.** Análise do coeficiente de silhueta  
- **Figura 23.** Visualização dos clusters com PCA (k = 12)  

## Lista de Tabelas

- **Tabela 1.** Indicadores com alta colinearidade  
- **Tabela 2.** Métricas de performance dos modelos de regressão linear  
- **Tabela 3.** Perfil detalhado dos 12 clusters  

## Seções
- [Introdução](#introdução)
- [Descrição e origem dos dados utilizados](#descrição-e-origem-dos-dados-utilizados)
- [Processamento e preparação dos dados](#processamento-e-preparação-dos-dados)
- [Análise exploratória](#análise-exploratória)
- [Metodologia](#metodologia)
  - [Procedimentos adotados](#procedimentos-adotados)
  - [Decisões técnicas](#decisões-técnicas)
- [Resultados e avaliação](#resultados-e-avaliação)
  - [Análise de regressão linear](#análise-de-regressão-linear)
	  - [Gráficos e interpretação dos resultados](#gráficos-e-interpretação-dos-resultados)
  - [Resultados do clustering K-Means (k = 2)](#resultados-do-clustering-k-means-k--2)
    - [Métricas e gráficos](#métricas-e-gráficos)
    - [Interpretação dos resultados](#interpretação-dos-resultados)
  - [Resultados do clustering hierárquico (k = 12)](#resultados-do-clustering-hierárquico-k-12)
    - [Métricas e gráficos](#métricas-e-gráficos-1)
    - [Interpretação dos resultados](#interpretação-dos-resultados-1)
- [Discussão, limitações e próximos passos](#discussão-limitações-e-próximos-passos)
- [Conclusão](#conclusão)
- [Referências](#referências)

## Introdução

O município de São Paulo, de acordo com o Censo Demográfico de 2022, realizado pelo Instituto Brasileiro de Geografia e Estatística (IBGE), é o maior do Brasil, totalizando quase 12 milhões de habitantes em aproximadamente 1.521 km². Todo esse território é subadministrado em 32 subprefeituras, criadas pela lei municipal nº 13.399, de 1º de agosto de 2002, as quais administram os 96 distritos do município, em que cada uma apresenta características socioeconômicas distintas, de modo a representarem diferentes realidades dentro do mesmo município.

O Índice de Gini é uma medida estatística, cujo valor varia entre 0 e 1, que serve como uma métrica de desigualdade, ao quantificar a desigualdade na distribuição de renda em um determinado grupo ou população. Quanto mais próximo de 1, maior a desigualdade de renda, enquanto que um valor próximo a 0 indica uma igualdade  (WORLD BANK, 2025), No caso de São Paulo, segundo o Departamento de Informação e Informática do SUS (DataSUS), o índice de Gini da renda domiciliar per capita do município é de 0,6453  (MINISTÉRIO DA SAÚDE, 2010), indicando um grau de desigualdade de renda elevado, com uma grande disparidade entre os habitantes. Além disso, outra métrica importante na avaliação de desigualdades regionais é o Índice de Desenvolvimento Humano (IDH), que utiliza indicadores relacionados à renda, educação e saúde para medir a qualidade de vida de uma dada população (WHO, 2025) Cada subprefeitura de São Paulo possui um determinado IDH e, nesse contexto, apesar de servir como uma importante ferramenta para compreender a realidade socioeconômica de dado país, cidade ou Estado, por usar como base indicadores de apenas três dimensões diferentes, ela pode ocultar nuances relevantes quando analisados em escalas territoriais menores, como as subprefeituras de São Paulo.

Dessa forma, este projeto tem como objetivo estruturar uma análise preditiva e exploratória dos indicadores socioeconômicos das 32 subprefeituras paulistanas, a partir de séries históricas, com o propósito de identificar padrões de evolução, prever tendências futuras e, sobretudo, mapear as regiões com as maiores vulnerabilidades socioeconômicas.

## Descrição e origem dos dados utilizados

Os dados utilizados no projeto são oriundos do [ObservaSampa](https://observasampa.prefeitura.sp.gov.br/) (Observatório de Indicadores da Cidade de São Paulo), uma plataforma online da Secretaria Municipal de Urbanismo e Licenciamento da Prefeitura de São Paulo que tem como intuito armazenar e reunir dados (indicadores) que são capazes de mensurar a qualidade de vida dos habitantes do município, acesso a equipamentos públicos pela população, assim como métricas e parâmetros de avaliação de desempenho das iniciativas governamentais. Essa plataforma é alimentada por um trabalho conjunto de várias secretarias municipais, institutos de pesquisa e outras agências. Dessa forma, esses dados servem como uma ferramenta de direcionamento de recursos e políticas públicas, auxiliando na tomada de decisão com base em critérios racionais. Os indicadores estão divididos em 18 temas distintos, como zeladoria, saúde, economia, educação, entre outros. Além dos indicadores, também é possível selecionar os dados com base no nível regional de interesse, sendo eles: distrito, subprefeitura e município. Por fim, ainda, apesar da variação entre cada um, há registro desses indicadores ao longo de cerca de vários anos, permitindo observar como eles flutuaram em um dado período de tempo e obter insights.

Neste projeto, foram escolhidos 11 temas e 21 indicadores, a nível subprefeitural, a serem trabalhados. Esse nível regional foi escolhido porque, embora possibilite uma granularidade espacial menor que a nível distrital, há uma maior disponibilidade de dados em comparação com este. Outros indicadores foram considerados relevantes, no entanto, não possuíam os dados necessários para a execução do projeto a nível subprefeitural. 

Os temas, com seus respectivos indicadores escolhidos foram:

- **Assistência social**
	- População em situação de rua;    
	- Quantidade de famílias que recebem recursos dos programas de transferência de renda (Renda Mínima, Renda Cidadã e Bolsa Família).
- **Cultura**
	- Livros disponíveis nos serviços municipais de leitura (por mil habitantes).
- **Economia:** 
	- Estabelecimentos formais no município - Total.
- **Educação:** 
	- Taxa de Universalização da Educação Básica obrigatória (%).
- **Meio ambiente: **
	- Cobertura vegetal per capita (m²/hab);
	- Cobertura vegetal no MSP (%).
- Mobilidade e Segurança no Trânsito
	- Mortes no trânsito (por 100 mil habitantes).
- **Moradia:**
	- Proporção de Domicílios não conectados a rede geral de Esgoto (%);
	- Proporção de Domicílios não conectados a rede geral de Água (%).
- **Saúde:** 
	- Taxa de mortalidade infantil (por mil nascidos vivos);
	- Proporção de gestantes adolescentes (%);
	- Tempo médio de espera para exames prioritários (em dias);
	- Número de Unidades Básicas de Saúde;
	- Idade média ao morrer (em anos).
- **Segurança e Violência**
	- Número de casos notificados de violência contra crianças e adolescentes;
	- Número de casos de notificação de violência contra pessoas idosas.
- **Trabalho e renda**
	- Empregos formais no município - Total.
- **Zeladoria**
	- Número de ocorrências atendidas – deslizamento;
	- Número de ocorrências atendidas – alagamento;
	- Número de moradias em setores de risco geológico alto ou muito alto.

## Processamento e preparação dos dados

A fim de garantir a usabilidade dos dados nas análises a serem realizadas, foram aplicadas etapas de processamento e preparação dos dados. Primeiramente, os arquivos em formato .csv contendo os indicadores escolhidos, foram baixados no ObservaSampa. Em seguida, foi observada a consistência entre as colunas dos arquivos, isto é, se todas possuíam o mesmo nome, uma vez que isso seria necessário para a junção dos arquivos, além da contagem do número de linhas, que deveriam ser iguais, e colunas de cada arquivo. Durante essa etapa, foi verificada uma inconsistência entre os arquivos, uma vez que alguns apresentavam 33 linhas, correspondendo ao número de subprefeituras no município de São Paulo e o cabeçalho, e outras 129 linhas. Após análise, foi constatado que alguns arquivos, apesar de terem sido filtrados no ObservaSampa para incluírem dados unicamente das subprefeituras, também continham informações sobre os distritos. Dessa maneira, foi necessário a inclusão de uma etapa de exclusão desse excedente de dados.

Subsequentemente, os 21 arquivos foram concatenados em um único DataFrame, que foi convertido de formato wide para long com o intuito de unificar o formato dos dados, resultando em um arquivo de 7.328 linhas e 6 colunas, contendo as informações agrupadas por região, nível regional, indicador, valor, ano e nome do indicador.

	Figura 1 - Dados Concatenados

![[projeto-desigualdade-ia-18.png]]

>[!info]
>Fonte: Elaboração Própria

Por conseguinte, foi iniciada a etapa de identificação de valores ausentes e nulos. Não foram identificados valores ausentes no DataFrame, porém foram apontados 162 linhas com a coluna “valor” igual a zero. Após inspeção minuciosa, foi observado que esses valores estão corretos e que, de fato, correspondem ao valor zero, refletindo a ausência do fenômeno medido em determinadas subprefeituras, como ocorrência de deslizamentos ou população em situação de rua. Finalmente, após isso, deu-se prosseguimento à análise exploratória de dados.

	Figura 2 - Identificação de Valores Nulos

![[projeto-desigualdade-ia-16.png]]

>[!info]
>Fonte: Elaboração Própria

## Análise explanatória

Na análise exploratória, primeiramente para fins de melhor usabilidade dos dados, foi utilizado a função “pivot()” no DataFrame concatenado para transformar regiões como índice (index = ’região’) e indicadores como colunas (columns = ’nome_indicador’), uma vez que antes havia uma única coluna que continha todos os indicadores. Após esse processo, cada indicador tornou-se uma própria coluna, facilitando a manipulação dos dados. Em seguida, foi inicializado o cálculo de medidas as estatísticas básicas descritivas de cada índice utilizando a função “describe()”, que proporcionou a observação, para cada indicador, do número de valores não nulos em cada coluna, a média, o desvio padrão, o ponto mínimo, o percentil 25%, o percentil 50% (mediana), o percentil 75% e ponto máximo. 

Nesse sentido, também foi calculado e plotado o coeficiente de variação, ferramenta de dispersão que, nesse caso, demonstrou o quanto cada indicador varia percentualmente em relação a sua média. No gráfico gerado, a conclusão nítida é que o índice com menor homogeneidade foi o de cobertura vegetal, e o de maior homogeneidade foi o de idade média ao morrer.

	Figura 3 - Coeficiente de Variação por Indicador

![[projeto-desigualdade-ia-8.png]]

>[!info]
>Fonte: Elaboração Própria

Ademais, foi inicializada as visualizações exploratórias, para detectar padrões nos dados, valores discrepantes (outliers), eventos anômalos e observar as variáveis dos indicadores mais a fundo. Nessa perspectiva, foram plotados um histograma e um boxplot para cada índice, como demonstrado a seguir:

	Figura 4 - Histograma dos Indicadores

![[projeto-desigualdade-ia-7.png]]

>[!info]
>Fonte: Elaboração Própria

	Figura 5 - Boxplot dos Indicadores

![[projeto-desigualdade-ia-10.png]]

>[!info]
>Fonte: Elaboração Própria

Além disso, foi realizada uma análise de correlação entre os índices. Para isso, foi plotado um heatmap entre todos os indicadores.

	Figura 6 - Matriz de correlação dos Indicadores

![[projeto-desigualdade-ia-9.png]]

>[!info]
>Fonte: Elaboração Própria

Subsequentemente, foi realizada a filtragem das correlações para detectar os indicadores com uma alta colinearidade ( > 0.85), os quais estão descritos na tabela abaixo.

	Tabela 1 -Indicadores com alta colinearidade

| Indicador 1                                  | Indicador 2                                   | Correlação |
|----------------------------------------------|-----------------------------------------------|-----------:|
| domicilios_sem_agua_percentual               | cobertura_vegetal_per_capita_m2hab            |      0.99 |
| domicilios_sem_esgoto_percentual             | cobertura_vegetal_per_capita_m2hab            |      0.87 |
| domicilios_sem_esgoto_percentual             | domicilios_sem_agua_percentual                |      0.91 |
| estabelecimentos_formais_total               | empregos_formais_municipio_total              |      0.97 |
| familias_transferencia_renda                 | familias_em_extrema pobreza                   |      0.99 |
| pop_em_situacao_de_rua                       | livros_servicos_leitura_1000hab               |      0.88 |
| proporcao_gestantes_adolescentes             | idade_media_ao_morrer                         |      0.96 |
| taxa_mortalidade_infantil                    | idade_media_ao_morrer                         |      0.87 |
| violencia_criancas_adolescentes_notificados  | proporcao_gestantes_adolescentes              |      0.92 |
| violencia_pessoas_idosas_notificados         | violencia_criancas_adolescentes_notificados   |      0.95 |

Por fim, para esses pares altamente correlacionados, foram feitos gráficos de dispersão, para visualizar suas tendências e observar o comportamento de uma variável à medida que a outra varia:

	Figura 7 - Dispersão domicílios sem água vs. cobertura vegetal per capita

![[projeto-desigualdade-ia-2.png]]

>[!info]
>Fonte: Elaboração Própria

	Figura 8 - Dispersão domicílios sem esgoto vs. cobertura vegetal per capita

![[projeto-desigualdade-ia-1.png]]

>[!info]
>Fonte: Elaboração Própria

	Figura 9 - Dispersão domicílios sem esgoto vs. domicílios sem água

![[projeto-desigualdade-ia-14.png]]

>[!info]
>Fonte: Elaboração Própria

	Figura 10 - Dispersão estabelecimentos formais vs empregos formais

![[projeto-desigualdade-ia-11.png]]

>[!info]
>Fonte: Elaboração Própria

	Figura 11 - Dispersão famílias transferência renda vs famílias em extrema pobreza

![[projeto-desigualdade-ia-13.png]]

>[!info]
>Fonte: Elaboração Própria

	Figura 12 - Dispersão  violência pessoas idosas vs violência crianças adolescentes

![[projeto-desigualdade-ia-15.png]]

>[!info]
>Fonte: Elaboração Própria

	Figura 13- Dispersão  taxa mortalidade infantil vs proporção gestantes adolescentes

![[projeto-desigualdade-ia-17.png]]

	Figura 14- Dispersão  taxa mortalidade infantil vs idade média ao morrer

![[projeto-desigualdade-ia-19.png]]

>[!info]
>Fonte: Elaboração Própria

	Figura 15- Dispersão proporção gestantes adolescentes vs idade média ao morrer

![[projeto-desigualdade-ia-20.png]]

>[!info]
>Fonte: Elaboração Própria

	Figura 16- Dispersão  população situação de rua vs livros servicos leitura

![[projeto-desigualdade-ia-21.png]]

>[!info]
>Fonte: Elaboração Própria

Portanto, a análise exploratória teve como principal objetivo detectar anomalias, padrões e comportamentos dos indicadores por meio de estatísticas descritivas, plotagem de histogramas, boxplots, mapa de correlação e gráficos de dispersão entre variáveis altamente correlacionadas.

## Metodologia

### Procedimentos adotados

No contexto de Machine Learning, os tipos de treinamentos aos quais foram submetidos os modelos testados neste projeto, a fim de atingir os objetivos propostos, podem ser classificados tanto como aprendizado supervisionado quanto não supervisionado, conforme os objetivos específicos de cada etapa da análise. O principal objetivo num aprendizado supervisionado é treinar um modelo a partir de um conjunto de dados que serve como base para que sejam feitas previsões sobre tendências futuras (RASCHKA; LIU; MIRJALILI, 2022). Já no caso do aprendizado não supervisionado, não há um conjunto de dados que possa “supervisionar” a análise, de modo que, dessa forma, se busca visualizar relações entre as variáveis ((RASCHKA; LIU; MIRJALILI, 2022). Nesse sentido, os modelos testados neste projeto foram aplicados nessas abordagens, respectivamente, com o objetivo de realizar previsões de tendências e agrupar regiões com características socioeconômicas semelhantes. Enquanto que o aprendizado supervisionado foi utilizado para prever a evolução temporal de diversos indicadores em cada subprefeitura, enquanto o aprendizado não supervisionado foi aplicado para a identificação de padrões e agrupamentos de subprefeituras com perfis similares.

Para as projeções temporais dos indicadores, optou-se pela utilização da regressão linear simples, mesmo existindo abordagens mais sofisticadas e robustas para séries temporais. A escolha foi fundamentada em algumas razões específicas: a disponibilidade limitada de dados históricos (muitas séries possuem apenas 10 a 15 anos de observações); a predominância de tendências lineares claras em grande parte dos indicadores analisados; e, por fim, a necessidade de uma abordagem simples, transparente e de fácil interpretação para a comunicação dos resultados. Como a base de dados possui poucas observações por série, a validação foi conduzida com foco em ajustes in-sample, sem separação de conjuntos de treino e teste, visto que a extrapolação temporal foi limitada a um horizonte de 5 anos futuros, onde o risco de overfitting é mitigado pela simplicidade do modelo linear. A avaliação dos modelos de regressão foi realizada com base em métricas clássicas de análise de predição: R² (coeficiente de determinação), que mede a proporção da variabilidade dos dados explicada pelo modelo; MAE (erro absoluto médio), que avalia o desvio médio entre os valores previstos e observados; e MAPE (erro percentual absoluto médio), que expressa o erro médio em termos percentuais, facilitando a comparação entre indicadores de escalas distintas. Como a base de dados possui poucas observações por série, a validação foi conduzida com foco em ajustes in-sample.

Para a etapa de agrupamento das subprefeituras, foram aplicadas técnicas de clustering não supervisionado, incluindo K-Means e Agrupamento Hierárquico, com o objetivo de identificar grupos de regiões com comportamentos similares em relação aos indicadores analisados. Nesta etapa, a escolha das técnicas foi guiada pela necessidade de métodos que permitissem tanto uma visão geral dos agrupamentos (K-Means) quanto uma análise mais granular das relações hierárquicas entre as subprefeituras (dendrogramas). O ajuste dos parâmetros considerou tanto critérios quantitativos quanto a interpretação qualitativa dos grupos formados, buscando coerência espacial e socioeconômica nos clusters identificados.

O processo de ajuste dos parâmetros foi realizado de forma iterativa: no K-Means, variando o número de clusters (k) e analisando a métrica de silhouette score para determinar a coesão e separação dos agrupamentos. Para o Agrupamento Hierárquico, foi testada a estratégia de linkage ward, já que ela minimiza a variância dentro de cada cluster, além de apresentar maior estabilidade e coerência nos resultados. Como etapa complementar à clusterização, foi aplicada a técnica de PCA (análise de componentes principais) para a redução de dimensionalidade e visualização dos agrupamentos, permitindo uma análise visual clara dos clusters formados.

Em suma, o fluxo metodológico envolveu a utilização de modelos preditivos simples e interpretáveis para projeção de tendências temporais e técnicas de agrupamento não supervisionado para análise espacial dos indicadores, com validação das métricas de desempenho e ajuste criterioso dos parâmetros envolvidos, assegurando resultados alinhados aos objetivos do projeto.

	Figura 17 - Fluxograma do projeto

![[projeto-desigualdade-ia-22.png]]

>[!info]
>Fonte: Elaboração Própria

### Decisões técnicas

Durante o desenvolvimento do projeto, foram tomadas algumas decisões técnicas para garantir a coerência dos resultados e a reprodutibilidade do estudo.

 Primeiramente, o projeto seria focado nos distritos do município de São Paulo, o que permitiria uma melhor análise espacial dos dados, no entanto, optou-se por utilizar dados por subprefeitura devido à maior disponibilidade e consistência dessas informações que da outra subdivisão, embora se reconheça que isso possa reduzir a granularidade da análise. Isso buscou garantir que houvesse dados suficientes para todos os agrupamentos, ainda que a heterogeneidade dos atributos coletados representasse um desafio adicional para a segmentação, o que também aconteceria caso fossem utilizados os dados de distritos. 

Além disso, foram removidas variáveis (indicadores) altamente correlacionadas, com o intuito de evitar redundância de informação e distorção nos resultados de clusterização. Isso foi feito após análise da matriz de correlação, definindo um limiar de corte de 0.85. Essa decisão foi motivada pelos silhouette scores inicialmente baixos no método de clustering por K-Means, de modo que a diferença antes e depois das remoções, apesar de pouca, pode ser observada no Notebook do projeto.

## Resultados e Avaliação

### Regressão Linear

A performance de cada modelo de regressão linear foi avaliada utilizando o Coeficiente de Determinação (R²), o Erro Absoluto Médio (MAE) e o Erro Percentual Absoluto Médio (MAPE). A Tabela 2 resume os resultados médios, agrupando todas as subprefeituras, em ordem decrescente por R². Os resultados correspondentes a cada uma das subprefeituras, por indicador, assim como de todos os demais gráficos gerados, estão presentes no [repositório](https://github.com/Thavr/ProjetoFinalGrupo2) associado ao projeto no GitHub.

	Tabela 2: Métricas de Performance dos Modelos de Regressão Linear


**Alta previsibilidade (R² > 0,90)**

| Indicador                               |   R² |    MAE | MAPE (%) |
|-----------------------------------------|-----:|-------:|---------:|
| domicilios_sem_agua_percentual          | 1.00 |  0.00  |     0.00 |
| domicilios_sem_esgoto_percentual        | 1.00 |  0.00  |     0.00 |
| idade_media_ao_morrer                   | 0.99 |  0.15  |     0.00 |
| moradias_setores_risco_geologico_alto   | 0.97 | 33.48  |     0.02 |
| violencia_pessoas_idosas_notificados    | 0.96 |  3.10  |     0.05 |
| numero_ubs                               | 0.93 |  0.07  |     0.01 |
| cobertura_vegetal_msp                   | 0.91 |  0.83  |     0.03 |
| proporcao_gestantes_adolescentes        | 0.91 |  0.60  |     0.06 |
| violencia_criancas_adolescentes_notificados | 0.90 | 17.13  |     0.07 |

**Média previsibilidade (0,50 < R² ≤ 0,90)**

| Indicador                         |   R² |     MAE | MAPE (%) |
|-----------------------------------|-----:|--------:|---------:|
| familias_transferencia_renda      | 0.85 | 1229.46 |     0.08 |
| taxa_universalizacao_educacao_basica | 0.83 |   1.66 |     0.02 |
| empregos_formais_municipio_total  | 0.81 | 5220.42 |     0.04 |
| mortes_transito_100milhab         | 0.78 |   0.85 |     0.11 |
| pop_em_situacao_de_rua            | 0.75 | 105.05 |     0.25 |
| taxa_mortalidade_infantil         | 0.69 |   0.27 |     0.02 |

**Baixa previsibilidade (R² ≤ 0,50)**

| Indicador                          |   R² |     MAE | MAPE (%) |
| ---------------------------------- | ---: | ------: | -------: |
| estabelecimentos_formais_total     | 0.44 |  406.52 |     0.05 |
| cobertura_vegetal_per_capita_m2hab | 0.42 |    1.56 |     0.02 |
| tempo_espera_exames_prioritarios   | 0.40 |    8.66 |     0.18 |
| familias_em_extrema pobreza        | 0.30 | 1770.36 |     0.10 |
| ocorrencias_deslizamento           | 0.27 |    3.21 |     0.49 |
| ocorrencias_alagamento             | 0.26 |    8.76 |     0.51 |
| livros_servicos_leitura_1000hab    | 0.16 |   64.60 |  8.8e+16 |
### Gráficos e Interpretação de Resultados

A análise das projeções (Figura 1 e 2) revela que indicadores de infraestrutura (saneamento, UBS) e demográficos (longevidade) mostram tendências claras e são altamente previsíveis. Em contrapartida, indicadores de vulnerabilidade social (pobreza, população de rua) e riscos ambientais (alagamentos) são muito mais voláteis, com baixo R², indicando que a sua evolução é influenciada por fatores mais complexos que a regressão linear simples não consegue capturar.

	 Figura 18: Tendência Linear Forte (Alto R²)

![[projeto-desigualdade-ia-23.png]]

>[!info]
>Fonte: Elaboração Própria

	Figura 19: Tendência Fraca (Baixo R²)

![[projeto-desigualdade-ia-24.png]]

>[!info]
>Fonte: Elaboração Própria

## Resultados do Clustering K-Means (k = 2)

### Métricas e Gráficos

Para a análise com K-Means, foi utilizado k = 2, correspondendo ao primeiro pico de estabilidade do coeficiente de silhouette score, que atinge o valor de 0.250.

	Figura 20: Visualização dos Clusters (K-Means, k = 2)

![[projeto-desigualdade-ia-3.png]]

>[!info]
>Fonte: Elaboração Própria

	Figura 21: Perfil Comparativo (K-Means, k=2)

![[projeto-desigualdade-ia-4.png]]

>[!info]
>Fonte: Elaboração Própria

### Interpretação dos Resultados

A análise com k = 2 revelou a principal fratura socioeconómica da cidade, dividindo-a em dois grandes eixos:

  

- Cluster 0 (Eixo da Vulnerabilidade): Agrupa 17 distritos com indicadores consistentemente mais desfavoráveis: maior pobreza, menor longevidade, maior exposição a riscos e maior violência infanto-juvenil. 
	- Distritos Pertencentes: Butantã, Campo Limpo, Capela Do Socorro, Cidade Ademar, Cidade Tiradentes, Freguesia-Brasilândia, Guaianases, Itaim Paulista, Itaquera, Jaçanã-Tremembé, M'Boi Mirim, Parelheiros, Perus, Pirituba-Jaraguá, Sapopemba, São Mateus, São Miguel.  

- Cluster 1 (Eixo do Desenvolvimento): Agrupa 15 distritos com melhores condições de vida: menor pobreza, maior longevidade, melhor acesso à educação e mais estabelecimentos formais. 
	- Distritos Pertencentes: Aricanduva-Formosa-Carrão, Casa Verde-Cachoeirinha, Ermelino Matarazzo, Ipiranga, Jabaquara, Lapa, Mooca, Penha, Pinheiros, Santana-Tucuruvi, Santo Amaro, Sé, Vila Maria-Vila Guilherme, Vila Mariana, Vila Prudente.

## Resultados do Clustering Hierárquico (k=12)

### Métricas e Gráficos

A análise do Coeficiente de Silhueta para o modelo hierárquico (Figura 5) apontou k=12 como o número ótimo de clusters, com um score de 0.3247, permitindo uma segmentação mais detalhada.

	Figura 22: Análise do Coeficiente de Silhueta

![[projeto-desigualdade-ia-5.png]]

>[!info]
>Fonte: Elaboração Própria

	Figura 23: Visualização dos Clusters com PCA (k=12)

![[projeto-desigualdade-ia-6.png]]

>[!info]
>Fonte: Elaboração Própria

### Interpretação dos Resultados

A segmentação em 12 clusters aprofunda a análise, revelando que os "Eixos de Vulnerabilidade e Desenvolvimento" não são blocos homogêneos. A Tabela 3 resume o perfil de cada cluster.

	Tabela 3: Perfil Detalhado dos 12 Clusters

| Cluster | Nome sugerido                          | Perfil principal                                                                 | Distritos pertencentes                                                                                                     |
|:------:|----------------------------------------|-----------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
|   0    | Elite e Alta Qualidade de Vida         | Menor mortalidade infantil, maior longevidade, menor pobreza e violência.        | Lapa; Pinheiros; Vila Mariana                                                                                              |
|   1    | Polos Educacionais com Desafios        | Maior taxa de educação, mas alta pobreza e mortalidade infantil.                 | Mooca; Penha                                                                                                               |
|   2    | Vulnerabilidade Crítica em Saúde e Pobreza | Altíssima mortalidade infantil, baixa longevidade e alta pobreza.               | Freguesia-Brasilândia; Guaianases; Pirituba-Jaraguá; São Mateus; São Miguel                                                |
|   3    | Desafios Moderados e Baixa Escolaridade| Indicadores médios/negativos, com baixa taxa de educação.                        | Butantã; Casa Verde-Cachoeirinha; Ermelino Matarazzo; Ipiranga; Jabaquara; Vila Prudente                                   |
|   4    | Vulnerabilidade em Saúde e Educação    | Baixa longevidade, alta mortalidade infantil e baixa taxa de educação.           | Jaçanã-Tremembé; Perus; Sapopemba                                                                                          |
|   5    | Pobreza e Violência Extremas           | Pobreza muito alta e o segundo maior índice de violência.                        | Campo Limpo; Capela do Socorro; Itaim Paulista                                                                              |
|   6    | Crise Socioeducacional e de Segurança  | Pobreza muito elevada, taxa de educação muito baixa e alta violência.            | Cidade Ademar; Itaquera                                                                                                     |
|   7    | Crise de Longevidade                   | Idade média ao morrer drasticamente baixa (59,5 anos), a menor de todas.        | Cidade Tiradentes; Parelheiros                                                                                              |
|   8    | Prosperidade com Lacunas na Saúde Infantil | Baixa pobreza, mas alta mortalidade infantil.                                   | Aricanduva-Formosa-Carrão; Vila Maria-Vila Guilherme                                                                        |
|   9    | Qualidade de Vida Elevada              | Baixa pobreza, alta longevidade e excelente taxa de educação.                    | Santana-Tucuruvi; Santo Amaro                                                                                               |
|  10    | Epicentro da Crise Múltipla            | Piores indicadores de pobreza e violência (caso extremo).                        | M’Boi Mirim                                                                                                                |
|  11    | Défice Educacional Crítico             | Pior taxa de educação, combinada com alta pobreza.                               | Sé                                                                                                                         |

## DISCUSSÃO, LIMITAÇÕES E PRÓXIMOS PASSOS

A partir dos resultados das análises realizadas, é possível inferir algumas hipóteses à respeito do que foi observado. Primeiramente, como dito anteriormente, foi verificado que o uso da técnica de regressão linear simples para prever indicadores de infraestrutura, como  percentual de domicílios com saneamento básico e número de UBS) e demográficos (longevidade) mostram tendências claras e são altamente previsíveis. Nesse contexto, 9 das 21 análises para os indicadores escolhidos apresentaram um elevado R² (> 0.9). 

Entretanto, a análise para indicadores de vulnerabilidade social e riscos ambientais, que somaram 7 do total de análises, tiveram previsibilidade baixa, com baixo R² (<= 0.5), indicando que são altamente voláteis, e que sua evolução é influenciada por fatores mais complexos que a regressão linear simples não consegue capturar. Assim, em estudos futuros, mostra-se necessário a inclusão de mais modelos de regressão para o estudo da previsão desses indicadores que não possuem tendências claras ao longo do tempo, além de verificar o registro de possíveis fenômenos atípicos que podem estar influenciando a previsibilidade do indicador, como pode ser o caso dos indicadores de riscos ambientais, cujos valores discrepantes em determinados anos podem ser explicados pela influência de fenômenos climáticos naturais de ocorrência irregular como El Niño e La Ninã (INSTITUTO NACIONAL DE PESQUISAS ESPACIAIS, 2024). 

No que se diz respeito às metodologias de clustering utilizadas, no caso do clustering hierárquico, o modelo com k=12 é superior para entender as nuances da desigualdade, uma vez que ele vai além da simples dicotomia centro-periferia e identifica perfis de vulnerabilidade específicos (crise na saúde, na educação, na segurança, etc…), permitindo a formulação de políticas públicas mais focadas e eficazes para cada realidade. Já no modelo de K-Means, k=2 é eficaz para mostrar a divisão de São Paulo, confirmando a narrativa de uma cidade partida entre um centro expandido com melhores condições e uma vasta periferia com maiores carências. 

Embora as análises de clustering realizadas permitissem identificar padrões relevantes entre as subprefeituras com base nos indicadores disponíveis, evidenciando regiões com características socioeconômicas e de infraestrutura semelhantes, os silhouette scores ligeiramente baixos indicam que o estudo apresenta algumas limitações importantes. 

A principal está relacionada à escassez de dados em nível de subprefeitura, já que muitas informações estão disponíveis apenas para o município como um todo. Além disso, a heterogeneidade dos indicadores dificultou a formação de clusters bem definidos, reduzindo a precisão na identificação de grupos homogêneos. Outra limitação foi a sensibilidade dos métodos utilizados, por exemplo, o K-means exige a definição prévia do número de clusters e é mais adequado para dados com variância uniforme, enquanto o hierárquico pode sofrer com a influência de outliers.

Como próximos passos, recomenda-se a inclusão de outras técnicas de clustering, como o DBSCAN (RASCHKA; LIU; MIRJALILI, 2022), que pode lidar melhor com dados ruidosos e identificar grupos de formatos irregulares , além da aplicação de métricas adicionais para avaliação da qualidade dos clusters, como o índice Davies-Bouldin. Tais abordagens podem refinar a análise, proporcionando interpretações mais robustas e auxiliando na tomada de decisão baseada em dados. Além disso, também seria interessante a realização de análises preditivas que mostram como a composição dos clusters varia ao longo do tempo, sendo uma forma adicional de verificar a evolução da qualidade de vida nas subprefeituras.

## CONCLUSÃO

Este projeto demonstrou que é possível enxergar pontos de desigualdade entre os bairros da cidade de São Paulo com mais profundidade do que índices muito utilizados atualmente, como o IDH. Com base em 21 indicadores disponibilizados pelo ObservaSampa, sobre as subprefeituras de São Paulo, foram realizadas diversas análises fundamentadas em técnicas profissionais, como projeções temporais com regressão linear, clustering de k-means e clustering no modelo hierárquico. 

Diante disso, a partir de cada método foram obtidas informações bastante relevantes. Na regressão linear, observou-se que indicadores de infraestrutura (saneamento, UBS) e demográficos (longevidade) mostram tendências claras e são altamente previsíveis, ao contrário dos indicadores de vulnerabilidade social (pobreza, população de rua) e riscos ambientais (alagamentos), que apresentaram resultado muito mais voláteis, com baixo R². Nesse sentido, tais reflexos sustentam o uso de modelos simples para infraestrutura e demografia, e abordagens mais complexas para risco e vulnerabilidade. 

Já no modelo de clustering por k-means, foram encontrados uma divisão clara em dois agrupamentos, também divididos em locais com melhor infraestrutura e locais com menor desenvolvimento. Essa dicotomia sintetiza o mapa da desigualdade paulistana e oferece um corte claro para políticas universais com intensidades conflitantes. Por fim, no método de clustering hierárquico, com k=12, foi possível observar que essa dicotomia apresenta traços mais escondidos, pois, com essa maior segmentação hierárquica, surgiram dentro de cada grupo principal (antes determinado pelo modelo anterior) clustering específicos, como “Crise de Longevidade”, “Epicentro da Crise Múltipla”, “Elite e Alta Qualidade de Vida” ou “Prosperidade com lacunas na saúde infantil”, que combinam distintamente os indicadores. Essa segmentação mais elaborada orienta intervenções sob medida (ex.: focos em mortalidade infantil, escolaridade ou violência por cluster), aumentando a eficiência alocativa.

Em síntese, o trabalho cumpriu seu objetivo proposto: oferecer uma base empírica para priorização territorial e desenho de políticas mais direcionadas para os diferentes agrupamentos. Entretanto, também foram reconhecidas falhas e pontos de melhoria, como o baixo escore de silhouette para os clusterings, o que pode indicar uma complexidade suscetível a erros, apesar da linearidade dos agrupamentos com o contexto real de São Paulo.

## REFERÊNCIAS

- IBGE – INSTITUTO BRASILEIRO DE GEOGRAFIA E ESTATÍSTICA. Censo Demográfico 2022 [dados]. Rio de Janeiro: IBGE, 2022.
- INSTITUTO NACIONAL DE PESQUISAS ESPACIAIS – INPE. O que é El Niño e La Niña? Acesso à Informação – Perguntas Frequentes – Principais Produtos e Serviços – Previsão de Tempo e Clima. Brasília, 20 set. 2024. Atualizado em 24 set. 2024. Disponível em: [https://www.gov.br/inpe/pt-br/acesso-a-informacao/perguntas-frequentes/principais-produtos-e-servicos-do-inpe/previsao-de-tempo-e-clima/o-que-e-el-nino](https://www.gov.br/inpe/pt-br/acesso-a-informacao/perguntas-frequentes/principais-produtos-e-servicos-do-inpe/previsao-de-tempo-e-clima/o-que-e-el-nino). Acesso em: 13 ago. 2025.
- MINISTÉRIO DA SAÚDE (Brasil). TabNet – Gini, pesquisa por definição. Disponível em: [http://tabnet.datasus.gov.br/cgi/ibge/censo/cnv/ginisp.def](http://tabnet.datasus.gov.br/cgi/ibge/censo/cnv/ginisp.def). Acesso em: 17 ago. 2025.
- PREFEITURA DO MUNICÍPIO DE SÃO PAULO. GeoSampa. Disponível em: [http://geosampa.prefeitura.sp.gov.br/PaginasPublicas/_SBC.aspx](http://geosampa.prefeitura.sp.gov.br/PaginasPublicas/_SBC.aspx). Acesso em: 31 jul. 2025.