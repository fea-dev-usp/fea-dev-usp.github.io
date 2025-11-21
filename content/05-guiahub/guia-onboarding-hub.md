---
title: Onboarding do Hub – Guia passo a passo
---
>[!warning]
>
>Isso aqui é um Tutorial direcionado apenas para os Membros da FEA.dev

>[!info]
>Os passos de 1 a 3 serão feitos uma **única vez**. Caso já tenha feito, você pode pular diretamente para o passo 4 em diante
>
>Se quiser aprender ou revisar a sintaxe da linguagem do Markdown acesse esse outro arquivo [colocar o caminho aqui]

Este guia ensina qualquer pessoa a **acessar, editar e publicar** o Hub hospedado no **GitHub da organização** usando **Obsidian + Git + Quartz**.

## 1) O que você vai precisar (pré‑requisitos)

- **Acesso ao repositório** da organização (peça para te adicionarem como _member_ e com permissão de escrita no repo do Hub).
    
- Ter o **Git e VsCode** instalados na sua máquina.
    
- Ter também o **Obsidian** instalado (para editar os arquivos Markdown `.md`)
    

>[!info]
> Links oficiais para download, caso ainda não tenha instalado:
>
> - [Git](https://git-scm.com)
> - [VsCode](https://code.visualstudio.com/)
> - [Obsidian](https://obsidian.md/)

## 2) Clonar o repositório da organização

Com ambos instalados no seu computador, siga os seguintes passos:

1- Abra seu VsCode;

2- Inicialize seu Terminal, pode tanto arrastando com mouse a parte inferior para cima (imagem abaixo como referência) ou por meio do atalho Ctrl + Shift + Aspas;

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-9.jpg]]

3- É esperado que você esteja visualizando isso na sua tela:

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-26.jpg]]

4- No terminal agora você vai clonar o repositório do github para sua máquina, por meio do git. Dessa forma: 

```powershell
# Alterar depois para os links corretos
git clone https://github.com/<ORGANIZACAO>/<REPO-DO-HUB>.git
cd felipesantanafs.github.io

# Só para confirmar a branch padrão do projeto
git branch -a # o output aqui esperado algo que contenha 'v4'
```

5- Pronto é esperado que você tenha uma pasta com os arquivos do hub na máquina;

6- Para visualizar ela no seu computador, você deve fazer isso (ainda no terminal do VsCode):

```powershell
explorer . # isso abre a pasta com os arquivos
code . # isso abre a pasta no VsCode
```

7- Por enquanto no Vscode é isso, voltaremos para ele depois.

## 3) Partindo para o Obsidian

1-  Abra o Obsidian;

2- No canto inferior esquerdo clique no "Vault" padrão que está no seu Obsidian (está ao lado do símbolo de interrogação e da engrenagem):

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-19.jpg]]

3- Após clicar nele, selecione em "Gerenciar Cofres...";

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-20.jpg]]

4- Nessa nova tela que se abriu, clique em "Abrir" na seção "Abrir pasta como cofre"; 

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-21.jpg]]

5- No explorador de arquivos, você vai colocar o caminho que você encontrou no passo 2.6
Você vai escrever na área de busca, algo parecido com isso:

>[!warning]
>Trocar essa imagem quando eu for trocar o nome do repositório para o da dev 


![[../imagens/guia-onboarding-hub/guia-onboarding-hub-22.jpg]]

6- Seguindo a imagem, a pasta que deve estar selecionada é a 'content'. Com isso, você vai estar vendo que o nosso hub dentro do Obsidian (ele servirá como local de apenas de criar mudanças,  se quiser utilizar para leitura de preferência a utilizar o site). 

7- A Cara do Hub é essa à princípio (imagem do dia 31/10/2025, no futuro poderá estar diferente):

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-23.jpg]]

## 4) Estrutura do Hub: 

### Estrutura do Hub:

a. Home Page: O arquivo referente a nossa página é o index (que não está em nenhuma pasta), à princípio a sua alteração fica a cargo apenas para o pessoal de Tech e da Gestão, não altera ele sem a permissão do pessoal. 

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-24.jpg]]


