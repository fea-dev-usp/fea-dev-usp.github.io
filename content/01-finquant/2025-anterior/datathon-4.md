---
title: Previsibilidade do Prêmio de Risco em Criptomoedas com Indicadores Técnicos
tags:
  - nivel/avancado
  - trilha/finquant
---
_**Autores:** Guilherme Vinicius Afonso Dias de Freitas · Gustavo Yamachi · Matias Lima_

_**Orientador:** Leandro dos Santos Maciel_

<div style="text-align: center;">

  <img src="Pasted image 20260322094834.png" width="100">

</div>

# 1. Overview


### **Objetivo:**

- Avaliar a previsibilidade do **prêmio pelo risco de criptomoedas** utilizando indicadores técnicos e relacionar essa previsibilidade com os **níveis de sentimento de mercado**.
    

### **Questões de pesquisa:**

- Indicadores técnicos têm capacidade de prever o prêmio pelo risco de criptomoedas?
    
- O sentimento de mercado influencia na previsibilidade do prêmio de risco?
    
- Índices de sentimento mais robustos capturam melhor essa potencial relação preditiva?
    

### **Metodologia:**

- Dados do **Bitcoin** e construção de **regressões bi-variadas** da literatura de _equity risk premium_;
    
- **Indicadores técnicos** de médias móveis, momentum e volume como regressores;
    
- Construção de **índice de sentimento** com **PCA** e raspagem de dados (_web scraping_);
    
- Desmembramento da capacidade preditiva de acordo com níveis de sentimento.
    

### **Inovação:**

- Mensuração da previsibilidade do prêmio pelo risco em criptos com indicadores técnicos;
    
- Criação de um novo índice de sentimento para criptomoedas — **SenticCrypto**;
    
- Qualificação da qualidade das previsões para distintos níveis de sentimento.
    

---

# 2. Fundamentação teórica

O  Prêmio  pelo  Risco  de  um  ativo  é  o  seu retorno esperado ajustado ao risco (em excesso à taxa livre de risco). Previsão mais acurada do prêmio pelo risco é importante para:

- Precificação de ativos/derivativos; Alocações mais eficientes de portfólios;

- Avaliação de performance da gestão em mercados financeiros.

- A  literatura  apresenta  modelos  de  regressão com Indicadores técnicos e variáveis fundamentais (WELCH & GOYAL, 2008) para previsão do prêmio pelo risco.

![[datathon-4-pr-risk.png]]

### 2.1 Previsão do Prêmio de Risco de criptomoedas: 
- literatura não considera a abordagem clássica; 
- não há indicadores fundamentalistas (quais os fundamentos econômicos das criptos?); 
- Espera-se que os indicadores técnicos possuam um papel relevante em sua previsibilidade.

Indicadores técnicos, por sua vez, são considerados adequados para prever o prêmio pelo risco dado que:

- Existe uma assimetria temporal no acesso à novas informações pelos investidores.
- As informações são processadas e decisões são tomadas em tempos diferentes. Investidores são heterogêneos.
- Os mercados enfrentam momentos de under e overreaction
- O sentimento dos investidores pode desviar os preços dos ativos de seu valor fundamental.

### 2.2 Hipótese de Pesquisa

Se o sentimento dos investidores provoca ineficiências nos preços (desvios do valor fundamental), as condições do mercado (nível de sentimento) podem alterar a qualidade preditiva dos prêmio pelo risco utilizando indicadores técnicos, que mensuram transmissão do efeito sentimento nos preços dos ativos. Bali et al. (2017) observaram que investidores com diferentes atitudes perante a incerteza agem distintamente no mercado. 

Aqueles menos avessos permanecem ativos, enquanto os mais avessos tendem a se retrair Cujean e Hasler (2017) apontam que a previsibilidade do mercado em tempos de incerteza é afetada pela discordância entre investidores. 
Quando a incerteza cresce, as opiniões se polarizam, impactando a eficácia de e stratégias baseadas em perseguição de tendências, como o uso de indicadores técnicos. 

