---
title: 2) Arquivos Jupyter Notebook
tags:
  - "#nivel/basico"
---
>[!warning]
>
>Isso aqui é um Tutorial direcionado apenas para os Membros da FEA.dev
>
>Antes de subir um arquivo no hub **avise algum membro de tech** 
>
>Qualquer dúvida/problema que tiver acione eles também, eles vão te ajudar! 😁
>
>Todos os atalhos colocados são para Windows, se você utiliza Mac, Linux ou outro sistema operacional, pesquise eles por fora! 

>[!info]
>Este guia ensina qualquer pessoa a **acessar, editar e publicar** o Hub hospedado no **GitHub da organização** usando **Vscode + Obsidian + Github**.

## 1) O que você vai precisar (pré‑requisitos)

- Ter o **VsCode** instalado na sua máquina.
    
- Ter também o **Obsidian** instalado (para editar os arquivos Markdown `.md`)

>[!info]
> Links oficiais para download, caso ainda não tenha instalado:
>
> - [VsCode](https://code.visualstudio.com/)
> - [Obsidian](https://obsidian.md/)

## 2) Transformando .ipynb em .md

1- Abra o seu VsCode;

2- Abra a pasta em que o seu arquivo está inserido (não abra apenas o arquivo diretamente, já te adianto não funcionará!), você pode fazer isso pelo atalho Crtl + Shift + E ou acessar pelo ícone lateral (imagem abaixo como referência):
![[Pasted image 20251124192930.png]]
![[Pasted image 20251124192949.png]]

Selecione a pasta que deseja e será aberto outra janela do VsCode, no meu caso ficou assim: 

![[Pasted image 20251124193118.png]]
Com a pasta aberta e com o arquivo desejado, siga as próximas instruções;

3- Abra o seu terminal, você pode fazer isso pelo atalho Crtl + Shift + Aspas ou arrastando para cima a barra inferior do Vscode, dessa forma: 

![[Pasted image 20251124193637.png]]

Você verá algo nesse sentido: 

![[Pasted image 20251124193817.png]]

O caminho da sua pasta deve estar presente (sublinhado em vemelho);

4- Instale essa biblioteca, se não tiver : 

```python 
 pip install jupyter nbconvert
```

![[Pasted image 20251124194222.png]]

5- Converte o notebook pra Markdown:

```python
jupyter nbconvert --to markdown introducao_poo_fea_dev.ipynb
```

No meu caso o meu arquivo de exemplo se chama "introducao_poo_fea_dev", altere para o nome do seu respectivo arquivo;

![[Pasted image 20251124194639.png]]

Se tudo der certo, após o comando ser rodado, espera-se que já na pasta esteja o novo arquivo em Markdown

## 3) Ajustando o Arquivo para a Formatação do Hub

Aqui vai ser abordado mais ou menos os passos já ensinados no guia 1, então serei um pouco mais direto. 
Qualquer dúvida dê um revisada no passo a passo mais detalhado no guia anterior! 

1- Abra seu arquivo agora em Markdown agora no Obsidian; 
 ![[Pasted image 20251124195152.png]]

2- Se tiver algum título no seu documento remova ele  e substitua pela formatação do Obsidian. 
(No meu caso não tenho, "introducao_poo_fea_dev" é o nome do arquivo)

Você escreverá três hífens ( "-" ) no topo da página e selecione o as propriedades "title" e "tags":

```
---
```

![[Pasted image 20251124195849.png]]

Dê o título apropriado ao seu trabalho e nas tags padronize, de acordo com essas:

```
nível:
#nivel/avancado #nivel/intermediario #nivel/basico 

trilhas: 
#trilha/finquant #trilha/ia #trilha/ciencia-de-dados #trilha/extras
```

Na linha abaixo do painel de propriedades, dê seus créditos pelo trabalho! Use essa formatação como referência:

```
_**Autores:** Autor(a) · Autor(a) · Autor(a)_
```

Obs-1: Se for apenas um autor não utilize a separação de pontos

Obs-2: Se o nome do arquivo conter 'underline' ( _ ) troque por hífen ( - ) para evitar possiveis problemas de formatação do arquivo

Pronto seu arquivo seu arquivo está certinho em Markdown, é recomendado dar um revisada para verificar nada faltando. 

3- Dê um Ctrl + S para salvar o arquivo e pode fechar o Obsidian
## 4) Dando Pull Request no Github

1- Entre no repositório do Hub: [Repositório do Hub](https://github.com/fea-dev-usp/fea-dev-usp.github.io)

![[Pasted image 20251124204150.png]]

2- Entre na pasta "Content":

![[Pasted image 20251124204250.png]]

3- Entre na Trilha que pertença o seu respectivo arquivo (se tiver dúvida em qual delas colocar pergunte a um membro de Tech), no meu caso aqui o meu arquivo pertence a trilha de '03-ciencia-de-dados'

![[Pasted image 20251124204448.png]]

4- Selecione a pasta referente ao seu ano e ao seu semestre (no caso da imagem ainda só existia a 2025-s2)

![[Pasted image 20251124204615.png]]

5- Um vez estando na pasta correta clique em 'Add File';

![[Pasted image 20251124204811.png]]

6- Clique em 'Upload Files':

![[Pasted image 20251124204849.png]]

7- Clique em 'choose your files' e coloque o seu arquivo

![[Pasted image 20251124204956.png]]

Na aba "ADD files via upload" preencha no seguinte formato:

```
[Ano-semestre] Tema - Nível
```

Na aba "Add an Optional extended description..." preencha no seguinte formato: 

```
Tipo de arquivo: Projeto Autoral / Jupiter Notebook / Aula Dev Ensina
Trilha: Ciência de Dados / FinQuant / Extras / IA
Nível de dificuldade: Iniciante / Intermediário / Avançado

Tópicos abordados: Dê uma Breve descrição 
```

No meu caso ficou assim:

![[Pasted image 20251124214347.png]]

Mais objetivamente dessa forma:

```
Tipo de arquivo: Jupiter Notebook 
Trilha: Ciência de Dados
Nível de dificuldade: Avançado

Tópicos abordados: 
- O que é Programação Orientada a Objetos (POO)
- Conceitos de classe, objeto, atributos e métodos
- Exemplos em Python 
```

Por favor tentem manter essa estrutura!

OBS: Deixem marcado a primeira bolinha, deixem o Commit na branch 'v4'

8- Para validar se tudo deu certo, pode checar isso na aba 'Actions': 

![[Pasted image 20251124214636.png]]

Se ficar ainda em amarelo as alterações ainda não foram submetidas ao Hub, esperem ficar em azul;

![[Pasted image 20251124214817.png]]

Tudo certo agora! Podem atualizar o Hub e tudo estará lá bonitinho! 