---
title: Programação Orientada a Objetos
tags:
  - "#trilha/ciencia-de-dados"
  - nivel/avancado
---
_**Autores:** Gabriel Navarro_
# **Módulo 1 - Introdução a Programação Orientada a Objetos**

## **1.1 - O que é Programação Orientada a Objetos ?**

A Programação Orientada a Objetos *(POO)* é um estilo de programação que organiza o código em unidades chamadas objetos. Esses objetos representam entidades do mundo real e possuem características *(dados)* e ações *(comportamentos)*. **Esse modelo facilita a organização do código e torna os programas mais intuitivos e modulares**.

Em suma, esse paradigma visa aproximar a programação da forma como percebemos o mundo real, onde objetos interagem entre si para realizar tarefas.

#### **Diferença entre Programação Procedural e Programação Orientada a Objetos**

A programação procedural, que geralmente é a primeira abordagem que aprendemos, organiza o código em funções e estruturas de controle, mantendo os dados e os procedimentos separados. Por outro lado, a Programação Orientada a Objetos encapsula dados e comportamentos dentro de objetos, promovendo uma estrutura mais modular, facilitando a reutilização e a manutenção do código.

##### *Exemplo de Programação Procedural*


```python
# Procedural: Funções manipulam diretamente os dados
def criar_conta(nome, saldo):
    return {"nome": nome, "saldo": saldo}

def depositar(conta, valor):
    conta["saldo"] += valor

def exibir_saldo(conta):
    print(f"Saldo de {conta['nome']}: {conta['saldo']}")

# Uso
diego = criar_conta("Diego", 1000)
depositar(diego, 500)
exibir_saldo(diego)
```

    Saldo de Diego: 1500
    

##### *Exemplo de Programação Orientada a Objetos*


```python
# Orientado a Objetos: Criamos uma classe Conta
class Conta:
    def __init__(self, nome, saldo):
        self.nome = nome
        self.saldo = saldo
    
    def depositar(self, valor):
        self.saldo += valor
    
    def exibir_saldo(self):
        print(f"Saldo de {self.nome}: {self.saldo}")

# Uso
diego = Conta("Diego", 1000)
diego.depositar(500)
diego.exibir_saldo()
```

    Saldo de Diego: 1500
    

##### **Benefícios da Programação Orientada a Objetos**

- Modularidade: O código é dividido em objetos independentes, facilitando a manutenção.
  
- Reutilização de Código: Classes podem ser reutilizadas em diferentes partes do projeto.
  
- Encapsulamento: Protege os dados do objeto e permite melhor controle de acesso.
  
- Flexibilidade e Extensibilidade: É fácil adicionar novas funcionalidades.
  
- Facilidade na modelagem: Permite criar representações próximas ao mundo real

## **1.2 - Definições fundamentais**

### **Classes**

#### **Definição intuitiva**

**Uma classe pode ser entendida como um molde ou projeto.**

Exemplo intuitivo:
Imagine que você quer construir várias casas. Contudo, antes de começar, precisa de um projeto que detalhe:

- Número de quartos
  
- Localização da porta
  
- Tamanho das janelas
  
- E outros detalhes importantes
  
**Esse projeto não é uma casa de verdade, mas define todas as informações necessárias para construir quantas casas você 
quiser. Esse projeto é o que chamamos de classe.**

#### **Classes na programação**

Em termos de programação, uma classe funciona da mesma forma. Ela é um projeto que define as características (atributos)
e os comportamentos (métodos) de um tipo específico de elemento.

Por exemplo, se quisermos representar carros no nosso programa, criamos uma classe chamada Carro. Essa classe vai dizer:

- Quais informações cada carro terá (cor, modelo, ano de fabricação).
  
- Quais ações o carro pode realizar (acelerar, frear, buzinar).

#### **Outra forma de pensar em uma classe**

**Uma classe também pode ser vista como a criação de um novo tipo de dado.**

Em Python, já temos tipos de dados como int *(para números inteiros)*, str *(para textos)* e float *(para números decimais)*.
**Quando você cria uma classe, está definindo seu próprio tipo de dado personalizado, com características e comportamentos únicos**.
Por exemplo:

Enquanto o tipo int serve para representar números inteiros. A classe Carro pode servir para representar carros, com todas 
as informações que você quiser incluir (como marca, cor e velocidade).


#### **Exemplo prático**


```python
# Vamos começar a criar uma classe para representar carros

# Primeiro, vamos criar a estrutura base da nossa classe.
# Neste momento, ela é apenas um "projeto" vazio, sem características nem comportamentos.

class Carro:
    pass    # Usamos a palavra-chave 'pass' para indicar que a classe está vazia por enquanto.
            # Isso evita erros de sintaxe e nos permite continuar desenvolvendo o código depois.    
```

### **Atributos**

#### **Definição intuitiva**


Depois de entender o que é uma classe (um molde ou projeto), **podemos pensar nos atributos como as características ou propriedades que definimos nesse projeto**.

Exemplo intuitivo:
Imagine novamente o projeto de uma casa. Esse projeto descreve várias características, como:

- Número de quartos
- Cor das paredes
- Tamanho das janelas
- E outros detalhes importantes

Esses detalhes são os atributos da casa. Quando você constrói várias casas com base no mesmo projeto, cada uma pode ter atributos diferentes. 

Por exemplo:

Uma casa pode ter 3 quartos e paredes azuis. Enquanto outra pode ter 4 quartos e paredes brancas.

**Ou seja, mesmo que o projeto (classe) seja o mesmo, os atributos permitem que cada casa construída tenha suas próprias características únicas.**

#### **Atributos na programação**

**Em termos de programação, atributos são as informações que descrevem algo criado a partir de uma classe.**

Por exemplo, se temos uma classe chamada Carro, os atributos podem ser:

- cor (ex: vermelho, azul)
- modelo (ex: Toyota, Ford)
- ano de fabricação (ex: 2020, 2023)
- velocidade atual (ex: 0 km/h, 60 km/h)
  
Cada carro que criamos a partir da classe Carro pode ter atributos diferentes. **Assim como no exemplo das casas, o molde é o mesmo, mas os detalhes (atributos) mudam de um carro para outro.**

#### **Exemplo prático**


```python
# 2. Adicionando Atributos

# Agora vamos definir as características (atributos) que cada carro terá.
# Para isso, usamos uma função especial chamada __init__ 
# (explicaremos melhor sobre funções/métodos especiais em tópicos futuros).
# O __init__ é automaticamente executado sempre que criamos um novo carro a partir da nossa classe.
# Ele é responsável por inicializar o carro com as informações que fornecemos,
# ou seja, atribui os valores passados como parâmetros (marca, modelo, ano, cor)
# às características específicas do carro, definindo seus atributos iniciais.

class Carro:
    def __init__(self, marca, modelo, ano, cor):
        # Observação importante:
        # O parâmetro 'self' representa o próprio carro que está sendo criado.
        # Ele é usado para acessar e definir as características (atributos) do carro,
        # associando os valores que passamos como parâmetros (marca, modelo, ano, cor)
        # às propriedades permanentes do carro (como self.marca, self.modelo, etc.).
        
        self.marca = marca       # 'self.marca' é o atributo do carro, ou seja, a marca que será armazenada no carro.
                                 # 'marca' (sem o self) é o valor que passamos quando criamos o carro.
                                 # Exemplo: se criarmos Carro("Toyota", "Corolla", 2020, "Vermelho"),
                                 # o valor "Toyota" será armazenado em self.marca.
                                 
        self.modelo = modelo     # 'self.modelo' é o atributo que guarda o modelo do carro.
                                 # 'modelo' é o valor passado quando o carro é criado.
                                 # Exemplo: "Corolla" será armazenado em self.modelo.
                                 
        self.ano = ano           # 'self.ano' é o atributo que representa o ano de fabricação do carro.
                                 # 'ano' é o valor passado na criação do carro.
                                 # Exemplo: 2020 será armazenado em self.ano.
                                 
        self.cor = cor           # 'self.cor' é o atributo que guarda a cor do carro.
                                 # 'cor' é o valor fornecido ao criar o carro.
                                 # Exemplo: "Vermelho" será armazenado em self.cor.
```

