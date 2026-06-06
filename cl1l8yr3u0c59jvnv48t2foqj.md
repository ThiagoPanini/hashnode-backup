---
title: "O Bash como Interpretador de Comandos"
datePublished: 2022-04-04T21:51:16.350Z
cuid: cl1l8yr3u0c59jvnv48t2foqj
slug: o-bash-como-interpretador-de-comandos
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1649024317524/7XGpQgmGn.PNG
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1649024337466/Ckj4MGo8G.PNG
tags: linux, terminal, bash, command-line, cli

---

No [artigo anterior](https://panini.hashnode.dev/operando-no-linux-conhecendo-o-shell), introduzimos a ideia do **shell** como um programa responsável por proporcionar integrações entre o sistema operacional e os usuários. Além disso, conhecemos as duas principais categorias deste tipo de aplicação (GUI e CLI) e entendemos como um sistema operacional recebe *inputs* dos usuários para realizar as mais variadas ações.

Ainda neste contexto, este artigo tem por objetivo explicar um pouco mais sobre os interpretadores de comando de um sistema operacional. Na prática, são eles os responsáveis por receber as entradas dos usuários na forma de comandos, interpretar e "traduzir" para o sistema operacional as ações solicitadas. 

## Interpretadores de Comandos

Já sabemos que ao entrar em uma interface de linha de comando e digitar, por exemplo, um código para listar os arquivos presentes em determinado diretório, estamos realizando uma operação via shell. Entre a inserção deste comando específico até a ação realizada no sistema operacional, existe um elemento intermediário capaz de entender o que está sendo pedido e enviar a solicitação ao sistema: os **interpretadores**.

Em sistemas Unix, existem diferentes tipos de intermediadores e interpretadores de comandos. Alguns exemplos são:

- Bourne Shell (sh)
- Korn Shell (sh)
- POSIX Shell (psh)
- Bourne Again Shell (bash)

De acordo com o artigo escrito por [Ariane G.](https://www.hostinger.com.br/tutoriais/comandos-bash-linux), uma lista completa de interpretadores shell pode ser acessada através da execução do seguinte comando em um sistema operacional Unix:

```cat /etc/shells``` 

O resultado será algo como:

```
/bin/bash
/bin/sh
/bin/tcsh
/bin/csh
```

Nos tópicos subsequentes, iremos explorar o Bash em detalhes e vamos explicar algumas das suas principais características que o tornam, sem sombra de dúvidas, uma das principais ferramentas para interpretação de código em sistemas Unix.

___

## Bash - Bourne Again Shell

O Bash (acrônimo para *Bourne Again Shell*) é um interpretador de comandos de sistemas Unix que surgiu como uma grande evolução do Bourne Shell (sh). Criado como parte do projeto GNU (mais uma vez, te convido a ler o [primeiro artigo](https://panini.hashnode.dev/conhecendo-o-linux-e-sua-historia) desta série se esta sigla soar estranha para você), o Bash teve como propósito a consolidação das características do seu antecessor e a inclusão de algumas funcionalidades adicionais.

Em geral, o Bash é executado em uma janela de texto onde usuários digitam comandos (terminal). Também é possível executar comandos através de um arquivo em um processo conhecido como **shell scripting**.

Fato é que o Bash hoje é uma das mais famosas ferramentas de script de sistemas Unix. Sua primeira versão foi lançada em 1989 e, atualmente, é utilizado como o shell padrão na grande maioria das distribuições GNU/Linux.

### Alguns exemplos de comandos

Em uma janela de terminal aberta, o comando `ls` pode ser utilizado para listar arquivos e diretórios presentes no caminho atual ou em um caminho especificado como argumento do comando:

![img01-ls.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1649023482998/zOnoDe-MB.PNG)

Em geral, os comandos Bash seguem um padrão dado por `<comando> <parametros>`. Ainda no exemplo acima, o comando `ls` poderia receber o parâmetro `-l` para uma listagem mais completa ou ainda o parâmetro `-a` para mostrar também arquivos ocultos (aqueles cujos nomes são iniciados por `.`). 

![img02-ls-la.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1649023689649/y2UHKuC-k.PNG)

Um outro exemplo comumente utilizado em operações via shell é a criação de diretórios. No exemplo abaixo, o comando `mkdir` pode ser utilizado para criar um novo diretório dentro de `~/Downloads`. Na sequência, o comando `ls` é utilizado para visualizar o novo diretório criado.

![img03-mkdir.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1649023861593/Pmc7Okum2.PNG)

Existem ainda uma série de outros comandos e exemplos que poderiam ser citados e demonstrados. O comando `cp` para copiar arquivos ou o `mv` para mover arquivos são largamente utilizados. O `touch` permite criar um novo arquivo e o `cat` permite mostrar na saída padrão do sistema o conteúdo de um arquivo.

Como o intuito deste artigo foi proporcionar uma visão geral sobre o Bash como um interpretador de comandos, garantindo o entendimento desta ferramenta e sua integração com o shell, CLI e outros termos já definidos, um detalhamento maior dos comandos será proporcionado em um próximo artigo nesta série.

### Primeiros passos no shell scripting

Apenas para deixar um gostinho especial para o leitor, vamos explorar um exemplo bem simples de criação de um script shell interpretado pelo Bash para realizar algumas operações específicas.

Com o terminal aberto e, utilizando um editor de texto de sua escolha (`nano`, `vi`, `vim`, etc), crie um arquivo com a extensão `.sh` em qualquer caminho acessível no sistema.

```bash
nano exemplo_script.sh
```

Neste caso, como o editor de texto nano foi utilizado, uma nova janela do nano será mostrada no terminal onde será possível alimentar o arquivo `.sh` com o código determinado. Por convenção, se a intenção é criar um arquivo que servirá como um script shell, então este arquivo deve, obrigatoriamente, iniciar com a seguinte sintaxe:

```bash
#!/bin/interpretador
```

Onde ```interpretador``` é, de fato, a linguagem utilizada para interpretar os comandos estabelecidos. No nosso caso, utilizaremos o bash e, dessa forma, a primeira linha do arquivo de script recém criado será dada por `#!/bin/bash`. 

Este primeiro elemento de um arquivo de script é importante para direcionar o sistema operacional a utilizar o interpretador correto. Em sistemas Linux, normalmente os "motores" de interpretadores estão posicionados no diretório `/bin`, o que dá um significado mais claro para esta convenção. Como curiosidade, segundo artigo escrito para o site [freecodecamp](https://www.freecodecamp.org/news/linux-command-line-bash-tutorial/), o elemento `#!` é normalmente conhecido como “hash-bang”, “she-bang” ou “sha-bang”.

Assim, após a inserção deste elemento direcionador, é possível inserir os comandos associados ao nosso script. Visando exemplificar algo da forma mais simples possível, o comando `echo` será utilizado para mostrar o texto "Hello World" na saída padrão do sistema. Dessa forma, o script `exemplo_script.sh` será composto por:

```bash
#!/bin/bash
echo "Hello World"
```

![img04-script-01.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1649107128925/K1q6YEWro.PNG)

Após isso, basta fechar e salvar o arquivo. Caso tenha utilizado o nano como editor de texto, basta pressionar `Ctrl`+ `X` e confirmar o salvamento do arquivo com `Y`. O comando `ls` pode ser utilizado para verificar se o arquivo está presente no diretório especificado pelo usuário.

![img05-script-02.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1649107136575/J8az9Drc8.PNG)

Depois de criar o script adequado, é preciso conceder as permissões necessárias para que o usuário do sistema possa executá-lo. O comando para este tipo de operação é o `chmod` e os níveis de permissão podem ser concedidos como:

```bash
chmod +x exemplo_script.sh
```

Por fim, para executar o script criado, basta executar chamá-lo no terminal utilizando a sintaxe:

```bash
./exemplo_script.sh
```

O resultado obtido será o texto "Hello World" mostrado na tela, visto que utilizamos o comando `echo` para realizar esta operação dentro do script.

![img05-script-03.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1649108182573/KY2NLB_HG.PNG)

Agora que temos uma noção primária sobre como criar scripts bash no Linux, o exemplo abaixo traz uma sintaxe relativamente mais complexa e utiliza, em sua essência, parâmetros e variáveis para criar um diretório de forma dinâmica de acordo com a entrada do usuário. Não se atente ao conteúdo do script pois, de certa forma, iremos abordar detalhes sobre shell scripting em um futuro não tão distante nesta série. A ideia deste exemplo é proporcionar uma visão com um tempero a mais para o leitor.

Assim, caso queira seguir os passos subsequentes, basta criar um arquivo de extensão `.sh` utilizando um editor de texto de sua escolha (ex: `nano create_dir.sh`). O conteúdo deste arquivo poderá ser alimentado com o script abaixo.

```bash
#!/bin/bash

# Recebendo entrada do usuário
read -e -p "Entre com o diretório: " base_path

# Criando variáveis para o diretório
dir_path=$1/base_path

# Executando comando
mkdir -p $dir_path
echo "Diretório $dir_path criado com sucesso"
```

Após fechar e salvar o arquivo, não se esqueça de configurar suas permissões de execução com o comando `chmod +x create_dir.sh`.

Sobre a lógica implementada, é válido citar que o script recebe um argumento determinado pelo elemento `$1` que é responsável, dentro dos propósitos estabelecidos no exemplo, por servir de diretório raiz para a criação de um subdiretório fornecido pelo usuário e coletado através do comando `read`. Ao final, o comando `mkdir` é utilizado com as variáveis criadas ao longo do script para formalizar a criação do diretório estabelecido. Um exemplo de execução deste script seria dado por:

```bash
./create_dir.sh ~/Downloads
```

O parâmetro de referência `$1` para o script foi passado como `~/Downloads`, indicando assim que o subdiretório será criado dentro deste diretório principal. Na sequência, o script solicitará uma entrada do usuário para saber, de fato, o nome do subdiretório a ser criado. Ao passar essa informação, será possível visualizar o novo subdiretório dentro do diretório principal passado como argumento:

![img05-script-05.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1649108655033/D4k1Vsk2F.PNG)

___

## Considerações Finais

Gostaria de reservar este passo para você que chegou até aqui e que tem acompanhado as postagens desta série de Linux. Muitos dos conceitos aqui escritos foram literalmente descobertos pelo autor no ato do estudo das referências, o que já justifica e prova o sucesso de todo o conteúdo aqui consolidado. Venho aprendendo muito e espero sinceramente que os tópicos aqui escritos estejam impactando positivamente sua jornada de aprendizado básico no Linux!

Perdeu alguma coisa?

- [01 - Conhecendo o Linux e sua história](https://panini.hashnode.dev/conhecendo-o-linux-e-sua-historia)
- [02 - Configurando uma máquina virtual Linux](https://panini.hashnode.dev/configurando-uma-maquina-virtual-linux)
- [03 - Operando no Linux: o Shell](https://panini.hashnode.dev/operando-no-linux-conhecendo-o-shell)

___

## Referências

- https://en.wikipedia.org/wiki/Shell_(computing)
- https://en.wikipedia.org/wiki/Unix_shell
- https://en.wikipedia.org/wiki/Bash_(Unix_shell)
- https://www.freecodecamp.org/news/linux-command-line-bash-tutorial/
- https://www.hostinger.com.br/tutoriais/comandos-bash-linu