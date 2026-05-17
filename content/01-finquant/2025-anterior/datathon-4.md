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
    

---

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

<div align="center">
<svg width="500" height="300" viewBox="0 0 500 300" xmlns="http://www.w3.org/2000/svg">
  
  <style>
    .title { font-family: sans-serif; font-size: 24px; font-style: italic; fill: currentColor; }
    .list { font-family: sans-serif; font-size: 16px; font-style: italic; fill: currentColor; }
    .label { font-family: sans-serif; font-size: 14px; fill: currentColor; }
    .line { stroke: currentColor; stroke-width: 2; fill: none; }
    .box { fill: transparent; stroke: currentColor; stroke-width: 2; }
  </style>

  <rect x="150" y="20" width="200" height="50" class="box" />
  <text x="250" y="55" text-anchor="middle" class="title">Risk premium</text>

  <path d="M250 70 L160 90 M250 70 L340 90" class="line" />

  <rect x="50" y="90" width="180" height="150" class="box" />
  <text x="70" y="130" class="list">Médias móveis</text>
  <text x="70" y="170" class="list">Momentum</text>
  <text x="70" y="210" class="list">Volatilidade</text>
  <text x="140" y="265" text-anchor="middle" class="label">Ind. Técnicos</text>

  <rect x="270" y="90" width="180" height="150" class="box" />
  <text x="290" y="120" class="list">Dividend yield</text>
  <text x="290" y="155" class="list">P/E ratio</text>
  <text x="290" y="190" class="list">Inflação Taxas</text>
  <text x="290" y="225" class="list">de juros</text>
  <text x="360" y="265" text-anchor="middle" class="label">Ind. Fundamentalistas</text>

</svg>
</div>