### **Métodos**

#### **Definição intuitiva**

Agora que sabemos que uma classe é um projeto e que os atributos são as características desse projeto, **podemos pensar nos métodos como as ações ou comportamentos que algo criado a partir da classe pode realizar**.

Exemplo intuitivo:
Voltando ao exemplo da casa, imagine que o projeto não define apenas as características (como o número de quartos), mas também o que a casa pode fazer, como:

- Abrir portas
- Acender luzes
- Trancar janelas

**Essas ações são os métodos da casa. Cada casa construída a partir do projeto pode realizar essas ações.**


#### **Métodos na programação**

**Na programação, métodos são funções associadas a uma classe. Eles definem o que os objetos (que são criados a partir da classe) podem fazer**.

Se criarmos uma classe Carro, podemos definir métodos como:

- acelerar() – para aumentar a velocidade do carro.
- frear() – para reduzir a velocidade.
- buzinar() – para emitir um som de buzina.
  
**Os métodos usam ou modificam os atributos do carro**. Por exemplo, o método acelerar() pode aumentar o valor do atributo velocidade atual.

#### **Exemplo prático**


```python
# 3. Adicionando Comportamentos (criando métodos)

# Agora vamos adicionar comportamentos que o carro pode realizar.
# Para isso, criaremos métodos, que são funções definidas dentro da classe.
# Esses métodos descrevem ações específicas que o carro pode executar, como acelerar, frear ou buzinar.
# Com isso, o carro deixa de ser apenas um conjunto de informações (atributos) e passa a interagir com o ambiente,
# simulando comportamentos do mundo real.

class Carro:
    def __init__(self, marca, modelo, ano, cor):
        self.marca = marca
        self.modelo = modelo
        self.ano = ano
        self.cor = cor
        self.velocidade = 0  # Começamos com o carro parado

    def acelerar(self, incremento):
        # O método acelerar aumenta o valor do atributo 'velocidade' do carro.
        # O parâmetro 'incremento' define o quanto a velocidade deve aumentar.
        # Por exemplo, se o carro estiver a 20 km/h e o incremento for 10, 
        # a nova velocidade será 30 km/h.
        
        self.velocidade += incremento
        print(f"O carro acelerou para {self.velocidade} km/h.")

    def frear(self, decremento):
        # O método frear reduz o valor do atributo 'velocidade' do carro.
        # O parâmetro 'decremento' define o quanto a velocidade deve diminuir.
        # Por exemplo, se o carro estiver a 30 km/h e o decremento for 10, 
        # a nova velocidade será 20 km/h. Se tentar reduzir mais do que a velocidade atual,
        # a velocidade será ajustada para 0 km/h.
        
        self.velocidade = max(0, self.velocidade - decremento) # A função max(0, ...) garante que a velocidade nunca será negativa.
        print(f"O carro desacelerou para {self.velocidade} km/h.")

    def buzinar(self):
        # O método buzinar simula o som da buzina do carro.
        # Quando chamado, ele simplesmente imprime "Bii Bii!".
        
        print("Bii Bii!")
```

#### **Métodos especiais**

##### **Definição intuitiva**

Agora que sabemos o que são métodos (as ações que um objeto pode realizar), podemos falar sobre os métodos especiais.

**Os métodos especiais são ações especiais que a linguagem de programação já reconhece automaticamente**. Em Python, esses métodos têm uma nomenclatura distinta: começam e terminam com dois underlines (por exemplo, __init__). Os mais comuns são:

- __init__ – Método de inicialização (construtor):

        O __init__ é chamado automaticamente quando criamos uma instância da classe. Ele é conhecido como construtor porque sua função essencial é construir o objeto, ou seja, definir seus atributos iniciais e garantir que o objeto (conceito que exploraremos em breve) esteja pronto para uso.

        Em termos simples, construtores configuram o estado inicial do objeto, estabelecendo os valores dos atributos que o definem. Por exemplo, ao criar um carro, o construtor define sua marca, modelo, ano e cor. Sem o construtor, o objeto seria criado, mas não teria características definidas.

- __str__ – Método de representação textual:

        Define como o objeto será exibido quando usarmos a função print(). Esse método retorna uma descrição legível do objeto, facilitando a visualização de suas informações.

##### **Exemplo prático**


```python
# 3. Adicionando Comportamentos Especiais (criando métodos especiais)

# Agora vamos adicionar um comportamento especial com o método __str__, que define como o objeto será representado como texto.
# Também vamos destacar novamente o papel do método especial __init__, responsável por inicializar o objeto.

class Carro:
    def __init__(self, marca, modelo, ano, cor):
        # O método __init__ é um método especial, também conhecido como construtor, e é chamado automaticamente 
        # sempre que criamos uma nova instância da classe Carro (iremos explorar o conceito de instância em breve).
        # Construtores, como o __init__, têm a função de inicializar o objeto, configurando seus atributos iniciais.
        # Neste caso, o carro é inicializado com as informações fornecidas: marca, modelo, ano, cor e velocidade.
        
        self.marca = marca
        self.modelo = modelo
        self.ano = ano
        self.cor = cor
        self.velocidade = 0

    def acelerar(self, incremento):
        self.velocidade += incremento
        print(f"O carro acelerou para {self.velocidade} km/h.")

    def frear(self, decremento):
        self.velocidade = max(0, self.velocidade - decremento)
        print(f"O carro desacelerou para {self.velocidade} km/h.")

    def buzinar(self):
        print("Bii Bii!")

    def __str__(self):
        # O método __str__ é chamado automaticamente quando usamos a função print() em um objeto Carro.
        # Ele retorna uma string que descreve o carro de forma legível, incluindo marca, modelo, ano, cor e velocidade atual.
        
        return f"{self.marca} {self.modelo} ({self.ano}), cor {self.cor}, velocidade atual: {self.velocidade} km/h"

```

### **Objetos**

#### **Definição intuitiva**

Agora que sabemos o que é uma classe (projeto), o que são atributos (características) e o que são métodos (ações), podemos entender o que é um objeto.

**Um objeto é um elemento concreto criado a partir da classe (projeto)**. Ele tem atributos definidos e é capaz de realizar ações (métodos).

Exemplo intuitivo:
**Se a classe é o projeto da casa, o objeto é a casa real construída a partir desse projeto.**

Por exemplo:

- Casa 1: 3 quartos, paredes azuis, janelas grandes.
- Casa 2: 4 quartos, paredes brancas, janelas pequenas.
  
**Cada casa é um objeto que tem suas próprias características (atributos) e pode realizar ações (métodos), como abrir portas ou acender luzes.**

#### **Instância de uma classe**


**Uma instância é um termo técnico usado para descrever um objeto criado a partir de uma classe.**

Imagine que você tem o projeto de uma casa. Esse projeto descreve como a casa deve ser: quantos quartos, o tamanho da sala, a cor das paredes, etc. Quando você usa esse projeto para construir uma casa real, essa casa é algo concreto. Cada casa construída a partir desse mesmo projeto é única, mas todas seguem a mesma estrutura.

