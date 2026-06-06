---
title: "O Hadoop em um Contexto Histórico"
datePublished: 2022-04-13T21:29:36.216Z
cuid: cl1y35jvu01gnklnvectgcal6
slug: o-hadoop-em-um-contexto-historico
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1649885293641/Obw-3D938.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1649885358678/PeUaGpnW1.png
tags: hadoop, big-data, distributed-system, history

---

No [primeiro artigo](https://panini.hashnode.dev/paradigmas-de-big-data-na-era-moderna) desta promissora série sobre o Ecossistema Hadoop, foram apresentados conceitos fundamentais sobre Big Data e os desafios relacionados ao armazenamento e processamento de grandes quantidades de dados na era moderna.

De forma introdutória, o artigo inicial trouxe alguns termos e elementos do Hadoop como soluções para os mais variados obstáculos que assolavam a comunidade de tecnologia. Nos dias atuais, sabe-se que a implementação e a difusão do Hadoop pode ser considerada como um marco histórico fundamental para a solução de problemas do Big Data. Entretanto, até que este estado pudesse ser alcançado, muita coisa aconteceu. 

Assim, este artigo tem um forte pilar teórico baseado no excelente (e quase obrigatório para entusiastas) livro [*Hadoop: The Definitive Guide*](https://www.amazon.com/Hadoop-Definitive-Storage-Analysis-Internet/dp/1491901632) de Thom White, um célebre desenvolvedor e contribuinte da comunidade Hadoop que alcançou um papel fundamental de transformação na forma com que estudantes e aprendizes entendem o Hadoop.

___

## O Hadoop como é conhecido atualmente

Em uma definição formal, o [site oficial](https://hadoop.apache.org/) da Apache elucida que:

> A biblioteca de software Apache Hadoop é um *framework* que permite processamento distribuído de grandes quantidades de dados ao longo de *clusters* de computadores utilizando simples modelos de programação. Sua arquitetura comporta uma alta escalabilidade, permeando desde servidores individuais até milhares de máquinas, cada uma oferecendo armazenamento e poder computacional local.

Esta definição foi coletada na data de publicação deste artigo. Nos dias atuais, é assim que novos desenvolvedores e entusiastas são apresentados oficialmente ao Apache Hadoop. Entretanto, muitos foram os caminhos até que as transformações deste sistema capaz de solucionar os principais problemas de Big Data pudesse ser conhecido como é hoje.

___

## Um breve histórico sobre o Hadoop

Para compreender o surgimento do Hadoop, é importante iniciar este contexto histórico mencionando que os primeiros passos do *framework* hoje mundialmente adotado não foram, de fato, dados em uma escala global. Tampouco seu nome, no início, é como conhecido atualmente.

Em meados de 2002, [Doug Cutting](https://en.wikipedia.org/wiki/Doug_Cutting) e [Mike Cafarella](https://en.wikipedia.org/wiki/Mike_Cafarella) iniciaram o [Nutch](https://en.wikipedia.org/wiki/Apache_Nutch): um motor de busca *open source* parte do projeto [Lucene](https://en.wikipedia.org/wiki/Apache_Lucene). 

![img01-nutch-logo.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649528945611/QjJlsbJ4q.png)

No contexto da época, construir um motor de busca web era uma tarefa computacionalmente e financeiramente ambiciosa. Mesmo que os componentes de *crawler* e o sistema de pesquisa do Nutch tenham sido desenvolvidos em um curto espaço de tempo, Doug e Mike notaram que a arquitetura do projeto não poderia lidar com os bilhões de páginas da web. O primeiro grande obstáculo estava lançado.

Foi neste ponto que, em 2003, um *paper* lançado pela Google demonstrou detalhes do sistema de armazenamento distribuído utilizado na empresa e serviu de grande inspiração para os futuros desenvolvedores do Hadoop. A proposta, nomeada GFS (*Google Filesystem*), solucionava os mais variados problemas de armazenamento para grandes quantidades de dados como parte dos processos de *crawling* e indexação de motores de busca.

E assim, em 2004, os desenvolvedores do Nutch implementaram sua própria ferramenta *open source* para o armazenamento distribuído de acordo com os propósitos estabelecidos no projeto. Nascia então o *Nutch Distributed Filesystem*, ou NDFS. No mesmo ano, a Google apresentava o MapReduce ao mundo e, pouco tempo depois, o Nutch contava com as ferramentas essenciais para solucionar problemas de armazenamento e processamento de dados antes considerados complexos: o NDFS e o MapReduce.

Neste ponto da história, os conceitos de armazenamento e processamento distribuído já haviam sido lançados. Os poderes e capacidades gerados através dessa união forneceram uma visão holística de que muita coisa poderia ser construída além de motores de busca. Dessa forma, em 2006, Doug Cutting criou um projeto independente intitulado Hadoop, cujo nome foi explicado pelo próprio criador como:

> "Hadoop é o nome no qual meu filho deu a seu elefante amarelo de pelúcia. Um nome pequeno, relativamente fácil de pronunciar, sem significado algum e não utilizado em nenhum lugar: estes certamente são meus critérios de nomeação. Crianças são boas em gerar estes termos. Googol é um termo de criança."

![img02-hadoop-elephant.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1649530222081/ebBLzbChb.jpg)

Pouco tempo depois da oficialização do Hadoop, Doug Cutting foi convidado a fazer parte do Yahoo! e, em 2008, a empresa anunciou que os índices de busca de seu sistema haviam sido gerados por um *cluster* Hadoop de 10.000 *cores*. Neste mesmo ano, o Hadoop tornou-se um projeto homônimo na Apache Software Foundation, confirmando o sucesso a adoção por toda a comunidade de tecnologia.

A partir de então, o Hadoop vem sendo utilizado por um gigantesco leque de usuários, desde entusiastas, até grandes companhias. Sendo uma ferramenta nativamente *open source*, qualquer um pode implementar seu próprio *cluster* de computadores com base no *framework* Hadoop. Por outro lado, soluções comerciais também são disponibilizadas por grandes empresas como AWS, IBM, Microsoft, Oracle e Cloudera.

O ecossistema Hadoop foi crescendo em tamanho, adoção e maturidade. Atualmente, componentes fundamentais compõem este leque de soluções para os mais variados problemas do universo de Big Data, incluindo ferramentas capazes de executar jobs de MapReduce como queries SQL (Apache Hive e Apache Impala), ferramentas para processamento de *streaming* de dados (Apache Spark e Apache Storm), ferramentas para transferência de dados entre bancos relacionais e sistemas distribuídos (Sqoop), entre outras.

![img02-hadoop-logo.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1649530846499/HOvMVkFWN.png)

___

## Considerações Finais

É virtualmente impossível desconsiderar o Hadoop como uma das grandes ferramentas desenvolvidas

Em 2016, o Hadoop completou 10 anos e o [artigo](https://www.informationweek.com/software-platforms/hadoop-at-10-doug-cutting-on-making-big-data-work) escrito por William Terdoslavich para o portal InformationWeek traz alguns desafios históricos enfrentados pelos criadores, incluindo um vídeo sensacional de Doug Cutting contando, com suas palavras, sua visão sobre o Hadoop no passado, presente e futuro. Vale a pena ver!

%[https://www.youtube.com/watch?time_continue=139&v=XHz_R33QnsI&feature=emb_title]

Espero que tenham gostado desta contextualização histórica do Hadoop. Fiquem ligados para os próximos post desta série!

___

## Referências

- https://www.amazon.com/Hadoop-Definitive-Storage-Analysis-Internet/dp/1491901632
- https://hadoop.apache.org/
- https://en.wikipedia.org/wiki/Doug_Cutting
- https://en.wikipedia.org/wiki/Mike_Cafarella
- https://en.wikipedia.org/wiki/Apache_Lucene
- https://en.wikipedia.org/wiki/Apache_Nutch
- https://www.informationweek.com/software-platforms/hadoop-at-10-doug-cutting-on-making-big-data-work
- https://www.youtube.com/watch?time_continue=139&v=XHz_R33QnsI&feature=emb_title