>[!warning]
>**NÃO RENOMEIE NENHUM ARQUIVO CHAMADO INDEX, ESSE NOME FAZ QUE O QUARTZ RECONHEÇA COMO PÁGINA PRINCIPAL.**

b. Trilhas: É a pasta que as 4 subpastas das nossas áreas de estudo

c. Subpastas: Estão organizadas pelas áreas de Finquant, IA, Ciência de dados e Extras. Decorrente a cada área mãe, os arquivos estão organizado por ano e semestre. Serão nelas que vocês irão colocar seus projetos.

d. Imagens: Logicamente é a pasta que vai conter as imagens que vocês vão anexar em seus arquivos. **É muito importante ela estar organizada**, **SEMPRE** coloque a imagem que vai usar **DENTRO DELA** e **NÃO** apenas cole no seu texto (o Obsidian vai fazer uma bagunça danada se apenas colar). Na próxima seção eu explico a razão.
## 4) Criando seu arquivo e pasta:

>[!info]
Aqui eu vou te ensinar como criar seu arquivo e como organizá-lo aqui dentro do hub. As personalizações referentes a sintaxe do Markdown está no arquivo [colocar o arquivo aqui] e te convido a não se limitar apenas a ela, faça suas pesquisas em outras fontes!

1- Criando arquivo genérico: Na barra lateral no canto superior direito clique no ícone com uma "folha e um lápis" chamado "Nova nota" e pronto vai ter seu arquivo criado. O nome que você colocar nele não importa tanto (o nome que aparecerá no site vai vir de uma personalização dentro dele, confie em mim!) coloque algo intuitivo e siga o mesmo padrão dos já existentes. 

OBS: não utilize ponto no nome do arquivo ( por exemplo: cluster.portfólio, utilize cluster-portfólio ), o ponto faz que o Obsidian tente o ler como arquivo, no caso citado seria um arquivo .portfolio e não como Markdown.

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-25.jpg]]

2- Criando pasta: Bom para criar é só clicar no ícone da "pasta com um sinal mais dentro" está do lado do ícone do arquivo. As mesma recomendações do Arquivo valem para as Pastas.

![[../imagens/guia-onboarding-hub/guia-onboarding-hub.jpg]]

3- Forma alternativa para ambos é só clicar com o botão direito na lateral

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-2.jpg]]


## 5) Personalização Essencial de sua Página:

Com a sua primeira página criada, vamos dar um cabeçalho para ela e anexar as tags que vão aparecer lá no site. Para isso siga o seguinte instrução:

1- Cabeçalho: Escreva exatamente três hífens (---) sem os parêntases no topo do arquivo, bem abaixo do título: 

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-1.jpg]]
vai aparecer isso exatamente na hora!

2- Título: preencha essa propriedade com 'title' e escrava seu título que quiser

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-3.jpg]]
3- Tags: para adicionar uma tag clique em 'Adicionar propriedade' e escreva 'tags'. Até o momento temos 2 tipos de tags e com suas classificações:

a- Nível:  escreva  "#nivel/basico" , "#nivel/intermediario" ou "#nivel/avancado"  

b- Trilhas: escreva "#trilha/finquant" , "#trilha/ia" , "#trilha/extras" ou "#trilha/ciencia-de-dados" 

Obs: escreva sem as aspas!

Pronto seu cabeçalho está pronto, ficará dessa forma: 

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-4.jpg]]

## 6) Adicionar imagens

Como já avisei anteriormente as imagens são algo que demandam bastante atenção aqui no Obsidian. Siga esses passos para deixar o ambiente organizado e funcional para todos:

1- Crie uma subpasta na pasta imagem para armazenar suas imagens dentro, nesse exemplo criei uma que se chama "guia-hub":

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-6.jpg]]

2- Observe que todas as imagens que usei nesse arquivo estão dentro dela, tente manter a mesma sintaxe vai te ajudar a selecioná-las depois; 

 ![[../imagens/guia-onboarding-hub/guia-onboarding-hub-8.jpg]]

3- Você pode salvar a imagem dando um Ctrl + V da imagem dentro da imagem e depois  a renomeando apertando com o botão direito do mouse ou você pode fazer seu manejo pelo explorador de arquivos fique tranquilo