Na programação, acontece o mesmo: a classe é o projeto que define as características e comportamentos de algo. Quando criamos algo com base nesse projeto, temos um objeto. Cada objeto criado é uma instância única desse projeto, com suas próprias características. 

Por exemplo, com a classe Carro, podemos criar carro1 e carro2, cada um representando uma instância individual (ou seja, um objeto único criado a partir da classe), com sua própria marca, modelo e cor.


#### **Objetos na programação**

**Na programação, um objeto é uma instância da classe, ou seja, um exemplo específico da estrutura que definimos.**

Exemplo prático:

Quando criarmos um carro específico no nosso programa, utilizando a classe Carro que estamos desenvolvendo, faremos algo assim:

```python
meu_carro = Carro("Toyota", "Corolla", 2020, "vermelho")
```

Esse meu_carro é um objeto da classe Carro, ou seja, uma instância da classe Carro. Ele tem:

Atributos:

- marca = Toyota
- modelo = Corolla
- ano = 2020
- cor = vermelho

Métodos que ele pode realizar:

- meu_carro.acelerar() – aumenta a velocidade.
- meu_carro.frear() – diminui a velocidade.
- meu_carro.buzinar() – toca a buzina.

Cada objeto criado a partir da classe Carro representa uma instância individual, com atributos próprios e capaz de realizar as ações definidas nos métodos da classe.

#### **Exemplo prático**


```python
# Relembrando como definimos a nossa classe Carro

class Carro:
    def __init__(self, marca, modelo, ano, cor):
        self.marca = marca
        self.modelo = modelo
        self.ano = ano
        self.cor = cor
        self.velocidade = 0  # Começamos com o carro parado

    def acelerar(self, incremento):
        # O método acelerar aumenta o valor do atributo 'velocidade' do carro.
        # O parâmetro 'incremento' define o quanto a velocidade deve aumentar.
        # Por exemplo, se o carro estiver a 20 km/h e o incremento for 10, 
        # a nova velocidade será 30 km/h.
        
        self.velocidade += incremento
        print(f"O carro acelerou para {self.velocidade} km/h.")

    def frear(self, decremento):
        # O método frear reduz o valor do atributo 'velocidade' do carro.
        # O parâmetro 'decremento' define o quanto a velocidade deve diminuir.
        # Por exemplo, se o carro estiver a 30 km/h e o decremento for 10, 
        # a nova velocidade será 20 km/h. Se tentar reduzir mais do que a velocidade atual,
        # a velocidade será ajustada para 0 km/h.
        
        self.velocidade = max(0, self.velocidade - decremento) # A função max(0, ...) garante que a velocidade nunca será negativa.
        print(f"O carro desacelerou para {self.velocidade} km/h.")

    def buzinar(self):
        # O método buzinar simula o som da buzina do carro.
        # Quando chamado, ele simplesmente imprime "Bii Bii!".
        
        print("Bii Bii!")
        
    def __str__(self):
    # O método __str__ é chamado automaticamente quando usamos a função print() em um objeto Carro.
    # Ele retorna uma string que descreve o carro de forma legível, incluindo marca, modelo, ano, cor e velocidade atual.
    
        return f"{self.marca} {self.modelo} ({self.ano}), cor {self.cor}, velocidade atual: {self.velocidade} km/h"
```


```python
# 4. Criando um Objeto

# Agora que temos a classe Carro pronta, com seus atributos e métodos definidos, vamos criar um objeto do tipo Carro.
# Esse objeto é uma instância da classe Carro, representando um carro específico com características definidas.

# Criando uma instância da classe Carro com marca Toyota, modelo Corolla, ano 2020 e cor Vermelho.
meu_carro = Carro("Toyota", "Corolla", 2020, "Vermelho")  

# Agora vamos utilizar os métodos da classe para ver o comportamento desse objeto em ação:
meu_carro.acelerar(30)  # Acelera o carro para 30 km/h.
print(f"Velocidade atual do meu_carro: {meu_carro.velocidade} km/h")  # Exibe a velocidade atual após acelerar.

meu_carro.buzinar()     # O carro emite o som da buzina: "Bii Bii!".

meu_carro.frear(10)     # Reduz a velocidade do carro para 20 km/h.
print(f"Velocidade atual do meu_carro após frear: {meu_carro.velocidade} km/h")  # Exibe a velocidade após frear.

print("\n------------------------------------\n")

# Podemos criar várias outras instâncias da classe Carro, cada uma representando um carro diferente:
carro_azul = Carro("Ford", "Focus", 2018, "Azul")
carro_preto = Carro("Honda", "Civic", 2022, "Preto")

# Cada instância tem seus próprios atributos e pode executar os mesmos métodos de forma independente:
carro_azul.acelerar(50)  # O carro azul acelera para 50 km/h.
print(f"Velocidade atual do carro_azul: {carro_azul.velocidade} km/h")  # Exibe a velocidade atual do carro azul.

carro_preto.buzinar()    # O carro preto buzina: "Bii Bii!".

carro_azul.frear(20)     # O carro azul reduz a velocidade para 30 km/h.
print(f"Velocidade atual do carro_azul após frear: {carro_azul.velocidade} km/h")  # Exibe a velocidade após frear.

# Para acessar os atributos dos objetos, basta referenciar o atributo desejado:
print(f"O {meu_carro.marca} {meu_carro.modelo} é da cor {meu_carro.cor} e foi fabricado em {meu_carro.ano}.")
print(f"O {carro_azul.marca} {carro_azul.modelo} é da cor {carro_azul.cor} e foi fabricado em {carro_azul.ano}.")
print(f"O {carro_preto.marca} {carro_preto.modelo} é da cor {carro_preto.cor} e foi fabricado em {carro_preto.ano}.")

```

    O carro acelerou para 30 km/h.
    Velocidade atual do meu_carro: 30 km/h
    Bii Bii!
    O carro desacelerou para 20 km/h.
    Velocidade atual do meu_carro após frear: 20 km/h
    
    ------------------------------------
    
    O carro acelerou para 50 km/h.
    Velocidade atual do carro_azul: 50 km/h
    Bii Bii!
    O carro desacelerou para 30 km/h.
    Velocidade atual do carro_azul após frear: 30 km/h
    O Toyota Corolla é da cor Vermelho e foi fabricado em 2020.
    O Ford Focus é da cor Azul e foi fabricado em 2018.
    O Honda Civic é da cor Preto e foi fabricado em 2022.
    

### **Exercício: Simulando uma Carteira de Investimentos**

Imagine que você é responsável por desenvolver um sistema simples de controle de investimentos para um investidor iniciante. Esse sistema precisa acompanhar diferentes ativos, como ações e títulos de renda fixa, calculando o valor atual de cada ativo e o retorno obtido.

#### **Parte 1: Criando a Classe AtivoFinanceiro**

1. Crie uma classe chamada AtivoFinanceiro com os seguintes **atributos**:

   - **nome**: Nome do ativo (ex: "Ação Petrobras").
   - **valor_investido**: Valor inicial investido no ativo.
   - **valor_atual**: Valor atual do ativo.


```python
# Seu código aqui
```

2. Atualize o código acima criando métodos para:

   - Atualizar o valor atual do ativo.
   - Calcular o retorno percentual do ativo: 
    
        $Retorno \ (\%) = \dfrac{Valor \ atual - Valor \ Investido}{Valor \ Investido}*100$
  


```python
# Seu código aqui
```

#### **Parte 2: Criando Objetos e Testando a Classe**

