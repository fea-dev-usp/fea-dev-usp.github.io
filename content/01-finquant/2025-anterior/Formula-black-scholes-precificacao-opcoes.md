---
title: Fórmula de Black-Scholes para Precificação de Opções
tags:
  - nivel/avancado
  - trilha/finquant
---
_**Autores:** Guilherme Freitas
# 0. Índice

1. O QUE SÃO OPÇÕES
2. MODELO DE BACHLIER
3. DYNAMIC HEDGING DE THORP
4. MODELO DE BLACK-SCHOLES
5. MODELO DE FREITAS
6. COMPARAÇÃO DOS MODELOS
7. PRÓXIMOS PASSOS

# 1. O QUE SÃO OPÇÕES


## 1.1 Definição: 

Opções são um tipo de derivativo negociados no mercado financeiro. 

"Elas representam um contrato que dá ao seu titular o direito de comprar ou de vender um determinado ativo por um valor pré-determinado em uma data específica do futuro." 

Temos 2 tipos de opções: 

- Opção de Compra (Call) 
- Opção de Venda (Put) 

> [!INFO] 
> Nota: Para os cálculos usaremos somente as Opções de Compra.


## 1.2 Exemplo

Imagine que uma ação da Amazon custe hoje \$100. Você acredita que a ação irá se valorizar no futuro, por isso compra uma Call Option por \$10:

![[black-scholes-opcoes-1-1-exemplo.png]]

> [!INFO] 
> Nota: Vamos considerar as opções européias, em que só se pode vender ou comprar o Ativo-Objeto na data de vencimento, não durante todo o período.

## 1.3 Gráfico de Ganhos / Perdas

![[black-scholes-opcoes-1-3-ganhos-perdas.png]]

---

# 2. MODELO DE BACHELIER

Na época de Louis Bachelier (1870-1946), matemática francês, não existia uma forma precisa de precificar opções. Os acordos eram feitos com base em barganhas e intuições pessoais de quanto a opção deveria valer com base no ativo. Pela complexidade em prever o Mercado, Bachelier encontrou um modo de modelar o movimento das ações e outros ativos: **Probabilidade**.

## 2.1 Probabilidade

Imaginando que o preço de um ativo pudesse subir ou descer uma unidade a cada período de tempo, com probabilidade p=1/2, tornamos o preço de um ativo um processo estocástico: um Passeio Aleatório, assim podendo modelá-lo como um Movimento Browniano.

![[black-scholes-opcoes-1-4-probabiidade.png]]

## 2.2 Modelo

Utilizando a ideia de um Movimento Browniano Padrão (B), Bachelier modelou o preço do ativo no futuro t como um Movimento Browniano Aritimético:

$$ S_t = S_0 + \mu t + \sigma B_t \implies dS_t = \mu S_t dt + \sigma dW$$

A solução da equação pode ser abordada de várias formas diferentes, usando cálculo estocástico, Martingales, técnicas de Cálculo Diferencial, entre outras. Nessa apresentação consideraremos a fórmula definida por Bachelier inicialmente, sem considerar uma taxa livre de risco:

$$ C = (S - X)\Phi(D) + \sigma\sqrt{T}\phi(D) $$

Onde: $D = \frac{S - X}{\sigma\sqrt{T}}$ , $\Phi$ é a CDF e $\phi$ a PDF da Normal Padrão N(0,1).

> [!INFO] 
> Nota: A demonstração da fórmula e várias outras abordagens podem ser encontradas em: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3428994

---

# 3. DYNAMIC HEDGING DE THORP


## 3.1 Definição

Dynamic Hedging é uma estratégia que procura garantir o valor de uma carteira utilizando uma opção de venda sintética. Envolve o reequilíbrio das posições de cobertura à medida que as condições de mercado mudam.

## 3.2 Ideia de Thorp

Tendo uma opção V no seu portifólio e uma certa quantidade Δ do ativo S o qual ela está atrelada, podemos reduzir nossas perdas e por consequência o risco do portifólio:

$$ \Pi = V - \Delta S \implies \partial \Pi = \partial V - \Delta \partial S $$

O risco do portifólio π está atrelado ao seu drift ∂: uma medida de movimento de valor, por consequência, o drift do portifólio é proporcional ao drift de cada ativo.

## 3.3 Delta

O drift de uma opção e do ativo associado a ela estão relacionados, por isso, se considerarmos:

![[black-scholes-opcoes-3-3-delta.png]]


$$\partial \Pi = \partial V - \Delta \partial S$$

$$\partial \Pi = \partial V - \frac{\partial V}{\partial S} \partial S$$

$$\partial \Pi = \partial V - \partial V = 0$$

Com o drift do portifólio nulo, π se torna determinístico e não possui mais risco!

---

# 4. MODELO DE BLACK-SCHOLES

## 4.1 Retorno do Portifólio π

Desenvolvendo o mesmo portifólio π de Thorp e definindo dR como o retorno acumulado do portifólio, temos que:

$$ (1) \quad dR = dV - \frac{\partial V}{\partial S} dS $$

Pelo **Lema de Itô**:

$$ (2) \quad dV = \frac{\partial V}{\partial t} dt + \frac{\partial V}{\partial S} dS + \frac{1}{2} \sigma^2 S^2 \frac{\partial^2 V}{\partial S^2} dt $$

Substituindo (2) em (1):

