---
title: FX Trading
tags:
  - nivel/basico
author: Leandro Santos
---
## 1. Motivação

Estratégias sistemáticas de FX baseadas em múltiplos fatores partem de uma premissa central: nenhum fator isolado consegue explicar de forma estável os retornos cross-sectionais de moedas ao longo do tempo. A literatura acadêmica e a prática de desks quantitativos consolidaram ao menos quatro prêmios de risco historicamente identificáveis em FX - carry, momentum, value e hikecycle (expectativa de política monetária) cada um com fundamento econômico distinto e com performance variável conforme o regime macroeconômico vigente. A combinação desses fatores em um único framework de alocação permite capturar diversas fontes de alpha simultaneamente, reduzindo a dependência de qualquer regime específico e produzindo um perfil de risco-retorno mais estável. Este projeto nasce da motivação de construir um modelo operacional de alocação em FX G10 que seja sistemático, replicável e fundamentado em dados macro públicos. Ao invés de decisões discricionárias baseadas em visão macroeconômica subjetiva, o objetivo é produzir mensalmente um portfólio dollar-neutral de moedas G10 com sinais derivados exclusivamente de variáveis observáveis: taxas de juros, yields de títulos soberanos, inflação e retornos de preço. O modelo foi desenvolvido internamente, com fatores próprios e otimização via Monte Carlo. O universo operacional é composto por sete moedas do G10 - EUR, GBP, JPY, CHF, AUD, CAD e SEK - todas negociadas contra o dólar americano. O portfólio é dollar-neutral: para cada posição comprada em uma moeda, há uma posição vendida de magnitude equivalente em outra, eliminando direcionalidade pura ao dólar e isolando o alpha relativo entre moedas. O rebalanceamento é mensal, no último dia útil de cada mês, com sinais gerados a partir dos dois fatores de maior robustez identificados na fase de diagnóstico: Momentum e Hike. 

Objetivo: Produzir um portfólio dollar-neutral de moedas G10 com Sharpe positivo fora da amostra (OOS), usando apenas sinais derivados de dados macro públicos.

### 1.1 Timeline dos Participantes

![[Pasted image 20260815181815.png]]

## 2. Dados e Universo Inicial

### 2.1 Fonte de Dados

![[Pasted image 20260815181849.png]]

### 2.2 Fundamentação Teórica

**Fator 1 - Momentum (Janela 21–63 dias)**

A hipótese de momentum em FX parte da evidência empírica de que moedas que se apreciaram nos últimos 1–12 meses tendem a continuar se apreciando no curto prazo. O mecanismo subjacente combina dois elementos: (i) ajuste lento do mercado a novas informações macroeconômicas, criando autocorrelação positiva nos retornos; e (ii) dinâmica de fluxo - gestores de carteira tendem a perseguir retornos recentes, amplificando tendências estabelecidas. No modelo, o sinal de momentum é calculado como o retorno acumulado diário de cada par FX, resampleado para frequência mensal, com janela de 21 a 63 dias otimizada via Monte Carlo a cada período. Moedas com momentum positivo relativo recebem posição longa; as com momentum negativo, posição curta.

**Fator 2 - Hike / Slope da curva de juros**

O fator Hike captura a expectativa do mercado sobre o ciclo de política monetária de cada banco central. O sinal é definido como o slope da curva de juros: 2Y yield − overnight rate. Um slope elevado sinaliza que o mercado precifica altas de juros futuras - o banco central está atrás da curva e deverá apertar a política monetária. Empiricamente, moedas de países com bancos centrais em ciclo de alta ou com expectativa de alta tendem a se apreciar no curto-médio prazo, pois atraem fluxo de carry e refletem diferencial de crescimento. A base teórica conecta-se à hipótese de paridade de juros descoberta (UIP), que na prática falha sistematicamente (o chamado forward premium puzzle), criando alpha explorável. O slope 2Y−overnight demonstrou ser o fator de maior Sharpe individual no diagnóstico, e o mais robusto em janelas longas (60m+). 

**Fator 3 - Carry Trade (testado, descartado)**