1. Utilizando a classe AtivoFinanceiro criada anteriormente, crie dois ativos financeiros distintos:

   - Um ativo de renda variável (ex: "Ação Itaú", valor investido R$ 1000, valor atual R$ 1200).
   - Um ativo de renda fixa (ex: "Tesouro Direto", valor investido R$ 2000, valor atual R$ 2050).

2. Atualize o valor de um dos ativos.

3. Calcule e imprima o retorno percentual de cada ativo.


```python
# Seu código aqui
```

#### **Exercício Extra 1**

Personalize a classe AtivoFinanceiro para exibir informações detalhadas sobre o ativo quando o objeto for impresso.

Ao utilizar o comando print() em um objeto da classe AtivoFinanceiro, ele deve mostrar:

- Nome do Ativo
- Valor Investido
- Valor Atual
- Retorno Percentual (lucro ou prejuízo em relação ao valor investido)
  
**Dica:**
**Utilize o método especial __str__, que permite definir como o objeto será representado em formato de texto. Esse método é automaticamente chamado quando usamos print() no objeto.**


```python
# Seu código aqui
```

#### **Parte 3: Criando uma Simples Carteira de Investimentos**

Agora que você já criou ativos individuais, vamos criar uma Carteira de Investimentos.

1. Crie uma classe chamada CarteiraInvestimentos.

    - Essa classe deve ter um atributo ativos, que será uma lista de objetos do tipo AtivoFinanceiro.
  
2. Crie métodos para:
   
    - Adicionar um novo ativo à carteira.
    - Calcular o valor total investido.
    - Calcular o valor atual total.
    - Calcular o retorno total da carteira.


```python
# Seu código aqui
```

#### **Exercício Extra 2**

Personalize a classe CarteiraInvestimentos para exibir informações detalhadas sobre a carteira quando o objeto for impresso.

Ao utilizar o comando print() em um objeto da classe CarteiraInvestimentos, ele deve mostrar:

- Lista de todos os ativos financeiros na carteira, com seus respectivos detalhes (nome do ativo, valor investido, valor atual e retorno percentual).
- Valor Total Investido na carteira.
- Valor Atual Total da carteira.
- Retorno Percentual Total (lucro ou prejuízo considerando todos os ativos da carteira).

**Dica:**
**Utilize o método especial __str__, que permite definir como o objeto será representado em formato de texto. Esse método é automaticamente chamado quando usamos print() no objeto.**


```python
# Seu código aqui
```

#### **Parte 4: Testando a Carteira**

1. Crie uma carteira de investimentos utilizando a classe CarteiraInvestimentos desenvolvida no exercício anterior.

   - Pense na carteira como um portfólio real, onde você gerencia diversos ativos financeiros.

   
2. Adicione à sua carteira os dois ativos financeiros que você criou anteriormente.
   - Inclua tanto a ação da empresa quanto o ativo de renda fixa para observar como diferentes tipos de investimentos impactam o desempenho da carteira.

   
3. Calcule e imprima os seguintes resultados:
    - Valor Total Investido: A soma do valor inicial aplicado em todos os ativos.
    - Valor Atual Total: O valor atual combinado de todos os ativos após as atualizações de mercado.
    - Retorno Total da Carteira: O percentual de lucro ou prejuízo da carteira como um todo.

**Dica: Use o método __str__ que você implementou para exibir os detalhes da carteira de forma clara e organizada. Isso simula um relatório financeiro, como aqueles que investidores e gestores recebem periodicamente!**


```python
# Seu código aqui
```

# **Módulo 2 - Avançando em Programação Orientada a Objetos**

## **2.1 - Os 4 Conceitos Fundamentais da Programação Orientada a Objetos**

### **Abstração**

#### **Definição intuitiva**

**Abstração é o processo de esconder detalhes desnecessários e mostrar apenas o que é essencial**.

Imagine um carro. Quando você dirige, não precisa saber exatamente como o motor funciona internamente, quais circuitos elétricos estão ativados ou como o combustível é processado. Você apenas interage com o carro por meio do volante, pedais e painel de controle. Ou seja, você se preocupa apenas com o que é necessário para dirigir. **Isso é abstração: mostrar apenas as informações relevantes e ocultar os detalhes internos**.

#### **Abstração na programação**

Na programação, a abstração funciona da mesma forma. Criamos classes que representam conceitos do mundo real, mas **escondemos os detalhes internos de implementação e mostramos apenas o necessário para quem usa a classe**.

**Por exemplo, podemos ter uma classe OrdemDeCompra que permite um investidor comprar ações, sem precisar expor os detalhes de como a ordem é processada na bolsa de valores**.


```python
class OrdemDeCompra:
    def __init__(self, ativo, quantidade, preco):
        self.ativo = ativo
        self.quantidade = quantidade
        self.preco = preco

    def executar(self):
        print(f"Enviando ordem de compra: {self.quantidade} ações de {self.ativo} a R$ {self.preco:.2f}")

# Criando uma ordem de compra
ordem = OrdemDeCompra("PETR4", 100, 32.50)
ordem.executar()  # Saída esperada: "Enviando ordem de compra: 100 ações de PETR4 a R$ 32.50"
```

    Enviando ordem de compra: 100 ações de PETR4 a R$ 32.50
    

**Aqui, a abstração permite que o usuário envie ordens de compra sem precisar saber como a ordem é roteada para o mercado, como os custos são calculados ou como os dados são armazenados. A classe esconde esses detalhes e expõe apenas o necessário para operar.**

*Vale destacar que, no exemplo acima, o processo de emissão da ordem de compra não foi efetivamente implementado. O objetivo é apenas ilustrar o conceito de abstração. Mesmo que a lógica real de envio de ordens fosse adicionada, a maneira como o usuário interage com a classe permaneceria a mesma — bastaria chamar o método executar(), sem precisar se preocupar com os detalhes internos. Essa é a essência da abstração na POO.*

### **Encapsulamento**

#### **Definição intuitiva**

**Encapsulamento significa proteger os dados de acesso indevido e garantir que eles só possam ser modificados de maneira controlada**.

Pense em um cofre de banco. Você não pode simplesmente abrir e pegar o dinheiro sem passar pelos procedimentos adequados. Você precisa de uma chave ou senha para acessar o conteúdo.

**No mundo da programação, o encapsulamento funciona de maneira semelhante: os atributos e métodos de um objeto podem ser protegidos para que só possam ser acessados ou modificados de maneira controlada**.

#### **Encapsulamento na programação**

Em programação, usamos modificadores de acesso para restringir o acesso direto a certos atributos e métodos de uma classe. **Em Python, seguimos uma convenção para diferenciar atributos e métodos públicos, protegidos e privados.**

Métodos e atributos públicos, protegidos e privados em Python:
- Públicos: Podem ser acessados diretamente de fora da classe.
  
- Protegidos (_atributo | _método): Devem ser tratados como internos à classe, mas ainda podem ser acessados fora dela (por convenção, não por restrição técnica).
  
- Privados (__atributo | __método): Não podem ser acessados diretamente de fora da classe, pois o Python aplica uma modificação de nome (name mangling).




