---
title: "O APT e o Gerenciamento de Pacotes"
datePublished: 2022-04-08T21:30:05.205Z
cuid: cl1qxywxx02re0wnv8gfm5a32
slug: o-apt-e-o-gerenciamento-de-pacotes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1649382808198/YH-9aTDfz.PNG
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1649382818389/260L2zXXy.PNG
tags: ubuntu, linux, package, linux-for-beginners, linux-basics

---

Após conhecer alguns dos [principais comandos](https://panini.hashnode.dev/principais-comandos-e-atalhos) que podem ser utilizados em uma distribuição GNU/Linux, a sequência de aprendizado nesta série trará um tema igualmente importante: o gerenciamento de pacotes do sistema.

Com o crescimento das distribuições, uma série de gerenciadores de pacotes surgiram e foram se estabelecendo em meio à comunidade. Certamente, conhecer o gerenciador de pacotes da distribuição GNU/Linux em que se está operando é essencial para ter uma noção clara sobre algumas ações comumente utilizadas em uma rotina de trabalho, como por exemplo:

- Listagem de repositórios
- Obtenção e instalação de pacotes
- Remoção e atualização de programas

Neste artigo, será proposta uma leve imersão no universo de gerenciamento de pacotes em ambientes Linux, entregando tópicos relevante sobre algumas operações que ocorrem por trás de alguns comandos de instalação ou remoção de programas.

___

## Definição de pacotes e dependências

Como ponto de partida, antes de falar de **gerenciadores de pacotes**, é essencial falar sobre **pacotes**. De forma direta, segundo [material](https://docente.ifrn.edu.br/filiperaulino/disciplinas/introducao-a-sistemas-abertos-redes2v/aulas/linux-07-gerencia-de-pacotes) disponibilizado pelo Instituto Federal do Rio Grande do Norte, **pacotes** são arquivos que contém bibliotecas ou programas já compilados e seus arquivos de configuração, incluindo aqueles necessários para a sua instalação. Em sistemas Debian, por exemplo, um pacote de instalação é identificado pela extensão `.deb`. Em sistemas RedHat, por sua vez, os pacotes são identificados pela extensão `.rpm`.

Já **dependências** são pacotes requeridos para a instalação de um outro pacote. Normalmente, os pacotes são desenvolvidos e construídos com base em algumas premissas necessárias para seu funcionamento. Dessa forma, a instalação destes pacotes irá exigir a presença destas premissas (ou dependências) para que as funcionalidades adequadas possam ser aplicadas.

Introduzidos os insumos, é chegada a hora de conhecer os gerenciadores de pacotes de sistemas Linux.

___

## Diferentes gerenciadores de pacotes

Como informado na início deste artigo, o crescimento das distribuições GNU/Linux ao longo dos anos fomentou o desenvolvimento e utilização de gerenciadores de pacotes específicos para cada sistema. Dessa forma, é correto dizer que certas distribuições utilizam certos gerenciadores de pacotes e, neste cenário, a tabela abaixo traz uma visão geral sobre alguns termos normalmente encontrados ou até mesmo utilizado no cotidiano Linux:

| Gerenciador | Acrônimo | Utilizado em Pacotes | Exemplos de Distros | Exemplo de Uso |
| :---: | :---: | :---: | :---: |
| APT | *Advanced Package Tool* | `.deb` | Ubuntu, Linux Mint, Kali Linux | `sudo apt install pacote` |
| YUM | *Yellow Dog Updater, Modified* | `.rpm` | Fedora, CentOS, RedHat Enterprise | `sudo yum install pacote` |
| DNF | *Dandified YUM* | `.rpm` | Fedora, CentOS, RedHat Enterprise | `sudo dnf install pacote` |

Existem ainda outros gerenciadores que poderiam ser citados. Para maiores detalhes, a leitura do artigo [7 Gerenciadores de Pacotes Linux que você Deve Conhecer](https://e-tinet.com/linux/7-gerenciadores-de-pacotes-linux/) pode ser de grande utilidade.

Assim, apresentados alguns conceitos fundamentais, no decorrer deste artigo será proposto um detalhamento maior e específico no gerenciador de pacotes APT, visto que trata-se de um elemento padrão em distribuições Debian (assim como o Ubuntu instalado e configurado em artigos anteriores nesta série).

___

## APT - Advanced Package Tool

O professor Edinaldo La Roque, em um [vídeo](https://www.youtube.com/watch?v=Xfgdu94sAcA) para seu canal no YouTube, define o APT como um sistema de gerenciamento de pacotes composto por um conjunto de ferramentas para download, remoção, atualização e configuração de pacotes do mundo Debian utilizando o utilitário DPKG como motor. Como principal característica, o APT consegue gerenciar automaticamente as dependências de cada pacote instalado, possibilitando assim uma operação simples e dinâmica na obtenção de novos softwares ou programas.

O APT é um dos gerenciadores de pacotes mais antigos do universo Linux. À ele, pode ser atribuído um dos grandes fatores de sucesso das distribuições Debian, dada sua facilidade na obtenção de pacotes e gerenciamento de dependências.

Na prática, o APT conecta o computador a um repositório de pacotes e, por meio dele, faz as instalações ou atualizações do sistema. Considerando este cenário, é válido destacar a presença de um **repositório de pacotes** central que armazena, de fato, os insumos necessários para as operações realizadas pelo gerenciador.

### Configurando o APT e os repositórios de pacotes

Em sistemas Linux baseados no Debian e que utilizam o APT como gerenciador de pacotes, informações adicionais sobre a configuração do gerenciador e dos repositórios de pacotes usados no sistema podem ser visualizadas acessando o diretório `/etc/apt`. O código abaixo navega até o diretório informado e lista os arquivos presentes.

```bash
cd /etc/apt
ls -l
```

![img01-apt-dir.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1649200213373/QFIXKvSoN.PNG)

Na prática, o arquivo `sources.list` funciona literalmente como uma "lista de fontes" e contém a lista dos repositórios que armazenam os pacotes a serem instalados no sistema. Essencialmente, quando o usuário solicita a instalação de um novo programa ou pacote, os repositórios configurados no arquivo `/etc/apt/sources.list` são utilizados como base para obtenção dos elementos necessários. Seu conteúdo pode ser visualizado através de um editor de texto:

```bash
nano sources.list
```

![img02-sourceslist.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1649200459354/B36fiw-PM.PNG)

Pela figura acima, é possível perceber algumas entradas presentes no arquivo formadas pelo seguinte padrão:

```
<tipo do repositório> <endereço do repositório> <tipo de distribuição> <seções>
```

Como exemplo, a primeira linha não comentada presente no arquivo `sources.list` exemplificado acima contém a seguinte informação:

- **Tipo do repositório:** deb (isto é, arquivos binários do Debian)
- **Endereço do repositório:** http://br.archive.ubuntu.com/ubuntu
- **Tipo de distribuição:** focal (isto é, o nome dado a versão utilizada do Ubuntu 20.04 - focal fossa)
- **Seções:** main e restricted

Assim, quando o usuário executa o comando `sudo apt install <nome_pacote>` para instalação de um pacote qualquer, o APT confere a lista de repositórios configurados no arquivo `sources.list` e, dessa forma, realiza a busca do `<nome_pacote>` solicitado para a devida instalação. Com a crescente difusão do Linux nos últimos tempos, grande parte dos programas e softwares comumente utilizados no dia a dia de trabalho estão presentes nos repositórios oficiais de grande parte das distribuições, o que permite, de fato, um menor trabalho operacional dos usuários para obtenção dos mesmos.

### Atualizando os repositórios e pacotes

Um comando comumente utilizado é o `apt update` e, de forma objetiva, este comando atualiza a lista de repositórios dos softwares já instalados e busca por novas versões disponíveis. Neste cenário, nenhuma atualização é realizada, mas sim a procura e listagem por novas versões disponíveis dos softwares e programas já instalados no sistema.

Já o comando `apt upgrade` realiza, de fato, a atualização dos pacotes instalados considerando as novas versões disponíveis. 

### Instalando um pacote presente no repositório

De uma forma intuitiva e dinâmica, o [vídeo](https://www.youtube.com/watch?v=d6xOB7hG7eo) gravado pelo professor Fábio para o canal Bóson Treinamentos do YouTube traz um exemplo de utilização do APT para instalação do pacote/programa `tree`. Seu funcionamento está atrelado a visualização de elementos de um diretório do sistema em um formato de "árvore".

De forma prévia, a imagem abaixo realiza uma tentativa de execução do comando antes de sua instalação.

![img03-tree-not-found.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1649201346004/973OtXUD2.PNG)

Considerando a versão utilizada do Ubuntu (20.04), é interessante citar que o terminal mostra para o usuário algumas opções plausíveis para tentar executar o comando solicitado, dado que nenhum pacote do tipo foi encontrado no sistema. Um deles usa o APT e, dessa forma, o comando abaixo pode ser realizado para a devida instalação do pacote.

```bash
sudo apt install tree
```

Até este ponto, é possível entender as operações realizadas pelo gerenciador APT para a obtenção, de fato, do pacote solicitado. No fundo, a lista de repositórios oficial é consultada e um arquivo binário de extensão `.deb` é obtido para a devida instalação do pacote. As mensagens no terminal estão mais claras após esta explicação.

![img04-tree-install.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1649201518803/lGEZDQJjq.PNG)

Após a instalação, o pacote `tree` pode ser utilizado como um novo comando no sistema, permitindo uma listagem dinâmica do conteúdo de um diretório ou caminho em um formato amigável de árvore.

![img05-tree-exec.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1649201576059/_wiyaRA3H.PNG)

Este processo pode ser realizado para grande parte dos pacotes ou programas desejados. Para tal, basta conhecer o nome do pacote associado para a sua inclusão no comando de instalação do APT. Ao final deste artigo, uma tabela resumida será disponibilizada com os principais comandos a serem utilizados em uma jornada básica de operação no Linux.

### Removendo um pacote

Supondo a necessidade de remover um pacote instalado incorretamente ou que não tem mais uso no sistema, o comando `apt remove` pode ser utilizado. Em continuidade ao exemplo acima, para a remoção do pacote `tree`, o comando abaixo poderia ser utilizado:

```bash
sudo apt remove tree
```

![img05-tree-remove.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1649201707870/waXFhOieB.PNG)

Dessa forma, o usuário não mais poderá utilizar as funcionalidades proporcionadas pelo pacote removido. 

Como dito anteriormente, o APT gerencia e instala automaticamente todas as dependências dos pacotes solicitados, mas não realiza sua remoção automática quando este mesmo pacote é removido. Isto é plausível, dado que as dependências podem estar sendo utilizadas em outros pacotes, tornando sua remoção uma possível causa de problemas mais sérios no sistema.

Para isso, sempre que um pacote que possui dependências for removido, o terminal irá alertar sobre algumas dependências que podem estar presentes no sistema, porém sem utilidade. Para remover estas dependências, **na certeza de que elas realmente não estão sendo utilizadas**, é possível utilizar o comando `apt autoremove`.

### Outras operações com o APT

Por fim, a tabela abaixo consolida algumas ações comumente utilizadas com o gerenciador de pacotes APT.

| Comando | Ação |
| :---: | :---: |
| `apt update` | Realiza a atualização dos repositórios do sistema e busca por novas versões dos pacotes instalados |
| `apt upgrade` | Realiza a atualização dos pacotes, de fato |
| `apt install <nome_pacote>` | Procura o pacote na lista de repositórios configurada e realiza sua instalação, caso encontrado, junto com suas dependências |
| `apt remove <nome_pacote>` | Realiza a remoção do pacote solicitado, mas mantém as dependências instaladas, caso existirem |
| `apt-cache search <nome_pacote>` | Permite procurar por um determinado pacote na listas de pacotes disponíveis no repositório configurado. Este é um comando interessante para validar se realmente um pacote existe nos repositórios. Por padrão, procura é feita tanto no nome do pacote quanto nas descrições dos pacotes disponíveis. Caso seja necessário procurar apenas pelo nome, é possível utilizar a opção `--names-only` |
| `apt-cache stats` | Mostra indicadores de pacotes e dependências instaladas |
| `apt-cache dump` | Lista todos os pacotes instalados no sistema. Como normalmente, o retorno deste comando é extenso, utiliza-se a junção com o `less`. |

___

## Alternativas para instalação de pacotes

Em uma distribuição Linux com ambiente gráfico, é possível utilizar alguns gerenciadores mais amigáveis para instalação ou remoção de pacotes do sistema. No caso do Ubuntu, existe um aplicativo chamado Ubuntu Software que permite aos usuários procurar e instalar os mais variados softwares disponíveis.

![img07-ubuntu-software.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1649203516302/bMQp3W7T_.PNG)

Em cenários de utilização de ambientes Linux com essa possibilidade, esta certamente é uma alternativa visualmente interessante para gerenciar pacotes. Entretanto, nem sempre há tal disponibilidade e, em muitos casos, tudo que se tem é um terminal de comando para a realização de operações no sistema. Nestes casos, o APT e o DPKG serão grandes amigos!

___

## Considerações Finais

Nesta jornada de aprendizado, conhecer sobre os gerenciadores de pacotes do sistema de trabalho é fundamental para obter uma maior liberdade de utilização e extrair um maior poder de uso do ambiente. Como dito previamente, o APT é uma ferramenta extremamente poderosa que realmente transformou o gerenciamento de pacotes e dependências em sistemas Linux.

Espero que tenha sido uma ótima leitura e que este conteúdo tenha impactado positivamente em seu conhecimento! Consulte as referências para maiores detalhes sobre este assunto.

Até a próxima!

___

## Referências
- https://www.youtube.com/watch?v=d6xOB7hG7eo
- https://www.youtube.com/watch?v=ar_95wlzim0
- https://www.youtube.com/watch?v=Xfgdu94sAcA
- https://www.youtube.com/watch?v=Pu3Uy92Moxo
- https://docente.ifrn.edu.br/filiperaulino/disciplinas/introducao-a-sistemas-abertos-redes2v/aulas/linux-07-gerencia-de-pacotes
