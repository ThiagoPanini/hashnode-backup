---
title: "Ferramentas e Softwares - Brave"
datePublished: 2022-05-07T16:11:26.354Z
cuid: cl2w2cu2h04dgt4nv76yy6pax
slug: ferramentas-e-softwares-brave
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1651939836691/GslbiAT-L.PNG
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1651939872649/fFNZU1Ll4.PNG
tags: tutorial, linux, beginner, learning, linux-for-beginners

---

Fala, galera! Em mais um artigo desta surpreendente série de Linux, iremos iniciar uma trajetória sequencial de posts abordando detalhes da instalação de algumas das principais ferramentas na jornada de um desenvolvedor ou engenheiro. Anteriormente nesta série, falamos sobre o [APT e o gerenciamento de pacotes](https://panini.hashnode.dev/o-apt-e-o-gerenciamento-de-pacotes) em ambientes Linux. Este pode ser um conteúdo interessante para ser consumido antes de mergulhar nesta sequência de instalação de programas e softwares.

A grande inspiração por trás deste e dos demais artigos subsequentes é, sem dúvidas, o excelente vídeo do canal [O Bruno Germano](https://www.youtube.com/channel/UCBWbWViVqDHckknir8PIIdg) onde o criador apresenta detalhes sobre seu ambiente Ubuntu 18.04. Além das customizações visuais, Bruno Germano também demonstra alguns programas e softwares presentes em seu ambiente de desenvolvimento, fornecendo dicas e elencando vantagens para utilizar tais programas em seus respectivos cenários. 

Preparados para mais uma jornada interessante? Bora lá!

___

## Brave

Para quem acabou de chegar no Ubuntu aplicando uma série de customizações fenomenais no ambiente (se você não acompanhou, sugiro a [última sequência](https://panini.hashnode.dev/customizando-o-ubuntu-parte-1) de artigos desta série), ter em mãos um navegador eficiente, visualmente interessante, amigável e, ainda por cima, seguro, é essencial!

Definido pelos próprios desenvolvedores como um navegador 3 vezes mais rápido que o Chrome, o [Brave](https://brave.com/pt/) é um software baseado no [Chromium](https://www.chromium.org/Home/) *open source* e que entrega uma interface amigável em uma navegação altamente segura.

![img00-brave-icon.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1649465463644/iaFQsYMSy.jpg)

Para instalar o Brave em seu sistema operacional, basta navegar até a página do [navegador](https://brave.com/pt/) e clicar no botão "Baixar o Brave". Na janela subsequente, siga as instruções relacionadas ao sistema operacional Ubuntu.

![img01-brave-install.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649463522393/sZWQJl1bj.png)

Se você entendeu bem o conteúdo do artigo [O APT e o gerenciamento de pacotes](https://panini.hashnode.dev/o-apt-e-o-gerenciamento-de-pacotes) disponibilizado em momentos anteriores nesta série, provavelmente irá olhar para a imagem acima e identificar algumas ações interessantes. Claro, conhecer os [principais comandos Linux](https://panini.hashnode.dev/principais-comandos-e-atalhos) também é essencial, mas nada que não tenha sido abordado nesta série também.

Na prática, o passo a passo para instalação do Brave em um sistema Ubuntu inicia com a ação de instalação de dois pacotes:

- `apt-transport-https`: pacote que permite o uso de repositórios via HTTPS. Para mais informações sobre o mesmo, é possível consultar o [link de documentação](https://manpages.ubuntu.com/manpages/focal/pt/man1/apt-transport-https.1.html)
- `curl`: pacote altamente utilizado no formado de comando executável no Linux. Em uma definição direta, o `curl` pode ser utilizado para transferência de dados a partir de URLs. Sua [página de documentação](https://curl.se/) traz ricos detalhes sobre sua usabilidade.

Esse parêntesis técnico acima é apenas uma forma de indicar ao leitor algumas situações que, por muitas vezes, passam batido em tutoriais de instalação ou realização de ações estabelecidas. Estamos acostumados a realizar operações sem muitas vezes nos preocuparmos nas ações que, de fato, estamos realizando. 

Considerando o processo sequencial da imagem de instalação do Brave, nota-se a presença dois longos comandos identificados por:

```bash
sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg
```

```bash
echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list
```

De forma direta e objetiva, os comandos acima indicam as etapas necessárias para **adicionar o Brave** como um dos **repositórios oficiais** de download de pacotes do sistema. No artigo sobre o APT, foi possível identificar a existência de arquivos de configuração e gerenciamento presentes no diretório `/etc/apt` da distribuição Ubuntu e, nele, arquivos como `source.list` e `sources.list.d` eram os responsáveis por alocar os indicadores de alvo sempre que o sistema precisa procurar ou instalar algum novo pacote.

O diagnóstico final, neste caso, é que o Brave ainda não é um pacote/programa presente no repositório oficial do Ubuntu (assim como muitos outros programas ainda não são) e, dessa forma, sua efetiva instalação depende de uma adição manual do repositório de download (onde os binários do Brave podem ser obtidos) no arquivo de configuração do APT. Dessa forma, quando o usuário tentar realizar a instalação padrão via `apt install`, o sistema saberá exatamente onde procurar o software desejado e, dessa forma, sua instalação será realizada com sucesso.

E assim, após uma certa carga densa de teoria, o tutorial de instalação do Brave segue com a atualização dos pacotes como um passo necessário após a alteração de arquivos de configuração do APT e, por fim, finaliza com a chamada padrão de instalação do programa.

```bash
sudo apt update
sudo apt install brave-browser
``` 

**Observação:** caso ainda tenha curiosidade sobre o gerenciamento de pacotes, verifique como os tutoriais são diferentes na página de instalação do Brave para o ambiente Linux de acordo com cada distribuição. Você verá que o bloco de tutorial para o Ubuntu usa o `apt`. Já o bloco para Fedora, CentOS, e RedHat EL utiliza o `dnf`. O OpenSUSE, por sua vez, utiliza o `zypper`. Com a evolução e o conhecimento obtidos até aqui, este tipo de parágrafo não soa nada misterioso e isso é sensacional!

Após a instalação, o Brave poderá ser acesso no gerenciador de aplicativos do Ubuntu 🎁

![img02-brave-installed.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649465589367/ysKBPXByf.png)

### Configurando Brave

Como uma espécie de bônus neste tutorial, os passos abaixo irão fornecer dicas básicas de configuração do navegador Brave em termos visuais e sistêmicos, permitindo um incremento em sua usabilidade e uma familiaridade em suas funções de usuário.

[1] Para iniciar esta jornada, abra o navegador e, ao ser confrontando com uma tela de boas vindas, clique em OK para configurar o Brave como o navegador padrão do sistema (claro, se assim desejar).

![img03-welcome-brave.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649466153819/J2EKIaQB9.png)

[2] Na sequência, após a *tour* inicial, clique no menu hambúrguer do canto superior direito e selecione a opção *"Settings"*.

![img04-brave-settings.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649466219681/jH3zHXqCg.png)

[3] Em *"Appearance"*, as configurações sugeridas são:
- **Brave colors:** Dark
- **Theme:** Morpheon Dark
- **Show bookmarks:** On
- **Show Brave Rewards icon in address bar:** Off

[4] Em *"Search Engine"*, altere o motor de procura para Google.

![img05-brave-search-engine.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649466286513/AkdPG2iIJ.png)

Pronto! O Brave está literalmente preparado para uso.

![img06-brave-ready.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649466306846/WPM78i19a.png)

[5] Para finalizar, passe o mouse na *dock* do sistema (canto inferior) e, clicando com o botão direito no ícone do Brave, selecione a opção *"Keep in Dock"*. Isto fará com que o navegador fique fixo na barra de ícones. Eventualmente, você pode desejar remover o Mozila Firefox da barra e, para tal, basta seguir um processo semelhante.

![img07-brave-dock.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649466365039/1rRuRBDTY.png)

Pronto! Agora o sistema está literalmente preparado para utilizar um navegador amigável e seguro! O Brave é uma ótima solução para usuários que prezam pela segurança e velocidade sem abrir mão da facilidade e de uma ótima interface.

___

## Referências

- https://www.youtube.com/watch?v=W_AnWAiuzaw&t=634s
- https://brave.com/pt/
- https://brave.com/linux/
- https://manpages.ubuntu.com/manpages/focal/pt/man1/apt-transport-https.1.html
- https://howtoinstall.co/pt/apt-transport-https
- https://curl.se/