```python
class ContaBancaria:
    def __init__(self, titular, saldo):
        self.titular = titular   # Atributo público
        self._saldo = saldo      # Atributo protegido (_atributo)
        self.__senha = "1234"    # Atributo privado (__atributo)

    def depositar(self, valor):  # Método público
        self._saldo += valor

    def sacar(self, valor):  # Método público
        if valor <= self._saldo:
            self._saldo -= valor
        else:
            print("Saldo insuficiente")

    def get_saldo(self):  # Método público 
        return self._saldo  

    def __verificar_senha(self, senha):  # Método privado (__método)
        return senha == self.__senha  

# Criando um objeto da classe ContaBancaria
minha_conta = ContaBancaria("Gabriel", 1000)

# Acessando métodos públicos
print(minha_conta.get_saldo())  # Saída esperada: 1000
minha_conta.sacar(200)
print(minha_conta.get_saldo())  # Saída esperada: 800

# Tentando acessar um atributo protegido (possível, mas não recomendado)
print(minha_conta._saldo)  # Saída esperada: 800

# Tentando acessar um atributo privado (não pode ser acessado diretamente)
# print(minha_conta.__senha)  # Isso geraria um erro!
# Porém, devido ao name mangling, podemos acessar manualmente (NÃO RECOMENDADO)
print(minha_conta._ContaBancaria__senha)  # Saída esperada: 1234
```

    1000
    800
    800
    1234
    

#### **Observação**

**Em Python, não existe efetivamente o conceito de atributos privados e protegidos como em linguagens como Java e C++.**

Isso acontece porque Python segue a filosofia de "somos todos adultos aqui" (We are all consenting adults here). Ou seja, em vez de impor restrições rígidas, Python confia que os desenvolvedores seguirão as convenções estabelecidas.

Por exemplo:

- Atributos protegidos (_atributo) **não são realmente protegidos** — é apenas uma convenção para indicar que devem ser tratados como internos à classe.
  
- Atributos privados (__atributo) também **não são verdadeiramente inacessíveis**, pois Python apenas renomeia (name mangling) o atributo, tornando-o acessível por _Classe__atributo.

**Imagine um cofre com um aviso escrito: "Favor não abrir sem permissão." O cofre está trancado? Não. Mas o aviso deixa claro que você não deveria mexer nele. O encapsulamento em Python funciona da mesma forma: o acesso aos dados não é bloqueado, mas há indicações claras de que certos atributos não devem ser modificados diretamente.**

### **Herança**

#### **Definição intuitiva**

**Herança permite criar novas classes a partir de classes existentes**, aproveitando e reutilizando código.

Imagine que uma empresa tem diferentes tipos de funcionários: estagiários, analistas e gerentes. Todos compartilham algumas características básicas, como nome e salário, mas têm responsabilidades diferentes. **Em vez de criar classes separadas do zero, podemos definir uma classe geral Funcionario e fazer com que Estagiario, Analista e Gerente herdem suas características básicas, adicionando apenas os detalhes específicos de cada um**.

#### **Herança na programação**

**Na programação, a herança permite que uma classe filha (subclasse) herde atributos e métodos de uma classe pai (superclasse). Isso evita duplicação de código e facilita a manutenção.**


```python
# Definição da classe pai (superclasse)
class Funcionario:
    def __init__(self, nome, salario):     
        self.nome = nome
        self.salario = salario

    def exibir_dados(self):
        print(f"Nome: {self.nome}, Salário: R$ {self.salario}")

# Definição da classe filho (subclasse) 
class Analista(Funcionario): # A sintaxe "class Analista(Funcionario)" indica que a subclasse Analista
                             # herda os atributos e métodos da superclasse Funcionario
                             
    def __init__(self, nome, salario, area):
        """
            O método __init__ da subclasse chama o __init__ da superclasse usando super().
            Isso evita a necessidade de reescrever a inicialização dos atributos nome e salario.
        """
        
        super().__init__(nome, salario)  # Chama o construtor da superclasse Funcionario
        self.area = area  # Adiciona um novo atributo exclusivo da subclasse

    def exibir_dados(self):
        """
            O método exibir_dados da subclasse reutiliza o método de mesmo nome da superclasse.
            Primeiro, chama super().exibir_dados(), que exibe nome e salário. Depois, adiciona 
            a exibição da área específica do Analista.
        """
        
        super().exibir_dados()  # Chama o método exibir_dados() da superclasse
        print(f"Área: {self.area}")  # Adiciona a nova informação exclusiva da subclasse

# Criando um objeto da classe Analista
ana = Analista("Ana", 5000, "TI")

# Chamando o método exibir_dados()
ana.exibir_dados()

# Saída esperada:
# Nome: Ana, Salário: R$ 5000
# Área: TI

# No exemplo acima, a classe Analista herda os atributos e métodos da classe Funcionario, 
# o que permite reutilizar a funcionalidade já definida. No entanto, ela tem a flexibilidade 
# de adicionar novos atributos, como o "area", e personalizar comportamentos, como fizemos 
# ao sobrescrever o método "exibir_dados()", para adaptar o comportamento da classe filha às necessidades específicas.
```

    Nome: Ana, Salário: R$ 5000
    Área: TI
    

#### **Em suma, o que significa herdar algo em POO?**

**Quando uma classe herda de outra, ela automaticamente recebe os atributos e métodos da classe pai. Isso significa que podemos:**

- **Criar objetos da subclasse e usar métodos da superclasse sem reimplementá-los**.

- **Adicionar novos atributos e métodos específicos da subclasse**.

- **Sobrescrever métodos para personalizar o comportamento da subclasse**.

Por exemplo, Analista herdou exibir_dados() de Funcionario, mas sobrescreveu esse método para exibir também a área de atuação. *(Esse comportamento de sobrescrever métodos é um exemplo clássico de polimorfismo, que veremos com mais detalhes no próximo tópico)*

### **Polimorfismo**

#### **Definição intuitiva**

**Polimorfismo significa 'muitas formas'. Esse conceito permite que classes relacionadas por herança tenham métodos com o mesmo nome, mas comportamentos diferentes.**

Imagine que uma empresa tem vários tipos de funcionários: estagiários, analistas e gerentes. Todos recebem salário, mas de formas diferentes:

- Estagiários recebem bolsa-auxílio.

- Analistas recebem salário fixo.

- Gerentes podem ter bônus adicionais.
  
Se quisermos calcular o pagamento de qualquer funcionário sem nos preocupar com o tipo específico dele, podemos usar o conceito de polimorfismo.

#### **Polimorfismo na programação**

Na programação, polimorfismo permite que métodos com o mesmo nome tenham implementações diferentes em classes relacionadas por herança. Isso torna o código mais flexível e reutilizável.

Vamos ver na prática:


```python
# Definição da classe base (superclasse)
class Funcionario:
    def __init__(self, nome, salario):
        """
            Inicializa os atributos nome e salario.
        """
        
        self.nome = nome
        self.salario = salario

    def calcular_pagamento(self):
        """
            Retorna o salário do funcionário. Este método pode ser sobrescrito em subclasses.
        """
        
        return self.salario

# Subclasse Estagiario herdando de Funcionario
class Estagiario(Funcionario):
    def __init__(self, nome, bolsa_auxilio):
        """
            Chama o construtor da superclasse passando a bolsa_auxilio como salário.
        """
        
        super().__init__(nome, bolsa_auxilio)

    def calcular_pagamento(self):
        """
            Sobrescreve o método calcular_pagamento da superclasse.
            Para estagiários, o pagamento é apenas a bolsa_auxilio (salario no contexto da superclasse).
        """
        
        return self.salario  

# Subclasse Gerente herdando de Funcionario
class Gerente(Funcionario):
    def __init__(self, nome, salario, bonus):
        """
            Chama o construtor da superclasse e adiciona o atributo bonus.
        """
        
        super().__init__(nome, salario)
        self.bonus = bonus

    def calcular_pagamento(self):
        """
            Sobrescreve o método calcular_pagamento da superclasse.
            Para gerentes, o pagamento inclui o salário e um bônus adicional.
        """
        
        return self.salario + self.bonus  

# Criando objetos de diferentes classes
funcionario1 = Funcionario("Carlos", 5000)
estagiario1 = Estagiario("Ana", 2000)
gerente1 = Gerente("Mariana", 8000, 2000)

# Chamando o mesmo método para diferentes tipos de funcionários
print(funcionario1.calcular_pagamento())  # 5000
print(estagiario1.calcular_pagamento())   # 2000
print(gerente1.calcular_pagamento())      # 10000 (salário + bônus)

# O que aconteceu aqui?
# Mesmo que Funcionario, Estagiario e Gerente tenham o método calcular_pagamento(),
# cada um se comporta de forma diferente. Isso é polimorfismo!
```

    5000
    2000
    10000
    

