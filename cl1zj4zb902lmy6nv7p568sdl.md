---
title: "Customizando o Ubuntu - Parte 1"
datePublished: 2022-04-14T21:44:49.537Z
cuid: cl1zj4zb902lmy6nv7p568sdl
slug: customizando-o-ubuntu-parte-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1649382900932/TJIBEsyeP.PNG
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1649382914981/KHZo9dqSt.PNG
tags: ubuntu, linux, gui, linux-for-beginners

---

Com uma abordagem relativamente diferente, este artigo faz parte de uma sequência de posts com o objetivo de explorar exemplos de customizações visuais da interface gráfica de uma distribuição Ubuntu. A grande ideia é proporcionar uma maior liberdade de configurações aos usuários para que estes transformem seus sistemas Linux de acordo com suas preferências! Será sensacional, eu prometo!

___

## Desktop Environment: o ambiente de trabalho

Vimos, em [artigos anteriores](https://panini.hashnode.dev/operando-no-linux-conhecendo-o-shell) nesta série sobre Linux, que uma GUI (*Graphical User Interface*) é um tipo de shell que possibilita aos usuários uma operação dinâmica e visual dentro do sistema operacional. Dentro deste cenário, existe ainda um outro conceito de suma importância a ser definido: os *Desktop Environments*, ou simplesmente abreviados como DE.

Na prática, um DE é um ambiente de desktop que engloba, além de outros componentes, a interface gráfica. Quando entramos em um ambiente de trabalho Linux, encontramos uma série de ferramentas que podem ser utilizadas pelos usuários para navegar ou gerenciar o sistema. Exemplos como calculadora, calendário, barra de tarefas, ícones e outros elementos fazem, em conjunto, parte de um *Desktop Environment*. São eles que, de fato, consolidam um ambiente amigável de trabalho em diversas distribuições Linux, refutando qualquer argumento relacionado a complexidade de sistemas operacionais com essa base.

O [artigo escrito por Dionatan Simioni](https://diolinux.com.br/sistemas-operacionais/os-7-ambientes-graficos-mais-populares-do-linux.html) para o portal diolinux traz alguns exemplos de DEs comumente conhecidas no universo Linux, sendo elas:

**Unity**

![img03-unity.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649038280771/cDVacWFQN.png)

**GNOME**

![img04-gnome.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1649038289558/GxnKnMJS3.jpg)

**KDE**

![img05-kde.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649038300951/WEyDh0Yws.png)

**XFCE**

![img06-xfce.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649038307208/VWSZ_4A66.png)

Diferentes distribuições Linux utilizam diferentes DEs. Nesta proposta de customização, utilizaremos uma distribuição Ubuntu em sua versão 20.4. Por padrão, esta versão do Ubuntu traz consigo o GNOME como ambiente de desktop e, antes de mergulhar de fato nas etapas necessárias para modificar nosso sistema, vamos entender um pouco melhor deste que é um dos ambientes gráficos mais famosos de todo o universo Linux.

### GNOME - GNU Network Object Model Environment

Até versão anteriores ao Ubuntu 17.10, o ambiente de desktop padrão utilizado era o Unity. A partir desta versão, distribuições Ubuntu aderiram o GNOME como DE. Por si só, o GNOME é um ambiente gráfico extremamente amigável com uma série de funcionalidades criadas para facilitar toda a operação no sistema operacional para os usuários. 

Para reforçar e consolidar a diferença entre uma DE e uma GUI, o projeto GNOME incorpora, entre seus componentes:

- O aplicativo GNOME Calculator
- O aplicativo GNOME Calendar
- O Nautilus para gerenciador de arquivos (análogo ao Windows Explorer)
- A interface gráfica (GUI) GNOME Shell
- etc...

Assim, é correto dizer que ambiente de desktop GNOME é composto pela GUI GNOME Shell e suas ferramentas adjacentes.

### O GNOME Tweaks

O GNOME possui um gerenciador de aplicação chamado Gnome Tweak Tool responsável por auxiliar usuários a configurar pontualmente alguns elementos visuais do ambiente de trabalho, incluindo paleta de cores, ícones, cursores, temas, botões, menus e muito mais. Sua instalação pode ser obtida através de duas abordagens distintas:

**1. Via terminal** através da execução do comando abaixo:

```bash
sudo apt install gnome-tweaks
```

**2. Via loja de aplicativos Ubuntu Software** através da procura pelo termo `tweaks` no menu de pesquisa:

![img01-gnome-tweaks.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649027830392/-Iu_9yEM5.png)

Em ambos os cenários, as dependências do pacote Gnome Tweaks serão obtidas pelo sistema e sua instalação será realizada. Para inicializá-la, basta procurar por "Gnome Tweaks" como um novo aplicativo do Ubuntu ou então executar o comando `gnome-tweaks` no terminal:

![img02-gnome-tweaks-software.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649027909713/XyPAxJEuW.png)

A partir de agora, é possível utilizar o Gnome Tweaks como ferramenta central de customização do Gnome no Ubuntu. Pelo gerenciador, é possível personalizar:

- Configurações gerais e aparência
- Extensões
- Fontes
- Teclado e mouse
- Aplicações
- Barras de aplicativos
- Janelas

Nos blocos subsequentes, recursos do site [Gnome Look](https://www.gnome-look.org/browse/) serão baixados, posicionados e instalados no sistema operacional. Os passos alocados funcionarão com sugestões de customizações. Os leitores deste artigo estão livres para modificar e escolher temas e personalizações específicas.
___

## Customizando o Tema

O primeiro elemento a ser modificado em nosso sistema Ubuntu é o tema. Para isso, vamos navegar até o site [Gnome Look](https://www.gnome-look.org/browse/) e procurar pelo tema "Sweet" na aba de pesquisa.

![img07-sweet.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649117334966/bTHPzZL9l.png)

Na página do tema [Sweet](https://www.gnome-look.org/p/1253385/), acesse a aba *"Files"* e escolha o arquivo *"Sweet-Dark.xz"* para realizar o download.

![img07-sweet-download.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649117404514/qWrk2c3N-.png)

Agora no Ubuntu, navegue até o diretório de Downloads do usuário e realize a extração do arquivo `tar.xz` recém baixado. Essa operação pode ser realizada diretamente pelo terminal ou através da própria interface do sistema clicando com o botão direito do mouse e selecionando a opção *"Extract Here"* (ou "Extrair Aqui").

![img09-sweet-extract.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649117497242/jh_Bd9fBF.png)

Após a extração, navegue até o diretório *home* do usuário e crie uma pasta específica para alocar os temas do GNOME. Esta operação é importante para que o Gnome Tweaks possa "enxergar" os temas baixados e permitir sua posterior configuração no sistema. Para este passo, é essencial que a pasta tenha o nome `.themes`.

```bash
cd ~
mkdir .themes
```

Com isso, é possível mover o arquivo extraído para a pasta de temas recém criada no sistema. Para facilitar esta operação, podemos utilizar o comando abaixo:

```bash
mv ~/Downloads/Sweet-Dark ~/.themes
```

![img10-mkdir-themes.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649117707209/11KbE5qS9.png)

Com isso, o novo tema Sweet Dark pode agora ser encontrado na ferramenta Gnome Tweaks. Para tal, basta abrir a ferramenta (via `gnome-tweaks` no terminal ou via gerenciador de aplicativos do Ubuntu), navegar até o meu *"Appearance"* e, na opção *"Applications"*, selecionar o novo tema Sweet Dark.

![img11-gnome-tweaks-theme.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649117784110/sSl-20NNT.png)

Assim, um novo e maravilhoso tema poderá ser usufruído pelo usuário em sua totalidade. 

![img12-sweet-dark-installed.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649118817888/RyXu0518x.png)

O Sweet Dark é uma opção extremamente interessante para usuários que preferem um tema mais escuro e charmoso. Sua recomendação foi obtida através do ótimo [vídeo](https://www.youtube.com/watch?v=S07IwKI5xH0&t=918s) do canal birobirobiro, no YouTube. Outros temas podem ser instalados seguindo esta mesma lógica que pode ser resumida em:

1. Procurar e selecionar um tema no site [Gnome Look](https://www.gnome-look.org/s/Gnome/browse/)
2. Baixar o arquivo desejado
3. Extrair o arquivo no sistema operacional
4. Mover o diretório resultante com os elementos do tema para a pasta `~/.themes`
5. Configurar e selecionar o novo tema na ferramenta Gnome Tweak.

___

## Customizando Ícones

O conjunto de ícones de um sistema operacional possui um papel visual muito importante durante a navegação. Utilizando o Gnome Tweaks, os usuários do Ubuntu podem customizar este conjunto seguindo uma abordagem estritamente semelhante à seguida anteriormente para a customização de um tema do sistema operacional. Neste tutorial, será utilizado o conjunto de ícones [Flatery](https://www.gnome-look.org/p/1332404/) como alvo da customização.

No site [Gnome Look](https://www.gnome-look.org/browse/), entre na aba de pesquisa e procure por *"Flatery"*. Acesse a página do conjunto de ícones e, na aba *"Files"*, escolha o arquivo *"Flatery.tar.gz"* para realização do download.

![img13-flatery-download.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649118587371/bigDqpf_s.png)

No Ubuntu, navegue até o diretório de Downloads e realize a extração do arquivo `tar.gz` baixado (seja pelo terminal ou pela interface). 

![img14-flatery-extract.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649118722595/obG_hPry4.png)

Após a extração, navegue até o diretório *home* do usuário e crie uma pasta específica para alocar os conjuntos de ícones. Esta operação é importante para que o Gnome Tweaks possa "enxergar" os conjuntos de ícones baixados e permitir sua posterior configuração no sistema. Para este passo, é essencial que a pasta tenha o nome `.icons`.

```bash
cd ~
mkdir .icons
```

Com isso, é possível mover o arquivo extraído para a pasta de ícones recém criada no sistema. Para facilitar esta operação, podemos utilizar o comando abaixo:

```bash
mv ~/Downloads/Flatery/* ~/.icons
```

Como observação, o conjunto de ícones Flatery possui um subdiretório de mesmo nome ao ser extraído. Perceba que, no comando `mv` acima, foi utilizado um *wildcard* (*) para mover todo o conteúdo presente no subdiretório Flatery. Caso contrário, o Gnome Tweaks não encontraria os ícones para configuração.

Após este procedimento, basta abrir o Gnome Tweaks, navegar até o menu *"Appearance"* e, na opção *"Applications"*, selecionar o conjunto de ícones Flatery. É necessário fechar e abrir o Gnome Tweaks a cada nova configuração. Se você seguiu este tutorial e instalou o tema Sweet Dark, saiba que novas configurações ficarão visíveis apenas após fechar e abrir novamente o Gnome Tweaks.

![img15-flatery-install.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649119142105/e8gh-ctKb.png)

Mais uma vez, concluímos mais uma customização no Ubuntu. Os novos ícones instalados ficarão visíveis instantaneamente após a configuração no Gnome Tweaks. 

![img16-flatery-installed.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649119247984/d5PzahUmG.png)

Assim como informado nos temas, os usuários poderão realizar as configurações de novos conjuntos seguindo o mesmo princípio de obtenção dos arquivos, posicionamento correto na pasta correta (`~/.themes` para temas ou `/.icons` para ícones) e a posterior configuração.

___

## Customizando Cursores

Finalizando a primeira parte deste artigo sobre customizações do Ubuntu, será proposta a modificação do conjunto de cursores do sistema. Dessa vez, o conjunto de cursores [McMojave cursors](https://www.gnome-look.org/p/1355701/) será instalado de modo a tornar o sistema operacional com um visual semelhante ao macOS.

Seguindo os mesmos princípios anteriores, no site [Gnome Look](https://www.gnome-look.org/browse/), procure pelo conjunto de cursores McMojave. 

![img17-mcmojave-gnome.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649120701092/fQ9cHZ0aY.png)

Na [página do cursor](https://www.gnome-look.org/p/1355701/), clique na aba *"Files"* e escolha o arquivo *“McMojave-cursors.tar.xz”* para realização do download.

![img18-mcmojave-download.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649120726425/vFV_GD9kX.png)

No Ubuntu, navegue até o diretório de Downloads e realize a extração do arquivo `tar.xz` (via terminal ou interface).

![img19-mcmojave-downloads.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649120813594/zyRveFM8p.png)

Os conjuntos de cursores normalmente são posicionados no diretório `~/.icons` para que possam ser configurados. Dessa forma, como esta pasta já foi criada na etapa anterior durante a instalação do conjunto de ícones, execute o comando abaixo para mover o diretório recém extraído para a pasta adequada no sistema.

```bash
mv ~/Downloads/McMojave-cursors ~/.icons
```

Por fim, basta abrir o Gnome Tweaks (fechar e abrir, caso não tenha feito após a instalação dos ícones no passo anterior) e, no menu *"Appearance"* e na opção *"Cursor"*, selecione o conjunto de cursores McMojave.

![img20-mcmojave-gnome.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649120964790/nPVcia54c.png)

A mudança dos cursores é mais sutil que as demais e perceptível em cenários de navegação recorrentes.

___

## Considerações Finais

E assim chegamos ao fim de mais uma postagem desta série super interessante sobre Linux. Nesta jornada, aprendemos tópicos extremamente interessantes sobre a customização de uma distribuição Ubuntu. Logo de cara, foi possível transformar todo o padrão do sistema em algo visualmente atrativo (pelo menos aos olhos deste autor que vos fala). 

Espero que este tenha sido mais um conteúdo relevante dentro da sua jornada de consumo. Na segunda parte desta sequência, aplicaremos uma transformação na barra de ícones (mais conhecida como *dock*) do Ubuntu.

Até a próxima!

Perdeu algo e quer rever algum tópico?

- [3 - Operando no Linux: Conhecendo o Shell](https://panini.hashnode.dev/operando-no-linux-conhecendo-o-shell)
- [4 - O Bash como Interpretador de Comandos](https://panini.hashnode.dev/o-bash-como-interpretador-de-comandos)
- [5 - Principais Comandos e Atalhos](https://panini.hashnode.dev/principais-comandos-e-atalhos)

___

## Referências

- https://www.youtube.com/watch?v=S07IwKI5xH0&t=918s
- https://linuxhint.com/desktop-customization-ubuntu/
- https://www.youtube.com/watch?v=GshXVIRk2fc
- https://www.youtube.com/watch?v=W_AnWAiuzaw&t=634s
- https://www.youtube.com/watch?v=rYe9xf0Wu7k&t=203s
- https://diolinux.com.br/gnome/gnome-tweak-tool-gnome-tweaks-no-ubuntu.ht