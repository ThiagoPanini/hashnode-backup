---
title: "Agregações e Agrupamentos de Dados"
datePublished: 2022-08-12T01:50:30.989Z
cuid: cl6ptbbcu02mygenv8yfihi72
slug: agregacoes-e-agrupamentos-de-dados
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1660268994159/9JV9BG62-.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1660268975933/brzET3sUv.png
tags: tutorial, big-data, spark, learning, beginners

---

Olá, caro leitor! Seja muito bem vindo a mais um post desta [série sobre o Apache Spark](https://panini.hashnode.dev/series/spark)! No momento atual da jornada de aprendizado, uma série de funções e métodos já foram apresentados aos leitores como elementos capazes de serem aplicados nos mais variados fluxos de transformação. Para adicionar ainda mais capacidade técnica e autonomia aos entusiastas do Spark, este artigo possui, como principal objetivo, demonstrar alguns métodos comumente aplicados para computar diferentes cálculos estatísticos e agregações.

Adicionalmente, o tipo `RelationalGroupedDataset` será apresentado como um elemento resultante de processos de agrupamento no qual as funções de agregações podem ser aplicadas, aumentando ainda mais o leque de possibilidades analíticas com o Spark.

Quer compreender como realizar agregações, agrupamentos, aplicar funções estatísticas e extrair análises específicas de conjuntos de dados no Spark? Embarque nessa jornada!

___

## Dados para exploração

Visando proporcionar uma nova experiência aos leitores, a proposta para este artigo gira em torno da utilização de uma base de dados inédita. Considerando obter um maior número de possibilidades, os exemplos práticos a serem consolidados serão aplicados em uma base de dados retirada a partir da **leitura de sensores IoT** posicionados em fábricas ao redor do mundo. 

Presente originalmente no [repositório oficial do livro Learning Spark](https://github.com/databricks/LearningSparkV2/tree/master/databricks-datasets/learning-spark-v2/iot-devices), os dados de sensores IoT são disponibilizados no formato JSON e possuem a seguinte característica:

```python
# Lendo dados
df_iot = spark.read.format("json")\
    .schema(iot_schema).load(iot_path)

# Criando tabelas temporárias
df_iot.createOrReplaceTempView("tbl_iot")

# Visualizando dados
df_iot.printSchema()
df_iot.show(5)
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660262448058/sXIXm0iGA.png align="left")

___

## Funções de Agregação

Para iniciar os detalhes práticos prometidos na seção de introdução, é importante pontuar que as operações a serem demonstradas refletem basicamente funções importadas do módulo `pyspark.sql.functions` e que serão aplicadas dentro de consultas a DataFrames a partir dos métodos `select()` ou `selectExpr()`. A partir deste ponto, uma avalanche de novos elementos estatísticos farão parte do leque de conhecimentos adquiridos!

### count

De modo simplório, o primeiro exemplo prático fornecido envolve a contagem de elementos de um DataFrame através da função `count`. O bloco de código abaixo pode ser utilizado para contabilizar as leituras realizadas pelos sensores:

```python
# Importando função
from pyspark.sql.functions import count

# Contando leituras realizadas
df_iot.select(
    count("device_id")
).show()
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660262769144/3w4Pu6AV1.png align="left")

___

### countDistinct

Em alguns cenários, pode ser necessário realizar uma contagem de elementos distintos presentes em um determinado atributo de uma base de dados. Dessa forma, a função `countDistinct` se faz presente e pode ser aplicada, no contexto da fonte de dados utilizada, para contabilizar a quantidade distinta de países onde os sensores de medição foram posicionados. A coluna que representa o país origem da medição é dada pela referência `cca3`:

```python
# Importando função
from pyspark.sql.functions import countDistinct

# Contabilizando países distintos
df_iot.select(
    countDistinct("cca3")
).show()
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660263020855/0hq7Mkiar.png align="left")

___

### first e last

Eventualmente, é possível obter a primeira e última linha de um DataFrame através das funções `first` e `last`, respectivamente. No contexto dos dados utilizados, a aplicação prática envolveria a obtenção da primeira e última medição de temperatura realizada pelos dispositivos:

```python
# Importando funções
from pyspark.sql.functions import first, last

# Obtendo primeira e última medição de temperatura
df_iot.select(
    first("temp").alias("primeira_temperatura"),
    last("temp").alias("ultima_temperatura")
).show()
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660263268370/En-Tm9rC0.png align="left")