O carry trade é a estratégia mais documentada em FX: comprar moedas de juros altos e vender moedas de juros baixos, capturando o diferencial de taxa overnight. A justificativa teórica é a falha da UIP - se os juros altos não fossem compensados por depreciação cambial, haveria arbitragem de risco. Na prática, o carry apresenta retornos positivos na maioria dos períodos, mas está sujeito a crash risk severo: quando ocorre reversão de apetite ao risco global (risk-off), moedas de carry alto colapsam rapidamente. No modelo G10, tanto carry nominal (diferencial de overnight vs USD) 5 quanto carry real (ajustado pelo diferencial de CPI) apresentaram Sharpe OOS negativo no diagnóstico, em linha com literatura que aponta deterioração do fator após 2008. O carry foi descartado do modelo final. 

**Fator 4 - Value / Paridade de Poder de Compra (testado, não selecionado) **

O fator value em FX baseia-se na hipótese de reversão à média via Paridade de Poder de Compra (PPP): moedas significativamente sub ou sobrevalorizadas em relação ao nível de PPP tendem a reverter ao equilíbrio no médio-longo prazo. O sinal é construído comparando o nível de câmbio real com uma referência de PPP derivada de diferenciais de CPI acumulados. Embora teoricamente sólido, o value em FX opera em horizonte muito longo (3–5 anos), tornando-o ruidoso em modelos mensais. No diagnóstico, apresentou Sharpe OOS de +0.14 - com sinal positivo, mas alta variância de resultados entre janelas. Na comparação direta (Mom+Hike vs Mom+Value), o Mom+Value mostrou Max Drawdown superior (−21.3% vs −15.9%), penalizando a relação risco retorno. Foi descartado do modelo final em favor da combinação Momentum + Hike. 

**Universo G10 (modelo final)**

EUR, GBP, JPY, CHF, AUD, CAD, SEK - 7 moedas, portfólio dollar-neutral. 

OBS: NOK e MXN foram excluídos, não tem dados fáceis de captar de juros futuros deles.

## 3. Fase 1 - Diagnóstico de Fatores

Antes de construir o modelo combinado, cada fator foi testado individualmente em walk-forward OOS com janelas de 36 meses para entender o que de fato funciona no G10. 

Fatores testados 
	• Momentum: Retorno acumulado diário resampleado mensalmente (janela 21–63 dias) 
	• Hike: Slope da curva: 2Y yield − overnight rate (proxy para expectativa de alta de juros) 
	• Carry Nominal: Diferencial de taxa overnight vs USD 
	• Carry Real: Carry ajustado por CPI (diferencial real) 
	
	
Resultados individuais (walk-forward 36m, G10)

![[Pasted image 20260815182240.png]]

*OBS: O Hike individual tinha look-ahead de 1 mês na função de diagnóstico; o valor real em janelas mais curtas é aproximadamente −0.48. O sinal funciona bem em janelas de 60m+. 

Conclusão: Carry (nominal e real) foi descartado. Momentum e Hike são os fatores com sinal, sendo Hike o mais robusto. Value tem algum sinal mas com alta volatilidade de resultados.

## 4. Fase 2 - Full Model 4 Fatores

Com base no diagnóstico, testou-se um modelo combinando todos os 4 fatores (Mom + Hike + Carry + Value) em walk-forward OOS com janela de 60 meses e otimização Monte Carlo. 

O Full Model 4F apresentou:

![[Pasted image 20260815182407.png]]
![[Pasted image 20260815182425.png]]

Ainda que positivo, o desempenho era inferior ao Hike isolado e ao modelo com apenas Mom+Hike. O Carry continuou degradando o resultado.

#### Comparação Mom+Hike vs Mom+Value 

Em seguida, testou-se substituir o Carry pelo Value como terceiro fator:

![[Pasted image 20260815182509.png]]
![[Pasted image 20260815182521.png]]

Decisão: Simplificar para 2 fatores - Mom + Hike - que têm o melhor custo-benefício em termos de interpretabilidade, robustez e desempenho OOS.

## 5. Fase 3 - Tentativa de Expansão para EM

Com o modelo G10 funcionando, tentou-se expandir o universo para incluir moedas de mercados emergentes (EM), aumentando a diversidade de oportunidades.

### 5.1 Diagnóstico do universo EM

![[Pasted image 20260815182613.png]]
![[Pasted image 20260815182627.png]]

### 5.3 EM com Mom + Hike (16 moedas, sem NOK/MXN/HUF)

![[Pasted image 20260815182800.png]]

### 5.4 Comparação direta G10 vs G10+EM

![[Pasted image 20260815182825.png]]

### 5.5 Resultado consolidado da expansão EM

![[Pasted image 20260815182850.png]]

