---
title: "Principais Comandos e Atalhos"
datePublished: 2022-04-06T11:10:25.200Z
cuid: cl1ngybbd00t9apnvhzbv7qeo
slug: principais-comandos-e-atalhos
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1649025816164/b5dpzpeHh.PNG
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1649025845968/CGSftTICx.PNG
tags: linux, bash, cli, shell, linux-for-beginners

---

Nos últimos dois artigos desta série, trouxemos algumas definições de suma importância para a operação em sistemas Unix. Se antes tudo era um mistério, com as últimas leituras é possível agora observar a tabela abaixo e ter um entendimento mais claro sobre alguns termos essenciais no cotidiano de uso de ambientes Linux.

| Termo | Definição |
| :---: | :---: |
| Shell | Programa independente do usuário, executado fora do kernel, que fornece uma interface para interpretação de comandos |
| CLI e GUI | Diferentes tipos de shell indicando, respectivamente, a interface de linha de comando e a interface gráfica de usuário |
| Bash | Um dos tipos mais famosos de interpretadores de comandos responsáveis por traduzir os inputs dos usuários para o sistema operacional |

Com tudo isso em mãos, o objetivo direto deste artigo é consolidar uma tabela com os principais comandos utilizados no terminal por usuários de Linux. Como bônus, também serão mostrados alguns dos principais atalhos que podem facilitar o dia a dia de trabalho neste ambiente operacional.

## Principais comandos do terminal

O Linux possui uma série de comandos que permitem que os usuários realizem as mais variadas operações através da interface de linha de comando. Normalmente, os comandos são abreviações de suas próprias ações realizadas, o que pode ser uma dica valiosa na hora de recordar algo (😅). A tabela abaixo traz alguns dos principais comandos coletados a partir de uma experiência prática de uso. 

| Comando | Acrônimo | Descrição | 
| :---: | :---: | :---: |
| `pwd` | *Print Working Directory* | Mostra o caminho atual do usuário no terminal |
| `cd` | *Change Directory* | Permite navegar entre diferentes diretórios no sistema |
| `ls` | *List* |  Lista os conteúdos de um diretório. Comumente utilizado com `ls -l` ou `ls -la` |
| `cat` | *Concat* | Utilizado para visualizar o conteúdo de um arquivo na saída padrão do sistema (stdout) ou concatenar dois arquivos em um só |
| `cp` | *Copy* | Copia arquivos de um diretório para outro |
| `mv` | *Move* | Move arquivos de um diretório para outro. Também pode ser utilizado para renomear arquivos. |
| `mkdir` | *Make Directory* | Cria diretórios no sistema. Eventualmente utilizado com `mkdir -p` para criar diretórios e subdiretórios para um caminho fornecido. |
| `rmdir` | *Remove Directory* | Remove diretórios vazios do sistema |
| `rm` | *Remove* | Remove arquivos de um diretório |
| `touch` | *Touch* | Permite criar um arquivo vazio no sistema operacional |
| `locate` | *Locate* | Permite localizar um arquivo no sistema. Aceita *wildcards* no parâmetro de pesquisa. |
| `find` | *Find* | Similar ao `locate`, porém utilizado para procurar arquivos em diretórios específicos |
| `grep` | *Global Regular Expression Print* | Permite procurar através do texto de um arquivo específico ou do resultado de um comando. Eventualmente utilizado em conjunto com o *pipe* em comandos encadeados. |
| `sudo` | *Super User Do* | Permite que tarefas sejam executadas sob permissões administrativas |
| `df` | *Disk Free* | Mostra a quantidade de espaço utilizado em disco no sistema |
| `du` | *Disk Usage* | Mostra a quantidade de espaço utilizado por um arquivo ou diretório |
| `head` | *Head* | Permite analisar as primeiras linhas de um arquivo de texto |
| `tail` | *Tail* | Permite analisar as últimas linhas de um arquivo de texto |
| `tar` | *Tape Archive* | Permite, entre outras funcionalidades, extrair arquivos tarball |
| `chmod` | *Change Mode* | Permite modificar permissões de um arquivo. Este é um comando complexo com uma série de opções que podem ser verificadas no [link](https://www.computerhope.com/unix/uchmod.htm) |
| `chown` | *Change Ownership* | Permite alterar a propriedade de um arquivo para fornecer permissões administrativos à outro usuário do sistema operacional |
| `wget` | *World Wide Web Get* | Permite baixar ou coletar arquivos da internet através de um link ou repositório |
| `uname` | *Unix name* | Mostra o nome do usuário do sistema |
| `man` | *manual* | Permite visualizar detalhes de documentação sobre instruções de um comando Linux |
| `echo` | *Echo* | Permite mostrar um texto na tela ou então transferir um texto para um arquivo específico através do comando adicional `>` |
| `zip` e `unzip` | *Zip* e *Unzip* | Permitem, respectivamente, compactar e descompactar arquivos do sistema |

___

## Principais atalhos do sistema operacional

Além dos comandos, a agilidade na operação em sistemas operacionais Linux também passa por alguns atalhos especiais que podem ser utilizados no dia a dia. A tabela abaixo irá consolidar alguns dos principais atalhos coletados através de uma experiência prática de uso do Ubuntu.

| Atalho | Uso | Ação / Descrição |
| :---: | :---: | :---: |
| `Ctrl` + `Alt` + `T` | Sistema | Abre o terminal Linux. Talvez este seja um dos atalhos mais importantes a serem mencionados 😂 |
| `TAB` | Terminal | Com o terminal aberto, o `tab` pode ser utilizado como um *auto complete* de comandos, diretórios ou nomes de arquivos do sistema |
| `Ctrl` + `Z` | Terminal | Utilizado para interromper um programa, comando ou processo no terminal |

___ 

## Considerações Finais

Conhecer os sistemas de trabalho é fundamental para uma operação confiante e segura. Ao longo desta jornada, consumi uma série de referências que puderam me auxiliar grandemente a entender um pouco mais sobre sistemas operacionais baseados no Unix. 

O primeiro vídeo que gostaria de compartilhar como referência em destaque é a excelente gravação do professor Fábio Akita. Nele, uma explicação resumida e eficaz sobre o Ubuntu é fornecida aos usuários. O vídeo é longo, mas vale a pena. Considerando as referências consumidas até este ponto desta série Linux, minha sugestão é assistir os 40 minutos do vídeo:

%[https://www.youtube.com/watch?v=epiyExCyb2s]

A segunda referência é um vídeo sobre Terminal gravado pelo professor Gustavo Guanabara para o canal Curso em Vídeo, também do YouTube. Além deste vídeo, recomendo a série inteira do canal que traz conceitos fundamentais sobre sistemas operacionais Linux.

%[https://www.youtube.com/watch?v=mgs92GtkQCE]

___

## Referências

- https://www.hostinger.com.br/tutoriais/comandos-linux
- https://www.hostinger.com.br/tutoriais/o-que-e-cli/
- https://www.linuxdescomplicado.com.br/2016/09/muito-alem-do-kernel-conheca-todos-os-elementos-que-formam-a-estrutura-do-sistema-linux.html
- https://www.youtube.com/watch?v=epiyExCyb2s
- https://www.youtube.com/watch?v=mgs92GtkQCE&list=PLHz_AreHm4dlIXleu20uwPWFOSswqLYbV&index=10