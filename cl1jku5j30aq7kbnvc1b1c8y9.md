---
title: "Operando no Linux: Conhecendo o Shell"
datePublished: 2022-04-03T17:48:04.815Z
cuid: cl1jku5j30aq7kbnvc1b1c8y9
slug: operando-no-linux-conhecendo-o-shell
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1649007554733/JuFla7HP3.PNG
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1649007986088/QRe0CTek2.PNG
tags: linux, cli, shell, gui, linux-for-beginners

---

No [artigo anterior](https://panini.hashnode.dev/configurando-uma-maquina-virtual-linux), conhecemos um pouco mais sobre o Ubuntu como uma distribuição GNU/Linux baseada no Debian e realizamos sua instalação em uma máquina virtual através do software VirtualBox.

Neste artigo, vamos explorar as diferentes formas de operação em ambiente Linux. Se você sempre teve curiosidade em conhecer termos como **shell**, **CLI** e **GUI**, saiba que este é o post certo!

## Conhecendo o Shell

Em uma definição formal, o shell pode ser dado como um programa de computador capaz de integrar os serviços de um sistema operacional à usuários ou outros programas. Basicamente, o shell é a ligação entre o usuário e o sistema e é ele quem interpreta os comandos enviados para outros aplicativos ou diretamente em chamadas de sistema.

![img01-kernel-diagram.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1649000206023/CdPjuPesS.jpg)

Historicamente falando, em 1964, para o sistema operacional Multics (e se você não reconhece este termo, te convido a ler o [primeiro artigo desta série de Linux](https://panini.hashnode.dev/conhecendo-o-linux-e-sua-historia)), Louis Pouzin concebeu a ideia de "usar comandos em um sistema operacional como uma linguagem de programação" e assim lançou o termo **shell** para descrevê-la.

## Tipos de Shell

Sistemas operacionais, em geral, proporcionam aos usuários uma série de serviços relevantes, como o gerenciamento de arquivos e processos, execução de processos em batch, monitoramento, configuração, entre outros.

Sabendo agora a definição de shell como um "meio de campo" entre o usuário e o sistema, é interessante conhecer como toda esta integração é proporcionada. Em essência, grande parte dos shells de sistemas operacionais podem ser divididos em duas principais categorias:

- GUI (*Graphic User Interface*)
- CLI (*Command Line Interface*)

E aqui conhecemos mais dois termos comumente utilizados e que serão explorados em maiores detalhes nas seções a seguir.

### GUI - Graphic User Interface

A interface gráfica do usuário (ou GUI) é um tipo de shell extremamente comum em ambientes de *desktop* presente em grande parte dos sistemas operacionais. Com esta interface, os usuários podem realizar as mais variadas operações, como listar e mover arquivos, gerenciar recursos, operações e uma série de outras funcionalidades.

![img02-gui-example.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649001132056/WLtNB2lGj.png)

Tecnicamente falando, operar em um sistema operacional através de uma interface gráfica é, no fundo, realizar ações shell via GUI. Se esta última frase não soou estranha para você com os novos termos aprendidos, significa que estamos no caminho certo.

Entretanto, existe um outro tipo de shell que abriu caminho para as primeiras explorações em sistemas operacionais.

### CLI - Command Line Interface

A famosa (e muitas vezes temida) linha de comando de um sistema é basicamente definida como um programa que permite que os usuários digitem comandos de texto dando instruções a um computador para realizar funções específicas. A grande diferença entre operar no shell via CLI e via GUI é justamente a ausência, no primeiro caso, de uma interface gráfica capaz de facilitar as operações para usuários que estão acostumados com este tipo abordagem. Para realizar atividades no sistema operacional utilizando a linha de comando, é preciso conhecer a sintaxe adequada dentro de um *pool* de comandos específicos para cada ação.

![img03-cli-example.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649005052591/YY2aPz_V7.png)

Neste cenário, é importante citar que outras aplicações também podem implementar sua própria interface de linha de comando, sendo esta de código aberto ou não. Exemplos comuns de CLIs:

* **AWS CLI (Amazon):** se você conhece um pouco sobre computação em nuvem, já deve ter se deparado com a famosa linha de comando da AWS conhecida como AWS CLI. Com ela, é possível operar sobre os mais variados serviços da AWS através de comandos específicos.

* **GIT (código aberto):** esta é um tipo de CLI que permite executar todos os comandos do CLI e traz uma extrema facilidade para usuários que pretendem realizar integrações com esta ferramenta.

### Afinal, devo escolher entre CLI ou GUI?

De acordo com o artigo escrito por [Andrei L. para a Hostinger](https://www.hostinger.com.br/tutoriais/o-que-e-cli/), nos anos 60, a CLI era usada a todo momento pois, naquele tempo, os usuários tinham em mãos apenas teclados como dispositivos de entrada e uma tela do computador. A inserção de comandos nesta troca de informações era a única forma de se comunicar com os computadores.

Mas e nos tempos atuais? Continua fazendo sentido utilizar a linha de comando mesmo com os crescentes avanços das interfaces gráficas? A resposta é sim, operar na linha de comando garante algumas vantagens especiais aos usuários, como por exemplo:

1. **Recursos:** programas baseados em texto consomem menos recursos de um computador do que uma interface gráfica
2. **Alta precisão:** uma sequência de comandos atua como uma automação com alta taxa de precisão (considerando a escrita correta da sintaxe do código)
3. **Autonomia:** diferente das interfaces gráficas, a linha de comando provê uma maior autonomia sobre o sistema operacional de trabalho

Por outro lado, o artigo escrito por [Ariane G. para a Hostinger](https://www.hostinger.com.br/tutoriais/comandos-linux) defende que a maioria das pessoas que iniciam suas jornadas em sistemas operacionais Unix (em especial o Linux), acredita que são ferramentas apenas para programadores avançados. Ao operar um sistema operacional Linux, você precisa, de fato, usar um shell – uma interface que fornece acessos aos serviços do sistema operacional. Porém, nos tempos atuais, a maioria da distribuições Linux usa interface gráfica do usuário (GUI - *Graphic User Interface*) como shell, principalmente para fornecer facilidade de uso para seus usuários.

Dessa forma, é possível construir alguns pontos-chave em relação ao uso da interface de linha de comando frente a uma interface gráfica:

1. O Linux não é um sistema complexo feito apenas para programadores avançados 
2. Grande parte dos sistemas Linux possuem interfaces gráficas de usuário (GUI - *Graphic User Interface*) como alternativas extremamente amigáveis de usabilidade
3. Por mais intuitivas que sejam as alternativas, usar uma interface de linha de comando (CLI - *Command Line Interface*) é fundamental.

___

## Considerações Finais

Com este artigo, foi possível compreender alguns dos principais termos utilizados no universo de sistemas operacionais, principalmente baseados no Unix. De forma resumida, temos as seguintes definições:

| Termo | Conceito |
| :---: | :---: |
| Shell | Programa independente do usuário, executado fora do kernel, que fornece uma interface para interpretação de comandos |
| GUI | Interface gráfica de usuário que permitem operações no sistema operacional de forma visual e intuitiva |
| CLI | Interface de linha de comando que permite operações no sistema operacional através de códigos que respeitam uma sintaxe específica |

Existem, ainda, termos adicionais que serão explorados em postagens subsequentes nesta série. Afinal, conhecer o shell e as formas de operar em sistemas operacionais é apenas o começo da jornada. A completude do caminho terá seu clímax quando entendermos as maneiras utilizadas para interpretar os comandos passados pelos usuários e a sintaxe utilizada neste conceito. Se você pensou em termos como **terminal** e **bash**, acompanhe as próximas postagens! 
___

## Referências

- https://en.wikipedia.org/wiki/Shell_(computing)
- https://www.hostinger.com.br/tutoriais/comandos-linux
- https://www.hostinger.com.br/tutoriais/o-que-e-cli/
- https://www.linuxdescomplicado.com.br/2016/09/muito-alem-do-kernel-conheca-todos-os-elementos-que-formam-a-estrutura-do-sistema-linux.html
- https://www.youtube.com/watch?v=epiyExCyb2