$$dR = \frac{\partial V}{\partial t} + \frac{\partial V}{\partial S} dS + \frac{1}{2} \sigma^2 S^2 \frac{\partial^2 V}{\partial S^2} - \frac{\partial V}{\partial S} dS$$

$$dR = \frac{\partial V}{\partial t} + \frac{1}{2} \sigma^2 S^2 \frac{\partial^2 V}{\partial S^2}$$


## 4.2 Hipótese do Mercado Eficiente (EMH)

Sob a hipótese do mercado eficiente, ou de um mercado justo, um portifólio com risco 0  teria o retorno igual a Taxa Livre de Risco r, já que sem um risco adicional para justificar o aumento do retorno, não deveria ser possível nada além de r, ou seja:

$$ dR = r\Pi \to r\Pi = \frac{\partial V}{\partial t} + \frac{1}{2} \sigma^2 S^2 \frac{\partial^2 V}{\partial S^2} $$

Substituindo $\Pi$ (que é $V - \Delta S$, com $\Delta = \frac{\partial V}{\partial S}$), chegamos à **Equação Diferencial Parcial de Black-Scholes**:

$$ \frac{\partial V}{\partial t} + \frac{1}{2} \sigma^2 S^2 \frac{\partial^2 V}{\partial S^2} + rS \frac{\partial V}{\partial S} - rV = 0 $$

## 4.3 Precificação de Call e Put Option

A resolução da equação diferencial é complexa e demorada, por isso não será abordada nessa apresentação, somente as soluções finais:

Precificação de Call e Put Option:

$$ C = S\Phi(d1) - Xe^{-rT}\Phi(d2) $$

Precificação de Put Option:

$$ P = Xe^{-rT}\Phi(-d2) - S\Phi(-d1) $$
Onde:

$$ d1 = \frac{\ln\left(\frac{S}{X}\right) + \left(r + \frac{\sigma^2}{2}\right)T}{\sigma\sqrt{T}} \quad \text{e} \quad d2 = \frac{\ln\left(\frac{S}{X}\right) + \left(r - \frac{\sigma^2}{2}\right)T}{\sigma\sqrt{T}} = d1 - \sigma\sqrt{T} $$


> [!INFO] 
> Nota: A demonstração completa em detalhes pode ser vista em:  https://digitalcommons.liu.edu/cgi/viewcontent.cgi?article=1074&context=post_honors_theses


---

# 5. MODELO DE FREITAS

## 5.1 Modelagem Probabilística

Se Ri é o log-retorno do ativo no instante i, então o valor da ação no instante T é:

$$ S_T = Se^{\sum_{i=1}^{T} R_i} $$

A suposição sobre os retornos $R_i$:

$$ R_i \sim N(\mu, \sigma^2) \implies E(R_i) = \mu \quad \text{e} \quad Var(R_i) = \sigma^2 $$

A distribuição resultante para $S_T$:

$$ S_T \sim N\left(Se^{T\mu + \frac{T\sigma^2}{2}} ; S^2\left[e^{T\sigma^2} - 1\right]\left[e^{2T\mu + T\sigma^2}\right]\right) $$

> [!INFO] 
> Nota: Usaremos Estimadores de Máxima Verossimilhança para estimar os parâmetros populacionais.

## 5.2 Precificação da Opção

Assim como para Black-Scholes, em um mercado eficiente, ou "justo", o preço C de uma opção deve ser aquele que iguala o valor esperado de perda e de ganho:

![[black-scholes-opcoes-5-3-precificacao-opcao.png]]

## 5.3 Valor Esperado

A esperança de uma variável aleatória contínua é dada por:

$$E(Y) = \int_{y \in \Omega} y f(y) dy $$

Porém, no nosso caso, o retorno não é linear. Sendo s o valor do ativo no tempo T, X o Strike Price e C o valor pago pela opção: 

- Se o valor do ativo s **não superar o Strike Price X**, o prejuízo é o valor pago na opção, C. 
- Se o valor estiver **entre o Strike Price X e X + o valor pago C**, o prejuízo é a diferença entre o valor do ativo, o preço de exercício e o valor pago, ou seja, s - (X+C). 
- Se o valor s **superar o Strike Price + o valor da opção C**, temos um lucro de s - (X+C).

Graficamente:

![[black-scholes-opcoes-5-4-strike.png]]

$$ P_t = \int_{0}^{X} - C f(s) ds $$

$$ P_p = \int_{X}^{X+C} (s - (X + C)) f(s) ds $$

$$ L = \int_{X+C}^{\infty} (s - (X + C)) f(s) ds $$

## 5.4 Solução

Não existe um método analítico, ou seja, exato, que nos entregue C, já que as integrais podem ser impróprias. Por isso, encontraremos C numéricamente, minimizando a função D:

$$ D(C) = |L + P_t + P_p| $$

> [!INFO] 
> Nota: Também podemos modelar o preço futuro pelos retornos brutos, os resultados são os mesmos.

---

# 6. COMPARAÇÃO DOS MODELOS

![[black-scholes-opcoes-6-comparacao-modelos.png]]

---

# 7. PRÓXIMOS PASSOS

- Realizar os cálculos para a opção de venda (Put Option); 
- Adicionar a taxa de risk-free nas equações; 
- Personalização do período para cálculo da média de Retornos; 
- Escrever o artigo no Medium da nova proposta de precificação.