4- Com isso em mente, para você colocar a sua imagem no corpo do seu arquivo faça a seguinte sintaxe: 

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-5.jpg]]

Dessa forma, já aparecerá uma sugestão para adicionar uma imagem salva no obsidian.

5- Referenciando a imagem que você quer, terá algo do tipo:

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-7.jpg]]

6- Pronto sua imagem foi indexada ao Texto.

OBS: Você se deve estar se perguntando todo esse trabalho para criar uma imagem somente, não seria mais fácil color e pronto? 
Eu concordo com você, seria muito mais fácil e direto, mas vou te mostrar o problemão que isso ai dar! 

se eu simplesmente colasse a imagem que eu queria aconteceria isso: 

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-10.jpg]]
O nome da imagem seria algo bem abstrato e que depois para saber o que aquela imagem queria mostrar e de qual projeto faz parte. Além disso, ao se fazer isso o Obsidian adiociona automaticamente a imagem na barra lateral de forma aleatória! Observe na imagem que anexei abaixo: 

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-11.jpg]] 

**Por fim eu sei que é um processo chato, mas que a longo prazo é necessário para a própria manutenção da organização do hub. Com pouco tempo você já acostuma com a sintaxe e já sai quase de forma automática. Conto com vocês com essa parte!**

## 7) Mandando seu arquivo para o Github e para o Hub

Bom espero que esteja acompanhando tudo até o momento, supunha que terminou as alterações no seu arquivo e já quer mandar ele para o Github. Para isso siga esses passo:

1- Volte para o VsCode
 
2- Mude para o ambiente da o hub;

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-12.jpg]]

3- Adicione o que você alterou na pasta content;

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-13.jpg]]

4- Dê o commit (coloquei um exemplo que estou fazendo, descreve o que você fez no seu caso);

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-14.jpg]]

Vai aparecer tudo que você fez, que beleza hein!

5- Por fim, de um push e mandará tudo ao github;

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-16.jpg]]

Beleza Tudo foi para o Github lá nosso! Mas se segura ai, a mudança lá no site do Hub não é algo automático! 
Primeiro verificamos no próprio Github se a nossa adição deu tudo certo

6- Abrindo a aba "Actions" do nosso repositório;

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-18.jpg]]

Clique na última sua última adição, que no meu caso foi essa marcada pela setinha vermelha. 
Se ao selecioná-la e ainda estiver amarela ainda as mudanças não foram adicionadas ao Hub (ou seja, não adianta ficar dando F5 lá na site ainda não vai ter alteração alguma), espere ele ficar azul que as mudanças foram enviadas (agora pode ficar dando F5 igual um louco) 

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-15.jpg]]
(sinal de esperar ainda)

![[../imagens/guia-onboarding-hub/guia-onboarding-hub-17.jpg]]
(agora foi!)

7- Pronto suas alterações foram feitas e o Hub estará atualizado! 😁
## Considerações Finais: 

Bom o guia básico de como acessar e criar seus arquivos foram feitos! Eu sei que parece muito a primeira vista, mas juro que com a prática de vocês logo tudo ficará guardado na cabeça de vocês e vai sair tudo de forma automática praticamente. Revisem tudo e façam todo o passo a passo com calma. 

Conto que vocês para sempre atualizar esse meio com excelentes materiais, você vai ajudar toda a comunidade dev e externa! 🚀🚀🚀

## [Opcional] - Background do Hub:

>[!info]
>Se ainda ficou curiso e quer saber como o Hub foi feito e entender mais o como funciona o Quartz, leia a seguinte documentação: 
>- [https://quartz.jzhao.xyz/authoring-content](https://quartz.jzhao.xyz/authoring-content )
>- [https://notes.nicolevanderhoeven.com](https://notes.nicolevanderhoeven.com/How+to+publish+Obsidian+notes+with+Quartz+on+GitHub+Pages) 
>- [https://yagasaki.bohr.io/blog/como-criar-um-blog-usando-github-pages-obsidian-quartz](https://yagasaki.bohr.io/blog/como-criar-um-blog-usando-github-pages-obsidian-quartz)
