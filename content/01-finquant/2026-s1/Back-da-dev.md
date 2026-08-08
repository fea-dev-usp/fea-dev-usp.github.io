---
title: Back-da-dev
tags:
  - nível/basico
  - trilha/finquant
---
_**Autores**: Pedro Tsuchie, Rodrigo Catto Menim, Lucas Navis, Vicente_

_**Repositório:** [link](https://github.com/Rdg-m/FQ26.1-GP2)_

# 1. Introdução

A validação empírica de hipóteses financeiras exige infraestrutura computacional robusta e metodologicamente rigorosa. O **Back-da-dev** consiste em uma biblioteca desenvolvida na linguagem Python com o propósito de viabilizar a prototipagem rápida e o *backtesting* quantitativo de estratégias de mercado.

Concebido como um projeto do segundo ciclo de capacitação dos membros da FEA.dev, o projeto encapsula as complexidades da engenharia de dados financeiros. A arquitetura do pacote foi projetada para systematizar processos críticos da pesquisa quantitativa, fornecendo ferramentas padronizadas para:

1. Ingestão e carregamento de dados históricos de mercado.
2. Limpeza e normalização algorítmica de séries temporais.
3. Execução orientada a eventos de simulações de estratégias de *trading*.
4. Geração automatizada de métricas de desempenho e relatórios analíticos.

Em sua estrutura interna, o repositório é organizado de forma modular, segregando responsabilidades de *design* de software através dos subpacotes de processamento de dados, motor de execução, visualização e orquestração.


# 2. História e Motivação

O desenvolvimento e a validação de estratégias de *trading* frequentemente esbarram no alto custo de engenharia necessário para estruturar um ambiente de testes isento de vieses (como *look-ahead bias* ou *survivorship bias*). Historicamente, pesquisadores e estudantes necessitavam construir *pipelines* de manipulação de dados *ad-hoc*, o que introduzia ineficiências e dificultava a reprodutibilidade dos experimentos empíricos.

A principal motivação subjacente à criação do **Back-da-dev** foi mitigar esse gargalo técnico. O projeto propõe-se a unificar as etapas de ingestão, sanitização de dados, execução da estratégia e avaliação de resultados em um fluxo computacional linear e coeso.

Para garantir a validade das simulações, o desenvolvimento foi orientado pela necessidade de manter uma estrita aderência às restrições do ambiente num patamar razoável. Dessa forma, o motor foi parametrizado para internalizar atritos transacionais essenciais, suportando o cálculo de taxas de corretagem (comissões) e o cálculo de métricas de risco do portfólio. A biblioteca permite que outros *.dev's* concentrem seus recursos estritamente na formulação matemática e validação estatística de suas hipóteses financeiras.


# 3. Metodologia de Simulação e Modelos Disponíveis

## O Paradigma Orientado a Eventos (*Event-Driven*)

Na arquitetura de sistemas de simulação financeira, as ferramentas geralmente bifurcam-se em duas metodologias predominantes para a iteração temporal: o *backtesting* vetorizado e o *backtesting* orientado a eventos (*event-driven*). A modelagem vetorizada, embora favorecida em estágios exploratórios por sua alta eficiência computacional ao operar matrizes de dados simultaneamente e inerentemente suscetível ao viés de antecipação de informação (*look-ahead bias*) e possui baixa capacidade para modelar dinâmicas complexas. Caso tente-se modelar tais dinâmicas a complexidade do sistema passa a ser paralisante.

Para mitigar essas limitações, o **Back-da-dev** foi projetado como um motor cronológico orientado a eventos. No código atual, após o `.run()` o programa irá carregar dados históricos de forma linear e os transformar em eventos que serão repassados à estratégia em teste, assim criando seu próprio fluxo de processamento que nem tem acesso aos dados antes de, de fato, os usar. Esse loop sequencial atualiza caixa, posições abertas e patrimônio, e aplica fricções como comissão e lógica de stop-loss/take-profit quando presente.

Essa abordagem depende diretamente da granularidade dos dados de entrada. O motor atual itera sobre os índices temporais únicos presentes em `self.data` e aplica sinais em cada data disponível, portanto a fidelidade da simulação está limitada à resolução dos dados carregados.


## Modelos Pré-Implementados

Como gostaríamos que usuários de nossa biblioteca também tivessem acesso a alguns modelos de estratégia básicos já programados pensando na arquitetura do motor de backtest, deixamos junto ao código principal uma classe abstrata que implementa as funções básicas da API esperada e algumas implementações dessa classe em objetos completos. A infraestrutura base força um contrato de interface rigoroso: qualquer algoritmo derivado deve emitir sinais padronizados contendo o tipo de ordem (ex: **BUY** ou **SELL**), preço, quantidade e justificativa lógica, garantindo compatibilidade com o avaliador de portfólio.

Como base para experimentação imediata, o repositório engloba três implementações nativas:

- **Alocação Estática (*Buy and Hold*):** Um modelo determinístico projetado para estabelecer uma linha de base (*benchmark*). A estratégia aloca o capital disponível uniformemente entre o universo de ativos no primeiro vetor de dados observável, mantendo a posição inalterada ao longo de toda a janela de simulação.
- **Médias Móveis Simples (*MA*):** Uma estratégia clássica de seguimento de tendência fundamentada no cruzamento de duas médias móveis com periodicidades distintas.
- **Médias Móveis Exponenciais (*EMA*):** Uma derivação matemática do modelo MA que substitui a média aritmética simples por um suavizador exponencial. Esta abordagem atribui pesos assimetricamente maiores a observações recentes da série de preços.

Acreditamos que os exemplos sejam bons e vastos o suficiente para desmistificar o funcionamento e implementação esperados ao redor da biblioteca.


# 4. Arquitetura do Sistema e Implementação

O **Back-da-dev** adota uma visão modular, visando à fácil expansão do código e segregação das classes e funções. Como o projeto visa ser distribuído por Pypi, todo o código fica centralizado em uma pasta de pastas onde cada uma é um passo importante de um backtest e outra, com os testes.

Abaixo, detalha-se a divisão dos submódulos e o fluxo de dependências do sistema:

<div align="center">
  <img src="imagens/assets-back-da-dev/arquitetura_sistema.png" alt="Arquitetura do Sistema" width="550" style="max-width: 100%; height: auto;" />
</div>

---

- **Ponto de Entrada:** O arquivo `padrão` expõe a API pública da biblioteca, atuando como uma camada de abstração para o usuário final. O módulo `interface` serve como o hub orquestrador de alto nível, integrando as etapas de dados, execução e geração de relatórios através de funções utilitárias unificadas.
- **Processamento de Dados (`dataprocessing`):** Subdividido em `load` (responsável pela ingestão de séries temporais via arquivos locais ou conexões remotas via APIs externas) e `clean` (encarregado de realizar a validação estrutural, limpeza e tratamento de lacunas nas séries de preços).
- **Motor de Execução (`backtesting`):** Onde é gerenciado o estado do `BacktestEngine` e o laço de iteração de eventos históricos. Este módulo consome diretamente as classes derivadas da abstrata e faz suas simulações.
- **Visualização Analítica (`graphing`):** O script encapsula a lógica de renderização estatística, transformando os vetores de resultados do motor em saídas gráficas inteligíveis.

### Gráficos do Módulo de Visualização

|                                                      Volatilidade Móvel Anualizada                                                      |                                            Índice de Força Relativa (RSI)                                             |
| :-------------------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------: |
| <img src="imagens/assets-back-da-dev/grafico_volatilidade.png" alt="Volatilidade" width="380" style="max-width: 100%; height: auto;" /> | <img src="imagens/assets-back-da-dev/grafico_rsi.png" alt="RSI" width="380" style="max-width: 100%; height: auto;" /> |

| Retorno Acumulado (%) | Curva de Patrimônio |
| :---: | :---: |
| <img src="imagens/assets-back-da-dev/grafico_retorno_acumulado.png" alt="Retorno Acumulado" width="380" style="max-width: 100%; height: auto;" /> | <img src="imagens/assets-back-da-dev/grafico_equity_curve.png" alt="Equity Curve" width="380" style="max-width: 100%; height: auto;" /> |

| Gráfico de Drawdown | Bandas de Bollinger |
| :---: | :---: |
| <img src="imagens/assets-back-da-dev/grafico_drawdown.png" alt="Drawdown" width="380" style="max-width: 100%; height: auto;" /> | <img src="imagens/assets-back-da-dev/grafico_bandas_bollinger.png" alt="Bandas de Bollinger" width="380" style="max-width: 100%; height: auto;" /> |


# 5. Capacidades Operacionais da Biblioteca

O pacote do **Back-da-dev** fornece um *pipeline* analítico fim-a-fim, permitindo que a transição entre o dado bruto e o relatório de performance ocorra de forma determinística e integrada. As principais capacidades funcionais da biblioteca compreendem:


## Ingestão Automatizada e Sanitização de Dados

A biblioteca abstrai a complexidade associada à coleta de dados de mercado. Através das funções de carregamento, o sistema conecta-se à API do Yahoo Finance ou consome arquivos estruturados locais nos formatos `csv`, `json` e `xlsx`. O carregador valida a presença das colunas `Open`, `High`, `Low`, `Close` e `Volume`. As rotinas de limpeza realizam conversões de tipo, trata valores ausentes com `ffill`, `bfill`, `interpolate` ou `drop`, remove duplicatas, ordena o índice e filtra linhas inconsistentes usando `pandas` como pilar central. Na implementação atual, pode remover outliers com base em z-score.


## Motor de Simulação Parametrizável com Controle de Fricção

A classe `BacktestEngine` opera de forma isolada do modelo de estratégia de *trading* escolhido. O motor é inicializado ingerindo o objeto da estratégia. Por padrão, ele rejeita compras impossíveis quando não há caixa suficiente; a não ser que o usuário mude as configurações, assim o motor passa a ajustar a quantidade para caber no saldo disponível. Uma opção que é contra indicada, pois a engine não comunica quanto foi possível comprar, podendo gerar de-sync.

O motor mantém o estado patrimonial do portfólio contando o dinheiro, valor, posições e histórico diário. A atualização diária do portfólio é feita no passo que os eventos gerados a partir dos dados são consumidos, que marca a mercado posições abertas com o preço de fechamento do período atual.


## Geração de Logs e Exportação de Métricas de Desempenho

Ao término do ciclo de eventos históricos, a interface avalia a trajetória do portfólio e computa métricas consolidadas de desempenho, incluindo o *drawdown* máximo percentual, retorno líquido, total de operações, taxa de acertos (*win rate*) e retorno anualizado. Compiladas as métricas, escreve um arquivo de resumo no formato `.log`. Atualmente, a biblioteca não exporta todo o histórico de transações executadas ou o estado completo das variáveis; a implementação da exportação do histórico de resultados e trades nos formatos CSV ou JSON é um item previsto no roadmap do projeto.


## Visualização Estatística de Resultados

O módulo de visualização converte os dados gerados durante o backtest em artefatos gráficos construídos sobre o `matplotlib`. O sistema gera gráficos da curva de evolução de patrimônio líquido (*equity curve*), *drawdowns*, retornos acumulados, volatilidade, Bandas de Bollinger, Oscilador RSI e séries temporais de preço, podendo salvá-los em formatos como PNG e SVG. Como a ferramenta é um protótipo, não há menção à geração de curvas comparativas frente a estratégias de referência ou *benchmarks* estáticos. Mesmo que esses possam ser facilmente rodados com os mesmos dados se utilizando dos modelos pré-implementados.


## Interface de Linha de Comando (CLI)

Para fins de automação e integração em scripts de infraestrutura, o pacote implementa um ponto de entrada CLI executável. A interface permite disparar pipelines de backtesting completos via terminal de comandos através do comando `python -m back_da_dev`.

```bash
python -m back_da_dev escrever algo legal aqui
```


# 6. Limitações Atuais e Trabalhos Futuros (_Roadmap_)

Apesar de sua arquitetura base estar plenamente funcional e validada empiricamente, o **Back-da-dev** é concebido como um ecossistema em evolução contínua. Sob a ótica da engenharia de *software* e da pesquisa quantitativa, mapeamos vetores de melhoria essenciais para expandir a robustez e a aplicabilidade da biblioteca em cenários de alta complexidade.

O plano de desenvolvimento futuro contempla os seguintes aprimoramentos:

- **Expansão das Métricas:** Onde o relatório final poderia conter métricas sobre o impacto de certo parâmetro, como a comissão ou o *slippage*.
- **Suporte Avançado a Multiativos e Portfólios:** Refatoração das lógicas de execução para suportar rebalanceamento dinâmico de portfólios complexos e regras de alocação de capital vetorial entre múltiplos ativos simultaneamente.
- **Rastreabilidade e Exportação Granular:** Implementação de *logs* de transação em nível de instrumento individual, com suporte a exportação serializada estruturada em formatos tabulares e hierárquicos (CSV e JSON), otimizando a interoperabilidade com outras ferramentas de *Data Science*.
- **Evolução Analítica de Visualização:** Ampliação das capacidades do módulo `graphing`, introduzindo sobreposições gráficas de pontos de execução (*trade overlays* em gráficos de preço) e plotagem de distribuições estatísticas de retorno.
- **Extensibilidade e Registro de Estratégias:** Desenvolvimento de um registro dinâmico e padronizado (*extensible strategy registry*) para acomodar novos *templates* de modelos matemáticos.
- **Resiliência do Processamento de Dados:** Fortalecimento dos mecanismos de tratamento de exceções e validação de esquemas (*schema validation*) nas sub-rotinas `load_data()` e `clean_data()`, mitigando falhas decorrentes de anomalias nos dados de entrada.


# 7. Conclusão

O desenvolvimento do **Back-da-dev** representa um marco metodológico significativo para a FEA.dev e para a comunidade de pesquisa quantitativa. Ao encapsular as fricções inerentes à engenharia de dados financeiros e abstrair o motor de simulação por trás de um paradigma rigorosamente orientado a eventos, a biblioteca não apenas reduz o tempo necessário para testar uma tese de mercado, mas também eleva a integridade científica dos resultados obtidos.

Mais do que um projeto laboratorial acadêmico, a ferramenta estabelece um padrão arquitetural reproduzível. Ela fomenta a construção empírica de conhecimento, permitindo que estudantes, pesquisadores e investidores modelem a realidade dos mercados com alta fidelidade cronológica e transacional.

A natureza de código aberto (*open-source*) e o modelo de licenciamento permissivo (Licença MIT) refletem a essência colaborativa da FEA.dev. Convidamos desenvolvedores e analistas quantitativos a explorar a base de código, submeter *pull requests*, reportar anomalias computacionais via *issues* e, fundamentalmente, utilizar o **Back-da-dev** como a fundação de suas próximas descobertas em Finanças Quantitativas.

Acessem em: [https://pypi.org/project/Back-da-dev/0.0.1/](https://pypi.org/project/Back-da-dev/0.0.1/)
