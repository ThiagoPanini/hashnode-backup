---
title: "Configurando uma máquina virtual Linux"
datePublished: 2022-03-31T16:22:54.352Z
cuid: cl1f7h29600hpzxnvhca96csk
slug: configurando-uma-maquina-virtual-linux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1648664805423/KXagdwx2l.PNG
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1648664844062/-PGs7Bnm7.PNG
tags: ubuntu, linux, linux-for-beginners, linux-kernel, linux-basics

---

No [primeiro artigo](https://panini.hashnode.dev/conhecendo-o-linux-e-sua-historia) desta série, uma visão conceitual do Linux e de sua história foi fornecida aos leitores. Dessa forma, foi possível compreender, mesmo que de forma resumida, termos como Unix, GNU, *kernel*, distros e outros mais. Seguindo adiante com o propósito da série, é chegado o momento de proporcionar, ao leitor, insumos para que o primeiro contato com um sistema operacional Linux seja realizado. Para tal, as seções e tópicos a seguir irão consolidar um tutorial para criação e configuração de uma máquina virtual Linux a partir da distribuição Ubuntu.

Antes, como de costume, vamos analisar alguns conceitos teóricos.

## Distribuições Debian

O Ubuntu é uma distribuição Linux baseada no Debian que, por sua vez, também pode ser considerada uma distribuição. Na prática, ao longo do processo evolutivo do GNU/Linux, algumas distribuições se tornaram tão famosas a ponto de servirem como base para praticamente todas as demais, sendo elas: Debian, Slackware e RedHat.

De acordo com o portal [debian.org](https://www.debian.org/derivatives/index.pt.html):

> Um derivado do Debian é uma distribuição baseada no trabalho realizado no Debian, mas com sua própria identidade, objetivos e público-alvo, e é criado por uma entidade que é independente do Debian. Os derivados modificam o Debian para atingir os objetivos que eles mesmos estabeleceram [...] e levam o Debian a um número maior de pessoas com experiências e necessidades mais diversas do que o público que alcançamos atualmente. 

Exemplos de distribuições Linux [baseadas no Debian](https://pt.linux-console.net/?p=189):

**Ubuntu**

![p0201-ubuntu-interface.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648661175916/L2efXk213.png)

**Linux Mint**

![p0202-linux-mint.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648661227996/JMQxmmmvh.png)

**Kali Linux**

![p02i03-kali-linux.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648661242516/Npq9u2bnR.png)

E aí? Olhando as três imagens acima de três distribuições diferentes, ainda acha o Linux um ambiente complexo que serve apenas para programadores avançados? Esta é uma discussão interessante e que vem à tona quando se fala em distribuições baseadas no Debian: um dos seus principais fatores de sucesso pode ser justamente atrelado a presença de interfaces amigáveis e altamente favoráveis, principalmente para usuários acostumados com ambientes Windows.

### Conhecendo melhor o Ubuntu

O Ubuntu é fornecido pela empresa [Canonical](https://canonical.com/) e seu nome é um derivado do idioma Zulu que indica a "humanidade através dos outros".

> "Eu sou o que sou pelo que você é!"

O logo do Ubuntu, inclusive, pode ser visto sob a ótica de três pessoas de mãos dadas.

![Ubuntu-circle.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1648662243882/P7BP_GYuF.jpg)

De fato, o Ubuntu tornou o Linux muito mais acessível. Sua interface baseada em [GNOME](https://en.wikipedia.org/wiki/GNOME) (*GNU Network Object Model Environment*) traz elementos gráficos atrativos para os mais diferentes usuários.

## Preparando um ambiente Linux

Dada a introdução sobre o propósito desta postagem, a partir deste ponto, serão dados os primeiros passos para que seja possível instalar e configurar uma máquina virtual Linux com a distribuição Ubuntu. De maneira visual, o diagrama abaixo pode servir como guia para os passos a serem dados a seguir:

![p01d01-configuracao-do-ambiente-linux.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1648521307666/W-Z0o3o98.PNG)

### Instalando o VirtualBox

Como primeiro passo, precisamos de um software de virtualização capaz de gerenciar nossa futura máquina virtual Linux. Uma escolha assertiva para este cenário é, sem dúvidas, o [VirtualBox](https://www.virtualbox.org/). Esta poderosa ferramenta *open source* é utilizada em larga escala, por empresas e entusiastas, entregando a seus usuários um pacote completo de opções relacionadas a virtualização de máquinas.

Para obtenção do VirtualBox, basta realizar o [download](https://www.virtualbox.org/wiki/Downloads) do software e sua subsequente instalação no sistema operacional de trabalho. Vale lembrar que o autor deste artigo está utilizando um sistema operacional Windows em toda a jornada, o que não impede o leitor de seguir os mesmos procedimentos, atentando apenas para possíveis particularidades do sistema operacional de trabalho.

Após o download e instalação, o software VirtualBox poderá ser acessado. A figura abaixo exemplifica sua interface.

![p01i01-virtualbox-installed.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648521668188/Oc9fpZXSY.png)

### Download do Ubuntu

O Ubuntu é a distribuição Linux escolhida para este tutorial de instalação.  Por possuir uma abordagem amigável e relativamente próxima ao Windows ou MacOS, o Ubuntu acaba sendo a porta de entrada para muitos entusiastas do Linux. Seu ambiente gráfico traz uma segurança adicional para aqueles que ainda possuem certo receio em operar em terminais ou com a linha de comando.

Assim, uma vez instalado o software de virtualização VirtualBox, é preciso realizar o download de uma imagem de sistema operacional (arquivo com extensão `.iso`) contendo todas as informações necessárias de _boot_. No caso do Ubuntu (e de muitas outras distribuições), existem uma série de versões gerenciadas e disponibilizadas pela comunidade que são atualizadas ao longo do tempo.

Ao visitar o site de [download do Ubuntu](https://ubuntu.com/download/desktop) ou mesmo o site de [_releases_](https://releases.ubuntu.com/), será possível visualizar algumas versões atualmente disponíveis. No momento de criação desta página, as versões *20.04.4 LTS (Focal Fossa)* e *18.04.6 LTSA (Bionic Beaver)* são as escolhas mais adequadas. Selecione uma dessas versões e realize o download da imagem.

A figura abaixo exemplifica três diferentes imagens do sistema operacional Ubuntu em três versões diferentes. Note que uma imagem é um arquivo `.iso` com alguns gigas de tamanho em disco.

![p01i02-ubuntu-images.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1648522503578/WJaJ5BpzY.PNG)

### Criando uma máquina virtual

Agora que temos em mãos todos os requisitos necessários, podemos iniciar a construção da nossa máquina virtual Linux com a distribuição Ubuntu. Para isso, com o software VirtualBox aberto, basta seguir os passos abaixo:

1. Clicar no botão "Novo"
2. Configurar um nome para a VM e um local para armazenar os arquivos associados. Opções a serem modificadas:
    - **Tipo:** Linux
    - **Versão:** Ubuntu (64-bit)
3. Configurar parâmetros de memória e armazenamento em disco nas seções subsequentes de criação da VM. As recomendações são:
    - **Memória:** 4096MB*
    - **Disco rígido:** Criar um novo disco rígido virtual agora
    - **Tipo de arquivo de disco rígido:** VDI (VirtualBox Disk Image)
    - **Armazenamento em disco rígido:** Dinamicamente alocado
    - **Tamanho do arquivo:** 40GB*

**Obs:** as opções marcadas com * devem ser configuradas de acordo com as capacidades atuais da máquina de trabalho.

Ao final do processo, uma nova entrada para a VM recém configurada estará disponível na interface do VirtualBox. Antes de inicializarmos nosso sistema Linux, vamos primeiro aplicar algumas configurações adicionais.

### Configurando a máquina virtual

O VirtualBox permite uma série de configurações adicionais a serem implementadas em uma VM criada. Parâmetros de sistema, monitor, áudio, armazenamento, rede, interface e uma série de outras opções podem ser alteradas de acordo com as necessidades e desejos do usuário. Este, inclusive, é um dos fatores que torna o VirtualBox um dos softwares mais utilizados pela comunidade de tecnologia para este tipo de propósito.

![p01i03-virtualbox-configs.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1648597297150/s14PXsOOO.PNG)

As configurações de uma VM podem ser modificadas a qualquer momento, sendo necessária apenas a reinicialização da máquina para que os efeitos sejam aplicados.

Nesta etapa, para que a VM criada e configurada possa ser inicializada da maneira correta, é preciso informar ao sistema o caminho para a imagem `.iso` da distribuição Ubuntu obtida nos passos anteriores. Assim, na janela de configurações da máquina virtual, selecione a categoria "Armazenamento" e siga as instruções abaixo visualmente complementadas por imagens:

**_Selecione a opção de controladora para busca do arquivo `.iso`_**
![p01i04-iso-config-01.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1648597827361/de6ELQ5Q-.PNG)

**_Selecione a imagem (arquivo `.iso`) do Ubuntu_**
![p01i05-iso-config-02.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1648597834872/56T28IrSR.PNG)

**_Finalize a operação clicando em "OK"_**
![p01i06-iso-config-03.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1648597838582/ppO0sonbQ.PNG)

Pronto! Agora será possível inicializar a máquina virtual Linux com a subsequente instalação do sistema operacional Ubuntu.

### Configurando e inicializando o Ubuntu

Após as devidas configurações no VirtualBox, basta selecionar a referida VM e clicar no botão "Inicializar". Como esta é a primeira inicialização, será preciso realizar a instalação e a configuração do Ubuntu. O processo é simples e intuitivo. A cada etapa, o sistema irá solicitar _inputs_ do usuário para proporcionar uma melhor experiência de uso. Leita atentamente as opções e escolha as que mais fazem sentido dentro de sua proposta de usabilidade.

Algumas recomendações:
- **Keyboard Layout:** Portuguese (Brazil)
- **What apps would you like to install to start with?** Minimal installation
- **Other options:** Download updates while installing Ubuntu
- **Installation type:** Erase disk and install Ubuntu

Ao final, o gerenciador de instalação do Ubuntu irá realizar o download dos arquivos necessários para a construção do sistema operacional. Basta aguardar.

![p01i07-ubuntu-installing.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648598380849/MTfIGIbqs.png)

Ao finalizar o processo, será solicitada a reinicialização da máquina. Uma vez realizado, tudo está pronto para que você possa dar seus primeiros passos em sua VM Linux.

![p01i08-ubuntu-login.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1648598626964/eqd1Mas6Y.png)

___

## Considerações Finais

Neste artigo, foi possível compreender melhor as distribuições Debian e o Ubuntu. Como principal ganho, foi fornecido um tutorial detalhado de instalação de um software de virtualização e a subsequente instalação e configuração de uma máquina virtual Linux sob a distribuição Ubuntu.

Complementando com os detalhes fornecidos pelo primeiro artigo, além de entender um pouco melhor sobre o Linux, agora podemos desbravar esse universo na prática dando os primeiros passos e executando os primeiros comandos em uma distribuição amigável. 

___

## Referências

- https://www.debian.org/derivatives/index.pt.html
- https://pt.linux-console.net/?p=189
- https://en.wikipedia.org/wiki/GNOME
- https://www.virtualbox.org/
- https://ubuntu.com/
- https://en.wikipedia.org/wiki/Linux_distribution
- https://ubuntu.com/download/desktop