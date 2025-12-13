---
title: 1) Onboarding do Hub
tags:
  - nivel/basico
---
>[!warning]
>
>Isso aqui é um Tutorial direcionado apenas para os Membros da FEA.dev
>
>Antes de subir qualquer arquivo no hub, **avise algum membro de tech!** 
>
>Qualquer dúvida/problema que tiver acione eles também, eles vão te ajudar! 😁
>
>Todos os atalhos colocados são para Windows, se você utiliza Mac, Linux ou outro sistema operacional, pesquise eles por fora! 

>[!info]
>Este guia ensina qualquer pessoa a **acessar, editar e publicar** o Hub hospedado no **GitHub da organização** usando **VsCode + Obsidian + Git**. 
## 1) O que você vai precisar (pré‑requisitos)

- Ter o **Obsidian** instalado (para editar os arquivos Markdown `.md`)
    
- Ter o **VsCode** instalado (IDE que servir como meio de utilizar o Git)
    
- Ter o **Git** instalado (utilizaremos para fazer os commits para o GitHub)

>[!info]
> Link oficial para download, caso ainda não tenha instalado:
>   [Obsidian](https://obsidian.md/)
>   [VsCode](https://obsidian.md/)
>   [Git](https://obsidian.md/)

## 2) Transformando seu Arquivo .docx para .md

Nesse primeiro caso iremos mostrar passo a passo como se upar um arquivo aos moldes de relatório (originalmente um arquivo em .docx) para o Hub. 

1- Abra o seu arquivo no Google Docs: [Google Docs](https://docs.google.com/?hl=pt-BR)

2- Com o arquivo aberto, clique na opção "Arquivos" no canto superior esquerdo (imagens abaixo como exemplo ilustrativo apenas):

![[Pasted image 20251211214425.png]]

3- Clique em seguida em Baixar e depois selecione em Markdown (.md):

![[Pasted image 20251211214456.png]]

 4- Desse tópico era isso, é esperado que esse arquivo esteja na sua pasta de Downloads
## 3) Clonando Repositório 

1- Abra o VsCode;

![[Pasted image 20251211210956.png]]

2- Abra o terminal, utilize o atalho Ctrl + Shift + Aspas: 

![[Pasted image 20251211211125.png]]

3- Vamos checar se o git está realmente instalado, use esse comando no console:

```
git --version
```

![[Pasted image 20251211211303.png]]
4- Vamos clonar o repositório que está lá no GitHub, utilize esse comando:
```
git clone https://github.com/fea-dev-usp/fea-dev-usp.github.io
```
![[Pasted image 20251211211416.png]]

5- Por enquanto o que precisamos fazer inicialmente no VsCode era isso, voltaremos nele mais para frente.
## 4) Abrindo o Hub pelo Obsidian

1- Abra o aplicativo do Obsidian na sua máquina;

![[Pasted image 20251211211553.png]]

2- No canto inferior esquerdo, clique onde está escrito "Obsidian Vault" (se você já utilizar o Obsidian, clique no nome do vault que esteja ali) 

![[Pasted image 20251211211605.png]]

3- Clique em "Gerenciar cofres..."

![[Pasted image 20251211211612.png]]

4- Clique em "Abrir" em "Abrir pasta como um cofre":

![[Pasted image 20251211211617.png]]

5- Ele abrirá o seu explorador de arquivos, vamos encontrar nossa pasta com os arquivos do hub;

6- Desça a barra de rolagem da esquerda até encontrar 'Este Computador' e clique nele;

![[Pasted image 20251211211826.png]]

7- Clique em 'Usuários':

![[Pasted image 20251211211855.png]]

8- Selecione o usuário em que você utilizou para baixar o repositório do Hub (no meu caso só 
tenho um e ele se chama 'felip', no seu caso clique no seu); 

![[Pasted image 20251211211924.png]]

9- Dentro da pasta do seu usuário, procure a pasta com o nome 'fea-dev-usp.github.io' e clique nela;

![[Pasted image 20251211212132.png]]

10- Dentro dessa pasta, clique na outra pasta chamada 'content';

![[Pasted image 20251211212238.png]]


11- Com essa pasta aberta, clique em 'Selecionar pasta' (verifique na barra superior se o caminho é parecido, o que deva divergir seria apenas o nome do usúario);

![[Pasted image 20251211212320.png]]

12- Você estará vendo toda a estrutura do Hub dentro do Obsidian (a estruturá poderá estar diferente no momento que você esteja vendo, mas em suma deverá aparecer algo parecido); 

![[Pasted image 20251211212552.png]]

>[!info]
>Não altere a estrutura por conta própria, deixe isso para o pessoal que faz a manutenção do Hub
>Também não altere nenhum nome dos arquivos, em especial os chamados 'Index', esse nome é fundamental para a gente, o Quartz utiliza indentifica os arquivos como Página Inicial

## 5) Colocando seu Projeto dentro Obsidian

>[!warning] Lembrete
>O seu arquivo deverá estar em formato .md, como informado no passo 1.
>Já te adianto que qualquer outro formato não funcionará!  

1- 


## 6) Enviando seu arquivo para o Github

1- Lembra do VsCode? Ele entra em cena novamente agora, se  você fechou abra ele novamente ou volte para ele se deixou aberto;

2- Abra o terminal novamente (Ctrl + Shift + Aspas) e escreva:

```
cd fea-dev-usp.github.io
```

![[Pasted image 20251212204448.png]]

Obs: O próprio VsCode já te um atalho caso para te ajudar

3- Dê Pull no repositorio lá do Github (para pegar as últimas alterações que pessoal fez lá, antes de você!) 

```
git pull origin v4
```

![[Pasted image 20251212204759.png]]

4- Adicione o conteúdo alterado na pasta 'content';

```
git add content
```

![[Pasted image 20251212210634.png]]


5- Vamos commitar o que foi feito, siga as boas condutas abaixo para deixar o hub bem estruturado!

```
git commit -m ''
```

Não cole simplesmente a linha acima, dentro das aspas coloque o que foi feito com base nisso: 

Nomeie seu Pull Request com um prefixo para indicar o tipo de mudança, por exemplo: `docs: atualiza README`.

Prefixos recomendados:
- **feat:** nova funcionalidade / conteúdo novo
- **fix:** correção de bug / ajuste de algo quebrado
- **docs:** mudanças em documentação (README, guias, comentários)
- **refactor:** reorganização/limpeza sem mudar o comportamento
- **chore:** tarefas gerais (config, scripts, dependências, organização)

Utilize alguma ferramenta de LLM para te ajudar a preencher se for necessário!
Exemplo:

![[Pasted image 20251212211014.png]]

6- Vamos dar mandar tudo isso para o Github, dê um Push para nossa Branch:

```
git push origin v4
```

![[Pasted image 20251212211111.png]]

7- Vamos checar se as mudanças foram feitas corretamente e lá no Github, acesse:
https://github.com/fea-dev-usp/fea-dev-usp.github.io/actions

![[Pasted image 20251212211500.png]]

Se esse símbolo estiver **amarelo** é só esperar que a magia do seu arquivo está sendo feita, espere ficar **azul** como na imagem! 

Quando ficar azul, vocês podem 

## Considerações Finais: 

Bom o guia básico de como acessar e criar seus arquivos foram feitos! Eu sei que parece muito a primeira vista, mas juro que com a prática de vocês logo tudo ficará guardado na cabeça de vocês e vai sair tudo de forma automática praticamente. Revisem tudo e façam todo o passo a passo com calma. 

Conto que vocês para sempre atualizar esse meio com excelentes materiais, você vai ajudar toda a comunidade dev e externa! 🚀🚀🚀

## [Opcional] - Background do Hub:

>[!info]
>Se ainda ficou curiso e quer saber como o Hub foi feito e entender mais o como funciona o Quartz, leia a seguinte documentação: 
>- [https://quartz.jzhao.xyz/authoring-content](https://quartz.jzhao.xyz/authoring-content )
>- [https://notes.nicolevanderhoeven.com](https://notes.nicolevanderhoeven.com/How+to+publish+Obsidian+notes+with+Quartz+on+GitHub+Pages) 
>- [https://yagasaki.bohr.io/blog/como-criar-um-blog-usando-github-pages-obsidian-quartz](https://yagasaki.bohr.io/blog/como-criar-um-blog-usando-github-pages-obsidian-quartz)
