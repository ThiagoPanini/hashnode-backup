---
title: "Customizando o Ubuntu - Parte 3"
datePublished: 2022-04-21T16:19:02.016Z
cuid: cl297kyz400nkx5nvh2e45uci
slug: customizando-o-ubuntu-parte-3
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1649382954186/DKwrVlAkK.PNG
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1649382977924/8_XfuUCk3.PNG
tags: ubuntu, linux, extension, gui, linux-for-beginners

---

Bem-vindos a mais um artigo da sequência de customização do ambiente Linux! Até este ponto, foram realizadas uma série de modificações no sistema operacional Ubuntu instalado como uma máquina virtual. Utilizando gerenciadores de aplicativos e extensões, os usuários puderam realizar o download de temas, conjuntos de ícones e cursores, garantindo assim uma personalização completa do ambiente.

Perdeu algo? Acesse os dois artigos desta sequência de customização e fique por dentro:

- [Customizando o Ubuntu - parte 1: temas, ícones e cursores](https://panini.hashnode.dev/customizando-o-ubuntu-parte-1)
- [Customizando o Ubuntu - parte 2: barra de ícones](https://panini.hashnode.dev/customizando-o-ubuntu-parte-2)

Imagine agora que interessante poder analisar uma série de indicadores do sistema, como a quantidade de processos executados, temperatura da CPU e uso da memória. As extensões adicionais do Gnome trazem essas e outras possibilidades extremamente ricas. Nesta seção, será apresentado um passo a passo detalhado para que os usuários do Ubuntu possam usufruir de *widgets* e extensões adicionais com poucos cliques.

## Configurando o Gnome Shell Extensions no navegador

Como primeiro passo, navegue até o site [Gnome Shell Extensions](https://extensions.gnome.org/) e selecione a opção *"Click here to install browser extension"* para instalar a extensão adicional no navegador.

![img01-gnome-shell-extensions-install.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649185555761/F_4Sx9FPO.png)

Aguarde a verificação e inicial e clique no botão *"Continue to Installation"* para permitir a instalação das extensões no navegador. Posteriormente, clique em *"Add"* para confirmar e em *"Okay"* para finalizar.

![img02-gnome-shell-extensions-install-wait.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649185608125/GFs6i-0YH.png)

Voltando na página inicial do Gnome Shell Extensions, clique em [wiki page](https://wiki.gnome.org/Projects/GnomeShellIntegrationForChrome/Installation) para entrar na documentação do projeto. Por padrão, os passos detalhados na página consideram o Chrome como navegador e, se você o utiliza, basta executar o comando `sudo apt-get install chrome-gnome-shell` no terminal Linux. Se você utiliza o Firefox, será preciso navegar até a página de add-ons do Mozilla Firefox e instalar manualmente clicando no botão de Instalação.

![img03-gnome-shell-firefox.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649185694955/DRFWfgW6k.png)

A partir deste ponto, uma série de extensões poderão ser adicionadas diretamente pelo navegador. Esta é a magia! Como um simples *add-on*, o usuário poderá pesquisar por uma série de extensões relevantes para o sistema e instalá-las com um clique no navegador.

O procedimento padrão envolve pesquisar e selecionar a extensão desejada através do site [Gnome Shell Extensions](https://extensions.gnome.org/) e "ligá-la" através do botão presente no canto superior direito. O exemplo abaixo utiliza a extensão **User Themes** como exemplo. A propósito, esta é uma das extensões recomendadas neste artigo.

![img04-user-themes.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649185824779/F1uOSHexW.png)

## Extensões e Widgets Recomendados

A quantidade de extensões presentes no site do Gnome é gigantesca. Considerando algumas dicas obtidas nas mais variadas fontes consultadas pelo autor, a sequência de indicações abaixo trazem exemplos relevantes que podem ser seguidos para aprimorar a usabilidade do sistema. Neste cenário, será proporcionado um link para cada indicação de extensão abaixo para que o leitor possa analisar em detalhes os efeitos e ações aplicadas após sua instalação:

**[1. User Themes](https://extensions.gnome.org/extension/19/user-themes/)**

**[2. OpenWeather](https://extensions.gnome.org/extension/750/openweather/)**

![img05-open-weather.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649186155770/f71cy4Nwv.png)

**[3. Tweaks & Extensions in System Menu](https://extensions.gnome.org/extension/1653/tweaks-in-system-menu/)**

![img06-tweaks-extensions.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649186162407/Ez1SzQz2d.png)

**[4. Vitals](https://extensions.gnome.org/extension/1460/vitals/)**

![img07-vitals.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649186169717/oLDpzvOe4.png)

**[5. Transparent Top Bar](https://extensions.gnome.org/extension/1266/transparent-top-bar/)**

![img08-transparent-top-bar.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649186177141/ucDFrBfsL.png)

___

## Alterando tema do shell

Por fim, uma última alteração proposta será a alteração do tema do shell para que alguns elementos do sistema, como o calendário e outras opções da barra superior, combinem mais com tema instalado.

Para isso, bastas abrir a janela do Gnome Tweaks, navegar até o menu *"Appearance"* e, na opção *"Shell"*, alterar o tema para *"Yaru-dark"*.

![img09-shell-yaru-dark.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649186244597/Nv_GieYKJ.png)

___

## Considerações Finais

Nesta última sequência de três artigos, realizamos uma verdadeira transformação no sistema operacional Ubuntu. Muito além de proporcionar um tutorial que deve ser seguido fielmente pelos usuários, a grande ideia foi garantir uma maior autonomia de customização aos leitores, permitindo que os mesmos se sintam à vontade para testar e implementar suas próprias configurações.

Como bônus, o site [unsplash](https://unsplash.com/) pode ser utilizado como um grande repositório de imagens profissionais para alterar o fundo de área de trabalho de seu ambiente de desktop Ubuntu.

Possuir um ambiente amigável é a porta de entrada para uma grande jornada de aprendizado!

___

## Referências

- https://www.youtube.com/watch?v=S07IwKI5xH0&t=918s
- https://linuxhint.com/desktop-customization-ubuntu/
- https://www.youtube.com/watch?v=GshXVIRk2fc
- https://www.youtube.com/watch?v=W_AnWAiuzaw&t=634s
- https://www.youtube.com/watch?v=rYe9xf0Wu7k&t=203s
- https://diolinux.com.br/gnome/gnome-tweak-tool-gnome-tweaks-no-ubuntu.h