___

### min e max

Considerando a possibilidade de extrair os extremos de uma dada informação com base em seu valor numérico, as funções `min` e `max` auxiliam, de maneira altamente intuitiva, na obtenção dos valores mínimo e máximo de um atributo contínuo de um DataFrame. Considerando a base de dados utilizada, ambas as funções poderiam ser aplicadas em conjunto para obter o pico e o vale de temperatura obtida no histórico de medições. Um filtro de escala foi adicionado na consulta para evitar que uma comparação indevida de valores de temperatura seja realizada:

```python
# Importando funções
from pyspark.sql.functions import min, max

# Obtendo mínimo e máximo de temperatura
df_iot.where(col("scale") == "Celsius")\
    .select(
        min("temp").alias("min_temp"),
        max("temp").alias("max_temp")
    ).show()
```

___

### sum

A soma é uma função agregadora bastante comum em uma série de aplicações práticas de análise de dados. Imaginando sua utilização na base de sensores IoT, seria possível obter a somatória total de gás carbônico lida pelos sensores nas fábricas:

```python
# Importando função
from pyspark.sql.functions import sum

# Soma total de nível de gás carbônico
df_iot.select(
    sum("c02_level")
).show()
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660263720851/tlIRo-GK6.png align="left")

___

### avg

Assim como a soma, a média também é uma função agregadora com papel extremamente representativo em análises reais de dados. Apesar de seu cálculo estar baseado na divisão entre soma e quantidade (`sum` / `count`), a utilização da função `avg` vai direto ao ponto. No contexto dos dados, seria possível aplicar tal função para a obter a umidade média medida pelos sensores:

```python
# Importando função
from pyspark.sql.functions import avg

# Obtendo a umidade média da base
df_iot.select(
    avg("humidity")
).show()
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660263907169/7ImAsVldp.png align="left")

___

### var e stddev

Aprofundando ainda mais na dinâmica estatística das análises fornecidas, a variância e o desvio padrão podem ser utilizadas de maneira isolada ou em conjunto para responder algumas questões específicas sobre o modelo de dados utilizado. Na prática, existe uma separação entre a aplicação das funções citadas em uma **população** ou em uma **amostra** e isto pode ser devidamente gerenciado pelas funções com sufixo `_pop` e `_samp`:

```python
# Importando funções
from pyspark.sql.functions import var_pop, var_samp, \
    stddev_pop, stddev_samp

# Obtendo variância e desvio padrão de gás carbônico
df_iot.select(
    var_pop("c02_level").alias("var_pop_co2"),
    var_samp("c02_level").alias("var_samp_co2"),
    stddev_pop("c02_level").alias("stddev_pop_co2"),
    stddev_samp("c02_level").alias("stddev_samp_co2")
).show()
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660264208301/mDXkB5h2j.png align="left")

___

### Outras funções e formas de agregação

Existem, ainda, uma infindade de funções de agregação que podem ser utilizadas em fluxos de trabalho no Spark. *Skewness*, *kurtosis*, covariância e correlação são apenas mais alguns exemplos que seguem a mesma lógica de aplicação demonstrada anteriormente para todas as demais funções. Além disso, o Spark oferece funções capazes de agregar dados para tipos complexos, como o caso de `collect_set()` e `collect_list()`.

A mensagem a ser passada neste momento é que, independente da necessidade de transformação de dados em um fluxo produtivo de trabalho, fatalmente opções de alto nível no Spark estarão disponíveis ao usuário.

___

## Agrupamento

Na prática, a utilização de funções de agregação, de maneira isolada, contribuem apenas para análises ad-hoc e específicas onde existem necessidades especiais para visualizar pontualmente um valor de uma base de dados.

Considerando a expansão deste processo para a construção de bases agregadas de acordo com um contexto específico, a utilização de métodos de agrupamento permite avançar um nível a mais no processo analítico de dados.

Em essência, a geração de DataFrames agregados em Spark é realizada através da seguinte dinâmica:

1. Primeiro, são especificadas as colunas (ou a coluna) alvo do processo de agregação, gerando assim um objeto do tipo `RelationalGroupedDataset`
2. Na sequência, são aplicadas as funções de agregação, retornando assim um novo objeto do tipo `DataFrame`

No exemplo abaixo, um bloco de código será estruturado para retornar os países com maior média de temperatura mensurada:

```python
# Importando função
from pyspark.sql.functions import desc