No estudo de Fernandez et al. (2023), verificou-se que indicadores técnicos possuem maior poder preditivo em períodos de menor incerteza. 

Com base nessa literatura, surge uma questão crucial: a previsibilidade do Prêmio de Risco é influenciada pelo nível sentimento do mercado? Se sim, qual o impacto do monitoramento do nível de sentimento do mercado para a tomada de decisões de investimento em criptomoedas?

![[dathaton-4-pr-fear-greed.png]]

![[dathaton-4-pr-serie-historica-fear-greed.png]]

---
## 3. Dados e Metodologia

**Dados**: extração da série histórica das cotações semanais do Bitcoin, por meio da API do Yahoo Finance no período de 02/02/2018 a 30/06/2023. Embora a literatura utilize dados mensais, utilizamos dados semanais para não negligenciar a considerável variabilidade ao longo dos meses.

São consideradas regressões bi-variadas, com indicadores técnicos como variáveis preditoras. Consideramos quatorze indicadores técnicos conforme delineado por Neely et al. (2014) e Fernández et al. (2023). Esses indicadores são fundamentais em estratégias de seguimento de tendências e incluem elementos como médias móveis (MA), volu me (VOL) e análise de mom entum (MOM). Os indicadores são construídos com base em sinais de compra e venda (buy/sell - BS), onde P é o preço do BTC
  
**Média Móvel (MA)**
$$MA_{j,t} = \frac{1}{j} \sum_{i=0}^{j-1} P_{t-i}$$

**On-Balance Volume (OBV)**
$$OBV_t = \sum_{k=1}^{t} VOL_k \cdot D_k$$

**Média Móvel do OBV**
$$MA_{j,t}^{OBV} = \frac{1}{j} \sum_{i=0}^{j-1} OBV_{t-i}$$

**Sinal de Compra/Venda 1 (Cruzamento de Médias Móveis)**
$$BS_{1,t} = \begin{cases} 1 & \text{if } MA_{s,t} \ge MA_{l,t} \\ 0 & \text{if } MA_{s,t} < MA_{l,t} \end{cases}$$

**Sinal de Compra/Venda 2 (Momentum de Preço)**
$$BS_{2,t} = \begin{cases} 1 & \text{if } P_t \ge P_{t-m} \\ 0 & \text{if } P_t < P_{t-m} \end{cases}$$

**Sinal de Compra/Venda 3 (Cruzamento de Médias Móveis do OBV)**
$$BS_{3,t} = \begin{cases} 1 & \text{if } MA_{s,t}^{OBV} \ge MA_{l,t}^{OBV} \\ 0 & \text{if } MA_{s,t}^{OBV} < MA_{l,t}^{OBV} \end{cases}$$

Ao avaliar o Risk Premium do Bitcoin, enfrentamos o desafio de estabelecer uma taxa livre de risco apropriada para esta criptomoeda devido à sua natureza única. Para contornar essa dificuldade, escolhemos adotar a taxa de retorno dos títulos do Tesouro dos Estados Unidos com vencimento de um mês como proxy. As taxas foram extraídas do site do FED. O prêmio pelo risco é:

**Prémio de Risco (Risk Premium)**
$$Rp = E(r) - Rf$$

Conforme apontado por Cujean e Hassler (2017), o conceito de 'previsibilidade' emerge de opiniões divergentes sobre os fundamentos do mercado. Esta previsibilidade tende a ser mais acentuada durante períodos desfavoráveis do mercado. Portanto, para tentar identificar esses períodos mais críticos no mercado, utilizamos o 'Crypto Fear & Greed Index'. Indice que tenta medir o sentimento por meio de 6 proxies: Volatility, Surveys, Volume, Social Media, Dominance e Trends.

Para delinear claramente os períodos de baixo e alto sentimento no mercado, adotamos uma abordagem de categorização do indicador em intervalos distintos. Esses intervalos são: 'Greed' , 'Neutral' e 'Fear'. Cada categoria representa diferentes níveis de sentimento no mercado. Com isso, as regressões preditivas foram estimadas e o $R^2$ desmembrado para períodos distintos de sentimento (disentangled $R^2$ )

