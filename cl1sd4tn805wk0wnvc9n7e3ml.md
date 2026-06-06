---
title: "Conhecendo a Raiz de um Sistema Linux"
datePublished: 2022-04-09T21:22:21.314Z
cuid: cl1sd4tn805wk0wnvc9n7e3ml
slug: conhecendo-a-raiz-de-um-sistema-linux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1649382831499/IU0FcP50N.PNG
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1649382882934/DMMsY_-jV.PNG
tags: ubuntu, operating-system, linux, os, linux-for-beginners

---

Bem-vindos a mais um artigo desta humilde e guerreira série de Linux! Em um *flashback* rápido de aprendizado, é imprescindível destacar o conteúdo abordado e absorvido nos últimos artigos. Entre os avanços obtidos, superamos obstáculos técnicos em tópicos como shell, bash, apt e instalação de pacotes. Expectativas foram criadas e estão sendo cumpridas!

Em uma busca constante no entendimento do Linux e de seus elementos, esta postagem trará um assunto curioso e igualmente importante: a raíz de um sistema Linux. O que tem lá dentro? Quais os diretórios existentes e suas respectivas funções? Esses são exemplos de perguntas que pretendemos responder na evolução textual a seguir.

Por mais complexo que isso possa parecer, o conteúdo aqui estabelecido será simples e direto. Basicamente, a ideia é proporcionar uma visão geral dos diretórios presentes na raiz `/` do sistema que sempre estiveram lá e nunca foram explorados (até agora).

## A raiz do sistema

Para acessar a raiz do sistema Ubuntu, basta navegar até o diretório `/` (barra) e listar os arquivos e diretórios presentes.

![img01-root.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1649213398121/Ab6oBkL_V.PNG)

Literalmente, esta é a raiz de uma distribuição Ubuntu. Nela, é possível encontrar uma série de diretórios, arquivos e links diversos, cada qual com sua função específica dentro do conjunto do sistema operacional.

Segundo o professor Ricardo, na [série de Linux](https://www.youtube.com/watch?v=mgs92GtkQCE&list=PLHz_AreHm4dlIXleu20uwPWFOSswqLYbV&index=10) gravada para o canal Curso em Vídeo no YouTube, existe uma norma mantida pela Linux Foundation que determina que distribuições Linux devem seguir (ou se inspirar) neste formato de construção do sistema.

A tabela abaixo traz uma visão geral sobre a função de alguns dos principais diretórios presentes na raiz do sistema:

| Diretório | Função |
| :---: | :---: |
| `/bin` | Diretório que armazena todos os comandos (arquivos binários) do sistema (ex: `ls`, `mkdir`, `rm`) |
| `/sbin` | Diretório que armazena os comandos executáveis de uso exclusivo do usuário root |
| `/boot` | Arquivos de configuração do *boot*, *kernels* e outros arquivos necessários |
| `/dev` | Abreviação de *device*, este é o diretório onde encontram-se os dispositivos do sistema (ex: hd da máquina, partições, pen drives). Na prática, os pontos de montagens de dispositivos normalmente são acessados em `/media`.  |
| `/etc` | Possui arquivos de configuração, scripts de inicialização, entre outros elementos. Desenvolvedores costumam literalmente considerar o significado deste diretório como "etcetera". |
| `/home` | Local de armazenamento de diretórios de usuários. Cada novo usuário Linux criado possuirá um diretório próprio no caminho `/home/nomeusuario`. |
| `/lost+found` | Fornece um sistema de "achados e perdidos" para arquivos que existem sob o diretório root (`/`) |
| `/media` | Diretório utilizado para montagem automática de partições no disco rígido ou mídias removíveis, como pendrives e outros dispositivos USB |
| `/mnt` | Diretório utilizado para montagem manual de arquivos e dispositivos no disco rígido. |
| `/opt` | Diretório que pode ser utilizado para a instalação de alguns programas externos (ex: Hadoop, Hive, Spark) |
| `/proc` | Representa os processos executados no sistema como diretórios. Um exemplo prático de utilização é executar o comando `ps` para listar os PIDs de processos executados e, no diretório `/proc`, navegar até o respectivo diretório de ID (que certamente estará lá) para visualizar detalhes de baixo nível dos processos. |
| `/root` | Diretório equivalente ao `/home` para o usuário root (administrador da máquina) |
| `/run` | Diretório utilizado para armazenar as informações necessárias para que um determinado programa ou processo possa ser executado. |
| `/srv` | Acrônimo de *serve*, este diretório pode conter arquivos que são servidos para outros sistemas. |
| `/sys` | Contém arquivos de sistema. |
| `/tmp` | Diretório que armazena arquivos temporários sem a garantir, por parte do sistema, que existirão no próximo *boot*. |  
| `/usr` | É um dos maiores diretórios sistema e armazena boa parte das aplicações instaladas. Seu acrônimo é Unix System Resources, mas |
| `/var` | Diretório que contém dados variáveis. O `/var/logs` serve para armazenamento de logs, o `/var/mail` para o envio de e-mail. O `/var/run` possui PIDs (Process IDs) de processos executados. O `/var/cache` para alguns caches do sistema. |

___

## Considerações Finais

Ter uma visão genérica e básica sobre o conteúdo da raiz de um sistema Linux é um feito bacana que pode propor uma maior autonomia no gerenciamento do sistema e no conhecimento agregado. Da maneira mais direta possível, este artigo trouxe algumas definições gerais sobre o significado de alguns dos principais diretórios. Para alcançar este feito, algumas referências fundamentais foram consumidas e podem ser visualizadas na seção abaixo. Entretanto, como forma de agradecimento, quero, mais uma vez, citar de maneira especial dois excelentes vídeos já citados em artigos anteriores.

O primeiro deles é o guia definitivo de Ubuntu gravado por Fabio Akita para o YouTube. O vídeo é longo e as informações relacionadas à raiz de um sistema Linux podem ser encontradas entre os minutos 23:00m e 30:00m.

%[https://www.youtube.com/watch?v=epiyExCyb2s&t=912s]

Já o segundo é mais uma recomendação da série de Linux do canal Curso em Vídeo. Nele, os professores Gustavo Guanabara e Ricardo Pinheiro abordam conceitos do terminal Linux e informações adicionais do sistema, como o conteúdo da raiz. O tema deste artigo pode ser assistido entre os minutos 15:00m e 21:00m.

%[https://www.youtube.com/watch?v=mgs92GtkQCE&t=1227s]

___

## Referências

- https://www.youtube.com/watch?v=mgs92GtkQCE&list=PLHz_AreHm4dlIXleu20uwPWFOSswqLYbV&index=10
- https://www.youtube.com/watch?v=epiyExCyb2s&t=2378s
- https://www.linuxando.com/tutorial.php?t=A%20estrutura%20de%20diret%C3%B3rios%20Linux_6#:~:text=O%20%2F%20%C3%A9%20o%20root%20ou,dentro%20da%20raiz%20do%20sistema.
- https://help.ubuntu.com/kubuntu/desktopguide/pt_BR/directories-file-systems.html
