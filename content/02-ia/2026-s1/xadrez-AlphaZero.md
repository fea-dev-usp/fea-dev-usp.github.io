---
tags:
  - nivel/avancado
  - trilha/ia
title: AlphaZero no jogo de Xadrez
---
_**Autores:** Felipe Bulgareli de Faria · Lucas Skate · Pedro Miguelez_ 

**_Repositório:_** [link](https://github.com/lucas-santt/dev.ensina-IAXadrez)
# O jogo de Xadrez

## **Tabuleiro**

Determinado por índices de 1 ... 64 em sistema linear

```
1  2  3  4  5  6  7  8
9 10 11 12 13 14 15 16
17 ...
...
57 58 59 60 61 62 63 64
```

Determinado por índices de (0, 0) ... (7, 7) em sistemas de coordenadas
```
(0, 0) (1, 0) (2, 0) (3, 0) (4, 0) (5, 0) (6, 0) (7, 0)
(0, 1) (1, 1) (2, 1) (3, 1) (4, 1) (5, 1) (6 ,1) (7, 1)
(0, 2) (1, 2) ...
...
(0, 7) (1, 7) (2, 7) (3, 7) (4, 7) (5, 7) (6, 7) (7, 7)
```

---

``` tabuleiro[y][x] = id + 1 ``` armazena o id da peça + 1 na casa (x, y), 0 se vazia
**Peças**

Cada peça possui um id que vai de 0 ... 15 para as pretas e 16 .. 31 para brancas

O valor ``` pecas[i] = pos ``` representa a posição linear da peça de id ``` i ```\
Se a peça foi capturada, sua posição é 0 (fora do tabuleiro)

Além disso, possuem um valor de **material** que representa o valor da peça

---

Conversão de posições lineares p/ coordenadas

```
x = (pieces[i]-1) % 8
y = (pecas[i]-1) // 8
```

Coluna: Fazemos um (mod 8) para iterar pelas colunas, já que cada linha possui 8 casas

Linha: Divisão inteira (```//```) por 8 pois dá exatamente o valor dde quantas linhas já passaram

Obs: ``` pieces[i]-1 ``` para converter a posição de índices que vão de 1 .. 64 para 0 ... 63. Fazemos isso para poder trabalhar com divisão por 8

## Monte Carlo Tree Search (MCTS)

O MCTS é uma árvore onde cada nó representa um estado do jogo onde a raíz da árvore é o estado do jogo atual. As arestas entre os nós representam uma jogada que levou o jogo do estado do pai para o estado do filho. É importante ressaltar que o jogador atual (que deve fazer o movimento) alterna entre os níveis da árvore.

Para cada nó, o MCTS escolhe uma ação para gerar um novo filho e realizar um processo de backpropagation atualizando o número de visitas de cada nó e a avaliação do nó. Assim, quando o nó possui todos os filhos, ele utiliza uma mética chamada Upper Confidence Bound (UCB) para escolher qual a melhor jogada a se fazer a partir desse nó pai

$$
UCB = U(s,a) = C \cdot \mathbb{P}(s,a) \cdot \sqrt{\frac{N(s)}{1 + N(s,a)}}
$$

Tal que $s$ é o número de visitas de um nó e $a$ a quantidade de visitas total.

$C$ é uma constante qualquer definida pelo usuário.

E $\mathbb{P}(s,a)$ é a probabilidade de escolher tal ação segundo a própria rede neural.

Assim, após expandir por um número limitado de vezes, temos a raiz com seus filhos representando possíveis jogadas. Podemos, agora, escolher a melhor ação a se tomar a partir do UCB de seus filhos

## Rede neural

Utilizamos o modelo de DeepLearning $\textbf{ResNet}$ para a parte de avaliação dos estados de jogos e probabilidades de ações.

Ela funciona baseada em:
- Uma camada de convolução
- Blocos de Resíduos
- Duas cabeças para output

Os blocos de Resíduos são arquitetados de maneira que cada camada é passada para a próxima e, também, diretamente para a saída do bloco. Assim, ao realizar a ativação $\textit{ReLU}$, o resultado da última camada foi somado com o resultado de todas as camadas que vieram antes. Isso se chama $\textit{skip connections}$.

## Treinamento

O treinamento geral é realizado por iterações de $\textit{self-plays}$ e treinamentos locais. Intuitivamente, o número de iterações impacta diretamente na eficácia da rede neural.

Aqui, utilizamos as seguintes nomeações para as funções dentro da classe `AlphaZero`:

- `learn(self)`: Chamamos de $\textbf{Treinamento}$ 
- `train(self, memory)`: Chamamos de $\textbf{Treinamento local}$
- `selfPlay(self)`: Chamamos de $\textbf{\textit{Self-Play}}$

### $\textit{Self-Play}$

O $\textit{Self-Play}$ simula uma partida apenas (ou seja, um caminho dentre todos que uma partida pode tomar). Realiza isso por meio da MCTS para saber qual o melhor próximo passo.

Assim, no final, temos uma partida completa onde cada movimento é o melhor movimento segundo a MCTS. Tendo em vista que a MCTS utiliza a própria rede neural para guiar sua busca, temos que: 

A rede neural se treina não só no quesito de jogar contra si mesma, mas também na questão de guiar a própria busca da MCTS!!!

### Treinamento local

Utilizando a partida simulada pelo $\textit{self-play}$, agora pedimos para a rede neural avaliar estado por estado dessa partida. Assim, penalizamos ou recompensamos a rede comparando a sua avaliação do estado com a avaliação da MCTS gerada durante o $\textit{self-play}$.

Como a MCTS sempre é melhor que a rede neural, pois aprofunda a própria decisão do modelo, ela será o juíz nesse processo de penalização ou recompensa.

# Fontes


Understanding Residual Network (ResNet) Architecture, Pooja Mahajan

https://medium.com/analytics-vidhya/understanding-resnet-architecture-869915cc2a98

---

AlphaZero: An Introduction, Aaron Davis

https://www.youtube.com/watch?v=gsbkPpoxGQk

---

AlphaZero from Scratch - Machine Learning Tutorial, freeCodeCamp.org

https://www.youtube.com/watch?v=wuSQpLinRB4

---

AlphaZeroFromScratch, foersterrobert

https://github.com/foersterrobert/AlphaZeroFromScratch