Por que o EM falhou - root cause 

  • 1. Sinal Hike invertido para EM O slope 2Y−overnight em moedas como BRL, TRY e CHINA é alto por causa de prêmio de risco país, não por expectativa de alta de juros. O modelo interpreta isso como sinal de 11 compra, mas essas moedas continuam caindo contra o dólar por razões estruturais (risco político, inflação, current account deficits). 
  
  • 2. Momentum negativo para EM (2011–2026) A dominância do USD no ciclo 2022–2024 (Fed hiking agressivamente) e carry crashes recorrentes destruíram qualquer sinal de momentum cross-sectional em EM. 
  
  • 3. Alta correlação intra-EM Todas as moedas EM movem juntas com o risk-off do USD. Isso elimina o benefício da seleção cross-sectional - todas sobem ou caem ao mesmo tempo, independente do sinal. Conclusão: expansão EM descartada definitivamente.

## 6. Fase 4 - Filtro VIX

Uma hipótese natural para o drawdown pós-2022 foi que o modelo estava sendo prejudicado por alta volatilidade de mercado. Testou-se um filtro VIX: zerar posições quando VIX > percentil 80 da janela rolling de 60 meses.

![[Pasted image 20260815183045.png]]

![[Pasted image 20260815183101.png]]

**Por que o filtro VIX não ajudou** 

O problema pós-2022 não é volatilidade de mercado - é regime de hiking sincronizado global. Em 2022–2024, Fed, ECB e BoE subiram juros juntos, eliminando a dispersão cross-sectional no sinal Hike. O VIX nesse período estava em níveis normais (não havia spike de volatilidade), então o filtro não ativava quando precisava e ativava em momentos errados. 

**Conclusão: filtro VIX descartado.**

## 7. Modelo Final G10 - Mom + Hike

![[Pasted image 20260815183202.png]]

Resultado OOS - Walk-Forward Completo (134 meses)

![[Pasted image 20260815183236.png]]

![[Pasted image 20260815183249.png]]

### Interpretação dos pesos Monte Carlo 

O Monte Carlo seleciona, a cada mês, o peso que maximizaria o Sharpe nos 60 meses anteriores. 

O padrão histórico revela: 

• 2015–2021: Momentum dominava (peso > 0.8 na maioria dos meses) 
• 2022–2026: Hike passou a dominar (~40–60% de peso), refletindo a maior relevância da diferenciação de política monetária no período pós-pandemia

## 8. Posicionamento Atual (Maio/2026)

Pesos MC selecionados para Maio/2026: Hike = 1.00, Momentum = 0.00

![[Pasted image 20260815183404.png]]

**Leitura Macro**

O modelo está comprando moedas de bancos centrais que ainda mantêm juros altos relativos (EUR, GBP, CAD) e vendendo JPY e CHF, cujos bancos centrais têm slopes 2Y−overnight menores. 

O CHF short reflete o ciclo de cortes do SNB; o JPY short ainda persiste apesar do início do hiking do BoJ, pois o slope 2Y−overnight japonês ainda é o menor do G10.

## 9. Fraqueza Conhecida e Limitações

Performance por período

![[Pasted image 20260815183611.png]]

Causa do drawdown pós-2022 

Em 2022–2024, Fed, ECB, BoE, SNB e Riksbank subiram juros simultaneamente em resposta à inflação pós-Covid. Isso eliminou a dispersão cross-sectional no sinal Hike - todas as moedas tinham slopes similares, o modelo não conseguia discriminar. À medida que os ciclos divergem novamente (BoJ subindo, Fed/ECB cortando), o sinal Hike deve recuperar poder discriminatório.

Limitações conhecidas

• Transaction costs não modelados - spread bid-ask estimado ~0.03% por trade pode reduzir Sharpe em ~0.05–0.10 

• NZD não testado - única moeda G10 ausente; pode ser extensão natural 

• Modelo não tem filtro de regime - opera em todos os meses, incluindo períodos de baixa dispersão 

• 2Y yields são compilação manual - risco de erro de dados nas atualizações mensais

## 10. Próximos Passos

![[Pasted image 20260815183901.png]]

## 11. Infraestrutura e Dados

![[Pasted image 20260815183935.png]]

![[Pasted image 20260815183951.png]]

**Fonte e APIs** 

![[Pasted image 20260815184027.png]]

Como rodar 

• Abrir g10_final.ipynb 

• Rodar todas as células em sequência (Kernel → Restart & Run All) 

• A última célula imprime o posicionamento do mês corrente