**Regressões bi-variadas e $R^2$ disentangled (IN-SAMPLE):**

$$r_t = \gamma_t + \lambda_t x_{t-1} + \epsilon_t$$
*Sendo $x_t$ o sinal (BS) dos ind. técnicos.*

$$R^2_c = 1 - \frac{\sum_{t=1}^T \epsilon_t^2 I_t^c}{\sum_{t=1}^T I_t^c(r_t - \bar{r}_t)^2}$$
*C = Fear, Neutral, Greed | $\epsilon_t$ é o erro de estimação*

**Regressões bi-variadas e $R^2$ disentangled (OUT-OF-SAMPLE):**

$$\hat{r}_{i,t} = \gamma_t + \lambda_t \hat{x}_{i,t-1}$$

$$\bar{r}_t^{HA} = \frac{1}{t} \sum_{j=1}^{t} r_j$$
*$\bar{r}_t^{HA}$ benchmark Média Histórica.*

$$R^2_{OS}(c) = 1 - \frac{\sum (r_t - \hat{r}_t)^2 I_t^c}{\sum (r_t - \bar{r}_t^{HA})^2 I_t^c}$$
*C = Fear, Neutral, Greed*


Com o objetivo de aprimorar a qualidade na mensuração do sentimento do mercado, visamos desenvolver um indicador mais preciso. Propomos a criação de um novo estimador que refinaria a quantificação das nuances sentimentais. Isso seria alcançado pela incorporação de informações relevantes, como as notícias, permitindo uma análise mais abrangente e precisa das tendências do mercado

A construção do corpus foi realizada por meio de um algoritmo de web scraping que interage com o navegador do Google para coletar as notícias mais relevantes de uma determinada palavra-chave em um intervalo de tempo específico. Milhares de noticias foram coletadas. Intervalo: 02/02/2018 a 30/06/2023

Após a captação das informações, procedemos com o processamento e a limpeza dos dados, removendo quaisquer inconsistências ou ruídos presentes. Em seguida, iniciamos uma série de análises qualitativas com o objetivo de avaliar a qualidade do nosso corpus.

Uma das abordagens que utilizamos para explorar os dados foi o Topic Modeling que é uma técnica de clusterização que utiliza embeddings para explorar e identificar tópicos em grandes volumes de texto. Sendo eficaz para extrair temas recorrentes e analisar padrões em dados textuais.

Após a fase de coleta e pré-processamento dos dados, efetuamos a aplicação do modelo de linguagem denominado finBERT. Este modelo, baseado no BERT, foi estruturado especificamente para a tarefa de análise de sentimentos em contextos financeiros. A sua incorporação no nosso projeto foi concretizada por meio da integração da API da plataforma Hugging Face, que oferece suporte para trabalhar com modelos de Processamento de Linguagem Natural, permitindo que nossas operações de análise de sentimento fossem executadas e o sentiment score fosse extraído

Após calcular os escores de sentimento, conduzimos uma Análise de Componentes Principais (PCA) entre esses escores e o Fear and Greed Index. A PCA é uma técnica que pode ajuda a melhorar índices, por meio da redução da redundância e do ruído nos dados, identificando padrões ocultos, simplificando a visualização e melhorando a precisão. Ela alcança isso ao reduzir a dimensionalidade dos dados e destacar as variáveis mais significativas, tornando o índice mais informativo e útil para análises. Com base na fusão, via PCA, do Fear and Greed Index com os escores gerados, criou-se o indicador proposto neste trabalho: o SenticCrypto. As análises também serão conduzidas utilizando esse novo indicador

## 4. Resultados - In Sample com Fear & Greed Index

![[dathaton-4-pr-tabela1.png]]

