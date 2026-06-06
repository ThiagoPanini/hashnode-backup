---
title: "Escrita de Fontes Externas com DataFrameWriter"
datePublished: 2022-07-20T15:35:47.591Z
cuid: cl5tro17702wtkcnvcgoi7lno
slug: escrita-de-fontes-externas-com-dataframewriter
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1658277329756/UOgLFptcR.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1658277357846/DMQDVn1JD.png
tags: tutorial, spark, learning, beginners, apache-spark

---

Olá, caro leitor! Seja muito bem vindo a mais um post desta [série sobre o Apache Spark](https://panini.hashnode.dev/series/spark)! Após um mergulho direto em algumas explorações práticas envolvendo a leitura de fontes externas através da classe `DataFrameReader` e seu vasto leque de opções, é chegado o momento de analisar o outro lado da moeda e detalhar processos de escrita de dados.

Neste cenário, é importante citar que, assim como existe uma classe dedicada e de alto nível para leitura dos dados em Spark, também há uma construção análoga utilizada para processos de escrita: trata-se da classe `DataFrameWriter` com seu conjunto específico de opções a serem exploradas ao longo deste artigo.

Para uma experiência completa nos assuntos aqui abordados, especialmente os exemplos práticos a serem fornecidos, a leitura do [artigo anterior](https://hashnode.com/edit/cl5r19kwo00kpscnvd3nc5mwh) sobre a leitura de dados no Spark é altamente recomendada! Alguns elementos prévios de código, como a obtenção dos dados e a configuração de uma sessão Spark com variáveis definidas para leitura local de arquivos, estão devidamente demonstrados no artigo citado e serão utilizados em caráter de continuidade no artigo atual.

Embarque nesta jornada para a conclusão de um importante ciclo de aprendizado envolvendo não só a leitura, mas também a escrita de dados através do Spark!

___

## Um pouco de teoria: a classe DataFrameWriter

Como bem introduzido, o Spark utiliza a classe `DataFrameWriter` para escrita de fontes externas de dados. De maneira geral, uma versão simplificada da sintaxe utilizada pode ser visualizada abaixo:

```python
DataFrameWriter.format(args).mode(args).option("key", "value").bucketBy(args).partitionBy(*cols).save(path)
```
Por mais que o funcionamento da classe para escrita dos dados seja semelhante à sua versão para leitura, existem algumas particularidades envolvendo a persistência dos dados e que podem ser notadas em sua própria sintaxe. De modo a esclarecer estes pontos, a tabela abaixo traz uma visão geral sobre as características da classe:

| Bloco de código | Descrição | Exemplo |
| :---: | :---: | :---: |
| `.format(args)` | Assim como na leitura dos dados, este bloco de código é utilizado para definir o formato do arquivo de saída, seja ele CSV, JSON, Parquet ou qualquer outro disponível | `.format("parquet")` |
| `.mode(args)` | Este bloco define o modo de escrita dos arquivos e pode ser alimentado com os seguintes argumentos: "append;overwrite;error;ignore". Na prática, o modo de salvamento dos arquivos determina o comportamento do Spark caso a saída já exista, podendo empilhar os dados (append), sobrescrever (overwrite), gerar um erro (error) ou simplesmente ignorar o comando (ignore) | `.mode("append")` |
| `.option("key", "value")` | Este bloco possui um comportamento análogo à sua versão na classe `DataFrameReader`. Dependendo do formato de saída, uma série de configurações podem ser implementadas para determinar características da fonte exportada | `.option("header", "true")` |
| `.bucketBy(args)` | Determina uma coluna para aplicação do processo de *bucketing* nos dados | `.bucketBy(128, "cpf_cnpj")` |
| `.partitionBy(*cols)` | Define as colunas de particionamento a serem consideradas no ato de escrita dos dados. O conceito de particionamento segue a mesma lógica presente em outras ferramentas de Big Data, como Hadoop e Hive | `.partitionBy("anomes")` |
| `.save(path)` | Assim como o bloco `.load(path)` atua na classe de leitura, o bloco `.save(path)` define a saída dos dados a serem persistidos | `.save("output/file.parquet")` |

Existe ainda uma série de outros métodos e configurações não abordadas na tabela acima, mas que podem ser consultadas através da [documentação oficial da classe](https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.DataFrameWriter.html). De maneira geral, sempre que existir a necessidade de construir um fluxo de trabalho que envolva a escrita dos dados, é importante consultar todas as opções e configurações possíveis para construir o código de acordo com os comportamentos desejados.

___

## Mãos à obra: exemplos de escrita de dados

Após uma breve passagem teórica, a principal premissa para navegar em exemplos práticos de escrita de dados é simplesmente a existência de um DataFrame lido em memória.

Em linha com a proposta definida para este artigo, os subtópicos a serem consolidados em sequência terão, como principal objetivo, fornecer um amplo leque de cenários que eventualmente poderão ser encontrados em situações reais de trabalho.

### Escrevendo em diferentes formatos

Como forma de inaugurar os exemplos de escrita de dados, o bloco de código abaixo considera a leitura prévia de um arquivo CSV armazenado na variável `df_csv` que, por sua vez, representa um objeto do tipo DataFrame. Em caso de dúvidas sobre como este objeto/variável foi originado, vale o reforço na recomendação de leitura do [artigo sobre a classe DataFrameReader](https://panini.hashnode.dev/leitura-de-fontes-externas-com-dataframereader). O comando abaixo realiza a escrita deste objeto em um formato JSON no mesmo diretório de execução do Jupyter Notebook:

```python
# Escrevendo DataFrame em formato JSON
df_csv.write.format("json").mode("overwrite").save('output/flights_json')
```

Algumas considerações importantes a serem destacadas neste momento:

- O bloco `.format()` atua da mesma forma demonstrada nos exemplos de leitura de arquivos e é ele quem define o formato final de saída do DataFrame a ser persistido
- O bloco `.mode()` define o modo de persistência do arquivo e, no caso do exemplo fornecido, qualquer existência prévia encontrada na referência de caminho fornecida será **sobrescrita** pelo Spark
- O bloco `.save()` determina o local de escrita do arquivo e, normalmente, o argumento passado é um **diretório** e não o nome final do arquivo. Na prática, o Spark cria uma pasta e salva o conteúdo do DataFrame alvo além de alguns arquivos de controle do *job* utilizado

Assim, para escrever arquivos em outros formatos utilizando o Spark sem configurações adicionais, basta repetir o mesmo comando alterando o argumento passado para o bloco `.format()`. Abaixo, será possível visualizar mais alguns exemplos:

```python
# Escrevendo DataFrame em formato CSV
df_csv.write.format("csv").mode("overwrite").save('output/flights_csv')

# Escrevendo DataFrame em formato ORC
df_csv.write.format("orc").mode("overwrite").save('output/flights_orc')

# Escrevendo DataFrame em formato PARQUET
df_csv.write.format("parquet").mode("overwrite").save('output/flights_parquet')
```

Após a execução dos códigos, é esperada a existência de quatro diretórios representando, cada um, o *output* do *job* Spark utilizado para escrita dos arquivos nos diferentes formatos demonstrados.

```bash
output/
├── flights_csv
│   ├── part-00000-35e92b3e-2fbe-446c-b4dd-215e0e73caf7-c000.csv
│   ├── .part-00000-35e92b3e-2fbe-446c-b4dd-215e0e73caf7-c000.csv.crc
│   ├── _SUCCESS
│   └── ._SUCCESS.crc
├── flights_json
│   ├── part-00000-2c01969a-eede-4537-b9da-a0988602436a-c000.json
│   ├── .part-00000-2c01969a-eede-4537-b9da-a0988602436a-c000.json.crc
│   ├── _SUCCESS
│   └── ._SUCCESS.crc
├── flights_orc
│   ├── part-00000-c7ad63ea-c363-4f57-a6b7-129cf5bcf38a-c000.snappy.orc
│   ├── .part-00000-c7ad63ea-c363-4f57-a6b7-129cf5bcf38a-c000.snappy.orc.crc
│   ├── _SUCCESS
│   └── ._SUCCESS.crc
└── flights_parquet
    ├── part-00000-3e59c676-8a30-4f07-bb3f-586a086bc79e-c000.snappy.parquet
    ├── .part-00000-3e59c676-8a30-4f07-bb3f-586a086bc79e-c000.snappy.parquet.crc
    ├── _SUCCESS
    └── ._SUCCESS.crc
```

___

### Escrevendo base particionada em PARQUET

Considerando a demonstração de exemplos que podem facilmente serem encontrados e aplicados no mundo real, o código abaixo demonstra a utilização da classe `DataFrameWriter` para escrita de um DataFrame no formato PARQUET utilizando uma coluna de partição.

```python
# Salvando base particionada no formato PARQUET
df_csv.write.format("parquet")\
    .mode("append")\
    .partitionBy("DEST_COUNTRY_NAME")\
    .save("output/flights_parquet_partitioned")
```

A principal diferença do comando acima exemplificado para os comandos demonstrados anteriormente está na utilização do bloco `.partitionBy()`. Com ele, é possível definir uma coluna de partição da base de dados para que a persistência dos arquivos físicos sejam feitas de acordo com o conteúdo da coluna. Assim, espera-se que o resultado seja composto não apenas por um único arquivo PARQUET, mas sim múltiplos arquivos posicionados em diferentes diretórios, cada qual representando uma entrada distinta da coluna utilizada para o particionamento.

```bash
flights_parquet_partitioned
├── DEST_COUNTRY_NAME=Algeria
│   ├── part-00000-679e69e0-41c2-4989-9b8d-26a719e13be8.c000.snappy.parquet
│   └── .part-00000-679e69e0-41c2-4989-9b8d-26a719e13be8.c000.snappy.parquet.crc
├── DEST_COUNTRY_NAME=Angola
│   ├── part-00000-679e69e0-41c2-4989-9b8d-26a719e13be8.c000.snappy.parquet
│   └── .part-00000-679e69e0-41c2-4989-9b8d-26a719e13be8.c000.snappy.parquet.crc
├── DEST_COUNTRY_NAME=Anguilla
│   ├── part-00000-679e69e0-41c2-4989-9b8d-26a719e13be8.c000.snappy.parquet
│   └── .part-00000-679e69e0-41c2-4989-9b8d-26a719e13be8.c000.snappy.parquet.crc
├── DEST_COUNTRY_NAME=Antigua and Barbuda
│   ├── part-00000-679e69e0-41c2-4989-9b8d-26a719e13be8.c000.snappy.parquet
│   └── .part-00000-679e69e0-41c2-4989-9b8d-26a719e13be8.c000.snappy.parquet.crc
├── DEST_COUNTRY_NAME=Argentina
│   ├── part-00000-679e69e0-41c2-4989-9b8d-26a719e13be8.c000.snappy.parquet
│   └── .part-00000-679e69e0-41c2-4989-9b8d-26a719e13be8.c000.snappy.parquet.crc
├── DEST_COUNTRY_NAME=Aruba
│   ├── part-00000-679e69e0-41c2-4989-9b8d-26a719e13be8.c000.snappy.parquet
│   └── .part-00000-679e69e0-41c2-4989-9b8d-26a719e13be8.c000.snappy.parquet.crc
├── DEST_COUNTRY_NAME=Australia
│   ├── part-00000-679e69e0-41c2-4989-9b8d-26a719e13be8.c000.snappy.parquet
│   └── .part-00000-679e69e0-41c2-4989-9b8d-26a719e13be8.c000.snappy.parquet.crc
...
```

Observando o resultado parcial acima, é possível notar que o comando de escrita gerou novos diretórios para cada entrada distinta presente na coluna `DEST_COUNTRY_NAME` e, em cada um deles, um arquivo PARQUET foi escrito. Assim, pode-se dizer que o particionamento foi realizado com sucesso.

Para os familiarizados com o ecossistema Hadoop, o particionamento acima demonstrado é análogo ao processo de [partições dinâmicas](https://www.geeksforgeeks.org/overview-of-dynamic-partition-in-hive/) encontrado no Apache Hive.

___

### Criando tabelas temporárias (SparkSQL)

Por fim, o último cenário de demonstração a ser considerado neste artigo envolve uma atuação altamente relevante no contexto de uso do Spark puramente via linguagem SQL. Para este tipo de caso, o bloco `saveAsTable(table_name)` se faz presente em substituição ao bloco `save(path)`, indicando assim a criação de uma "view" (ou tabela temporária) no Spark que pode ser posteriormente consultada através de linguagem SQL via SparkSQL.

Na prática, o bloco de código abaixo utiliza o DataFrame `df_csv` para criação de uma tabela temporária chamada `tbl_flights`:

```python
# Escrevendo DataFrame em tabela temporária no Spark
df_csv.write.mode("overwrite").saveAsTable("tbl_flights")
```

Uma vez criada, a tabela pode então ser consultada utilizando SparkSQL:

```python
# Executando consulta nesta tabela
df_csv_sql = spark.sql("""
    SELECT * FROM tbl_flights LIMIT 5
""")
df_csv_sql.show()
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1658331026908/JFcCJKo92.png align="left")

Trabalhar com SparkSQL é realmente algo mágico e extremamente gratificante. Por mais que uma abordagem inicial tenha sido dada nos exemplos acima, existe a intenção em escrever um artigo específico sobre o tema com uma série de detalhes adicionais envolvendo sintaxe, DAGs e toda a atuação do Spark em utilizar SQL.

___

## Conclusão e encerramento

Conhecer os processos de leitura e escrita de dados a partir das APIs estruturadas do Spark é algo fundamental dentro da jornada de utilização desta ferramenta para os mais variados fluxos de dados. Obter dados em um formato que pode ser posteriormente trabalhado dentro da lógica de transformação do Spark é, por muitas vezes, o primeiro passo de qualquer *pipeline* no universo de dados. Configurar a saída deste fluxo em um formato adequado para os consumidores é de tal forma importante.

Com os ensinamentos adquiridos nos dois últimos artigos, é possível afirmar que um passo extremamente relevante foi dado e, dessa forma, cada vez mais nos permitimos dizer que o conhecimento em Spark vem tomando forma.

Espero que tenham aproveitado esta jornada! Muito mais está por vir! Até a próxima!

___

## Referências

- [Spark: The Definitive Guide](https://www.amazon.com.br/Spark-Definitive-Guide-Bill-Chambers/dp/1491912219/ref=asc_df_1491912219/?tag=googleshopp00-20&linkCode=df0&hvadid=379733272930&hvpos=&hvnetw=g&hvrand=9219814726222784669&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=1001767&hvtargid=pla-318947193480&psc=1)
- [Learning Spark - Lightning-Fast Data Analytics](https://www.amazon.com.br/Learning-Spark-2e-Jules-Damji/dp/1492050040/ref=asc_df_1492050040/?tag=googleshopp00-20&linkCode=df0&hvadid=379795170134&hvpos=&hvnetw=g&hvrand=7989558043694463297&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=1001767&hvtargid=pla-918087322526&psc=1)