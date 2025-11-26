# **1. Introdução ao Aprendizado de Máquina**

Neste curso, você será exposto a diversos termos expressos em notação matemática. Buscaremos sempre ilustrar de forma intuitiva o significado de cada uma dessas notações. No entanto, para avançar no curso, é fundamental dedicar um tempo para compreendê-las, pois, à medida que os modelos se tornam mais complexos, nem sempre será possível oferecer uma explicação puramente intuitiva.

Se você não está familiarizado com notação matemática ou sente receio ao vê-la, não se preocupe! Pense nela como uma forma compacta de expressar muitas informações em poucas palavras — como uma linguagem própria da matemática. Encare isso como o aprendizado de um novo idioma. 

Boa sorte!

## **O que é Inteligência Artificial?**

Antes de começar com qualquer tipo de conteúdo, é muito importante esclarecer uma coisa: IA NÃO É SÓ CHATGPT!!!

Nos últimos anos, o termo IA tem se tornado uma tendência e é cada vez mais ouvido e repetido por todos os lados. Contudo, apesar de ser amplamente utilizado, são raros os casos em que sua definição é de fato explicitada para o público. Na verdade, chega até mesmo a ser difícil de definir IA com uma explicação simples.

<img src="https://i0.wp.com/cadernopop.com.br/wp-content/uploads/2025/02/robo-selvagem-1024x576.jpg?resize=1024%2C576&ssl=1" height=350>

Inteligência Artificial é um termo muito amplo, que abrange uma vasta gama de estudos em diversas áreas, mas, da maneira mais simples possível, __IA é a capacidade de máquinas simularem a inteligência humana__. Mas o que é a inteligência humana? Bom, somos programadores, não filósofos, mas uma coisa é certa, ela não é algo tão simples de entender ou definir, o que também se aplica à IA.

Da mesma forma como separamos o estudo do corpo humano em diferentes áreas para melhor entendê-lo, assim também fazemos com IA. Dessa forma, algumas das principais subdivisões criadas são:
- Machine Learning
- Deep Learning
- Processamento de linguagem natural (NLP)

Na sequência, traremos uma distinção mais clara sobre alguns desses termos e a IA propriamente dita.

## **Diferenças entre IA, Machine Learning e Deep Learning**

Como dito anteriormente, __IA__ é um campo da ciência da computação que cria sistemas capazes de simular a inteligência humana. Isso inclui desde regras simples baseadas em lógica até sistemas avançados que aprendem com dados. 

Alguns exemplos de IA que podemos ver no dia a dia são:
- Siri 
- Alexa.


__Machine Learning__ por sua vez é uma subárea da Inteligência Artificial. Ela permite que computadores aprendam a partir de dados sem serem explicitamente programados. Em vez de seguir regras fixas, os algoritmos analisam padrões e fazem previsões com base nas informações fornecidas. 

Alguns exemplos de Machine Learning que podemos ver no dia a dia são:
- Algoritmos que recomendam filmes na Netflix
- Sistema de detecção de fraudes em bancos


__Deep Learning__, por fim, é um subconjunto do Machine Learning, que usa redes neurais artificiais profundas para processar dados de forma semelhante ao cérebro humano. Ele é especialmente útil para tarefas que envolvem grandes volumes de dados e reconhecimento de padrões complexos.

Alguns exemplos de Deep Learning que podemos ver no dia a dia são:
- Reconhecimento facial do Facebook
- Carros autônomos da Tesla

De uma maneira geral, podemos entender os três como sendo diferentes partes de um todo, como demonstrado na imagem a seguir:

<img src="https://media.licdn.com/dms/image/v2/C4D12AQFnajkkfJ5ISg/article-cover_image-shrink_720_1280/article-cover_image-shrink_720_1280/0/1608737877258?e=2147483647&v=beta&t=htBCpaT-E02Wzh7dfWnrwcnUca0sDC6FraWgDmwvt14" height=400>

## **Tipos de aprendizado de máquina**

### **O que é o Aprendizado Supervisionado?**

Aprendizado supervisionado é uma técnica de machine learning que usa dados rotulados para treinar algoritmos (mas o que isso quer dizer??). 

Imagine seu professor de cálculo VIII escrevendo tanta letra na lousa que você não sabe se o que ele está fazendo é matemática ou um poema. Ele está assumindo que os alunos entendem tudo o que ele está dizendo (mas todo o mundo sabe que está assumindo errado). Seria muito bom se ele explicasse o significado daquele hieróglifo egípcio, trazendo exemplos com outros exercícios que a gente já conhece e entende. 

E é por isso mesmo que vamos tomar o lugar dele e explicar para o nosso querido aluno (o PC) o que ele precisa entender, trazendo diversos exemplos de exercícios com a resposta correta.

<img src="https://static.wikia.nocookie.net/2a3a4ed5-cece-4538-b323-ef3dbcf09787/scale-to-width/755" height=300/>

Uma vez que ensinamos nosso pupilo, como bons professores que somos, devemos oferecer novos exercícios para ele (sem solução dessa vez), e assim, verificar se agora ele aprendeu e é capaz de fazer por conta própria, apresentando também um feedback apontando seus erros e acertos. Com base nesse feedback, caso o aluno tenha errado boa parte dos exercícios, é hora de chamarmos todos os monitores e fazermos mais outra revisão, possivelmente até mais completa que a primeira. E assim o ciclo pode se repetir algumas vezes até chegarmos a um nível agradável.

Depois de 3 semestres e a um passo de jubilar, o aluno uma hora consegue passar na disciplina. Da mesma forma, após alguns minutos tentando, o nosso modelo está pronto e já é capaz de executar sua tarefa com um certo nível de precisão.

### **O que é o Aprendizado Não Supervisionado**

Se por um lado o aprendizado supervisionado precisa da supervisão humana, o aprendizado não supervisionado não necessita dela.

Nesse caso, imagine que você está vivendo sua vida tranquilamente, curtindo o sítio da dev, e de repente você recebe um e-mail dizendo que seu querido professor de cálculo veio a falecer com seus 136 anos de idade... que tristeza. Se era ruim com ele, o que será de nós sem ele? Nesse caso não teremos mais ninguém para nos dizer a resposta correta dos exercícios para aprendermos antes de testar na prova...

<img src="https://media.tenor.com/gPbkAifeXnkAAAAM/naruto-sad.gif" height=300/>

Mas você não pode ficar de reaval. Sua viagem para o Japão para conhecer o Naruto já está marcada e essa prova vale 8 pontos na média. Você vai passar por bem ou por mal. Dessa forma, você estuda por semanas, até esquece o que é dormir, e enfrenta a prova, dando tudo de si. Apesar dos esforços, você abre a prova e a primeira questão é assombrosa... é um pesadelo. Mas você não se dá por vencido e segue para a próxima, e vê que ela não era tão difícil quanto a primeira. Na verdade nenhuma outra questão é tão difícil quanto a primeira. 

Você faz a prova, ciente de que boa parte das questões está correta, mas a primeira é infernal... não há o que ser feito. Nesse caso, um chute técnico tem mais chances do que uma resposta em branco, e é isso que você faz. Utiliza todo o seu conhecimento adquirido vendo jogadas do Ronaldinho no YouTube e dá o melhor chute de sua vida. 

Com isso você vai tranquilo para o Japão e torce para que o professor não te obrigue a fazer a matéria de novo no próximo semestre (ou no caso, espera que seu código funcione de primeira e você não precise refiná-lo e tentar de novo).

### **O que é o Aprendizado por Reforço?**

Bom dia!!! <br>

Era tudo um sonho! O professor nunca existiu. Na verdade você está em um laboratório e é alvo de testes macabros 💀 <br>

E para piorar a prova é e sempre foi real... <br>

<img src="https://media.tenor.com/M7ec11RfaboAAAAM/waking-up.gif" height=300>

Nesse caso, o estudo tem de continuar, mas dessa vez por conta própria. Serão listas e mais listas de exercícios que devem ser feitas sem ninguém para te ajudar. A única coisa que os cientistas vão fazer para te "apoiar" é te dar um sonho de valsa caso acerte ou uma paulada caso erre o resultado da questão.

Dessa forma, como ninguém aprende assim do nada, nos primeiros dias você leva tanta paulada que fica parecendo o Thanos de tão roxo. Mas na segunda semana, você começa a acertar. Na terceira, mais ainda. Até que chega um momento em que você vai receber tanto sonho de valsa que vai acabar engordando.

O mesmo acontece com a máquina. Quando incentivamos seus acertos e punimos seus erros, também estaremos treinando-o para entregar resultados cada vez mais precisos. Portanto, não tenha medo de dar pauladas nele (só não literalmente por favor. Não nos responsabilizamos por possíveis danos causados aos computadores).

## **Definições iniciais**

### **O que são dados?**

Imagine que você quer entender melhor um grupo de pessoas. 

Para isso, você decide anotar algumas informações sobre cada uma delas, como altura *(em cm)*, peso *(em kg)* e idade *(em anos)*. Você observa uma pessoa e registra esses três valores. Depois, faz o mesmo com outra pessoa e assim por diante.

Cada conjunto de informações que você registra (neste caso, altura, peso e idade) constitui um **dado**, isto é,uma representação de algo do mundo real que queremos estudar ou analisar.

Suponha que coletamos os seguintes dados:

- Pessoa 1: 170cm de altura, 70kg e 25 anos.

- Pessoa 2: 160cm de altura, 55kg e 30 anos.

- Pessoa 3: 180cm de altura, 80kg e 28 anos.

Perceba que, com base nessas três informações podemos representar cada pessoa com três números, veja:

- Pessoa 1 -> (170, 70, 25).

- Pessoa 2 -> (160, 55, 30).

- Pessoa 3 -> (180, 80, 28).
  
Cada linha acima é um conjunto de informações sobre uma pessoa.

**Assim, o conjunto de dados que possuímos é: $$\{(170,70,25),(160,55,30),(180,80,28)\}$$**
 

### **O que são características?**

Agora, perceba que cada dado é formado por três números diferentes. Cada um deles representa um tipo específico de informação:

- O primeiro número indica a **altura**.

- O segundo número indica o **peso**.

- O terceiro número indica a **idade**.

Chamamos essas informações individuais de **características**. Elas são os aspectos que escolhemos para descrever cada pessoa.

Se tivéssemos escolhido outras informações, como cor dos olhos ou cidade onde mora, teríamos características diferetentes. Assim, **as características são os elementos que compõem cada dado.**

### **O que é um espaço de características?**

Agora que compreendemos que, no exemplo que estamos usando, cada pessoa é caracterizada por três atributos (altura, peso e idade), podemos pensar em um jeito de visualizar essas informações.

Imagine um gráfico em que cada ponto representa uma pessoa, sendo descrita por três características: altura, peso e idade:

- O **eixo X** representa a altura.

- O **eixo Y** representa o peso.

- O **eixo Z** representa a idade.

Cada pessoa pode ser representada por um ponto dentro desse espaço. **Esse espaço, onde todas as combinações possíveis de altura, peso e idade podem existir—isto é, onde essas características podem assumir quaisquer valores dentro de um intervalo permitido—é chamado de espaço de características.**  

Se tivéssemos apenas altura e peso, nosso espaço teria apenas dois eixos, como um gráfico bidimensional. Se adicionássemos mais características, precisaríamos de mais dimensões para representar tudo.

💡 Dica: Tente visualizar esse conceito de forma gráfica: imagine um ponto em um espaço tridimensional, onde o eixo X representa a altura, o eixo Y representa o peso e o eixo Z representa a idade. Esse ponto corresponde a uma pessoa dentro do nosso conjunto de dados. No início, pode parecer desafiador imaginar esse espaço, mas compreender essa ideia tornará o aprendizado muito mais intuitivo no futuro!

### **O que são vetores de características?**

Agora que entendemos que cada pessoa é representada por um ponto dentro do espaço de características, podemos dar um nome especial para essa representação: **vetor de características**

Um vetor de características é simplesmente um conjunto de números que descreve uma pessoa dentro desse espaço. Podemos imaginá-lo como uma "seta" que parte da origem do espaço de características e aponta diretamente para a posição (coordenadas) correspondente a essa pessoa.

Por exemplo, para a Pessoa 1, o vetor de características é $(170, 70, 25)$, o que significa:

- Altura: **170cm**.

- Peso: **70kg**.

- Idade: **25 anos**.

Se pensarmos em um gráfico tridimensional, onde cada eixo representa uma característica (altura, peso e idade), esse vetor nos dá a posição exata da pessoa nesse espaço. A "seta" que parte da origem até esse ponto é uma forma intuitiva de visualizar como cada observação do nosso conjunto de dados pode ser representada matematicamente.

Em resumo, vetor de características é um termo matemático que usamos para representar cada observação dentro do nosso conjunto de dados.

💡 Dica: Realmente tente imaginar que cada pessoa do nosso conjunto de dados é representada por uma seta partindo da origem e apontando para um ponto no espaço tridimensional. Essa seta nada mais é do que o vetor de características, que indica a posição exata da pessoa nesse espaço. No começo, pode ser desafiador visualizar essa ideia, mas pensar nos vetores como "setas direcionadas" ajudará a compreender melhor como os dados são organizados e analisados matematicamente!

## **Formalizando as definições iniciais**

Agora que construímos uma boa intuição, podemos formalizar esses conceitos matematicamente — mantendo o formalismo apenas no nível necessário por enquanto.

### **Dados**

- São um conjunto de observações $X = \{x_{1}, x_{2}, ..., x_{n}\}$, onde cada $x_{i}$ é uma observação.

- No nosso exemplo, os dados são o conjunto de pessoas que analisamos.

### **Características**

- São os atributos que usamos para descrever cada observação. 
  
- Por exemplo, para a observação: $x_{i} = (x_{i1}, x_{i2},...,x_{id})$, cada valor $x_{ij}$ representa um atributo específico da observação $x_{i}$ *(ex: altura, peso, idade)*, onde $j$ varia de $1$ até $d$.

### **Espaço de características**

- É o conjunto de todas as possíveis combinações dos atributos que utilizamos para descrever uma observação.

- Se cada observação é descrita por $d$ características, esse espaço contém todas as combinações possíveis desses $d$ atributos e é matematicamente representado por $R^{d}$.

- Intuitivamente, podemos imaginar esse espaço como um ambiente onde cada observação ocupa uma posição única com base nos valores de suas características.

### **Vetores de características**

- Representam cada observação dentro do espaço de características.

- No nosso exemplo, a **Pessoa 1** é representada pelo vetor: $x_{1} = (170,70,25) \in R^{3}$.

- De forma geral, para um espaço de características com $d$ dimensões, cada observação é um vetor da forma: $x_{i} = (x_{i1},x_{i2},...,x_{id}) \in R^{d}$, onde $i$ indica o número da observação e cada índice $j$ (com $j \in \{1,2,...,d\}$) representa uma característica dessa observação.

### 💡 Dica:

Não se preocupe se essas definições parecerem um pouco abstratas no começo! Você pode continuar avançando no curso sem dominar completamente essas notações matemáticas. No entanto, quanto mais confortável você estiver com essas notações, mais rápido será seu progresso e mais profundo será seu entendimento dos próximos tópicos.

Se algo não ficou claro, pergunte ao responsável pelo case e revise essas definições sempre que for estudar. Criar familiaridade com essas notaçãos ao longo do tempo tornará o aprendizado muito mais natural e intuitivo!

# **2. Fundamentos de Machine Learning**

## **O que é um modelo preditivo?**

Um modelo preditivo é um tipo de modelo de machine learning que tem como objetivo principal fazer previsões sobre novos dados com base em padrões aprendidos a partir de dados históricos.

---

Esses modelos utilizam padrões extraídos dos dados para fazer previsões sobre novas observações. Em termos formais, esses modelos buscam aprender uma função $$f: x_{i} \in X \rightarrow Y$$ que relacione os vetores de características $x_{i} \in X$ com a variável alvo $Y$, de forma que seja possível estimar um $Y$ para um novo $x_{i} \in X$ não observado anteriormente.

---

Os modelos preditivos podem ser utilizados para diferentes tipos de tarefas, como prever se um cliente pagará um empréstimo (classificação), estimar o valor de um imóvel (regressão) ou antecipar o comportamento de uma série temporal (como preços de ativos financeiros).

No entanto, as abordagens para construir esse tipo de modelo variam bastante, dependendo da forma como os dados são tratados e da estratégia utilizada para ajustar os parâmetros do modelo. Podemos dividir os modelos preditivos em algumas categorias principais, são elas:



### **1. Modelos Estatísticos e Probabilísticos**

Esses modelos assumem que os dados seguem uma distribuição probabilística específica e ajustam seus parâmetros para maximizar a verossimilhança dos dados observados.

✅ **Objetivo:** Estimar a distribuição dos dados e inferir a relação entre as variáveis.

**Exemplos:**

- Regressão Linear: Assume que a relação entre as variáveis é linear e que os resíduos seguem uma distribuição normal.

- Regressão Logística: Usa a função sigmoide para modelar probabilidades em problemas de classificação binária.

- Naïve Bayes: Baseia-se na regra de Bayes e assume independência condicional entre os atributos.

📌 **Diferencial:** Esses modelos são baseados em conceitos estatísticos bem definidos e geralmente interpretáveis.

### **2. Modelos Baseados em Otimização**

Esses modelos aprendem a função $f$ otimizando uma métrica específica, sem necessariamente assumir uma distribuição subjacente dos dados.

✅ **Objetivo:** Encontrar um modelo que minimize uma função de erro ou maximize uma margem de separação.

**Exemplos:**

- SVM (Máquinas de Vetores de Suporte): Maximiza a margem entre as classes em problemas de classificação.

- Redes Neurais (MLPs clássicas): Ajustam pesos para minimizar um erro através do gradiente descendente.

📌 **Diferencial:** Baseiam-se em técnicas numéricas de otimização e não exigem uma suposição explícita sobre a distribuição dos dados.

### **3. Modelos Baseados em Particionamento de Dados**

Esses modelos criam regras para dividir os dados em subconjuntos homogêneos, organizando-os hierarquicamente.

✅ **Objetivo:** Criar regras de decisão que segmentem os dados em diferentes categorias.

**Exemplos:**

- Árvores de Decisão: Criam um conjunto de regras sequenciais que levam a decisões.

- Random Forests: Conjunto de árvores de decisão para aumentar a robustez.

📌 **Diferencial:** São fáceis de interpretar e não exigem transformações matemáticas complexas.

### **4. Modelos Baseados em Agrupamento (Clustering)**

Modelos que tentam encontrar padrões e estruturas nos dados sem rótulos supervisionados.

✅ **Objetivo:** Agrupar os dados de forma a maximizar a semelhança dentro dos clusters e minimizar entre os clusters.

**Exemplos:**

- K-Means: Baseado na minimização da soma das distâncias dos pontos ao centro do cluster.

- DBSCAN: Detecta clusters com base na densidade dos dados.

📌 **Diferencial:** Úteis para análise exploratória e segmentação de dados sem supervisão.



### **5. Modelos Baseados em Instâncias**

Esses modelos fazem previsões baseadas nos exemplos mais próximos no conjunto de treinamento, sem construir explicitamente uma função generalizada durante o aprendizado.

✅ **Objetivo:** Utilizar diretamente os dados observados para fazer previsões sem uma fase explícita de aprendizado de parâmetros.

**Exemplo:**
    
- KNN (K-Nearest Neighbors): Classifica ou estima valores com base nos $k$ vizinhos mais próximos.

📌 Diferencial: São conhecidos como modelos preguiçosos (lazy learners) porque não possuem uma fase explícita de treinamento; todo o esforço computacional ocorre no momento da previsão.

### **A importância da amostra de treinamento para um modelo preditivo**

No fim das contas, modelos preditivos tentam encontrar uma função matemática que capture a relação entre as variáveis de entrada (características) e a variável de saída (o que queremos prever). Essa função pode ser vista como uma aproximação da verdadeira relação existente nos dados. No entanto, os dados usados para treinar o modelo representam apenas uma amostra de um conjunto muito maior e desconhecido. Se essa amostra for pequena, enviesada ou não representativa, o modelo pode aprender padrões artificiais que não se repetem em novos dados — um problema conhecido como overfitting.

Diferentes modelos fazem suposições distintas sobre essa relação. Modelos estatísticos assumem que os dados seguem certas distribuições probabilísticas, enquanto modelos baseados em otimização simplesmente ajustam funções para melhor se encaixar nos exemplos observados, sem pressupor uma estrutura fixa. Em ambos os casos, a qualidade da amostra influencia diretamente a capacidade do modelo de fazer boas previsões.

Por isso, ao treinar um modelo, é essencial garantir que os dados de entrada representem bem o fenômeno que estamos tentando modelar. Métodos como validação cruzada, regularização e aumento da diversidade dos dados ajudam a reduzir vieses e melhorar a capacidade do modelo de generalizar para novas situações.

## **Tradeoff entre Bias e Variância** 

No contexto de machine learning, bias e variance são conceitos centrais para entender o erro total de um modelo e avaliar sua capacidade de generalização. Esses componentes descrevem como o modelo se comporta ao lidar com novos dados, ou seja, dados que não foram usados durante o treinamento, e ajudam a identificar as causas de diferentes tipos de erro.

### **Explicando o Bias**

O bias está associado à incapacidade do modelo de captar as complexidades subjacentes nos dados. Modelos com alto bias fazem suposições simplificadas, resultando em um desempenho ruim tanto nos dados de treino quanto nos de teste. Esse comportamento caracteriza o subajuste (underfiting), quando o modelo não consegue representar adequadamente as relações reais nos dados.

Características do Bias:
- Modelos com bias altos geralmente são simples. Um exemplo é a regressão linear aplicada quando os dados possuem relações **não-lineares**
- Ocorre quando o modelo subestima a complexidade das relações entre os dados
- Está associada com baixa acurácia tanto nos dados de treino quanto nos dados de teste.

A imagem abaixo deixa mais claro uma situação de um modelo com alto bias.

<p align='center'>
<img src="https://sigmoidal.ai/wp-content/uploads/2023/11/621609a7e64cfb63781a0426_24-300x200.png" width="400"></img>
</p>

Perceba que claramente há uma relação não-linear entre os dados. Porém, o modelo tenta ajustar uma reta ao conjunto de dados, não capturando toda a complexidade envolvida


### **Definição formal de Bias**

O bias mede o erro sistemático do modelo. Formalmente, ele se refere à diferença entre o valor médio das predições do modelo e o valor verdadeiro que estamos tentando prever. Matematicamente, para uma variável-alvo y, com base em entradas x, o bias é definido como:

$$
	Bias(\hat{f}(x)) = \mathbb{E}[\hat{f}(x)] - f(x)
$$

Onde:

- $E[\hat{f}(x)]$ é o valor esperado das predições do modelo (considerando diferentes amostras de treino).
- $f(x)$ é o verdadeiro mapeamento subjacente (função real que gera os dados).

### **Explicando a Variância**

Por outro lado, a variancia reflete a sensibilidade do modelo às flutuações nos dados de treino. Modelos com alta variancia não apenas aprendem os padrões gerais, mas também o ruído específico dos dados de treino. Isso resulta em um excelente desempenho nos dados de treino, mas um desempenho ruim em novos dados, caracterizando o superajuste (overfitting). 

Características da Variancia:

- Modelos com variancia alta são geralmente complexos, como árvores de decisão profundas ou redes neurais complexas treinadas com poucos dados.
- Ocorre quando o modelo se ajusta excessivamente aos dados de treinamento.
- Resulta em alta acurácia no **treinamento**, mas baixa acurácia em dados de **teste**, pois o modelo não generaliza bem.


A imagem abaixo mostra um exemplo de uma caso com alta variancia (overfitting):
<p align='center'>
<img src="https://cdn.prod.website-files.com/5fb24a974499e90dae242d98/621608ae7abbdc500080ef96_23.png" width="400"></img>
</p>

Neste caso, perceba que o modelo foca não nas relacões fundamentais entre os dados, mas sim no rúido específicio dos dados de treino. Se formos aplicar esse modelo a uma outra amostra de dados que não seja a de treino, o desempenho será muito baixo, pois é como se o modelo tivesse apenas memorizado o conjunto de treinamento.

💡 **Dica**: Lembra daquela prova em que você teve pouco tempo de estudar e dois dias antes da prova bate aquele desespero? O que você faz? Não dá tempo de entender todo o conteúdo em tão pouco tempo.

Uma alternativa nesse cenário é decorar aquela lista que o professor passou para estudo. Vai que cai uma questão igualzinha né? 

Esse é um caso em que você está em um overfitting!! Você pode ser capaz de responder cada questão da lista de bate pronto, mas você não entendeu o conteúdo de fato, se houver alguma pergunta diferente, você não saberá responder.

### **Definição formal de Variância**

 A variancia mede a sensibilidade do modelo às flutuações nos dados de treino. Ela descreve o quanto as predições do modelo variam em relação à média das predições quando o modelo é treinado com diferentes amostras de treino. Formalmente, a variancia é definida como:

$$
	Var(\hat{f}(x)) = \mathbb{E}[(\hat{f}(x) - \mathbb{E}[\hat{f}(x)])^{2}] 
$$

Onde:

- $\hat{f}(x)$ é a predição do modelo.
- $\mathbb{E}[\hat{f}(x)]$ é o valor esperado das predições do modelo.

### **Explicando o Tradeoff entre Bias e Variância**

Fundamentalmente, a questão de encontrar "o melhor modelo" se refere a encontrar um ponto ótimo no trade-off entre bias e variancia

A capacidade de generalização de um modelo depende de encontrar um equilíbrio entre bias e variancia. Um modelo com alto bias é muito simples e subajusta os dados, enquanto um modelo com alta variancia é excessivamente complexo e superajusta os dados de treino.

O trade-off entre bias e variance refere-se ao equilíbrio necessário entre simplicidade e complexidade do modelo para alcançar a melhor performance possível.
- 🔺Aumentar a complexidade de um modelo reduz o bias, mas aumenta a variância.
- 🔻Simplificar o modelo reduz a variância, mas aumenta o bias.

O objetivo é encontrar um ponto de equilíbrio onde o modelo não seja nem muito simples (evitando underfitting), nem excessivamente complexo (evitando overfitting).

## **Validação Cruzada**

A validação cruzada é uma técnica que avalia um modelo dividindo os dados em múltiplos subconjuntos, treinando o modelo em um subconjunto e testando-o nos restantes de forma iterativa. Isso tem como intuito avaliar como o modelo se comporta com dados inéditos, simulando uma situação de uso real.

#### *Dados i.i.d. (sem ordem temporal relevante)*

Quando as observações podem ser assumidas **independentes e identicamente distribuídas (i.i.d.)** e não há dependência temporal ou estrutural relevante, usa-se a CV (Cross Validation/Validação Cruzada) padrão:

- **K-Fold CV (aleatória):** particiona $ \mathcal{D} $ em $K$ blocos aproximadamente do mesmo tamanho. Em cada iteração $k$, treina-se no complemento do bloco $k$ e avalia-se no bloco $k$. A estimativa de desempenho é a média (ou mediana) das métricas ao longo dos $K$ folds.  
  $$
  \widehat{\text{Score}} = \frac{1}{K} \sum_{k=1}^K \text{score}\big(f^{(-k)}, \mathcal{D}^{(k)}\big)
  $$
  onde $ f^{(-k)} $ é o modelo treinado sem o fold $k$ e $ \mathcal{D}^{(k)} $ é o conjunto de validação do fold $k$.

- **Estratificada (classificação):** preserva a proporção de classes em cada fold.
- **Group K-Fold / Leave-One-Group-Out:** evita vazamento entre grupos correlacionados (mesmo usuário, empresa, etc.).

> **Observação:** Em dados i.i.d., é comum embaralhar as amostras antes de gerar os folds; em séries temporais, **não**.


#### *Séries temporais (ordem temporal relevante)*

Quando há dependência temporal (autocorrelação, tendência, sazonalidade) ou risco de **vazamento temporal**, a K-Fold aleatória **não é adequada**. Em vez disso, usam-se partições que **respeitam a ordem** e impõem que o **treino seja estritamente anterior** ao **validação/teste**.

##### Validação “rolling origin” (walk-forward) com janela **expansiva**
- Em cada iteração $t$, o modelo treina em $[1, t]$ e valida em $(t, t+h]$ (típico $h=1$ para “um passo à frente”).
- Sequência de splits:
  $$
  \text{Train}_1 = [1{:}t_1],\ \text{Val}_1 = (t_1{:}t_1+h];\quad
  \text{Train}_2 = [1{:}t_2],\ \text{Val}_2 = (t_2{:}t_2+h];\ \ldots
  $$
- **Propriedades:** usa toda a história acumulada; adequado quando a relação $y_t \mid x_{\le t}$ é relativamente estável no tempo.

##### Validação “rolling window” com janela **deslizante (fixa)**
- Mantém uma janela fixa de treino de comprimento $W$: treina em $[t-W+1, t]$ e valida em $(t, t+h]$.
- **Propriedades:** dá mais ênfase à dinâmica recente; útil em ambientes com **não-estacionaridade**.

##### **Blocked / Purged K-Fold** para séries temporais
- Divide a série em $K$ blocos **contíguos** (sem embaralhar). Em cada iteração, um bloco é validação e os demais (anteriores) compõem o treino.  
- **Purging / Embargo:** insere-se um **gap temporal** entre as janelas de treino e validação para evitar vazamento por **sobreposição de janelas** ou **labels** (comum em finanças). Se o label usa informações até $t+\ell$, impõe-se um embargo $g \ge \ell$ entre o fim do treino e o início da validação.

##### Agregação de métricas no tempo
- Para horizontes de previsão $h$, avalia-se uma métrica $m$ (ex.: RMSE, MAE, MAPE, AUC) em cada iteração e agrega-se:
  $$
  \widehat{m} = \frac{1}{S} \sum_{s=1}^{S} m_s
  $$
  onde $S$ é o número de splits walk-forward. Intervalos de confiança podem ser obtidos por suposições assintóticas ou por *block bootstrap*.

## **Problemas de classificação**

### **O que é um problema de classificação?**

A classificação é o processo de reconhecimento, compreensão e agrupamento de objetos e ideias em categorias predefinidas. Utilizando conjuntos de dados de treinamento previamente categorizados, algoritmos de classificação em machine learning conseguem categorizar novos dados de forma precisa.

Esses algoritmos analisam dados de entrada para prever a probabilidade de que novos dados pertençam a uma das categorias estabelecidas.

Em termos simples, a classificação é uma forma de reconhecimento de padrões, em que os algoritmos identificam padrões nos dados de treinamento e aplicam esse conhecimento a novos conjuntos de dados.

**Motivação:** Suponha que você tenha um conjunto de dados com características de vários clientes de um banco que desejam obter empréstimos. Seus dados possuem um conjunto de características desses clientes como idade, renda, nível de educação, entre outros. 

Baseando-se no conjunto de características fornecidas, você deseja **classificar** os clientes entre aqueles que terão o empréstimo aprovado e aqueles que não terão o empréstimo aprovado

Formalmente, em problemas de classificação o objetivo é prever uma *class label*, uma lista de possibilidades pré-determinadas e que são variáveis discretas.

Na motivação acima, a nossa *class label* era se a pessoa teria o crédito aprovado ou não. Perceba que a resposta só assume dois valores possíveis, sim ou não (1 ou 0 em linguagem matemática). Além disso, podemos chamar essa variável de discreta porque ela só assume dois valores possíveis, ela "dá um salto" de 0 para 1.

Os problemas de classificação podem ser separados em:

- Classificação binária (binary classification)
- Classificação multiclasse (Multi-class classification)
- Classificação multirótulo (Multi-label Classification)
- Classificação desbalanceada (Imbalanced Classification)

### **Classificação binária (binary classification)**

O objetivo da classificação binária é classificar cada observação (vetor de características) tendo como possibilidade de resposta (label) exatamente duas classes. Você pode pensar na classificação binária como tentar responder uma pergunta do tipo sim ou não. Um email é um span? sim ou não. Um cliente terá seu pedido de empréstimo aprovado? sim ou não.

Neste cenário, podemos dizer que a class label é mutuamente exclusiva. Ou seja, ou uma observação é classificada como sim ou ela é classifica como não. É impossível uma observação ser classficadas como sim e não ao mesmo tempo.

📝 **Observação**: No contexto de classificação binária, é comum usar True ou False, positivo ou negativo, 1 ou 0 para se referir a uma resposta do tipo "sim ou não". Não se preocupe, são apenas maneiras diferentes de se referir a mesma coisa.

### **Classificação multiclasse (Multi-class classification)**

Semelhante a classificação binária, na classificação multiclasse também queremos classificar cada observação no nosso conjunto de dados. Porém, nossa lista de possibilidades pré-determinadas agora é maior que duas. Porém, de maneira semelhante, as class labels ainda são mutuamente exclusivas e discretas.

**Exemplo:** Se tivermos um conjunto de dados com características de alunos da FEA, podemos querer classificá-los de acordo com o curso em que eles estão matriculados. As possíveis respostas (class labels) são (i) Administração, (ii) Economia, (iii) Contabilidade ou (iv) Atuária. Perceba que um aluno não pode estar matrículado em dois ou mais destes cursos ao mesmo tempo.

### **Classificação multirótulo (Multi-label Classification)**

Semelhante a classificação multiclasse, queremos classificar cada observação na nossa base de dados em uma lista de possibilidades pré-determinadas em duas ou mais class labels. Porém, no caso da classificação multirótulo, as labels agora não são mais mutuamente exclusivas.

Pense em um problema em que queremos classificar um vetor de característcas em X, Y, e/ou Z. Em um problema de multirótulo, é totalmente possível que uma observação seja classficada como X e Y ou Y e Z **ao mesmo tempo**. Estranho né? Mas um exemplo deixa tudo mais claro.

**Exemplo:** Pense agora que temos um conjunto de dados de vários filmes e queremos classificá-los de acordo com seus gêneros. Perceba agora que os gêneros de um filme não são mutuamente exclusivas, é totalmente possível que um filme seja de comédia e ao mesmo tempo seja um filme de ação ou que um filme seja de terror e de suspense psicológico ao mesmo tempo. Ou seja, é totalmente possível que cada observação tenha uma ou mais label

### **Classificação desbalanceada (Imbalanced Classification)**

A classificação desbalanceada não é exatamente uma categoria de classificação diferente, mas sim um ponto de atenção que devemos ter quando trabalhamos com qualquer problema de classificação abordado nos tópicos anteriores.

Ela acontece quando as class labels do nosso conjunto de dados não está está balanceada. Neste caso, temos que as observações serão classificadas majoritamente de um tipo e poucas serão classificadas de outro.

**Exemplo:** Suponha que uma doença rara afeta apenas 1% da população.

Se nossa base de dados de dados for representativa da população, apenas cerca de 1% deveria ser classficado como positivo para a doença e 99% deveria ser negativo.

Apesar de não ser uma categoria diferenciada de classificação, é importante que tenhamos noção se estivermos trabalhando com um problema desse tipo porque as técnicas e modelos usuais que veremos podem não funcionar muito bem neste contexto. 

Outro ponto de atenção necessário é quando tivermos avaliando um modelo nesse contexto.

### **O que é um classificador?**

Um classificador é um **algoritmo** de Machine Learning que é utilizado para mapear cada vetor de características no conjunto de dados a uma categoria específica. Conforme nossas definições iniciais, pense no classificador como um **conjunto de regras** que definem a metodologia utilizada para que o modelo que você está treinando produza o resultado esperado.

Estes algoritmos, de maneira geral, implementam métodos matemáticos e estatísticos sofisticados para classificar as observações do conjunto de dados.

Alguns exemplos de classificadores que veremos ao longo do case são:
- KNN (K-Nearest Neighbor)
- Naive Bayes
- Regressão Logística
- Máquinas de Vetores de Suporte (SVC)
- Árvores de Decisão

Passaremos em mais detalhes por cada um deles, então não se preocupe em querer entender todos neste momento. Apenas tenha em mente que cada um desses classificadores segue um algoritmo específico para produzir o resultado final.

### **Prática**

Visando tornar o material um pouco mais prático. Ao longo de alguns tópicos abaixo iremos utilizar um dataset de prática fornecido pela biblioteca Scikit-Learn. o Scikit-Learn (ou somente Sklearn) é a principal biblioteca de Machine Learning do Python e fundamental para nosso objetivo neste case. Dessa forma, recomendamos fortemente que o leitor dedique um tempo a consultar a documentação e, se necessário, procurar fontes externas para entender o seu uso.

[Documentação Scikit-Learn](https://scikit-learn.org/stable/)

**Descrição do Dataset: Análise de Vinhos Italianos**

Origem e Objetivo:

Este dataset contém os resultados de uma análise química realizada em vinhos cultivados na mesma região da Itália, mas provenientes de três produtores (ou cultivares/castas) distintos. O objetivo principal é classificar os vinhos em um desses três produtores com base em suas características químicas. É um exemplo clássico para problemas de reconhecimento de padrões e classificação.

**Características (Features) Analisadas:**

As 13 características presentes no dataset representam diferentes componentes químicos e propriedades físicas dos vinhos, que podem ajudar a distinguir suas origens:

Álcool: Refere-se ao teor alcoólico do vinho, uma das suas características fundamentais.

Ácido Málico: Um dos principais ácidos orgânicos encontrados nas uvas e no vinho, contribui para o sabor e acidez.

Cinzas: Representa o conteúdo mineral do vinho, obtido após a evaporação e queima do resíduo seco. Indica a quantidade total de minerais.

Alcalinidade das Cinzas: Mede a alcalinidade do resíduo mineral (cinzas), o que pode estar relacionado com a composição do solo do vinhedo.

Magnésio: Quantidade deste mineral específico, importante para diversas reações bioquímicas na uva e no vinho.

Fenóis Totais: Compostos orgânicos que afetam o sabor, cor e sensação na boca (adstringência) do vinho. Incluem taninos e outros antioxidantes.

Flavonoides: Um subgrupo importante de compostos fenólicos, conhecidos por seus benefícios à saúde e impacto nas características sensoriais do vinho (cor, corpo, adstringência).
Fenóis Não Flavonoides: Outro grupo de compostos fenólicos que também contribuem para as propriedades do vinho.

Proantocianidinas: São taninos condensados, um tipo específico de flavonoide que contribui significativamente para a adstringência (aquela sensação de "boca seca") e cor dos vinhos tintos.

Intensidade da Cor: Medida quantitativa da intensidade da cor do vinho.

Tonalidade (Matiz): Descreve a cor específica do vinho (por exemplo, se é mais para o vermelho-rubi, vermelho-púrpura, etc.).

DO280/DO315 de vinhos diluídos: Uma medição espectrofotométrica (Densidade Óptica em comprimentos de onda de 280nm e 315nm). Essa razão pode estar relacionada à concentração de proteínas e outros compostos fenólicos que absorvem luz UV, ajudando a caracterizar o vinho.

Prolina: Um aminoácido frequentemente encontrado em uvas e vinhos, cuja concentração pode variar dependendo da variedade da uva e das condições de cultivo.


```python
# Caso não tenha o sklearn instalado, instale-o com o comando (descomente a linha abaixo):
# pip install -U scikit-learn
```


```python
# Começamos importando as bibliotecas necessárias
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Tendo o sklearn instalado, começamos importando nosso dataset de classificação
# Para praticar os conceitos que iremos percorrer
from sklearn.datasets import load_wine

# Carregamos o dataset
wine = load_wine()
# E o transformamos em um DataFrame do Pandas
df = pd.DataFrame(data=wine.data, columns=wine.feature_names)
# Adicionamos a coluna de classes
df['target'] = wine.target

# Tradução das colunas para o portugues
df = df.rename(columns={'alcohol': 'Álcool',
                        'malic_acid': 'Ácido Málico',
                        'Ash': 'Cinzas',
                        'alcalinity_of_ash': 'Alcalinidade das Cinzas',
                        'magnesium': 'Magnésio',
                        'total_phenols': 'Fenóis Totais',
                        'flavanoids': 'Flavonoides',
                        'nonflavanoid_phenols': 'Fenóis Não Flavonoides',
                        'proanthocyanins': 'Proantocianidinas',
                        'color_intensity': 'Intensidade da Cor',
                        'hue': 'Tonalidade',
                        'od280/od315_of_diluted_wines': 'DO280/DO315 de vinhos diluídos',
                        'proline': 'Prolina'
                        })

# E exibimos as 5 primeiras linhas
df.head()
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Álcool</th>
      <th>Ácido Málico</th>
      <th>ash</th>
      <th>Alcalinidade das Cinzas</th>
      <th>Magnésio</th>
      <th>Fenóis Totais</th>
      <th>Flavonoides</th>
      <th>Fenóis Não Flavonoides</th>
      <th>Proantocianidinas</th>
      <th>Intensidade da Cor</th>
      <th>Tonalidade</th>
      <th>DO280/DO315 de vinhos diluídos</th>
      <th>Prolina</th>
      <th>target</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>14.23</td>
      <td>1.71</td>
      <td>2.43</td>
      <td>15.6</td>
      <td>127.0</td>
      <td>2.80</td>
      <td>3.06</td>
      <td>0.28</td>
      <td>2.29</td>
      <td>5.64</td>
      <td>1.04</td>
      <td>3.92</td>
      <td>1065.0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>13.20</td>
      <td>1.78</td>
      <td>2.14</td>
      <td>11.2</td>
      <td>100.0</td>
      <td>2.65</td>
      <td>2.76</td>
      <td>0.26</td>
      <td>1.28</td>
      <td>4.38</td>
      <td>1.05</td>
      <td>3.40</td>
      <td>1050.0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>13.16</td>
      <td>2.36</td>
      <td>2.67</td>
      <td>18.6</td>
      <td>101.0</td>
      <td>2.80</td>
      <td>3.24</td>
      <td>0.30</td>
      <td>2.81</td>
      <td>5.68</td>
      <td>1.03</td>
      <td>3.17</td>
      <td>1185.0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>14.37</td>
      <td>1.95</td>
      <td>2.50</td>
      <td>16.8</td>
      <td>113.0</td>
      <td>3.85</td>
      <td>3.49</td>
      <td>0.24</td>
      <td>2.18</td>
      <td>7.80</td>
      <td>0.86</td>
      <td>3.45</td>
      <td>1480.0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>13.24</td>
      <td>2.59</td>
      <td>2.87</td>
      <td>21.0</td>
      <td>118.0</td>
      <td>2.80</td>
      <td>2.69</td>
      <td>0.39</td>
      <td>1.82</td>
      <td>4.32</td>
      <td>1.04</td>
      <td>2.93</td>
      <td>735.0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>


Com o objetivo de exemplificar alguns tópicos abaixo, iremos treinar um modelo simples de knn de classificação (não se preocupe, iremos explicar oque é KNN).

O bloco de código abaixo cria, treina e faz previsões de um modelo da maneira mais simples possível para que o utilizemos para mostrar como implementar em python os tópicos que formos cobrir em seguida. Ele tem pode ser utilizado como uma base para o projeto que você for fazer para praticar os conceitos aprendidos.


```python
# Importa o modelo KNN
from sklearn.neighbors import KNeighborsClassifier

# Instancia o modelo KNN
knn = KNeighborsClassifier(n_neighbors=3)

# Separa os dados em variáveis independentes (X) e dependentes (y)
X = df.drop(columns=['target'])
y = df['target']

# Utiliza o método train_test_split para dividir os dados em conjuntos de treino e teste
from sklearn.model_selection import train_test_split

# Divide os dados em 80% para treino e 20% para teste
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Treina o modelo KNN com os dados de treino
knn.fit(X_train, y_train)

# Faz previsões com os dados de teste
y_pred = knn.predict(X_test)
```

### **Métricas de Avaliação para Classificação**

#### **Acurácia**

A Acurácia é o método mais simples e direto de se avaliar o resultado gerado por um modelo de Classificação

Em resumo, ela mostra a **porcentagem de classificações corretas que o modelo fez**. Pensando de outra forma, a acurácia é a **soma das previsões corretas** dividida pelo **total de previsões que o modelo fez**.

A fórmula que define a Acurácia é a seguinte:

$$
ACC = \frac{TP + TN}{TP + TN + FP + FN} 
$$

Onde:

$TP$ = True Positive, $TN$ = True Negative, $FP$ = False Positive, $FN$ = False Negative


```python
# Importa a função de acurácia do sklearn metrics
from sklearn.metrics import accuracy_score

# Calcula a acurácia
accuracy = accuracy_score(y_test, y_pred)

print(f'Acurácia do modelo KNN: {accuracy:.5f}')
```

    Acurácia do modelo KNN: 0.80556
    

#### **Precisão**

Refere-se à proporção de previsões positivas corretas em relação ao total de previsões positivas feitas pelo modelo. A fórmula da métricas de Precisão é a seguinte:

$$
Precison = \frac{TP} {TP + FP}
$$

A Precisão é bastante usada quando o objetivo é limitar o número de falsos positivos. Um exemplo é um modelo que tenta prever se um novo remédio sera efetivo no tratamento de uma doença. Nesse caso, é fundamental que o modelo minimize os falsos positivos para uma correta mensuração da eficácia do remédio. Esse é um caso em que é fundamental o modelo possuir uma alta precisão.


```python
# Calcula a precisão do modelo
from sklearn.metrics import precision_score

# Calcula a precisão
precision = precision_score(y_test, y_pred, average='weighted')
print(f'Precisão do modelo KNN: {precision:.5f}')
```

    Precisão do modelo KNN: 0.82315
    

#### **Recall (ou Sensitivity)**

Recall, também chamado de Sensitivity em alguns materiais, mede quanto das observações que são positivas no conjunto de dados foram capturadas corretamente pelo modelo. 

$$
Sensitivity=\frac{TP}{TP + FN}
$$

Essa métrica é crucial quando é essencial capturar todos os casos positivos, como no diagnóstico de doenças graves ou detecção de fraudes. Ou seja, queremos minimizar a ocorrência de falsos negativos. No exemplo de diagnóstico de uma doença, é fundamental que não deixemos nenhum paciente doente não ser identificado corretamente pelo modelo.

📝**Observação:**

Existe um trade-off entre otimizar o **recall** e otimizar a **precisão**. É possível obter um recall perfeito de forma trivial se você prever que todas as amostras pertencem à classe positiva — dessa forma, não haverá falsos negativos, mas também não haverá verdadeiros negativos. No entanto, ao prever todas as amostras como positivas, haverá muitos falsos positivos, o que fará com que a precisão seja muito baixa.

Por outro lado, se você encontrar um modelo que prevê como positiva apenas a única amostra da qual tem total certeza (supondo que essa amostra seja realmente positiva) e classifica todas as outras como negativas, a precisão será perfeita. Contudo, o recall será muito ruim, pois o modelo deixará de identificar outras amostras positivas.


```python
# Calcula o recall do modelo
from sklearn.metrics import recall_score

# Calcula o recall
recall = recall_score(y_test, y_pred, average='weighted')

print(f'Recall do modelo KNN: {recall:.5f}')
```

    Recall do modelo KNN: 0.80556
    

#### **F1-Score**

Vimos que tanto a Precisão quanto o Recall são importantes medidas para avaliar um modelo de classificação. Como vimos, devemos fazer um trade-off entre as duas métricas e analisar ambas para garantirmos que estamos com um bom modelo.

Uma maneira de sumarizar ambas as métricas em uma só é o chamado **F1-Score**. Ele é a média harmonica entre a Precisão e o Recall.

$$
F1-Score = {2}\times{\frac{\text{Precision}\times\text{Recall}}{\text{Precision}+\text{Recall}}}
$$

O F1-Score pode ser uma medida melhor que a acurácia em conjunto de dados em classificação binária desbalanceada.


```python
# Calcula o F1-score do modelo
from sklearn.metrics import f1_score

# Calcula o F1-score
f1 = f1_score(y_test, y_pred, average='weighted')

print(f'F1-score do modelo KNN: {f1:.5f}')
```

    F1-score do modelo KNN: 0.81054
    

#### **Curva ROC-AUC**

A curva ROC (Receiver Operation Characteristcs) é uma curva em um gráfico que coloca a taxa de false positive (FPR) contra a taxa de true positive (TPR). Perceba que a taxa de true positive é apenas outro nome para o Recall enquanto a taxa de false positive é a fração de falsos positivos em relação a todos as observações classificadas como negativas na nossa base de dados. 

$$
FPR = {\frac{FP}{FP+TN}}
$$

<p align='center'>
<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjhApq1sW6tLaFEXU4jK9g5YzvQBsudIhRUNkSBSYldIPaQ1Rwny1Z7Sj-Rt_8W2CCVKGCMDqu5GoSu4Cao1rAkfwVjgPfINcRuJTGjR-JPXbxY7NtgKQbFYUT2z6IfOAaeZadKVjdvQlkSG7JbDntxsUXWatk1tOUk0XPGBzbnKIRL6f929n8u3Pk1alQf/s1600-rw/roc.png" width="500"></img>
</p>

Na curva ROC, a curva ideal é próxima ao canto superior esquerdo. Perceba que próximo deste ponto é **maximizada** a taxa de True Positives e **minimizada** a taxa de False Positives.

As vezes queremos resumir a informação fornecida pela curva ROC em um simples número. É aqui que entra a sigla AUC. Ela significa Area Under the Curve (Área abaixo da Curva). Ou seja, podemos calcular a área abaixo da curva ROC para avaliarmos a qualidade do modelo.

Intuitivamente, é perceptível que queremos que essa área tenha o maior valor possível. Isso acontece porque desejamos que a curva ROC alcance o mais próximo possível do canto superior esquerdo (no limite, chegando no número 1 do eixo vertical). Dessa forma, quanto maior o valor da AUC, melhor a performance do modelo.


```python
# Constrói a curva ROC e calcula a AUC
from sklearn.metrics import roc_curve, auc

# Calcula as probabilidades de cada classe
y_prob = knn.predict_proba(X_test)

# Calcula a curva ROC
fpr, tpr, thresholds = roc_curve(y_test, y_prob[:, 1], pos_label=1)

# Calcula a AUC
roc_auc = auc(fpr, tpr)
print(f'AUC do modelo KNN: {roc_auc:.5f}')

# Plota a curva ROC
plt.figure()
plt.plot(fpr, tpr, color='blue', label=f'Curva ROC (AUC = {roc_auc:.2f})')
plt.xlim([0.0, 1.0])
plt.ylim([0.0, 1.05])
plt.xlabel('Taxa de Falsos Positivos')
plt.ylabel('Taxa de Verdadeiros Positivos')
plt.title('Curva ROC do modelo KNN')
plt.legend(loc='lower right')
plt.show()
```

    AUC do modelo KNN: 0.88636
    


    
![png](case_ia_files/case_ia_104_1.png)
    


## **Problemas de regressão**

### **O que é um problema de regressão?**

Problemas de regressão é outro tipo de problemas dentro do campo do **aprendizado supervisionado**

Se problemas de classificação é quando queremos prever uma variável discreta (também chamada de variável categorica), em problemas de **Regressão** o objetivo é fazer previsão de uma **varíavel contínua**, ou uma variável do tipo float em termos de programação (ou uma variável real em termos matématicos).

Um exemplo clássico de um problema de regressão é prever o salário de uma pessoa com base em um vetor de caracteríscas como a idade, anos de educação, área de trabalho, entre outros.

💡 **Dica**: Uma maneira fácil de distinguir entre problemas de classificação e problema de regressão é pensar se há continuidade ou se há algum "salto" na variável que você está tentando prever. No caso da renda de uma pessoa há claramente uma continuidade, uma pessoa pode ganhar R$ 3.000,00 ou R$ 3.001,00, e assim por diante. Teoricamente, há um conjunto infinito de valores a variável renda pode assuim. 

Porém, em problemas de classificação, há um claro salto na variável target. Se queremos prever, por exemplo, se uma pessoa terá um crédito aprovado ou não, só há duas respotas possível, sim ou não.

### **O que é um regressor?**

De maneira semelhante a um classificador, um **regressor** é um algoritmo de Machine Learning que mapeia cada vetor de características na base de dados a um output. Porém, neste caso, não estamos mais falando de categorias e sim a um output contínuo. 

Os regressores também se utilizam de métodos matemáticos e estátiscos para regredir uma variável target (também chamada de variável dependente) a um vetor de características (variáveis independentes).

Alguns dos principais regressores são:
- Regressão Linear
- Lasso Regression
- Ridge Regression
- Máquinas de Vetores de Suporte para Regressão (SVR)
- Árvores de Regressão


#### **Prática**

De maneira semelhante ao tópico de classificação, iremos mostrar como implementar alguns tópicos de regressão em python.

**Descrição do Dataset: California Housing Prices**

Origem e Objetivo:

Este dataset é baseado em dados do censo de 1990 dos Estados Unidos, especificamente para grupos de quarteirões (block groups) na Califórnia. O objetivo principal ao utilizar este dataset é prever o valor mediano das casas em cada um desses grupos de quarteirões, com base em um conjunto de características demográficas e geográficas.

**Características (Features) Analisadas:**

Renda Mediana: Renda média dos moradores da região.

Idade Mediana das Casas: Idade média das casas na região.

Média de Cômodos: Número médio de cômodos nas casas da região.

Média de Quartos: Número médio de quartos nas casas da região.

População: Número total de pessoas que vivem na região.

Ocupação Média: Número médio de moradores por casa na região.

Latitude: Posição geográfica da região (norte-sul).

Longitude: Posição geográfica da região (leste-oeste).

Valor Mediano das Casas (target): Preço mediano das casas na região (geralmente em unidades de $100.000).


```python
# Começamos importando as bibliotecas necessárias
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Importa o dataset
from sklearn.datasets import fetch_california_housing

# Carrega o dataset
california_housing = fetch_california_housing()
# Transforma em um DataFrame
df_california = pd.DataFrame(data=california_housing.data, columns=california_housing.feature_names)
# Adiciona a coluna de classes
df_california['target'] = california_housing.target

# Tradução das colunas para o portugues
df_california = df_california.rename(columns={'MedInc': 'Renda Mediana',
                                               'HouseAge': 'Idade Média',
                                               'AveRooms': 'Número Médio de Cômodos',
                                               'AveBedrms': 'Número Médio de Quartos',
                                               'Population': 'População',
                                               'AveOccup': 'Ocupação Média',
                                               'Latitude': 'Latitude',
                                               'Longitude': 'Longitude',
                                               'target': 'Valor Mediano da Casa'
                                               })

# E exibe as 5 primeiras linhas
df_california.head()
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Renda Mediana</th>
      <th>Idade Média</th>
      <th>Número Médio de Cômodos</th>
      <th>Número Médio de Quartos</th>
      <th>População</th>
      <th>Ocupação Média</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Valor Mediano da Casa</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>8.3252</td>
      <td>41.0</td>
      <td>6.984127</td>
      <td>1.023810</td>
      <td>322.0</td>
      <td>2.555556</td>
      <td>37.88</td>
      <td>-122.23</td>
      <td>4.526</td>
    </tr>
    <tr>
      <th>1</th>
      <td>8.3014</td>
      <td>21.0</td>
      <td>6.238137</td>
      <td>0.971880</td>
      <td>2401.0</td>
      <td>2.109842</td>
      <td>37.86</td>
      <td>-122.22</td>
      <td>3.585</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7.2574</td>
      <td>52.0</td>
      <td>8.288136</td>
      <td>1.073446</td>
      <td>496.0</td>
      <td>2.802260</td>
      <td>37.85</td>
      <td>-122.24</td>
      <td>3.521</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5.6431</td>
      <td>52.0</td>
      <td>5.817352</td>
      <td>1.073059</td>
      <td>558.0</td>
      <td>2.547945</td>
      <td>37.85</td>
      <td>-122.25</td>
      <td>3.413</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3.8462</td>
      <td>52.0</td>
      <td>6.281853</td>
      <td>1.081081</td>
      <td>565.0</td>
      <td>2.181467</td>
      <td>37.85</td>
      <td>-122.25</td>
      <td>3.422</td>
    </tr>
  </tbody>
</table>
</div>


Da mesma forma que no exemplo de classificação. Iremos treinar um modelo simples de regressão linear para ilustrar os tópicos seguintes (mais uma vez, não se preocupe, iremos explicar oque é uma regressão linear)


```python
# Importa o modelo de regressão linear
from sklearn.linear_model import LinearRegression

# Instancia o modelo de regressão linear
lin_reg = LinearRegression()

# Separa os dados em variáveis independentes (X) e dependentes (y)
X_california = df_california.drop(columns=['Valor Mediano da Casa'])
y_california = df_california['Valor Mediano da Casa']

# Utiliza o método train_test_split para dividir os dados em conjuntos de treino e teste
from sklearn.model_selection import train_test_split

# Divide os dados em 80% para treino e 20% para teste
X_train, X_test, y_train, y_test = train_test_split(X_california, y_california, test_size=0.2, random_state=42)

# Treina o modelo de regressão linear com os dados de treino
lin_reg.fit(X_train, y_train)

# Faz previsões com os dados de teste
y_pred_california = lin_reg.predict(X_test)
```

### **Métricas de Avaliação para Regressão**

#### **MAE**

O Erro Médio Absoluto (MAE - Mean Squared Error), de maneira simplificada, mede a diferença média entro valor predito pelo modelo e o valor real observado. Por haver valores positivos e negativos, é adicionado o módulo da diferença. Assim, queremos que o MAE tenha o menor valor possível.

A fórmula do MAE é a seguinte:

$$
MAE(y, \hat{y}) = \frac{1}{n} \sum_{i=1}^{n} |y_i - \hat{y}_i|
$$

Uma vantagem do MAE é que sua escala é a mesma dos dados, facilitando sua interpretação. Por exemplo, se estamos prevendo o salário e temos um MAE de 100, significa que, em média, o modelo tem um erro de R$100.00.

a desvantagem do MAE é que ele é uma métrica não afetada por outliers. Isso acontece porque cada erro tem possui o mesmo peso. 




```python
# Importa a função de erro médio absoluto do sklearn metrics
from sklearn.metrics import mean_absolute_error

# Calcula o erro médio absoluto
mae = mean_absolute_error(y_test, y_pred_california)
print(f'Erro Médio Absoluto do modelo: {mae:.5f}')
```

    Erro Médio Absoluto do modelo: 0.53320
    

#### **MSE**

O erro quadrático médio (MSE — Mean Squared Error) é semelhante a métrica MAE, também calculado o erro médio do modelo entre o valor predito e o valor real. Porém, no MSE elevamos a diferença ao quadrado. A ideia por trás disto é penalizarmos valores que sejam muito diferentes entre o valor previsto e o valor real. Também queremos que o MSE tenha o menor valor possível.

A fórmula do MSE é a seguinte:

$$
MSE(y, \hat{y}) = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2
$$

Um desvantagem do MSE é que, por elevarmos o valor ao quadrado, sua escala fica distorcida. Para contornar esse problema, podemos extrair a raiz do MSE. Oque nos leva a próxima métrica


```python
# Importa a função de erro quadrático médio do sklearn metrics
from sklearn.metrics import mean_squared_error

# Calcula o erro quadrático médio
mse = mean_squared_error(y_test, y_pred_california)
print(f'Erro Quadrático Médio do modelo: {mse:.5f}')
```

    Erro Quadrático Médio do modelo: 0.55589
    

#### **RMSE**

A raiz do erro quadrático médio (RMSE — Root Mean Squared Error) é basicamente o mesmo cálculo do MSE, onde queremos penalizar grandes diferenças entre o valor previsto e o valor real. Mas, como já comentamos, extraímos a raiz quadrado desse valor para lidar com o problema de interpretação das unidades. Ao fazermos isso, unidade fica na mesma escala do dado original.

$$
RMSE(y, \hat{y}) = \sqrt[]{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2)}
$$

📝 **Observação**: Apesar de estar na mesma unidade que o MAE, as métricas costumam não ter o mesmo valor. Isso vem do fato do RMSE estar capturando os outliers. 


```python
# Importa a funçção de raiz do erro quadrático médio do sklearn metrics
from sklearn.metrics import mean_squared_error

# Calcula a raiz do erro quadrático médio
rmse = np.sqrt(mse)
print(f'Raiz do Erro Quadrático Médio do modelo: {rmse:.5f}')
```

    Raiz do Erro Quadrático Médio do modelo: 0.74558
    

#### **MAPE**

O erro percentual absoluto médio (MAPE — Mean Absolute Percentual Error) é uma métrica que mostra a porcentagem de erro em relação aos valores reais. A ideia é bastante parecida com as métricas de erro médio apresentadas anteriormente, porém aqui estamos pensando em termos percentuais. Então se tivermos um MAPE de 12% por exemplo, significa que o modelo faz, em média, previsões que diferem em 12% dos valores reais.

A fórmula do MAPE é:

$$

MAPE(y, \hat{y}) = \frac{1}{n} \sum_{i=1}^{n} |\frac{y_i - \hat{y}_i}{y_i}| \times 100

$$


```python
# Importa a função de erro percentual absoluto médio do sklearn metrics
from sklearn.metrics import mean_absolute_percentage_error

# Calcula o erro percentual absoluto médio
mape = mean_absolute_percentage_error(y_test, y_pred_california)
print(f'Erro Percentual Absoluto Médio do modelo: {mape:.5f}')
```

    Erro Percentual Absoluto Médio do modelo: 0.31952
    

#### **$R^{2}$**

A métrica $R^2$, representa o percentual de variância que é explicada pelo modelo. Os resultados vão de 0 a 1 (ou de 0% a 100% em termos percentuais). Quanto maior o $R^2$, mais explicativo é o modelo. 

A fórmula é a seguinte:

$$
R^2(y,\hat{y}) = 1 - \frac{\sum_{i=1}^{n} (y_i - \hat{y}_i)2}{\sum_{i=1}^{n} (y_i - \overline{y}_i)^2}
$$

Podemos pensar no $R^2$ como o poder explicativo do seu modelo. No exemplo do salário, regredindo contra idade, anos de educação e setor de atividade. Se tivermos um $R^2$ de 60%, significa que nosso modelo explica 60% da variação do salário.

Se isso for alto ou baixo, vai depender de outras métricas e outros benchmarks.



```python
# Importa a funlção de R² do sklearn metrics
from sklearn.metrics import r2_score

# Calcula o R²
r2 = r2_score(y_test, y_pred_california)
print(f'R² do modelo: {r2:.5f}')
```

    R² do modelo: 0.57579
    

## **Um pouco de feature engineering**

A Feature Engineering é o processo de extração, manipulação e transformação de dados brutos, permitindo que esses dados se transformem em variáveis que um modelo de machine learning pode usar para alcançar um objetivo desejado. A engenharia de recursos é um desafio porque envolve uma combinação de análise de dados, conhecimento do domínio de negócios e certa intuição.

Pense que dados, por si só, podem não significar muita coisa. Esse problema se torna ainda mais agravante nos dias atuais quando pensamos na quantidade massiva de dados gerados na era do big data. Mais do que nunca, temos um mar de dados a nossa disposição. Porém, devemos pensar, como tirar valor disso? Podemos pensar no processo de **feature engineering** de forma abrangente, como a maneira de transformar **dados** em **informação**.

Uma analogia é imaginar o trabalho de um minerador de ouro. Ele extrai rochas brutas (dados) e precisa processá-las para encontrar o ouro (informação útil). Do mesmo modo, a Feature Engineering extrai informações valiosas dos dados e traduz em uma linguagem que o modelo de machine learning consiga ler.

<p align=center>
<img src="https://www.kdnuggets.com/wp-content/uploads/Feature-Engineering.png" width=600></img>
<p>

Existem algumas recomendações para uma feature engineering que sempre devemos seguir e iremos abordar elas nos próximos tópicos. Porém, é necessário termos em mente que boa parte do processo de feature engineering vai variar em cada situação específica e boa parte dela vem de termos criatividade e expertise para olharmos para nossos dados e imaginar como podemos extrair valor deles.

### **Encoding**



De longe, a maneira mais comum de se representar variáveis categoricas é utilizando encoding. Imagine que uma de suas features em sua base de dados é uma coluna de nível educacional que possui como valores *Fundamental*, *Ensino Médio*, *Superior* e *Pós-Graduação*. Lembre-se que os modelos de machine learning nada mais são do que algoritmos matemáticos/estatísticos. Dessa forma, não podemos utilizar variáveis textuais no modelo, precisamos traduzir isso em linguagem matemática.


#### **One-hot encoding**
O método mais conhecido e utilizado é o **one-hot encoding** que cria uma coluna binária para cada categoria. Essas colunas também são chamadas de variáveis dummies.

No nosso exemplo, teríamos uma coluna fundamental que receberia valor 1 para cada observação com este nível educacional e 0 caso contrário, uma coluna ensino médio com valor 1 para cada observação com esse nível educacional e 0 caso contrário, e assim por diante.

📝 **Observação**: Devemos ter cuidado ao aplicar o one-hot encoding para não incorrermos no problema de multicolinearidade. Esse problema acontece quando uma coluna pode ser perfeitamente prevista a partir das outras. Isso cria redundância nos dados e pode atrapalhar alguns modelos estatísticos, como regressão linear, ao tornar os cálculos instáveis.

no nosso exemplo a última coluna (Pós-Graduação) pode ser perfeitamente inferida das outras três, pois Pós-Graduação = 1 - (Fundamental + Ensino Médio + Superior). Para contornamos esse problema, basta excluirmos uma coluna ao fazer o one-hot encoding

#### **Label encoding**

Outro método bastante utilizado para encoding é o label encoding. De maneira simples, ele converte os valores de uma variável categorica em números inteiros. No nosso exemplo, Fundamental poderia ser convertido para 0, Ensino médio = 1, Superior = 2 e Pós-Graduação = 3.

📝 **Observação**: Devemos ter o cuidado ao utilizar o label encoding porque os modelos podem interpretar essa transformação como uma relação ordinal. Por exemplo, o modelo pode entender que "Pós-Graduação" (3) é três vezes mais importante do que "Fundamental" (0), o que pode levar a inferências incorretas.

#### **Prática**

Para ilustrar a aplicação de encoding em python, iremos importar um novo dataset que possui variáveis categoricas.

Este dataframe contém dados de tripulantes do titanic.


```python
from sklearn.datasets import fetch_openml
import pandas as pd

# Carrega o dataset
titanic = fetch_openml('titanic', version=1, as_frame=True)
# Transforma em um DataFrame
df_titanic = pd.DataFrame(data=titanic.data, columns=titanic.feature_names)

# Adiciona a coluna de classes
df_titanic['survived'] = titanic.target

# Tradução das colunas para o portugues
df_titanic = df_titanic.rename(columns={'pclass': 'Classe',
                                        'name': 'Nome',
                                        'sex': 'Sexo',
                                        'age': 'Idade',
                                        'sibsp': 'Irmãos/Cônjuges',
                                        'parch': 'Pais/Filhos',
                                        'ticket': 'Bilhete',
                                        'fare': 'Tarifa',
                                        'cabin': 'Cabine',
                                        'embarked': 'Embarque',
                                        'boat': 'Bote',
                                        'body': 'Corpo',
                                        'home.dest': 'Destino',
                                        'survived': 'Sobreviveu'
                                        })

# E exibe as 5 primeiras linhas
df_titanic.head(3)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Classe</th>
      <th>Nome</th>
      <th>Sexo</th>
      <th>Idade</th>
      <th>Irmãos/Cônjuges</th>
      <th>Pais/Filhos</th>
      <th>Bilhete</th>
      <th>Tarifa</th>
      <th>Cabine</th>
      <th>Embarque</th>
      <th>Bote</th>
      <th>Corpo</th>
      <th>Destino</th>
      <th>Sobreviveu</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Allen, Miss. Elisabeth Walton</td>
      <td>female</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>24160</td>
      <td>211.3375</td>
      <td>B5</td>
      <td>S</td>
      <td>2</td>
      <td>NaN</td>
      <td>St Louis, MO</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Allison, Master. Hudson Trevor</td>
      <td>male</td>
      <td>0.9167</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>11</td>
      <td>NaN</td>
      <td>Montreal, PQ / Chesterville, ON</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>Allison, Miss. Helen Loraine</td>
      <td>female</td>
      <td>2.0000</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Montreal, PQ / Chesterville, ON</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Importa a função de one-hot encoding do sklearn
from sklearn.preprocessing import OneHotEncoder

# Instancia o OneHotEncoder
encoder = OneHotEncoder(drop='first')

# Aplica o one-hot encoding nas colunas categóricas
categorical_cols = ['Cabine']
X_titanic = df_titanic.drop(columns=['Sobreviveu'])
y_titanic = df_titanic['Sobreviveu']
X_titanic_encoded = encoder.fit_transform(X_titanic[categorical_cols]).toarray()
X_titanic_encoded_df = pd.DataFrame(X_titanic_encoded, columns=encoder.get_feature_names_out(categorical_cols))
X_titanic_encoded_df = pd.concat([X_titanic.drop(columns=categorical_cols).reset_index(drop=True), X_titanic_encoded_df], axis=1)

# E exibe as 5 primeiras linhas
X_titanic_encoded_df.head(3)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Classe</th>
      <th>Nome</th>
      <th>Sexo</th>
      <th>Idade</th>
      <th>Irmãos/Cônjuges</th>
      <th>Pais/Filhos</th>
      <th>Bilhete</th>
      <th>Tarifa</th>
      <th>Embarque</th>
      <th>Bote</th>
      <th>...</th>
      <th>Cabine_F E69</th>
      <th>Cabine_F G63</th>
      <th>Cabine_F G73</th>
      <th>Cabine_F2</th>
      <th>Cabine_F33</th>
      <th>Cabine_F38</th>
      <th>Cabine_F4</th>
      <th>Cabine_G6</th>
      <th>Cabine_T</th>
      <th>Cabine_nan</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Allen, Miss. Elisabeth Walton</td>
      <td>female</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>24160</td>
      <td>211.3375</td>
      <td>S</td>
      <td>2</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Allison, Master. Hudson Trevor</td>
      <td>male</td>
      <td>0.9167</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>S</td>
      <td>11</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>Allison, Miss. Helen Loraine</td>
      <td>female</td>
      <td>2.0000</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>S</td>
      <td>NaN</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
<p>3 rows × 198 columns</p>
</div>



Perceba a quantidade de colunas resultante. Talvez o one hot encoding não seja a melhor maneira de tratar a variável categorica neste caso.


```python
# Importa a função de label encoding do sklearn
from sklearn.preprocessing import LabelEncoder

# Instancia o LabelEncoder
label_encoder = LabelEncoder()

# Aplica o label encoding nas colunas categóricas
categorical_cols = ['Cabine']

X_titanic = df_titanic.drop(columns=['Sobreviveu'])
y_titanic = df_titanic['Sobreviveu']
X_titanic[categorical_cols] = X_titanic[categorical_cols].apply(label_encoder.fit_transform)

# E exibe as 5 primeiras linhas
X_titanic.head(3)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Classe</th>
      <th>Nome</th>
      <th>Sexo</th>
      <th>Idade</th>
      <th>Irmãos/Cônjuges</th>
      <th>Pais/Filhos</th>
      <th>Bilhete</th>
      <th>Tarifa</th>
      <th>Cabine</th>
      <th>Embarque</th>
      <th>Bote</th>
      <th>Corpo</th>
      <th>Destino</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Allen, Miss. Elisabeth Walton</td>
      <td>female</td>
      <td>29.0000</td>
      <td>0</td>
      <td>0</td>
      <td>24160</td>
      <td>211.3375</td>
      <td>43</td>
      <td>S</td>
      <td>2</td>
      <td>NaN</td>
      <td>St Louis, MO</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Allison, Master. Hudson Trevor</td>
      <td>male</td>
      <td>0.9167</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>79</td>
      <td>S</td>
      <td>11</td>
      <td>NaN</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>Allison, Miss. Helen Loraine</td>
      <td>female</td>
      <td>2.0000</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>79</td>
      <td>S</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
  </tbody>
</table>
</div>



Perceba que agora, a variável "Cabine" não é mais categorica, e sim númerica.

### **Scaling**

Scaling é o processo de transformar os valores númericos de uma base de dados para que eles fiquem dentro de uma mesma escala. Pense em uma base de dados em que temos idade e salário de várias pessoas. A variável idade deverá ter um range com algo em torno de 0 a 100, enquanto o salário pode ir de 0 a R$ 1.000.000,00 por exemplo. Muitos algoritmos de machine learning são sensíveis a escalas diferentes entre os dados.


```python
# Importa a função de min max scaling do sklearn
from sklearn.preprocessing import MinMaxScaler

# Instancia o MinMaxScaler
scaler = MinMaxScaler()

# Aplica o min max scaling na coluna idade
X_titanic = df_titanic.drop(columns=['Sobreviveu'])
y_titanic = df_titanic['Sobreviveu']
X_titanic['Idade'] = scaler.fit_transform(X_titanic[['Idade']])
# E exibe as 5 primeiras linhas
X_titanic.head(3)

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Classe</th>
      <th>Nome</th>
      <th>Sexo</th>
      <th>Idade</th>
      <th>Irmãos/Cônjuges</th>
      <th>Pais/Filhos</th>
      <th>Bilhete</th>
      <th>Tarifa</th>
      <th>Cabine</th>
      <th>Embarque</th>
      <th>Bote</th>
      <th>Corpo</th>
      <th>Destino</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Allen, Miss. Elisabeth Walton</td>
      <td>female</td>
      <td>0.361169</td>
      <td>0</td>
      <td>0</td>
      <td>24160</td>
      <td>211.3375</td>
      <td>B5</td>
      <td>S</td>
      <td>2</td>
      <td>NaN</td>
      <td>St Louis, MO</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Allison, Master. Hudson Trevor</td>
      <td>male</td>
      <td>0.009395</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>11</td>
      <td>NaN</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>Allison, Miss. Helen Loraine</td>
      <td>female</td>
      <td>0.022964</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
  </tbody>
</table>
</div>



### **Padronização**

Padronização é o processo de transformar a **distribuição** de uma variável de modo que ela tenha média 0 e desvio padrão 1. Esse é um método que pode ser interessante de usar quando os dados possuem uma distribuição normal ou quando há outliers, pois a média e o desvio padrão são menos afetados que os valores extremos no Min-Max Scaling.


```python
# Importa a função de normalização do sklearn
from sklearn.preprocessing import StandardScaler

# Instancia o StandardScaler
scaler = StandardScaler()

# Aplica a normalização na coluna idade
X_titanic = df_titanic.drop(columns=['Sobreviveu'])
y_titanic = df_titanic['Sobreviveu']
X_titanic['Idade'] = scaler.fit_transform(X_titanic[['Idade']])

# E exibe as 5 primeiras linhas
X_titanic.head(3)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Classe</th>
      <th>Nome</th>
      <th>Sexo</th>
      <th>Idade</th>
      <th>Irmãos/Cônjuges</th>
      <th>Pais/Filhos</th>
      <th>Bilhete</th>
      <th>Tarifa</th>
      <th>Cabine</th>
      <th>Embarque</th>
      <th>Bote</th>
      <th>Corpo</th>
      <th>Destino</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Allen, Miss. Elisabeth Walton</td>
      <td>female</td>
      <td>-0.061162</td>
      <td>0</td>
      <td>0</td>
      <td>24160</td>
      <td>211.3375</td>
      <td>B5</td>
      <td>S</td>
      <td>2</td>
      <td>NaN</td>
      <td>St Louis, MO</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Allison, Master. Hudson Trevor</td>
      <td>male</td>
      <td>-2.010496</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>11</td>
      <td>NaN</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>Allison, Miss. Helen Loraine</td>
      <td>female</td>
      <td>-1.935302</td>
      <td>1</td>
      <td>2</td>
      <td>113781</td>
      <td>151.5500</td>
      <td>C22 C26</td>
      <td>S</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Montreal, PQ / Chesterville, ON</td>
    </tr>
  </tbody>
</table>
</div>



### **Imputação de valores ausentes**

Imputação de valores ausentes é preencher lacunas quando certos dados não foram registrados. Ex.: um sensor meteorológico que falhou em medir a temperatura em algumas horas; um questionário online com a cidade deixada em branco; um log de e-commerce sem o tempo de permanência de certos usuários. Para lidar com isso, pode-se usar média/mediana (numéricos), moda (categóricos), forward/backward fill em séries temporais, KNN ou modelos de imputação multivariada. Faça a imputação apenas no conjunto de treino (ou dentro de cada fold) para evitar vazamento de informação e valide o impacto nas métricas do modelo.


```python
# Exemplo fictício de dados com valores ausentes
df_clientes = pd.DataFrame({
    'Idade': [25, np.nan, 42, 31, np.nan],
    'Salario': [3000.0, 4500.0, np.nan, 5200.0, 4100.0],
    'Cidade': ['A', 'B', None, 'A', None]
})

# Separa features (X) e alvo (y) apenas como exemplo (suponha que 'Cidade' não seja alvo)
X = df_clientes.copy()

# Imputação:
# - Numéricos: média para Idade, mediana para Salario
# - Categórico: moda para Cidade
X['Idade']   = X['Idade'].fillna(X['Idade'].mean())
X['Salario'] = X['Salario'].fillna(X['Salario'].median())
X['Cidade']  = X['Cidade'].fillna(X['Cidade'].mode().iloc[0])

print("Valores ausentes após a imputação:")
print(X.isnull().sum())

# Visualiza as 3 primeiras linhas
X.head()
```

    Valores ausentes após a imputação:
    Idade      0
    Salario    0
    Cidade     0
    dtype: int64
    




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Idade</th>
      <th>Salario</th>
      <th>Cidade</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>25.000000</td>
      <td>3000.0</td>
      <td>A</td>
    </tr>
    <tr>
      <th>1</th>
      <td>32.666667</td>
      <td>4500.0</td>
      <td>B</td>
    </tr>
    <tr>
      <th>2</th>
      <td>42.000000</td>
      <td>4300.0</td>
      <td>A</td>
    </tr>
    <tr>
      <th>3</th>
      <td>31.000000</td>
      <td>5200.0</td>
      <td>A</td>
    </tr>
    <tr>
      <th>4</th>
      <td>32.666667</td>
      <td>4100.0</td>
      <td>A</td>
    </tr>
  </tbody>
</table>
</div>



##### 💡 Alternativas possíveis:

- Imputação por moda 

- _KNN Imputer_

- _Iterative Imputer_

### **Criação de novas features**

A criação de novas features nada mais é do que transformar ou combinar variáveis para revelar padrões que o modelo sozinho talvez não capture. Exemplos comuns incluem: transformações (log, raiz, padronização), interações (produto/razão entre variáveis), agregações temporais (médias móveis), extração de componentes de data (mês, dia da semana) e codificação de categóricas. Sempre crie features usando apenas o treino (ou dentro de cada fold) para evitar vazamento de informação.


```python
# Exemplo fictício
df = pd.DataFrame({
    'Idade':  [22, 35, 41, 29, 33, 26],
    'Salario':[2500, 5200, 6800, 3900, 4500, 3100],
    'Cidade': ['A', 'B', 'A', 'C', 'B', 'A'],
    'Data':   pd.to_datetime(['2025-01-01','2025-01-02','2025-01-03','2025-01-04','2025-01-05','2025-01-06'])
})

# Trabalhe numa cópia
X = df.copy()

# 1) Transformações
X['log_Salario'] = np.log1p(X['Salario'])              # log(1 + Salario)
X['Salario_por_Idade'] = X['Salario'] / (X['Idade']+1) # razão simples (evita div. por zero)

# 2) Interações simples
X['Idade_x_logSal'] = X['Idade'] * X['log_Salario']

# 3) Extração de componentes temporais
X['Mes'] = X['Data'].dt.month
X['DiaSemana'] = X['Data'].dt.dayofweek  # 0 = segunda

# 4) Agregações temporais (ex.: média móvel de 3 dias do salário)
X = X.sort_values('Data')
X['Salario_MM3'] = X['Salario'].rolling(window=3, min_periods=1).mean()

# 5) Codificação de categóricas (one-hot)
X = pd.get_dummies(X, columns=['Cidade'], drop_first=True)

print("Colunas após feature engineering:")
print(list(X.columns))

print("\nPrévia dos dados com novas features:")
print(X.head(10))

```

    Colunas após feature engineering:
    ['Idade', 'Salario', 'Data', 'log_Salario', 'Salario_por_Idade', 'Idade_x_logSal', 'Mes', 'DiaSemana', 'Salario_MM3', 'Cidade_B', 'Cidade_C']
    
    Prévia dos dados com novas features:
       Idade  Salario       Data  log_Salario  Salario_por_Idade  Idade_x_logSal  \
    0     22     2500 2025-01-01     7.824446         108.695652      172.137810   
    1     35     5200 2025-01-02     8.556606         144.444444      299.481217   
    2     41     6800 2025-01-03     8.824825         161.904762      361.817823   
    3     29     3900 2025-01-04     8.268988         130.000000      239.800658   
    4     33     4500 2025-01-05     8.412055         132.352941      277.597811   
    5     26     3100 2025-01-06     8.039480         114.814815      209.026478   
    
       Mes  DiaSemana  Salario_MM3  Cidade_B  Cidade_C  
    0    1          2  2500.000000     False     False  
    1    1          3  3850.000000      True     False  
    2    1          4  4833.333333     False     False  
    3    1          5  5300.000000     False      True  
    4    1          6  5066.666667      True     False  
    5    1          0  3833.333333     False     False  
    

Esses são alguns métodos usuais de feature engineering, mas não são todos. Conforme ressaltado, a depender do problema em questão você deverá ter um pingo de criatividade para pensar formas diferentes de extrair informação contida nos dados. Por exemplo, muitas vezes você pode criar novas variáveis fazendo interações de variáveis em sua base.

Sempre dedique um tempo especial a parte de feature engineering quando estiver desenvolvendo um modelo de machine learning, ela pode ser o diferencial para alcançar um resultado satisfatório!

# **3. Modelos para Problemas de Classificação**

**Antes de começar**

*Em alguns modelos abaixo há mais de um texto de explicação. Esses textos foram escritos por pessoas diferentes ao longo do desenvolvimento deste case. Em vez de tratá-los como trechos descontínuos, encare-os como perspectivas complementares sobre o mesmo assunto. A alternância entre esses textos será marcada por uma barra horizontal.*

## **3.1 KNN (K-Nearest-Neighbors)**

O KNN é provavelmente o mais simples modelo de machine learning e geralmente o primeiro a ser apresentado nos materiais didáticos. Isso acontece por sua lógica relativamente simples e de fácil entendimento. Basicamente, oque o modelo faz é "guardar" os dados de treino e, toda vez que vai fazer uma predição, o algoritmo acha os dados "mais próximos".

Voltando a nossas definições iniciais, lembre-se que temos um *espaço de características*. Cada observação em nossa base de dados é representada por um *vetor de características* neste espaço. Dessa forma, o KNN pega cada vetor desse na base de dados e coloca no espaço de características. Quando for fazer uma previsão, ele coloca esse novo vetor de características a ser feito a previsão no espaço e procura qual o vetor (ou vetores) de treino que estão **mais próximos** desse novo vetor. Daí o nome *nearest neighbor* (vizinho mais próximo)

O gif abaixo ilustra de maneira didática esse processo:

<p align=center>
<img src="https://machinelearningknowledge.ai/wp-content/uploads/2018/08/KNN-Classification.gif" width=600 height=400></img> </p>

Na sua versão mais simples, o algoritmo considera apenas um único vizinho mais próximo. Porém, podemos passar qualquer valor arbitrário k (daí o K em K-Nearest Neighbor). Quando utilizamos mais de 1 vizinho, estamos meio que um sistema de votos para classificar o novo vetor de características. Então, para cada observação de teste, contamos quantos vizinhos pertencem a cada classe e classificamos essa observação como aquela que tiver a maior contagem.

Quando estamos trabalhando com o modelo KNN, geralmente devemos nos preocupar com dois parâmetros importantes: O número de vizinhos e como calcular a distância entre os vetores. Quanto menor o número de vizinhos, mais complexo é o modelo e quanto maior o número de vizinhos, mais simples ele é. Para calcular a distância, usualmente a distancia euclidiana é a mais utilizada.

**Vantagens**: 
- O modelo KNN é um modelo com algoritmo intuitivo e de fácil entendimento.
- Capaz de capturar relações não lineares entre os dados
- Fácil de implementar sem fazer muitos ajustes

**Desvantagens**:
- Lento quando temos um conjunto de dados de treino muito grande
- Afetado por features com escalas muito diferentes
- Não performa bem quando o conjunto de dados possui muitas features
- É particulamente ruim quando a maioria das features tem valor 0 na maior parte do tempo


```python
# Vamos voltar ao nosso dataset de vinha para treinar os diferentes modelos de classificação
# Novamente, apresentamos o código para utilizar o modelo KNN

# Importa o modelo KNN
from sklearn.neighbors import KNeighborsClassifier

# Instancia o modelo KNN
knn = KNeighborsClassifier(n_neighbors=3)

# Separa os dados em variáveis independentes (X) e dependentes (y)
X = df.drop(columns=['target'])
y = df['target']

# Utiliza o método train_test_split para dividir os dados em conjuntos de treino e teste
from sklearn.model_selection import train_test_split

# Divide os dados em 80% para treino e 20% para teste
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Treina o modelo KNN com os dados de treino
knn.fit(X_train, y_train)

# Faz previsões com os dados de teste
y_pred = knn.predict(X_test)

# Importa a função de acurácia do sklearn metrics
from sklearn.metrics import accuracy_score
# Calcula a acurácia
accuracy = accuracy_score(y_test, y_pred)

print(f'Acurácia do modelo KNN: {accuracy:.5f}')
```

    Acurácia do modelo KNN: 0.80556
    

###
---

### Introdução ao Problema (KNN)

 Imagine que você é um novo usuário na Netflix. A plataforma quer prever se você vai gostar de um filme específico que nunca viu, digamos, "Crespúsculo". Esse é um problema típico de classificação que o KNN resolver.

**"K" - O número de pessoas com seu gosto**

- O sistema não vai comparar o seu gosto com o de todos os usários, isso não é eficiente nem útil. Então ele definirá quantas pessoas ele irá compara, um número `K` de usuários. Vamos dizer que ele escolhe `K=10`. Portanto, o objetivo agora é encontrar os 10 usuários na plataforma cujo gosto para filmes é o mais parecido com o seu.

**"N" - A "Distância de Gosto"(?)**

- Como o sistema encontra suas 10 almas gêmeas? Ele não mede a distãncia entre você e a pessoa, mas precisamos de uma medida para **"distância entre gostos"**.

- Na verdade, é mais intuitívo do que parece, imagine que você assistiu e e avaliou alguns filmes (ex.: deu nota 5 para Divergente, 3 para Senhor dos Anéis e 1 para Interestelar...). podemos criar o algoritmo que então varre o banco de dados em busca dos 10 usuários cujas avaliações para esses mesmos filmes são matematicamente mais parecidas com a suas.

- Por exemplo, um usuário que também amou Divergente e odiou Interestelar está muito "mais perto". Enquanto alguém com opnião oposta está "mais longe".

**Classificação**

- Agora que identificamos seus vizinhos mais próximos, o algoritmo simplesmente verifica o que eles acharam de Crepúsculo:
    - Exemplo: 8 dos 10 usuários deram uma nota alta para Crepúsculo

O algoritmo retornará que com base nessa maioria, você provavelmente irá gostar desse filme, e o coloca na sua lista de recomendações


### Intuição (KNN)



Para intuição, vamos usar o exemplo mais simples do machine learning:

 O **Iris Dataset**

**A ideia:**

Imagine que você encontrou uma flor íris na natureza e mediu suas caracteríristicas:
- Comprimento da pétala: 4.5 cm
- Largura da pétala: 1.5 cm

Existem 3 espécies de íris: Setosa, Versicolor e a Virginica.

Pergunta: **Qual espécie essa flor pertence?**



```python
# =======================================================
# IMPORTANDO AS BIBLIOTECAS
# =======================================================

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from collections import Counter
from sklearn.datasets import load_iris

```


```python
# CARREGANDO O IRIS DATASET
iris = load_iris()

X = iris.data # Features: 4 características das flores
y = iris.target # Labels: 3 classes (0, 1, 2) das flores

print("Classes:")
for i, nome in enumerate(iris.target_names):
    print(f" Classe {i}: {nome.capitalize()} ({np.sum(y == i)} amostras)")
print("===" * 50)

print("\nFeatures (cm):")
for i, nome in enumerate(iris.feature_names):
    print(f"{i+1}. {nome}")
print(f"\nFormato dos dados: {X.shape}")
print("===" * 50)

# =======================================================
# VISUALIZANDO OS DADOS

print("\nVisualizando os dados:")
pd.DataFrame(X, columns=iris.feature_names).head()
```

    Classes:
     Classe 0: Setosa (50 amostras)
     Classe 1: Versicolor (50 amostras)
     Classe 2: Virginica (50 amostras)
    ======================================================================================================================================================
    
    Features (cm):
    1. sepal length (cm)
    2. sepal width (cm)
    3. petal length (cm)
    4. petal width (cm)
    
    Formato dos dados: (150, 4)
    ======================================================================================================================================================
    
    Visualizando os dados:
    


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sepal length (cm)</th>
      <th>sepal width (cm)</th>
      <th>petal length (cm)</th>
      <th>petal width (cm)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.6</td>
      <td>3.1</td>
      <td>1.5</td>
      <td>0.2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>3.6</td>
      <td>1.4</td>
      <td>0.2</td>
    </tr>
  </tbody>
</table>
</div>



```python
# Vamos simplificar o problema para visualização para apenas duas features:
# - Comprimento da pétala
# - Largura da Pétala

# **Nota:** Estas são as features mais discriminativas - ou seja, são as que melhor diferenciam as 3 espécies de íris

# *(como eu sei disso?)* 

X_2d = X[:, [2, 3]]
```


```python
# Criando a flor que queremos classificar
novo_ponto = np.array([4.5, 1.5]) # Comprimento e largura da pétala

print("Nossa flor:")
print(f"    Comprimento da pétala: {novo_ponto[0]} cm")
print(f"    Largura da pétala: {novo_ponto[1]} cm")
print(f"    Classe: Desconhecida")
```

    Nossa flor:
        Comprimento da pétala: 4.5 cm
        Largura da pétala: 1.5 cm
        Classe: Desconhecida
    


```python
# =======================================================
# Passo 1: CALCULAR DISTÂNCIAS
# =======================================================

def euclidean_distance(X, point):
    """Calcula a distância Euclidiana entre um ponto e todos os pontos em X.
    
    Distância Eucliana: d = sqrt((x2 - x1)^2 + (y2 - y1)^2) (veremos mais sobre isso depois)
    """

    distance = np.sqrt(np.sum((X - point) ** 2, axis=1))

    return distance

distancias = euclidean_distance(X_2d, novo_ponto)
print("Distâncias calculadas:")
for i in range(5):
    print(f"  Distância até ponto {i+1}: {distancias[i]:.4f} cm")
print("...")
print(f"  Distância até ponto 150: {distancias[-1]:.4f} cm")

print(f"\nTotal de distâncias calculadas: {len(distancias)}")

```

    Distâncias calculadas:
      Distância até ponto 1: 3.3615 cm
      Distância até ponto 2: 3.3615 cm
      Distância até ponto 3: 3.4540 cm
      Distância até ponto 4: 3.2696 cm
      Distância até ponto 5: 3.3615 cm
    ...
      Distância até ponto 150: 0.6708 cm
    
    Total de distâncias calculadas: 150
    


```python
# =======================================================
# PASSO 2: ENCONTRAR OS K VIZINHOS MAIS PRÓXIMOS
# =======================================================

def find_knn(distancias, k):
    """
    Retorna os índices dos k vizinhos mais próximos 
    """

    indices_dos_vizinhos = np.argsort(distancias)[:k]
    return indices_dos_vizinhos

k = 7
k_vizinhos = find_knn(distancias, k)

for i, idx in enumerate(k_vizinhos):
    classe = iris.target_names[y[idx]]
    print(f" {i+1}º Vizinho: Flor ${idx+1} - Classe: {classe} - Distância: {distancias[idx]:.4f} cm ")

print("\nNote: Os vizinhos mais próximos têm as menores distâncias.")
```

     1º Vizinho: Flor $52 - Classe: versicolor - Distância: 0.0000 cm 
     2º Vizinho: Flor $79 - Classe: versicolor - Distância: 0.0000 cm 
     3º Vizinho: Flor $69 - Classe: versicolor - Distância: 0.0000 cm 
     4º Vizinho: Flor $67 - Classe: versicolor - Distância: 0.0000 cm 
     5º Vizinho: Flor $85 - Classe: versicolor - Distância: 0.0000 cm 
     6º Vizinho: Flor $55 - Classe: versicolor - Distância: 0.1000 cm 
     7º Vizinho: Flor $86 - Classe: versicolor - Distância: 0.1000 cm 
    
    Note: Os vizinhos mais próximos têm as menores distâncias.
    


```python
# =======================================================
# PASSO 3: Fazer a PREVISÃO DA CLASSE
# =======================================================

def predict_class(y_train, k_vizinhos_indices):
    """
    Faz a previsão da classe com base nos k vizinhos mais próximos
    """

    k_classes = y_train[k_vizinhos_indices]
    contagem = Counter(k_classes)
    most_common = contagem.most_common(1)
    return most_common[0][0], contagem

classe_prevista, contagem_classes = predict_class(y, k_vizinhos)

print("Resultado da previsão:")
for classe_id in sorted(contagem_classes.keys()):
    nome_classe = iris.target_names[int(classe_id)]
    quantidade = contagem_classes[classe_id]
    percentual = (quantidade / k) * 100
    barra = '*' * quantidade
    print(f" {nome_classe.capitalize():12s}: {quantidade}/{k} ({percentual:.2f}%) {barra}")

resultado_nome = iris.target_names[int(classe_prevista)]

print(f"\n" + "===" * 50)
print(f"\n RESULTADO FINAL: A flor é da classe '{resultado_nome.upper()}'")
print(f"\n Confiança: {contagem_classes[classe_prevista]}/{k} ({(contagem_classes[classe_prevista]/k)*100:.2f}%)")
```

    Resultado da previsão:
     Versicolor  : 7/7 (100.00%) *******
    
    ======================================================================================================================================================
    
     RESULTADO FINAL: A flor é da classe 'VERSICOLOR'
    
     Confiança: 7/7 (100.00%)
    

**Desafio: Você consegue fazer o mesmo com o exemplo da recomendação da Netflix?**

### Visualizando os Resultados

**É necessário executar a sessão 3.1.2**


```python
# =======================================================
# VISUALIZAÇão GRÁFICA
# =======================================================

# Criando amostra para o gráfico
np.random.seed(42)
amostra_indices = []
for classe in range(3):
    indices_classe = np.where(y == classe)[0]
    amostra_classe = np.random.choice(indices_classe, 10, replace=False)
    amostra_indices.extend(amostra_classe)

X_amostra = X_2d[amostra_indices]
y_amostra = y[amostra_indices]

novo_ponto_viz = np.array([4.5, 1.5])
dist_viz = euclidean_distance(X_amostra, novo_ponto_viz)
k_viz = 5
vizinhos_viz = find_knn(dist_viz, k_viz)
classe_viz, contagem_viz = predict_class(y_amostra, vizinhos_viz)

cores = ['r', 'g', 'b']
labels = iris.target_names
fig, axes = plt.subplots(1, 3, figsize=(20, 4))
fig.suptitle("Classificação KNN - Visualização dos 3 Passos do Algoritmo", fontsize=16, fontweight='bold', y=1)
# -----------------------------------------------------
# ----- GRÁFICO 1: Calcular Distâncias -----
ax1 = axes[0]

for i in range(3):
    indices = y_amostra == i
    ax1.scatter(X_amostra[indices, 0], X_amostra[indices, 1], 
                 c=cores[i], s=150, alpha=0.7, label=labels[i],
                 edgecolors='k', linewidth=1.5, zorder=3)
    
ax1.scatter(novo_ponto_viz[0], novo_ponto_viz[1], c='gold', s=400, marker='*', 
            label='Flor Desconhecida', edgecolors='k', linewidth=1.5, zorder=10)

for i, ponto in enumerate(X_amostra):
    ax1.plot([novo_ponto_viz[0], ponto[0]], [novo_ponto_viz[1], ponto[1]], 
             'gray', alpha=0.3, linewidth=1.5, linestyle='-', zorder=1)

ax1.set_xlabel("Comprimento da Pétala (cm)", fontsize=12)
ax1.set_ylabel("Largura da Pétala (cm)", fontsize=12)
ax1.set_title("Passo 1: Calcular Distâncias")
ax1.legend(loc='upper left', fontsize=10, framealpha=0.95)
ax1.set_xlim(0, 7)
ax1.set_ylim(0, 3)

# ----- GRÁFICO 2: Encontrar K Vizinhos ------
ax2 = axes[1]

for i in range(3):
    indices = y_amostra == i
    ax2.scatter(X_amostra[indices, 0], X_amostra[indices, 1], 
                 c=cores[i], s=80, alpha=0.4,
                 edgecolors='gray', linewidth=0.5, zorder=1)

# Destacando os k vizinhos mais próximos
vizinhos_pts = X_amostra[vizinhos_viz]
vizinhos_cls = y_amostra[vizinhos_viz]
cores_viz = [cores[int(cls)] for cls in vizinhos_cls]

ax2.scatter(vizinhos_pts[:, 0], vizinhos_pts[:, 1],
            c=cores_viz, s=300, alpha=0.95,
            edgecolors='black', linewidth=2.5, zorder=5)

    
ax2.scatter(novo_ponto_viz[0], novo_ponto_viz[1], c='gold', s=400, marker='*',
            edgecolors='k', linewidth=2.5, zorder=10)

ax2.set_xlabel("Comprimento da Pétala (cm)", fontsize=12)
ax2.set_title("Passo 2: Encontrar os K Vizinhos Mais Próximos")
ax2.set_xlim(0, 7)
ax2.set_ylim(0, 3)

# ----- GRÁFICO 3: Prever a Classe ------
ax3 = axes[2]

for i in range(3):
    indices = y_amostra == i
    ax3.scatter(X_amostra[indices, 0], X_amostra[indices, 1], 
                 c=cores[i], s=60, alpha=0.3,
                 edgecolors='gray', linewidth=0.3, zorder=1)
    
ax3.scatter(vizinhos_pts[:, 0], vizinhos_pts[:, 1],
            c=cores_viz, s=180, alpha=0.5,
            edgecolors='gray', linewidth=1.5, zorder=3)

cor_prev = cores[int(classe_viz)]
ax3.scatter(novo_ponto_viz[0], novo_ponto_viz[1], c=cor_prev, s=500, marker='*',
            edgecolors='k', linewidth=3, zorder=10, alpha=0.95, label=f'classe: {labels[int(classe_viz)]}')

from matplotlib.patches import Circle
circulo = Circle(novo_ponto_viz, dist_viz[vizinhos_viz[-1]],
                  fill= False, edgecolor=cor_prev, linewidth=3, linestyle='--', alpha=0.7, zorder=2)
ax3.add_patch(circulo)

ax3.set_xlabel("Comprimento da Pétala (cm)", fontsize=12)
ax3.set_title("Passo 3: Prever a Classe")
ax3.set_xlim(0, 7)
ax3.set_ylim(0, 3)
ax3.legend(loc='upper left', fontsize=10, framealpha=0.95)
plt.tight_layout()
plt.show()

```


    
![png](case_ia_files/case_ia_175_0.png)
    


### Formulação Formal 

Fonte: https://medium.com/@amirm.lavasani/classic-machine-learning-in-python-k-nearest-neighbors-knn-a06fbfaaf80a

**Entrada**
- Conjunto de treinamento em pares $D=\{(x_1, y_1), (x_2, y_2), ...\}$

    onde:

    $x_i$: vetor de features (ex.: Largura, Comprimento...)

    $y_i$: label (ex: Classe da planta ou se gostou ou não gostou de um filme)

- Inteiro K - Números de vizinhos a serem considerados

- vetor $x_o$ - Para previsão 



**Processo**

- Calcular distâncias para cada ponto `xᵢ` : A mais comum é a
    - Distância Euclidiana 
        Usado para vetores com valor real:

        $d(x_o, x_i) = \sqrt{\sum^n_{i=1}(x_o-x_i)^2}$

        *Nota:* é simplesmente a distância em linha reta entre os dois pontos em um espaço de n dimensões (features)

    Saber Mais: [Metricas de Distância](https://diegoinacio.medium.com/metricas-de-distancia-e-dissimilaridade-94f9d8d962d4)

    **Importante:** Normalize as escalas das features no Pré-processamento (Ver implementação em SKlearn)

- Ordene e identifique os vizinhos:
    Após, ordenar as distâncias selecione o conjunto `N` que contém `K` pontos de treinamento que correspondem às `K` menores distâncias. Esta é a vizinhança.

    *Nota: Você deve estar se perguntando como escolher o `K` ótimo?*. 
    
    Tem algumas formas "inteligentes" (falaremos mais depois), mas se você está vendo que seu modelo é muito sensível a esse valor, pode ser uma forte indicação de que ele não é o melhor modelo para  o seu problema.

**Saída: Previsão**

A previsão `ŷ` para classificação é simplesmente a classe mais frequente (moda) entre os rótulos dos `K` vizinhos no conjunto `N`

- Formalmente:

    $\hat{y} = \arg\max_v \sum_{(x_i, y_i) \in N} I(y_i = v)$

    (monstruoso, mas é só uma forma de dizer "conte os votos para cada classe (v) e escolha a que tiver mais")

### Desafio: "From Scratch"


Sabendo agora como funciona o KNN, tente implementar o algoritmo de zero, usando apenas NumPy!


```python
class KNN:
    def __init__(self, k=3):
        """
        Inicializa o classificador KNN

        Parâmetros:
        k (int): Número de vizinhos a considerar (padrão é 3)
        """

        pass

    def fit (self, X_train, y_train):
        """
        Armazena os dados de treinamento

        Parâmetros:
        X_train (array-like): Dados de treinamento (features)
        y_train (array-like): Labels de treinamento (classes)
        """

        pass

    def _euclidean_distance(self, x1, x2):
        """
        Calcula a distância Euclidiana entre dois pontos

        Parâmetros:
        x1, x2 (array-like): Pontos para calcular a distância

        Retorna:
        float: Distância Euclidiana
        """

        pass

    def predict(self, X_test):
        """
        Faz previsões para os dados de teste

        Parâmetros:
        X_test (array-like): Dados de teste (features)

        Retorna:
        array: Previsões das classes
        """

        pass

    def _predict_single(self, x):
        """
        Faz a previsão para um único ponto de dados

        Parâmetros:
        x (array-like): Ponto de dados

        Retorna:
        int: Classe prevista
        """

        pass

    def score(self, X_test, y_test):
        """
        Calcula a acurácia do classificador

        Parâmetros:
        X_test (array-like): Dados de teste (features)
        y_test (array-like): Labels verdadeiros (classes)

        Retorna:
        float: Acurácia do classificador
        """

        pass

```


```python
# Dados para Teste (dataset Iris)
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split

# Carregar o dataset Iris
iris = load_iris()
X = iris.data
y = iris.target

# Dividir em conjunto de treinamento e teste
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

```

### Usando SKlearn

Agora vamos implementar o KNN usando o SKlearn!


```python
# Carregando os dados (de novo)
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split

# Carregar o dataset Iris
iris = load_iris()
X = iris.data
y = iris.target

# Dividir em conjunto de treinamento e teste
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

```

**Implementação Básica**


```python
from sklearn.neighbors import KNeighborsClassifier

knn = KNeighborsClassifier(n_neighbors=7) #Modelo com K=7

knn.fit(X_train, y_train) #Treinando o modelo

predictions = knn.predict(X_test) #Fazendo previsões

# Sim, 3 linhas de código!
# Avaliando o modelo
from sklearn.metrics import accuracy_score, classification_report, confusion_matrix
accuracy = accuracy_score(y_test, predictions)
print(f"Acurácia: {accuracy*100:.2f}%\n")
```

    Acurácia: 96.67%
    
    

Saber Mais: [Documentação oficial SKlearn - KNN](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html)

Mas aqui está algumas ferramentas úteis:


```python
# Cross-Validation (Para avaliar a robustez do modelo e encontrar o K "ideal")
from sklearn.model_selection import cross_val_score
import numpy as np

# Ideia: 
#  - Divide os dados em "folds" (partes)
#  - Treina o modelo em alguns folds e testa em outros
#  - Repete isso várias vezes e calcula a média da acurácia

k_range = range(1, 31)
k_scores = []
for k in k_range:
    knn = KNeighborsClassifier(n_neighbors=k)
    scores = cross_val_score(knn, X, y, cv=5, scoring='accuracy')
    k_scores.append(scores.mean())

best_k = k_range[np.argmax(k_scores)]
best_score = max(k_scores)

print(f'MELHOR K: {best_k}')
print(f'Acurácia média (CV): {best_score*100:.2f}%')

```

    MELHOR K: 6
    Acurácia média (CV): 98.00%
    


```python
# Normalização dos Dados (Importante para KNN)
from sklearn.preprocessing import StandardScaler

# Ideia:
#  - KNN usa distância Euclidiana, então se as features tiverem escalas muito diferentes, o modelo pode ser enviesado
#  - Normalizar os dados coloca todas as features na mesma escala (média 0, desvio padrão 1)
#  - Isso ajuda o KNN a funcionar melhor

#===============================================================================================================
# Criando dados com escalas diferentes
from sklearn.datasets import make_classification
X, y = make_classification(n_samples=200, n_features=2, n_informative=2, n_redundant=0, random_state=42)

X[:, 1] = X[:, 1] * 100  

x_train_us, X_test_us, y_train_us, y_test_us = train_test_split(X, y, test_size=0.2, random_state=42)
# =============================================================================================================

print("Sem Normalização:")
knn_without_norm = KNeighborsClassifier(n_neighbors=5)
knn_without_norm.fit(x_train_us, y_train_us)
acc_without_norm = knn_without_norm.score(X_test_us, y_test_us)
print(f"Acurácia: {acc_without_norm*100:.2f}%\n")

print("Com Normalização:")
scaler = StandardScaler()
X_train_norm = scaler.fit_transform(x_train_us)
X_test_norm = scaler.transform(X_test_us)

knn_with_norm = KNeighborsClassifier(n_neighbors=5)
knn_with_norm.fit(X_train_norm, y_train_us)
acc_with_norm = knn_with_norm.score(X_test_norm, y_test_us)
print(f"Acurácia: {acc_with_norm*100:.2f}%\n")

print(f"Melhoria: {((acc_with_norm - acc_without_norm) * 100):.2f}%")

print("Por isso, SEMPRE normalize seus dados quando usar KNN!")

```

    Sem Normalização:
    Acurácia: 60.00%
    
    Com Normalização:
    Acurácia: 80.00%
    
    Melhoria: 20.00%
    Por isso, SEMPRE normalize seus dados quando usar KNN!
    


```python
# Pipeline (Fluxo de Trabalho Completo)
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score

# Ideia:
#  - Usar Pipeline para encadear várias etapas (normalização, modelo, etc.)
#  - Facilita o deployment
#  - Previne data leakage
#  - Garante que o mesmo pré-processamento é aplicado nos dados de treino e teste

pipeline = Pipeline([
    ('scaler', StandardScaler()),  # Normalização
    ('knn', KNeighborsClassifier(n_neighbors=5))  # Modelo KNN
])

pipeline.fit(X_train, y_train)  
predictions = pipeline.predict(X_test)  
print(f"Acurácia: {accuracy_score(y_test, predictions)*100:.2f}%")


```

    Acurácia: 100.00%
    

## **3.2 Naive Bayes**

Os modelos de classificação Naive Bayes são modelos probabilísticos construídos com base no **Teorema de Bayes**. Na classificação Bayeseana estamos interessados em calcular a probabilidade de certa observação pertencer a uma categoria (ou classe) dado as características observadas. Podemos escrever isso da seguinte forma $P(C_k | X)$ (Probabilidade da categoria k dado o vetor de características X)

O Naive Bayes classifica uma amostra $X= (x_1, x_2, ..., x_n)$ atribuindo a classe $C_k$ que maximiza a probabilidade condicional:

$$
P(C_k|X) = \frac{P(X|C_k)P(C_k)}{P(X)}
$$

Onde:
- $P(C_k|X)$: Probabilidade da classe $C_k$ dado os atributos $X$
- $P(X|C_k)$: Probabilidade de observar os atributos $X$ na classe $C_k$
- $P(C_k)$: Probabilidade prévia da classe $C_k$
- $P(X)$: Probabilidade dos atributos $X$

A predição é feita escolhendo a classe que tem o maior valor de $P(C_k|X)$

### **De onde vêm o Naive (ingênuo) de Naive Bayes?**

O Naive vem da principal hipótese simplificadora que é a suposição que as variáveis são independentes entre si. Dessa forma, a probabilidade condicional se torna:

$$
P(X|C_k) = P(x_1|C_k)\times P(x_2|C_k)\times ... \times P(x_n|C_k)
$$

Isso facilita os cálculos, pois agora basta calcular a probabilidade de cada feature separadamente.

### **Gaussian Naive Bayes**

Conforme dito, existem alguns modelos Naive Blayes classificadores. O primeiro é o Gaussiano. De maneira simples, ele assume que os dados dentro de cada classe possui uma distribuição Gaussiana (Normal). Assim, você pode treinar esse modelo achando a média e o desvio padrão dos dados dentro de cada classe. O Naive Bayes Gaussiano é usado quando estamos trabalhando com dados contínuos

### **Multinomial Naive Bayes**
De maneira semelhante, classificadores Multinomial Naive Bayes assumem distribuição multinomial. Assume que as features representam frequências de contagem (Por exemplo, quantas vezes determinada palavra aparece em um email). Um dos usos mais comuns dos modelos multinomial é na classificação de textos.

### **Vantagens**:
- Muito rápido tanto na etapa de treino quanto na etapa de teste
- Usualmente são fáceis de interpretar
- Há poucos hiperparametros para se preocupar (se é que há algum)

### **Desvantagens**:
- Suposição ingênua de independência entre as variáveis
- Não funciona bem com dados altamente correlacionados
- Pode haver problemas se os dados não seguirem distribuição guassiana (para dados contínuos)

Em resumo, os modelos bayseanos, apesar de suas suposições que podem não ser verossímeis na prática, usualmente fornecem bons resultados e podem ser considerados um bom benchmark para comparar outros modelos de classificação.


```python
# Importa o modelo Naive Bayes
from sklearn.naive_bayes import GaussianNB

# Instancia o modelo Naive Bayes
naive_bayes = GaussianNB()

# Treina o modelo Naive Bayes com os dados de treino
naive_bayes.fit(X_train, y_train)

# Utiliza o metodo train_test_split para dividir os dados em conjuntos de treino e teste
from sklearn.model_selection import train_test_split

# Divide os dados em 80% para treino e 20% para teste
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Faz previsões com os dados de teste
y_pred_naive_bayes = naive_bayes.predict(X_test)

# Calcula a acurácia
accuracy_naive_bayes = accuracy_score(y_test, y_pred_naive_bayes)
print(f'Acurácia do modelo Naive Bayes: {accuracy_naive_bayes:.5f}')
```

    Acurácia do modelo Naive Bayes: 1.00000
    

###
---

Seguindo a mesma estrutura do KNN, Vamos começar com o problema:

Imagine que você acaba de receber um email. O sistema precisa decidir se essa mensagem que acabou de chegar, com o assunto "Esse está pagando! Aposte agora", é um email importante ou se é spam. Esse é o problema de classificação classico de **Naive Bayes**.

Vamos construir isso:

**Probabilidade a Priori**

A probabilidade a *Priori* é a nossa crença sobre algo antes de analisar qualquer nova evidência. Por exemplo:

- O algoritmo olha para todo o seu histórico de e-mails e calcula a proporção de cada categoria.

- Se de 10.000 emails recebidos, 2.000 foram Spam e 8.000 não eram, as probabilidades a priori são:
    - $P(Spam) = \frac{2.000}{10.000} = 20\% \Rightarrow$
    - $P(Não\space Spam) = 80\%$
    
- Isso significa que, sem ler o novo email, já sabemos que há uma chance de 20% de ser spam.

**Verossimilhança**

A verossimilhança (*likelihood*) mede o quão provável é encontrar a evidência (as palavras do email) assumindo que ele pertence a uma determinada categoria. Por exemplo:

- Se este email fosse um Spam, qual seria a probabilidade de ele conter as palavras "Pagando", "Aposte", "agora"? e se não fosse um Spam?

- O algoritmo volta ao histórico e calcula a frequência das palavras dentro de cada categoria:
    - **Spams**
        - $P("Pagando"|Spam) = 40\%$ (40% de todos os spams continham a palavra "Pagando")
        - $P("Aposte"|Spam) = 30\%$
    
    - **Não Spams**
        - $P("Pagando|Não \space Spam) = 1\%$ 
        - $P("Aposte"|Não \space Spam) = 0.5\%$

Nota: Como retomaremos o Naive Bayes assume que a presença de uma palavra é independente da outra. Isso significa que podemos simplesmente multiplicar as probabilidades individuais:

- Verossimilhança (Spam):

    - $P(\text{Evidência}|Spam) = P("Pagando"|Spam) \times P("Aposte"|Spam) ...$

- Verossimilhança (Não Spam):

    - $P(\text{Evidência}|Não \space Spam) = P("Pagando"|Não \space Spam) \times P("Aposte"|Não \space Spam) ...$

**Probabilidade a Posteriori**

A probabilidade a *posteriori* é o resultado final que o algoritmo nos entrega. É a probabilidade de um e-mail pertencer a uma categoria, depois de termos analisado a evidência (das palavras). A fórmula de Bayes nos diz como faz isso:

$P(y|X) = \frac{P(X|y) \times P(y)}{P(X)}$

Onde:

- $P(y|X):$ Probabilidade a *posteriori*, Probabilidade da categoria (classe) $y$ (spam ou não spam) dado evidência (features) $X$
- $P(X|y):$ Verossimilhança das features $X$ dado classe $y$
- $P(y):$ Probabilidade a *priori* da classe $y$
- $P(X):$ Evidência

**Classificação**

Finalmente, note que apesar da probabilidade a priori favorecer "Não Spam" (80:20), a evidência contida nas palavras gera uma verossimilhança tão maior para a categoria "Spam" que, no final, a probabilidade a posteriori de ser Spam será a mais alta!

### Intuição 

Vamos ver isso na prática, dessa vez usaremos o SMS Spam Collection Dataset:

Você recebe um SMS com o texto:

- WINNER!! You have won a £1000 prize! Call now to claim!

Pergunta: **Você classificaria esse email como `spam` ou `ham` (não spam)?**


```python
# =======================================================
# IMPORTANDO AS BIBLIOTECAS
# =======================================================



```


```python
# Carregando o Dataset
import kagglehub
from kagglehub import KaggleDatasetAdapter

df = kagglehub.dataset_load(
  KaggleDatasetAdapter.PANDAS,
  "uciml/sms-spam-collection-dataset",
  "spam.csv",
  pandas_kwargs={"encoding": "latin", "usecols": [0,1], "names": ["class", "sms"], 'header': 0}
)
# =================================================================

```

#### **Desafio: Pré-processamento**

Dessa Vez, precisamos processar o texto:

Ideia: 

1. Transformar todo o texto em minúsculo

2. Remover pontuações

3. Tokenizar (separar as palavras)

4. Remover stopwords (palavras comuns como "e", "o") - opcional, mas boa prática

Faça isso!


```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import re
```


```python
# IGNORE ================================================
from build.utils.text import preprocess_text

try: 
    df['words'] = df['sms'].apply(preprocess_text)
except Exception as e:
    print("Não existe a função preprocess_text")
    pass
# =====================================================
```


```python
# =======================================================
# Passo 1: Calcular as probabilidades a priori

# Fórmula: P(class) = numbers of class's messages / total messages
# =======================================================

total_messages = len(df)
spam_count = len(df[df['class'] == 'spam'])
ham_count = len(df[df['class'] == 'ham'])

prior_spam = spam_count / total_messages
prior_ham = ham_count / total_messages

print(f"Total de Mensagens: {total_messages}")
print(f"\nTotal de Mensagens Spam: {spam_count}")
print(f"\nTotal de Mensagens Ham: {ham_count}")
print(f"\nP(SPAM): {prior_spam*100:.2f}%")
print(f"\nP(HAM): {prior_ham*100:.2f}%")

print(f'''\nInterpretação:
      Antes de analisar o conteúdo de uma mensagem,
        - Há probabilidade de ser SPAM é de aproximadamente {prior_spam*100:.2f}%.
        - Há probabilidade de ser HAM é de aproximadamente {prior_ham*100:.2f}%.
      ''')

```

    Total de Mensagens: 5572
    
    Total de Mensagens Spam: 747
    
    Total de Mensagens Ham: 4825
    
    P(SPAM): 13.41%
    
    P(HAM): 86.59%
    
    Interpretação:
          Antes de analisar o conteúdo de uma mensagem,
            - Há probabilidade de ser SPAM é de aproximadamente 13.41%.
            - Há probabilidade de ser HAM é de aproximadamente 86.59%.
          
    


```python
# =======================================================
# Passo 2: Calcular Verossimilhança (Likelihood)

# Fórmula: P(word|class) = (count(word in class) + 1) / (total words in class + V)
# Onde V é o tamanho do vocabulário (número de palavras únicas)
# O "+1" é usado para suavização de Laplace (Laplace Smoothing) - evitar probabilidade zero
# =======================================================

from collections import Counter

spam_words = df[df['class'] == 'spam']['words'].sum()
ham_words = df[df['class'] == 'ham']['words'].sum()

# Contar a frequência das palavras em cada classe
spam_word_count = Counter(spam_words)
ham_word_count = Counter(ham_words)

vocabulary = set(spam_word_count.keys()).union(set(ham_word_count.keys()))

total_spam_words = len(spam_words)
total_ham_words = len(ham_words)

print(f'''Estatísticas de Palavras:
      
  - Vocabulário Total (V): {len(vocabulary)} palavras únicas
  - Total de Palavras em Mensagens SPAM: {total_spam_words}
  - Total de Palavras em Mensagens HAM: {total_ham_words}
      ''')

print(f"Palavras mais comuns em SPAM:")

for word, count in spam_word_count.most_common(5):
    print(f"  {word}: {count}")
print(f"\nPalavras mais comuns em HAM:")
for word, count in ham_word_count.most_common(5):
    print(f"  {word}: {count}")

def likelihood(word, cls):
    if cls == 'spam':
        word_count = spam_word_count.get(word, 0)
        return (word_count + 1) / (total_spam_words + len(vocabulary))
    else:
        word_count = ham_word_count.get(word, 0)
        return (word_count + 1) / (total_ham_words + len(vocabulary))

print(f'''\nExemplo de Cálculo de Verossimilhança:
  P("free"|SPAM) = {likelihood("free", "spam")*10:.4f}%
  P("free"|HAM) = {likelihood("free", "ham")*100:.4f}%
      ''')


```

    Estatísticas de Palavras:
    
      - Vocabulário Total (V): 8512 palavras únicas
      - Total de Palavras em Mensagens SPAM: 14934
      - Total de Palavras em Mensagens HAM: 61423
          
    Palavras mais comuns em SPAM:
      to: 686
      call: 350
      you: 287
      your: 263
      free: 219
    
    Palavras mais comuns em HAM:
      you: 1837
      to: 1554
      the: 1119
      and: 848
      in: 813
    
    Exemplo de Cálculo de Verossimilhança:
      P("free"|SPAM) = 0.0938%
      P("free"|HAM) = 0.0858%
          
    


```python
# =======================================================
# Passo 3: Classificação de uma nova mensagem
# =======================================================

new_message = "WINNER!! You have won a £1000 prize! Call now to claim!"

preprocessed_message = preprocess_text(new_message) 

# Calcular a probabilidade logarítmica para evitar underflow (falaremos mais sobre isso depois)
log_prob_spam = np.log(prior_spam)
log_prob_ham = np.log(prior_ham)

for word in preprocessed_message:
    log_prob_spam += np.log(likelihood(word, 'spam'))
    log_prob_ham += np.log(likelihood(word, 'ham'))

print(f'''\nClassificação da Mensagem:
    Mensagem: "{new_message}"
    Classificação: {"Spam" if log_prob_spam > log_prob_ham else "Ham"}
''')

```

    
    Classificação da Mensagem:
        Mensagem: "WINNER!! You have won a £1000 prize! Call now to claim!"
        Classificação: Spam
    
    

### Formulação Formal

**Entrada**
1. Conjunto de treinamento de n amostra em pares $D=\{(x^{(1)}, y^{(1)}), (x^{(2)}, x^{(i)}), ..., x^{(n)}, y^{(n)}\}$

    onde:

    - $x^{(i)}$: vetor de d features ($x^{(i)} = (x^{(i)}_1, x^{(i)}_2, ..., x^{(i)}_d)$)

    - $y^{(i)}$: rótulo de classe pertencente a um conjunto finito de classes $C = \{c_1, c_2, ..., c_k\}$ (label) 

    - $x^o$ : Vetor de features ($x^o = (x_1, x_2, ..., x_d)$), que precisa ser classficado na previsão


**Processamento**

Objetivo é encontrar a classe $\hat{y}$ que maximiza a probabilidade a posteriori $P(y|x^o)$

1. Teorema de Bayes: 

Para cada classe $c_k \in C$, calculamos a probabilidade a posteriori:

$P(c_k|x^o) = \frac{P(x^o|c_k)P(c_k)}{P(x^o)}$

Onde, como já vimos:

- $P(c_k|x^o):$ **Probabilidade a posteriori**
- $P(c_k): **Probabilidade a priori** a classe $c_k$
- $P(x^o| c_k):$ **Verossimilhança (likelihood) da amostra $x^o$ dada a classe $c_k$
- $P(X):$ **Evidência (evidence)**

2. Cálculo da Probabilidade  a Priori $P(c_k):

A priori é estimada a partir da frequência relativa de cada classe no conjunto de treinamento:

$P(c_k) = \frac{\text{Número de amostras da classe } c_k}{\text{Número total de amostras}} = \frac{\sum_{i=1}^{n} I(y^{(i)} = c_k)}{n}$

3. Cálculo da Verossimilhança $P(x^o|c_k)$:

Aqui reside a suposição naive (ingênua) do algoritmo: todas as features são condicionalmente independentes, dada a classe. Matematicamente, isso simplifica o cálculo da verossimilhança:

$P(x^o|c_k) = P(x_1, x_2, ...,x_d|c_k) = \prod^d_{j=1}P(x_j|c_k)$

O cálculo de cada $P(x_j|c_k)$ depende da natureza da feature $x_j$, o que nos leva ao diferentes tipos de modelos Naive Bayes, que veremos!

4. Tomada de Decisão (MAP):

Como o termo P(x^o) é constante para todas as classes, ele pode ser descartado na etapa da maximização. Portanto, a regra de decisão se torna:

$\hat{y} = \arg \max_{c_k \in C} P(c_k) \prod^d_{j=1}P(x_j|c_k) $

- O rótulo da classe predita $\hat{y} \in$ C para $x^o$


**II. Tipos de Modelos de Processamento da Verossimilhança**
Praticamente qualquer diferença entre os tipos de Naive Bayes está emm como eles modelam a distribuição $P(x_j|c_k)$ para diferentes tipos de dados. Alguns deles são:

1. Gaussian Naive Bayes:

- Uso: Features contínuas que se assume seguir uma distribuição normal (Gaussiana)

- Hipótese: Para cada classe $c_k$, o valor da feature $x_j$ é distribuido segundo uma Gaussiana

- Processamento: Durante o treinamento, o algoritmo calcula a média $\mu_{j,k}$ e a variância $\sigma^2_{j,k}$ da feature $j$ para todas as amostras da classe $c_k$. A verossimilhança é então calculado usando a função de densidade de probabilidade (PDF) da distribuição normal:

$P(x_j|c_k) = \frac{1}{2\pi\sigma^2_{j,k}}\exp\left(-\frac{(x_j-\mu_{j,k})^2}{2\sigma^2_{j,k}}\right) $

Saber mais: [GaussianNB](https://www.geeksforgeeks.org/machine-learning/gaussian-naive-bayes/)

2. Multinomial Naive Bayes:

- Uso: Features discretas que representam contagens ou frequências (clássico para classificação de texto com TF ou TF-IDF).

- Hipótese: As features são geradas a partir de uma distribuição multinomial.

- Processamento: A verossimilhança $P(x_j|c_k)$ é a frequência relativa da feature $x_j$ (e.g., uma palavra) dentro dos documentos da classe de $c_k$. Para evitar o problema de frequência zero, utiliza-se o Laplace Smoothing:

$P(x_j|c_k) = \frac{N_{i,j} + \alpha}{N_k + \alpha d}$

Onde:

- $N_{j,k}:$ contagem da feature $x_j$ na classe $c_k$
- $N_k:$ contagem total de todas as features na classe $c_k$
- $d$: o número total de features únicas (tamanho do vocabulário).
- $\alpha:$ é o parâmetro de suavização ($\alpha = 1$ para Laplace smoothing).

Saber mais: [MultionomiaNB](https://www.geeksforgeeks.org/machine-learning/multinomial-naive-bayes/)

3. Bernoulli Naive Bayes:

- Uso: Features binárias (Bernoulli) (e.g., presença ou ausência de uma palavra em um documento)

- Hipótese: As features são varáveis binárias independentes.

- Processamento: A verossimilhamça é calculada para a presença ($x_j = 1$) da feature na classe $c_k$. O cálculo da probabilidade total da amostra considera tanto as features presentes quanto as ausentes: 

$P(x_j|c_k) = P(j|c_k)^{x_j}(1-P(j|c_k))^{(1-x_j)}$

Onde $P(j|c_k)$ é a probabilidade da feature $j$ ocorrer na classe $c_k$.

Saber mais: [BernoulliNB](https://www.geeksforgeeks.org/machine-learning/bernoulli-naive-bayes/)



### Desafio: "From Scratch"



Vamos implementar o algoritmo naive bayes do zero:


```python
class NaiveBayesClassifier:
    def __init__(self, alpha=1.0):
        """
        Inicializa o classificador Naive Bayes 

        Parâmetros:
        alpha: parâmetro de suavização de Laplace (default=1.0)

        alpha=1.0 é "add-one smoothing"
        alpha=0.0  significa sem suavização
        """
        pass
    
    def fit(self, X, y):
        """
        Treina o classificador Naive Bayes

        Parâmetros:
        X: lista de listas de palavras (features)
        y: lista de labels (classes)
        """
        pass

    def _preprocess(self, text):
        """
        Pré-processa o texto de entrada

        Parâmetros:
        text: string de texto a ser processada

        Retorna:
        string: texto processado
        """
        pass
        
    def _calculate_priors(self):
        """
        Calcula as probabilidades a priori P(class)

        Fórmula: P(class) = numbers of class's messages / total messages
        """
        pass

    def _calculate_likelihoods(self):
        """
        Calcula as verossimilhanças P(word|class) com suavização de Laplace

        Fórmula: P(word|class) = (count(word in class) + alpha) / (total words in class + alpha * V)
        Onde V é o tamanho do vocabulário (número de palavras únicas)
        """
        pass

    def _calculate_log_probabilities(self, text, class_label):
        """
        Calcula a probabilidade logarítmica de uma mensagem pertencer a uma classe

        Parâmetros:
        text: lista de palavras da mensagem
        class_label: label da classe (spam ou ham)

        Retorna:
        float: probabilidade logarítmica
        """
        pass

    def predict(self, text):
        """
        Classifica uma nova mensagem

        Parâmetros:
        text: string de texto da mensagem a ser classificada

        Retorna:
        string: label da classe prevista (spam ou ham)
        """
        pass

    def predict_proba(self, text):
        """
        Calcula as probabilidades de uma mensagem pertencer a cada classe

        Parâmetros:
        text: string de texto da mensagem

        Retorna:
        dict: dicionário com as probabilidades para cada classe
        """
        pass

    def score(self, X, y):
        """
        Avalia a acurácia do classificador no conjunto de dados fornecido

        Parâmetros:
        X: lista de listas de palavras (features)
        y: lista de labels (classes)

        Retorna:
        float: acurácia do classificador
        """
        pass
```


```python
# Dados para Teste (Spam e Ham)
import kagglehub
from kagglehub import KaggleDatasetAdapter
from sklearn.model_selection import train_test_split

df = kagglehub.dataset_load(
  KaggleDatasetAdapter.PANDAS,
  "uciml/sms-spam-collection-dataset",
  "spam.csv",
  pandas_kwargs={"encoding": "latin", "usecols": [0,1], "names": ["class", "sms"], 'header': 0}
)

X = df['sms'].tolist()
y = df['class'].tolist()

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)
```

### Usando SKlearn




```python
# Carregando o Dataset (denovo)
import kagglehub
from kagglehub import KaggleDatasetAdapter
from sklearn.model_selection import train_test_split

df = kagglehub.dataset_load(
  KaggleDatasetAdapter.PANDAS,
  "uciml/sms-spam-collection-dataset",
  "spam.csv",
  pandas_kwargs={"encoding": "latin", "usecols": [0,1], "names": ["class", "sms"], 'header': 0}
)

X = df['sms'].tolist()
y = df['class'].tolist()

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)
```


```python
from sklearn.feature_extraction.text import CountVectorizer, TfidfVectorizer
from sklearn.naive_bayes import MultinomialNB, GaussianNB, BernoulliNB
from sklearn.metrics import accuracy_score


```


```python
# =======================================================
# 1. Essencial
# Ideia:
# - Vetorizar
# - Treinar o modelo
# =======================================================

vectorizer = CountVectorizer()

X_train_vec = vectorizer.fit_transform(X_train)
X_test_vec = vectorizer.transform(X_test)

print(f"Vocabulario: {vectorizer.get_feature_names_out()[1000:5000:400]} ...")
print(f"X_train_vec shape: {X_train_vec.shape}")
print(f"X_test_vec shape: {X_test_vec.shape}")

# ---

nb = MultinomialNB()
nb.fit(X_train_vec, y_train)
y_pred = nb.predict(X_test_vec)

accuracy = accuracy_score(y_test, y_pred)
print(f"\nAcurácia: {accuracy*100:.2f}%")
```

    Vocabulario: ['aphexåõs' 'blonde' 'chinese' 'decent' 'enemies' 'free' 'hellogorgeous'
     'jay' 'lotr' 'msgrcvd18'] ...
    X_train_vec shape: (4457, 7735)
    X_test_vec shape: (1115, 7735)
    
    Acurácia: 98.39%
    


```python
# 2. Usando as Variantes do NB

# 2.1. MultinomialNB (dados de contagem)
nb_multi = MultinomialNB()
nb_multi.fit(X_train_vec, y_train)
accuracy_multi = nb_multi.score(X_test_vec, y_test)


# 2.2. BernoulliNB (dados binários)
# Transformar os dados em binários (0 ou 1)
X_train_bin = (X_train_vec > 0).astype(int)
X_test_bin = (X_test_vec > 0).astype(int)

nb_bernoulli = BernoulliNB()
nb_bernoulli.fit(X_train_bin, y_train)
accuracy_bernoulli = nb_bernoulli.score(X_test_bin, y_test)


# 2.3. GaussianNB (dados contínuos)
# Converter os dados esparsos para densos (GaussianNB não aceita sparse)
X_train_dense = X_train_vec.toarray()
X_test_dense = X_test_vec.toarray()

nb_gaussian = GaussianNB()
nb_gaussian.fit(X_train_dense, y_train)
accuracy_gaussian = nb_gaussian.score(X_test_dense, y_test)

print('''
Nota:

1. MultinomialNB: {:.2f}% de acurácia - Melhor para classificação de texto, especialmente com contagem de palavras (e.g. Classificação de emails)
2. BernoulliNB: {:.2f}% de acurácia - Bom para textos curtos com recursos binários (e.g. Classificação de tweets)
3. GaussianNB: {:.2f}% de acurácia - Menos adequado para texto, melhor para dados contínuos (e.g. Classificação de imagens/sinais)
'''.format(accuracy_multi*100, accuracy_bernoulli*100, accuracy_gaussian*100))

```

    
    Nota:
    
    1. MultinomialNB: 98.39% de acurácia - Melhor para classificação de texto, especialmente com contagem de palavras (e.g. Classificação de emails)
    2. BernoulliNB: 97.49% de acurácia - Bom para textos curtos com recursos binários (e.g. Classificação de tweets)
    3. GaussianNB: 90.04% de acurácia - Menos adequado para texto, melhor para dados contínuos (e.g. Classificação de imagens/sinais)
    
    


```python
# Parâmetros Importantes do MultinomialNB
# - alpha: parâmetro de suavização de Laplace (default=1.0)
#   - alpha=1.0 é "add-one smoothing"
#   - alpha=0.0  significa sem suavização

# fit_prior (default=True): se True, aprende a probabilidade a priori das classes a partir dos dados de treinamento. Se False, assume que todas as classes são igualmente prováveis.

# class_prior (default=None): se fit_prior for False, você pode fornecer suas próprias probabilidades a priori para as classes.
# =======================================================

alphas = [0.001, 0.1, 0.5, 1.0, 2.0, 5.0]
results = []
for alpha in alphas:
    nb = MultinomialNB(alpha=alpha)
    nb.fit(X_train_vec, y_train)
    accuracy = nb.score(X_test_vec, y_test)
    results.append((alpha, accuracy))
    print(f"Alpha: {alpha}, Acurácia: {accuracy*100:.2f}%")

```

    Alpha: 0.001, Acurácia: 98.30%
    Alpha: 0.1, Acurácia: 98.39%
    Alpha: 0.5, Acurácia: 98.21%
    Alpha: 1.0, Acurácia: 98.39%
    Alpha: 2.0, Acurácia: 97.85%
    Alpha: 5.0, Acurácia: 97.04%
    


```python
# =======================================================
# COUNTVECTORIZER vs TFIDF VECTORIZER

# CounterVectorizer: conta a frequência das palavras
# TFIDFVectorizer: considera a frequência das palavras e a importância delas (menos frequentes são mais importantes)

# Qual é melhor? Depende!
# =======================================================

vectorizer_count = CountVectorizer()
X_train_count = vectorizer_count.fit_transform(X_train)
X_test_count = vectorizer_count.transform(X_test)

nb_count = MultinomialNB()
nb_count.fit(X_train_count, y_train)
acc_count = nb_count.score(X_test_count, y_test)

vectorizer_tfidf = TfidfVectorizer()
X_train_tfidf = vectorizer_tfidf.fit_transform(X_train)
X_test_tfidf = vectorizer_tfidf.transform(X_test)

nb_tfidf = MultinomialNB()
nb_tfidf.fit(X_train_tfidf, y_train)
acc_tfidf = nb_tfidf.score(X_test_tfidf, y_test)
print(f"CountVectorizer Acurácia: {acc_count*100:.2f}%")
print(f"TFIDFVectorizer Acurácia: {acc_tfidf*100:.2f}%")

print('''
Nota:
1. CountVectorizer: {:.2f}% de acurácia - Simples e eficaz para muitos casos, normalmente funciona melhor para NB
2. TFIDFVectorizer: {:.2f}% de acurácia - Útil quando a importância das palavras varia muito
'''.format(acc_count*100, acc_tfidf*100))
```

    CountVectorizer Acurácia: 98.39%
    TFIDFVectorizer Acurácia: 96.23%
    
    Nota:
    1. CountVectorizer: 98.39% de acurácia - Simples e eficaz para muitos casos, normalmente funciona melhor para NB
    2. TFIDFVectorizer: 96.23% de acurácia - Útil quando a importância das palavras varia muito
    
    

### Conclusões e Considerações

**Suposição de Independência Condicional:** Embora MUITO raramente seja verdadeira em cenários reais (e.g., as palavras "São" e "Paulo" não são independentes), o Naive Bayes frequentemente apresenta uma performance muito boa. Isso acontece porque a classificação não exige uma estimativa de probabilidade perfeitamente calibrada, mas apenas que a classe correta tenha a maior pontuação a posteriori

**Zero-Frequency Problem**: Se uma featurer de uma nova amostra não foi vista durante o treinamento para uma determinada classe, sua probabilidade $P(x_j|c_K)$ seria 0. Devido ao produtório, isso anularia a posteriori para aquela classe. O smoothing é a técnica que você deve usar para mitigar esse problema.

**Estabilidade Numérica (Log-Probabilities):** A multiplicação de muitas probabilidade pode resultar em valores extremamentes pequenos, levando a problemas de underflow (arrendondar para 0). Por isso normalmente, trabalhamos com a soma dos logaritmos das probabilidades, transformando o produtório em um somatório. A regra de decisão se torna:

$\hat{y} = \arg \max_{c_k \in C} \left(\log{(P(c_k)+\sum^d_{j=1}\log{(P(x_j|c_k))}} \right) $

**Aplicações do Naive Bayes Classifier**:

- Filtragem de e-mail de spam

- Classificação de texto (e.g., análise de sentimento e categorização de documentos)

- Diagnóstico médico: probabilidade de uma doença, baseado nos sintomas

- Pontuação de crédito: avaliação de credibilidade para aprovação de empréstimos

- Previsão do tempo: classificação de condições meteorológicas com base em vários fatores



## **3.3 Regressão Logística**

A Regressão Logística é um modelo matemático usado para modelar a relação de uma variável categorica e um conjunto de variáveis independentes. Neste sentido, a regressão logística se assemelha muito com uma regressão linear, mas uma distinção importante é que a saída de um modelo de regressão logística nos fornece a **probabilidade** de ocorrência de uma categoria.

Esse tipo de modelo estatístico (também conhecido como modelo logit) frequentemente é usado para classificação binária e análise preditiva. Como o resultado é uma probabilidade, a variável dependente é limitada entre 0 e 1.

Para calcular essa probabilidade, a regressão logística mapeia y como uma **função sigmoide** de x:

$$
f(x) = \frac{1}{1 + e^{-x}}
$$

Se imaginarmos que o conjunto x possui apenas uma variável e traçarmos uma curva, teremos o seguinte resultado:

<p align=center>
<img src="https://upload.wikimedia.org/wikipedia/commons/a/ac/Logistic-curve.png" width=600 height=400></img> </p>

Perceba que os possíveis resultados da variável dependente estão limitados entre 0 e 1.

A saída do modelo é uma probabilidade, e a classificação é feita com um limiar (threshold), geralmente 0.5:

- Se $P(Y=1) \geq 0.5$, então classe será 1
- se $P(Y=1) < 0.5$, então classe será 0


Podemos reescrever a equação de regressão logística da seguinte forma:

$$
\log\left(\frac{P(Y=1)}{1 - P(Y=1)}\right) = \beta_0 + \beta_1 X_1 + \beta_2 X_2 + ... + \beta_n X_n
$$

onde:
- $( P(Y=1))$ é a probabilidade do evento ocorrer.
- $\frac{P(Y=1)}{1 - P(Y=1)}$ representa a razão de chances. (Odds Ratio (razão de chances))
- $( \log(\frac{P(Y=1)}{1 - P(Y=1)} ))$ é a transformação logarítmica da razão de chances (Logaritmo da odds, que se relaciona linearmente com as variáveis preditoras.)

$\beta_0$ (Intercepto): epresenta o logaritmo da odds quando todas as variáveis preditoras $X_i = 0$. Após a exponenciação, fornece a odds base do evento ocorrer na ausência de influências das variáveis.

Se por exemplo. tivermos $\beta_1 = 0.3$, teremos que para cada aumento de 1 unidade em $X_1$, o logaritmo da razão de chances aumenta em $0.3$

Para interpretar diretamente o efeito da variável na razão de chances (odds ratio). Aplicamos a exponenciação: $e^{\beta_i}$

No exemplo em que $\beta_1 = 0.3$, teríamos que $e^{\beta_1} = e^{0.3} = 1.35$. Intepretamos assim que, para cada aumento adicional em $X$ as probabilidades do evento positivo aumentam em $35%$.


#### **Vantagens**:

- Rápido na etapa de treinamento e na etapa de teste
- Fácil interpretação
- Saída probabilística

#### **Desvantagens**::
- Assune relação linear entre as features
- Não funciona bem quando as variáveis são muito correlacionadas
- Não funciona bem com alta dimensionalidade das features
- Possível viés com classes desbalanceadas


#### **Regressão Logística Binária**

A regressão logística binária funciona bem para problemas de classificação binária que tenham apenas dois resultados possíveis. A variável dependente pode ter apenas dois valores, como sim e não ou 0 e 1.

#### **Regressão Logística Multinomial**

A regressão multinomial pode analisar problemas que tenham vários resultados possíveis, desde que o número de resultados seja finito. Por exemplo, ela é capaz de prever se os preços das casas aumentarão em 25%, 50%, 75% ou 100% com base em dados populacionais, mas não pode prever o valor exato de uma casa.

#### **Regressão Logística Ordinal**

A regressão logística ordinal, ou o modelo logit ordenado, é um tipo especial de regressão multinomial para problemas em que os números representam classificações em vez de valores reais. Por exemplo, você usaria a regressão ordinal para prever a resposta a uma pergunta de pesquisa que pede para os clientes classificarem seu serviço como ruim, regular, bom ou excelente com base em um valor numérico, como o número de itens que eles compram de você ao longo do ano.


```python
# Importa o modelo Regressão Logística
from sklearn.linear_model import LogisticRegression

# Instancia o modelo Regressão Logística
logistic_regression = LogisticRegression()

# Treina o modelo Regressão Logística com os dados de treino
logistic_regression.fit(X_train, y_train)

# Faz previsões com os dados de teste
y_pred_logistic_regression = logistic_regression.predict(X_test)

# Calcula a acurácia
accuracy_logistic_regression = accuracy_score(y_test, y_pred_logistic_regression)
print(f'Acurácia do modelo Regressão Logística: {accuracy_logistic_regression:.5f}')

```

    Acurácia do modelo Regressão Logística: 0.97222
    

    c:\Users\felip\AppData\Local\Programs\Python\Python312\Lib\site-packages\sklearn\linear_model\_logistic.py:469: ConvergenceWarning: lbfgs failed to converge (status=1):
    STOP: TOTAL NO. of ITERATIONS REACHED LIMIT.
    
    Increase the number of iterations (max_iter) or scale the data as shown in:
        https://scikit-learn.org/stable/modules/preprocessing.html
    Please also refer to the documentation for alternative solver options:
        https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression
      n_iter_i = _check_optimize_result(
    

###
---

Fonte: https://www.geeksforgeeks.org/machine-learning/understanding-logistic-regression/

https://medium.com/@nara.guimaraes/regress%C3%A3o-log%C3%ADstica-como-usu%C3%A1-la-em-an%C3%A1lise-de-dados-3fdb6be3a255

Ao contrário da regressão linear que prevê valores contínuos, ela prevê a probabilidade de uma entrada pertencer a uma classe específica. É usado para classificação binária onde a saída pode ser uma das duas categorias possíveis, como "Sim/Não", "Verdadeiro/Falso", "1/0". 
 
Será que poderiamos dizer, com algum grau de certeza, se alguém sobreviveu ou não ao Titanic sabendo apenas algumas informações como sexo, idade, classe?

Vamos construir o raciocínio do algoritmo.

**1. Ponderando as Evidências**

Primeiro, o algoritmo precisa aprender com os dados históricos dos passageiros. A Regressão logística faz isso atribuindo um "peso" a cada informação. Esse peso representa a importância e a direção daquela característica na chance de sobrevivência.

Por exemplo, se fosse para chutar:

- **Sexo = Feminino:** Receberia um peso positivo ou negativo? será que ser mulher afetaria a chance de sobrevivência de uma pessoa no dia do titanic?

- **Classe = 1ª:** Aumentaria a probabilidade de ter acesso a um bote salva vidas, talvez?

- **Classe = 3ª:** Bom, se ser da 1ª seria um valor positivo, esse imagino que deve ter um sinal negativo então, estar na terceira classe diminuía sua chance de sobreviver, faz sentido?

- **Idade:** Imagino que pessoas mais velhas diminua um pouco as chances, então talvez seja negativo, quanto mais velho menor é a probabilidade de sobrevivência.

*(note que eu pulei a classe 2)*

Para cada novo passageiro, o algoritmo calcula um "score de sobrevivência" combinando suas características com os pesos aprendidos.

- **Score_Sobrevivência = (Peso_sexo x Valor_Sexo) + (Peso_Classe x Valor_Classe) + (Peso_Idade x Valor_Idade) + ...**

Este é o **log-odds**, um número único que resume toda a evidência.

- Logodds positivos -> Probabilidade maior que 0.5
- Logodds negativos -> probabilidade menor que 0.5

**2. Função Logística**

Por mais que o log-odds é interessante, ele não é intuitivo. Precisamos ir atrás de uma probabilidade: um número claro entre 0% e 100%

É aqui que entra a Função Logística (ou Sigmoide):

- Ela pega o score (de $-\infin$ a $\infin$) e transforma em um valor entre 0 e 1

A intuiçlão é a seguinte:

- Score muito alto é convertido em uma prob. perto de 1 

- Score muito baixo é convertido em uma prob. perto de 0

- Score igual a zero é convertido para 0.5

![Função sigmoide (logística)](https://upload.wikimedia.org/wikipedia/commons/8/88/Logistic-curve.svg)

** 3. Classificação**

Agora, para cada passageiro, temos uma probabilidade clara. Para fazer a classificação final, estabelecemos um limiar de decisão (default 50%)

- Se Prob. de sobrevivência > 0.5, o modelo prevê que o passageiro Sobreviveu (1)

- (0), cc.


### Intuição 

Agora, vamos analisar os dados do naufrágio do Titanic em 1912. 
Você tem informações sobre um passageiro desconhecido:

- Idade: 22 anos
- Classe: 3ª classe 
- Sexo: Masculino

Pergunta: **O Jack sobreviveu ou não sobreviveu ao naufrágio?**



```python
# ==================================================
import kagglehub
from kagglehub import KaggleDatasetAdapter

# Load the latest version
df = kagglehub.dataset_load(
  KaggleDatasetAdapter.PANDAS,
  "yasserh/titanic-dataset",
  "Titanic-Dataset.csv",
  pandas_kwargs={"encoding": "latin", "usecols": [1, 2, 4, 5]}
)
# ==================================================
```


```python
import pandas as pd
```


```python
#=================================================  
# Análise exploratória
#=================================================

print(f"Dataset shape: {df.shape}")
print("---" * 20)
print(f"\nDataset columns: {df.columns.tolist()}")
print("---" * 20)
print(f"\nDataset info:")
df.info()

print("---" * 20)
print(f"\nDataset description:")
print(df.describe())
print("---" * 20)
```

    Dataset shape: (891, 4)
    ------------------------------------------------------------
    
    Dataset columns: ['Survived', 'Pclass', 'Sex', 'Age']
    ------------------------------------------------------------
    
    Dataset info:
    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 891 entries, 0 to 890
    Data columns (total 4 columns):
     #   Column    Non-Null Count  Dtype  
    ---  ------    --------------  -----  
     0   Survived  891 non-null    int64  
     1   Pclass    891 non-null    int64  
     2   Sex       891 non-null    object 
     3   Age       714 non-null    float64
    dtypes: float64(1), int64(2), object(1)
    memory usage: 28.0+ KB
    ------------------------------------------------------------
    
    Dataset description:
             Survived      Pclass         Age
    count  891.000000  891.000000  714.000000
    mean     0.383838    2.308642   29.699118
    std      0.486592    0.836071   14.526497
    min      0.000000    1.000000    0.420000
    25%      0.000000    2.000000   20.125000
    50%      0.000000    3.000000   28.000000
    75%      1.000000    3.000000   38.000000
    max      1.000000    3.000000   80.000000
    ------------------------------------------------------------
    


```python
# Sobrevivência por categoria

survival_by_sex = df.groupby("Sex")["Survived"].agg(["mean", "count"])
survival_by_sex["mean"] *= 100  
print(survival_by_sex)

print("---" * 20)

survival_by_class = df.groupby("Pclass")["Survived"].agg(["mean", "count"])
survival_by_class["mean"] *= 100
print(survival_by_class)

print("---" * 20)

df['Age_group'] = pd.cut(df['Age'], bins=[0, 16, 35, 60, 100], 
                         labels=['Child(0-16)', 'Young Adult(17-35)', 'Adult(36-60)', 'Senior(61+)'])

survival_by_age = df.groupby("Age_group", observed=True)["Survived"].agg(["mean", "count"])
survival_by_age["mean"] *= 100
print(survival_by_age)

print("---" * 20)


```

                 mean  count
    Sex                     
    female  74.203822    314
    male    18.890815    577
    ------------------------------------------------------------
                 mean  count
    Pclass                  
    1       62.962963    216
    2       47.282609    184
    3       24.236253    491
    ------------------------------------------------------------
                             mean  count
    Age_group                           
    Child(0-16)         55.000000    100
    Young Adult(17-35)  38.287154    397
    Adult(36-60)        40.000000    195
    Senior(61+)         22.727273     22
    ------------------------------------------------------------
    


```python
# Visualizações
# ==================================================
import matplotlib.pyplot as plt
import seaborn as sns

fig, axes = plt.subplots(2, 2, figsize=(14, 10))

fig.suptitle('Análise do Conjunto de Dados do Titanic', fontsize=16, fontweight='bold')

ax1 = axes[0, 0]
survival_sex = df.groupby('Sex')['Survived'].mean() * 100
bars = ax1.bar(survival_sex.index, survival_sex.values, color=['lightcoral', 'skyblue'], alpha=0.7, edgecolor='black', linewidth=2)
ax1.set_ylabel('Taxa de Sobrevivência (%)')
ax1.set_ylim(0, 100)
ax1.set_title('Taxa de Sobrevivência por Gênero', fontsize=14)
ax1.grid(axis='y', linestyle='--', alpha=0.7)
for bar in bars:
    height = bar.get_height()
    ax1.text(bar.get_x() + bar.get_width() / 2, height + 1, f'{height:.1f}%', ha='center', va='bottom')

ax2 = axes[0, 1]
survival_class = df.groupby('Pclass')['Survived'].mean() * 100
bars = ax2.bar(survival_class.index.astype(str), survival_class.values, color=['lightgreen', 'orange', 'lightgrey'], alpha=0.7, edgecolor='black', linewidth=2)
ax2.set_ylabel('Taxa de Sobrevivência (%)')
ax2.set_ylim(0, 100)
ax2.set_title('Taxa de Sobrevivência por Classe do Passageiro', fontsize=14)
ax2.grid(axis='y', linestyle='--', alpha=0.7)
for bar in bars:
    height = bar.get_height()
    ax2.text(bar.get_x() + bar.get_width() / 2, height + 1, f'{height:.1f}%', ha='center', va='bottom')

ax3 = axes[1, 0]
survived = df[df['Survived'] == 1]['Age']
died = df[df['Survived'] == 0]['Age']
ax3.hist([died, survived], bins=20, stacked=True, color=['lightcoral', 'lightblue'], edgecolor='black', alpha=0.7)
ax3.set_xlabel('Idade')
ax3.set_ylabel('Número de Passageiros')
ax3.set_title('Distribuição de Idade por Status de Sobrevivência', fontsize=14)
ax3.legend(['Não Sobreviveu', 'Sobreviveu'])
ax3.grid(axis='y', linestyle='--', alpha=0.7)

ax4 = axes[1, 1]
pivot = df.pivot_table(values='Survived', index='Pclass', columns='Sex', aggfunc='mean')
sns.heatmap(
    pivot * 100, annot=True, fmt=".1f",
    cmap='YlGnBu', cbar_kws={'label': 'Taxa de Sobrevivência (%)'},
    ax=ax4, linewidths=.5, linecolor='black'
)
ax4.set_title('Taxa de Sobrevivência por Classe e Gênero', fontsize=14)
ax4.set_ylabel('Classe do Passageiro')
ax4.set_xlabel('Gênero')

plt.tight_layout()
plt.show()
```


    
![png](case_ia_files/case_ia_239_0.png)
    


Note algumas coisas:

- Mulheres tiveram uma taxa de 74.2% de sobrevivência vs 18.9% dos homens

- Passageiros da 1ª classe: 63.0% de sobrevivência

- Passageiros da 3ª classe: 24.2% de sobrevivência

- Crianças (0-16 anos): 55% de sobrevivência

Parece que mulheres e crianças primeiro era real



```python
# =================================================
# Entendendo a sigmóide
# =================================================

import numpy as np

def sigmoid(z):
    return 1 / (1 + np.exp(-z))

z_values = np.linspace(-10, 10, 400)
sigmoid_values = sigmoid(z_values)

fig, ax = plt.subplots(figsize=(12, 6))
ax.plot(z_values, sigmoid_values, 'b-', linewidth=2, label='Função Sigmóide')
ax.axhline(0.5, color='black', linestyle='--', linewidth=2, alpha=0.7, label='Limiar de decisão (0.5)')
ax.axvline(0, color='black', linewidth=1, linestyle='--', alpha=0.5)
ax.fill_between(z_values, 0, sigmoid_values, where=(sigmoid_values >= 0.5), color='lightblue', alpha=0.5, label='Classe 1 (Sobreviveu)')
ax.fill_between(z_values, 0, sigmoid_values, where=(sigmoid_values < 0.5), color='lightcoral', alpha=0.5, label='Classe 0 (Não Sobreviveu)')

examples = [
    (-6, sigmoid(-6), "z=-6"), (-3, sigmoid(-3), "z=-3"), (0, sigmoid(0), "z=0"), (3, sigmoid(3), "z=3"), (6, sigmoid(6), "z=6")
]

for z, s, label in examples:  
    ax.plot(z, s, 'ro', markersize=10)
    ax.annotate(f'{label}\n({s:.2f})', xy=(z, s), xytext=(z, s + 0.03),
                arrowprops=dict(facecolor='wheat', arrowstyle='->'),
                fontsize=10, ha='center')

ax.set_title('Função Sigmóide e Limiar de Decisão', fontsize=16, fontweight='bold')
ax.set_xlabel('Valor de z', fontsize=14)
ax.set_ylabel('Sigmóide(z)', fontsize=14)
ax.set_ylim(-0.1, 1.1)
ax.legend()
plt.grid(linestyle='--', alpha=0.7)
plt.show()

```


    
![png](case_ia_files/case_ia_241_0.png)
    


### Formulação Formal

**Log-Odds (Logit)**

A odd de um evento é a razão entre a probabilidade de ele ocorrer $(p)$ e a probabilidade de não ocorrer $(1-p)$

$ Odds = \frac{p}{1-p}$

A Regressão Logística assume que o logaritmo da odd (**log-odds ou logit**) é uma função linear das features:

$\ln \left(\frac{p}{1-p}\right) = \mathbf{w}^T\mathbf{x}+b$

Onde $\mathbf{w}$ e $\mathbf{x}$ são os vetores de pesos e features respectivamente.

Note que, ao isolar $p$ na equação, obtemos exatamente a função sigmoide.

**Entrada**

1. Conjunto de treinamento de n amostra em pares $D=\{(x^{(1)}, y^{(1)}), (x^{(2)}, x^{(i)}), ..., x^{(n)}, y^{(n)}\}$

    onde:

    - $x^{(i)}$: vetor de d features ($x^{(i)} = (x^{(i)}_1, x^{(i)}_2, ..., x^{(i)}_d)$), também adicionamos o termo de intercepto $x_0{(i)} = 1$, portanto $x^{(i)} \in \mathbb{R}^{d+1}$

    - $y^{(i)}$: rótulo de classe binário, ou seja, $y^{(i)} \in \{0,1\}$



**Processamento**

O processamento aqui consiste em aprender um vetor de parâmetro (pesos) $\mathbf{w} \in \mathbb{R}^{d+1}$ que melhor mapeia as entradas $x$ para saídas $y$

**1. Log Loss**

Para uma única amostra de treinamento (x, y) a função custo é definida como:

$L(\hat{p}, y) = -[y\log{(\hat{p})}+(1-y)log(1-\hat{p})]$

Essa função penaliza as predições erradas:

- Se a classe real é $y=1$, a perda é $-log(\hat{p})$ se o modelo prevê \hat{p} -> 0, a perda tende a $\infin$

- Se a classe real é $y=0$, a perda é $-log(1-\hat{p})$ se o modelo prevê \hat{p} -> 1, a perda tende a $\infin$

A função custo total $J(\mathbf{w}, b)$ para o conjunto de dados inteiro é a média das perdas individuais:

$J(\mathbf{w}, b) = -\frac{1}{n}\sum^n_{i=1}[y^{(i)}\log{(h_{\mathbf{w}, b}(x^{(i)}))} + (1-y^{(i)})\log{(1-h_{\mathbf{w}, b}(x^{(i)}))}]$

Assim encontramos um mínimo global a partir dela

**2. Otimização**

Para minimizar $J(\mathbf{w}, b)$, utilizamos o algoritmo Gradiente Descendente. Ele atualiza iterativamente os parâmetros na direção oposta ao gradiente da função de custo.

As CPOs da função de custo em relação a cada peso $w_j$ e ao bias b são:

1: $\frac{\partial J}{\partial w_j} = \frac{1}{n}\sum^n_{i=1}(h_{\mathbf{w}, b}(x^{(i)}) - y^{(i)})x_j^{(i)}$

2: $\frac{\partial J}{\partial b} = \frac{1}{n}\sum^n_{i=1}(h_{\mathbf{w}, b}(x^{(i)}) - y^{(i)})$

As regras de atualização a cada iteração são:

$w_j := w_j - \alpha\frac{\partial J}{\partial w_j}$

$b := b - \alpha\frac{\partial J}{\partial b}$

onde $\alpha$ é chamado de (learning rate)

**Saída - Classificação**

- **Parâmetros do Modelo**: Um vetor de pesos $mathbb{w}$ e um bias $b$ otimizados

- **Predição**: Para uma nova amostra $x^o$, o modelo calcula a probabilidade $\hat{p} = \sigma (\mathbf{w}^T x^o + b)$

- **Classificação**: Um limiar de decisão (threshold), e.g. 0.5, é aplicado à probabilidade para obter a classe final:

$\hat{y} = 
\begin{cases}
1, & \text{se } \hat{p} \geq 0.5 \\
0, & \text{se } \hat{p} < 0.5
\end{cases}
$

**Considerações**

1. Interpretação dos Coeficientes: 

- Os pesos ($w_j$) podem ser interpretados de forma intuitiva, quando exponenciados, obtemos a razão de chances:

    - Para cada aumento de uma unidade em $x_j$, as odds do resultado ser $y=1$ é multiplicada por $\mathbb{e}^{w_j}$

2. Fronteira de Decisão (Decision Boundary)

A fronteira de decisão é a superficie que separa as classes. No caso da Regressão logística, ela ocorre onde a probabilidade é exatamente 0.5, como vimos, o que corresponde a $z=\mathbf{w}^T + b = 0$. Note que a fronteira de deciçao da Regressão Logística é linear

3. Regularização (L1 e L2)

Para evitar overfitting, especialmente com um grande número de features, fazemos o seguinte:

- **Ridge (L2)**: Adiciona $\frac{\lambda}{2n} \sum^d_{j=1}w^2_j$ para penalizar pesos grandes

- **Lasso (L1)**: Adiciona $\frac{\lambda}{n} \sum^d_{j=1}|w_j|$ para forçar os pesos a se tornaerem exatamente zero

- Saiba mais: [Regularization: avoiding overfitting](https://medium.com/@rithpansanga/logistic-regression-and-regularization-avoiding-overfitting-and-improving-generalization-e9afdcddd09d)

4. Extensão para Classificação Multiclasse (Regressão Softmax)

- Regressão Logística pode ser generalizada para problemas com mais de duas classes através da regressão softmax. Ela usa a função Softmax, em vez da sigmoide, para calcular a probabilidade de cada uma das $K$ classes

    - $P(y=k|x) = \frac{e^{z_k}}{\sum^K_{j=1}e^z_j}$

- Saiba mais: [Softmax Regression](https://rasbt.github.io/mlxtend/user_guide/classifier/SoftmaxRegression/#:~:text=Softmax%20Regression%20(synonyms%3A%20Multinomial%20Logistic,the%20classes%20are%20mutually%20exclusive).)

### Desafio: "From Scratch"

Vamos implementar o algoritmo de Regressão Logística do zero


```python
class LogisticRegression:
    def __init__(self, learning_rate=0.01, n_iterations=1000):
        """
        Inicializa o modelo de Regressão Logística.

        Parâmetros:
        -----------
        learning_rate: float
            α para o gradiente descendente.
        n_iterations: int
            Número de iterações do gradiente descendente.

        """
        pass


    def _add_intercept(self, X):
        """
        Adiciona uma coluna de intercepto (bias) aos dados de entrada.

        Parâmetros:
        -----------
        X: np.ndarray
            Matriz de características.

        Retorna:
        --------
        np.ndarray
            Matriz de características com a coluna de intercepto adicionada.
        """
        pass


    def _sigmoid(self, z):
        """
        Aplica a função sigmóide.

        Parâmetros:
        -----------
        z: np.ndarray
            Valor ou matriz de valores para aplicar a função sigmóide.

        Retorna:
        --------
        np.ndarray
            Valor(es) transformados pela função sigmóide.
        """
        pass

    def _compute_cost(self, h, y):
        """
        Calcula a função de custo (loss).

        Parâmetros:
        -----------
        h: np.ndarray
            Saídas do modelo (valores previstos).
        y: np.ndarray
            Rótulos verdadeiros.

        Retorna:
        --------
        float
            Valor da função de custo.
        """
        pass

    def fit(self, X, y):
        """
        Treina o modelo de Regressão Logística usando gradiente descendente.

        Processo: 
        1. Adiciona a coluna de intercepto aos dados de entrada.
        2. Inicializa os pesos.
        3. Para cada iteração:
              a. Calcula as previsões (h).
              b. Calcula a função de custo (loss).
              c. Calcula o gradiente.
              d. Atualiza os pesos.
        Parâmetros:
        -----------
        X: np.ndarray
            Matriz de características.
        y: np.ndarray
            Rótulos verdadeiros.
        """
        pass

    def predict_proba(self, X):
        """
        Faz previsões de probabilidade para os dados de entrada.

        Parâmetros:
        -----------
        X: np.ndarray
            Matriz de características.

        Retorna:
        --------
        np.ndarray
            Probabilidades previstas para cada classe.
        """
        pass
    
    def predict(self, X, threshold=0.5):
        """
        Faz previsões de classe para os dados de entrada com base em um limiar.

        Parâmetros:
        -----------
        X: np.ndarray
            Matriz de características.
        threshold: float
            Limiar para classificar as previsões.

        Retorna:
        --------
        np.ndarray
            Classes previstas (0 ou 1).
        """
        pass

    def score(self, X, y, threshold=0.5):
        """
        Calcula a acurácia do modelo.

        Parâmetros:
        -----------
        X: np.ndarray
            Matriz de características.
        y: np.ndarray
            Rótulos verdadeiros.
        threshold: float
            Limiar para classificar as previsões.

        Retorna:
        --------
        float
            Acurácia do modelo.
        """
        pass
```


```python
# Dados para Teste
# ==================================================
import kagglehub
from kagglehub import KaggleDatasetAdapter

# Load the latest version
df = kagglehub.dataset_load(
  KaggleDatasetAdapter.PANDAS,
  "yasserh/titanic-dataset",
  "Titanic-Dataset.csv",
  pandas_kwargs={"encoding": "latin", "usecols": [1, 2, 4, 5]}
)

X = df[['Pclass', 'Sex', 'Age']].values
y = df['Survived'].values

```

## **3.4 Máquinas de Vetores de Suporte (SVM)**

Fonte: https://www.ibm.com/br-pt/think/topics/support-vector-machine

https://medium.com/turing-talks/turing-talks-12-classifica%C3%A7%C3%A3o-por-svm-f4598094a3f1

https://uk.mathworks.com/discovery/support-vector-machine.html

Support Vector Machines (SVM) são algoritmos de aprendizado supervisionado que podem ser usados tanto para classificação quanto para regressão. O objetivo principal do SVM é encontrar a melhor fronteira de decisão que separa diferentes classes de dados com a maior margem possível.

Imagine que você tem dados de duas classes que podem ser separados por uma linha. Mas existem infinitas linhas que poderiam separar essas duas classes. O SVM encontra a linha que maximiza a distância entre os pontos mais próximos de cada classe.

**1. Conceitos Fundamentais**

O SVM funciona encontrando o hiperplano que melhor separa as classes. Para dados bidimensionais, esse hiperplano é uma linha. Para dados tridimensionais, é um plano. Para dimensões maiores, continuamos chamando de hiperplano.

Os pontos mais próximos à fronteira de decisão são chamados de **Support Vectors** (Vetores de Suporte). Estes são os pontos mais importantes porque determinam a posição da fronteira.

A **margem** é a distância entre a fronteira de decisão e os support vectors mais próximos. O SVM busca maximizar essa margem.

<img src="https://uk.mathworks.com/discovery/support-vector-machine/_jcr_content/mainParsys/band_1231704498_copy/mainParsys/lockedsubnav/mainParsys/columns/4d6875cb-8556-43eb-9393-53bcec9e3682/columns/29ee2f91-358a-4aca-8f04-e0f536feb8f2/image_2128876021_cop.adapt.full.medium.jpg/1759842383498.jpg">

**2. Kernel Trick**

Na prática, nem sempre os dados são linearmente separáveis. Nesses casos, o SVM usa o "kernel trick" para mapear os dados para um espaço de maior dimensão onde podem se tornar linearmente separáveis.

Tipos de kernels comuns:
- **Linear**: Para dados já linearmente separáveis
- **Polinomial**: Para dados com relacionamentos polinomiais  
- **RBF (Radial Basis Function)**: O mais comum, funciona bem para a maioria dos casos
- **Sigmoid**: Usado em casos específicos

**3. Parâmetros Importantes**

- **C (regularização)**: Controla o trade-off entre maximizar a margem e minimizar os erros de classificação
  - C alto: Margem menor, menos erros de treinamento
  - C baixo: Margem maior, mais tolerante a erros

- **Gamma** (para kernels RBF): Define quão longe a influência de um único exemplo de treinamento alcança
  - Gamma alto: Influência apenas de pontos próximos (pode causar overfitting)
  - Gamma baixo: Influência mais ampla (pode causar underfitting)

### Intuição 

Vamos retornar com o Íris dataset:

**A ideia:**

Imagine que você encontrou uma flor íris na natureza e mediu suas caracteríristicas:
- Comprimento da pétala: 4.5 cm
- Largura da pétala: 1.5 cm

Existem 3 espécies de íris: Setosa, Versicolor e a Virginica.

Pergunta: **Qual espécie essa flor pertence?**


```python
# ================================================
# Bibliotecas

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.datasets import load_iris
```


```python
# =================================================
# 1. Análise Exploratória
# =================================================

iris = load_iris()
X = iris.data[:, [2, 3]] 
y = iris.target

print(f"Iris data shape: {X.shape}")
print(f"\n Classes:")
for i, name in enumerate(iris.target_names):
    count = np.sum(y == i)
    print(f" {i}: {name} ({count} samples)")

# Visualização dos dados
fig, ax = plt.subplots(figsize=(12, 8))

color = ['red', 'blue', 'green']
marker = ['o', 's', '^']

for i, name in enumerate(iris.target_names):
    indices = y == i
    ax.scatter(X[indices, 0], X[indices, 1], 
    c=color[i], marker=marker[i], s=100, alpha=0.7, 
    edgecolors='k', linewidth=1.5, label=name.capitalize())

ax.set_xlabel(iris.feature_names[2].capitalize(), fontsize=12, fontweight='bold')
ax.set_ylabel(iris.feature_names[3].capitalize(), fontsize=12, fontweight='bold')
ax.set_title('Iris Dataset - Sepal Length vs Sepal Width', fontsize=14, fontweight='bold', pad=20)
ax.legend(fontsize=11, loc='upper left')
ax.grid(True, alpha=0.3)
plt.tight_layout()
plt.show()
```

    Iris data shape: (150, 2)
    
     Classes:
     0: setosa (50 samples)
     1: versicolor (50 samples)
     2: virginica (50 samples)
    


    
![png](case_ia_files/case_ia_257_1.png)
    



```python
# =================================================
#2. Setosa vs Não-Setosa
# Ideia:
#  - Transformar o problema em binário para facilitar a visualização
#  - Setosa (0) vs Não-Setosa (1)
# =================================================

y_binary = (y != 0).astype(int)

fig, axes = plt.subplots(1, 3, figsize=(18, 5))
fig.suptitle('SVM: Conceitos', fontsize=16, fontweight='bold', y=1.02)

# Gráfico 1: Fronteiras de Decisão
ax1 = axes[0]

setosa_mask = y_binary == 0
not_setosa_mask = y_binary == 1

ax1.scatter(X[setosa_mask, 0], X[setosa_mask, 1],
            c='red', s=100, alpha=0.7, edgecolors='k', linewidth=1.5,
            label='Setosa', marker='o')

ax1.scatter(X[not_setosa_mask, 0], X[not_setosa_mask, 1],
            c='blue', s=100, alpha=0.7, edgecolors='k', linewidth=1.5,
            label='Não-Setosa', marker='s')

x_line = np.linspace(0, 7, 100)

y_line1 = -0.3 * x_line + 1
ax1.plot(x_line, y_line1, 'gray', linestyle='--', linewidth=2, alpha=0.5, label='Fronteira Ruim')

y_line2 = 0.02 * x_line + 0.7
ax1.plot(x_line, y_line2, 'orange', linestyle='--', linewidth=2, alpha=0.7, label='Fronteira OK')

y_line3 = -0.3 * x_line + 1.5
ax1.plot(x_line, y_line3, 'green', linestyle='-', linewidth=3, label='Fronteira SVM (ótima)')

ax1.set_xlabel('Comprimento da Pétala (cm)', fontsize=11, fontweight='bold')
ax1.set_ylabel('Largura da Pétala (cm)', fontsize=11, fontweight='bold')
ax1.set_title('Fronteiras de Decisão', fontsize=12, fontweight='bold', pad=15)
ax1.legend(fontsize=9, loc='upper left')
ax1.set_xlim(0, 7)
ax1.set_ylim(0, 2.8)
ax1.grid(True, alpha=0.3)

# Gráfico 2: Margens
ax2 = axes[1]

ax2.scatter(X[setosa_mask, 0], X[setosa_mask, 1],
            c='red', s=100, alpha=0.7, edgecolors='k', linewidth=1.5,
            label='Setosa', marker='o')

ax2.scatter(X[not_setosa_mask, 0], X[not_setosa_mask, 1],
            c='blue', s=100, alpha=0.7, edgecolors='k', linewidth=1.5,
            label='Não-Setosa', marker='s')

y_hyperplane = -0.3 * x_line + 1.5
ax2.plot(x_line, y_hyperplane, 'green', linestyle='-', linewidth=3,
         label='Hiperplano')

margin = 0.4
y_margin1 = y_hyperplane + margin
y_margin2 = y_hyperplane - margin

ax2.plot(x_line, y_margin1, 'green', linestyle=':', linewidth=2, alpha=0.7)
ax2.plot(x_line, y_margin2, 'green', linestyle=':', linewidth=2, alpha=0.7)
ax2.fill_between(x_line, y_margin1, y_margin2, color='green', alpha=0.1, 
                 label='Margem')

support_vectors = []
for i in range(len(X)):
    x_val, y_val = X[i]
    if 0 < x_val < 7:
        y_pred = -0.3 * x_val + 1.5
        if abs(y_val - y_pred) <= margin + 0.15:
            support_vectors.append(i)

if len(support_vectors) > 0:
    sv_points = X[support_vectors]
    ax2.scatter(sv_points[:, 0], sv_points[:, 1],
                s=200, facecolors='none', edgecolors='gold', linewidth=2,
                label='Support Vectors')
    
ax2.set_xlabel('Comprimento da Pétala (cm)', fontsize=11, fontweight='bold')
ax2.set_ylabel('Largura da Pétala (cm)', fontsize=11, fontweight='bold')
ax2.set_title('Margens e Support Vectors', fontsize=12, fontweight='bold', pad=15)
ax2.legend(fontsize=9, loc='upper left')
ax2.set_xlim(0, 7)
ax2.set_ylim(0, 2.8)
ax2.grid(True, alpha=0.3)

# Gráfico 3: Regiões de Decisão
ax3 = axes[2]

x_min, x_max = 0, 7
y_min, y_max = 0, 2.8
xx, yy = np.meshgrid(np.linspace(x_min, x_max, 200), np.linspace(y_min, y_max, 200))

Z = (yy > (-0.3 * xx + 1.5)).astype(int)

ax3.contourf(xx, yy, Z, alpha=0.3, levels=1, colors=['red', 'blue'])
ax3.contour(xx, yy, Z, levels=1, colors='green', linewidths=3)
ax3.scatter(X[setosa_mask, 0], X[setosa_mask, 1],
            c='red', s=100, alpha=0.9, edgecolors='k', linewidth=1.5,
            label='Setosa', marker='o')
ax3.scatter(X[not_setosa_mask, 0], X[not_setosa_mask, 1],
            c='blue', s=100, alpha=0.9, edgecolors='k', linewidth=1.5,
            label='Não-Setosa', marker='s')

ax3.set_xlabel('Comprimento da Pétala (cm)', fontsize=11, fontweight='bold')
ax3.set_ylabel('Largura da Pétala (cm)', fontsize=11, fontweight='bold')
ax3.set_title('Regiões de Decisão', fontsize=12, 
              fontweight='bold', pad=15)
ax3.legend(fontsize=9, loc='upper left')
ax3.set_xlim(0, 7)
ax3.set_ylim(0, 2.8)
ax3.grid(True, alpha=0.3)
```


    
![png](case_ia_files/case_ia_258_0.png)
    


---

**Vamos dificultar um pouco mais o problema**

**E se os dados não forem linearmente separáveis?**
- e.g., Cículos côncêntricos
    - Classe Vermelha: Círculo interior
    - Classe Azul: Círculo exterior

Vamos fazer isso!

---




```python
# =================================================
# 3. Kernel Trick

# Ideia:
# - Projete os dados em um espaço de dimensão maior
# - Lá, eles se tornam linearmente separáveis
# - Encontre o hiperplano nesse novo espaço
# - Volte para o espaço original
# =================================================

from sklearn.datasets import make_circles   

X_circles, y_circles = make_circles(n_samples=300, noise=0.05, factor=0.5, random_state=42)

fig, axes = plt.subplots(1, 2, figsize=(14, 6))
fig.suptitle('Kernel Trick', fontsize=16, fontweight='bold', y=1.02)

# Gráfico 1: Dados Originais
ax1 = axes[0]

ax1.scatter(X_circles[y_circles == 0, 0], X_circles[y_circles == 0, 1],
            c='red', s=100, alpha=0.7, edgecolors='k', linewidth=1.5,
            label='Classe 0', marker='o')
ax1.scatter(X_circles[y_circles == 1, 0], X_circles[y_circles == 1, 1],
            c='blue', s=100, alpha=0.7, edgecolors='k', linewidth=1.5,
            label='Classe 1', marker='s')

ax1.set_xlabel('Feature 1', fontsize=11, fontweight='bold')
ax1.set_ylabel('Feature 2', fontsize=11, fontweight='bold')
ax1.set_title('Dados Originais', fontsize=12, fontweight='bold', pad=15)
ax1.legend(fontsize=9, loc='upper right')
ax1.set_xlim(-1.5, 1.5)
ax1.set_ylim(-1.5, 1.5)
ax1.grid(True, alpha=0.3)

# Gráfico 2: Com Kernel RBF (Gaussiano)
ax2 = axes[1]

ax2.scatter(X_circles[y_circles == 0, 0], X_circles[y_circles == 0, 1],
            c='red', s=80, alpha=0.7, edgecolors='k', linewidth=1,
            label='Classe 0', marker='o')
ax2.scatter(X_circles[y_circles == 1, 0], X_circles[y_circles == 1, 1],
            c='blue', s=80, alpha=0.7, edgecolors='k', linewidth=1,
            label='Classe 1', marker='s')

# Desenhar fronteira de decisão circular (resultado do kernel RBF (você verá isso mais tarde))
theta_circle = np.linspace(0, 2 * np.pi, 100)
r_boundary = 0.75
x_boundary = r_boundary * np.cos(theta_circle)
y_boundary = r_boundary * np.sin(theta_circle)
ax2.plot(x_boundary, y_boundary, 'green', linestyle='-', linewidth=3,
            label='Fronteira de Decisão (Kernel RBF)')

# Áreas de decisão
circle = plt.Circle((0, 0), r_boundary, alpha=0.1, color='blue')
ax2.add_patch(circle)
ax2.fill_between([0], [0], [0], color='blue', alpha=0.3)



ax2.set_xlabel('Feature 1', fontsize=11, fontweight='bold')
ax2.set_ylabel('Feature 2', fontsize=11, fontweight='bold')
ax2.set_title('Com Kernel RBF (Gaussiano)', fontsize=12, fontweight='bold', pad=15)
ax2.legend(fontsize=9, loc='upper right')
ax2.set_xlim(-1.5, 1.5)
ax2.set_ylim(-1.5, 1.5)
ax2.grid(True, alpha=0.3)
ax2.set_aspect('equal', 'box')

plt.show()
```


    
![png](case_ia_files/case_ia_260_0.png)
    


### Formulação Formal

**Entrada**

1. Conjunto de treinamento de n amostras em pares $D=\{(x^{(1)}, y^{(1)}), (x^{(2)}, y^{(2)}), ..., (x^{(n)}, y^{(n)})\}$

    onde:

    - $x^{(i)}$: vetor de d features ($x^{(i)} = (x^{(i)}_1, x^{(i)}_2, ..., x^{(i)}_d)$), portanto $x^{(i)} \in \mathbb{R}^d$

    - $y^{(i)}$: rótulo de classe binário, ou seja, $y^{(i)} \in \{-1, +1\}$ (diferente dos outros algoritmos que usam {0,1})

**Processamento**

O objetivo é encontrar o hiperplano que separa as classes com a maior margem possível.

**1. Hiperplano de Separação**

O hiperplano é definido por:

$\mathbf{w}^T\mathbf{x} + b = 0$

onde $\mathbf{w}$ é o vetor normal ao hiperplano e $b$ é o bias.

Para classificação:
- Se $\mathbf{w}^T\mathbf{x} + b > 0$, então $\hat{y} = +1$
- Se $\mathbf{w}^T\mathbf{x} + b < 0$, então $\hat{y} = -1$

**2. Margem**

A distância de um ponto $\mathbf{x}^{(i)}$ ao hiperplano é:

$\text{distância} = \frac{|\mathbf{w}^T\mathbf{x}^{(i)} + b|}{||\mathbf{w}||}$

Para os pontos corretamente classificados:
$y^{(i)}(\mathbf{w}^T\mathbf{x}^{(i)} + b) \geq 1$

A margem total é $\frac{2}{||\mathbf{w}||}$

**3. Problema de Otimização (Hard Margin)**

Para dados linearmente separáveis, queremos maximizar a margem:

$\max_{\mathbf{w}, b} \frac{2}{||\mathbf{w}||} \Leftrightarrow \min_{\mathbf{w}, b} \frac{1}{2}||\mathbf{w}||^2$

Sujeito a: $y^{(i)}(\mathbf{w}^T\mathbf{x}^{(i)} + b) \geq 1$ para $i = 1, ..., n$

**4. Soft Margin (Dados não Separáveis)**

Para dados não linearmente separáveis, introduzimos variáveis de folga $\xi_i$:

$\min_{\mathbf{w}, b, \xi} \frac{1}{2}||\mathbf{w}||^2 + C\sum_{i=1}^{n}\xi_i$

Sujeito a:
- $y^{(i)}(\mathbf{w}^T\mathbf{x}^{(i)} + b) \geq 1 - \xi_i$
- $\xi_i \geq 0$

onde $C$ é o parâmetro de regularização que controla o trade-off entre maximizar a margem e minimizar os erros.

**5. Kernel Trick**

Para dados não linearmente separáveis, mapeamos para um espaço de maior dimensão usando funções kernel:

$K(\mathbf{x}^{(i)}, \mathbf{x}^{(j)}) = \phi(\mathbf{x}^{(i)})^T\phi(\mathbf{x}^{(j)})$

Kernels comuns:

- **Linear**: $K(\mathbf{x}_i, \mathbf{x}_j) = \mathbf{x}_i^T\mathbf{x}_j$

- **Polinomial**: $K(\mathbf{x}_i, \mathbf{x}_j) = (\gamma\mathbf{x}_i^T\mathbf{x}_j + r)^d$

- **RBF (Gaussiano)**: $K(\mathbf{x}_i, \mathbf{x}_j) = \exp(-\gamma||\mathbf{x}_i - \mathbf{x}_j||^2)$

- **Sigmoid**: $K(\mathbf{x}_i, \mathbf{x}_j) = \tanh(\gamma\mathbf{x}_i^T\mathbf{x}_j + r)$

**Saída - Classificação**

- **Parâmetros do Modelo**: Vetores de suporte e seus coeficientes $\alpha_i$

- **Função de Decisão**: $f(\mathbf{x}) = \sum_{i \in SV} \alpha_i y^{(i)} K(\mathbf{x}^{(i)}, \mathbf{x}) + b$

- **Predição**: $\hat{y} = \text{sign}(f(\mathbf{x}))$

onde $SV$ representa o conjunto de índices dos vetores de suporte.


Saiba Mais: https://medium.com/data-science/the-kernel-trick-c98cdbcaeb3f

### Desafio: "From Scratch"

Vamos implementar uma versão simplificada do algoritmo SVM do zero


```python
class SimpleSVM:
    def __init__(self, learning_rate=0.001, lambda_param=0.01, n_iterations=1000):
        """
        Implementação simplificada do SVM usando gradiente descendente.
        
        Parâmetros:
        -----------
        learning_rate: float
            Taxa de aprendizagem para o gradiente descendente.
        lambda_param: float 
            Parâmetro de regularização (equivalente a 1/C no sklearn).
        n_iterations: int
            Número de iterações para treinamento.
        """
        pass

    def fit(self, X, y):
        """
        Treina o modelo SVM.
        
        Parâmetros:
        -----------
        X: np.ndarray
            Matriz de características de forma (n_samples, n_features).
        y: np.ndarray
            Labels das classes (-1 ou +1).
        """
        pass

    def predict(self, X):
        """
        Faz predições para novos dados.
        
        Parâmetros:
        -----------
        X: np.ndarray
            Matriz de características.
            
        Retorna:
        --------
        np.ndarray
            Predições (-1 ou +1).
        """
        pass

    def decision_function(self, X):
        """
        Calcula a função de decisão (distância ao hiperplano).
        
        Parâmetros:
        -----------
        X: np.ndarray
            Matriz de características.
            
        Retorna:
        --------
        np.ndarray
            Valores da função de decisão.
        """
        pass

    def score(self, X, y):
        """
        Calcula a acurácia do modelo.
        
        Parâmetros:
        -----------
        X: np.ndarray
            Matriz de características.
        y: np.ndarray
            Labels verdadeiros.
            
        Retorna:
        --------
        float
            Acurácia do modelo.
        """
        pass
```


```python
# Dados para Teste
# ==================================================
from sklearn.model_selection import train_test_split
import kagglehub
from kagglehub import KaggleDatasetAdapter

# Load the latest version
df = kagglehub.dataset_load(
  KaggleDatasetAdapter.PANDAS,
  "yasserh/titanic-dataset",
  "Titanic-Dataset.csv",
  pandas_kwargs={"encoding": "latin", "usecols": [1, 2, 4, 5]}
)

# Preparar os dados
df['Sex'] = df['Sex'].map({'male': 0, 'female': 1})
df['Age'] = df['Age'].fillna(df['Age'].mean())

X = df[['Pclass', 'Sex', 'Age']].values
y = df['Survived'].values

# Converter para formato SVM (-1, +1)
y = np.where(y == 0, -1, 1)

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)
```

### Usando SKlearn


```python
# Carregando os dados (novamente)
# ==================================================
import kagglehub
from kagglehub import KaggleDatasetAdapter


# Load the latest version
df = kagglehub.dataset_load(
  KaggleDatasetAdapter.PANDAS,
  "yasserh/titanic-dataset",
  "Titanic-Dataset.csv",
  pandas_kwargs={"encoding": "latin", "usecols": [1, 2, 4, 5]}
)

# Preparar os dados
df['Sex'] = df['Sex'].map({'male': 0, 'female': 1})
df['Age'] = df['Age'].fillna(df['Age'].mean())

X = df[['Pclass', 'Sex', 'Age']].values
y = df['Survived'].values

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)
```


```python
# =================================================
# Biliotecas

from sklearn.preprocessing import StandardScaler
from sklearn.svm import SVC
from sklearn.metrics import accuracy_score
```


```python
# =================================================
# 1. Básico - SVM Linear

# Ideia:
# - Normalizar features (MUITO IMPORTANTE para SVM)
# - Treinar o modelo
# =================================================

# Normalizar os dados (crucial para SVM)
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# SVM básico com kernel linear
svm = SVC(kernel='linear', random_state=42)
svm.fit(X_train_scaled, y_train)
y_pred = svm.predict(X_test_scaled)

accuracy = accuracy_score(y_test, y_pred)
print(f"SVM Linear - Acurácia: {accuracy*100:.2f}%")

# Informações sobre o modelo
print(f"Número de Support Vectors: {svm.n_support_}")
print(f"Total de Support Vectors: {len(svm.support_)}")
print(f"Proporção de Support Vectors: {len(svm.support_)/len(X_train)*100:.1f}%")
```

    SVM Linear - Acurácia: 78.21%
    Número de Support Vectors: [155 158]
    Total de Support Vectors: 313
    Proporção de Support Vectors: 44.0%
    


```python
# =================================================
# 2. Testando Diferentes Kernels

# Kernels disponíveis no sklearn:
# - 'linear': para dados linearmente separáveis
# - 'poly': kernel polinomial
# - 'rbf': Radial Basis Function (Gaussiano) - default
# - 'sigmoid': kernel sigmoide
# =================================================

kernels = ['linear', 'poly', 'rbf', 'sigmoid']
results = []

for kernel in kernels:
    # Treinar SVM com kernel específico
    svm = SVC(kernel=kernel, random_state=42)
    svm.fit(X_train_scaled, y_train)
    
    # Avaliar
    y_pred = svm.predict(X_test_scaled)
    accuracy = accuracy_score(y_test, y_pred)
    
    results.append((kernel, accuracy, len(svm.support_)))
    print(f"Kernel {kernel:8}: Acurácia = {accuracy*100:5.2f}%, Support Vectors = {len(svm.support_):3d}")

print(f"\nMelhor kernel: {max(results, key=lambda x: x[1])[0]}")
```

    Kernel linear  : Acurácia = 78.21%, Support Vectors = 313
    Kernel poly    : Acurácia = 79.33%, Support Vectors = 317
    Kernel rbf     : Acurácia = 77.09%, Support Vectors = 318
    Kernel sigmoid : Acurácia = 74.30%, Support Vectors = 264
    
    Melhor kernel: poly
    


```python
# =================================================
# 3. Parâmetros Importantes do SVM

# C (default=1.0): Parâmetro de regularização
# - C alto: Margem menor, menos tolerância a erros (pode causar overfitting)
# - C baixo: Margem maior, mais tolerância a erros (pode causar underfitting)

# gamma (para kernels RBF, poly, sigmoid): Define a influência de cada exemplo
# - gamma alto: Influência apenas de pontos próximos (pode causar overfitting)  
# - gamma baixo: Influência mais ampla (pode causar underfitting)
# - 'scale' (default): 1 / (n_features * X.var())
# - 'auto': 1 / n_features

# degree (para kernel poly): Grau do polinômio

# kernel: Tipo de kernel a ser usado
# =================================================

# Testar diferentes valores de C
C_values = [0.1, 1, 10, 100]
gamma_values = ['scale', 'auto', 0.001, 0.01, 0.1, 1]

print("Testando parâmetro C (com kernel RBF):")
for C in C_values:
    svm = SVC(kernel='rbf', C=C, random_state=42)
    svm.fit(X_train_scaled, y_train)
    accuracy = svm.score(X_test_scaled, y_test)
    print(f"C = {C:5.1f}: Acurácia = {accuracy*100:5.2f}%, Support Vectors = {len(svm.support_):3d}")

print(f"\nTestando parâmetro gamma (com kernel RBF, C=1):")
for gamma in gamma_values:
    svm = SVC(kernel='rbf', C=1, gamma=gamma, random_state=42)
    svm.fit(X_train_scaled, y_train)
    accuracy = svm.score(X_test_scaled, y_test)
    print(f"gamma = {str(gamma):5}: Acurácia = {accuracy*100:5.2f}%, Support Vectors = {len(svm.support_):3d}")
```

    Testando parâmetro C (com kernel RBF):
    C =   0.1: Acurácia = 78.21%, Support Vectors = 375
    C =   1.0: Acurácia = 77.09%, Support Vectors = 318
    C =  10.0: Acurácia = 78.21%, Support Vectors = 314
    C = 100.0: Acurácia = 77.65%, Support Vectors = 317
    
    Testando parâmetro gamma (com kernel RBF, C=1):
    gamma = scale: Acurácia = 77.09%, Support Vectors = 318
    gamma = auto : Acurácia = 77.09%, Support Vectors = 318
    gamma = 0.001: Acurácia = 78.21%, Support Vectors = 537
    gamma = 0.01 : Acurácia = 78.21%, Support Vectors = 354
    gamma = 0.1  : Acurácia = 78.21%, Support Vectors = 321
    gamma = 1    : Acurácia = 79.33%, Support Vectors = 327
    


```python
# =================================================
# 4. Otimização de Hiperparâmetros com Grid Search
# =================================================

from sklearn.model_selection import GridSearchCV
from sklearn.metrics import classification_report

# Definir espaço de busca
param_grid = {
    'C': [0.1, 1, 10, 100],
    'gamma': ['scale', 'auto', 0.001, 0.01, 0.1, 1],
    'kernel': ['rbf', 'linear']
}

# Grid search com validação cruzada
svm_grid = SVC(random_state=42)
grid_search = GridSearchCV(svm_grid, param_grid, cv=5, scoring='accuracy', verbose=1)
grid_search.fit(X_train_scaled, y_train)

# Melhores parâmetros
print(f"Melhores parâmetros: {grid_search.best_params_}")
print(f"Melhor score CV: {grid_search.best_score_*100:.2f}%")

# Avaliar no conjunto de teste
best_svm = grid_search.best_estimator_
y_pred_best = best_svm.predict(X_test_scaled)
accuracy_best = accuracy_score(y_test, y_pred_best)
print(f"Acurácia no teste: {accuracy_best*100:.2f}%")

# Relatório detalhado
print(f"\nRelatório de Classificação:")
print(classification_report(y_test, y_pred_best))
```

    Fitting 5 folds for each of 48 candidates, totalling 240 fits
    Melhores parâmetros: {'C': 1, 'gamma': 1, 'kernel': 'rbf'}
    Melhor score CV: 80.61%
    Acurácia no teste: 79.33%
    
    Relatório de Classificação:
                  precision    recall  f1-score   support
    
               0       0.78      0.90      0.84       105
               1       0.82      0.64      0.72        74
    
        accuracy                           0.79       179
       macro avg       0.80      0.77      0.78       179
    weighted avg       0.80      0.79      0.79       179
    
    


```python
# =================================================
# 5. Interpretação dos Resultados

# Vamos analisar as predições para alguns casos específicos
# =================================================
from sklearn.metrics import confusion_matrix
import seaborn as sns

# Casos de teste específicos
test_cases = [
    [1, 1, 25],  # 1ª classe, feminino, 25 anos - deveria sobreviver
    [3, 0, 22],  # 3ª classe, masculino, 22 anos - provavelmente não sobrevive
    [2, 1, 35],  # 2ª classe, feminino, 35 anos - provavelmente sobrevive
    [3, 1, 5],   # 3ª classe, feminino, 5 anos - criança, provavelmente sobrevive
]

print("Predições para casos específicos:")
print("=" * 60)

for i, case in enumerate(test_cases):
    # Normalizar o caso de teste
    case_scaled = scaler.transform([case])
    
    # Fazer predição
    prediction = best_svm.predict(case_scaled)[0]
    confidence = best_svm.decision_function(case_scaled)[0]
    
    # Mapear características
    class_names = {1: "1ª classe", 2: "2ª classe", 3: "3ª classe"}
    sex_names = {0: "Masculino", 1: "Feminino"}
    result_names = {0: "Não Sobrevive", 1: "Sobrevive"}
    
    print(f"Caso {i+1}:")
    print(f"  Classe: {class_names[case[0]]}")
    print(f"  Sexo: {sex_names[case[1]]}")
    print(f"  Idade: {case[2]} anos")
    print(f"  Predição: {result_names[prediction]}")
    print(f"  Confiança: {abs(confidence):.3f}")
    print(f"  {'*' * 40}")

# Matriz de confusão
plt.figure(figsize=(8, 6))
cm = confusion_matrix(y_test, y_pred_best)
sns.heatmap(cm, annot=True, fmt='d', cmap='Blues', 
            xticklabels=['Não Sobrevive', 'Sobrevive'],
            yticklabels=['Não Sobrevive', 'Sobrevive'])
plt.title('Matriz de Confusão - SVM Otimizado')
plt.ylabel('Valor Real')
plt.xlabel('Predição')
plt.show()
```

    Predições para casos específicos:
    ============================================================
    Caso 1:
      Classe: 1ª classe
      Sexo: Feminino
      Idade: 25 anos
      Predição: Sobrevive
      Confiança: 1.007
      ****************************************
    Caso 2:
      Classe: 3ª classe
      Sexo: Masculino
      Idade: 22 anos
      Predição: Não Sobrevive
      Confiança: 1.000
      ****************************************
    Caso 3:
      Classe: 2ª classe
      Sexo: Feminino
      Idade: 35 anos
      Predição: Sobrevive
      Confiança: 1.003
      ****************************************
    Caso 4:
      Classe: 3ª classe
      Sexo: Feminino
      Idade: 5 anos
      Predição: Sobrevive
      Confiança: 0.084
      ****************************************
    


    
![png](case_ia_files/case_ia_277_1.png)
    


### Conclusões e Considerações

**Vantagens do SVM:**

1. **Eficaz em Espaços de Alta Dimensão**: Funciona bem mesmo quando o número de features é maior que o número de amostras

2. **Uso Eficiente de Memória**: Usa apenas os support vectors para fazer predições, não todos os dados de treinamento

3. **Versátil**: Diferentes kernels permitem capturar relacionamentos complexos entre as features

4. **Robusto a Overfitting**: Especialmente em espaços de alta dimensão

**Desvantagens do SVM:**

1. **Não Fornece Estimativas de Probabilidade**: Por padrão, SVM não calcula probabilidades (embora possa ser habilitado com `probability=True`)

2. **Sensível à Escala das Features**: Requer normalização dos dados

3. **Escolha do Kernel e Parâmetros**: Requer experimentação para encontrar os melhores hiperparâmetros

4. **Lento em Conjuntos Grandes**: Complexidade computacional pode ser alta para datasets muito grandes

**Aplicações Comuns do SVM:**

- Classificação de texto e análise de sentimento
- Classificação de imagens
- Reconhecimento de padrões bioinformáticos  
- Detecção de fraude
- Classificação de documentos

**Dicas Práticas:**

1. **Sempre normalize os dados** antes de usar SVM
2. **Comece com kernel RBF** para a maioria dos problemas
3. **Use Grid Search** para encontrar os melhores parâmetros
4. **Para datasets grandes**, considere usar `LinearSVC` ou `SGDClassifier`
5. **Para problemas multiclasse**, SVM usa estratégias como "one-vs-one" automaticamente

### 
--- 

### **Máquinas de Vetores de Suporte para Classificação (SVC)**

#### **Problemas linearmente separáveis e não linearmente separáveis**

Um problema é considerado **linearmente separável** quando existe uma linha, plano ou hiperplano que pode dividir as classes de dados de forma clara, sem sobreposição, no espaço de características. Nesse cenário, todas as instâncias de uma classe estão de um lado do limite de decisão, e as instâncias da outra classe estão do outro lado.

**Exemplo**: Imagine um conjunto de dados 2D onde um grupo de pontos (classe A) está no lado esquerdo de uma linha e outro grupo de pontos (classe B) está no lado direito. Nesse caso, o problema pode ser resolvido por um classificador linear.

Quando as classes de dados não podem ser separadas por uma linha ou plano no espaço original, o problema é **não linearmente separável**. Isso ocorre quando as classes estão dispostas de forma complexa, como em padrões curvos, agrupamentos sobrepostos ou em espirais.

**Exemplo**: Imagine dois conjuntos de pontos no plano 2D, onde um forma um círculo dentro do outro. Nenhuma linha reta pode separar essas classes.

#### **Classificadores de Máxima Margem**

Os classificadores de máxima margem são algoritmos de aprendizado de máquina usados para classificação, cujo objetivo é encontrar a melhor separação entre diferentes classes, garantindo a maior separação possível entre os pontos mais próximos de cada classe, pontos esses conhecidos como vetores de suporte.

Uma fraqueza dos classificadores de máxima margem é que eles são muito sensíveis a outliers. Um outlier pode alterar consideravelmente a margem de classificação, levando-o próximo de outra classe. Isso faz com que o modelo classifique incorretamente pontos que estão próximos à fronteira de separação, mesmo que esses pontos estejam, na prática, mais alinhados com a outra classe.

Em uma dimensão, o classificador é um ponto (um subespaço de dimensão 0, no jargão matemático).

Em duas dimensões, o classificador é uma reta(um subespaço de dimensão 1, no jargão matemático).

Em três dimensões, ele é um plano (um subespaço de dimensão 2, no jargão matemático).

Em quatro ou mais dimensões, o classificador se torna um hiperplano, (que é um subespaço de uma dimensão a menos que o espaço de entrada, no jargão matemático).

#### **Soft Margin**

O conceito de Soft Margin (margem suave) é uma abordagem utilizada para lidar com dados não perfeitamente separáveis. Ele permite que alguns pontos violem a margem ou até mesmo fiquem do lado "errado" do hiperplano de separação.

Perceba que o conceito de **soft margin** está intimamente conectado ao **Bias-variance tradeoff**.

De modo geral, uma soft margin é uma adaptação da margem máxima que aceita que alguns pontos caiam dentro da margem ou do lado incorreto do hiperplano. Isso equilibra o Bias-variance tradeoff, reduzindo o risco de overfitting.

Por fim, ao utilizar a soft margin, é comum que os outliers sejam acomodados dentro da margem ou até classificados incorretamente, dependendo de sua posição em relação ao hiperplano. Essa flexibilidade é intencional e visa priorizar a generalização do modelo em vez de uma separação perfeita nos dados de treinamento. Como resultado, os modelos com soft margin demonstram maior robustez frente a ruídos e valores discrepantes, mantendo bom desempenho mesmo em cenários com dados imperfeitos.

#### **O que é Support Vector Classification (SVC)?**

O SVC (Support Vector Classifier) é um algoritmo de aprendizado de máquina supervisionado baseado na Máquina de Vetores de Suporte (SVM - Support Vector Machine) para tarefas de classificação. Ele busca encontrar um hiperplano ótimo que separa os dados em diferentes classes com máxima margem. A margem é a distância entre o hiperplano de separação e os pontos mais próximos de cada classe, conhecidos como vetores de suporte, que são fundamentais para definir a posição e orientação do hiperplano.

O SVC é projetado para equilibrar a precisão na classificação dos dados de treinamento com a capacidade de generalização para novos dados, fundamentando-se em dois conceitos principais: a margem máxima e a soft margin. Embora seja classificado como um classificador de máxima margem, ele apresenta adaptações que o tornam mais robusto para lidar com dados reais.

Em situações ideais, onde os dados são linearmente separáveis e livres de ruído ou outliers, o SVC funciona como um classificador de máxima margem tradicional. Nesse contexto, o modelo busca um hiperplano que separa perfeitamente as classes, garantindo que nenhum ponto caia dentro da margem ou do lado errado do hiperplano.

No entanto, em cenários reais, os dados frequentemente apresentam outliers ou ruído, e as classes podem não ser perfeitamente separáveis. Para lidar com essas limitações, o SVC incorpora o conceito de soft margin, permitindo certa flexibilidade na definição da margem. Essa abordagem tolera erros, como pontos que ficam dentro da margem (entre o hiperplano e os vetores de suporte) ou que são classificados incorretamente.

A imagem abaixo deixa mais claro uma situação hipotética do processo de separação de classes de um SVC:
<p align=center>
<img src="https://www.iunera.com/wp-content/uploads/image-16-1024x756.png?v=1596602837" width=600 height=400></img> </p>

#### **Funções kernel (linear, polinomial, radial)**

##### **Support Vector Machines e o Kernel Trick**

O maior avanço das SVMs sobre os classificadores tradicionais é o uso do **kernel trick**. Quando os dados não são linearmente separáveis no espaço original, os SVMs podem usar uma técnica chamada kernel trick para mapear os dados para um espaço de maior dimensão onde eles podem ser separáveis de forma linear. Além dessa ideia brilhante, o kernel trick possui uma outra sacada muito inteligente: Em vez de calcular diretamente as coordenadas no novo espaço, o kernel calcula o **produto interno** entre os pontos de dados mapeados, sem a necessidade de realizar a transformação explícita. Isso torna o processo mais eficiente e permite a criação de fronteiras de decisão não lineares.

O conceito central é que muitos algoritmos de aprendizado de máquina, incluindo as SVMs, dependem do cálculo de distâncias ou relações geométricas entre pontos de dados. Para isso, o produto interno entre dois vetores é frequentemente utilizado. Esse produto interno nos dá uma medida de similaridade entre os vetores, o que é crucial para definir a posição relativa dos pontos em relação ao hiperplano de separação.

O truque do kernel resolve esse problema de forma elegante: ele utiliza uma **função kernel** que calcula diretamente o produto interno dos dados como se estivessem no espaço de dimensão superior, sem jamais realizar a transformação explícita. Em outras palavras, o kernel fornece o valor que seria obtido após o mapeamento, mas sem a necessidade de realmente mapear os dados.

##### **O que são funções Kernel?**

As funções kernel são técnicas utilizadas em Máquinas de Vetores de Suporte (SVM) e outros modelos de aprendizado de máquina para transformar dados não linearmente separáveis em um espaço de maior dimensão onde possam ser linearmente separados.

Elas permitem que o classificador SVM trabalhe com separações não lineares, sem precisar explicitamente mapear os dados para um espaço de alta dimensão.

Em vez de calcular diretamente as coordenadas dos dados em um espaço de maior dimensão, o kernel calcula o produto interno entre os pontos transformados, o que simula como se os dados estivessem em uma dimensão superior. O kernel “faz isso” através de uma função matemática que, ao ser aplicada nos pontos, é capaz de calcular o produto interno correspondente ao espaço de maior dimensão sem precisar realmente fazer essa transformação.

**Os principais tipos de kernels são**:

**Kernel Linear**: Quando os dados já são linearmente separaveis:

$$K(x, x') = x \cdot x'$$

**Kernel polinomial**: Quando há relações polinomiais entre classes

$$K(x, x') = (x \cdot x' + c)^d$$

**Kernel RBF(Radial Basis Function)**: 	Quando os dados não seguem um padrão linear

$$K(x, x') = \exp(-\gamma ||x - x'||^2)$$

Em muitos casos, o kernel RBF (Gaussiano) é o mais usado, pois funciona bem para uma ampla variedade de problemas.


```python
# Importa o modelo Suporte Vector Machine Classifier
from sklearn.svm import SVC

# Instancia o modelo Suporte Vector Machine Classifier
svm_classifier = SVC()

# Treina o modelo Suporte Vector Machine Classifier com os dados de treino
svm_classifier.fit(X_train, y_train)

# Faz previsões com os dados de teste
y_pred_svm_classifier = svm_classifier.predict(X_test)
# Calcula a acurácia
accuracy_svm_classifier = accuracy_score(y_test, y_pred_svm_classifier)
print(f'Acurácia do modelo Suporte Vector Machine Classifier: {accuracy_svm_classifier:.5f}')
```

    Acurácia do modelo Suporte Vector Machine Classifier: 0.80556
    

### **O que é Support Vector Regression (SVR)?**

O Support Vector Regression (SVR) é um algoritmo de regressão que usa os princípios das Máquinas de Vetores de Suporte (SVM) para prever valores contínuos.

#### **Intuição:**

Você viu que quando estamos falando de regressão linear, a ideia basica é que o algoritmo busca encontrar uma linha que melhor se adeque ao conjunto de dados. Falando de forma mais matemática, ele busca traçar a linha que minimize a soma da distância ao quadrado entre os pontos e a reta traçada.

Imagine agora, que, em vez de tentar encontrar uma linha que passe o mais próximo possível de todos os pontos de dados (como na regressão linear simples, que minimiza a soma dos erros quadrados), o SVR tenta ajustar um tubo que contenha a maior quantidade possível de pontos de dados.

A largura do tubo ($\epsilon$-insensivel): Este tubo tem uma certa largura, definida pelo parâmetro $\epsilon$. O SVR "não se importa" com os erros dos pontos que estão dentro da largura desse tubo. Ou seja, se a previsão estiver dentro de uma margem ϵ do valor real, o erro é considerado zero. Essa é a chamada zona $\epsilon$-insensível.

Dessa forma,  O SVR se concentra principalmente nos pontos que estão nas bordas ou fora desse tubo. Esses pontos são os "vetores de suporte" (Support Vectors) que, assim como no SVM para classificação, definem a "fronteira" da função de regressão.

Ao mesmo tempo que tenta manter os pontos dentro do tubo, o SVR também tenta encontrar a função mais "plana" possível. Uma função mais plana significa que o modelo é menos complexo e, teoricamente, generaliza melhor para novos dados. "Planicidade" está relacionada a minimizar a magnitude dos coeficientes da função.

Em resumo: O SVR tenta encontrar uma função que se ajuste aos dados, permitindo uma margem de erro ($\epsilon$) onde os erros não são penalizados. Ele penaliza apenas os pontos que caem fora dessa margem, e a forma como essa penalização é feita (e o quão "plana" a função deve ser) é controlada por outros parâmetros.

O gráfico abaixo ajuda a entender o funcionamento do "tubo":
<p align=center>
<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ2HJHPPDD2uk7QTOsWa_s7xBg4L78o-vt5Bw&s" width=500 height=300></img> </p>

Como mencionado, o SVR introduz uma margem de tolerância $\epsilon$. Para um ponto de dado $(x_i,y_i)$, se a função de previsão é $f(x_i)$, o erro só é considerado se a diferença entre o valor real $y_i$ e o valor previsto $f(x_i)$ for maior que $\epsilon$:

- $Se |y_i - f(x_i)| <= \epsilon$, o erro é 0
- $Se |y_i - f(x_i)| > \epsilon$, o erro é $|y_i - f(x_i)| - \epsilon$


A função objetivo que o SVR busca minimizar é:
$$
\min_{w, b, \xi, \xi^*} \frac{1}{2} \|w\|^2 + C \sum_{i=1}^{N} (\xi_i + \xi_i^*)
$$
Sujeito as seguintes restrições:
- $y_i - (\langle w, x_i \rangle + b) \leq \epsilon + \xi_i$
- $(\langle w, x_i \rangle + b) - y_i \leq \epsilon + \xi_i^*$
- $\xi_i, \xi_i^* \geq 0$

Onde:
- $\frac{1}{2} \|w\|^2$ Termo de regularização. Tenta manter os pesos $w$ pequenos, levando a uma função mais suave e menos propensa a overfitting.
- $C$: Parâmetro de regularização (ou custo). É um valor positivo que controla o trade-off entre:
    - A "planicidade" da função
    - A quantidade de erros maiores que $\epsilon$ que o modelo tolera.
    - Um C alto penaliza mais os erros, levando a um ajuste mais preciso aos dados de treino (podendo causar overfitting), tentando colocar mais pontos dentro ou próximos do tubo $\epsilon$
    - Um C baixo permite mais erros (uma rua "mais larga" no sentido de tolerância a pontos fora dela), resultando em uma função mais plana, mas podendo levar a underfitting se for baixo demais.
- $\sum_{i=1}^{N} (\xi_i + \xi_i^*)$: Soma das magnitudes dos erros que excedem a margem $\epsilon$.


**Vetores de Suporte (Support Vectors)**

São os pontos de dados que:
- Estão exatamente nas bordas da zona $\epsilon$-insensível (Onde $|y_i - f(x_i)| = 0$)
- Estão fora da zona $\epsilon$-insensível (onde $|y_i - f(x_i)| > \epsilon$ e, portanto, $\xi_i > 0$ ou $\xi_i^* > 0$)

Os pontos que estão dentro da zona $\epsilon$-insensível (com erro zero) não influenciam diretamente a definição da função de regressão final. Apenas os vetores de suporte são cruciais para definir o tubo.

**Funções Kernel**

Assim como no SVM para classificação, o SVR pode usar o "truque do kernel" para modelar relações não lineares. A ideia é mapear os dados de entrada para um espaço de características de dimensão maior, onde uma relação linear pode ser encontrada.

Em vez de realizar explicitamente esse mapeamento (que pode ser computacionalmente caro), as funções de kernel calculam o produto escalar dos vetores nesse espaço de alta dimensão diretamente a partir dos vetores originais.

Kernels comuns incluem:
- Linear
- Polinomial
- Guassiano
- Sigmoide


**Vantagens**
- Eficaz em espaços de alta dimensionalidade: Funciona bem mesmo quando o número de características é grande.
- Eficiente em termos de memória: Utiliza um subconjunto dos pontos de treinamento na função de decisão (os vetores de suporte).
- Diferentes funções de kernel podem ser especificadas, permitindo grande flexibilidade na modelagem de diversos tipos de dados.
- Robustez a outliers (devido à zona ϵ-insensível): Pequenos ruídos dentro da margem ϵ não afetam o modelo.
- Boa capacidade de generalização: O princípio de minimização do risco estrutural (que busca minimizar um limite superior do erro de generalização) e a regularização ajudam a evitar overfitting.

**Desvantagens**
- Sensibilidade a hiperparâmetros: O desempenho do SVR pode ser bastante sensível à escolha do parâmetro C, do parâmetro ϵ e dos parâmetros do kernel. Requer um bom ajuste (tuning) desses hiperparâmetros, geralmente via busca em grade (grid search) e validação cruzada.
- Interpretabilidade: Pode ser menos interpretável que modelos como regressão linear
- Custo computacional: O treinamento pode ser lento em conjuntos de dados muito grandes, especialmente com kernels complexos.
- Escolha do kernel: Não há uma regra de ouro para escolher o melhor kernel para um determinado problema.


## **3.5 Árvores de Decisão para Classificação**

Fonte: https://www.datacamp.com/pt/tutorial/decision-tree-classification-python

https://medium.com/data-science/decision-tree-classifier-explained-a-visual-guide-with-code-examples-for-beginners-7c863f06a71e

https://blog.somostera.com/data-science/arvores-de-decisao

Honestamente, depois que cheguei até aqui, acho que deveria ter começado por ele, não por sua complexidade, mas por quão facil é entendê-lo e como ele pode ajudar a intuir os outros, então se fosse para reorganizar a **Árvore de Decisão**, seria, sem dúvida, a primeira da lista. Antes de nos perdermos em probabilidades, margens geométricas ou funções logísticas, a árvore de decisões é muito mais familiar

**Um fluxograma de perguntas e respostas**, o único modelo que pensa de forma fundamentalmente humana. É um modelo "caixa branca", onde cada decisão é explicito e pode ser explicado de maneira simples

Vamos ver como ela funciona, nosso contexto agora é decidir se um banco deve ou não aprovar um pedido de crédito.

Imagine um gerente de crédito experiente, Sr. Roberto. Ele precisa treinar um novo analista, mas sua própria experiência é baseada em anos de intuição. Para tornar o processo claro e replicável, ele precisa mapear seu raciocínio em uma série de perguntas.

**Passo 1: A pergunta mais importante (O Nó Raiz)**

Sr. Roberto pensa: "Qual é a primeira pergunta que eu posso fazer para separar os bons dos maus pagadores?". Ele percebe que a informação mais impactante é se o cliente possui uma fonte de renda. 

Essa se torna a primeira pergunta no topo do seu fluxograma. É a raiz da sua árvore.

- Pergunta: *O cliente tem uma fonte de renda?*
    - **Sim**: O cliente para para o próximo estágio da análise
    - **Não**: Risco alto. A decisão deve ser: **NEGAR**

**Passo 2: Criando os ramos (Nós Internos)**

Agora, para o grupo que respondeu "Sim', o Sr. Roberto precisa de uma segunda pergunta, Ele não vai usar a mesma lógica para todos; ele está focando em um grpo mais promissor. Talvez, pessoas com menos dívidas:

- Pergunta (para quem tem renda): *O nível de dívida atual é alto*
    - **Sim**: Esse grupo é arriscado. Precisamos decidir.
    - **Não**: Este grupo é de baixo risco. A chance de aprovar deve ser mais alta.

**Passo 3: Chegando às folhas (Decisão)**

O fluxograma continua se ramificando.

- Para o grupo com renda estável e dívida baixa, a decisão é simples: **APROVAR**

- Para o grupo com renda estável mas dívida alta, o Sr Roberto decide mais uma pergunta para desempatar, como: "O cliente possui um imóvel como garantia?".
    - **Sim**: O risco é mitigado pela garantia. A decisão é **APROVAR**. Outra folha

    - **Não**: Renda estável, mas alta dívida e sem garantia? a decisão parece ser **NEGAR**. (Outra folha)

**O fluxograma final:**

No final, o Sr. Roberto criou um fluxograma, um guia passo a passo que qualquer um pode seguir.

Quando um novo pedido de crédito chega, qualquer pessoa com esse roteiro chega na decisão final e justificada





### Intuição 

Imagine que você é o Sr. Roberto e precisa decidir se aprova ou não um pedido de crédito. Você tem as informações do cliente:

- Renda anual: $50.000
- Dívida Atual: $10.000
- Histórico de Crédito: Bom
- Empregado: Sim
- Garantia: Sim

Pergunta: Aprovar (+) ou Rejeitar (-) o crédito?

Como vimos a anatomia de uma árvore:

- Root Node:
    - Primeiro nó no topo
    - Representa a feature mais importante
    - De onde todas as decisões começam

- Internal Nodes:
    - Fazem testes/perguntas sobre features
    - Têm pelo menos 2 ramos saindo
    - Cada ramo representa uma resposta possível

- Branches:
    - Conectam os nós
    - Representam as respostas possíveis (Sim/Não, valores)

- Leaf Nodes:
    - Nós finais, sem ramos saindo
    - Contêm a decisão final
    - Exemplo: "Aprovar", "Rejeitar"

- Depth:
    - Número de níves da árvore
    - Quanto mais profunta mais complexa é a árvore

O algoritmo usa uma estratégia greedy (Guloso), ela é construida assim:

1. Escolhe a 'melhor' feature para dividr os dados
"melhor" = aquela que mais reduz impureza

2. Divide os dados baseado nessa feature

3. Repete recursivamente para cada subconjunto

4. Para:
    - quando todos os exemplos são da mesma classe (puro)
    - Não há mais features para dividir
    - Atinge profundidade máxima
    - Conjunto se torna muito pequeno (min_samples_split)

- IMPUREZA: Mede o quão misturadas estão as classes
    - Impureza = 0: Todos na mesma classe (puro)

**Medindo a impureza:"**

- Gini impurity

$Gini = 1 - \sum(P_i)^2$

eg: 
- [50 aprovados, 50 rejeitados]
    - $Gini = 1 - (0.5^2 + 0.5^2) = 0.5$ (Máxima impureza para 2 classes)

- [90 aprovados, 10 rejeitados]
- $Gini = 1- (0.9^2 + 0.1^2) = 0.18$

- Shannon Entropy

$Entropy = -\sum P_i\log_2(P_i)$

e.g. 
- [50 aprovados, 50 rejeitados]
    - $-(0.5\times\log(0.5) + 0.5\times\log(0.5)) = 1$ (máximo)

- Information Gain

$Gain = Impureza(antes) - Impureza(depois da divisão)

- Quanto a divisão reduziu da impureza

**Vamos visualizar**!


```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from matplotlib.patches import Rectangle, FancyBboxPatch
```


```python
# Dessa vez, vamos gerar os dados para interpretarmos
np.random.seed(42)
n_samples = 100

age = np.random.randint(18, 70, n_samples)
income = np.random.randint(20000, 120000, n_samples)
debt = np.random.randint(0, 50000, n_samples)
employed = np.random.choice([0, 1], n_samples, p=[0.7, 0.3])  # 0: No, 1: Yes
credit_score = np.random.choice(['Good', 'Fair', 'Poor'], n_samples, p=[0.4, 0.4, 0.2])

approved = []
for i in range(n_samples):
    score = 0

    if income[i] > 60000:
        score += 3
    if income[i] > 40000:
        score += 2
    else:
        score += 1

    if debt[i] < 15000:
        score += 3
    elif debt[i] < 30000:
        score += 1

    if employed[i] == 1:
        score += 2
        
    if credit_score[i] == 'Good':
        score += 3
    elif credit_score[i] == 'Fair':
        score += 1
  
    approved.append(1 if score >= 6 else 0)

df = pd.DataFrame({
    'Age': age,
    'Income': income,
    'Debt': debt,
    'Employed': employed,
    'Credit_Score': credit_score,
    'Approved': approved
})

print("Total de registros:", len(df))
print(f"\nDistribuição das decisões:")
print(df['Approved'].value_counts(normalize=True))

```

    Total de registros: 100
    
    Distribuição das decisões:
    Approved
    1    0.71
    0    0.29
    Name: proportion, dtype: float64
    


```python
# Calcular Gini Impurity
def gini_impurity(y):
    if len(y) == 0:
        return 0
    proportions = np.bincount(y) / len(y)
    return 1 - np.sum(proportions ** 2)

def entropy(y):
    if len(y) == 0:
        return 0
    proportions = np.bincount(y) / len(y)
    proportions = proportions[proportions > 0]
    return -np.sum(proportions * np.log2(proportions))

gini_initial = gini_impurity(df['Approved'])
entropy_initial = entropy(df['Approved'])
print(f"Gini Impurity (Initial): {gini_initial}")
print(f"Entropy (Initial): {entropy_initial}")
print(f"\nTemos {np.sum(df['Approved'])} aprovações e {len(df) - np.sum(df['Approved'])} rejeições.")
```

    Gini Impurity (Initial): 0.41180000000000005
    Entropy (Initial): 0.8687212463394045
    
    Temos 71 aprovações e 29 rejeições.
    


```python
y = df['Approved'].values
threshold_income = 60000
high_income_mask = df['Income'] > threshold_income
low_income_mask = ~high_income_mask

# Grupo: Income > 60000
high_income_approved = y[high_income_mask]
gini_high = gini_impurity(high_income_approved)
print(f"\nGrupo 1 (Income > ${threshold_income:,}):")
print(f"   Total: {len(high_income_approved)} pessoas")
print(f"   Aprovados: {np.sum(high_income_approved)} ({np.mean(high_income_approved)*100:.1f}%)")
print(f"   Gini: {gini_high:.4f}")

# Grupo: Income <= 60000
low_income_approved = y[low_income_mask]
gini_low = gini_impurity(low_income_approved)
print(f"\nGrupo 2 (Income <= ${threshold_income:,}):")
print(f"   Total: {len(low_income_approved)} pessoas")
print(f"   Aprovados: {np.sum(low_income_approved)} ({np.mean(low_income_approved)*100:.1f}%)")
print(f"   Gini: {gini_low:.4f}")

# Calcular Gini após a divisão
gini_after_split = (len(high_income_approved) / len(y)) * gini_high + (len(low_income_approved) / len(y)) * gini_low
print(f"\nGini após a divisão: {gini_after_split:.4f}")
print(f"\nGanho: {gini_initial - gini_after_split:.4f}")
```

    
    Grupo 1 (Income > $60,000):
       Total: 60 pessoas
       Aprovados: 57 (95.0%)
       Gini: 0.0950
    
    Grupo 2 (Income <= $60,000):
       Total: 40 pessoas
       Aprovados: 14 (35.0%)
       Gini: 0.4550
    
    Gini após a divisão: 0.2390
    
    Ganho: 0.1728
    


```python
# Desenho da árvore de decisão

def draw_node(ax, x, y, text, width=2, height=0.6, color='lightblue'):
    box = FancyBboxPatch((x-width/2, y-height/2), width, height,
                         boxstyle="round,pad=0.1", 
                         edgecolor='black', facecolor=color, linewidth=2)
    ax.add_patch(box)
    ax.text(x, y, text, ha='center', va='center', fontsize=10, 
           fontweight='bold', wrap=True)

def draw_arrow(ax, x1, y1, x2, y2, label=''):
    ax.annotate('', xy=(x2, y2), xytext=(x1, y1),
               arrowprops=dict(arrowstyle='->', lw=2, color='black'))
    if label:
        mid_x, mid_y = (x1+x2)/2, (y1+y2)/2
        ax.text(mid_x, mid_y, label, ha='center', fontsize=9,
               bbox=dict(boxstyle='round', facecolor='white', alpha=0.8))


fig, ax = plt.subplots(figsize=(12, 8))
# Root Node
draw_node(ax, 7, 7, 'Income > $60k?', color='#fff3cd')

# Ramo esquerdo (Sim)
draw_arrow(ax, 6.5, 6.7, 4, 5.3, 'Sim')
draw_node(ax, 4, 5, 'Employed = Yes?', color='#d4edda')

# Sub-ramos esquerda
draw_arrow(ax, 3.5, 4.7, 2.5, 3.3, 'Sim')
draw_node(ax, 2.5, 3, 'APROVADO', width=1.8, color='#28a745')

draw_arrow(ax, 4.5, 4.7, 5.5, 3.3, 'Não')
draw_node(ax, 5.5, 3, 'Debt > $20k', color='#fff3cd')

draw_arrow(ax, 5.2, 2.7, 4.5, 1.3, 'Sim')
draw_node(ax, 4.5, 1, 'REJEITADO', width=1.8, color='#dc3545')

draw_arrow(ax, 5.8, 2.7, 6.5, 1.3, 'Não')
draw_node(ax, 6.5, 1, 'APROVADO', width=1.8, color='#28a745')

# Ramo direito (Não)
draw_arrow(ax, 7.5, 6.7, 10, 5.3, 'Não')
draw_node(ax, 10, 5, 'CreditScore = Good?\n(Gini=0.44)', color='#f8d7da')

draw_arrow(ax, 9.5, 4.7, 8.5, 3.3, 'Sim')
draw_node(ax, 8.5, 3, 'APROVADO', width=1.8, color='#28a745')

draw_arrow(ax, 10.5, 4.7, 11.5, 3.3, 'Não')
draw_node(ax, 11.5, 3, 'REJEITADO', width=1.8, color='#dc3545')

ax.set_xlim(0, 14)
ax.set_ylim(0, 8)
ax.axis('off')
ax.set_title('Árvore de Decisão - Credit Approval', 
            fontsize=14, fontweight='bold', pad=20)


plt.tight_layout()
plt.show()
```


    
![png](case_ia_files/case_ia_304_0.png)
    


### Formulação Formal

**Entrada**

1. Conjunto de treinamento de n amostras em pares $D=\{(x^{(1)}, y^{(1)}), (x^{(2)}, y^{(2)}), ..., (x^{(n)}, y^{(n)})\}$

    onde:

    - $x^{(i)}$: vetor de d features ($x^{(i)} = (x^{(i)}_1, x^{(i)}_2, ..., x^{(i)}_d)$), portanto $x^{(i)} \in \mathbb{R}^d$

    - $y^{(i)}$: rótulo de classe, $y^{(i)} \in C = \{c_1, c_2, ..., c_k\}$ para classificação

**Processamento**

O algoritmo de árvore de decisão funciona recursivamente dividindo o espaço de características.

**1. Critérios de Impureza**

**Entropia**: Para um conjunto $S$ com $k$ classes:

$H(S) = -\sum_{i=1}^{k} p_i \log_2(p_i)$

onde $p_i$ é a proporção de amostras da classe $i$ em $S$.

**Gini Impurity**: 

$Gini(S) = 1 - \sum_{i=1}^{k} p_i^2$

**2. Information Gain**

Para uma feature $A$ que divide $S$ em subconjuntos $S_1, S_2, ..., S_m$:

$IG(S, A) = H(S) - \sum_{j=1}^{m} \frac{|S_j|}{|S|} H(S_j)$

**3. Algoritmo de Construção**

``` code
função BuildTree(S, Features):
    se S é puro (todas as amostras têm a mesma classe):
        retorna folha com essa classe
    
    se Features é vazio:
        retorna folha com classe majoritária em S
    
    seleciona feature A que maximiza Information Gain
    cria nó com teste em A
    
    para cada valor v de A:
        S_v = subconjunto de S onde A = v
        se S_v é vazio:
            adiciona folha com classe majoritária em S
        senão:
            adiciona subárvore BuildTree(S_v, Features - {A})
```

**4. Critérios de Parada**

- Profundidade máxima atingida
- Número mínimo de amostras por folha
- Information Gain mínimo
- Nó puro (todas amostras da mesma classe)

**Saída - Classificação**

- **Estrutura da Árvore**: Conjunto de nós internos (testes) e folhas (predições)

- **Predição**: Para uma nova amostra $x^{new}$:
  1. Começar na raiz
  2. Aplicar o teste do nó atual em $x^{new}$
  3. Seguir o ramo correspondente ao resultado
  4. Repetir até chegar a uma folha
  5. Retornar a classe da folha

- **Probabilidades**: Para probabilidades de classe, usar a distribuição das classes na folha

**Poda (Pruning)**

Para evitar overfitting, aplicamos poda:

**Pré-poda**: Parar o crescimento da árvore antecipadamente
- Profundidade máxima
- Número mínimo de amostras por nó
- Information gain mínimo

**Pós-poda**: Remover partes da árvore após construção
- Cost complexity pruning (usado no sklearn)
- Validação cruzada para escolher melhor complexidade

### Desafio: "From Scratch"

Vamos implementar uma versão simplificada do algoritmo de Árvore de Decisão do zero


```python
import numpy as np
from collections import Counter

class SimpleDecisionTree:
    def __init__(self, max_depth=5, min_samples_split=2, criterion='gini'):
        """
        Implementação simplificada de uma Árvore de Decisão.
        
        Parâmetros:
        -----------
        max_depth: int
            Profundidade máxima da árvore.
        min_samples_split: int
            Número mínimo de amostras necessárias para dividir um nó.
        criterion: str
            Critério para medir a qualidade da divisão ('gini' ou 'entropy').
        """
        pass

    def _calculate_gini(self, y):
        """
        Calcula o índice de Gini para um conjunto de labels.
        
        Parâmetros:
        -----------
        y: array-like
            Labels das classes.
            
        Retorna:
        --------
        float
            Índice de Gini.
        """
        pass

    def _calculate_entropy(self, y):
        """
        Calcula a entropia para um conjunto de labels.
        
        Parâmetros:
        -----------
        y: array-like
            Labels das classes.
            
        Retorna:
        --------
        float
            Entropia.
        """
        pass

    def _calculate_impurity(self, y):
        """
        Calcula a impureza baseada no critério escolhido.
        """
        pass

    def _best_split(self, X, y):
        """
        Encontra a melhor divisão para os dados.
        
        Parâmetros:
        -----------
        X: np.ndarray
            Matriz de características.
        y: np.ndarray
            Labels das classes.
            
        Retorna:
        --------
        dict
            Dicionário com informações da melhor divisão.
        """
        pass

    def _split_data(self, X, y, feature_index, threshold):
        """
        Divide os dados baseado em uma característica e threshold.
        
        Parâmetros:
        -----------
        X: np.ndarray
            Matriz de características.
        y: np.ndarray
            Labels das classes.
        feature_index: int
            Índice da característica para divisão.
        threshold: float
            Valor threshold para divisão.
            
        Retorna:
        --------
        tuple
            Dados divididos (X_left, X_right, y_left, y_right).
        """
        pass

    def _build_tree(self, X, y, depth=0):
        """
        Constrói a árvore recursivamente.
        
        Parâmetros:
        -----------
        X: np.ndarray
            Matriz de características.
        y: np.ndarray
            Labels das classes.
        depth: int
            Profundidade atual.
            
        Retorna:
        --------
        dict
            Nó da árvore.
        """
        pass

    def fit(self, X, y):
        """
        Treina a árvore de decisão.
        
        Parâmetros:
        -----------
        X: np.ndarray
            Matriz de características.
        y: np.ndarray
            Labels das classes.
        """
        pass

    def _predict_sample(self, sample, node):
        """
        Faz predição para uma única amostra.
        
        Parâmetros:
        -----------
        sample: np.ndarray
            Amostra para predição.
        node: dict
            Nó atual da árvore.
            
        Retorna:
        --------
        class
            Classe predita.
        """
        pass

    def predict(self, X):
        """
        Faz predições para um conjunto de dados.
        
        Parâmetros:
        -----------
        X: np.ndarray
            Matriz de características.
            
        Retorna:
        --------
        np.ndarray
            Predições.
        """
        pass

    def score(self, X, y):
        """
        Calcula a acurácia do modelo.
        
        Parâmetros:
        -----------
        X: np.ndarray
            Matriz de características.
        y: np.ndarray
            Labels verdadeiros.
            
        Retorna:
        --------
        float
            Acurácia do modelo.
        """
        pass
```


```python
# Dados para Teste - Credit Approval Dataset
# ==================================================
from ucimlrepo import fetch_ucirepo 
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import LabelEncoder
import pandas as pd

# Fetch dataset
credit_approval = fetch_ucirepo(id=27) 

# Data (as pandas dataframes) 
X = credit_approval.data.features 
y = credit_approval.data.targets

# Simplificar dataset para fins didáticos
# Selecionar algumas features importantes e tratar valores ausentes
X_simple = X[['A2', 'A3', 'A8', 'A11', 'A14', 'A15']].copy()
X_simple.columns = ['Age', 'Years_Employed', 'Debt_to_Income', 'Credit_Score', 'Income', 'Debt']

# Tratar valores ausentes - substituir por mediana para numéricos
for col in X_simple.columns:
    if X_simple[col].dtype in ['float64', 'int64']:
        X_simple[col] = pd.to_numeric(X_simple[col], errors='coerce')
        X_simple[col] = X_simple[col].fillna(X_simple[col].median())

# Remover amostras com muitos valores ausentes
X_simple = X_simple.dropna()
y_simple = y.loc[X_simple.index]

# Converter target para binário (aprovado/negado)
le = LabelEncoder()
y_binary = le.fit_transform(y_simple.values.ravel())

print(f"Dataset shape: {X_simple.shape}")
print(f"Classes: {le.classes_}")
print(f"Distribuição das classes: {np.bincount(y_binary)}")

# Dividir em treino e teste
X_train, X_test, y_train, y_test = train_test_split(
    X_simple.values, y_binary, test_size=0.2, random_state=42
)
```

    Dataset shape: (690, 6)
    Classes: ['+' '-']
    Distribuição das classes: [307 383]
    

### Usando SKlearn


```python
# Carregando os dados (novamente)
# ==================================================
from ucimlrepo import fetch_ucirepo 
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import LabelEncoder
import pandas as pd

# Fetch dataset
credit_approval = fetch_ucirepo(id=27) 

# Data (as pandas dataframes) 
X = credit_approval.data.features 
y = credit_approval.data.targets

# Simplificar dataset para fins didáticos
X_simple = X[['A2', 'A3', 'A8', 'A11', 'A14', 'A15']].copy()
X_simple.columns = ['Age', 'Years_Employed', 'Debt_to_Income', 'Credit_Score', 'Income', 'Debt']

# Tratar valores ausentes
for col in X_simple.columns:
    if X_simple[col].dtype in ['float64', 'int64']:
        X_simple[col] = pd.to_numeric(X_simple[col], errors='coerce')
        X_simple[col] = X_simple[col].fillna(X_simple[col].median())

X_simple = X_simple.dropna()
y_simple = y.loc[X_simple.index]

# Converter target para binário
le = LabelEncoder()
y_binary = le.fit_transform(y_simple.values.ravel())

print(f"Dataset shape: {X_simple.shape}")
print(f"Classes: {le.classes_}")
print(f"Taxa de aprovação: {np.mean(y_binary)*100:.2f}%")

X_train, X_test, y_train, y_test = train_test_split(
    X_simple.values, y_binary, test_size=0.2, random_state=42
)
```

    Dataset shape: (690, 6)
    Classes: ['+' '-']
    Taxa de aprovação: 55.51%
    


```python
# =================================================
# Bibliotecas
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.tree import DecisionTreeClassifier, export_text, plot_tree
from sklearn.metrics import accuracy_score, classification_report, confusion_matrix
import matplotlib.pyplot as plt
import seaborn as sns

```


```python
# ===================================================
# 1. Implementação Básica

tree = DecisionTreeClassifier(random_state=42)
tree.fit(X_train, y_train)
predictions = tree.predict(X_test)

accuracy = accuracy_score(y_test, predictions)
print(f"Acurácia: {accuracy*100:.2f}%")

```

    Acurácia: 67.39%
    


```python
# =================================================
# 2. Visualização do Modelo

tree_small = DecisionTreeClassifier(max_depth=3, random_state=42) #melhorar visualização
tree_small.fit(X_train, y_train)

print("\nRegras da Árvore de Decisão:")
rules = export_text(tree_small, feature_names=list(X_simple.columns))
print(rules)
```

    
    Regras da Árvore de Decisão:
    |--- Credit_Score <= 2.50
    |   |--- Debt_to_Income <= 1.21
    |   |   |--- Debt <= 5500.00
    |   |   |   |--- class: 1
    |   |   |--- Debt >  5500.00
    |   |   |   |--- class: 0
    |   |--- Debt_to_Income >  1.21
    |   |   |--- Debt <= 186.50
    |   |   |   |--- class: 1
    |   |   |--- Debt >  186.50
    |   |   |   |--- class: 0
    |--- Credit_Score >  2.50
    |   |--- Years_Employed <= 1.42
    |   |   |--- Income <= 257.00
    |   |   |   |--- class: 1
    |   |   |--- Income >  257.00
    |   |   |   |--- class: 0
    |   |--- Years_Employed >  1.42
    |   |   |--- Debt_to_Income <= 0.06
    |   |   |   |--- class: 0
    |   |   |--- Debt_to_Income >  0.06
    |   |   |   |--- class: 0
    
    


```python
# =================================================
# 3. Parâmetros Importantes da Árvore de Decisão

# criterion (default='gini')
# - 'gini': Gini impurity
# - 'entropy': Information gain
# - 'log_loss': Log loss

# max_depth (default=None)
# - Profundidade máxima da árvore
# - None = sem limite (pode causar overfitting)

# min_samples_split (default=2)
# - Número mínimo de amostras necessárias para dividir um nó interno

# min_samples_leaf (default=1)
# - Número mínimo de amostras necessárias em uma folha

# max_features (default=None)
# - Número de features a considerar ao procurar a melhor divisão
# - None: usa todas as features

# ccp_alpha (default=0.0)
# - Parâmetro de complexidade para poda de custo mínimo
# =================================================

# Testar diferentes critérios
criteria = ['gini', 'entropy']
results = []

for criterion in criteria:
    dt = DecisionTreeClassifier(criterion=criterion, random_state=42)
    dt.fit(X_train, y_train)
    accuracy = dt.score(X_test, y_test)
    depth = dt.get_depth()
    leaves = dt.get_n_leaves()
    
    results.append((criterion, accuracy, depth, leaves))
    print(f"Critério {criterion:8}: Acurácia = {accuracy*100:5.2f}%, Profundidade = {depth:2d}, Folhas = {leaves:3d}")

# Testar diferentes profundidades máximas
max_depths = [3, 5, 7, 10, None]
print(f"\nTestando diferentes profundidades máximas:")

for max_depth in max_depths:
    dt = DecisionTreeClassifier(max_depth=max_depth, random_state=42)
    dt.fit(X_train, y_train)
    train_acc = dt.score(X_train, y_train)
    test_acc = dt.score(X_test, y_test)
    depth = dt.get_depth()
    leaves = dt.get_n_leaves()
    
    max_depth_str = str(max_depth) if max_depth else "None"
    print(f"Max_depth = {max_depth_str:4}: Train = {train_acc*100:5.2f}%, Test = {test_acc*100:5.2f}%, "
          f"Profundidade Real = {depth:2d}, Folhas = {leaves:3d}")

print(f"""\nNotas: 
      \n - como profundidades menores podem ter melhor generalização (menor overfitting)
      \n - Note como a árvore sem limites de profundade tem 100% de acurácia no treino, mas pior no teste. (decorou os dados)""")
```

    Critério gini    : Acurácia = 67.39%, Profundidade = 15, Folhas = 108
    Critério entropy : Acurácia = 72.46%, Profundidade = 15, Folhas = 104
    
    Testando diferentes profundidades máximas:
    Max_depth = 3   : Train = 80.80%, Test = 73.91%, Profundidade Real =  3, Folhas =   8
    Max_depth = 5   : Train = 84.96%, Test = 76.81%, Profundidade Real =  5, Folhas =  22
    Max_depth = 7   : Train = 90.04%, Test = 73.91%, Profundidade Real =  7, Folhas =  47
    Max_depth = 10  : Train = 95.83%, Test = 71.74%, Profundidade Real = 10, Folhas =  82
    Max_depth = None: Train = 100.00%, Test = 67.39%, Profundidade Real = 15, Folhas = 108
    
    Notas: 
          
     - como profundidades menores podem ter melhor generalização (menor overfitting)
          
     - Note como a árvore sem limites de profundade tem 100% de acurácia no treino, mas pior no teste. (decorou os dados)
    


```python
## =================================================
# 4. FEATURE IMPORTANCE
# =================================================

tree_analysis = DecisionTreeClassifier(max_depth=5, random_state=42)
tree_analysis.fit(X_train, y_train)

# Importar bibliotecas necessárias
importances = tree_analysis.feature_importances_
indices = np.argsort(importances)[::-1]

# Exibir as características mais importantes (limitado ao número de features disponíveis)
print("Características mais importantes:")
for f in range(min(10, len(importances))):
    print(f"{f + 1}. {X_simple.columns[indices[f]]} ({importances[indices[f]]:.4f})")

# Plotar a importância das características usando gráfico ASCII
print("\n" + "="*60)
print("GRÁFICO DE IMPORTÂNCIA DAS CARACTERÍSTICAS (ASCII)")
print("="*60)

max_bar_length = 50
for f in range(len(importances)):
    idx = indices[f]
    importance = importances[idx]
    bar_length = int(importance * max_bar_length / importances[indices[0]])
    bar = '█' * bar_length
    print(f"{X_simple.columns[idx]:20} | {bar} {importance:.4f}")

print("="*60)
```

    Características mais importantes:
    1. Credit_Score (0.4710)
    2. Debt (0.1680)
    3. Years_Employed (0.1350)
    4. Debt_to_Income (0.1197)
    5. Age (0.0644)
    6. Income (0.0420)
    
    ============================================================
    GRÁFICO DE IMPORTÂNCIA DAS CARACTERÍSTICAS (ASCII)
    ============================================================
    Credit_Score         | ██████████████████████████████████████████████████ 0.4710
    Debt                 | █████████████████ 0.1680
    Years_Employed       | ██████████████ 0.1350
    Debt_to_Income       | ████████████ 0.1197
    Age                  | ██████ 0.0644
    Income               | ████ 0.0420
    ============================================================
    


```python
# =================================================
# 5. Otimização de Hiperparâmetros com Grid Search
# =================================================

from sklearn.model_selection import GridSearchCV

# Definir espaço de busca
param_grid = {
    'criterion': ['gini', 'entropy'],
    'max_depth': [3, 5, 7, 10, None],
    'min_samples_split': [2, 5, 10],
    'min_samples_leaf': [1, 2, 4],
    'max_features': [None, 'sqrt', 'log2']
}

# Grid search com validação cruzada
dt_grid = DecisionTreeClassifier(random_state=42)
grid_search = GridSearchCV(dt_grid, param_grid, cv=5, scoring='accuracy', verbose=1, n_jobs=-1)
grid_search.fit(X_train, y_train)

# Melhores parâmetros
print(f"Melhores parâmetros: {grid_search.best_params_}")
print(f"Melhor score CV: {grid_search.best_score_*100:.2f}%")

# Avaliar no conjunto de teste
best_dt = grid_search.best_estimator_
y_pred_best = best_dt.predict(X_test)
accuracy_best = accuracy_score(y_test, y_pred_best)
print(f"Acurácia no teste: {accuracy_best*100:.2f}%")

# Informações sobre a melhor árvore
print(f"\nInformações da melhor árvore:")
print(f"Profundidade: {best_dt.get_depth()}")
print(f"Número de folhas: {best_dt.get_n_leaves()}")
print(f"Número de nós: {best_dt.tree_.node_count}")

# Relatório detalhado
print(f"\nRelatório de Classificação:")
print(classification_report(y_test, y_pred_best, target_names=['Negado', 'Aprovado']))
```

    Fitting 5 folds for each of 270 candidates, totalling 1350 fits
    Melhores parâmetros: {'criterion': 'gini', 'max_depth': 7, 'max_features': 'sqrt', 'min_samples_leaf': 1, 'min_samples_split': 5}
    Melhor score CV: 75.36%
    Acurácia no teste: 74.64%
    
    Informações da melhor árvore:
    Profundidade: 7
    Número de folhas: 45
    Número de nós: 89
    
    Relatório de Classificação:
                  precision    recall  f1-score   support
    
          Negado       0.86      0.60      0.71        70
        Aprovado       0.69      0.90      0.78        68
    
        accuracy                           0.75       138
       macro avg       0.77      0.75      0.74       138
    weighted avg       0.77      0.75      0.74       138
    
    


```python
# =================================================
# 5. Análise de Casos Específicos e Interpretabilidade
# =================================================

# Vamos analisar alguns casos específicos para entender as decisões da árvore
test_cases = [
    [35, 5, 0.3, 700, 50000, 15000],  # Caso favorável: idade média, empregado há tempo, baixo debt-to-income
    [25, 1, 0.8, 500, 25000, 20000],  # Caso desfavorável: jovem, pouco tempo empregado, alto debt-to-income
    [45, 10, 0.2, 800, 80000, 16000], # Caso muito favorável: idade madura, muito tempo empregado, baixo debt-to-income
    [22, 0.5, 0.9, 450, 20000, 18000] # Caso muito desfavorável: muito jovem, pouco tempo empregado, muito alto debt-to-income
]

feature_names = ['Age', 'Years_Employed', 'Debt_to_Income', 'Credit_Score', 'Income', 'Debt']

print("Análise de Casos Específicos:")
print("=" * 80)

for i, case in enumerate(test_cases):
    # Fazer predição
    prediction = best_dt.predict([case])[0]
    probabilities = best_dt.predict_proba([case])[0]
    
    # Mostrar o caminho da decisão
    decision_path = best_dt.decision_path([case])
    leaf_id = best_dt.apply([case])[0]
    
    result_names = {0: "Negado", 1: "Aprovado"}
    
    print(f"Caso {i+1}:")
    print(f"  Características:")
    for j, (feature, value) in enumerate(zip(feature_names, case)):
        print(f"    {feature}: {value}")
    
    print(f"  Predição: {result_names[prediction]}")
    print(f"  Probabilidades: Negado={probabilities[0]:.3f}, Aprovado={probabilities[1]:.3f}")
    print(f"  Confiança: {max(probabilities):.3f}")
    print(f"  {'*' * 60}")

# Matriz de confusão
plt.figure(figsize=(8, 6))
cm = confusion_matrix(y_test, y_pred_best)
sns.heatmap(cm, annot=True, fmt='d', cmap='Blues', 
            xticklabels=['Negado', 'Aprovado'],
            yticklabels=['Negado', 'Aprovado'])
plt.title('Matriz de Confusão - Árvore de Decisão Otimizada')
plt.ylabel('Valor Real')
plt.xlabel('Predição')
plt.show()

# Curva de learning
from sklearn.model_selection import learning_curve

train_sizes, train_scores, val_scores = learning_curve(
    best_dt, X_train, y_train, cv=5, 
    train_sizes=np.linspace(0.1, 1.0, 10)
)

plt.figure(figsize=(10, 6))
plt.plot(train_sizes, np.mean(train_scores, axis=1), 'o-', label='Score de Treino')
plt.plot(train_sizes, np.mean(val_scores, axis=1), 'o-', label='Score de Validação')
plt.xlabel('Tamanho do Conjunto de Treino')
plt.ylabel('Acurácia')
plt.title('Curva de Aprendizado - Árvore de Decisão')
plt.legend()
plt.grid(True, alpha=0.3)
plt.show()
```

    Análise de Casos Específicos:
    ================================================================================
    Caso 1:
      Características:
        Age: 35
        Years_Employed: 5
        Debt_to_Income: 0.3
        Credit_Score: 700
        Income: 50000
        Debt: 15000
      Predição: Negado
      Probabilidades: Negado=1.000, Aprovado=0.000
      Confiança: 1.000
      ************************************************************
    Caso 2:
      Características:
        Age: 25
        Years_Employed: 1
        Debt_to_Income: 0.8
        Credit_Score: 500
        Income: 25000
        Debt: 20000
      Predição: Negado
      Probabilidades: Negado=1.000, Aprovado=0.000
      Confiança: 1.000
      ************************************************************
    Caso 3:
      Características:
        Age: 45
        Years_Employed: 10
        Debt_to_Income: 0.2
        Credit_Score: 800
        Income: 80000
        Debt: 16000
      Predição: Negado
      Probabilidades: Negado=1.000, Aprovado=0.000
      Confiança: 1.000
      ************************************************************
    Caso 4:
      Características:
        Age: 22
        Years_Employed: 0.5
        Debt_to_Income: 0.9
        Credit_Score: 450
        Income: 20000
        Debt: 18000
      Predição: Negado
      Probabilidades: Negado=1.000, Aprovado=0.000
      Confiança: 1.000
      ************************************************************
    


    
![png](case_ia_files/case_ia_321_1.png)
    



    
![png](case_ia_files/case_ia_321_2.png)
    


### Conclusões, Expertises e Dicas Práticas

**Vantagens das Árvores de Decisão:**

1. **Alta Interpretabilidade**: Fácil de entender e explicar para stakeholders não-técnicos
2. **Não Requer Preparação Extensiva dos Dados**: Funciona com dados categóricos e numéricos sem normalização
3. **Captura Relacionamentos Não-Lineares**: Pode modelar interações complexas entre features
4. **Seleção Automática de Features**: Ignora features irrelevantes automaticamente
5. **Robusta a Outliers**: Divisões baseadas em rankings, não em valores absolutos

**Desvantagens:**

1. **Tendência ao Overfitting**: Especialmente com árvores profundas
2. **Instabilidade**: Pequenas mudanças nos dados podem resultar em árvores muito diferentes
3. **Bias para Features com Mais Categorias**: Features com mais valores únicos têm vantagem
4. **Dificuldade com Relacionamentos Lineares**: Pode ser ineficiente para padrões lineares simples
5. **Predições "Escalonadas"**: Só pode prever valores que existem no conjunto de treino


### 
---

### **Conceito de Decision Trees para Classificação**

Árvores de decisão é um tipo de modelo não paramétrico utilizado para fazer classificação baseado em **condições sequencias**. Essencialmente, podemos pensar nesse tipo de modelo como uma sequência de questões do tipo **if/else**, levando a uma decisão final. Um modelo de árvore de decisão tenta aprender qual sequência de questões if/else nos leva a o resultado desejado de forma mais rápida.

Para váriaveis categoricas, podemos pensar que as questões feitas serão do tipo sim ou não. Por exemplo, "essa variável pertence a classe 1? se (if) sim ..., se não (else)..."

Já para variáveis contínuas, as perguntas feitas tem a finalidade de dividir a decisão tendo como condicional um threshold para dividir os dados. Por exemplo, "essa variável i é maior que o valor x? se(if) sim ..., se não (else)..."

Algumas terminologias importantes:
- **Nó (node)**: Pontos onde as questões if/else são feitas
- **Folhas (leafs)**: Representam o resultado final das questões feitas

Em uma árvore de decisão bem feita, cada nó (questão) irá cortar o número de decisões pela metade, aproximadamente. O ponto principal, no final das contas, é o modelo conseguir aprender quais são as questões **ótimas** a se fazer.

Vamos utilizar um exemplo simples para ilustrar uma árvore de decisão. Imagine que você está decidindo se irá a praia e, para isso, irá considerar duas variáveis: Se há vento e se há sol. A árvore de decisão para essa situação está ilustrada abaixo:

<p align=center>
<img src="https://didatica.tech/wp-content/uploads/2020/07/image-3.png" width=500 height=300></img> </p>

No nó inicial, você se pergunta: Há sol? Se não houver sol, você vai para o ramo da direita e decide não ir a praia. Porém, se houver sol, você vai para o ramo da esquerda e faz a próxima pergunta: Está ventando? Mais uma vez, caso a resposta seja sim, você decide não ir a praia. Porém, se não estiver ventando, você decidirá ir a praia.

#### **Classification Trees**

As **árvores de classificação** são um tipo de árvore de decisão projetada para categorizar dados em diferentes classes. Elas funcionam dividindo os dados em subconjuntos baseados em condições específicas, representadas por regras de "se-então". O objetivo final é determinar a classe mais provável de um dado, com base nos valores de suas características. As folhas da árvore representam as classes finais, enquanto os nós internos contêm condições que guiam o processo de decisão.

### **Critérios de divisão**

#### **Critério de Gini**

##### **Impureza**

 A **Impureza** em uma árvore de decisão é uma medida da heterogeneidade ou mistura das classes em um conjunto de dados em um determinado nó da árvore. Ela quantifica o grau de incerteza associado à distribuição das classes no nó, ou seja, o quão "confuso" ele é em termos de pertencer predominantemente a uma única classe. Quanto menor a impureza, mais homogêneo é o nó e mais confiante o modelo pode estar ao classificar uma instância que atinge aquele nó.

##### **Por que a impureza é importante?**

A impureza é usada durante o treinamento para determinar as condições de divisão nos nós. O objetivo de uma árvore de classificação é criar nós que sejam os mais homogêneos possíveis em relação às classes. Isso significa que, após cada divisão, os subconjuntos resultantes devem ter impureza reduzida em comparação com o nó original. Essa redução na impureza é conhecida como ganho de informação ou redução de Gini, dependendo do critério escolhido.

##### **Índice de Gini**
O Índice de Gini mede a probabilidade de um elemento ser classificado incorretamente se for escolhido aleatoriamente de um conjunto de dados. Ou seja, ele avalia o quão misturadas estão as classes dentro de um nó.

A fórmula do Índice de Gini para um nó $t$ é:

$$
G = 1 - \sum_{i=1}^{k} p_i^{2}
$$

Onde:
- $p_i$ é a proporção de elementos da classe $i$ no conjunto de dados do nó.
- $k$ é o número total de classes.

O valor do índice varia entre 0 e 1:
- **0 (pureza máxima)**: Todos os elementos pertencem a uma única classe.
- **Próximo de 1 (impureza máxima)**: As classes estão distribuídas de forma uniforme.

Caso o nó possua ramificações, o seu **Índice de Gini** será dado pela média ponderada dos Índices de Gini de seus dois nós filhos:

$$
G_{\text{total}} \;=\; \frac{n_a}{n_a+n_b}\, G_A \;+\; \frac{n_b}{n_a+n_b}\, G_B
$$

Onde:
- $G_A$ é o Índice de Gini do nó filho $A$;
- $G_B$ é o Índice de Gini do nó filho $B$;
- $\frac{n_a}{n_a+n_b}$ e $\frac{n_b}{n_a+n_b}$ são as proporções de instâncias nas folhas $A$ e $B$, respectivamente.

**Interpretação:**
- Se as duas folhas tiverem grande diferença no número de instâncias, a folha com mais instâncias terá peso maior no $G_{\text{total}}$.
- Quanto mais homogêneo for um nó filho, menor o seu índice de Gini. Se ambos forem homogêneos, a impureza da ramificação e, por consequência, do nó pai diminui.


#### **Entropia**

Entropia pode ser definida como a medida que nos diz o quanto nossos dados estão desorganizados e misturados. Quanto maior a entropia, menor o ganho de informação e vice-versa. Nossos dados ficam menos entrópicos conforme dividimos os dados em conjuntos capazes de representar apenas uma classe do nosso modelo.

A fórmula da entropia é a seguinte:

$$H(S) = - \sum_{i=1}^{C} p_i \log_2(p_i)$$

Onde:
- $p_i$ é a proporção de elementos da classe $i$.
- $C$ é o número total de classes

Se todos os exemplos pertencem à mesma classe (ou seja, não há incerteza), a entropia é zero. Se há uma divisão uniforme entre diferentes classes, a entropia é máxima.

Perceba que tanto o índice de Gine quanto a entropia são muito semelhantes. Porém, o índice de Gini é baseado na teoria da probabilidade e mede impureza como a probabilidade de erro na classificação. Já a entropia vêm da teoria da informação e mede a impureza com base nela.

### **Poda e Overfitting**

O problema de overfitting costuma ser um ponto de grande atenção em modelos de árvores de decisão. Pense que, no limite, podemos fazer quantas perguntas do tipo if/else quisermos e iremos conseguir classificar os dados de treino de forma quase perfeita. Quando isso acontece, temos uma árvore tão profunda que ela passa a focar no ruído particular dos dados de treino ao invés das relações fundamentais entre os dados. Dessa forma, o modelo irá falhar ao tentar generalizar para novos dados. 

Em uma árvore de decisão, o overfitting pode ocorrer quando a árvore é construída com profundidade excessiva, ou seja, quando ela continua dividindo os dados até o ponto em que cada folha contém apenas uma instância de dados ou poucas instâncias. Isso leva a um modelo que é extremamente sensível a pequenas variações nos dados de entrada e pode não ser robusto o suficiente para fazer previsões precisas em dados não vistos.

**Poda (post-pruning)**:

Uma das estratégias para controlar o overfiting é a chamada **poda**. Basicamente, ela consiste em, após a construção da árvore, remover nós que tragam pouca informação para a decisão final (pense mesmo na analogia com a poda de uma árvore). Isso é feito para simplificar a árvore e reduzir sua complexidade.

**Limitar o tamanho da árvore (pré-pruning):**

Outro tipo de poda possível é, antes de criarmos a árvore, limitar a profundida máxima da árvore ou o número mínimo de itens classificados dentro de uma categoria. Assim, conseguimos impedir que a árvore cresça demais e impedindo o overfitting.



```python
# Importa o modelo de Arvores de Decisão
from sklearn.tree import DecisionTreeClassifier

# Instancia o modelo de Arvores de Decisão
decision_tree_classifier = DecisionTreeClassifier()

# Treina o modelo de Arvores de Decisão com os dados de treino
decision_tree_classifier.fit(X_train, y_train)

# Faz previsões com os dados de teste
y_pred_decision_tree_classifier = decision_tree_classifier.predict(X_test)

# Calcula a acurácia
accuracy_decision_tree_classifier = accuracy_score(y_test, y_pred_decision_tree_classifier)
print(f'Acurácia do modelo de Arvores de Decisão: {accuracy_decision_tree_classifier:.5f}')
```

    Acurácia do modelo de Arvores de Decisão: 0.94444
    

# **Extra: Um pouco sobre métodos de ensemble**

Fontes: https://en.wikipedia.org/wiki/Ensemble_learning

https://hub.asimov.academy/blog/o-que-e-ensemble-learning/

Vamos imaginar que você precisa tomar uma decisão importante: investir em uma ação na bolsa. Você poderia:

1. **Consultar apenas um especialista** - E se ele estiver tendo um dia ruim ou tiver um viés?

2. **Consultar vários especialistas e combinar suas opiniões** - provavelmente mais confiável, mas mais rápido

É exatamente essa ideia com **Ensemble Learning**!

Até agora, estudamos vários algoritmos de classificação: KNN, Naive Bayes, Regressão Logística, Árvores de Decisão, SVM. Cada um tem seus pontos fortes e fracos:

- **Árvores de Decisão**: Fáceis de interpretar, mas propensas a overfitting
- **KNN**: Simples e eficaz, mas sensível a ruído e features irrelevantes
- **Naive Bayes**: Rápido e eficiente, mas assume independência entre features
- **Regressão Logística**: Interpretável e estável, mas assume relação linear

**Mas o que aconteceria se pudessemos unir eles?**

### 3.6.1 O Problema: Por que um único modelo não é suficiente?

Vamos fazer um experimento. Imagine que você está construindo um modelo para prever se um cliente vai cancelar sua assinatura (churn).

**Cenário 1: Uma única Árvore de Decisão**

Você treina uma árvore de decisão e obtém 85% de acurácia no conjunto de teste. Ótimo, certo?

Mas espera... imagina que isso é o que acontece (e normalmente será) se treinar a mesma árvore com pequenas variações nos dados:

- **Tentativa 1**: 85% de acurácia
- **Tentativa 2**: 82% de acurácia (removemos 5% dos dados aleatoriamente)
- **Tentativa 3**: 88% de acurácia (diferentes dados de treino)
- **Tentativa 4**: 79% de acurácia
- **Tentativa 5**: 86% de acurácia

**Problemas:**

1. **Alta Variância**: Pequenas mudanças nos dados causam grandes variações no modelo
2. **Overfitting**: O modelo pode estar "decorando" os dados de treino
3. **Instabilidade**: Não podemos confiar plenamente em suas previsões

**A Solução dos Ensembles:**

Em vez de confiar em uma única árvore, será que faz sentido treinar várias árvores diferentes e combinar suas previsões?

- Se 8 de 10 árvores dizem "cliente vai cancelar", provavelmente ele vai...

### 3.6.2 Bagging: Bootstrap Aggregating

**O que é Bagging?**

Bagging (Bootstrap Aggregating) é como pedir a opinião de várias pessoas que estudaram o mesmo assunto, mas com materiais ligeiramente diferentes.

**A Ideia:**

1. Pegamos nosso conjunto de dados original
2. Criamos várias "versões" diferentes dele (amostras bootstrap)
3. Treinamos um modelo em cada versão
4. Combinamos as previsões

**Bootstrap?**

Bootstrap é uma técnica de reamostragem com substituição. Imagine que você tem uma sacola com 100 bolas numeradas:

- Você retira uma bola, anota o número, e **devolve a bola** na sacola
- Repete isso 100 vezes
- Resultado: alguns números aparecem várias vezes, outros não aparecem

Isso cria uma versão "similar, mas diferente" do conjunto original! Retornaremos nisso

#### 3.6.2.1 Intuição do Bagging

Vamos usar o dataset do Titanic (achei um bom dataset) para entender o Bagging na prática.

**Mesmo Problema**: Prever se um passageiro sobreviveu ao naufrágio.

**Abordagem com uma única Árvore de Decisão:**
- Treina em todos os dados
- Pode fazer overfitting
- Instável com mudanças nos dados

**Abordagem com Bagging:**
- Cria 10 versões diferentes do dataset (bootstrap)
- Treina uma árvore em cada versão
- Cada árvore vota: "Sobreviveu" ou "Não sobreviveu"
- Decisão final: maioria dos votos

Vamos ver isso acontecer!


```python
# =======================================================
# IMPORTANDO AS BIBLIOTECAS
# =======================================================

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import accuracy_score, classification_report

# Configuração de visualização (ignora, estou testando novas visualizações)
sns.set_style("whitegrid")
plt.rcParams['figure.figsize'] = (12, 6)
```


```python
# =======================================================
# Carregando o Dataset do Titanic
# =======================================================

import kagglehub
from kagglehub import KaggleDatasetAdapter

df = kagglehub.dataset_load(
    KaggleDatasetAdapter.PANDAS,
    "yasserh/titanic-dataset",
    "Titanic-Dataset.csv",
    pandas_kwargs={"encoding": "latin", "usecols": [1, 2, 4, 5]}
)

# Pré-processamento
df['Sex'] = df['Sex'].map({'male': 0, 'female': 1})
df['Age'] = df['Age'].fillna(df['Age'].mean())

X = df[['Pclass', 'Sex', 'Age']].values
y = df['Survived'].values

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

print(f"Tamanho do conjunto de treino: {len(X_train)}")
print(f"Tamanho do conjunto de teste: {len(X_test)}")
```

    Tamanho do conjunto de treino: 712
    Tamanho do conjunto de teste: 179
    


```python
# =======================================================
# Passo 1: Treinar uma ÚNICA Árvore de Decisão
# =======================================================

single_tree = DecisionTreeClassifier(random_state=42)
single_tree.fit(X_train, y_train)

y_pred_single = single_tree.predict(X_test)
metrics_single = classification_report(y_test, y_pred_single)

print(f"Métricas de uma única árvore:\n{metrics_single}")

# Vamos ver como essa árvore se comporta com diferentes amostras
print("\nTestando estabilidade (treinando em diferentes subconjuntos):")
accuracies = []

for i in range(10):
    # Criar uma amostra bootstrap
    indices = np.random.choice(len(X_train), size=len(X_train), replace=True)
    X_boot = X_train[indices]
    y_boot = y_train[indices]
    
    # Treinar árvore
    tree = DecisionTreeClassifier(random_state=i)
    tree.fit(X_boot, y_boot)
    
    # Avaliar
    acc = accuracy_score(y_test, tree.predict(X_test))
    accuracies.append(acc)
    print(f"Árvore {i+1}: {acc*100:.2f}%")

print(f"\nMédia: {np.mean(accuracies)*100:.2f}%")
print(f"Desvio padrão: {np.std(accuracies)*100:.2f}%")
print(f"\nInterpretação: A acurácia varia entre {min(accuracies)*100:.2f}% e {max(accuracies)*100:.2f}%")
print("nota: Cada árvore 'aprendeu' algo diferente.")
```

    Métricas de uma única árvore:
                  precision    recall  f1-score   support
    
               0       0.79      0.85      0.82       105
               1       0.76      0.68      0.71        74
    
        accuracy                           0.78       179
       macro avg       0.77      0.76      0.77       179
    weighted avg       0.78      0.78      0.77       179
    
    
    Testando estabilidade (treinando em diferentes subconjuntos):
    Árvore 1: 79.33%
    Árvore 2: 79.89%
    Árvore 3: 79.33%
    Árvore 4: 83.80%
    Árvore 5: 77.09%
    Árvore 6: 78.21%
    Árvore 7: 74.30%
    Árvore 8: 78.21%
    Árvore 9: 75.98%
    Árvore 10: 77.65%
    
    Média: 78.38%
    Desvio padrão: 2.41%
    
    Interpretação: A acurácia varia entre 74.30% e 83.80%
    nota: Cada árvore 'aprendeu' algo diferente.
    


```python
# =======================================================
# Passo 2: Implementar Bagging Manualmente
# =======================================================
seeds = np.arange(10)

# Armazenar os modelos
models = []
predictions = []

print("Treinando ensemble com Bagging...")
for i in seeds:
    # 1. Criar amostra bootstrap
    indices = np.random.choice(len(X_train), size=len(X_train), replace=True)
    X_boot = X_train[indices]
    y_boot = y_train[indices]
    
    # 2. Treinar modelo na amostra bootstrap
    tree = DecisionTreeClassifier(random_state=i)
    tree.fit(X_boot, y_boot)
    models.append(tree)
    
    # 3. Fazer previsões
    pred = tree.predict(X_test)
    predictions.append(pred)
    
    print(f"Árvore {i+1} treinada em {len(np.unique(indices))} amostras únicas (de {len(X_train)} possíveis)")


predictions = np.array(predictions)

print(f"\nShape das previsões: {predictions.shape}")
print(f"({seeds.size} árvores, {len(X_test)} amostras de teste)")

# =======================================================
# Passo 3: Combinar previsões por votação majoritária
# =======================================================

# Para cada amostra de teste, contar os votos
final_predictions = []

for i in range(len(X_test)):
    votes = predictions[:, i]  # Votos de todas as árvores para a amostra i
    # Votação majoritária
    prediction = np.bincount(votes).argmax()
    final_predictions.append(prediction)

final_predictions = np.array(final_predictions)

# Avaliar
metrics_bagging = classification_report(y_test, final_predictions)

print(f"\n{'='*50}")
print(f"RESULTADOS:")
print(f"{'='*50}")
print(f"Métricas com Bagging ({seeds.size} árvores):\n{metrics_bagging}")
metric = accuracy_score(y_test, final_predictions)
print(f"Acurácia com Bagging ({seeds.size} árvores): {metric*100:.2f}%")
print(f"Melhoria: {(metric - accuracy_score(y_test, y_pred_single))*100:.2f} pontos percentuais")
```

    Treinando ensemble com Bagging...
    Árvore 1 treinada em 452 amostras únicas (de 712 possíveis)
    Árvore 2 treinada em 457 amostras únicas (de 712 possíveis)
    Árvore 3 treinada em 453 amostras únicas (de 712 possíveis)
    Árvore 4 treinada em 449 amostras únicas (de 712 possíveis)
    Árvore 5 treinada em 448 amostras únicas (de 712 possíveis)
    Árvore 6 treinada em 459 amostras únicas (de 712 possíveis)
    Árvore 7 treinada em 448 amostras únicas (de 712 possíveis)
    Árvore 8 treinada em 438 amostras únicas (de 712 possíveis)
    Árvore 9 treinada em 454 amostras únicas (de 712 possíveis)
    Árvore 10 treinada em 447 amostras únicas (de 712 possíveis)
    
    Shape das previsões: (10, 179)
    (10 árvores, 179 amostras de teste)
    
    ==================================================
    RESULTADOS:
    ==================================================
    Métricas com Bagging (10 árvores):
                  precision    recall  f1-score   support
    
               0       0.79      0.85      0.82       105
               1       0.76      0.68      0.71        74
    
        accuracy                           0.78       179
       macro avg       0.77      0.76      0.77       179
    weighted avg       0.78      0.78      0.77       179
    
    Acurácia com Bagging (10 árvores): 77.65%
    Melhoria: 0.00 pontos percentuais
    


```python
# =======================================================
# Visualização: Como cada árvore vota
# =======================================================

# Vamos ver as previsões para as primeiras 10 amostras de teste
n_samples_to_show = 10

fig, ax = plt.subplots(figsize=(14, 6))

# Criar matriz de votos
vote_matrix = predictions[:, :n_samples_to_show].T

# Plotar heatmap
im = ax.imshow(vote_matrix, cmap='RdYlGn', aspect='auto', vmin=0, vmax=1)

# Configurar eixos
ax.set_xlabel('Árvore', fontsize=12)
ax.set_ylabel('Amostra de Teste', fontsize=12)
ax.set_title('Votação de Cada Árvore (0 = Não Sobreviveu, 1 = Sobreviveu)', fontsize=14, fontweight='bold')
ax.set_xticks(range(seeds.size))
ax.set_xticklabels([f'Árvore {i+1}' for i in range(seeds.size)], rotation=45)
ax.set_yticks(range(n_samples_to_show))
ax.set_yticklabels([f'Amostra {i+1}' for i in range(n_samples_to_show)])
ax.grid(False)

# Adicionar valores nas células
for i in range(n_samples_to_show):
    for j in range(seeds.size):
        text = ax.text(j, i, int(vote_matrix[i, j]), 
                      ha="center", va="center", color="black", fontsize=10)


# Adicionar informação sobre a votação final
for i in range(n_samples_to_show):
    votes = vote_matrix[i]
    final_vote = "Sobreviveu" if np.sum(votes) > seeds.size/2 else "Não Sobreviveu"
    vote_count = int(np.sum(votes))
    ax.text(seeds.size, i, f'{final_vote}\n({vote_count}/{seeds.size})', 
           ha="left", va="center", fontsize=9, fontweight='bold')

plt.tight_layout()
plt.show()

print("\nInterpretação:")
print("- Verde: Árvore previu 'Sobreviveu' (1)")
print("- Vermelho: Árvore previu 'Não Sobreviveu' (0)")
print("- Decisão final: maioria dos votos")
```


    
![png](case_ia_files/case_ia_346_0.png)
    


    
    Interpretação:
    - Verde: Árvore previu 'Sobreviveu' (1)
    - Vermelho: Árvore previu 'Não Sobreviveu' (0)
    - Decisão final: maioria dos votos
    

#### 3.6.2.2 Formulação Formal do Bagging

**Entrada:**

1. Conjunto de treinamento: $D = \{(x^{(1)}, y^{(1)}), (x^{(2)}, y^{(2)}), ..., (x^{(n)}, y^{(n)})\}$

2. Algoritmo de aprendizado base $\mathcal{A}$ (e.g., Árvore de Decisão)

3. Número de modelos no ensemble: $T$

**Processamento:**

Para cada modelo $t = 1, 2, ..., T$:

1. **Criar amostra bootstrap** $D_t$:
   - Amostrar $n$ exemplos de $D$ com substituição
   - Aproximadamente 63.2% das amostras originais aparecem em $D_t$
   - As amostras restantes (~36.8%) são chamadas de "out-of-bag" (OOB), (por quê?)

2. **Treinar modelo base**:
   - $h_t = \mathcal{A}(D_t)$
   - Cada modelo $h_t$ é treinado independentemente

**Saída - Predição:**

Para uma nova amostra $x^o$:

- votação majoritária:

$$\hat{y} = \text{moda}\{h_1(x^o), h_2(x^o), ..., h_T(x^o)\}$$

**Propriedades Importantes:**

1. **Redução de Variância**: 
   - Se os modelos base têm variância $\sigma^2$, a variância do ensemble é aproximadamente $\frac{\sigma^2}{T}$ (assumindo independência)
   - Na prática, $\frac{\sigma^2}{T}$ nunca acontece porque há correlação entre modelos, mas de fato a variância é reduzida

2. **Out-of-Bag Error (OOB)**:
   - Para cada amostra de treino, podemos usar os modelos que NÃO a viram no treino para estimar o erro
   - Isso fornece uma estimativa de validação "gratuita" sem precisar de um conjunto de validação separado
   e.g

   Suponha $n=5$ amostras e $T=3$ modelos:

   - Modelo 1 treinou com amostras: {1, 2, 3, 5} → amostra 4 está OOB
   - Modelo 2 treinou com amostras: {1, 2, 4, 5} → amostra 3 está OOB  
   - Modelo 3 treinou com amostras: {2, 3, 4, 5} → amostra 1 está OOB

   Para avaliar a amostra 4:
   - Use apenas Modelo 1 (que não viu a amostra 4)
   - $\hat{y}^{OOB}_4 = h_1(x^{(4)})$

   Para avaliar a amostra 1:
   - Use apenas Modelo 3 (que não viu a amostra 1)
   - $\hat{y}^{OOB}_1 = h_3(x^{(1)})$


3. **Bias-Variance Tradeoff**:
   - O grande dilema!
   - Por isso, funciona melhor com modelos de baixo bias e alta variância (como árvores mais profundas)

#### 3.6.2.3 Desafio: Implementar Bagging do Zero

Esse é um pouco mais complicado, mas tente implementar uma classe `BaggingClassifier` que funcione com qualquer classificador base.

**Requisitos:**

1. Deve aceitar qualquer classificador como base (DecisionTree, KNN, etc.)
2. Criar amostras bootstrap
3. Treinar múltiplos modelos
4. Combinar previsões por votação
5. Calcular OOB error (desafio extra, se pra ti estiver facil)


```python
from sklearn.base import clone

class BaggingClassifier:
    def __init__(self, base_estimator, n_estimators=10, random_state=None):
        """
        Inicializa o BaggingClassifier
        
        Parâmetros:
        -----------
        base_estimator: classificador base (e.g., DecisionTreeClassifier())
        n_estimators: número de modelos no ensemble
        random_state: seed para reprodutibilidade
        """
        pass
    
    def _create_bootstrap_sample(self, X, y):
        """
        Cria uma amostra bootstrap de X e y
        
        Retorna:
        --------
        X_boot, y_boot: amostra bootstrap
        oob_indices: índices das amostras out-of-bag
        """
        pass
    
    def fit(self, X, y):
        """
        Treina o ensemble
        
        Processo:
        1. Para cada estimador:
           a. Criar amostra bootstrap
           b. Clonar o estimador base
           c. Treinar o clone na amostra bootstrap
           d. Armazenar o modelo e os índices OOB
        """
        pass
    
    def predict(self, X):
        """
        Faz previsões usando votação majoritária
        
        Retorna:
        --------
        y_pred: array de previsões
        """
        pass
    
    def score(self, X, y):
        """
        Calcula a acurácia do modelo
        """
        pass
    
    def oob_score(self):
        """
        DESAFIO EXTRA: Calcular o OOB error
        
        Para cada amostra de treino:
        - Usar apenas os modelos que NÃO a viram no treino
        - Fazer votação com esses modelos
        - Comparar com o label verdadeiro
        
        Retorna:
        --------
        oob_accuracy: acurácia calculada nas amostras OOB
        """
        pass
```

#### 3.6.2.4 Usando Sklearn: BaggingClassifier e Random Forest

Agora vamos ver como funcionas as implementações do scikit-learn!


```python
from sklearn.ensemble import BaggingClassifier, RandomForestClassifier
from sklearn.tree import DecisionTreeClassifier
from sklearn.neighbors import KNeighborsClassifier
from sklearn.naive_bayes import GaussianNB

# =======================================================
# 1. BaggingClassifier com Árvores de Decisão
# =======================================================

bagging_tree = BaggingClassifier(
    estimator=DecisionTreeClassifier(),
    n_estimators=50,
    random_state=42,
    oob_score=True  # Calcular OOB score
)

bagging_tree.fit(X_train, y_train)

print("="*60)
print("BAGGING COM ÁRVORES DE DECISÃO")
print("="*60)
print(f"Acurácia no teste: {bagging_tree.score(X_test, y_test)*100:.2f}%")
print(f"OOB Score: {bagging_tree.oob_score_*100:.2f}%")
print(f"Número de estimadores: {bagging_tree.n_estimators}")

# =======================================================
# 2. Random Forest (Bagging + Feature Randomness)
# =======================================================

# Random Forest é um tipo especial de Bagging que:
# - Usa árvores de decisão como base
# - Adiciona aleatoriedade na seleção de features

random_forest = RandomForestClassifier(
    n_estimators=50,
    random_state=42,
    oob_score=True
)

random_forest.fit(X_train, y_train)

print("\n" + "="*60)
print("RANDOM FOREST (Bagging + Feature Randomness)")
print("="*60)
print(f"Acurácia no teste: {random_forest.score(X_test, y_test)*100:.2f}%")
print(f"OOB Score: {random_forest.oob_score_*100:.2f}%")

# Feature importance
feature_names = ['Pclass', 'Sex', 'Age']
importances = random_forest.feature_importances_
print("\nImportância das features:")
for name, importance in zip(feature_names, importances):
    print(f"  {name}: {importance*100:.2f}%")

# =======================================================
# 3. Bagging com outros classificadores
# =======================================================

print("\n" + "="*60)
print("BAGGING COM DIFERENTES CLASSIFICADORES BASE")
print("="*60)

# KNN
bagging_knn = BaggingClassifier(
    estimator=KNeighborsClassifier(n_neighbors=5),
    n_estimators=50,
    random_state=42
)
bagging_knn.fit(X_train, y_train)
print(f"\nBagging + KNN: {bagging_knn.score(X_test, y_test)*100:.2f}%")

# Naive Bayes
bagging_nb = BaggingClassifier(
    estimator=GaussianNB(),
    n_estimators=50,
    random_state=42
)
bagging_nb.fit(X_train, y_train)
print(f"Bagging + Naive Bayes: {bagging_nb.score(X_test, y_test)*100:.2f}%")
```

    ============================================================
    BAGGING COM ÁRVORES DE DECISÃO
    ============================================================
    Acurácia no teste: 78.77%
    OOB Score: 79.07%
    Número de estimadores: 50
    
    ============================================================
    RANDOM FOREST (Bagging + Feature Randomness)
    ============================================================
    Acurácia no teste: 79.33%
    OOB Score: 79.49%
    
    Importância das features:
      Pclass: 16.11%
      Sex: 40.54%
      Age: 43.34%
    
    ============================================================
    BAGGING COM DIFERENTES CLASSIFICADORES BASE
    ============================================================
    
    Bagging + KNN: 79.89%
    Bagging + Naive Bayes: 75.42%
    


```python
# =======================================================
# Parâmetros Importantes do BaggingClassifier
# =======================================================

# n_estimators: número de modelos base
# max_samples: número/proporção de amostras para cada bootstrap
# max_features: número/proporção de features para cada modelo
# bootstrap: se True, usa bootstrap; se False, usa todo dataset
# oob_score: se True, calcula OOB score

configs = [
    {'n_estimators': 10, 'max_samples': 1.0, 'max_features': 1.0},
    {'n_estimators': 50, 'max_samples': 0.8, 'max_features': 1.0},
    {'n_estimators': 100, 'max_samples': 1.0, 'max_features': 0.8},
    {'n_estimators': 50, 'max_samples': 0.7, 'max_features': 0.7},
]

print("Testando diferentes configurações:\n")
for i, config in enumerate(configs, 1):
    bag = BaggingClassifier(
        estimator=DecisionTreeClassifier(),
        random_state=42
    )
    bag.fit(X_train, y_train)
    
    print(f"{i}. n_estimators={config['n_estimators']}, "
          f"max_samples={config['max_samples']}, "
          f"max_features={config['max_features']}")
    print(f"   Acurácia: {bag.score(X_test, y_test)*100:.2f}%")
```

    Testando diferentes configurações:
    
    1. n_estimators=10, max_samples=1.0, max_features=1.0
       Acurácia: 78.21%
    2. n_estimators=50, max_samples=0.8, max_features=1.0
       Acurácia: 78.21%
    3. n_estimators=100, max_samples=1.0, max_features=0.8
       Acurácia: 78.21%
    4. n_estimators=50, max_samples=0.7, max_features=0.7
       Acurácia: 78.21%
    

-Adicione o OOB score e veja o que acontece- Como você faria uma validação cruzada?

**Dica: Random Forest vs Bagging**

- **BaggingClassifier com árvores**: Cada árvore vê TODAS as features em cada divisão
- **RandomForest**: Cada divisão da árvore vê apenas um subconjunto aleatório de features

Por que isso importa?
- Random Forest cria árvores mais **decorrelacionadas**
- Resultado: geralmente melhor performance que Bagging puro
- Trade-off: um pouco mais de bias, mas muito menos variância

### 3.6.3 Boosting: Aprendizado Sequencial

**O que é Boosting?**

- **Bagging**: Modelos treinados em **paralelo**, independentemente
  - "Todos vocês, estudem o material e me digam o que acham"

- **Boosting**: Modelos treinados em **sequência**, cada um focando nos erros do anterior
  - "Você 1, estude tudo. Você 2, foque no que o 1 errou. Você 3, foque no que os anteriores erraram..."

**A ideia:**

1. Treinar um modelo "fraco" (weak learner)
2. Identificar em quais amostras ele errou
3. Dar mais **peso/atenção** a essas amostras difíceis
4. Treinar um novo modelo focado nelas
5. Repetir o processo
6. Combinar todos os modelos, dando mais peso aos melhores

#### 3.6.3.1 Intuição do AdaBoost (Adaptive Boosting)

AdaBoost foi um dos primeiros e mais populares algoritmos de boosting. Vamos entender como funciona!

**O Processo:**

1. **Início**: Todas as amostras têm peso igual (e.g., 1/n cada)

2. **Treinar modelo 1**: 
   - Treina em todas as amostras
   - Identifica quais errou

3. **Ajustar pesos**:
   - ↑ Aumenta peso das amostras que errou
   - ↓ Diminui peso das que acertou

4. **Treinar modelo 2**:
   - Agora "presta mais atenção" nas amostras difíceis
   - Tem que acertar as que o modelo 1 errou

5. **Repetir** o processo T vezes

6. **Combinar**: Cada modelo tem um peso baseado em sua acurácia
   - Modelos melhores têm mais influência na decisão final

Vamos ver isso na prática!


```python
# =======================================================
# Simulação Visual do AdaBoost

# ideia:
# - Mostrar como os pesos das amostras mudam a cada iteração
# - Mostrar como os erros são tratados
# - Mostrar a importância (alpha) de cada modelo 
# * Não se preocupe com o cálculo exato ainda
# =======================================================

# Dataset 2D simples
np.random.seed(42)
n_samples = 40 
X_viz = np.random.randn(n_samples, 2)  
y_viz = (X_viz[:, 0] + X_viz[:, 1] > 0).astype(int)
y_viz = 2 * y_viz - 1  # Converter para {-1, +1}

# Inicializar
weights = np.ones(n_samples) / n_samples
n_iterations = 3
models = []
alphas = []
all_weights = []

# Treinar AdaBoost
for t in range(n_iterations):
    all_weights.append(weights.copy())
    
    # Treinar weak learner
    weak_learner = DecisionTreeClassifier(max_depth=1, random_state=t)
    weak_learner.fit(X_viz, y_viz, sample_weight=weights)
    predictions = weak_learner.predict(X_viz)
    
    # Calcular erro e alpha
    incorrect = predictions != y_viz
    error = np.sum(weights * incorrect) / np.sum(weights)
    alpha = 0.5 * np.log((1 - error) / (error))
    
    # Atualizar pesos
    weights = weights * np.exp(-alpha * y_viz * predictions)
    weights = weights / np.sum(weights)
    
    models.append(weak_learner)
    alphas.append(alpha)

# Visualização com 3 iterações
fig, axes = plt.subplots(1, 3, figsize=(18, 5))

for t in range(n_iterations):
    ax = axes[t]
    weights_t = all_weights[t]
    predictions = models[t].predict(X_viz)
    incorrect = predictions != y_viz

    sizes = 500 * weights_t / weights_t.max()
    
    # corretos
    correct = ~incorrect
    ax.scatter(X_viz[correct, 0], X_viz[correct, 1], 
              c=y_viz[correct], s=sizes[correct], 
              alpha=0.7, cmap='seismic', edgecolors='k', linewidth=2)
    
    # errados
    if incorrect.sum() > 0:
        ax.scatter(X_viz[incorrect, 0], X_viz[incorrect, 1], 
                  s=sizes[incorrect]*1.5, marker='X', 
                  c=predictions[incorrect],
                  cmap='seismic', edgecolors='r', linewidth=1, zorder=5, alpha=0.9)
    
    # Título
    ax.set_title(f'Modelo {t+1}\n(Alpha = {alphas[t]:.2f})', 
                fontsize=12, fontweight='bold')
    ax.grid(alpha=0.1)
    ax.set_xlabel('Feature 1', fontsize=12)
    if t == 0:
        ax.set_ylabel('Feature 2', fontsize=12)

plt.suptitle('AdaBoost\n(Tamanho = Peso)', 
            fontsize=14, fontweight='bold', y=1.05)
plt.tight_layout()
plt.show()

print("\nINTERPRETAÇÃO:")
print("=" * 60)
print("Pontos MAIORES = amostras com MAIS peso")
print("X = erros -> cor = classe prevista")
print("  - X azul = modelo previu -1 (mas era +1)")
print("  - X vermelho = modelo previu +1 (mas era -1)")
print("A cada iteração, o modelo foca nos erros anteriores")
print(f"\nQuantidade de erros por modelo: {[int((models[t].predict(X_viz) != y_viz).sum()) for t in range(n_iterations)]}")
print(f"\nImportância dos modelos (alphas): {[f'{a:.2f}' for a in alphas]}")

```


    
![png](case_ia_files/case_ia_357_0.png)
    


    
    INTERPRETAÇÃO:
    ============================================================
    Pontos MAIORES = amostras com MAIS peso
    X = erros -> cor = classe prevista
      - X azul = modelo previu -1 (mas era +1)
      - X vermelho = modelo previu +1 (mas era -1)
    A cada iteração, o modelo foca nos erros anteriores
    
    Quantidade de erros por modelo: [5, 7, 14]
    
    Importância dos modelos (alphas): ['0.97', '1.10', '1.04']
    

#### 3.6.3.2 Formulação Formal do AdaBoost

**Entrada:**

1. Conjunto de treinamento: $D = \{(x^{(1)}, y^{(1)}), ..., (x^{(n)}, y^{(n)})\}$ onde $y^{(i)} \in \{-1, +1\}$

2. Algoritmo de aprendizado fraco $\mathcal{A}$

3. Número de iterações: $T$

**Processamento:**

**Inicialização:**
- Pesos uniformes: $w^{(1)}_i = \frac{1}{n}$ para $i = 1, ..., n$

**Para cada iteração** $t = 1, 2, ..., T$:

1. **Treinar modelo fraco**:
   - $h_t = \mathcal{A}(D, w^{(t)})$
   - Cada amostra $(x^{(i)}, y^{(i)})$ tem peso $w^{(t)}_i$

2. **Calcular erro ponderado**:
   
   $$\epsilon_t = \sum_{i=1}^{n} w^{(t)}_i \cdot \mathbb{I}(h_t(x^{(i)}) \neq y^{(i)})$$
   
   onde $\mathbb{I}$ é a função indicadora (1 se erro, 0 se acerto)

3. **Calcular peso do modelo** (influência na predição final):
   
   $$\alpha_t = \frac{1}{2}\ln\left(\frac{1-\epsilon_t}{\epsilon_t}\right)$$
   
   - Se $\epsilon_t$ é pequeno (modelo bom) → $\alpha_t$ é grande
   - Se $\epsilon_t \approx 0.5$ (chute aleatório) → $\alpha_t \approx 0$

4. **Atualizar pesos das amostras**:
   
   $$w^{(t+1)}_i = w^{(t)}_i \cdot \exp(-\alpha_t \cdot y^{(i)} \cdot h_t(x^{(i)}))$$
   
   Simplificando:
   - Se $h_t$ acerta $(y^{(i)} = h_t(x^{(i)}) \Rightarrow y^{(i)}\cdot h_t(x^{(i)}) = 1)$: peso diminui (multiplicado por $e^{-\alpha_t}$)
   - Se $h_t$ erra $(y^{(i)} \neq h_t(x^{(i)})\Rightarrow y^{(i)}\cdot h_t(x^{(i)}) = -1)$: peso aumenta (multiplicado por $e^{\alpha_t}$)

5. **Normalizar pesos**:
   
   $$w^{(t+1)}_i = \frac{w^{(t+1)}_i}{\sum_{j=1}^{n}w^{(t+1)}_j}$$

**Saída - Predição:**

Para uma nova amostra $x^o$:

$$H(x^o) = \text{sign}\left(\sum_{t=1}^{T}\alpha_t \cdot h_t(x^o)\right)$$

- Votação ponderada: modelos melhores ($\alpha_t$ maior) têm mais influência
- $\text{sign}()$ retorna +1 ou -1 (a classe final)

#### 3.6.3.3 Usando Sklearn: AdaBoost e Gradient Boosting


```python
from sklearn.ensemble import AdaBoostClassifier, GradientBoostingClassifier

# =======================================================
# 1. AdaBoost
# =======================================================

ada_boost = AdaBoostClassifier(
    estimator=DecisionTreeClassifier(max_depth=1),  # Stumps
    n_estimators=50,
    learning_rate=1.0,
    random_state=42
)

ada_boost.fit(X_train, y_train)

print("="*60)
print("ADABOOST")
print("="*60)
print(f"Acurácia no teste: {ada_boost.score(X_test, y_test)*100:.2f}%")

# Pesos dos estimadores
print(f"\nPrimeiros 5 pesos dos modelos (alpha):")
print(ada_boost.estimator_weights_[:5])

# =======================================================
# 2. Gradient Boosting
# =======================================================

# Gradient Boosting é uma generalização do AdaBoost
# Em vez de ajustar pesos, ele ajusta os resíduos (erros) diretamente

gradient_boost = GradientBoostingClassifier(
    n_estimators=50,
    learning_rate=0.1,
    max_depth=3,
    random_state=42
)

gradient_boost.fit(X_train, y_train)

print("\n" + "="*60)
print("GRADIENT BOOSTING")
print("="*60)
print(f"Acurácia no teste: {gradient_boost.score(X_test, y_test)*100:.2f}%")

# Feature importance
feature_names = ['Pclass', 'Sex', 'Age']
importances = gradient_boost.feature_importances_
print("\nImportância das features:")
for name, importance in zip(feature_names, importances):
    print(f"  {name}: {importance*100:.2f}%")

# =======================================================
# 3. Comparação: Bagging vs Boosting
# =======================================================

from sklearn.ensemble import RandomForestClassifier

models = {
    'Single Tree': DecisionTreeClassifier(random_state=42),
    'Bagging (Random Forest)': RandomForestClassifier(n_estimators=50, random_state=42),
    'AdaBoost': AdaBoostClassifier(n_estimators=50, random_state=42),
    'Gradient Boosting': GradientBoostingClassifier(n_estimators=50, random_state=42)
}

print("\n" + "="*60)
print("COMPARAÇÃO DE MODELOS")
print("="*60)

for name, model in models.items():
    model.fit(X_train, y_train)
    acc = model.score(X_test, y_test)
    print(f"{name:25s}: {acc*100:.2f}%")
```

    ============================================================
    ADABOOST
    ============================================================
    Acurácia no teste: 80.45%
    
    Primeiros 5 pesos dos modelos (alpha):
    [1.31244107 0.7490842  0.26007147 0.13770149 0.0865725 ]
    
    ============================================================
    GRADIENT BOOSTING
    ============================================================
    Acurácia no teste: 79.89%
    
    Importância das features:
      Pclass: 23.10%
      Sex: 58.33%
      Age: 18.57%
    
    ============================================================
    COMPARAÇÃO DE MODELOS
    ============================================================
    Single Tree              : 77.65%
    Bagging (Random Forest)  : 79.33%
    AdaBoost                 : 80.45%
    Gradient Boosting        : 79.89%
    


```python
# =======================================================
# Parâmetros Importantes do Gradient Boosting
# =======================================================

# n_estimators: número de árvores
# learning_rate: taxa de aprendizado (shrinkage)
#   - Valores menores = mais árvores necessárias, mas melhor generalização
# max_depth: profundidade máxima de cada árvore
# subsample: fração de amostras usadas para treinar cada árvore
#   - < 1.0 = Stochastic Gradient Boosting (reduz overfitting)

configs = [
    {'n_estimators': 50, 'learning_rate': 0.1, 'max_depth': 3, 'subsample': 1.0},
    {'n_estimators': 100, 'learning_rate': 0.05, 'max_depth': 3, 'subsample': 1.0},
    {'n_estimators': 50, 'learning_rate': 0.1, 'max_depth': 5, 'subsample': 1.0},
    {'n_estimators': 100, 'learning_rate': 0.1, 'max_depth': 3, 'subsample': 0.8},
]

print("Testando diferentes configurações de Gradient Boosting:\n")
for i, config in enumerate(configs, 1):
    gb = GradientBoostingClassifier(**config, random_state=42)
    gb.fit(X_train, y_train)
    
    print(f"{i}. n_est={config['n_estimators']}, lr={config['learning_rate']}, "
          f"depth={config['max_depth']}, subsample={config['subsample']}")
    print(f"   Acurácia: {gb.score(X_test, y_test)*100:.2f}%\n")
```

    Testando diferentes configurações de Gradient Boosting:
    
    1. n_est=50, lr=0.1, depth=3, subsample=1.0
       Acurácia: 79.89%
    
    2. n_est=100, lr=0.05, depth=3, subsample=1.0
       Acurácia: 79.89%
    
    3. n_est=50, lr=0.1, depth=5, subsample=1.0
       Acurácia: 80.45%
    
    4. n_est=100, lr=0.1, depth=3, subsample=0.8
       Acurácia: 80.45%
    
    

**Dica: Learning Rate no Boosting**

O `learning_rate` (ou shrinkage) controla o quanto cada árvore contribui para a predição final.

- **learning_rate = 1.0**: Cada árvore contribui totalmente
  -  Converge rápido
  - Porém, Mais propenso a overfitting

- **learning_rate = 0.1**: Cada árvore contribui apenas 10%
  - Melhor generalização
  - Porém, Precisa de mais árvores (maior n_estimators)

**Regra:** learning_rate baixo + mais árvores = melhor performance (mas mais lento)

### 3.6.4 Stacking: Combinando Diferentes Modelos

**O que é Stacking?**

Stacking (Stacked Generalization) é como além de uma **equipe de especialistas diferentes** ter um **coordenador** que aprende a melhor forma de combinar suas opiniões.

**A Ideia:**

1. **Nível 0 (Base)**: Treinar vários modelos diferentes
   - KNN, Árvore de Decisão, Naive Bayes, SVM, etc.
   - Cada um tem suas próprias forças e fraquezas

2. **Gerar meta-features**: As previsões desses modelos base se tornam novas features

3. **Nível 1 (Meta)**: Treinar um "meta-modelo" que aprende a combinar as previsões dos modelos base
   - Geralmente um modelo simples (Regressão Logística)
   - Aprende qual modelo confiar em cada situação

**Diferença de Bagging/Boosting:**

- **Bagging/Boosting**: Múltiplos modelos do MESMO tipo (várias árvores)
- **Stacking**: Modelos DIFERENTES + meta-modelo que aprende a combiná-los

#### 3.6.4.1 Intuição do Stacking

Imagine que você está decidindo se um e-mail é spam:

**Modelos Base (Nível 0):**

1. **Naive Bayes** diz: "90% spam" 
2. **KNN** diz: "60% spam"
3. **Árvore de Decisão** diz: "80% spam" 
4. **SVM** diz: "85% spam" 
**Meta-Modelo (Nível 1):**

Em vez de simplesmente fazer a média (78.75%), o meta-modelo aprende que:

- "Quando Naive Bayes está confiante (>85%), confie nele"
- "Quando os modelos discordam muito, prefira o SVM (por quê?)"
- "Se KNN está muito diferente dos outros, ignore-o"

Resultado final: **92% spam**

Vamos entender na prática:


```python
# =======================================================
# Implementação Manual do Stacking
# =======================================================

from sklearn.model_selection import cross_val_predict
from sklearn.linear_model import LogisticRegression

# Passo 1: Definir modelos base
base_models = {
    'KNN': KNeighborsClassifier(n_neighbors=5),
    'Decision Tree': DecisionTreeClassifier(max_depth=5, random_state=42),
    'Naive Bayes': GaussianNB(),
    'Random Forest': RandomForestClassifier(n_estimators=50, random_state=42)
}

# Passo 2: Treinar modelos base e obter previsões
print("="*60)
print("NÍVEL 0: Treinando modelos base")
print("="*60)

# Armazenar previsões dos modelos base
base_predictions_train = []
base_predictions_test = []

for name, model in base_models.items():
    # Treinar no conjunto de treino
    model.fit(X_train, y_train)
    
    # Fazer previsões (probabilidades)
    # Usamos cross-validation para evitar overfitting no meta-modelo
    train_pred = cross_val_predict(
        model, X_train, y_train, cv=5, method='predict_proba'
    )[:, 1]  # Probabilidade da classe 1
    
    # Previsões no teste
    test_pred = model.predict_proba(X_test)[:, 1]
    
    base_predictions_train.append(train_pred)
    base_predictions_test.append(test_pred)
    
    acc = model.score(X_test, y_test)
    print(f"{name:20s}: {acc*100:.2f}%")

# Converter para arrays numpy
X_meta_train = np.column_stack(base_predictions_train)
X_meta_test = np.column_stack(base_predictions_test)

print(f"\nShape das meta-features:")
print(f"  Treino: {X_meta_train.shape}")
print(f"  Teste: {X_meta_test.shape}")

# Passo 3: Treinar meta-modelo
print("\n" + "="*60)
print("NÍVEL 1: Treinando meta-modelo")
print("="*60)

meta_model = LogisticRegression(random_state=42)
meta_model.fit(X_meta_train, y_train)

# Fazer previsões finais
y_pred_stacking = meta_model.predict(X_meta_test)
accuracy_stacking = accuracy_score(y_test, y_pred_stacking)

print(f"Acurácia do Stacking: {accuracy_stacking*100:.2f}%")

# Visualizar os coeficientes do meta-modelo
print("\nCoeficientes do meta-modelo (importância de cada modelo base):")
for name, coef in zip(base_models.keys(), meta_model.coef_[0]):
    print(f"  {name:20s}: {coef:.4f}")
```

    ============================================================
    NÍVEL 0: Treinando modelos base
    ============================================================
    KNN                 : 76.54%
    Decision Tree       : 78.21%
    Naive Bayes         : 75.42%
    Random Forest       : 79.33%
    
    Shape das meta-features:
      Treino: (712, 4)
      Teste: (179, 4)
    
    ============================================================
    NÍVEL 1: Treinando meta-modelo
    ============================================================
    Acurácia do Stacking: 83.24%
    
    Coeficientes do meta-modelo (importância de cada modelo base):
      KNN                 : 0.4803
      Decision Tree       : 1.7282
      Naive Bayes         : 1.2743
      Random Forest       : 1.4832
    

**DESAFIO: Como seria a visualização para o Stacking?**

#### 3.6.4.2 Formulação Formal do Stacking

**Entrada:**

1. Conjunto de treinamento: $D = \{(x^{(1)}, y^{(1)}), ..., (x^{(n)}, y^{(n)})\}$

2. Conjunto de $K$ algoritmos de nível 0 (base): $\{\mathcal{A}_1, \mathcal{A}_2, ..., \mathcal{A}_K\}$

3. Algoritmo de nível 1 (meta): $\mathcal{A}_{meta}$

**Processamento:**

**Nível 0 - Treinar Modelos Base:**

Para cada algoritmo $\mathcal{A}_k$ ($k = 1, ..., K$):

1. **Treinar modelo**: $h_k = \mathcal{A}_k(D)$

2. **Gerar meta-features** usando validação cruzada para evitar overfitting:
   - Dividir $D$ em $V$ folds
   - Para cada fold $v$:
     - Treinar $h_k$ nos outros $V-1$ folds
     - Prever no fold $v$
   - Resultado: $\tilde{h}_k(x^{(i)})$ para todo $i$ (previsões out-of-fold)

**Criar Dataset de Meta-Features:**

Para cada amostra $(x^{(i)}, y^{(i)})$:

$$x_{meta}^{(i)} = [\tilde{h}_1(x^{(i)}), \tilde{h}_2(x^{(i)}), ..., \tilde{h}_K(x^{(i)})]$$

O novo dataset meta é: $D_{meta} = \{(x_{meta}^{(1)}, y^{(1)}), ..., (x_{meta}^{(n)}, y^{(n)})\}$

**Nível 1 - Treinar Meta-Modelo:**

$$h_{meta} = \mathcal{A}_{meta}(D_{meta})$$

**Saída - Predição:**

Para uma nova amostra $x^o$:

1. **Obter previsões dos modelos base**:
   
   $$x_{meta}^o = [h_1(x^o), h_2(x^o), ..., h_K(x^o)]$$

2. **Aplicar meta-modelo**:
   
   $$\hat{y} = h_{meta}(x_{meta}^o)$$

**Variações Importantes:**

1. **Features Originais no Meta-Modelo**: 
   - Em vez de usar apenas as previsões dos modelos base, podemos concatenar com as features originais:
   
   $$x_{meta}^{(i)} = [x^{(i)}, \tilde{h}_1(x^{(i)}), ..., \tilde{h}_K(x^{(i)})]$$

2. **Multi-Level Stacking**:
   - Podemos ter múltiplos níveis: Nível 0 → Nível 1 → Nível 2 → ...
   - Cada nível usa as previsões do nível anterior como features

#### 3.6.4.3 Usando Sklearn: StackingClassifier


```python
from sklearn.ensemble import StackingClassifier
from sklearn.svm import SVC

# =======================================================
# 1. Stacking Básico
# =======================================================

# Definir modelos base
estimators = [
    ('knn', KNeighborsClassifier(n_neighbors=5)),
    ('tree', DecisionTreeClassifier(max_depth=5, random_state=42)),
    ('nb', GaussianNB()),
    ('rf', RandomForestClassifier(n_estimators=50, random_state=42))
]

# Criar stacking com Regressão Logística como meta-modelo
stacking = StackingClassifier(
    estimators=estimators,
    final_estimator=LogisticRegression(),
    cv=5  # Validação cruzada para gerar meta-features
)

stacking.fit(X_train, y_train)

print("="*60)
print("STACKING CLASSIFIER (sklearn)")
print("="*60)
print(f"Acurácia: {stacking.score(X_test, y_test)*100:.2f}%")

# =======================================================
# 2. Stacking com passthrough (features originais)
# =======================================================

# passthrough=True adiciona as features originais ao meta-modelo
stacking_passthrough = StackingClassifier(
    estimators=estimators,
    final_estimator=LogisticRegression(),
    cv=5,
    passthrough=True  # Incluir features originais
)

stacking_passthrough.fit(X_train, y_train)

print("\n" + "="*60)
print("STACKING COM PASSTHROUGH")
print("="*60)
print(f"Acurácia: {stacking_passthrough.score(X_test, y_test)*100:.2f}%")

# =======================================================
# 3. Diferentes meta-modelos
# =======================================================

meta_models = {
    'Logistic Regression': LogisticRegression(),
    'Random Forest': RandomForestClassifier(n_estimators=50, random_state=42),
    'Gradient Boosting': GradientBoostingClassifier(n_estimators=50, random_state=42),
    'SVM': SVC(kernel='rbf', probability=True, random_state=42)
}

print("\n" + "="*60)
print("TESTANDO DIFERENTES META-MODELOS")
print("="*60)

for name, meta_model in meta_models.items():
    stack = StackingClassifier(
        estimators=estimators,
        final_estimator=meta_model,
        cv=5
    )
    stack.fit(X_train, y_train)
    acc = stack.score(X_test, y_test)
    print(f"{name:25s}: {acc*100:.2f}%")
```

    ============================================================
    STACKING CLASSIFIER (sklearn)
    ============================================================
    Acurácia: 83.24%
    
    ============================================================
    STACKING COM PASSTHROUGH
    ============================================================
    Acurácia: 83.24%
    
    ============================================================
    TESTANDO DIFERENTES META-MODELOS
    ============================================================
    Logistic Regression      : 83.24%
    Random Forest            : 78.21%
    Gradient Boosting        : 78.21%
    SVM                      : 82.12%
    

**Dica: Escolhendo Modelos Base para Stacking**

Para um bom Stacking, escolha modelos **diversos**:

**Bons para Stacking:**
- Modelos com princípios diferentes (KNN + Árvore + Naive Bayes)
- Modelos lineares + não-lineares
- Modelos que cometem erros diferentes

**Ruins para Stacking:**
- Múltiplas variações do mesmo modelo (3 árvores de decisão diferentes)
- Modelos muito correlacionados
- Modelos que sempre concordam

*Se os modelos base sempre preveem a mesma coisa, o stacking não ajuda*

#### 3.6.4.4 Desafio: Criar um Ensemble Híbrido

Agora é sua vez! Combine Bagging, Boosting e Stacking em um único ensemble.

**Objetivo:** Criar um StackingClassifier onde os modelos base sejam ensembles!

**Estrutura sugerida:**

Nível 0 (Modelos Base):
1. Random Forest (Bagging)
2. Gradient Boosting (Boosting)
3. AdaBoost (Boosting)
4. Bagging com SVM

Nível 1 (Meta-modelo):
- Você escolhe!

**Desafio Extra:** Implemente validação cruzada e compare com todos os modelos individuais.


```python
# =======================================================
# SEU CÓDIGO AQUI!
# =======================================================

# Dica: Use StackingClassifier com estimators que sejam
# BaggingClassifier, RandomForestClassifier, AdaBoostClassifier, etc.

# Exemplo de estrutura:
# hybrid_ensemble = StackingClassifier(
#     estimators=[
#         ('rf', RandomForestClassifier(...)),
#         ('gb', GradientBoostingClassifier(...)),
#         ('ada', AdaBoostClassifier(...)),
#         ('bag_svm', BaggingClassifier(SVC(...), ...))
#     ],
#     final_estimator=...
# )

pass
```

### 3.6.5 Comparação: Bagging vs Boosting vs Stacking


```python
# =======================================================
# Idéia:
# - Comparamos todos os modelos (single tree, bagging, boosting, stacking)
# - Medimos tempo de treino, acurácia no teste, cross-validation score
# - Analisamos a importância de cada modelo no ensemble

# =======================================================

import time
from sklearn.model_selection import cross_val_score

# Definir todos os modelos para comparação
models_comparison = {
    # Baseline
    'Decision Tree (baseline)': DecisionTreeClassifier(random_state=42),
    
    # Bagging
    'Bagging (Decision Tree)': BaggingClassifier(
        estimator=DecisionTreeClassifier(),
        n_estimators=50,
        random_state=42
    ),
    'Random Forest': RandomForestClassifier(
        n_estimators=50,
        random_state=42
    ),
    
    # Boosting
    'AdaBoost': AdaBoostClassifier(
        n_estimators=50,
        random_state=42
    ),
    'Gradient Boosting': GradientBoostingClassifier(
        n_estimators=50,
        random_state=42
    ),
    
    # Stacking
    'Stacking': StackingClassifier(
        estimators=[
            ('knn', KNeighborsClassifier(n_neighbors=5)),
            ('tree', DecisionTreeClassifier(max_depth=5, random_state=42)),
            ('nb', GaussianNB()),
            ('rf', RandomForestClassifier(n_estimators=30, random_state=42))
        ],
        final_estimator=LogisticRegression(),
        cv=5
    )
}

# Avaliar todos os modelos
results = []

print("="*80)
print("COMPARAÇÃO COMPLETA DE ENSEMBLE METHODS")
print("="*80)
print(f"{'Modelo':<30} {'Acurácia Teste':<15} {'CV Score (mean)':<20} {'Tempo (s)':<10}")
print("-"*80)

for name, model in models_comparison.items():
    # Medir tempo de treino
    start_time = time.time()
    
    # Treinar
    model.fit(X_train, y_train)
    
    # Acurácia no teste
    test_acc = model.score(X_test, y_test)
    
    # Cross-validation score
    cv_scores = cross_val_score(model, X_train, y_train, cv=5)
    cv_mean = cv_scores.mean()
    cv_std = cv_scores.std()
    
    # Tempo
    elapsed_time = time.time() - start_time
    
    results.append({
        'name': name,
        'test_acc': test_acc,
        'cv_mean': cv_mean,
        'cv_std': cv_std,
        'time': elapsed_time
    })
    
    print(f"{name:<30} {test_acc*100:>6.2f}%        {cv_mean*100:>6.2f}% ± {cv_std*100:>4.2f}%    {elapsed_time:>6.2f}s")

print("-"*80)
```

    ================================================================================
    COMPARAÇÃO COMPLETA DE ENSEMBLE METHODS
    ================================================================================
    Modelo                         Acurácia Teste  CV Score (mean)      Tempo (s) 
    --------------------------------------------------------------------------------
    Decision Tree (baseline)        77.65%         78.93% ± 1.48%      0.04s
    Bagging (Decision Tree)         78.77%         78.51% ± 0.57%      0.90s
    Random Forest                   79.33%         79.07% ± 2.14%      0.59s
    AdaBoost                        80.45%         79.91% ± 2.96%      0.61s
    Gradient Boosting               79.89%         79.63% ± 1.89%      0.48s
    Stacking                        82.68%         80.89% ± 2.68%      2.83s
    --------------------------------------------------------------------------------
    

### 3.6.6 Conclusões e Considerações

Agora que exploramos os três principais métodos de ensemble

#### **Comparando**

| Aspecto | Bagging | Boosting | Stacking |
|---------|---------|----------|----------|
| **Paralelização** | Modelos treinados em paralelo | Modelos treinados sequencialmente | Nível 0 em paralelo, Nível 1 depois |
| **Diversidade** | Amostras bootstrap diferentes | Foco em erros diferentes | Algoritmos diferentes |
| **Objetivo Principal** | Reduzir **variância** | Reduzir **bias** e **variância** | Combinar **diferentes perspectivas** |
| **Modelos Base** | Geralmente modelos complexos (high variance) | Geralmente modelos simples (high bias) | Modelos diversos |
| **Risco de Overfitting** | Baixo | Médio-Alto (se não regularizado) | Médio |
| **Interpretabilidade** | Baixa | Baixa | Muito baixa |
| **Velocidade** | Rápido (paralelo) | Lento (sequencial) | Médio |
| **Mais usados** | Random Forest, BaggingClassifier | AdaBoost, Gradient Boosting, XGBoost | StackingClassifier |

#### **Quando usar cada um?**

**Bagging (Random Forest):**
-  Quando você tem modelos com **alta variância** (ex: árvores profundas)
-  Quando você quer **reduzir overfitting**
-  Quando você tem **recursos computacionais para paralelização**
-  Dataset grande com features redundantes
- **Exemplo**: Classificação de imagens, detecção de fraude

**Boosting (Gradient Boosting, AdaBoost):**
-  Quando você precisa de **máxima acurácia** (geralmente o melhor desempenho)
-  Quando você tem modelos com **alto bias** (ex: stumps)
-  Quando você pode **ajustar cuidadosamente os hiperparâmetros**
-  Cuidado com overfitting em datasets pequenos
-  **Exemplo**: Competições de ML (Kaggle), ranking de busca

**Stacking:**
-  Quando você quer **combinar modelos fundamentalmente diferentes**
-  Quando você já tem **vários modelos bons** e quer espremer mais performance
-  Em **competições** onde cada 0.1% de acurácia importa
-  Mais complexo de implementar e manter
-  **Exemplo**: Sistemas de recomendação, previsão de séries temporais

#### **Considerações**

**1. Interpretabilidade:**

Todos os métodos de ensemble reduzem a interpretabilidade:
- Um modelo único é mais fácil de explicar
- Ensembles são "caixas-pretas"
- Use **feature importance** para ter alguma interpretação

**2. Hiperparâmetros Críticos:**

**Bagging:**
- `n_estimators`: Quantos modelos (mais = melhor, mas com retorno decrescente)
- `max_samples`: Tamanho das amostras bootstrap
- `max_features`: Features aleatórias (para Random Forest)

**Boosting:**
- `n_estimators`: Número de modelos (cuidado com overfitting)
- `learning_rate`: Taxa de aprendizado (menor = mais modelos necessários)
- `max_depth`: Profundidade das árvores (geralmente shallow)

**Stacking:**
- Escolha dos **modelos base** (diversidade é chave!)
- Escolha do **meta-modelo** (geralmente simples: LogisticRegression)
- `cv`: Número de folds (importante para evitar overfitting)

#### **Dicas**

**Comece simples**: Random Forest é geralmente uma ótima escolha inicial
- Robusto, fácil de usar, bom desempenho out-of-the-box

**Para máxima performance**: Gradient Boosting (ou XGBoost/LightGBM)
- Mas requer mais tuning de hiperparâmetros

**Compute vs Accuracy**:
- Bagging: Pode ser paralelizado → rápido
- Boosting: Sequencial → mais lento
- Stacking: Overhead adicional → mais lento ainda

**Evite ensembles de ensembles (em produção)**:
- Stacking de Boosting pode dar overfitting
- Complexidade de manutenção explode
- Trade-off entre 0.5% de acurácia vs simplicidade

#### **Aplicações no Mundo Real**

1. **Detecção de Spam**: Random Forest ou Gradient Boosting
2. **Diagnóstico Médico**: Stacking 
3. **Previsão de Churn**: Gradient Boosting (maximiza acurácia)
4. **Sistemas de Recomendação**: Stacking (combine collaborative filtering + content-based)
5. **Detecção de Fraude**: Random Forest (lidar com desbalanceamento)

#### **Nota:**

Bibliotecas para se aprofundar mais:

- **[XGBoost](https://xgboost.readthedocs.io/en/stable/)**: Gradient Boosting extremamente otimizado
- **[LightGBM](https://lightgbm.readthedocs.io/en/stable/Python-Intro.html)**: Gradient Boosting ainda mais rápido (da Microsoft)
- **[CatBoost](https://catboost.ai/docs/en/concepts/python-installation)**: Gradient Boosting para features categóricas (da Yandex)
- **[VotingClassifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.VotingClassifier.html)**: Ensemble simples por votação (sklearn)

Todos são variações~melhorias dos métodos que estudamos

# **4. Modelos para Problemas de Regressão**

## **4.1 Regressão Linear Múltipla**

### **Introdução ao Problema (Regressão Linear Múltipla)**

Imagine que você é um corretor de imóveis iniciante e sua gerente, a Sra. Ana, uma avaliadora experiente, consegue estimar o preço de uma casa apenas olhando para algumas de suas características. Você, por outro lado, se sente um pouco perdido. Como ela faz isso?

Você pergunta a ela, e a Sra. Ana responde: "É uma questão de entender o impacto de cada característica. Um quarto a mais não adiciona um valor fixo; o impacto dele depende da área total da casa. A localização, o número de banheiros, a idade do imóvel... tudo isso contribui para o preço final, e meu trabalho é ponderar a importância de cada um desses fatores."

E como podemos criar um modelo que aprenda essas ponderações a partir de dados históricos? E se, em vez de depender apenas da intuição, pudéssemos usar a matemática para encontrar a 'receita' exata que combina essas características para chegar ao preço mais provável?

É exatamente esse o problema que a **Regressão Linear Múltipla** se propõe a resolver. Ela nos ajuda a entender e quantificar a relação entre **duas ou mais variáveis independentes** (nossos 'ingredientes', como área, quartos, etc.) e uma **variável dependente** contínua (nosso 'resultado', o preço da casa).

**Diferença importante:** Nos algoritmos anteriores (KNN, SVM, etc.), trabalhamos com **classificação** - prever categorias discretas (ex: "Setosa", "Versicolor", "Virginica" ou "Sobreviveu/Não Sobreviveu"). Agora, estamos lidando com **regressão** - prever valores contínuos (ex: preço de R$ 250.000, R$ 380.000, etc.).

### **Intuição**

A Regressão Linear Múltipla expande a ideia da regressão linear simples. Se na regressão simples tentamos encontrar a **melhor linha** que descreve a relação entre *uma* variável de entrada e a saída, na regressão múltipla, tentamos encontrar o **melhor 'plano' ou 'hiperplano'** que descreve a relação entre *múltiplas* variáveis de entrada e a saída.

Pense na 'receita de bolo' da Sra. Ana para precificar uma casa. A receita dela pode ser algo como:

**Preço Estimado = (Preço Base) + (Valor por m² × Área) + (Valor por Quarto × N° de Quartos) - (Depreciação por Ano × Idade do Imóvel)**

O que a Regressão Linear Múltipla faz é exatamente encontrar os valores para 'Preço Base', 'Valor por m²', 'Valor por Quarto' e 'Depreciação por Ano'. Esses valores são os **coeficientes** (ou pesos) do nosso modelo. Cada coeficiente nos diz o seguinte:

> *Mantendo todas as outras características constantes, qual é o impacto médio de se adicionar uma unidade desta característica no resultado final?*

Por exemplo, se o 'Valor por Quarto' for R$ 50.000, isso significa que, para casas com a mesma área e idade, adicionar um quarto extra tende a aumentar o preço em R$ 50.000, em média.

Seguindo na mesma lógica do módulo 3

Desta vez, vamos trabalhar com o dataset **[California Housing](https://scikit-learn.org/stable/datasets/real_world.html#california-housing-dataset)** - dados reais de preços de casas na Califórnia. Queremos prever o preço médio de uma casa com base em características como:

- **MedInc**: Renda média da região
- **HouseAge**: Idade média das casas
- **AveRooms**: Número médio de cômodos
- **AveBedrms**: Número médio de quartos
- **Population**: População da região
- **AveOccup**: Média de ocupantes por casa
- **Latitude** e **Longitude**: Localização geográfica

Pergunta: **Qual será o preço de uma casa com essas características específicas?**


```python
# =======================================================
# IMPORTANDO AS BIBLIOTECAS
# =======================================================

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.datasets import fetch_california_housing
from sklearn.model_selection import train_test_split

```


```python
# CARREGANDO O CALIFORNIA HOUSING DATASET
housing = fetch_california_housing()

X = housing.data  # Features: 8 características das casas
y = housing.target  # Target: Preço médio (em centenas de milhares de dólares)

print("Dataset California Housing:")
print(f"Número de amostras: {X.shape[0]}")
print(f"Número de features: {X.shape[1]}")
print("=" * 50)

print("\nFeatures:")
for i, nome in enumerate(housing.feature_names):
    print(f"{i+1}. {nome}")
print("=" * 50)

print("\nVisualizando os dados:")
df = pd.DataFrame(X, columns=housing.feature_names)
df['Price'] = y
print(df.head())
print("\nEstatísticas descritivas:")
print(df.describe())
```

    Dataset California Housing:
    Número de amostras: 20640
    Número de features: 8
    ==================================================
    
    Features:
    1. MedInc
    2. HouseAge
    3. AveRooms
    4. AveBedrms
    5. Population
    6. AveOccup
    7. Latitude
    8. Longitude
    ==================================================
    
    Visualizando os dados:
       MedInc  HouseAge  AveRooms  AveBedrms  Population  AveOccup  Latitude  \
    0  8.3252      41.0  6.984127   1.023810       322.0  2.555556     37.88   
    1  8.3014      21.0  6.238137   0.971880      2401.0  2.109842     37.86   
    2  7.2574      52.0  8.288136   1.073446       496.0  2.802260     37.85   
    3  5.6431      52.0  5.817352   1.073059       558.0  2.547945     37.85   
    4  3.8462      52.0  6.281853   1.081081       565.0  2.181467     37.85   
    
       Longitude  Price  
    0    -122.23  4.526  
    1    -122.22  3.585  
    2    -122.24  3.521  
    3    -122.25  3.413  
    4    -122.25  3.422  
    
    Estatísticas descritivas:
                 MedInc      HouseAge      AveRooms     AveBedrms    Population  \
    count  20640.000000  20640.000000  20640.000000  20640.000000  20640.000000   
    mean       3.870671     28.639486      5.429000      1.096675   1425.476744   
    std        1.899822     12.585558      2.474173      0.473911   1132.462122   
    min        0.499900      1.000000      0.846154      0.333333      3.000000   
    25%        2.563400     18.000000      4.440716      1.006079    787.000000   
    50%        3.534800     29.000000      5.229129      1.048780   1166.000000   
    75%        4.743250     37.000000      6.052381      1.099526   1725.000000   
    max       15.000100     52.000000    141.909091     34.066667  35682.000000   
    
               AveOccup      Latitude     Longitude         Price  
    count  20640.000000  20640.000000  20640.000000  20640.000000  
    mean       3.070655     35.631861   -119.569704      2.068558  
    std       10.386050      2.135952      2.003532      1.153956  
    min        0.692308     32.540000   -124.350000      0.149990  
    25%        2.429741     33.930000   -121.800000      1.196000  
    50%        2.818116     34.260000   -118.490000      1.797000  
    75%        3.282261     37.710000   -118.010000      2.647250  
    max     1243.333333     41.950000   -114.310000      5.000010  
       MedInc  HouseAge  AveRooms  AveBedrms  Population  AveOccup  Latitude  \
    0  8.3252      41.0  6.984127   1.023810       322.0  2.555556     37.88   
    1  8.3014      21.0  6.238137   0.971880      2401.0  2.109842     37.86   
    2  7.2574      52.0  8.288136   1.073446       496.0  2.802260     37.85   
    3  5.6431      52.0  5.817352   1.073059       558.0  2.547945     37.85   
    4  3.8462      52.0  6.281853   1.081081       565.0  2.181467     37.85   
    
       Longitude  Price  
    0    -122.23  4.526  
    1    -122.22  3.585  
    2    -122.24  3.521  
    3    -122.25  3.413  
    4    -122.25  3.422  
    
    Estatísticas descritivas:
                 MedInc      HouseAge      AveRooms     AveBedrms    Population  \
    count  20640.000000  20640.000000  20640.000000  20640.000000  20640.000000   
    mean       3.870671     28.639486      5.429000      1.096675   1425.476744   
    std        1.899822     12.585558      2.474173      0.473911   1132.462122   
    min        0.499900      1.000000      0.846154      0.333333      3.000000   
    25%        2.563400     18.000000      4.440716      1.006079    787.000000   
    50%        3.534800     29.000000      5.229129      1.048780   1166.000000   
    75%        4.743250     37.000000      6.052381      1.099526   1725.000000   
    max       15.000100     52.000000    141.909091     34.066667  35682.000000   
    
               AveOccup      Latitude     Longitude         Price  
    count  20640.000000  20640.000000  20640.000000  20640.000000  
    mean       3.070655     35.631861   -119.569704      2.068558  
    std       10.386050      2.135952      2.003532      1.153956  
    min        0.692308     32.540000   -124.350000      0.149990  
    25%        2.429741     33.930000   -121.800000      1.196000  
    50%        2.818116     34.260000   -118.490000      1.797000  
    75%        3.282261     37.710000   -118.010000      2.647250  
    max     1243.333333     41.950000   -114.310000      5.000010  
    


```python
# Vou simplificar para 3 features
# Seleciono as features mais correlacionadas com o preço

features = ['MedInc', 'AveRooms', 'HouseAge']
indices = [0, 2, 1]  # Índices dessas features no array original

X_simples = X[:, indices]
```


```python
# Criando um exemplo: uma casa específica para prever o preço
nova_casa = np.array([5.0, 6.0, 15.0])  # MedInc=5.0, AveRooms=6.0, HouseAge=15.0

print("Nossa casa para avaliação:")
print(f"  Renda média da região: ${nova_casa[0] * 10000:.0f}")
print(f"  Número médio de cômodos: {nova_casa[1]:.1f}")
print(f"  Idade média das casas: {nova_casa[2]:.0f} anos")
print("\nQual será o preço estimado?")
```

    Nossa casa para avaliação:
      Renda média da região: $50000
      Número médio de cômodos: 6.0
      Idade média das casas: 15 anos
    
    Qual será o preço estimado?
    


```python
# Visualizando a relação entre features e preço
fig, axes = plt.subplots(1, 3, figsize=(18, 4))
fig.suptitle("Relação entre Features e Preço das Casas", fontsize=16, fontweight='bold')

for i, (ax, feature) in enumerate(zip(axes, features)):
    # Amostragem para melhor visualização
    sample_indices = np.random.choice(X.shape[0], 1000, replace=False)
    
    ax.scatter(X_simples[sample_indices, i], y[sample_indices], 
               alpha=0.5, s=20, c=y[sample_indices], cmap='viridis')
    ax.set_xlabel(feature, fontsize=12)
    ax.set_ylabel("Preço (x$100k)", fontsize=12)
    ax.set_title(f"{feature} vs Preço")
    ax.grid(alpha=0.3)

plt.tight_layout()
plt.show()
```


    
![png](case_ia_files/case_ia_387_0.png)
    


#### **Como funciona a Regressão Linear Múltipla?**

**1. A Equação Linear**

O modelo cria uma equação que combina todas as features:

$$\text{Preço} = \beta_0 + \beta_1 \times \text{MedInc} + \beta_2 \times \text{AveRooms} + \beta_3 \times \text{HouseAge}$$

Onde:
- $\beta_0$ é o **intercepto** (preço base)
- $\beta_1, \beta_2, \beta_3$ são os **coeficientes** (peso de cada feature)

**2. Encontrando os Melhores Coeficientes**

O algoritmo tenta encontrar os valores de $\beta$ que minimizam o **erro quadrático médio** (MSE):

$$\text{MSE} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2$$

Onde:
- $y_i$ é o preço real
- $\hat{y}_i$ é o preço previsto
- $n$ é o número de amostras

**3. Interpretação dos Coeficientes**

Cada coeficiente nos diz: "Se eu aumentar essa feature em 1 unidade (mantendo todas as outras constantes), quanto o preço vai mudar?"

- Se $\beta_1 = 40.000$: Aumentar a renda média em 1 unidade aumenta o preço em $40k
- Se $\beta_3 = -2.000$: Cada ano a mais de idade diminui o preço em $2k


```python
# Vamos treinar um modelo simples para ver os coeficientes
from sklearn.linear_model import LinearRegression

X_train, X_test, y_train, y_test = train_test_split(
    X_simples, y, test_size=0.2, random_state=42
)

# Treinar o modelo
modelo = LinearRegression()
modelo.fit(X_train, y_train)

# Coeficientes
print("Coeficientes do modelo:")
print(f"Intercepto (β₀): ${modelo.intercept_ * 100000:.2f}")
print()
for nome, coef in zip(features, modelo.coef_):
    print(f"  {nome} (β): ${coef * 100000:.2f}")
    print(f"    - Aumentar {nome} em 1 unidade muda o preço em ${abs(coef * 100000):.2f}")
    print()

# Fazer previsão para nossa casa
preco_previsto = modelo.predict([nova_casa])[0]
print("=" * 60)
print(f"Preço estimado para nossa casa: ${preco_previsto * 100000:.2f}")
print("=" * 60)


```

    Coeficientes do modelo:
    Intercepto (β₀): $1729.56
    
      MedInc (β): $44475.78
        - Aumentar MedInc em 1 unidade muda o preço em $44475.78
    
      AveRooms (β): $-2814.97
        - Aumentar AveRooms em 1 unidade muda o preço em $2814.97
    
      HouseAge (β): $1683.62
        - Aumentar HouseAge em 1 unidade muda o preço em $1683.62
    
    ============================================================
    Preço estimado para nossa casa: $232473.00
    ============================================================
    

**Desafio: Parece contraintuitivo que a aumentar a quantidade de quartos diminua o preço da casa, levante hipóteses do porque isso está acontecendo**


```python
# Visualização: Valores reais vs Previstos
y_pred = modelo.predict(X_test)

plt.figure(figsize=(10, 6))
plt.scatter(y_test, y_pred, alpha=0.5, s=20)
plt.plot([y_test.min(), y_test.max()], [y_test.min(), y_test.max()], 
         'r--', lw=2, label='Previsão Perfeita')
plt.xlabel("Preço Real (x$100k)", fontsize=12)
plt.ylabel("Preço Previsto (x$100k)", fontsize=12)
plt.title("Preços Reais vs Previstos - Regressão Linear Múltipla", 
          fontsize=14, fontweight='bold')
plt.legend()
plt.grid(alpha=0.3)
plt.tight_layout()
plt.show()

# Calcular métricas de desempenho
from sklearn.metrics import mean_squared_error, r2_score, mean_absolute_error

mse = mean_squared_error(y_test, y_pred)
rmse = np.sqrt(mse)
mae = mean_absolute_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

print("Métricas de Desempenho:")
print(f"  MSE (Erro Quadrático Médio): {mse:.4f}")
print(f"  RMSE (Raiz do MSE): {rmse:.4f} (≈ ${rmse * 100000:.2f})")
print(f"  MAE (Erro Absoluto Médio): {mae:.4f} (≈ ${mae * 100000:.2f})")
print(f"  R² (Coeficiente de Determinação): {r2:.4f}")
print()
print("Interpretação do R²:")
print(f"  O modelo explica {r2*100:.2f}% da variação nos preços das casas")
```


    
![png](case_ia_files/case_ia_391_0.png)
    


    Métricas de Desempenho:
      MSE (Erro Quadrático Médio): 0.6589
      RMSE (Raiz do MSE): 0.8117 (≈ $81173.32)
      MAE (Erro Absoluto Médio): 0.6033 (≈ $60332.14)
      R² (Coeficiente de Determinação): 0.4972
    
    Interpretação do R²:
      O modelo explica 49.72% da variação nos preços das casas
    

### **Formulação Formal**

**Modelo Matemático**

Dado um conjunto de dados com $n$ amostras e $p$ features, a regressão linear múltipla modela a relação entre as variáveis independentes $X$ e a variável dependente $y$ através da equação:

$$y_i = \beta_0 + \beta_1 x_{i1} + \beta_2 x_{i2} + ... + \beta_p x_{ip} + \epsilon_i$$

Ou em forma vetorial:

$$y = X\beta + \epsilon$$

Onde:
- $y$ é o vetor de valores observados (target)
- $X$ é a matriz de features ($n \times p$)
- $\beta$ é o vetor de coeficientes ($p \times 1$)
- $\epsilon$ é o vetor de erros (resíduos)

**Objetivo: Método dos Mínimos Quadrados**

Encontrar $\beta$ que minimize a soma dos quadrados dos resíduos (SSR):

$$\text{SSR} = \sum_{i=1}^{n} (y_i - \hat{y}_i)^2 = \sum_{i=1}^{n} (y_i - \beta_0 - \sum_{j=1}^{p} \beta_j x_{ij})^2$$

Ou em forma matricial:

$$\text{SSR} = (y - X\beta)^T(y - X\beta)$$

**Solução Analítica (Equação Normal)**

A solução que minimiza SSR é:

$$\hat{\beta} = (X^TX)^{-1}X^Ty$$

Esta é a **Equação Normal** - a solução de forma fechada para regressão linear.

**Premissas do Modelo**

1. **Linearidade**: A relação entre X e y é linear
2. **Independência**: As observações são independentes
3. **Homocedasticidade**: A variância dos erros é constante
4. **Normalidade**: Os erros seguem distribuição normal
5. **Não-colinearidade**: As features não são altamente correlacionadas entre si

**Revisando Métricas de Avaliação**

Para problemas de regressão, usamos métricas diferentes das de classificação:

**1. MSE (Mean Squared Error)**

$$\text{MSE} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2$$

Penaliza erros grandes mais fortemente (devido ao quadrado).

**2. RMSE (Root Mean Squared Error)**

$$\text{RMSE} = \sqrt{\text{MSE}}$$

Tem a mesma unidade que a variável target (mais interpretável).

**3. MAE (Mean Absolute Error)**

$$\text{MAE} = \frac{1}{n} \sum_{i=1}^{n} |y_i - \hat{y}_i|$$

Menos sensível a outliers que o MSE.

**4. R² (Coeficiente de Determinação)**

$$R^2 = 1 - \frac{\sum_{i=1}^{n} (y_i - \hat{y}_i)^2}{\sum_{i=1}^{n} (y_i - \bar{y})^2}$$

Indica a proporção da variância explicada pelo modelo (0 a 1).
- $R^2 = 1$: Modelo perfeito
- $R^2 = 0$: Modelo não melhor que a média

### **Grande Desafio: "From Scratch"**

Agora que você entende como funciona a Regressão Linear Múltipla, tente implementar o algoritmo do zero, usando apenas NumPy! 


```python
class RegressaoLinearMultipla:
    def __init__(self):
        """
        Inicializa o modelo de Regressão Linear Múltipla
        """
        self.coef_ = None  # Coeficientes β
        self.intercept_ = None  # Intercepto β₀
    
    def fit(self, X, y):
        """
        Treina o modelo usando a Equação Normal
        
        Parâmetros:
        X (array-like): Matriz de features (n_samples, n_features)
        y (array-like): Vetor target (n_samples,)
        """
        # Adicionar coluna de 1s para o intercepto
        # X_b = [1, x1, x2, ..., xp]
        
        # Aplicar a Equação Normal: β = (X^T X)^(-1) X^T y
        
        # Separar intercepto dos coeficientes
        
        pass
    
    def predict(self, X):
        """
        Faz previsões para novos dados
        
        Parâmetros:
        X (array-like): Matriz de features (n_samples, n_features)
        
        Retorna:
        array: Previsões (n_samples,)
        """
        # y_pred = β₀ + β₁x₁ + β₂x₂ + ... + βₚxₚ
        
        pass
    
    def score(self, X, y):
        """
        Calcula o R² (coeficiente de determinação)
        
        Parâmetros:
        X (array-like): Matriz de features
        y (array-like): Vetor target verdadeiro
        
        Retorna:
        float: R² score
        """
        # R² = 1 - (SS_res / SS_tot)
        # SS_res = Σ(y_i - ŷ_i)²
        # SS_tot = Σ(y_i - ȳ)²
        
        pass
    
    def mean_squared_error(self, y_true, y_pred):
        """
        Calcula o MSE
        
        Parâmetros:
        y_true (array-like): Valores verdadeiros
        y_pred (array-like): Valores previstos
        
        Retorna:
        float: MSE
        """
        # MSE = (1/n) Σ(y_i - ŷ_i)²
        
        pass
```


```python
# Dados para Teste (California Housing - simplificado)
from sklearn.datasets import fetch_california_housing
from sklearn.model_selection import train_test_split

housing = fetch_california_housing()
X = housing.data[:, [0, 2, 1]]  # MedInc, AveRooms, HouseAge
y = housing.target

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

print("Dados carregados!")
print(f"Tamanho do treino: {X_train.shape[0]} amostras")
print(f"Tamanho do teste: {X_test.shape[0]} amostras")
```

### **Usando Scikit-learn**

## **4.2 Support Vector Regression (SVR)**



A Support Vector Regression (SVR) aplica os princípios das Máquinas de Vetores de Suporte para prever valores contínuos. Em vez de procurar um hiperplano que separa classes com margem máxima, o SVR busca uma função que:

1. Seja a mais **“plana”** possível (minimiza ||w||²).
2. Mantenha a maioria dos pontos **dentro de um tubo de espessura ε** (epsilon-insensitive zone).
3. Penalize somente os pontos que ultrapassam essa margem (erros > ε) via folgas (ξ, ξ*).

Vamos construir a intuição, visualizar, formalizar, implementar (desafio) e usar o sklearn.

Recapitulando rapidamente o SVM de classificação:

- **Hiperplano**: Fronteira de decisão que separa as classes no espaço de features.
- **Margem**: Distância entre o hiperplano e os pontos mais próximos de cada classe (maximizada no SVM).
- **Vetores de suporte**: Pontos que definem a margem e são críticos para posicionar o hiperplano.

![](https://www.researchgate.net/publication/359343222/figure/fig1/AS:1182277103042573@1658888235641/SVM-and-SVR-modeling-In-SVM-left-a-hyperplane-with-maximal-margin-is-constructed-to.png?fit=600%)

Para regressão, não queremos separar classes — queremos ajustar uma função $f(x)$ que aproxima $y$.

Em vez de como na regressão linear, minimizar o erro quadrático diretamente, o SVR ignora erros pequenos. Se $|y - f(x)| \le \epsilon$, consideramos "bom o suficiente" e o custo é zero. Só quando $|y - f(x)| > \epsilon$ ativamos uma penalização.

**Hiperparâmetros:**

- **ε (epsilon)**: Largura da zona de tolerância (quanto erro é aceitável sem penalização).
    - **ε muito pequeno** >> muitos pontos fora, terá mais vetores de suporte (overfitting).
    - **ε muito grande** >> quase nenhum ponto fora (underfitting).

- **C**: Penalidade para erros fora do tubo (trade-off entre viés e variância).
    - **C alto** >> prioriza ajuste (mais complexidade).
    - **C baixo** >> prioriza suavidade (mais generalização).

- **Kernel**: Mapeia dados para espaço de maior dimensão, podendo ser linear ou não linear (RBF, Polinomial)

### Introdução

Vamos criar dois cenários para analisar o impacto de C, $\epsilon$ e kernel:
1. Dataset linear (pelo menos quase).
2. Dataset não linear (seno).

Além das métricas padrões (MSE, RMSE, MAE, R²), é legal utilizar o número de vetores de suporte como métrica de complixidade


```python
# =======================================================
# IMPORTANDO AS BIBLIOTECAS
# =======================================================

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.datasets import make_regression
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error, mean_absolute_error, r2_score
from math import sqrt
```


```python
# =======================================================
# DATASETS (Linear e Não Linear)
# =======================================================

# 1. Dataset Linear
X_lin, y_lin = make_regression(n_samples=400, n_features=1, noise=12, random_state=42)
y_lin = y_lin / 100  # escala mais comportada

# 2. Dataset Não Linear (seno)
X_non = np.linspace(-3, 3, 400).reshape(-1, 1)
np.random.seed(42)
y_non = np.sin(X_non[:, 0]) + np.random.normal(0, 0.15, size=X_non.shape[0])
```


```python
# =======================================================
# VISUALIZAÇÃO INICIAL
# =======================================================

fig, axes = plt.subplots(1, 2, figsize=(12,4))
axes[0].scatter(X_lin, y_lin, s=15, alpha=0.6)
axes[0].set_title('Dataset Linear')
axes[0].set_xlabel('X')
axes[0].set_ylabel('y')

axes[1].scatter(X_non, y_non, s=15, alpha=0.6, c='tab:orange')
axes[1].set_title('Dataset Não Linear (seno + ruído)')
axes[1].set_xlabel('X')
axes[1].set_ylabel('y')
plt.tight_layout()
plt.show()
```


    
![png](case_ia_files/case_ia_405_0.png)
    


#### Visualizando o Tubo ε

Vamos ajustar um SVR linear simples e desenhar o tubo ε para ver quais pontos ficam dentro e fora.


```python
# =======================================================
# SVR Linear: Tubo epsilon
# =======================================================
from sklearn.svm import SVR 

Xtr, Xte, ytr, yte = train_test_split(X_lin, y_lin, test_size=0.2, random_state=42)

svr_lin = SVR(kernel='linear', C=1.0, epsilon=0.2) 
# kernel = 'linear' para regressão linear
# C = penalidade por erro fora do tubo (quanto maior, mais rígido)
# epsilon = largura do tubo (quanto maior, mais tolerante)

svr_lin.fit(Xtr, ytr) # Treinamento do modelo

y_pred_lin = svr_lin.predict(Xte) # Predições no conjunto de teste
rmse_lin = sqrt(mean_squared_error(yte, y_pred_lin)) # RMSE
r2_lin = r2_score(yte, y_pred_lin) # R²

# Linha de predição e tubos
X_plot = np.linspace(X_lin.min(), X_lin.max(), 300).reshape(-1,1)
y_line = svr_lin.predict(X_plot)

plt.figure(figsize=(8,5))
plt.scatter(X_lin, y_lin, s=15, alpha=0.6, label='Dados')
plt.plot(X_plot, y_line, 'r', label='Função f(x)')
plt.plot(X_plot, y_line + svr_lin.epsilon, 'k--', linewidth=1, label='+ε') # Tubo epsilon
plt.plot(X_plot, y_line - svr_lin.epsilon, 'k--', linewidth=1, label='-ε')

# Destacar pontos fora do tubo
outside_mask = np.abs(y_lin - svr_lin.predict(X_lin)) > svr_lin.epsilon
plt.scatter(X_lin[outside_mask], y_lin[outside_mask], c='gold', edgecolors='k', s=40, label='Vetores de Suporte (fora)')

plt.title(f'SVR Linear (ε={svr_lin.epsilon}) - Tubo')
plt.xlabel('X')
plt.ylabel('y')
plt.legend()
plt.grid(alpha=0.3)
plt.show()

print(f"RMSE: {rmse_lin:.3f} | R²: {r2_lin:.3f}")
print(f"Total de vetores de suporte: {len(svr_lin.support_)} ({len(svr_lin.support_)/len(Xtr)*100:.1f}% do treino)")
```


    
![png](case_ia_files/case_ia_407_0.png)
    


    RMSE: 0.113 | R²: 0.911
    Total de vetores de suporte: 40 (12.5% do treino)
    

### Formulação Formal

Essa parte é um pouco mais complexa, mas vamos tentar entender: 
#### Retomando o objetivo:

Aprender uma função de regressão $ f(x) $ que:
- Aceita pequenos desvios (até $\epsilon$) sem custo.
- Penaliza apenas erros que ultrapassam o “tubo” $\epsilon$.
- Usa somente alguns pontos “ativos” (vetores de suporte) para definir a solução.

#### Conjunto de Dados

$$
D=\{(x^{(i)}, y^{(i)})\}_{i=1}^n,\quad x^{(i)}\in \mathbb{R}^d,\ y^{(i)}\in \mathbb{R}
$$

#### Hiperparâmetros

- $\epsilon$: largura da zona de tolerância (erro ignorado).
- $C$: peso da penalização para pontos fora do tubo (controle viés × variância).
- Kernel $K(\cdot,\cdot)$: implementa o mapeamento implícito $\phi(x)$ sem calcular $\phi$ diretamente (Kernel Trick).

#### Forma Primal: O Problema Original de Otimização

A **forma primal** é a formulação direta do problema de otimização do SVR. Aqui definimos explicitamente o que queremos minimizar:

**Minimizar:**
$$
\frac{1}{2}\|w\|^2 + C \sum_{i=1}^n (\xi_i + \xi_i^*)
$$

**Sujeito a:**
$$
\begin{aligned}
y^{(i)} - (w^T\phi(x^{(i)}) + b) &\le \epsilon + \xi_i \quad \text{\small (desvio por cima da predição, penalizado se exceder $\epsilon$)} \\ 
(w^T\phi(x^{(i)}) + b) - y^{(i)} &\le \epsilon + \xi_i^* \quad \text{\small (desvio por baixo da predição, penalizado se exceder $\epsilon$)} \\
\xi_i,\ \xi_i^* &\ge 0 \quad \text{\small (slack nunca negativo)}
\end{aligned}
$$

**Interpretação dos componentes:**

1. **$\frac{1}{2}\|w\|^2$**: Termo de regularização que controla a complexidade do modelo
    - Busca por uma função mais com menos oscilações (suave)
    - Previne overfitting ao penalizar pesos grandes

2. **$\xi_i$ e $\xi_i^*$**: Variáveis de folga (slack variables)
    - $\xi_i$ mede quanto o ponto $i$ ultrapassa o tubo **acima** da predição
    - $\xi_i^*$ mede quanto o ponto $i$ ultrapassa o tubo **abaixo** da predição
    - Só são ativadas (≠ 0) quando o erro excede $\epsilon$

3. **$C$**: Hiperparâmetro que balanceia o trade-off
    - $C$ grande >> prioriza minimizar erros >> mais vetores de suporte >> maior complexidade
    - $C$ pequeno >> prioriza simplicidade ($\|w\|^2$ pequeno) >> função mais lisa

4. **Restrições**: Garantem que os erros sejam contabilizados corretamente
    - A primeira restrição captura erros por cima
    - A segunda captura erros por baixo

#### Perda ε-Insensitive

A **perda ε-insensitive**  define como os erros são tratados no problema de otimização:

$$
L_\epsilon(y, f(x)) = 
\begin{cases}
0,& \text{se } |y - f(x)| \le \epsilon \\
|y - f(x)| - \epsilon,& \text{se } |y - f(x)| > \epsilon
\end{cases}
$$

- **Na forma primal**, essa perda aparece nas restrições do problema: só penalizamos desvios que ultrapassam o tubo de largura $\epsilon$.
- As variáveis de folga $\xi_i$ e $\xi_i^*$ representam exatamente o quanto cada ponto excede esse limite, sendo ativadas apenas quando $|y^{(i)} - f(x^{(i)})| > \epsilon$.
- O termo $C \sum_{i=1}^n (\xi_i + \xi_i^*)$ no objetivo controla o quanto penalizamos esses excessos, enquanto $\frac{1}{2}\|w\|^2$ regula a suavidade da função.

**Resumo da relação:**
- A perda ε-insensitive define o "tubo" de tolerância na forma primal.
- Só erros fora do tubo geram penalização e ativam as variáveis de folga.
- O SVR busca uma função que seja suave, ignore pequenos erros e penalize apenas desvios significativos, conforme explicitado na formulação primal.

#### Forma Dual: Representação em Termos de Vetores de Suporte

Através da teoria de otimização convexa (multiplicadores de Lagrange), transformamos o problema primal em sua **forma dual**:

$$
f(x)=\sum_{i=1}^n (\alpha_i - \alpha_i^*)\, K(x^{(i)}, x) + b
$$

**Por que a forma dual é importante:**

1. **Dependência explícita apenas dos dados**: Não precisamos calcular $w$ diretamente
2. **Kernel Trick habilitado**: Substituímos $\phi(x^{(i)})^T\phi(x)$ por $K(x^{(i)}, x)$
3. **Solução esparsa automática**: A maioria dos $\alpha_i - \alpha_i^* = 0$

**Significado dos coeficientes $\alpha$:**

- **$\alpha_i = 0$ e $\alpha_i^* = 0$**: Ponto dentro do tubo >> não influencia a solução
- **$\alpha_i > 0$ ou $\alpha_i^* > 0$**: Ponto é um **vetor de suporte** >> define a função
- **Vetores de suporte**: São os pontos no limite ou fora do tubo $\epsilon$

**Principais kernels e quando usar:**

| Kernel | Fórmula | Quando usar |
|--------|---------|-------------|
| **Linear** | $K(x, x') = x^T x'$ | Relação linear entre variáveis |
| **RBF (Gaussiano)** | $K(x, x') = \exp(-\gamma \|x - x'\|^2)$ | Padrões não lineares suaves e locais |
| **Polinomial** | $K(x, x') = (x^T x' + c)^d$ | Interações polinomiais de grau $d$ |

#### Geometria do Tubo

- Faixa de largura $2\epsilon$ centrada em $f(x)$.
- Dentro do tubo: pontos “inertes” (não afetam gradiente no dual).
- Fora do tubo: pontos “ativos” (geram $\alpha$ ≠ 0).


#### Efeitos dos Hiperparâmetros

- $\epsilon$ pequeno >> mais pontos fora >> mais vetores de suporte >> maior complexidade.
- $\epsilon$ grande >> poucos vetores de suporte >> risco de subajuste.
- $C$ grande >> baixo viés, maior variância (modelo força proximidade aos dados).
- $C$ pequeno >> maior viés, menor variância (função mais lisa).


#### Saídas do Modelo

- Função aprendida $f(x)$.
- Predição: $\hat{y} = f(x)$.
- Vetores de suporte: medida indireta de complexidade efetiva.
- Métricas usuais: MSE, RMSE, MAE, $R^2$ + quantidade de vetores de suporte.


#### Resumo 
SVR = Regressão + Tubo ($\epsilon$) + Perda que ignora pequenos erros + Penalização controlada por $C$ + Kernel Trick + Vetores de Suporte como estrutura mínima da solução.

### Usando SKlearn

A implementação oficial já resolve a otimização dual internamente. Vamos comparar kernels e hiperparâmetros rapidamente.


```python
from sklearn.svm import SVR

Xtr_l, Xte_l, ytr_l, yte_l = train_test_split(X_lin, y_lin, test_size=0.2, random_state=0)

model_linear = SVR(kernel='linear')
model_linear.fit(Xtr_l, ytr_l)
pred_linear = model_linear.predict(Xte_l)

model_rbf = SVR(kernel='rbf')
model_rbf.fit(Xtr_l, ytr_l)
pred_rbf = model_rbf.predict(Xte_l)

for name, pred, m in [('Linear', pred_linear, model_linear), ('RBF', pred_rbf, model_rbf)]:
    mse = mean_squared_error(yte_l, pred)
    rmse = sqrt(mse)
    mae = mean_absolute_error(yte_l, pred)
    r2 = r2_score(yte_l, pred)
    print(f"{name:<7} | RMSE={rmse:.3f} | MAE={mae:.3f} | R²={r2:.3f} | SVs={len(m.support_)}")
```

    Linear  | RMSE=0.115 | MAE=0.090 | R²=0.915 | SVs=137
    RBF     | RMSE=0.114 | MAE=0.089 | R²=0.917 | SVs=142
    

#### Kernel Trick na Regressão

Vamos comparar ajuste de kernel linear vs RBF no dataset não linear (seno).


```python
# =======================================================
# Kernel Linear vs RBF (não linear)
# =======================================================
Xtr_n, Xte_n, ytr_n, yte_n = train_test_split(X_non, y_non, test_size=0.2, random_state=42)

svr_lin_n = SVR(kernel='linear', C=1.0, epsilon=0.05)
svr_lin_n.fit(Xtr_n, ytr_n)

svr_rbf_n = SVR(kernel='rbf', C=1.0, epsilon=0.05, gamma='scale')
svr_rbf_n.fit(Xtr_n, ytr_n)

X_plot_n = np.linspace(-3,3,400).reshape(-1,1)
lin_pred_curve = svr_lin_n.predict(X_plot_n)
rbf_pred_curve = svr_rbf_n.predict(X_plot_n)

plt.figure(figsize=(10,5))
plt.scatter(X_non, y_non, s=15, alpha=0.5, label='Dados')
plt.plot(X_plot_n, lin_pred_curve, 'r--', label='SVR Linear')
plt.plot(X_plot_n, rbf_pred_curve, 'g', linewidth=2, label='SVR RBF')
plt.title('Kernel Linear vs RBF no Padrão Senoidal')
plt.xlabel('X')
plt.ylabel('y')
plt.legend()
plt.grid(alpha=0.3)
plt.show()

for name, model in [('Linear', svr_lin_n), ('RBF', svr_rbf_n)]:
    pred = model.predict(Xte_n)
    rmse = sqrt(mean_squared_error(yte_n, pred))
    r2 = r2_score(yte_n, pred)
    print(f"{name:<6} | RMSE={rmse:.3f} | R²={r2:.3f} | SVs={len(model.support_)}")
```


    
![png](case_ia_files/case_ia_413_0.png)
    


    Linear | RMSE=0.484 | R²=0.548 | SVs=295
    RBF    | RMSE=0.160 | R²=0.951 | SVs=244
    

#### Hiperparâmetros Importantes

- C: Controle de penalização (alto >> mais ajuste, baixo >> mais suavidade).
- ε: Largura do tubo (alto >> ignora muitos erros pequenos >> pode subajustar; baixo >> tubo fino >> mais SVs >> risco overfitting).
- kernel: 'linear', 'rbf', 'poly', 'sigmoid'.
- gamma (RBF / poly / sigmoid): Influência local (alto >> captura detalhes / risco overfit; baixo >> mais suave).
- degree (poly): Grau do polinômio.

Vamos ver sensibilidade rápida em grade reduzida (dataset seno):


```python
# =======================================================
# MINI GRID SEARCH (demonstração)
# =======================================================
param_C = [0.1, 1, 10]
param_eps = [0.01, 0.05, 0.2]
param_gamma = ['scale', 0.5, 2]

results = []
for C in param_C:
    for eps in param_eps:
        for gamma in param_gamma:
            svr_tmp = SVR(kernel='rbf', C=C, epsilon=eps, gamma=gamma)
            svr_tmp.fit(Xtr_n, ytr_n)
            pred = svr_tmp.predict(Xte_n)
            r2 = r2_score(yte_n, pred)
            rmse = sqrt(mean_squared_error(yte_n, pred))
            results.append({'C': C, 'epsilon': eps, 'gamma': gamma, 'R2': r2, 'RMSE': rmse, 'SVs': len(svr_tmp.support_)})

res_df = pd.DataFrame(results).sort_values('R2', ascending=False)
print(res_df.head(10))
```

           C  epsilon  gamma        R2      RMSE  SVs
    14   1.0     0.05      2  0.952148  0.157571  245
    5    0.1     0.05      2  0.951569  0.158521  237
    21  10.0     0.05  scale  0.951479  0.158668  247
    22  10.0     0.05    0.5  0.951347  0.158884  246
    23  10.0     0.05      2  0.951303  0.158956  243
    11   1.0     0.01      2  0.951266  0.159017  302
    24  10.0     0.20  scale  0.950812  0.159755   55
    12   1.0     0.05  scale  0.950708  0.159923  244
    13   1.0     0.05    0.5  0.950703  0.159931  245
    25  10.0     0.20    0.5  0.950641  0.160033   53
    

*O que a saída nos diz sobre a sensibilidade aos hiperparâmetros?*

#### Otimização de Hiperparâmetros com Grid Search

Para encontrar a melhor combinação de hiperparâmetros de forma sistemática, utilizaremos `GridSearchCV` junto com a validação cruzada. Isso nos permitirá testar diferentes kernels, valores de `C`, `epsilon` e `gamma` para identificar a configuração que proporciona o melhor desempenho.



```python
from sklearn.model_selection import GridSearchCV
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.svm import SVR
import numpy as np
from sklearn.metrics import mean_squared_error, r2_score
from sklearn.model_selection import train_test_split

# Reutilizando o dataset não linear (seno)
# Certifique-se de que X_non, y_non estão definidos no notebook
X_non = np.linspace(-3, 3, 400).reshape(-1, 1)
np.random.seed(42)
y_non = np.sin(X_non[:, 0]) + np.random.normal(0, 0.15, size=X_non.shape[0])

Xtr_n, Xte_n, ytr_n, yte_n = train_test_split(X_non, y_non, test_size=0.2, random_state=42)

# Definir o pipeline (escalar os dados antes do SVR é uma boa prática)
pipeline = Pipeline([
    ('scaler', StandardScaler()),
    ('svr', SVR())
])

# Definir o espaço de busca para os hiperparâmetros
param_grid = {
    'svr__kernel': ['rbf', 'linear'],
    'svr__C': [0.1, 1, 10, 100],
    'svr__epsilon': [0.01, 0.05, 0.1, 0.2],
    'svr__gamma': ['scale', 'auto', 0.1, 1] # 'gamma' é ignorado para kernel='linear'
}

# Configurar o GridSearchCV
# cv=5: validação cruzada com 5 folds
# scoring='r2': métrica R² para otimização
# n_jobs=-1: usa todos os processadores disponíveis
grid_search = GridSearchCV(pipeline, param_grid, cv=5, scoring='r2', n_jobs=-1, verbose=1)

# Executar o Grid Search
print("Executando GridSearchCV...")
grid_search.fit(Xtr_n, ytr_n)

# Melhores parâmetros encontrados
print(f"Melhores parâmetros: {grid_search.best_params_}")
print(f"Melhor score (R²) CV: {grid_search.best_score_:.3f}")

# Avaliar o modelo com os melhores parâmetros no conjunto de teste
best_svr = grid_search.best_estimator_
y_pred_best = best_svr.predict(Xte_n)
test_r2 = r2_score(yte_n, y_pred_best)
test_rmse = np.sqrt(mean_squared_error(yte_n, y_pred_best))

print(f"R² no conjunto de teste: {test_r2:.3f}")
print(f"RMSE no conjunto de teste: {test_rmse:.3f}")

```

#### Pipeline e Normalização

Assim como no SVM de classificação, escalar features normalmente melhora estabilidade (principalmente com RBF / polinomial).


```python
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler

pipe_svr = Pipeline([
    ('scaler', StandardScaler()),
    ('svr', SVR(kernel='rbf', C=1.0, epsilon=0.05))
])
pipe_svr.fit(Xtr_n, ytr_n)
pred_pipe = pipe_svr.predict(Xte_n)

print(f"R² Pipeline: {r2_score(yte_n, pred_pipe):.3f}")
print(f"RMSE Pipeline: {sqrt(mean_squared_error(yte_n, pred_pipe)):.3f}")
```

    R² Pipeline: 0.951
    RMSE Pipeline: 0.160
    

#### Diagnóstico: Resíduos

Mesmas análises que regressão linear: queremos resíduos sem padrão, centrados em 0. Aqui mostramos rapidamente para o modelo RBF.


```python
# =======================================================
# Resíduos do modelo RBF
# =======================================================
res_rbf = yte_n - svr_rbf_n.predict(Xte_n)

fig, axes = plt.subplots(1,3, figsize=(14,4))
axes[0].scatter(svr_rbf_n.predict(Xte_n), res_rbf, s=25, alpha=0.6)
axes[0].axhline(0, color='r', linestyle='--')
axes[0].set_title('Resíduos vs Preditos')

axes[1].hist(res_rbf, bins=30, edgecolor='black', alpha=0.7)
axes[1].set_title('Histograma Resíduos')

from scipy import stats
stats.probplot(res_rbf, dist='norm', plot=axes[2])
axes[2].set_title('Q-Q Plot')

plt.tight_layout()
plt.show()
```


    
![png](case_ia_files/case_ia_422_0.png)
    


### Conclusões e Dicas Práticas

1. Ajuste primeiro um SVR linear: se não capta padrão >> teste RBF.
2. Normalize sempre antes de kernels não lineares.
3. Ajuste ε: comece pequeno (0.05) e avalie % de vetores de suporte (muito alto >> tente aumentar ε).
4. Ajuste C: se overfitting (muitos SVs e ruído) >> reduza C.
5. Explore gamma (RBF): 'scale' geralmente bom ponto de partida.
6. Use Grid/Random Search só depois de validar pipeline básico.
7. Compare sempre com regressão linear para ver se complexidade compensa.

#### Referências
- [Scikit-learn SVR Docs](https://scikit-learn.org/stable/modules/generated/sklearn.svm.SVR.html)
- Kernel Trick ([relembrar](https://www.geeksforgeeks.org/machine-learning/kernel-trick-in-support-vector-classification/))
- [Diagnóstico de regressão](https://lamfo-unb.github.io/2019/04/13/Diagnostico-em-Regressao/)



## **4.3 Árvores de Decisão para Regressão**

Na classificação, cada nó busca uma pergunta que **reduza impureza** (Gini, Entropia) de forma mais agressiva. Já na regressão, o objetivo muda: agora queremos nós (segmentos) onde os valores reais **fiquem concentrados** e o erro seja baixo.

Em vez de medir mistura de classes, medimos quão dispersos são os valores numéricos dentro de cada região.

Ou seja, para regressão buscamos tipicamente:
- Redução da Soma dos Erros Quadráticos (SSE)
- Redução da Variância
- Mean Squared Error (MSE) dentro dos nós

A ideia continua ser escolher o melhor split local, construir recursivamente até parar por algum critério.

### Intuição

Vamos manter a ideia da predição do preço de uma casa usando:
- Área (m²)
- Número de quartos
- Idade do imóvel

Uma árvore de regressão pensa em "segmentar" o espaço em blocos onde o **preço médio** dentro de cada bloco seja uma boa aproximação. Em vez de devolver uma classe na folha, ela devolve um **valor (geralmente a média ou mediana dos valores naquele nó)**.

Perguntas sucessivas podem criar regiões cada vez mais homogêneas em termos de preço, ou seja, se segmentarmos demais, memorizamos ruído (overfitting). Se segmentarmos de menos, perdemos estrutura (underfitting).

Vamos construir um exemplo sintético com relação não-linear para visualizar.


```python
# Imports principais
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.tree import DecisionTreeRegressor, plot_tree, export_text
from sklearn.metrics import mean_squared_error, mean_absolute_error, r2_score
from sklearn.model_selection import train_test_split, GridSearchCV
from sklearn.preprocessing import StandardScaler
from sklearn.pipeline import Pipeline



```


```python
# Gerar dados sintéticos (não-linear + interação)
np.random.seed(42)
N = 400
X1 = np.random.uniform(0, 10, N)          # Ex: área
X2 = np.random.uniform(-5, 5, N)           # Ex: idade (centrada)
X3 = np.random.uniform(0, 1, N)            # Ex: fator de localização (score)

# Relação verdadeira (não linear)
# Inclui termo senoidal e interação X1*X3
y = 15 + 4*X1 - 2.5*X2 + 10*X3 + 3*np.sin(X1) + 5*X1*X3 + np.random.normal(0, 2.0, N)

X = pd.DataFrame({'Area': X1, 'Idade': X2, 'LocalScore': X3})
df = X.copy()
df['Preco'] = y

print(df.head())
print(f"Shape: {df.shape}")
```

           Area     Idade  LocalScore      Preco
    0  3.745401 -3.968761    0.707239  61.648059
    1  9.507143  4.025529    0.152539  51.362876
    2  7.319939  0.052524    0.576288  72.475182
    3  5.986585  3.264575    0.606715  57.898310
    4  1.560186 -1.799504    0.424131  33.393230
    Shape: (400, 4)
    


```python
# Visualização
plt.figure(figsize=(7,5))
sc = plt.scatter(df['Area'], df['Preco'], c=df['LocalScore'], cmap='viridis', alpha=0.7)
plt.colorbar(sc, label='LocalScore')
plt.xlabel('Área (m²)')
plt.ylabel('Preço')
plt.title('Dados Sintéticos - Regressão')
plt.show()

```


    
![png](case_ia_files/case_ia_430_0.png)
    


Vamos inserir uma árvore de decisão como exemplo, com um split de `LocalScore > 0.5` criando duas folhas


```python
import numpy as np
from sklearn.metrics import mean_squared_error, mean_absolute_error, r2_score

def sse(y):
    return ((y - y.mean())**2).sum() # Soma dos erros ao quadrado

# split por LocalScore > 0.5
threshold_local = 0.5
grupo_esq = df[df['LocalScore'] <= threshold_local]
grupo_dir = df[df['LocalScore'] > threshold_local]

baseline_sse = sse(df['Preco'])
baseline_mse = ((df['Preco'] - df['Preco'].mean())**2).mean()

split_sse = sse(grupo_esq['Preco']) + sse(grupo_dir['Preco'])
gain_1 = baseline_sse - split_sse
split_mse = split_sse / len(df)

pred_manual1 = np.where(df['LocalScore'] > threshold_local, grupo_dir['Preco'].mean(), grupo_esq['Preco'].mean())
rmse1 = mean_squared_error(df['Preco'], pred_manual1)
mae1 = mean_absolute_error(df['Preco'], pred_manual1)
r2_1 = r2_score(df['Preco'], pred_manual1)

print('=== Árvore ===')
print(f'Tamanho total: {len(df)} | Esq: {len(grupo_esq)} | Dir: {len(grupo_dir)}')
print(f'Média Global: {df['Preco'].mean():.3f}')
print(f'Média Esq (LS<=0.5): {grupo_esq['Preco'].mean():.3f}')
print(f'Média Dir (LS>0.5): {grupo_dir['Preco'].mean():.3f}')
print('\nSSE Baseline:', f'{baseline_sse:.2f}')
print('SSE Pós-Split:', f'{split_sse:.2f}')
print('Gain (redução SSE):', f'{gain_1:.2f}')
print('\nMSE Baseline:', f'{baseline_mse:.3f}')
print('MSE Pós-Split:', f'{split_mse:.3f}')
print('\nMétricas predição (2 folhas):')
print(f'RMSE: {rmse1:.3f} | MAE: {mae1:.3f} | R²: {r2_1:.3f}')
```

    === Árvore ===
    Tamanho total: 400 | Esq: 196 | Dir: 204
    Média Global: 53.201
    Média Esq (LS<=0.5): 43.589
    Média Dir (LS>0.5): 62.436
    
    SSE Baseline: 220637.38
    SSE Pós-Split: 185131.94
    Gain (redução SSE): 35505.44
    
    MSE Baseline: 551.593
    MSE Pós-Split: 462.830
    
    Métricas predição (2 folhas):
    RMSE: 462.830 | MAE: 18.266 | R²: 0.161
    


```python
# Segundo nível: adicionar split por Area > 5 dentro de cada lado
threshold_area = 5
L_esq = df[(df['LocalScore'] <= threshold_local) & (df['Area'] <= threshold_area)]
L_esq_2 = df[(df['LocalScore'] <= threshold_local) & (df['Area'] > threshold_area)]
L_dir = df[(df['LocalScore'] > threshold_local) & (df['Area'] <= threshold_area)]
L_dir_2 = df[(df['LocalScore'] > threshold_local) & (df['Area'] > threshold_area)]

sse_4 = sse(L_esq['Preco']) + sse(L_esq_2['Preco']) + sse(L_dir['Preco']) + sse(L_dir_2['Preco'])
gain_total_2 = baseline_sse - sse_4
gain_incremental_2 = split_sse - sse_4

mean_L_esq = L_esq['Preco'].mean()
mean_L_esq_2 = L_esq_2['Preco'].mean()
mean_L_dir = L_dir['Preco'].mean()
mean_L_dir_2 = L_dir_2['Preco'].mean()

def predict_row_manual2(row):
    if row['LocalScore'] <= threshold_local:
        if row['Area'] <= threshold_area:
            return mean_L_esq
        else:
            return mean_L_esq_2
    else:
        if row['Area'] <= threshold_area:
            return mean_L_dir
        else:
            return mean_L_dir_2

pred_manual2 = df.apply(predict_row_manual2, axis=1).values
rmse2 = mean_squared_error(df['Preco'], pred_manual2)
mae2 = mean_absolute_error(df['Preco'], pred_manual2)
r2_2 = r2_score(df['Preco'], pred_manual2)

print('\n=== Árvore 2 ===')
print('Tamanhos folhas:', len(L_esq), len(L_esq_2), len(L_dir), len(L_dir_2))
print(f'SSE 1º nível: {split_sse:.2f}')
print(f'SSE 2º nível: {sse_4:.2f}')
print(f'Gain acumulado total: {gain_total_2:.2f}')
print(f'Gain incremental segundo nível: {gain_incremental_2:.2f}')
print('\nMédias por folha:')
print(f'  (LS<=0.5, A<=5): {mean_L_esq:.3f}')
print(f'  (LS<=0.5, A>5): {mean_L_esq_2:.3f}')
print(f'  (LS>0.5, A<=5): {mean_L_dir:.3f}')
print(f'  (LS>0.5, A>5): {mean_L_dir_2:.3f}')
print('\nMétricas predição (4 folhas):')
print(f'RMSE: {rmse2:.3f} | MAE: {mae2:.3f} | R²: {r2_2:.3f}')
print('\nEvolução RMSE:', f'{rmse1:.3f} -> {rmse2:.3f}')
print('Evolução R²  :', f'{r2_1:.3f} -> {r2_2:.3f}')
```

    
    === Árvore 2 ===
    Tamanhos folhas: 97 99 96 108
    SSE 1º nível: 185131.94
    SSE 2º nível: 61953.07
    Gain acumulado total: 158684.31
    Gain incremental segundo nível: 123178.87
    
    Médias por folha:
      (LS<=0.5, A<=5): 29.151
      (LS<=0.5, A>5): 57.736
      (LS>0.5, A<=5): 41.023
      (LS>0.5, A>5): 81.470
    
    Métricas predição (4 folhas):
    RMSE: 154.883 | MAE: 9.930 | R²: 0.719
    
    Evolução RMSE: 462.830 -> 154.883
    Evolução R²  : 0.161 -> 0.719
    

### Formulação

A árvore de regressão é MUITO parecida com a da classificação, só trocamos a métrica de impureza de classe por uma métrica de dispersão de valores.

**Entrada**

1. Conjunto de treinamento de n amostras em pares $ D=\{(x^{(i)}, y^{(i)})\}_{i=1}^n $

    onde:

    - $ x^{(i)} $: vetor de d features ($ x^{(i)} = (x^{(i)}_1, x^{(i)}_2, ..., x^{(i)}_d) $).

    - $ y^{(i)} $: rótulo numérico contínuo, ou seja, $ y^{(i)} \in \mathbb{R} $.

**Processamento**

O algoritmo constrói a árvore de forma recursiva, procurando em cada nó a melhor divisão possível. A "melhor" divisão é aquela que torna os subconjuntos resultantes o mais homogêneos possível em relação ao valor de $ y $.

**1. Critério de 'Impureza' para Regressão (Dispersão)**

Em vez de medir a mistura de classes (Gini/Entropia), medimos a dispersão dos valores numéricos dentro de um nó. O critério mais comum é a ja conhecida **Soma dos Erros Quadráticos (SSE - Sum of Squared Errors)**, que é minimizada quando os valores em um nó estão próximos uns dos outros.

Para um nó $ S $, o SSE é calculado em relação à média dos valores ($ \bar{y}_S $) daquele nó:

$$SSE(S) = \sum_{i \in S} (y^{(i)} - \bar{y}_S)^2$$

Um nó com baixo SSE é considerado "puro" no contexto da regressão.

**2. Ganho na Divisão (Redução de Variância)**

De forma análoga ao *Information Gain*, o algoritmo escolhe a divisão que maximiza a **redução do SSE**. Para uma feature $ A $ que divide o nó $ S $ em subconjuntos $ S_L $ (esquerda) e $ S_R $ (direita), o ganho é:
$$ \text{Redução de SSE} = SSE(S) - (SSE(S_L) + SSE(S_R))$$

O algoritmo testa todas as features e todos os possíveis pontos de corte para encontrar a divisão que resulta na maior redução de SSE.

**3. Algoritmo de Construção**

O processo é o mesmo da classificação, mas usando a métrica de regressão:

```
função BuildTree(S, Features):
    se critério de parada for atingido (ex: profundidade máxima):
        retorna folha com o valor médio de y em S
    
    seleciona feature A e threshold t que maximizam a Redução de SSE
    cria nó com o teste (A <= t)
    
    S_L, S_R = divide S baseado no teste
    
    adiciona subárvore esquerda BuildTree(S_L, Features)
    adiciona subárvore direita BuildTree(S_R, Features)
```

**4. Critérios de Parada**

Idênticos aos da classificação, usados para regularizar a árvore e evitar overfitting:
- Profundidade máxima da árvore (`max_depth`).
- Número mínimo de amostras para dividir um nó (`min_samples_split`).
- Número mínimo de amostras em um nó folha (`min_samples_leaf`).

**Saída - Regressão**

- **Estrutura da Árvore**: Um conjunto de nós com regras de divisão.
- **Predição**: Para uma nova amostra, ela percorre a árvore de acordo com as regras até chegar a um nó folha. O valor da predição é o **valor médio** de $ y $ das amostras de treinamento que caíram naquela folha durante a construção da árvore.

**Poda (Pruning)**

O conceito de pré-poda (usando critérios de parada) e pós-poda para controlar a complexidade e evitar overfitting é exatamente o mesmo aplicado às árvores de classificação.

### Desafio: "From Scratch" (Regressão)

Vamos criar um esqueleto simplificado de uma Árvore de Decisão para Regressão. Objetivo didático: entender onde entram cálculo de erro e divisão.

Implementar depois:
- seleção de melhor split
- cálculo de SSE/variância
- recursão com critérios de parada



```python
class SimpleDecisionTreeReg:
    def __init__(self, max_depth=5, min_samples_split=10, min_samples_leaf=5):
        """Árvore de Regressão simplificada (esqueleto).
        Parâmetros:
        - max_depth: profundidade máxima
        - min_samples_split: mínimo de amostras para tentar split
        - min_samples_leaf: mínimo em cada folha
        """
        pass

    def _sse(self, y):
        """Calcula soma dos erros quadráticos em relação à média."""
        pass

    def _best_split(self, X, y):
        """Encontra melhor feature + threshold (retorna dict ou None)."""
        pass

    def _build(self, X, y, depth=0):
        """Construção recursiva da árvore."""
        pass

    def fit(self, X, y):
        """Treina e armazena raiz."""
        pass

    def _predict_row(self, row, node):
        """Percorre nó até folha e retorna valor."""
        pass

    def predict(self, X):
        """Retorna vetor de predições."""
        pass

    def score(self, X, y):
        """Retorna R² como métrica simples."""
        pass
```


```python
# Split treino/teste
X_train, X_test, y_train, y_test = train_test_split(X.values, y, test_size=0.25, random_state=42)
print(X_train.shape, X_test.shape)

```

    (300, 3) (100, 3)
    

### Uso com sklearn

Vamos treinar uma árvore de regressão simples e observar métricas:
- RMSE
- MAE
- R²


```python
# Treino simples
reg = DecisionTreeRegressor(random_state=42)
reg.fit(X_train, y_train)

pred = reg.predict(X_test)
rmse = mean_squared_error(y_test, pred)
mae = mean_absolute_error(y_test, pred)
r2 = r2_score(y_test, pred)
print(f"RMSE: {rmse:.3f} | MAE: {mae:.3f} | R²: {r2:.3f}")

# Visualização: real vs predito
plt.figure(figsize=(6,5))
plt.scatter(y_test, pred, alpha=0.6)
plt.xlabel('Real')
plt.ylabel('Predito')
plt.title('Real vs Predito - Árvore Regressão')
lims = [min(y_test.min(), pred.min()), max(y_test.max(), pred.max())]
plt.plot(lims, lims, 'r--') 
plt.show()

```

    RMSE: 41.517 | MAE: 4.952 | R²: 0.919
    


    
![png](case_ia_files/case_ia_439_1.png)
    


### Visualizando a Predição em Degraus da Árvore de Decisão

Uma característica fundamental das Árvores de Decisão é que suas predições são feitas em "degraus". Isso significa que a árvore divide o espaço de features em regiões retangulares, e dentro de cada região, a predição é um valor constante (a média dos valores de treinamento naquela região).

Vamos visualizar isso com um exemplo simples usando apenas uma feature.



```python
import matplotlib.pyplot as plt
import numpy as np
from sklearn.tree import DecisionTreeRegressor
from sklearn.model_selection import train_test_split

N_viz = 400
X1_viz = np.random.uniform(0, 10, N_viz) # Ex: área
X_1d = X1_viz.reshape(-1, 1)
noise_viz = np.random.normal(0, 2.0, N_viz)
y_1d = 15 + 4*X1_viz + 3*np.sin(X1_viz) + noise_viz 


X_train_1d, X_test_1d, y_train_1d, y_test_1d = train_test_split(X_1d, y_1d, test_size=0.25, random_state=42)

# Treinar uma Árvore de Decisão de Regressão com profundidade limitada
tree_reg_1d = DecisionTreeRegressor(max_depth=3, random_state=42)
tree_reg_1d.fit(X_train_1d, y_train_1d)

# Gerar pontos para plotar a função de degraus
X_plot_1d = np.linspace(X_1d.min(), X_1d.max(), 500).reshape(-1, 1)
y_plot_1d = tree_reg_1d.predict(X_plot_1d)

plt.figure(figsize=(10, 6))
plt.scatter(X_1d, y_1d, s=20, edgecolor="black", c="darkorange", label="Dados Reais")
plt.plot(X_plot_1d, y_plot_1d, color="cornflowerblue", label="Predição da Árvore (degraus)", linewidth=2)

plt.xlabel("Feature Única (Ex: Área)")
plt.ylabel("Target (Ex: Preço)")
plt.title("Visualização da Predição em Degraus de uma Árvore de Regressão")
plt.legend()
plt.grid(True, alpha=0.3)
plt.show()

```


    
![png](case_ia_files/case_ia_441_0.png)
    


### Grid Search (Hiperparâmetros)

Vamos buscar combinação que maximize R² com validação cruzada.


```python
param_grid = {
    'max_depth': [3,5,7,None],
    'min_samples_split': [2,5,10],
    'min_samples_leaf': [1,2,5],
    'criterion': ['squared_error','friedman_mse']
}
reg_base = DecisionTreeRegressor(random_state=42)
grid = GridSearchCV(reg_base, param_grid, cv=5, scoring='r2', n_jobs=-1, verbose=0)
grid.fit(X_train, y_train)
print('Melhores parâmetros:', grid.best_params_)
print('Melhor R2 CV:', grid.best_score_)

best = grid.best_estimator_
pred_best = best.predict(X_test)
print('R2 teste:', r2_score(y_test, pred_best))
print('RMSE teste:', mean_squared_error(y_test, pred_best))
```

    Melhores parâmetros: {'criterion': 'friedman_mse', 'max_depth': None, 'min_samples_leaf': 1, 'min_samples_split': 2}
    Melhor R2 CV: 0.9040213882158511
    R2 teste: 0.918594678404642
    RMSE teste: 41.92404439214985
    

### Diagnóstico de Resíduos

Resíduos = real - predito. Devem estar centrados em zero e sem padrão claro.


```python
res = y_test - pred_best
fig, axes = plt.subplots(1,3, figsize=(14,4))

# Scatter residuos vs predito
axes[0].scatter(pred_best, res, alpha=0.6)
axes[0].axhline(0, color='red', linestyle='--')
axes[0].set_xlabel('Predito')
axes[0].set_ylabel('Resíduo')
axes[0].set_title('Resíduo vs Predito')

# Histograma
axes[1].hist(res, bins=20, edgecolor='k')
axes[1].set_xlabel('Resíduo')
axes[1].set_ylabel('Freq')
axes[1].set_title('Distribuição Resíduos')

# QQ plot
import scipy.stats as stats
stats.probplot(res, dist="norm", plot=axes[2])
axes[2].set_title('Q-Q Plot')

plt.tight_layout()
plt.show()

```


    
![png](case_ia_files/case_ia_445_0.png)
    


### Conclusões, Dicas Práticas e Próximos Passos

**Vantagens de Árvores de Decisão para Regressão**

1. **Interpretabilidade**: Modelo "caixa branca". Podemos visualizar regras de decisão (plot_tree, export_text).
2. **Sem premissas de distribuição**: Não assume linearidade nem normalidade de resíduos.
3. **Lida com interações naturalmente**: Captura relações não-lineares e interações sem engineering manual.
4. **Facilidade com dados mistos**: Features contínuas e categóricas sem transformações elaboradas (basta codificação simples).
5. **Rápida para treinar e prever**: Complexidade log(N) na predição quando balanceada.

**Desvantagens**

1. **Overfitting**: Sem regularização (max_depth, min_samples_leaf), tende a memorizar ruído.
2. **Instabilidade**: Pequenas mudanças nos dados alteram radicalmente a estrutura da árvore.
3. **Predições em degrau**: Árvore divide espaço em blocos. Dentro de cada bloco, predição é constante (média). Não suaviza bem limites.
4. **Pobre extrapolação**: Fora do range treinado, repetirá média da folha mais próxima (sem extrapolação linear).
5. **Tendência a viés em features com mais valores únicos**: Similar à classificação.

**Dicas Práticas**

- Comece com `max_depth` entre 3 e 7, depois ajuste com cross-validation.
- Use `min_samples_split` e `min_samples_leaf` para evitar folhas com poucos pontos (reduz variância).
- `criterion='absolute_error'` mais robusto se há outliers fortes.
- Observe resíduos: padrão forte indica má captura da estrutura ou necessidade de features adicionais.
- **Ensemble > Árvore Única**: Random Forest e Gradient Boosting (XGBoost, LightGBM) são superiores na prática ao combinar múltiplas árvores, reduzindo variância e melhorando generalização.

# **Extra 2: Um pouco mais sobre ensembles, agora para Regressão**


Se você já leu o capítulo de Ensembles para Classificação, vai perceber que a estrutura é bem parecida. A diferença é Em vez de votar em classes ("Sobreviveu" ou "Não Sobreviveu"), agora vamos fazer a média de predições numéricas (preços de casas, por exemplo).

Agora que você já domina Regressão Linear, SVR e Árvores de Decisão para Regressão, está na hora de juntá-los!

### A Situação

Imagine que você precisa prever o **preço de casas** na Califórnia. Você tem dados sobre:
- Onde a casa fica (latitude/longitude)
- Quantos quartos tem em média
- A renda das pessoas na região
- Quão velhas são as construções

### Recap dos Modelos que Já Vimos

Se cada modelo fosse uma pessoa dando uma opnião, seria mais ou menos assim:

- **Regressão Linear**: "É simples, casa maior = maior preço, relação é direta"
- **SVR**: "Depende do contexto, às vezes o preço sobe rápido, às vezes devagar."
- **Árvore de Regressão**: "se a casa está em tal região, tem tantos quartos, então o preço é X, senão, o preço é Y.

Vamos juntar essas interpretações agora:

### Bagging

Se você leu o capítulo de Ensembles para Classificação, já sabe como Bagging funciona:

1. **Pega** o dataset de treino
2. **Cria** várias versões dele (bootstrap = amostragem com reposição)
3. **Treina** um modelo em cada versão
4. **Combina** as previsões

A única diferença aqui? Em vez de **votar** ("8 de 10 árvores dizem que sobreviveu"), agora fazemos **média**:

- Árvore 1 prevê: $2.5M
- Árvore 2 prevê: $2.8M
- Árvore 3 prevê: $2.3M
- ...
- **Previsão final**: média = $2.53M

**Por que funciona?**

Cada árvore erra de um jeito diferente. Uma superestima, outra subestima. Quando você tira a média, esses erros tendem a se cancelar.

**Detalhe importante: OOB Score**

Lembra que ~37% dos dados ficam de fora de cada bootstrap? (Out-of-Bag)

Podemos usar esses dados pra avaliar o modelo **de graça**, sem precisar separar um conjunto de validação! Em regressão, o OOB score é basicamente o R² calculado nessas amostras.

#### 5.2.2.1 Vendo Isso na Prática

Vamos usar o **California Housing Dataset** (preços de casas na Califórnia).

A ideia:
1. Treinar uma árvore e ver como ela se comporta
2. Treinar várias árvores bootstrap e observar a variação
3. Aplicar BaggingRegressor do sklearn e comparar resultados


```python
# =======================================================
# IMPORTS INICIAIS
# =======================================================
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.datasets import fetch_california_housing
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeRegressor
from sklearn.metrics import mean_squared_error, mean_absolute_error, r2_score

sns.set_style("whitegrid")
plt.rcParams['figure.figsize'] = (12, 6)

# Carregar dataset California Housing
california = fetch_california_housing()
X_full = pd.DataFrame(california.data, columns=california.feature_names)
y_full = california.target  # MedHouseVal

# Usar subconjunto para velocidade (opcional)
X = X_full.sample(n=6000, random_state=42)
y = y_full[X.index]

X_train, X_test, y_train, y_test = train_test_split(X.values, y, test_size=0.25, random_state=42)
```


```python
# =======================================================
# Árvore única de regressão (baseline)
# =======================================================
base_tree = DecisionTreeRegressor(random_state=42, max_depth=None)
base_tree.fit(X_train, y_train)

pred_base = base_tree.predict(X_test)
rmse_base = mean_squared_error(y_test, pred_base)
mae_base = mean_absolute_error(y_test, pred_base)
r2_base = r2_score(y_test, pred_base)

print(f"Árvore Única - RMSE: {rmse_base:.3f} | MAE: {mae_base:.3f} | R²: {r2_base:.3f}")

# Visualização real vs predito
plt.scatter(y_test, pred_base, alpha=0.4)
plt.xlabel('Real')
plt.ylabel('Predito')
plt.title('Árvore Única - Real vs Predito')
lims = [min(y_test.min(), pred_base.min()), max(y_test.max(), pred_base.max())]
plt.plot(lims, lims, 'r--')
plt.show()

```

    Árvore Única - RMSE: 0.690 | MAE: 0.544 | R²: 0.485
    


    
![png](case_ia_files/case_ia_453_1.png)
    



```python
# =======================================================
# Várias Árvores bootstrap (manual) para observar variância
# =======================================================
B = 12 
metrics = []
for b in range(B):
    indices = np.random.choice(len(X_train), size=len(X_train), replace=True)
    X_boot = X_train[indices]
    y_boot = y_train[indices]
    tree_b = DecisionTreeRegressor(random_state=b)
    tree_b.fit(X_boot, y_boot)
    pred_b = tree_b.predict(X_test)
    r2_b = r2_score(y_test, pred_b)
    rmse_b = mean_squared_error(y_test, pred_b)
    metrics.append((r2_b, rmse_b))
    print(f"Árvore {b+1:02d} -> R²: {r2_b:.3f} | RMSE: {rmse_b:.3f}")

r2_vals = [m[0] for m in metrics]
print(f"\nR² Médio: {np.mean(r2_vals):.3f} | Desvio: {np.std(r2_vals):.3f} | Min: {min(r2_vals):.3f} | Max: {max(r2_vals):.3f}")

plt.figure(figsize=(8,4))
plt.plot(r2_vals, marker='o')
plt.axhline(np.mean(r2_vals), color='red', linestyle='--', label='Média R²')
plt.title('Distribuição de R² entre Árvores Bootstrap')
plt.xlabel('Árvore')
plt.ylabel('R²')
plt.legend()
plt.show()

```

    Árvore 01 -> R²: 0.458 | RMSE: 0.726
    Árvore 02 -> R²: 0.523 | RMSE: 0.640
    Árvore 03 -> R²: 0.474 | RMSE: 0.705
    Árvore 04 -> R²: 0.494 | RMSE: 0.678
    Árvore 05 -> R²: 0.504 | RMSE: 0.665
    Árvore 06 -> R²: 0.522 | RMSE: 0.641
    Árvore 07 -> R²: 0.478 | RMSE: 0.699
    Árvore 08 -> R²: 0.476 | RMSE: 0.702
    Árvore 09 -> R²: 0.529 | RMSE: 0.632
    Árvore 10 -> R²: 0.484 | RMSE: 0.691
    Árvore 06 -> R²: 0.522 | RMSE: 0.641
    Árvore 07 -> R²: 0.478 | RMSE: 0.699
    Árvore 08 -> R²: 0.476 | RMSE: 0.702
    Árvore 09 -> R²: 0.529 | RMSE: 0.632
    Árvore 10 -> R²: 0.484 | RMSE: 0.691
    Árvore 11 -> R²: 0.520 | RMSE: 0.643
    Árvore 12 -> R²: 0.461 | RMSE: 0.723
    
    R² Médio: 0.494 | Desvio: 0.024 | Min: 0.458 | Max: 0.529
    Árvore 11 -> R²: 0.520 | RMSE: 0.643
    Árvore 12 -> R²: 0.461 | RMSE: 0.723
    
    R² Médio: 0.494 | Desvio: 0.024 | Min: 0.458 | Max: 0.529
    


    
![png](case_ia_files/case_ia_454_1.png)
    


### Usando o BaggingRegressor do Sklearn

Agora que você viu manualmente como várias árvores bootstrap se comportam, vamos usar a implementação pronta do sklearn.

Vamos ativar `oob_score=True` pra ver o "score grátis" nos dados Out-of-Bag. Temos um conjunto de validação sem precisar separar dados!


```python
from sklearn.ensemble import BaggingRegressor

bag = BaggingRegressor(
    estimator=DecisionTreeRegressor(random_state=0),
    n_estimators=50,
    oob_score=True,
    random_state=42,
    n_jobs=-1
)
bag.fit(X_train, y_train)

pred_bag = bag.predict(X_test)
rmse_bag = mean_squared_error(y_test, pred_bag)
mae_bag = mean_absolute_error(y_test, pred_bag)
r2_bag = r2_score(y_test, pred_bag)
print(f"Bagging - RMSE: {rmse_bag:.3f} | MAE: {mae_bag:.3f} | R² Teste: {r2_bag:.3f} | OOB R²: {bag.oob_score_:.3f}")
```

    Bagging - RMSE: 0.320 | MAE: 0.383 | R² Teste: 0.761 | OOB R²: 0.746
    

### Random Forest: 

Random Forest é um Bagging que além de criar versões diferentes dos dados (bootstrap), ele também escolhe **features aleatórias** em cada divisão da árvore.

**Por que isso?**

No Bagging normal, se uma feature é muito forte (ex: "renda mediana" em preços de casas), TODAS as árvores vão usá-la na primeira divisão. Resultado? As árvores ficam muito parecidas (correlacionadas).

Random Forest força cada árvore a considerar apenas um **subset aleatório de features** em cada divisão. Isso deixa as árvores mais diferentes umas das outras, e quando você tira a média, ganha ainda mais estabilidade.

Random Forest costuma ser o primeiro modelo que você deve tentar em problemas tabulares. Funciona bem out-of-the-box e raramente falha feio.

**Hiperparâmetros importantes:**
- `n_estimators`: quantas árvores (mais = melhor, até um ponto)
- `max_features`: quantas features considerar por split (default `sqrt` funciona bem)
- `max_depth`, `min_samples_leaf`: controlam complexidade de cada árvore


```python
from sklearn.ensemble import RandomForestRegressor

rf = RandomForestRegressor(
    n_estimators=300,
    max_depth=None,
    min_samples_leaf=2,
    max_features='sqrt',
    random_state=42,
    n_jobs=-1
)
rf.fit(X_train, y_train)

pred_rf = rf.predict(X_test)
rmse_rf = mean_squared_error(y_test, pred_rf)
mae_rf = mean_absolute_error(y_test, pred_rf)
r2_rf = r2_score(y_test, pred_rf)
print(f"RandomForest - RMSE: {rmse_rf:.3f} | MAE: {mae_rf:.3f} | R²: {r2_rf:.3f}")

# Importância de features
imp = rf.feature_importances_
cols = california.feature_names
order = np.argsort(imp)[::-1]
print("\nImportância das features:")
for i in order:
    print(f"{cols[i]:15}: {imp[i]:.4f}")

plt.figure(figsize=(7,4))
plt.bar([cols[i] for i in order], imp[order])
plt.xticks(rotation=45)
plt.ylabel('Importância')
plt.title('Random Forest - Importância de Features')
plt.tight_layout()
plt.show()

```

    RandomForest - RMSE: 0.300 | MAE: 0.374 | R²: 0.776
    
    Importância das features:
    MedInc         : 0.3649
    AveRooms       : 0.1294
    Latitude       : 0.1248
    Longitude      : 0.1206
    AveOccup       : 0.1201
    HouseAge       : 0.0595
    AveBedrms      : 0.0448
    Population     : 0.0358
    


    
![png](case_ia_files/case_ia_458_1.png)
    


### Gradient Boosting

Bagging e Random Forest são **paralelos**: todas as árvores são treinadas independentemente.

Gradient Boosting é **sequencial**: cada árvore nova tenta **corrigir os erros** da anterior.

**A Ideia:**

1. Treina a primeira árvore (prevê os preços)
2. Calcula os **resíduos** (erros: real - previsto)
3. Treina a segunda árvore pra prever os **resíduos**
4. Adiciona essa correção à predição anterior
5. Repete até ter N árvores

É tipo ir refinando a estimativa aos poucos. Cada árvore é fraca (pequena), mas juntas formam um modelo forte.

**Learning Rate (Taxa de Aprendizado)**

Controla o "peso" de cada correção. Se for muito alto (ex: 0.5), você aprende rápido mas pode overfitar. Se for muito baixo (ex: 0.01), você precisa de muitas árvores mas generaliza melhor.

**de bolso**: learning_rate baixo (~0.05) + muitas árvores (~300) costuma funcionar bem.


```python
from sklearn.ensemble import GradientBoostingRegressor

lrs = [0.05, 0.1, 0.2]
results_gb = []
for lr in lrs:
    gb = GradientBoostingRegressor(
        learning_rate=lr,
        n_estimators=300,
        max_depth=3,
        random_state=42
    )
    gb.fit(X_train, y_train)
    pred_gb = gb.predict(X_test)
    r2_gb = r2_score(y_test, pred_gb)
    rmse_gb = mean_squared_error(y_test, pred_gb)
    results_gb.append((lr, r2_gb, rmse_gb))
    print(f"GB (lr={lr}) -> R²: {r2_gb:.3f} | RMSE: { rmse_gb:.3f}")

plt.figure(figsize=(6,4))
plt.plot([r[0] for r in results_gb],[r[1] for r in results_gb], marker='o')
plt.xlabel('learning_rate')
plt.ylabel('R²')
plt.title('Gradient Boosting - efeito do learning_rate')
plt.show()

```

    GB (lr=0.05) -> R²: 0.797 | RMSE: 0.272
    GB (lr=0.1) -> R²: 0.811 | RMSE: 0.253
    GB (lr=0.1) -> R²: 0.811 | RMSE: 0.253
    GB (lr=0.2) -> R²: 0.814 | RMSE: 0.249
    GB (lr=0.2) -> R²: 0.814 | RMSE: 0.249
    


    
![png](case_ia_files/case_ia_460_1.png)
    


### Combinando Modelos Diferentes: Voting e Stacking

Até agora combinamos várias **versões do mesmo modelo** (várias árvores). E se combinarmos **modelos completamente diferentes**?

**VotingRegressor**

Você treina vários modelos (Linear, SVR, RandomForest) e faz a **média simples** das predições.

Exemplo:
- Regressão Linear prevê: $2.3M (captura tendência geral)
- SVR prevê: $2.7M (captura não-linearidades)
- Random Forest prevê: $2.5M (captura interações)
- **Voting**: $(2.3 + 2.7 + 2.5) / 3 = 2.5M$

**StackingRegressor**

Em vez de só tirar a média, Stacking treina um **modelo meta** que aprende a melhor forma de combinar as predições.

É tipo ter vários especialistas dando opinião e um coordenador que sabe quanto peso dar pra cada um.

**Quando usar?** Quando você quer extrair os últimos 0.5-1% de performance. Mas cuidado: mais complexidade = mais chance de overfitting.


```python
from sklearn.ensemble import VotingRegressor, StackingRegressor
from sklearn.linear_model import LinearRegression
from sklearn.svm import SVR

lin = LinearRegression()
svr = SVR(kernel='rbf', C=10, epsilon=0.1)
small_rf = RandomForestRegressor(n_estimators=120, random_state=7, n_jobs=-1)

vote = VotingRegressor([
    ('lin', lin),
    ('svr', svr),
    ('rf', small_rf)
])
vote.fit(X_train, y_train)
pred_vote = vote.predict(X_test)
print(f"VotingRegressor R²: {r2_score(y_test, pred_vote):.3f}")

stack = StackingRegressor(
    estimators=[('lin', LinearRegression()), ('svr', SVR(kernel='rbf', C=10, epsilon=0.1)), ('rf', RandomForestRegressor(n_estimators=150, random_state=11))],
    final_estimator=GradientBoostingRegressor(learning_rate=0.05, n_estimators=200, max_depth=3, random_state=42),
    passthrough=False,
    n_jobs=-1
)
stack.fit(X_train, y_train)
pred_stack = stack.predict(X_test)
print(f"StackingRegressor R²: {r2_score(y_test, pred_stack):.3f}")
```

    VotingRegressor R²: 0.623
    StackingRegressor R²: 0.769
    StackingRegressor R²: 0.769
    

### Entendendo Bias vs Variância com Ensembles

Lembra do dilema bias-variância?

- **Alta variância**: modelo muda muito com pequenas alterações nos dados (overfitting)
- **Alto bias**: modelo é simples demais e não captura padrões (underfitting)

**Como cada ensemble lida com isso:**

**Árvore única profunda:**
- Bias: Baixo ✅ (captura tudo)
- Variância: Alta ❌ (instável)

**Bagging / Random Forest:**
- Reduz **variância** drasticamente (média estabiliza)
- Mantém bias relativamente baixo
- Solução maioria dos casos

**Gradient Boosting:**
- Reduz **bias** progressivamente (corrige erros)
- Se exagerar, pode aumentar variância (overfit)
- Precisa tunnar bem

**Dicas práticas:**

Se seu modelo tá overfitting (treino ótimo, teste ruim):
- ↓ `max_depth` (árvores mais rasas)
- ↑ `min_samples_leaf` (folhas maiores)
- ↓ `learning_rate` (boosting mais conservador)

Se seu modelo tá underfitting (treino e teste ruins):
- ↑ `n_estimators` (mais árvores)
- ↑ `max_depth` (mais profundidade)

### Comparando Todos os Modelos

Agora que treinamos vários ensembles, vamos botar todos lado a lado e ver quem performou melhor no nosso dataset de casas da Califórnia!


```python
# Garantir que já existem variáveis dos modelos (base_tree, bag, rf, results_gb, vote, stack)
# Pegar melhor Gradient Boosting (maior R²)
best_gb_lr, best_gb_r2, best_gb_rmse = sorted(results_gb, key=lambda x: x[1], reverse=True)[0]

comparacao = []
# Regressor base
comparacao.append(['Árvore Única', r2_base, rmse_base])
comparacao.append(['Bagging', r2_bag, rmse_bag])
comparacao.append(['RandomForest', r2_rf, rmse_rf])
comparacao.append([f'GradientBoosting(lr={best_gb_lr})', best_gb_r2, best_gb_rmse])
comparacao.append(['Voting', r2_score(y_test, pred_vote), mean_squared_error(y_test, pred_vote)])
comparacao.append(['Stacking', r2_score(y_test, pred_stack), mean_squared_error(y_test, pred_stack)])

res_df = pd.DataFrame(comparacao, columns=['Modelo','R2','RMSE']).sort_values('R2', ascending=False)
print(res_df)

plt.figure(figsize=(7,4))
plt.bar(res_df['Modelo'], res_df['R2'])
plt.xticks(rotation=40, ha='right')
plt.ylabel('R²')
plt.title('Comparação de Modelos - Ensembles Regressão')
plt.tight_layout()
plt.show()

```

                         Modelo        R2      RMSE
    3  GradientBoosting(lr=0.2)  0.814240  0.248985
    2              RandomForest  0.776306  0.299829
    5                  Stacking  0.769270  0.309261
    1                   Bagging  0.761046  0.320283
    4                    Voting  0.622896  0.505453
    0              Árvore Única  0.484958  0.690340
    


    
![png](case_ia_files/case_ia_465_1.png)
    


### Conclusão

Algumas coisas que é interessante tirar desse capitulo:

**TL;DR:**

- **Random Forest**: Seu melhor amigo. Funciona bem na maioria dos casos, não precisa de muito tuning. Comece sempre por ele.
- **Gradient Boosting**: Consegue extrair mais performance.
- **Voting/Stacking**: Quando você quer os últimos 1-2% de melhoria. Combina modelos diferentes (Linear + SVR + RF) pra capturar aspectos complementares.

**Seu Workflow Prático:**

1. **Baseline**: Testa um RandomForest com configurações padrão
2. **Tuning**: Ajusta `n_estimators`, `max_depth`, `min_samples_leaf`
3. **Boosting**: Experimenta GradientBoosting (ou XGBoost/LightGBM)
4. **Ensemble heterogêneo**: Se ainda não tá bom, combina modelos diferentes com Voting/Stacking

**Cuidados:**

- ⚠️ **Computação**: Ensembles são mais lentos que modelos únicos (você tá treinando dezenas/centenas de árvores)
- ⚠️ **Interpretabilidade**: Fica mais difícil explicar "por que o modelo decidiu isso". Use feature importance e SHAP values quando precisar.
- ⚠️ **Overfitting**: Boosting agressivo pode overfitar

**E Agora?**

Se você gostou de Gradient Boosting, o próximo passo natural é aprender **XGBoost**, **LightGBM** e **CatBoost** e— versões turbinadas com:
- Early stopping automático
- Regularização
- Otimizações de velocidade
- GPU support

Esses são os modelos que ganham competições de Kaggle. E você já tem a base pra entendê-los!

*E quem sabe, adicionar esse material aqui e marcar seu nome*

---