A análise in-sample avalia se existe capacidade explicativa dos indicadores técnicos para o prêmio pelo risco. A Tabela 1 mostra uma maioria de R² expressivos, indicando que há poder de previsão dos indicadores técnicos sobre o prêmio pelo risco do mercado de criptomoedas - valores são maiores que 0,5%, benchmark da literatura. Em condições distintas de sentimento, Fear, Neutral e Greed, os indicadores técnicos têm maior capacidade preditiva em momentos de Greed Market, conforme Tabela 2 e Gráfico 1, que apresentam o R² desmembrado. Em períodos de Fear Market, a performance dos indicadores técnicos é deteriorada.

![[dathaton-4-pr-grafico1.png]]

![[dathaton-4-pr-tabela2.png]]

Utilizando o índice SenticCrypto desenvolvido, vemos um alinhamento com os resultados anteriores, porém, com R² maiores, como mostra a Tabela 3, representando um poder preditivo maior dos indicadores técnicos nos níveis de sentimento de mercado avaliados. O Gráfico 2 destaca o melhor desempenho dos indicadores técnicos nos níveis de sentimento Greed e Neutral, confirmando a capacidade preditiva nesses momentos, sendo mais relevante na categorização dos níveis de sentimento decorrentes do SenticCrypto Index, proposto neste trabalho.

![[dathaton-4-pr-grafico2.png]]

![[dathaton-4-pr-tabela3.png]]

Os resultados out-of-sample avaliam a qualidade das previsões realizadas com base nos indicadores técnicos como preditores. A Tabela 4 apresenta os R², total e desmembrado para os níveis de sentimento, categorizados de acordo com o índice SenticCrypto, que performou melhor na análise in-sample - os resultados usando o Fear & Greed Index são qualitativamente similares. Valores positivos (em destaque) dos R² indicam que os indicadores técnicos têm melhor desempenho preditivo do que o benchmark (média histórica) para a previsão do prêmio pelo risco. Quando o sentimento é classificado com o índice SenticCrypto, os indicadores técnicos mostraram maior poder preditivo em períodos de neutralidade do sentimento de mercado. E, quando performam bem em momentos de Fear e Greed, as melhores previsões são associadas aos períodos de Greed Market. Os indicadores técnicos que superam a média histórica com mais frequência são MA(2 ,9), MA(3, 12) e VOL(3, 12).

![[dathaton-4-pr-tabela4.png]]

## 5. Considerações Finais

CONCLUSÕES
- Indicadores técnicos apresentam poder preditivo para o prêmio pelo risco no mercado de criptomoedas, em alinhamento com Baker e Wurgler (2006); 
- Em períodos de Neutral e Greed Markets, melhores previsões são obtidas; 
- O índice SenticCrypto mostrou-se capaz de categorizar adequadamente o nível de sentimento de mercado, dada a maior capacidade preditiva dos indicadores técnicos em períodos de Neutral e Greed Markets quando comparada com a utilização do Crypto Fear & Greed Index.

IMPLICAÇÕES

Teóricas - Atesta a previsibilidade do prêmio pelo risco com o uso de indicadores técnicos, em linha com a literatura (Neely et al., 2014, Fernandéz et al., 2023), mas para criptomoedas. Valida também a hipótese de que o nível de sentimento de mercado está associado com uma maior/menor previsibilidade do prêmio pelo risco. 

Práticas - Mostra que o monitoramento do sentimento do mercado de criptomoedas, por meio de índices robustos, é relevante para agentes de mercado que estão interessandos em utilizar previsões mais acuradas do prêmio pelo risco em seus processos de tomada de decisão.

**Trabalhos futuros **

- Desenvolver uma taxa de retorno livre de riscos para criptomoedas; 
- Avaliar estatisticamente os resultados, a fim de definir quais indicadores técnicos possuem poder preditivo estatisticamente relevante; 
- Mensurar os resultados em termos econômicos, com a utilização das previsões na composição de carteiras e na gestão de riscos.

## 6. Anexos

![[dathaton-4-pr-anexo1.png]]

![[dathaton-4-pr-anexo2.png]]

![[dathaton-4-pr-anexo3.png]]

![[dathaton-4-pr-anexo4.png]]