#### **Em Resumo**

- Polimorfismo permite que diferentes classes tenham métodos com o mesmo nome, mas comportamentos diferentes.
  
- Ele torna o código mais genérico e reutilizável, pois podemos tratar objetos de diferentes classes de forma uniforme.

# **Módulo 3 - Projeto Final, Curiosidades e Conclusões**

## **Projeto Final**

### **Contexto**

#### **📊 O que é uma Estratégia Quantitativa?**

Uma estratégia quantitativa é uma abordagem de investimento baseada em modelos matemáticos, estatísticos e computacionais para tomar decisões no mercado financeiro. Essas estratégias utilizam dados históricos e algoritmos para identificar padrões e executar operações de compra e venda de ativos de forma sistemática, reduzindo a influência de emoções humanas.

#### **🔍 O que é um Backtest e Por que Ele é Importante?**


Um backtest é o processo de testar uma estratégia de investimento utilizando dados históricos para avaliar seu desempenho antes de aplicá-la no mercado real. Esse processo é essencial para entender como uma estratégia teria se comportado em diferentes cenários do passado.

#### **✅ Por que fazer um backtest?**

Realizar um backtest oferece diversas vantagens que ajudam a tomar decisões mais informadas e seguras:

✔ Permite testar uma estratégia sem arriscar dinheiro real.

✔ Identifica pontos fortes e fracos do modelo antes da implementação.

✔ Ajuda a ajustar parâmetros e melhorar a robustez da estratégia.

✔ Evita decisões baseadas apenas em intuição, utilizando dados e evidências.

Com esses benefícios em mente, é fundamental contar com ferramentas que tornem o processo de backtesting mais eficiente e preciso. É aqui que entra o **Backtrader**.

#### **🚀 Como o Backtrader Facilita o Backtest?**

O Backtrader é uma biblioteca em Python projetada para automatizar o processo de backtesting, permitindo testar múltiplas estratégias com diferentes parâmetros de forma rápida e eficiente. Ele simplifica o trabalho de traders e analistas, tornando o desenvolvimento de estratégias quantitativas mais acessível.

**Vantagens do Backtrader**:

✔ Simulação realista → Gerencia a execução de ordens e a gestão de capital automaticamente.

✔ Suporte a múltiplos ativos → Teste estratégias em diversas ações, moedas e commodities.

✔ Indicadores embutidos → Inclui dezenas de indicadores como RSI, MACD e Médias Móveis.

✔ Visualização gráfica → Permite gerar gráficos detalhados com o desempenho da estratégia.

**Como essa biblioteca se relaciona com POO?**

- Abstração → O usuário apenas interage com a API sem precisar entender os detalhes internos do funcionamento do backtesting.

- Encapsulamento → Os dados do mercado e as regras de estratégia são protegidos e acessados apenas por métodos específicos.

- Herança → Criamos novas estratégias herdando da classe base bt.Strategy, evitando repetição de código.

- Polimorfismo → Diferentes estratégias podem ser implementadas, e todas interagem com o sistema de backtesting da mesma forma.

Em suma, o Backtrader transforma o processo de criação e teste de estratégias quantitativas em algo mais fácil, rápido e confiável. Com ele, traders e analistas podem validar suas ideias com dados históricos, ajustá-las conforme necessário e aplicá-las no mercado real com muito mais confiança.

#### **🔧 Sobre o Backtrader**

##### **1. bt.Strategy: A Classe Base das Estratégias**

**O que é?**

bt.Strategy é a classe base no Backtrader que define como criar estratégias de trading. Para implementar uma estratégia, você deve criar uma nova classe que herda dessa classe base.

**Por que é importante?**

Isso permite que você defina suas próprias regras de compra e venda, utilizando os métodos e atributos da classe base sem precisar reescrever toda a lógica do backtest.

##### **2. __init__: Inicializando a Estratégia**

**O que é?**

O método __init__ é usado para inicializar os atributos da sua estratégia, como indicadores técnicos (Médias Móveis, RSI, etc.). É aqui que você define o que será usado para tomar decisões.

**Exemplo:**

```python
    def __init__(self):
        # Inicializa dois indicadores de Média Móvel Simples (SMA).
        
        # Cria uma média móvel simples de curto prazo (10 períodos) usando o preço de fechamento dos dados fornecidos.
        self.ma_short = bt.indicators.SimpleMovingAverage(self.data.close, period=10)
        
        # Cria uma média móvel simples de longo prazo (30 períodos) usando o preço de fechamento dos dados fornecidos.
        self.ma_long = bt.indicators.SimpleMovingAverage(self.data.close, period=30)
```

##### **3. next: Definindo a Lógica da Estratégia**

**O que é?**

O método next é chamado a cada novo dado (cada candle diário, por exemplo). Aqui você define quando comprar ou vender com base nos seus indicadores.

**Exemplo:**
```python
    def next(self):
        if self.ma_short[0] > self.ma_long[0]:  # Se a média curta cruzar acima da longa
            self.buy()  # Comprar
        elif self.ma_short[0] < self.ma_long[0]:  # Se a média curta cruzar abaixo da longa
            self.sell()  # Vender
```

##### **4. Cerebro: O Cérebro do Backtrader**

**O que é?**
Cerebro é o motor do Backtrader que executa o backtest. Ele gerencia a estratégia, os dados, a alocação de capital e gera os resultados.

**Funções principais:**

- Adicionar a estratégia: cerebro.addstrategy(SuaEstrategia)

- Adicionar dados: cerebro.adddata(dados)

- Executar o backtest: cerebro.run()

- Plotar resultados: cerebro.plot()

##### **5. Dados: Alimentando o Backtest**

**O que é?**

O Backtrader aceita diferentes fontes de dados, como arquivos CSV ou dados do Yahoo Finance.

**Exemplo (Yahoo Finance):**

```python
    from backtrader.feeds import YahooFinanceData
    dados = YahooFinanceData(dataname='AAPL', fromdate=datetime(2020, 1, 1), todate=datetime(2023, 1, 1))
```

##### **6. Indicadores Técnicos no Backtrader**

**O que é?**
O Backtrader já vem com diversos indicadores técnicos, como Médias Móveis, RSI, MACD, entre outros.

**Exemplo (Média Móvel):**
```python
    self.ma = bt.indicators.SimpleMovingAverage(self.data.close, period=20)
```

##### **7. Visualização Gráfica**

**O que é?**

O Backtrader gera gráficos automáticos mostrando o desempenho da sua estratégia.

**Exemplo:**

```python
    cerebro.plot()
```

### **📌 Projeto Final: Estratégia de Trading Orientada a Objetos com Backtrader**

