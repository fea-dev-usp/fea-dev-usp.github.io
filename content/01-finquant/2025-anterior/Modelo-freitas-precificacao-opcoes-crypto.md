---
title: Modelo de Freitas para Precificação de Opções de Compra no Mercado de Criptomoedas
tags:
  - nivel/avancado
  - trilha/finquant
---

*Autores:* André Pennini, Guilherme Freitas, Theo Borten

# 1. OVERVIEW

## Objetivo: 

Desenvolver um novo modelo de precificação de opções de compra para o mercado de criptomoedas e compará-lo com o modelo benchmark Black-Scholes.

## Questões de pesquisa:

- Porque criar um novo modelo?
- Qual a base teórica que sustenta o modelo?
- O novo modelo reflete adequadamente os preços do mercado?

## Metodologia:

- Modelagem probabilística;
- Adequação das suposições;
- Ideia de preço justo;
- Precificação

## Inovação

Criação de um modelo de precificação de opções com interpretação simples e que reflete os preços reais do mercado.

# 2. MOTIVAÇÃO E PROBLEMA

*OPÇÕES*

"Contrato que dá ao seu titular o direito de comprar ou de vender um determinado ativo (com preço S) por um valor pré determinado, chamado preço de exercício (X), em uma data específica do futuro (T períodos à frente)."

*MODELO BLACK-SCHOLES*

$$
C = S\Phi(d_1) - Xe^{-rT}\Phi(d_2)
$$

$$
d_1 = \frac{\ln\left(\frac{S}{X}\right) + \left(r + \frac{\sigma^2}{2}\right)T}{\sigma\sqrt{T}}
\quad \text{e} \quad
d_2 = \frac{\ln\left(\frac{S}{X}\right) + \left(r - \frac{\sigma^2}{2}\right)T}{\sigma\sqrt{T}}
= d_1 - \sigma\sqrt{T}
$$

Utilizado para precificação de opções financeiras. Baseado na hipótese de um mercado eficiente, o modelo assume que os preços dos ativos seguem um movimento browniano geométrico, com retornos logarítmicos normalmente distribuídos. Pressupõe a inexistência de arbitragem, a possibilidade de negociação contínua, um ativo subjacente sem pagamentos de dividendos, taxas de juros constantes, e volatilidade do ativo subjacente constante. A solução do modelo é derivada da equação diferencial parcial de Black-Scholes, considerada a base para várias extensões e análises financeiras modernas 

*BLACK-SCHOLES PARA O MERCADO DE CRIPTOATIVOS*

Embora renomado nos mercados tradicionais, o modelo de Black Scholes enfrenta limitações significativas no mercado de cripto, com características possivelmente inadequadas para capturar a complexidade desses ativos:

- *Mercado Ineficiente:* Os preços de criptoativos são fortemente influenciados por especulação, emoções e eventos exógenos, violando a hipótese de eficiência de mercado, base do Black-Scholes.

- *Liquidez e Microestrutura*: Movimentos abruptos de preço em mercados pouco líquidos não são considerados pelo modelo

- *Complexidade do Modelo*: Por possuir equações diferenciais e modelos estocásticos, Black-Scholes possuí um grau de complexidade que dificulta a interpretação por parte do mercado, funcionando como uma ferramenta enigmática

- *Risk-free rate*: No mercado de criptoativos, a taxa livre de risco (risk-free rate) pode não ser o suficiente como desconto, dada a alta volatilidade e incerteza única desse mercado.

*CARACTERÍSTICAS QUE BUSCAMOS NO NOVO MODELO DE PRECIFICAÇÃO DE OPÇÕES PARA O MERCADO DE CRIPTO*

- *Simplicidade e Transparência*: Deve ser compreensível e acessível, evitando a dependência de equações diferenciais e modelos estocásticos complexos, garantindo maior aplicabilidade no mercado.

- *Adaptação ao Mercado Ineficiente*: Precisa lidar com especulação, emoções e choques exógenos, sem pressupor que os preços refletem todas as informações disponíveis.

- *Taxa de Desconto Realista*: Em vez de depender exclusivamente de uma taxa livre de
risco, o modelo deve ajustar-se à realidade volátil e especulativa do mercado de
criptoativos

# 3. DADOS E METODOLOGIA

*DADOS*

- *ATIVO - IBIT*

iShares Bitcoin Trust ETF (IBIT), é um produto financeiro negociado em bolsa que permite acesso ao bitcoin de forma  conveniente, sem a necessidade de compra e custódia direta da criptomoeda, oferecendo segurança, por meio da parceria com a BlackRock e Coinbase Prime, e operações com opções.

- *RISK - FREE RATE*

A taxa livre de risco foi obtida por meio de raspagem de dados da plataforma YCHARTS. Foi considerado a taxa do título de 10 anos do tesouro americano.

- *SÉRIE HISTÓRICA*

A série histórica das cotações do IBIT foi extraída via API do Yahoo Finance, abrangendo o período de 11/01/2024 a 23/11/2024. Além disso, foram coletadas todas as negociações de opções de compra de 19/11/2024 a 23/11/2024, utilizando a mesma API.

*MODELAGEM PROBABILÍSTICA*

Se \(R_i\) é o log-retorno do ativo no instante \(i\) e \(S\) o preço no tempo \(0\), então seu valor no instante \(T\) é:

$$
S_T = S e^{\sum_{i=1}^{T} R_i}
$$

Supondo que a cada período de tempo o retorno do ativo é independente do anterior e é adequadamente explicado por:

$$
R_i \sim \mathcal{N}(0,\sigma^2)
$$

