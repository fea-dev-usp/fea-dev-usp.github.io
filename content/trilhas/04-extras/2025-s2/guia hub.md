---
title: Onboarding do Hub – Guia passo a passo
---
Este guia ensina qualquer pessoa a **acessar, editar e publicar** o Hub hospedado no **GitHub da organização** usando **Obsidian + Git + Quartz**.

## 1) O que você vai precisar (pré‑requisitos)

- **Acesso ao repositório** da organização (peça para te adicionarem como _member_ e com permissão de escrita no repo do Hub).
    
- Ter o **Git** instalado na sua máquina.
    
- Ter também o **Obsidian** instalado (para editar os arquivos Markdown `.md`).

>[!info]
>Links oficiais para download, caso ainda não tenha instalado:
>-Git: <https://git-scm.com> 
>-Obsidian: <https://obsidian.md/>

## 2) Clonar o repositório da organização

Com ambos instalados no seu computador, siga os seguintes passos:

1 - Abra seu VsCode;

2 - Inicialize seu Terminal, pode tanto arrastando com mouse a parte inferior para cima (imagem abaixo como referência) ou por meio do atalho Crtl + Shift + Aspas;

![[guia-hub-2.jpg]]

3 - É esperado que você esteja visualizando isso na  sua tela:

![[guia-hub-1.jpg]]

4- No terminal agora você vai clonar o repositório do github para sua máquina, por meio do git. Dessa forma: 

```powershell
# Alterar depois para os links corretos
git clone https://github.com/<ORGANIZACAO>/<REPO-DO-HUB>.git
cd <REPO-DO-HUB>

# Só para confirmar a branch padrão do projeto
git branch -a # o output aqui esperado é 'v4'
```