Neste projeto final, desenvolveremos um sistema de backtesting de estratégias de trading utilizando a biblioteca Backtrader. O objetivo é integrar de forma prática e aprofundada os 4 pilares da Programação Orientada a Objetos (POO) — Abstração, Encapsulamento, Herança e Polimorfismo — juntamente com os conceitos fundamentais de Classes, Atributos, Métodos e Objetos.

#### **🛠️ O que vocês terão que fazer**

##### **1. Configuração do Ambiente**

**Instalar o Backtrader**

Execute o seguinte comando no terminal para instalar a biblioteca:


```python
!pip install backtrader
```

    Defaulting to user installation because normal site-packages is not writeable
    Requirement already satisfied: backtrader in /home/user/.local/lib/python3.10/site-packages (1.9.78.123)
    

**Obter Dados Históricos**

Baixe um dataset de ações de empresas como Apple (AAPL) ou Google (GOOGL) utilizando o Yahoo Finance. Porém, antes disso você precisara instalar essa biblioteca. Para tal, utilize o seguinte comando:


```python
!pip install yfinance
```

    Defaulting to user installation because normal site-packages is not writeable
    Requirement already satisfied: yfinance in /home/user/.local/lib/python3.10/site-packages (0.2.52)
    Requirement already satisfied: frozendict>=2.3.4 in /home/user/.local/lib/python3.10/site-packages (from yfinance) (2.4.4)
    Requirement already satisfied: requests>=2.31 in /home/user/.local/lib/python3.10/site-packages (from yfinance) (2.31.0)
    Requirement already satisfied: multitasking>=0.0.7 in /home/user/.local/lib/python3.10/site-packages (from yfinance) (0.0.11)
    Requirement already satisfied: html5lib>=1.1 in /home/user/.local/lib/python3.10/site-packages (from yfinance) (1.1)
    Requirement already satisfied: beautifulsoup4>=4.11.1 in /home/user/.local/lib/python3.10/site-packages (from yfinance) (4.12.3)
    Requirement already satisfied: pandas>=1.3.0 in /home/user/.local/lib/python3.10/site-packages (from yfinance) (2.2.3)
    Requirement already satisfied: pytz>=2022.5 in /home/user/.local/lib/python3.10/site-packages (from yfinance) (2024.1)
    Requirement already satisfied: lxml>=4.9.1 in /home/user/.local/lib/python3.10/site-packages (from yfinance) (5.2.2)
    Requirement already satisfied: numpy>=1.16.5 in /home/user/.local/lib/python3.10/site-packages (from yfinance) (1.24.3)
    Requirement already satisfied: peewee>=3.16.2 in /home/user/.local/lib/python3.10/site-packages (from yfinance) (3.17.6)
    Requirement already satisfied: platformdirs>=2.0.0 in /home/user/.local/lib/python3.10/site-packages (from yfinance) (4.2.0)
    Requirement already satisfied: soupsieve>1.2 in /home/user/.local/lib/python3.10/site-packages (from beautifulsoup4>=4.11.1->yfinance) (2.5)
    Requirement already satisfied: webencodings in /home/user/.local/lib/python3.10/site-packages (from html5lib>=1.1->yfinance) (0.5.1)
    Requirement already satisfied: six>=1.9 in /usr/lib/python3/dist-packages (from html5lib>=1.1->yfinance) (1.16.0)
    Requirement already satisfied: python-dateutil>=2.8.2 in /home/user/.local/lib/python3.10/site-packages (from pandas>=1.3.0->yfinance) (2.9.0.post0)
    Requirement already satisfied: tzdata>=2022.7 in /home/user/.local/lib/python3.10/site-packages (from pandas>=1.3.0->yfinance) (2024.1)
    Requirement already satisfied: certifi>=2017.4.17 in /home/user/.local/lib/python3.10/site-packages (from requests>=2.31->yfinance) (2024.12.14)
    Requirement already satisfied: idna<4,>=2.5 in /usr/lib/python3/dist-packages (from requests>=2.31->yfinance) (3.3)
    Requirement already satisfied: urllib3<3,>=1.21.1 in /usr/lib/python3/dist-packages (from requests>=2.31->yfinance) (1.26.5)
    Requirement already satisfied: charset-normalizer<4,>=2 in /home/user/.local/lib/python3.10/site-packages (from requests>=2.31->yfinance) (3.3.2)
    

**Importação das Bibliotecas Essenciais**

Na célula abaixo, importem as bibliotecas que considerarem necessárias para o desenvolvimento do projeto. Lembrem que talvez vocês precisem instalar alguma delas. Para começar, já incluímos algumas bibliotecas fundamentais que facilitarão o processo:


```python
# Importa o Backtrader, uma biblioteca de backtesting para estratégias de trading
import backtrader as bt

# Importa o yFinance, utilizado para baixar dados financeiros históricos diretamente do Yahoo Finance
import yfinance as yf

# Importa a classe datetime para manipulação de datas
from datetime import datetime

# Importa o pandas, biblioteca essencial para análise e manipulação de dados em formato de DataFrames
import pandas as pd

# Importa o matplotlib.pyplot, biblioteca para criação de gráficos e visualizações de dados
import matplotlib.pyplot as plt

```

##### **2. Desenvolvimento da Estratégia de Trading com POO**

**Criar uma Classe para a Estratégia**
Definam uma classe que herde de bt.Strategy, que será o coração do seu projeto. Essa classe deve conter:

- Atributos: Definam indicadores técnicos, como médias móveis de curto e longo prazo.

- Métodos:
    - __ init __: Inicializa os indicadores e variáveis da estratégia.
    - next: Define a lógica de compra e venda baseada nos sinais dos indicadores.


**Exemplo:**


```python
# Definimos uma classe de estratégia que herda da classe base bt.Strategy do Backtrader.
# Isso é um exemplo de **Herança** em Programação Orientada a Objetos (POO), permitindo que nossa estratégia utilize
# todas as funcionalidades embutidas da classe Strategy, como controle de posições e execução de ordens.
class MovingAverageCrossStrategy(bt.Strategy):

    # O método __init__ é chamado uma vez no início da execução da estratégia.
    # Usamos esse método para inicializar os **atributos** da nossa estratégia, como indicadores técnicos.
    def __init__(self):
        # Criamos um indicador de Média Móvel Simples (SMA) de 10 períodos sobre o preço de fechamento dos dados.
        # 'self.ma_short' é um atributo que guarda a média móvel curta, que reage mais rapidamente às mudanças de preço.
        self.ma_short = bt.indicators.SimpleMovingAverage(self.data.close, period=10)
        
        # Criamos outro indicador de Média Móvel Simples (SMA), agora de 30 períodos.
        # 'self.ma_long' é um atributo que guarda a média móvel longa, que é mais lenta para reagir às variações do preço.
        self.ma_long = bt.indicators.SimpleMovingAverage(self.data.close, period=30)

    # O método next é chamado automaticamente pelo Backtrader a cada novo "candle" ou barra de dados (ex.: diário, horário).
    # É aqui que definimos a **lógica de compra e venda** da nossa estratégia.
    def next(self):
        # Condição para compra:
        # Se a média móvel curta (ma_short) cruzar acima da média móvel longa (ma_long),
        # e ainda **não temos uma posição aberta** (not self.position), então executamos uma compra.
        
        # O que é self.position?
        # 'self.position' é um atributo do Backtrader que indica se já temos uma posição aberta no ativo.
        # Se não houver posição aberta, 'self.position' é avaliado como False (ou 0).
        # Se estivermos comprados, 'self.position' é True (ou o número de unidades compradas).
        
        if self.ma_short[0] > self.ma_long[0] and not self.position:
            self.buy()  # Método do Backtrader que executa uma ordem de compra.
            
            # Quanto é comprado?
            # Por padrão, o método 'self.buy()' compra 1 unidade do ativo. 
            # Para comprar uma quantidade específica, podemos passar o argumento 'size', por exemplo: self.buy(size=100).
        
        # Condição para venda:
        # Se a média móvel curta cruzar abaixo da média móvel longa,
        # e **já temos uma posição aberta** (self.position), então vendemos.
        elif self.ma_short[0] < self.ma_long[0] and self.position:
            self.sell()  # Método do Backtrader que executa uma ordem de venda.
            
            # Quanto é vendido?
            # Por padrão, 'self.sell()' vende todas as unidades do ativo que foram compradas anteriormente, encerrando a posição.
            # Para vender uma quantidade específica (por exemplo, vender parcialmente), podemos usar: self.sell(size=50).

```

