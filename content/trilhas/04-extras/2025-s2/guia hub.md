---
title: Onboarding do Hub – Guia passo a passo
---
>[!warning]
>
>Isso aqui é um Tutorial direcionado apenas para os Membros da FEA.dev

Este guia ensina qualquer pessoa a **acessar, editar e publicar** o Hub hospedado no **GitHub da organização** usando **Obsidian + Git + Quartz**.

## 1) O que você vai precisar (pré‑requisitos)

- **Acesso ao repositório** da organização (peça para te adicionarem como _member_ e com permissão de escrita no repo do Hub).
    
- Ter o **Git** instalado na sua máquina.
    
- Ter também o **Obsidian** instalado (para editar os arquivos Markdown `.md`).

>[!info]
> Links oficiais para download, caso ainda não tenha instalado:
>
> - [Git](https://git-scm.com)
> - [Obsidian](https://obsidian.md/)


## 2) Clonar o repositório da organização

Com ambos instalados no seu computador, siga os seguintes passos:

1 - Abra seu VsCode;

2 - Inicialize seu Terminal, pode tanto arrastando com mouse a parte inferior para cima (imagem abaixo como referência) ou por meio do atalho Crtl + Shift + Aspas;

![[guia-hub-2.jpg]]

3 - É esperado que você esteja visualizando isso na  sua tela:

![[guia-hub-1.jpg]]

4 - No terminal agora você vai clonar o repositório do github para sua máquina, por meio do git. Dessa forma: 

```powershell
# Alterar depois para os links corretos
git clone https://github.com/<ORGANIZACAO>/<REPO-DO-HUB>.git
cd <REPO-DO-HUB>

# Só para confirmar a branch padrão do projeto
git branch -a # o output aqui esperado algo que contenha 'v4'
```

5 - Pronto é esperado que você tenha uma pasta com os arquivos do hub na máquina;

6 - Para visualizar ela no seu computador, você deve fazer isso (ainda no terminal do VsCode):

```powershell
explorer . # isso abre a pasta com os arquivos
code . # isso abre a pasta no VsCode
```

7 - Por enquanto no Vscode é isso, voltaremos para ele depois.

## 3) Partindo para o Obsidian

1 -  Abra o Obsidian;

2 - No canto inferior esquerdo clique 'Vault' (está do lado do símbolo ponto de interrogação e da engragem):

![[guia-hub-3.jpg]]

3 - Após clicar nele, selecione em "Gerenciar Cofres...";

![[guia-hub-4.jpg]]

4 - Nessa nova tela que se abriu clique em "Abrir pasta como cofre"; 