Então, pode-se mostrar que:

$$
S_T \sim \text{LogNormal}\left(\ln(S),\, T\sigma^2\right)
$$

*Obs:* chamaremos de \(f(s)\) a função densidade de probabilidade de \(S_T\).

*ADEQUAÇÃO DAS SUPOSIÇÕES*

- **Independência:** Aceita com valor-p de 36,64% no Teste Ljung-Box. 
- **Normalidade:** Para confirmar a suposição de normalidade foi utilizado o teste de Kolmogorov-Smirnov (valor-p = 0.27) e o QQ-plot na Figura 1:

![[freitas-opcoes-crypto-fig1.png]]

**Média dos log-retornos = 0:** Suportada pelo p-valor = 0.16 do teste t de médias.

*PRECIFICAÇÃO DAS OPÇÕES*

Preço Justo: Possuindo a distribuição dos preços no futuro, o preço justo C de uma opção de compra, com o preço de exercício X, é tal que a esperança estatística de lucro da opção é igual à de perdas, como mostra a Figura 2:

![[freitas-opcoes-crypto-fig2.png]]

Precificação: Utilizando a definição de esperança na probabilidade, construímos as quantidades: 
- L: A esperança de lucro ao exercer a opção; 
- $P_p$  : Esperança de perda parcial, ou seja, a perda financeira ao exercer a opção. 
- $P_t$  : Esperança da perda do valor total pago na opção, i. e., quando não se exerce o direito de compra adquirido. Graficamente na Figura 3 e algébricamente na Figura 4.

![[freitas-opcoes-crypto-fig3.png]]

$$P_t = \int_{0}^{X} -C f(s) ds$$
$$P_p = \int_{X}^{X+C} (s - (X+C)) f(s) ds$$
$$L = \int_{X+C}^{\infty} (s - (X+C)) f(s) ds$$


Não existe um método analítico, ou seja, exato, que nos entregue C, já que as integrais podem ser impróprias. Por isso, encontraremos C numericamente, minimizando a função D:
$$D(C) = |L + P_t + P_p|$$

Em seguida, aplicaremos o fator de desconto dado por:
$$e^{-r.T.ln(S)}$$

![[freitas-opcoes-crypto-fig6.png]]

![[freitas-opcoes-crypto-fig7.png]]

Os modelos de Freitas e Black-Scholes apresentam uma forte correlação (0,9933), demonstrando que o modelo proposto pela equipe oferece precificações bastante alinhadas com o padrão de mercado estabelecido, visível na Figura 5. Diferenças entre os preços dos contratos observados e os modelos sugerem que o de Freitas incorpora particularidades que podem melhorar a precisão em contextos específicos, como ambientes de alta volatilidade ou condições únicas do mercado de criptomoedas. Além disso, ambos os modelos apresentaram comportamentos similares em relação a variáveis como preço de exerício (Figura 6) e dias até a expiração (Figura 7), reforçando a proximidade das suas abordagens e sugerindo que o modelo de Freitas é uma alternativa promissora ao Black-Scholes.

![[freitas-opcoes-crypto-fig5.png]]

## 4. Resultados

Para avaliar o desempenho do modelo, utilizamos dados reais de contratos de opções de compra (call) do IBIT com diferentes datas de vencimento, comparando os preços previstos com os preços reais de mercado. Com base no cálculo do Erro Absoluto Médio (EAM), constatamos que o modelo de Freitas apresenta maior precisão, com um EAM menor em comparação ao modelo Black-Scholes, como é apresentado na Tabela 1. Essa diferença é corroborada pela análise visual na Figura 8, onde os pontos representando o modelo de Freitas (em rosa) estão mais próximos do eixo (zero), indicando menores discrepâncias em relação aos preços efetivamente negociados.

![[freitas-opcoes-crypto-fig8.png]]

![[freitas-opcoes-crypto-tb1.png]]

## 5. Conclusão

**Precisão** 
A análise comparativa entre os modelos de Freitas e Black-Scholes revela que o novo modelo não apenas alcança uma precisão superior, conforme indicado pelo Erro Absoluto Médio (EAM) mais baixo, mas também mantém uma forte correlação com o modelo tradicional. A capacidade do modelo de Freitas de incorporar nuances do mercado de criptomoedas pode torná-lo uma ferramenta valiosa para a precificação de opções nesse contexto específico, especialmente em ambientes de maior volatilidade. Em resumo, os resultados sugerem que o modelo de Freitas oferece uma alternativa robusta e eficaz ao BlackScholes, com potencial para fornecer estimativas mais precisas em cenários de mercado dinâmico.

**Compatibilidade com Mercado** 
A forte correlação entre o modelo de Freitas e o Black-Scholes sugere que a implementação do nosso modelo pode ser realizada de forma simples e direta, pois ele é altamente compatível com o que já é operado no mercado financeiro. A proximidade entre os dois, visível na análise de variáveis como o preço de exercício e os dias até a expiração, reforça que o modelo de Freitas pode ser adotado sem grandes adaptações nos sistemas existentes, oferecendo uma alternativa de precificação que preserva a consistência e a familiaridade com os padrões tradicionais do mercado.

**Trabalho Futuro**
Para aprimorar a análise, sugerese a ampliação do conjunto de dados, incluindo opções de outros ativos digitais ou expandindo o período analisado, permitindo avaliar sua robustez em diferentes cenários de mercado. Além disso, o modelo pode ser aplicado diretamente no mercado em estratégias como arbitragem, explorando diferenças de precificação para gerar oportunidades de lucro.