##### **3. Executar o Backtest:**

Com a estratégia pronta, configurem e executem o backtest usando o Cerebro, o motor de execução do Backtrader.

**Configurar o Cerebro**

Inicializem o motor Cerebro, adicionem os dados históricos e a estratégia desenvolvida:


```python
# Parâmetros relacionados a captura de dados do ticker.
ticker = 'AAPL'
start_date = '2020-01-01'
end_date = '2021-01-01'

# Baixando os dados do ticker com auto ajuste
data = yf.download(ticker, start=start_date, end=end_date, auto_adjust=True)

# Verificando e ajustando as colunas para o formato correto
if isinstance(data.columns, pd.MultiIndex):
    data.columns = data.columns.get_level_values(0)  # Remove o MultiIndex

# Carregando os dados no Backtrader
data_feed = bt.feeds.PandasData(dataname=data)

# Inicializando o Cerebro
cerebro = bt.Cerebro()
cerebro.adddata(data_feed)
cerebro.addstrategy(MovingAverageCrossStrategy)
```

    [*********************100%***********************]  1 of 1 completed
    




    0



**Executar o Backtest**

Rodem o backtest e visualizem o desempenho:


```python
# Setando o valor inicial a ser investido na estratégia
initial_cash = 15000

# Definindo o saldo inicial
cerebro.broker.set_cash(initial_cash)

# Executando o backtest
cerebro.run()

# Capturando o saldo final
final_cash = cerebro.broker.getvalue()

# Exibindo os resultados
print(f'Saldo inicial: ${initial_cash:.2f}')
print(f'Saldo final: ${final_cash:.2f}')
print(f'Lucro/Prejuízo: ${final_cash - initial_cash:.2f}')

# Plota o gráfico e salva como PNG
fig = cerebro.plot()[0][0]
filename = f'backtest_{ticker}_{start_date}_to_{end_date}.png'
fig.savefig(f'backtest_{ticker}_{start_date}_to_{end_date}.png')
print(f'O gráfico foi salvo como {filename}. \nEsse é um gráfico bastante poluído, mas, se tiver interesse, existem formas de mudá-lo, basta uma rápida pesquisa :)')

```

    Saldo inicial: $15000.00
    Saldo final: $15025.05
    Lucro/Prejuízo: $25.05
    


    <IPython.core.display.Javascript object>



<div id='0f9a277d-8d29-42ea-8805-40372d4db19f'></div>


    O gráfico foi salvo como backtest_AAPL_2020-01-01_to_2021-01-01.png. 
    Esse é um gráfico bastante poluído, mas, se tiver interesse, existem formas de mudá-lo, basta uma rápida pesquisa :)
    

## **POO na Prática: O Que Você Já Usava Sem Perceber**

### **1. Pandas e NumPy São Baseados em POO**

Quando vocês criam um DataFrame no Pandas ou uma matriz no NumPy, estão na verdade instanciando objetos de classes que já foram definidas pelos desenvolvedores dessas bibliotecas!

🔹 Exemplo: Quando usamos:

```python
    import pandas as pd

    df = pd.DataFrame({"Nome": ["Ana", "Carlos"], "Idade": [25, 30]})
    print(df.shape)  # Atributo
    print(df.describe())  # Método
```

Aqui, df é um objeto da classe DataFrame, e .shape e .describe() são atributos e métodos, exatamente como vocês aprenderam!

🔹 O mesmo acontece no NumPy:

```python
    import numpy as np

    matriz = np.array([[1, 2], [3, 4]])
    print(matriz.T)  # Transposta (método)
    print(matriz.shape)  # Dimensão (atributo)
```

Agora fica claro que tudo isso são apenas classes bem projetadas!

### **2. Strings, Listas e Dicionários Também São Objetos**

Vocês já usaram .upper(), .append() e .items() centenas de vezes, certo? Agora vocês sabem que esses são métodos das classes str, list e dict.

🔹 Exemplo:

```python
    texto = "hello"
    print(texto.upper())  # Método da classe str

    lista = [1, 2, 3]
    lista.append(4)  # Método da classe list

    dicionario = {"chave": "valor"}
    print(dicionario.items())  # Método da classe dict
```

Cada um desses tipos é uma classe que disponibiliza métodos específicos sem que precisemos nos preocupar com sua implementação interna!

### **3. Modelos de Machine Learning São Objetos!**

Se você já usou Scikit-Learn, viu que um modelo precisa ser instanciado, treinado e testado – tudo isso são conceitos de POO.

🔹 Exemplo:

```python
    from sklearn.linear_model import LinearRegression

    modelo = LinearRegression()  # Criando um objeto da classe LinearRegression
    modelo.fit(X_train, y_train)  # Método para treinar o modelo
    y_pred = modelo.predict(X_test)  # Método para prever valores
```

O modelo é um objeto, e .fit() e .predict() são métodos que manipulam esse objeto!

Esses são apenas alguns exemplos, mas o mundo da programação está repleto de aplicações da POO. Frameworks como Django para desenvolvimento web, bibliotecas de visualização como Matplotlib e até ferramentas de automação seguem esses mesmos princípios. Agora que você entende a base por trás dessas estruturas, conseguirá identificar a POO em quase todos os códigos que encontrar.

## **Conclusão: POO é uma Nova Forma de Pensar Programação**

Ao longo dessa jornada, exploramos os conceitos fundamentais da Programação Orientada a Objetos (POO) e como eles se aplicam tanto na teoria quanto na prática. Aprendemos que POO não é apenas um conjunto de regras ou palavras-chave, mas sim uma forma diferente de estruturar e organizar nossos programas.

Através de abstração, encapsulamento, herança e polimorfismo, vimos como é possível criar sistemas modulares, reutilizáveis e mais fáceis de manter. Mais do que isso, percebemos que essas ideias não estão isoladas do nosso dia a dia: bibliotecas que usamos o tempo todo, como Pandas e NumPy, foram construídas seguindo esses princípios.

Agora que vocês conhecem POO, conseguem enxergar que quase tudo o que usamos em Python segue esse modelo. O conhecimento que vocês adquiriram não serve apenas para criar classes do zero, mas também para entender como as bibliotecas funcionam internamente e até para desenvolver códigos mais eficientes e organizados. 🚀💡

POO também não se limita a uma única área. Seja no mercado financeiro, inteligência artificial, desenvolvimento web ou até mesmo em jogos, essa abordagem pode tornar o código mais intuitivo e escalável. Cada problema pode ser resolvido de diferentes formas, e POO nos dá uma maneira poderosa de estruturar nossas soluções.

Agora que você compreende esses conceitos, vale a pena revisitar códigos antigos e tentar enxergá-los com essa nova perspectiva. Você vai perceber como muitas das ferramentas que já usa são baseadas nesses mesmos princípios! 🚀
