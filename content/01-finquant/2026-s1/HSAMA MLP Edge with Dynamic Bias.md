---
title: HSAMA MLP Edge with Dynamic Bias
tags:
  - nivel/avancado
  - trilha/finquant
---
_**Autor:** David  Leati_

_**Repositório:** [link](https://github.com/DavidLeati/project_C)_

# HSAMA: quando uma teoria de mercado vira uma arquitetura testável

## Uma leitura validativa da HSAMA aplicada a trading quantitativo

Existe uma diferença importante entre ter uma ideia promissora e ter uma teoria que pode ser testada.

Na HSAMA, a teoria central é simples de formular, mas difícil de executar: mercados não estacionários não deveriam ser tratados por um modelo fixo, treinado para repetir uma associação estática entre features e retorno. Se o regime muda, a própria política interna do modelo precisa mudar. Não apenas os pesos finais. Não apenas a saída. A forma como o modelo propaga informação também deveria ser sensível ao contexto.

Essa é a aposta da arquitetura HSAMA no repositório: uma meta-arquitetura neural em grafo, na qual hiper-redes geram modulações dinâmicas para as arestas, guiadas por contexto temporal, memória multi-escala e surprisal. A pergunta deste texto não é "o modelo ganhou dinheiro?". Essa pergunta vem depois. A pergunta mais importante aqui é:

**a teoria foi transformada em um sistema falsificável, executável e empiricamente auditável?**

A resposta curta é: sim, no nível de pesquisa. O projeto já valida várias partes estruturais da teoria. Mas os resultados operacionais ainda mostram que a transição de teoria para capital real continua incompleta.

***
## A tese teórica

A teoria por trás da HSAMA pode ser organizada em cinco hipóteses.
### 1. Mercados mudam de regime

Um candle de 15 minutos não tem o mesmo significado em todos os contextos. Um movimento pequeno pode ser irrelevante em baixa volatilidade e altamente informativo depois de uma compressão de range. Um rompimento pode ser continuação em um regime e armadilha em outro.

Logo, a representação do modelo precisa ser condicional ao contexto.
### 2. O contexto relevante é multi-escala

Trading em 15m não é apenas um problema de 15m. A decisão local carrega informação de horizontes maiores: 1h, 4h, 1d, funding, BTC, ETH, sessão do dia, volume e microestrutura.

O modelo, portanto, não deveria depender apenas de uma janela única de features. Ele deve observar memória curta, média e longa.
### 3. Eventos surpreendentes importam mais que eventos comuns

Em séries financeiras, as amostras mais valiosas raramente são as mais frequentes. Regimes de choque, viradas e perdas anormais carregam informação que um treino uniforme tende a diluir.

Surprisal vira então um sinal operacional: quando a perda do modelo excede seu padrão histórico, esse evento deve influenciar mais a adaptação.
### 4. Prever direção sem incerteza é insuficiente

Um previsor que retorna apenas "alta" ou "baixa" está escondendo a parte mais importante da decisão: o grau de confiança. A HSAMA evolui para previsores probabilísticos, emitindo `mu` e `sigma`, para que o trader consuma sinais ajustados por risco.

A tese não é "prever o retorno perfeitamente". É produzir uma estimativa de edge normalizada por incerteza.
### 5. O objetivo final não é acurácia, é PnL líquido sob custo

Em trading, acertar direção e perder dinheiro é uma falha comum. Custos, giro, alavancagem, drawdown e distribuição de posição importam tanto quanto o retorno bruto.

Por isso, a teoria exige uma função de perda que penalize comportamento operacional ruim, não apenas erro de regressão.

***
## Como a teoria virou arquitetura

A HSAMA não implementa essa tese como um único modelo grande e opaco. Ela separa a teoria em componentes testáveis.
### O grafo HSAMA

No centro está `src/models/hsama.py`. A classe `HSAMA` constrói um grafo k-regular e executa passagem de mensagens entre nós. A parte teoricamente relevante é que as arestas não são apenas pesos fixos. Cada aresta possui uma MLP local com viés dinâmico, gerado por hiper-redes setoriais a partir do contexto.

Esse detalhe importa. A teoria diz que o regime de mercado deve mudar a forma de computar o sinal. A implementação faz isso ao gerar DNA por aresta:

- T0 codifica contexto e surprisal;
- hiper-redes geram modulações dinâmicas;
- T1 executa a passagem de mensagens no grafo;
- a saída final é produzida depois da agregação dos estados dos nós.

Isso valida a primeira parte da teoria: a arquitetura não é apenas uma MLP com features temporais. Ela tem um mecanismo explícito de reconfiguração contextual.
### Memória multi-escala

Em `src/runtime/multiscale.py`, o projeto implementa `MultiScaleT0Builder`. Cada escala temporal usa um encoder GRU próprio. As escalas podem representar ritmos diferentes, como:

- `fast`;
- `slow`;
- `micro`;
- `short`;
- `medium`.

O trader usa três escalas internas. Os previsores usam duas escalas por timeframe. Isso cria uma estrutura em que a decisão local recebe informação de históricos com frequências diferentes.

Essa parte valida a segunda hipótese: a teoria multi-escala não ficou apenas em discurso; ela está codificada como contrato de runtime.
### Surprisal e replay

Em `src/runtime/surprisal.py`, o sistema calcula surprisal como excesso positivo de perda em relação a uma média e variância móveis. Em `src/runtime/replay.py`, eventos podem ser armazenados em um buffer priorizado.

Isso cria um ciclo de aprendizado orientado por erro inesperado:

1. o modelo observa uma amostra;
2. calcula perda;
3. estima se aquela perda foi surpreendente;
4. usa essa informação para priorizar replay ou modular a política.

Essa parte valida a terceira hipótese: eventos raros e informativos recebem um canal arquitetural próprio.
### Previsão probabilística

No engine walk-forward, cada previsor HSAMA tem `out_features=2`. A primeira saída representa `mu`, a segunda representa `sigma`. O sinal usado pelo trader é derivado da relação entre retorno esperado e incerteza.

Isso é teoricamente importante porque evita tratar toda previsão direcional como igualmente confiável.

Se dois previsores apontam alta, mas um tem incerteza muito maior, o trader não deveria consumir esses sinais como equivalentes.
### Loss orientada a trading

Em `trade/loss.py`, a `TriplexTradingLoss` combina:

- PnL líquido;
- custo de transação;
- penalidade de viés direcional;
- penalidade de estagnação;
- termo de Sharpe;
- termo de drawdown;
- desconto temporal de recompensa.

Esse desenho valida a quinta hipótese: o sistema treina para comportamento financeiro, não apenas para minimizar erro matemático abstrato.

***
## O ponto mais importante: causalidade

Uma teoria de trading pode parecer brilhante e ainda assim ser falsa por um motivo banal: vazamento de futuro.

A HSAMA trata isso como parte central da arquitetura. Em `trade/dataset.py`, cada timeframe é processado no seu próprio ritmo nativo. Depois, as features são projetadas para o grid de 15m usando o momento em que a informação fica conhecida (`known_time`).

Isso evita um erro comum: calcular indicadores de 1h, 4h ou 1d depois de expandir artificialmente a série para 15m. Se isso acontecesse, o modelo poderia enxergar informação que não existia no momento da decisão.

O teste local também cobre esse ponto. A suíte inclui verificações de alinhamento causal multi-timeframe e features live sem target futuro.

Essa é uma forma forte de validação teórica: antes de perguntar se a estratégia performa, o projeto verifica se a informação usada seria realmente disponível no tempo correto.

***
## O experimento walk-forward

motor principal está em `trade/engine_walkforward.py`.

A estrutura do experimento é:

1. quatro previsores HSAMA, um por timeframe: 15m, 1h, 4h e 1d;
2. um trader HSAMA final;
3. warm-up dos previsores;
4. treino conjunto com loss auxiliar;
5. inferência OOS passo a passo;
6. persistência de CSV, gráfico, checkpoint e resumo de configuração.

Os artefatos mostram uma configuração recorrente:

- 8 walks;
- 45.000 amostras de treino por walk;
- 15.000 amostras OOS por walk;
- 120.000 candles OOS consolidados por execução;
- até 180.000 candles usados;
- modelos com 16 nós, `state_dim=16`, `context_dim=32` e `max_hops=3`.

Isso importa porque a teoria não está sendo validada em um único split conveniente. O walk-forward cria uma simulação mais próxima da realidade: treina em uma janela, testa na próxima, avança e repete.

Não elimina todos os riscos. Mas reduz a chance de uma validação puramente acidental.

***
## O que os resultados dizem

Foram encontrados oito backtests walk-forward em `artifacts/run_*`. Todos usam a mesma janela base, com Buy & Hold consolidado de `+0.9669`.

A tabela abaixo resume os resultados OOS:

| Run             |  Custo | Deadzone | Retorno agente |  Sharpe |   Max DD | Trades |  Flat | Atrito |
| --------------- | -----: | -------: | -------------: | ------: | -------: | -----: | ----: | -----: |
| 20260520_113742 |  5 bps |     0.15 |      +725.9056 | +20.002 | -224.50% | 33.786 |  7.2% | 37.25% |
| 20260521_124438 |  5 bps |     0.15 |       +44.5392 | +13.175 |  -23.55% | 38.231 | 51.5% | 44.62% |
| 20260526_104840 |  5 bps |     0.15 |      +770.9468 | +19.491 | -187.47% | 50.385 | 60.7% | 39.51% |
| 20260527_004238 |  5 bps |     0.15 |      +578.6824 | +16.239 | -241.38% | 40.991 | 42.3% | 40.07% |
| 20260527_134608 |  5 bps |     0.15 |      +766.2616 | +20.918 | -203.79% | 39.252 | 47.1% | 34.76% |
| 20260528_140909 | 10 bps |     0.10 |      +127.5121 |  +6.817 | -137.61% | 14.890 | 75.4% | 50.33% |
| 20260529_111853 |  5 bps |     0.15 |      +811.6585 | +21.358 | -251.86% | 39.858 | 16.1% | 37.26% |
| 20260530_071612 | 10 bps |     0.10 |      +182.6469 | +10.971 | -106.50% | 18.118 | 33.3% | 42.83% |
> [!info] Legenda
> **Tabela 1.** Resultados dos oito backtests walk-forward da HSAMA.

Em uma leitura superficial, os números parecem apenas "bons demais". Em uma leitura validativa da teoria, eles dizem algo mais específico:

1. O agente consegue gerar comportamento diferente de Buy & Hold.
2. O modelo não colapsa para uma posição única em todas as execuções.
3. A distribuição Long/Short/Flat muda entre rodadas.
4. A mudança de custo e deadzone altera comportamento, trades e retorno.
5. A arquitetura produz artefatos auditáveis e repetíveis.

Mas essa validação vem com um asterisco grande.

***
## O que os resultados ainda não validam

Os drawdowns são altos demais. Em várias rodadas, o Max Drawdown ultrapassa `-100%`. Isso indica que a estratégia opera em um regime de risco muito agressivo ou que a métrica acumulada alavancada expande quedas de forma incompatível com uma operação real conservadora.

O atrito também é alto. Em várias execuções, os custos representam algo entre 35% e 50% do PnL bruto. Isso sugere que a teoria do edge existe, mas ainda é consumida por giro e alavancagem.

Em outras palavras:

**o backtest valida que a arquitetura encontra sinal, mas não valida que a política atual é operacionalmente robusta.**

Essa distinção é essencial. Um sistema pode ser teoricamente promissor e ainda assim perigoso como robô de trading.

***
## A evidência operacional é mais dura

Os logs de `artifacts/live_trading*` são especialmente valiosos porque funcionam como um teste fora do conforto do backtest.

Foram encontrados dois períodos:

| Log                    | Eventos | Equity inicial | Equity final | Variação |
| ---------------------- | ------: | -------------: | -----------: | -------: |
| `live_trading`         |      89 |        42.1112 |      36.1603 |  -14.13% |
| `live_trading_neutral` |     180 |        47.5340 |      42.1280 |  -11.37% |
> [!info] 
> **Tabela 2.** Resultados dos testes de *live trading* da HSAMA.

Esse resultado não invalida a teoria, mas invalida qualquer narrativa apressada de que o sistema já está pronto para produção.

A leitura correta é:

- o backtest mostra capacidade de extrair sinal;
- os testes mostram coerência estrutural e causal;
- os logs operacionais mostram que execução real, sizing, custos, timing e filtros ainda precisam amadurecer.

Essa é uma boa forma de validação científica: a teoria sobrevive parcialmente, mas encontra seus limites quando encosta no mundo real.

***
## A validação por testes

A suíte local foi executada com sucesso:

```
47 passed in 17.59s
```

Isso não prova rentabilidade. Testes unitários não fazem isso.

Mas eles validam propriedades que uma teoria de trading precisa preservar:

- o alinhamento multi-timeframe não copia target de 15m para outros horizontes;
- features live incluem a última linha sem usar target futuro;
- a loss cobra custo na borda de batches;
- o sizing respeita alavancagem e filtros de ordem;
- o runtime batch preserva causalidade dentro do lote;
- o cliente Binance trata sincronização de timestamp;
- live trading exige confirmação explícita de risco e limites de notional.

Essa camada de teste é parte da validação teórica porque impede que resultados aparentemente bons dependam de erros triviais de implementação.

***
## O critério de validação que a HSAMA já cumpre

Uma teoria quantitativa minimamente séria deveria cumprir quatro critérios:
### 1. Implementabilidade

A teoria precisa virar código executável.

A HSAMA cumpre. A arquitetura, memória multi-escala, surprisal, replay, losses e motores de execução estão implementados.
### 2. Causalidade

O modelo não pode usar informação futura.

A HSAMA trata causalidade explicitamente no dataset, nas features live e nos testes.
### 3. Auditoria

O experimento precisa gerar artefatos verificáveis.

A HSAMA salva CSVs OOS, plots, checkpoints e resumos de configuração por rodada.
### 4. Falsificabilidade

A teoria precisa poder falhar.

A HSAMA também cumpre isso: os logs operacionais negativos e os drawdowns altos são evidências que limitam a teoria atual. O sistema não esconde esses sinais.

Esse ponto é subestimado. Uma teoria que não consegue produzir evidência contrária não está sendo validada; está sendo protegida.

***
## Onde a teoria ficou mais forte

Depois de ler o projeto, a parte mais forte da teoria é a separação entre:

- previsão multi-timeframe;
- estimativa de incerteza;
- decisão de posição;
- controle por PnL líquido;
- adaptação por contexto.

Essa separação é melhor do que treinar um único modelo para cuspir uma posição diretamente a partir de features brutas. Ela permite diagnosticar onde a cadeia falha:

- os previsores erraram o retorno?
- o `sigma` ficou mal calibrado?
- o trader consumiu mal o edge?
- o custo matou o PnL?
- a alavancagem ampliou drawdown?
- o sizing real divergiu do backtest?

Essa capacidade de decompor erro é um ganho teórico real.

***
## Onde a teoria ainda precisa ser pressionada

Para transformar essa validação de pesquisa em uma tese mais forte, os próximos testes deveriam mirar pontos de falsificação mais duros.
### 1. Slippage e custos mais conservadores

O sistema já testa 5 e 10 bps, mas a operação real pode sofrer slippage dependente de volatilidade, spread e tamanho da ordem. O custo deveria ser dinâmico.
### 2. Limite de drawdown como parte do ambiente

O backtest não deveria apenas reportar drawdown. Ele deveria reagir ao drawdown com redução de risco, cooldown ou desligamento.
### 3. Ablations

Para validar a teoria HSAMA, é preciso comparar contra versões removendo componentes:

- sem surprisal;
- sem memória multi-escala;
- sem `sigma`;
- sem features inter-mercado;
- sem trader HSAMA, usando MLP simples;
- sem replay priorizado.

Se a arquitetura completa não superar essas variantes de forma consistente, a teoria fica mais fraca.
### 4. Walk-forward com seeds e períodos alternativos

Os artefatos atuais são fortes como trilha experimental, mas a validação deveria incluir variância por seed, diferentes ativos e janelas históricas.
### 5. Replay dos logs live

Os eventos live negativos deveriam virar dataset de diagnóstico. Se o modelo performa bem no backtest e mal no live, a diferença entre os dois ambientes precisa ser medida, não apenas observada.

***
## Conclusão

A HSAMA valida algo importante: a teoria foi transformada em uma arquitetura concreta, causal, testada e auditável. Ela não está apenas descrita em um README. Ela existe como código, como runtime, como dados alinhados, como backtest walk-forward, como checkpoints e como logs operacionais.

Os resultados OOS indicam que a arquitetura encontra sinal e gera políticas diferentes de Buy & Hold. A suíte de testes reforça que as principais invariantes causais e operacionais foram preservadas.

Mas a validação também revela o limite atual: a teoria ainda é mais forte como plataforma de pesquisa do que como sistema pronto para capital real. Drawdowns extremos, giro, atrito e perdas em logs operacionais mostram que o problema agora não é apenas "achar edge". É transformar edge em execução robusta.

Essa talvez seja a conclusão mais honesta e mais útil: a HSAMA não prova que venceu o mercado. Ela prova que a teoria chegou ao ponto certo para ser testada de verdade.

E isso, em pesquisa quantitativa, já é uma fronteira importante.