# Retornando os países com maior média de temperatura
df_high_temp = df_iot\
    .groupBy("cca3")\
    .avg("temp")\
    .orderBy(desc("avg(temp)"))

# Visualizando resultado
df_high_temp.show(10)
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660265240672/qWMexW58o.png align="left")

Entretanto, na dinâmica acima exemplificada, existe uma limitação sobre o uso de diferentes funções de agregação em diferentes colunas da base de dados. Em outras palavras, seria impossível calcular a média de temperatura e os valores máximo e mínimo de umidade por país. 

Como em Spark quase tudo é possível, o cenário acima poderia ser facilmente codificado através da utilização do método `agg()` da seguinte forma:

```python
# Coletando temperatura média e picos de umidade por país
df_iot\
    .groupBy("cca3").agg(
        count("device_name").alias("qtd_medicoes"),
        avg("temp").alias("temperatura_media"),
        max("humidity").alias("max_humid"),
        min("humidity").alias("min_humid")
    ).orderBy(desc("max_humid")).show(10)
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660265671317/JisdwHC6x.png align="left")

Além de tudo, expressões em Spark também poderiam ser utilizadas para obter resultados idênticos:

```python
# Agrupando por país e lcd
df_iot.groupby("cn", "lcd").agg(
    expr("count(1) AS qtd_medicoes"),
    expr("round(avg(c02_level), 1) AS co2_medio"),
    expr("round(stddev_pop(battery_level), 1) AS stddev_battery"),
    expr("round(max(temp), 1) AS max_temp"),
    expr("round(min(temp), 1) AS min_temp"),
).orderBy(desc("qtd_medicoes")).show(10, truncate=False)
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660266077806/c73d3RfTM.png align="left")

___

## Conclusão e encerramento

Adicionar possibilidades de agregação e agrupamento em *pipelines* de transformação de dados é um ganho extremamente valioso dentro dos objetivos de aprendizado no ramo do Spark. No presente artigo, vimos como as funções de agregação podem ser utilizadas em conjunto com os métodos `groupBy()` e `agg()` para construir as mais variadas análises dentro das necessidades existentes.

Adicionalmente, todos os métodos já abordados até aqui podem ser utilizados em conjunto para a criação de planos de transformações cada vez mais ricos em detalhes. Com isto em mente, nos aproximamos aos poucos de um nível de conhecimento suficientemente rico a ponto de nos proporcionar a autonomia necessária para a construção de fluxos de trabalho complexos.

Foi ótimo ter você aqui, caro leitor! Até a próxima!

___

## Referências

- [Spark: The Definitive Guide](https://www.amazon.com.br/Spark-Definitive-Guide-Bill-Chambers/dp/1491912219/ref=asc_df_1491912219/?tag=googleshopp00-20&linkCode=df0&hvadid=379733272930&hvpos=&hvnetw=g&hvrand=9219814726222784669&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=1001767&hvtargid=pla-318947193480&psc=1)
- [Learning Spark - Lightning-Fast Data Analytics](https://www.amazon.com.br/Learning-Spark-2e-Jules-Damji/dp/1492050040/ref=asc_df_1492050040/?tag=googleshopp00-20&linkCode=df0&hvadid=379795170134&hvpos=&hvnetw=g&hvrand=7989558043694463297&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=1001767&hvtargid=pla-918087322526&psc=1)