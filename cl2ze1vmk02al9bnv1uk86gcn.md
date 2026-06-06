---
title: "Ferramentas e Softwares - Terminator"
datePublished: 2022-05-10T00:02:09.050Z
cuid: cl2ze1vmk02al9bnv1uk86gcn
slug: ferramentas-e-softwares-terminator
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1652141016238/3LTbBFeLC.PNG
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1652141021088/xo6OrPw9u.PNG
tags: tutorial, linux, terminal, learning, linux-for-beginners

---

Fala, galera! Sejam bem vindos a mais um post desta sequência extraordinária de instalação de algumas ferramentas essenciais no nosso ambiente Ubuntu. Neste artigo, será proposta a instalação e exploração de uma das ferramentas mais queridas pelos amantes Linux: o Terminator!

___

## Terminator

Sabe-se que o terminal em um ambiente Linux é uma ferramenta indispensável. Em alguns cenários, grande parte do trabalho de um desenvolvedor ou de um administrador de sistemas é realizado no terminal. Dessa forma, faz toda a diferença possuir um ambiente amigável e com funcionalidades relevantes dentro do dia a dia de trabalho.

O [Terminator](https://dev.to/xeroxism/how-to-install-terminator-a-linux-terminal-emulator-on-steroids-1m3h) é um emulador de terminal do Linux com algumas *features* e vantagens que o torna uma ferramenta extraordinária! Com o Terminator é possível:
- Trabalhar com vários terminais em uma mesma janela
- Utilizar atalhos rápidos para abrir novas sessões
- Salvar e restaurar *layouts* personalizados e muito mais!

Sua instalação é simples e direta, necessitando apenas de alguns passos que serão exemplificados logo a seguir:

[1] Com o terminal aberto, execute o comando abaixo para adicionar o repositório do Terminator no sistema:

```bash
sudo add-apt-repository ppa:gnome-terminator
```

![img08-terminator-add-repository.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649467318948/QqoKnUm03.png)

[2] Na sequência, atualize os pacotes do sistema e execute o comando para instalação do Terminator conforme abaixo:

```bash
sudo apt update
sudo apt install terminator
```

[3] Pronto! Agora o Terminator pode ser encontrado como um aplicativo dentro do sistema operacional 🎁

![img09-terminator-installed.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649467375205/FYIm6ER4G.png)

___

### Temas e Layouts do Terminator

Uma das *features* interessantes do Terminator é a possibilidade de adicionar configurações visuais pontualmente no sistema. As modificações são centralizadas em um arquivo de configuração disponível em `~/.config/terminator/config` e, nele, é possível alterar, por exemplo, opções de *profile* e *layout* que são responsáveis por gerenciar aspectos visuais do emulador de terminais.

Existem uma série de temas prontos e uma [página do GitHub](https://github.com/EliverLara/terminator-themes/tree/master/schemes) do usuário EliverLara traz praticamente todas as configurações de todos os temas disponíveis. Esta será a principal referência utilizada para modificar o visual do Terminator e, para tal, será preciso inserir manualmente as modificações no arquivo de configuração citado acima e, posteriormente, utilizar uma interface visual do próprio Terminator para finalizar as configurações.

Considerando a existência de diferentes *profiles* configuráveis no Terminator, cada um com seu aspecto visual, paleta de cores e combinações, o autor deste artigo navegou e testou algumas das principais opções e selecionou, pontualmente, os perfis abaixo:

___

#### Aurora

```bash
[[Aurora]]
    background_color = "#0f1c21"
    cursor_color = "#00485a"
    foreground_color = "#80b6ad"
    palette = "#0f1c21:#046655:#04c975:#b5bd68:#308891:#94a5bc:#8abeb7:#80b6ad:#0f1c21:#046655:#04c975:#b5bd68:#308891:#94a5bc:#8abeb7:#80b6ad"
```

![img11-terminator-aurora.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649514697198/VGkm_pr-i.png)

___

#### Afterglow

```bash
[[Afterglow]]
    palette = "#151515:#ac4142:#7e8e50:#e5b567:#6c99bb:#9f4e85:#7dd6cf:#d0d0d0:#505050:#ac4142:#7e8e50:#e5b567:#6c99bb:#9f4e85:#7dd6cf:#f5f5f5"
    background_color = "#212121"
    cursor_color = "#d0d0d0"
    foreground_color = "#d0d0d0"
    background_image = None
```

![img12-terminator-afterglow.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649514864776/kOZG75Bcz.png)

___

#### Alienblood

```bash
[[AlienBlood]]
    palette = "#112616:#7f2b27:#2f7e25:#717f24:#2f6a7f:#47587f:#327f77:#647d75:#3c4812:#e08009:#18e000:#bde000:#00aae0:#0058e0:#00e0c4:#73fa91"
    background_color = "#0f1610"
    cursor_color = "#73fa91"
    foreground_color = "#637d75"
    background_image = None
```

![img13-terminator-alienblood.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649514921412/89d-3Z1Cb.png)

___

#### Galaxy

```bash
[[Galaxy]]
    palette = "#000000:#f9555f:#21b089:#fef02a:#589df6:#944d95:#1f9ee7:#bbbbbb:#555555:#fa8c8f:#35bb9a:#ffff55:#589df6:#e75699:#3979bc:#ffffff"
    background_color = "#1d2837"
    cursor_color = "#bbbbbb"
    foreground_color = "#ffffff"
    background_image = None
```

![img14-terminator-galaxy.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649514933336/nDmdx8bBm.png)

___

### Modificando o aspecto visual do emulador

Nos tópicos elencados nesta seção, serão consideradas as etapas necessárias para modificar o *profile* padrão do Terminator de acordo com os temas previamente levantados. A seleção feita acima não tem nenhum apego técnico ou visual à temas. O usuário pode pesquisar por diferentes temas e selecionar aqueles que mais lhe agradarem. Uma boa referência para observação dos temas e das combinações de cores é o [github](https://github.com/piotros/pretty-terminator/tree/master/screenshots) do usuário piotros.

[1] Após a seleção inicial de temas, utilize um editor de textos para abrir o arquivo de configuração do Terminator

```bash
nano ~/.config/terminator/config
```

[2] Abaixo de `[[default]]`, insira todos os temas selecionados de acordo com a imagem ilustrada abaixo:

![img15-terminator-config.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649515259046/-3ifVqlx_.png)

[3] Sempre ao inicializar, o Terminator considera a configuração parametrizada sob a identificação `[[default]]` para estabelecer o aspecto visual da ferramenta. Dessa forma, para realmente alterar os perfis, é preciso garantir que o *profile* padrão tenha outro nome. Para isso, altere o nome `[[default]]` para `[[default-old]]`.

[4] Escolha um dos temas para ser testado e altere seu nome para `[[default]]`. Dessa forma, o Terminator, ao inicializar, irá buscar e carregar as configurações estabelecidas dentro do *profile* padrão. No exemplo abaixo, o tema `[[Aurora]]` foi escolhido como padrão no Terminator, tendo seu nome alterado para `[[default]]`.

![img16-aurora-default.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649515593166/lJU4Qd5jh.png)

**Observação:** para maiores detalhes na dinâmica de configuração dos *profiles*, é possível acessar [este link](https://askubuntu.com/questions/158159/how-do-i-get-terminator-to-start-up-with-my-custom-layout)

[5] Para carregar as configurações, basta fechar e abrir novamente o Terminator e visualizar o novo tema Aurora estabelecido tanto para a janela principal, quanto também para novas janelas que forem abertas durante a operação. 

![img17-terminator-aurora-config.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649515700529/m5WmoMthR.png)

[6] Para testar novas configurações, basta seguir o mesmo procedimento de alteração do arquivo de configuração. Após explorar as demais opções selecionadas, o tema `[[Galaxy]]` foi o que mais agradou, particularmente. Dessa forma, vamos editar o arquivo `~/.config/terminator/config` novamente e garantir que o tema `[[Aurora]]` retorne com seu nome original e vamos estabelecer o tema `[[Galaxy]]` como novo *default*. O resultado prático poderá ser visualizado abaixo:

![img18-terminator-galaxy-config.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649515831674/lxL2OTdGv.png)

[7] Por fim, para encerrar este bloco de configurações do Terminator, será proposta a alteração da transparência da janela, proporcionando um aspecto mais *clean*. Com uma janela de terminal aberta, clique com o botão direito e selecione a opção *Preferences*.

[8] Na aba *Profiles*, com o perfil *default* selecionado, navegue até o menu *Background*, troque para a opção *Transparent background* e configure a barra para 0,70 (ou qualquer parâmetro que possa ser de maior agrado).

![img19-terminator-transparent-bg.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649515964258/zgEuTKN_z.png)

Pronto! Agora o Terminator está ativo, operante, customizado e literalmente disponível para as mais variadas operações em um cotidiano de atividade de um ambiente Ubuntu!

![img20-terminator-finished.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649516009028/dcX6YHlmn.png)

___

## Referências

- https://dev.to/xeroxism/how-to-install-terminator-a-linux-terminal-emulator-on-steroids-1m3h
- https://github.com/EliverLara/terminator-themes/tree/master/schemes
- https://github.com/piotros/pretty-terminator/tree/master/screenshots
- https://askubuntu.com/questions/158159/how-do-i-get-terminator-to-start-up-with-my-custom-layout
