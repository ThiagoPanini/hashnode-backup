---
title: "Customizando o Ubuntu - Parte 2"
datePublished: 2022-04-18T14:59:00.319Z
cuid: cl24uehzd012zrznv0md6hkb4
slug: customizando-o-ubuntu-parte-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1649382928658/isNcsdrKK.PNG
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1649382939095/GKlAJVcnU.PNG
tags: ubuntu, linux, gui, linux-for-beginners

---

Na [primeira parte](https://panini.hashnode.dev/customizando-o-ubuntu-parte-1) desta sequência de artigos focados na customização do Ubuntu, foi possível entender a diferença entre GUI (*Graphical User Interface*) e DE (*Desktop Environment*) como elementos fundamentais na usabilidade e difusão de sistemas Linux para novos usuários. 

Além disso, foi possível conhecer o GNOME como a DE utilizada no Ubuntu e em uma outra série de distribuições Linux. O GNOME possui uma ferramenta extremamente útil chamada Gnome Tweaks que permite as mais variadas customizações de sistemas, envolvendo a configuração de novos temas, ícones, cursores e muito mais. Essencialmente, estes três elementos citados foram os alvos de customizações do artigo anterior.

Neste artigo, a proposta será continuar com as ações de customização, dessa vez pautadas na modificação da famosa barra lateral de ícones (ou *dock*, como é comumente chamada). Para tal, será utilizado o gerenciador Plank que, por sua vez, transformará a tradicional *dock* do Ubuntu em uma *dock* estritamente semelhante ao que se pode encontrar em sistemas macOS.

Ficou curioso? Vamos nessa!

___

## Customizando a barra lateral de ícones (*dock*)

Nas últimas versões do Ubuntu (até a 20.04, pelo menos), a barra de ícones (ou *dock*) pode ser visualizada no canto esquerdo da tela. Esta é uma ferramenta análoga à barra de tarefas em ambientes Windows e permite que usuários tenham uma maior facilidade em inicializar certos programas, possibilitando aos mesmos posicionar, movimentar ou fixar softwares como bem entenderem.

![img01-dock-raw.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1649180533251/NEOT8r_XI.PNG)

No [excelente artigo](https://itsfoss.com/customize-ubuntu-dock/#:~:text=When%20you%20log%20into%20Ubuntu,launch%20your%20frequently%20used%20programs.) escrito por Abhishek Prakash para o portal *It's FOSS*, uma série de detalhes sobre a *dock *do Ubuntu são fornecidos aos usuários, incluindo tutoriais para aplicar as mais variadas configurações, como por exemplo, alterar seu posicionamento, ocultá-la automaticamente ou mesmo desabilitá-la por completo.

Nesta seção de customização, as ações propostas irão envolver:

- A utilização da aplicação *Extensions* para desabilitar a *dock*
- Instalação do [Plank](https://www.edivaldobrito.com.br/plank-uma-dock-leve/) para alterar a *dock* em um formato semelhante ao MacOS
- Configurar o sistema para que o Plank seja iniciado automaticamente
- Alterar as preferências do Plank através de um gerenciador
- Baixar e instalar um tema específico para o Plank, aplicando-o à nova *dock* do sistema

Mãos à obra!

De largada, acesse a loja de aplicativos do Ubuntu e pesquise por *"gnome extensions"* para realizar o download do aplicativo indicado na imagem abaixo.

![img02-gnome-extensions-download.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649179822595/EFHUueNkw.png)

Ao finalizar o download, será possível encontrar o aplicativo *"Extensions"* disponível no Ubuntu. No fundo, este aplicativo funciona como um gerenciador que permite algumas modificações rápidas no sistema. No contexto desta seção, vamos abrir o aplicativo de extensões e desabilitar a *dock* do Ubuntu clicando no botão indicado na imagem abaixo.

![img03-gnome-extensions.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649180078898/4JLT62bkV.png)

Uma vez selecionada, esta opção fará com que a barra de ícones literalmente desapareça. Mas calma, este é apenas o começo da customização. Logo ela voltará mais bela e funcional do que nunca e a ferramenta responsável por este retorno magistral será o Plank!

No terminal Ubuntu, execute o seguinte comando para instalação do Plank:

```bash
sudo apt-get install plank -y
```

Uma vez instalado, o Plank pode ser encontrado e inicializado manualmente pelo usuário como um dos aplicativos instalados no Ubuntu:

![img04-plank.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649180913721/7DC-BWUl_.png)

Dessa forma, a inicialização do Plank fez com que a *dock* tenha um novo comportamento: sua posição abaixo da tela faz referência a sistemas MacOS e, além disso, passar o mouse em cada um dos ícones faz com que os elementos se destaquem automaticamente, trazendo um aspecto interessante nesta linha de customização. A *dock* será oculta caso o mouse permaneça um determinado tempo fora do intervalo de seleção da mesma.

![img05-dock-plank.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649181220274/OBUfGANfH.png)

Neste cenário, o Plank foi inicializado manualmente pelo usuário o que, de certa forma, traria um trabalho operacional indesejado cada vez que o Ubuntu fosse acessado. Para alterar este comportamento, é necessário configurar o sistema para que a aplicação Plank seja inicializada junto com o próprio sistema, garantindo que a *dock* estará neste mesmo formato sempre que o usuário realizar o login.

Para isso, basta entrar no aplicativo Gnome Tweaks, acessar o menu *"Startup Applications"* e adicionar o Plank como ferramenta de inicialização automática junto ao sistema. A imagem abaixo poderá servir como auxílio nesta etapa da configuração.

![img07-plank-startup.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649181240907/zwoonot2n.png)

Pronto! Temos agora uma *dock* do Ubuntu altamente profissional e customizada. Para navegar e testar outras configurações, basta modificar os parâmetros estabelecidos nas ferramentas Extensions e Gnome Extensions. Como complemento, será consolidado abaixo um tutorial para modificar temas do Plank para deixar a *dock* ainda mais personalizada.

### Customizando o Plank

O Plank pode ser configurado de várias maneiras, incluindo a modificação do tema principal, o posicionamento da *dock*, alinhamento, tamanho de ícones, comportamento, entre outros. Para editar suas configurações, é preciso realizar a instalação de uma ferramenta chamada *Plank Preferences* disponível na loja de aplicativos do Ubuntu.

![img07-plank-preferences.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649181710499/n2Oc5RjZS.png)

Uma vez instalado, o aplicativo para modificação do Plank pode ser inicializado via terminal através do comando:

```bash
plank --preferences
```

Com isso, a janela de configuração das preferências do Plank será aberta e, nela, será possível aplicar uma série de alterações na nova *dock* do sistema.

![img08-plank-preferences-init.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1650205970842/Jb-nN2njA.png)

Como primeira grande modificação, será proposta a instalação de um tema customizado obtido através do já conhecido site [Gnome Look](https://www.gnome-look.org/browse/). Para encontrar os temas específicos do Plank, basta pesquisar, no canto esquerdo do site, por *"plank themes"*.

![img09-plank-themes.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649181938344/jcd6LH7uS.png)

Com este filtro estabelecido, busque por *"Catalinas"* na aba superior de pesquisa e encontre o tema indicado pela figura abaixo:

![img10-plank-catalinas.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649181966683/mFW8bangv.png)

Na página do tema Catalinas, navegue até a aba *"Files"* e realize o download do tema *"Catalinas_Trend_by_PT_Alfred.tar.xz"*, assim como indicado na figura:

![img11-plank-themes-catalinas.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649182011539/bp0vedMcR.png)

Uma vez realizado o download do tema do Plank, basta extrair o arquivo (via terminal ou via interface) e movê-lo para a pasta `~/.local/share/plank/themes` através do seguinte comando:

```bash
mv ~/Downloads/Catalinas_Trend_by_PT_Alfred ~/.local/share/plank/themes/
```

Dessa forma, o gerenciador de alteração de preferências do Plank poderá enxergar um novo tema selecionável para configuração. Assim, com o terminal aberto, execute o comando `plank --preferneces` para abrir o gerenciador (caso o aplicativo estivesse aberto no ato da extração e movimentação do tema, será preciso fechar e abrir novamente).

Na aba *"Appearance"*, selecione o tema Catalinas recém baixado para aplicar a modificação. Opcionalmente, é possível aumentar o tamanho dos ícones presentes na *dock* através da opção *"Icon Size"* para um valor que seja confortável para uso.

![img13-catalinas-config.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649182226767/RxC-T2nVO.png)

E assim é concluída esta seção de configuração da *dock* do Ubuntu utilizando o Plank. O resultado final é uma barra de ícones estritamente semelhante ao que pode ser encontrado em sistemas macOS. Adicionalmente, uma série de outras configurações podem ser implementadas utilizando o gerenciador de preferências do Plank.

![img14-dock-final.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649182769561/jCd0veoa0.png)

___

## Considerações Finais

Seguindo esta linha de customizações, é surpreendente imaginar a liberdade que um usuário Linux tem em relação à modificação de seu sistema. Através de gerenciadores de aplicativos (que facilitam muito o trabalho de quem está acostumado com sistemas Windows), uma série de opções podem ser parametrizadas de acordo com a obtenção de diferentes temas para os mais variados cenários.

Na terceira parte desta sequência focada em customização do sistema, serão apresentados tópicos relacionados à inserção de *widgets* para analisar indicadores do próprio sistema, como os processos executados, temperatura da CPU, uso da memória, entre outros.

___

## Referências

- https://www.youtube.com/watch?v=S07IwKI5xH0&t=918s
- https://linuxhint.com/desktop-customization-ubuntu/
- https://www.youtube.com/watch?v=GshXVIRk2fc
- https://www.youtube.com/watch?v=W_AnWAiuzaw&t=634s
- https://www.youtube.com/watch?v=rYe9xf0Wu7k&t=203s
- https://diolinux.com.br/gnome/gnome-tweak-tool-gnome-tweaks-no-ubuntu.h