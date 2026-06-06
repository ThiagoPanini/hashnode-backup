---
title: "Orquestrando Glue Jobs com Step Functions "
slug: orquestrando-glue-jobs-com-step-functions

---

Olá, caro leitor! Seja muito bem vindo ao primeiro artigo da série **AWS Labs**, onde abordaremos cenários práticos e soluções reais utilizando serviços AWS. Após apresentar oficialmente a iniciativa no artigo de boas vindas (link), podemos finalmente iniciar nossa jornada de aprendizado.

Para isso, um tema especialmente prazeroso foi selecionado e, ao longo deste artigo, iremos acompanhar a jornada de um aprendiz em serviços AWS responsável por construir um fluxo encadeado de processamento de dados

Garantindo uma visão geral sobre os objetivos traçados e as maneiras de alcança-los neste artigo, a tabela abaixo traz um resumo efetivo da proposta:

| 🎯 **Objetivo** | Orquestrar múltiplos jobs de processamento de dados |
| --- | --- |
| ☁️ **Serviços Principais** | Glue e Step Functions |
| 🌧️ **Serviços Auxiliares** | S3, IAM, KMS e Eventbridge |
| ⚙️ **Ferramentas** | datadelivery, terraglue, sparksnake, Apache Spark, cron |
| 🎲 **Dados** | Brazilian E-Commerce |

Sem mais spoilers, vamos ao artigo!

## Introdução e Contexto

Para garantir uma verdadeira imersão na problemática que tange a temática do artigo, vamos apresentar um cenário prático e introduzir as ferramentas utilizadas para alcançarmos os objetivos estabelecidos.

### Cenário

> Você trabalha na área de Analytics de uma das maiores empresas de vendas online do mercado. Em um dado momento da cadeia transacional desta empresa, dados brutos são disponibilizados em um formato próximo ao de um star schema (fatos e dimensões), permitindo armazenar informações específicas e detalhadas sobre todos os pedidos realizados na plataforma, bem como informações complementares sobre os itens de cada pedido, produtos, formas de pagamento, reviews, vendedores e compradores.
> 
> O grande número de tabelas existentes (8 ao todo) atrelado à recorrente necessidade de realização de processos de join para análises pontuais fez com que sua área fosse acionada para proporcionar uma visão desnormalizada de todas as tabelas deste star schema, permitindo assim que os consumidores possam realizar análises refinadas e extrair insights sobre as vendas online de uma forma muito mais amigável através de uma ou duas tabelas especializadas.

**Disclaimer importante:** neste momento, é fundamental pontuar que o cenário acima proposto poderia ser solucionado de uma infinidade de formas diferentes. Muitas outras variáveis poderiam se fazer presente para balizar a escolha dos serviços AWS utilizados na solução.

### Ferramentas e Serviços

Visando proporcionar uma solução cristalina para a problemática acima exemplificada considerando, de forma estratégica, a temática do artigo, os serviços utilizados podem ser divididos em três grandes tópicos:

* **Serviços principais,** servindo como o coração da solução proposta.:
    
    * [Glue](https://aws.amazon.com/glue/) para o processamento de dados
        
    * [Step Functions](https://aws.amazon.com/step-functions/) para orquestração dos jobs de processamento
        
* **Serviços auxiliares:** atuam de modo complementar aos serviços principais:
    
    * [IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) para gerenciamento das permissões necessárias
        
    * [S3](https://aws.amazon.com/s3/) para o armazenamento de dados
        
    * [Glue Data Catalog](https://docs.aws.amazon.com/glue/latest/dg/catalog-and-crawler.html) para catalogação dos metadados e disponibilização de tabelas
        
    * [Athena](https://aws.amazon.com/athena/) para realização de consultas em tabelas catalogadas
        
    * [KMS](https://aws.amazon.com/kms/) para criptografia dos dados e dos logs
        
    * [CloudWatch](https://aws.amazon.com/cloudwatch/) para armazenamento e análise de logs
        
    * [Eventbridge](https://aws.amazon.com/eventbridge/) para agendamento de fluxos
        
* **Ferramentas open source:** ferramentas que contribuem para que a solução seja reprodutível em qualquer ambiente:
    
    * [Terraform](https://www.terraform.io/) para implantação de toda a infrastrutura da solução através de código
        
    * ⭐ [datadelivery](https://datadelivery.readthedocs.io/en/latest/) para criação das estruturas de buckets, inserção e catalogação dos dados utilizando Terraform
        
    * ⭐ [terraglue](https://terraglue.readthedocs.io/en/latest/) para criação de um job Glue pré configurado utilizando Terraform
        
    * [Apache Spark](https://spark.apache.org/) para servir como o principal motor de processamento de dados nos jobs de ETL
        
    * ⭐ [sparksnake](https://sparksnake.readthedocs.io/en/latest/) para facilitar o desenvolvimento das aplicações Spark a serem submetidas como jobs do Glue na AWS
        

Temos elementos extremamente interessantes nessa proposta de artigo, não é mesmo: Caso tenham curiosidades adicionais sobre o funcionamento de alguma das ferramentas acima, acessem os links disponibilizados e se divirtam estudando. Vale a pena.

### Dados

Bom, falamos sobre o cenário, fornecemos um contexto prático de trabalho e, inclusive apresentamos as ferramentas e serviços parte da construção da solução. Parece faltar algo, certo: Ah sim, os dados.

Ainda considerando a possibilidade de que todos os leitores deste artigo possam replicar fielmente os passos aqui consolidados para construir e implementar uma solução análoga em seus próprios ambientes, para a proposta deste artigo será utilizado o famoso dataset \[Brazilian E-Commerce\]([Brazilian E-Commerce Public Dataset by Olist | Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)) disponível na plataforma Kaggle.

O dataset Brazilian E-Commerce traz uma visão extremamente interessante sobre vendas online. Possuindo um total de 8 datasets diferentes, o conjunto de dados abre margem para uma série de análises envolvendo pedidos, itens, produtos, pagamentos, reviews e uma série de outros elementos que fazem parte da dinâmica do comércio online. Em termos visuais, a imagem abaixo mostra como os diferentes datasets podem se relacionar de acordo com seus respectivos contextos.

![Data Schema](https://i.imgur.com/HRhd2Y0.png align="left")

Não se preocupe em baixar ou catalogar esses dados em um ambiente AWS para construção da solução proposta pelo artigo. Este objetivo será alcançado através do uso da solução *datadelivery* anteriormente mencionada e isso será explicado em detalhes na seção de desenvolvimento deste artigo.

### Estratégia de Atuação

Considerando os objetivos propostos e os dados apresentados, a solução a ser construída terá, como base, os seguintes elementos:

1. Criação de um job do Glue para ler, transformar e disponibilizar uma tabela curada (SoT) contendo dados de itens de pedidos
    
2. Criação de um job do Glue para ler, transformar e disponibilizar uma tabela curada (SoT) contendo dados essencialmente de pedidos
    
3. Criação de um job Glue para ler as duas bases curadas (SoTs) disponibilizadas pelos jobs descritos anteriormente, unindo-as e disponibilizando uma visão especializada (Spec) que contenha todas as informações desnormalizadas de pedidos online
    
4. Orquestração dos jobs via Step Functions para disponibilização das três tabelas resultantes em uma execução única
    

Assim, considerando as saídas esperadas, temos três tabelas a serem catalogadas com os seguintes pretextos:

| Tabela | Origens |
| --- | --- |
| SoT de itens de pedidos | order\_items, products, sellers, geolocation |
| SoT de pedidos | orders, payments, customers, reviews |
| Spec do e-commerce | Todos os dados unidos e desnormalizados |

Para deixar tudo ainda mais claro, vamos observar a estratégia através de um desenho de arquitetura.

### Arquitetura de Solução

Por fim, finalizando este grande bloco de introdução e contexto da problemática e, aproveitando todo o conhecimento já adquirido até o momento sobre o cenário proposto, a imagem abaixo contempla um desenho de arquitetura que pode servir como um grande guia durante o desenvolvimento da solução.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689815599692/9ed8765b-29da-4282-ae32-33985b10f027.png align="center")

Descrevendo as etapas destacadas no diagrama, temos:

1. Execução paralela de dois Glue jobs para leitura de SoRs e geração de SoTs
    
2. Ao término da etapa 1, execução de um Glue job para leitura de SoTs e geração de uma Spec
    
3. Consulta do resultado final através do Athena
    

À esquerda, é possível ter uma visão sobre o uso dos diferentes módulos e recursos Terraform de modo a implantar todos os serviços necessários para a construção da solução.

### Estruturação de Diretórios Locais

Existem diferentes formas de se estruturar um projeto Terraform. Nesta proposta de solução, vamos considerar a criação de diferentes arquivos com extensão `.tf` para declarar recursos em diferentes propósitos. Trazendo novamente à tona o diagrama de solução apresentado anteriormente, teremos os seguintes arquivos Terraform presentes:

* `datadelivery.tf` para chamada do módulo datadelivery de modo a implantar toda uma estrutura de buckets, os dados do conjunto Brazilian E-Commerce (já são disponibilizados por padrão no módulo datadelivery), um Glue Crawler pré agendado para catalogação dos datasets automaticamente inseridos em um bucket SoR. Legal, né? Dá uma olhada na documentação para saber mais.
    
* `terraglue.tf` para chamada do módulo terraglue visando a declaração, configuração e implantação dos jobs Glue de acordo com seus respectivos propósitos.
    
* `iam.tf` para definição de uma policy e uma role do IAM para ser utilizada no Step Functions.
    
* `stepfunctions.tf` para declaração do workflow de orquestração utilizando o Step Functions.
    

Os arquivos Terraform acima listados contribuem efetivamente para a declaração de recursos a serem implantados em uma conta AWS alvo. Entretanto, existem ainda outros arquivos fundamentalmente essenciais para o projeto de IaC, como por exemplo:

* `locals.tf` para definição de valores locais e variáveis dinâmicas do Terraform, como o ID de uma conta AWS ou o nome da região alvo da implantação dos recursos
    
* `variables.tf` para definição de variáveis do projeto
    
* `versions.tf` para definição de restrições relacionados às versões do *runtime* Terraform ou do provider utilizado
    

Alem disso, outros diretórios e arquivos auxiliares se fazem necessários para complementar toda a dinâmica do projeto. Para ter uma visão completa sobre como o diretório de construção da solução deste artigo pode ser estruturado, considere a árvore abaixo como base:

```bash
├───app
│   └───src
│           sot_itens.py
│           sot_pedidos.py
│           spec_ecommerce.py
│
├───iam
│   ├───policy
│   │       policy-sfn-execution.json
│   │
│   └───trust
│           trust-stepfunctions.json
│
└───infra
        datadelivery.tf
        iam.tf
        stepfunctions.tf
        terraglue.tf
        locals.tf
        variables.tf
        versions.tf
```

Não se preocupe em sair criando toda essa estrutura de diretórios exatamente agora. Faz parte dos objetivos deste artigo fornecer um passo a passo detalhado para a criação de cada uma das etapas da infraestrutura a ser provisionada.

E assim, chegamos ao fim desta seção introdutória. Por mais denso que possa ter sido este conteúdo inicial, aqui pudemos definir:

* O cenário e o problema a ser solucionado
    
* O objetivo final a ser alcançado
    
* A arquitetura de solução idealizada
    
* A estruturação do projeto Terraform para implantação dos recursos
    

Agora, é hora de consolidar todo este conteúdo teórico e colocar a mão na massa para iniciarmos a orquestração de jobs Glue para especialização de dados.

---

## Desenvolvimento

Após conhecer profundamente o cenário de trabalho proposto, é hora de iniciar definitivamente as construções práticas necessárias para a solução.

### Definindo Variáveis Locais

Um dos passos fundamentais para garantir uma melhor gestão dos recursos Terraform a serem declarados no projeto envolve a criação isoladas de algumas variáveis locais capazes de facilitar a obtenção de valores dinâmicos de um ambiente AWS.

Para isso, de forma clara e objetiva, vamos preencher nosso arquivo `locals.tf` com o seguinte conteúdo:

```bash
/* -----------------------------------------------------------
ARQUIVO: locals.tf

Arquivo responsável por consolidar variáveis locais criadas
para facilitar a utilização de valores dinâmicos em um projeto
Terraform envolvendo provedores Cloud. Valores como o ID de
uma conta ou o nome da região de implantação são exemplos de
variáveis que podem ser declaradas e obtidas neste arquivo.
Em sua grande maioria, tais variáveis são obtidas através da
declaração de "data sources" e coleta de seus atributos.
----------------------------------------------------------- */

# Obtendo data sources para coleta de ID da conta e nome de região
data "aws_caller_identity" "current" {}
data "aws_region" "current" {}

# Definindo valores locais
locals {
    # Extraindo ID da conta e nome da região
    account_id = data.aws_caller_identity.current.account_id
    region_name = data.aws_region.current.name
}
```

Assim como pontuado nos comentários do próprio arquivo, tais valores locais serão essenciais para referências futuras nos demais arquivos do projeto. Por hora, entenda que todas as variáveis aqui definidas serão utilizadas em diferentes momentos de declaração dos demais recursos da solução.

### Ingestão de Dados com datadelivery

O próximo passo da criação da nossa solução envolve garantir a existência dos dados brutos (dataset Brazilian E-Commerce). Felizmente, esta é uma *feature* padrão do módulo Terraform [datadelivery](https://datadelivery.readthedocs.io/en/latest/) que, através de uma única chamada, possibilita a criação de todo um *toolkit* de infraestrutura que envolve, entre outros componentes:

* A criação de buckets S3 para armazenamento de dados SoR, SoT e Spec
    
* A ingestão e catalogação automática de dados (incluindo o dataset Brazilian E-Commerce)
    

Portanto, para obter tudo isso no nosso projeto, vamos alterar o arquivo `datadelivery.tf` e incluir uma chamada ao módulo homônimo da seguinte forma:

```bash
/* -----------------------------------------------------------
ARQUIVO: datadelivery.tf

Arquivo responsável por declarar a chamada ao módulo datadelivery
para preparação de toda a infraestrutura de buckets, ingestão
de dados brutos para exploração, seguida da catalogação dos
mesmos. Para maiores detalhes sobre o módulo datadelivery,
acesse sua documentação oficial em:

https://datadelivery.readthedocs.io/en/latest/
----------------------------------------------------------- */

# Chamando módulo datadelivery para ingestão e catalogação de dados
module "datadelivery" {
  source = "git::https://github.com/ThiagoPanini/datadelivery"
}
```

Uma vez declarada a chamada de um módulo Terraform, é possível inicializá-lo e implantar seus recursos declarados em uma conta AWS alvo. Caso queira ter uma visão prévia de tudo aquilo que o módulo datadelivery entrega, basta navegar até o diretório de infraestrutura do projeto e executar os seguintes comandos Terraform:

* `terraform init` para inicializar os módulos do projeto
    
* `terraform plan` para visualizar o plano de implantação
    
* `terraform apply` para implantar os recursos
    

Em um momento oportuno deste artigo, iremos executar tais comandos juntos de forma detalhada.

### Criação de Jobs Glue com terraglue

Agora que já temos toda a nossa estrutura de dados brutos já provisionada, podemos avançar nas etapas relacionadas a definição dos jobs Glue responsáveis por ler, transformar e escrever os dados de origem (SoR) em camadas curadas (SoT) e especializadas (Spec).

Para garantir um acompanhamento detalhado de tudo o que precisará ser realizado para criação dos jobs Glue, esta seção será dividida nas seguintes etapas:

1. Definição dos elementos IAM (policies e role) para garantir as permissões necessárias para todos os jobs
    
2. Definição do código em pyspark para a tabela SoT de Itens seguida da chamada ao módulo [terraglue](https://terraglue.readthedocs.io/en/latest/) para implantação do job na AWS
    
3. Definição do código em pyspark para a tabela SoT de Pedidos seguida da chamada ao módulo [terraglue](https://terraglue.readthedocs.io/en/latest/) para implantação do job na AWS
    
4. Definição do código em pyspark para tabela Spec E-Commerce seguida da chamada ao módulo [terraglue](https://terraglue.readthedocs.io/en/latest/) para implantação do job na AWS
    

Mãos à obra que o caminho é longo!

#### Definindo Policy e Role IAM para o Glue

Conforme mencionado, vamos começar nossa dinâmica de uso do Glue através da definição dos elementos IAM necessários a serem associados a todos os jobs visando garantir as permissões mínimas de execução.

Para isso, dentro do diretório `./infra/iam/policy`, crie um arquivo JSON chamado `policy-glue-basic-access.json` e alimente-o com o seguinte conteúdo:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "GlueFullAccess",
            "Effect": "Allow",
            "Action": [
                "glue:*"    
            ],
            "Resource": [
                "*"
            ]
        },
        {
            "Sid": "GlueS3Access",
            "Effect": "Allow",
            "Action": [
                "s3:GetBucketLocation",
                "s3:ListBucket",
                "s3:ListAllMyBuckets",
                "s3:GetBucketAcl",
                "s3:CreateBucket",
                "s3:PutBucketPublicAccessBlock",
                "s3:GetObject",
                "s3:PutObject",
                "s3:DeleteObject"
            ],
            "Resource": [
                "arn:aws:s3:::*"
            ]
        },
        {
            "Sid": "GlueIAMAccess",
            "Effect": "Allow",
            "Action": [
                "iam:ListRolePolicies",
                "iam:GetRole",
                "iam:GetRolePolicy"		
            ],
            "Resource": "*"
        },
        {
            "Sid": "GlueCloudWatchLogsAccess",
            "Effect": "Allow",
            "Action": [
                "cloudwatch:PutMetricData",
                "logs:CreateLogGroup",
                "logs:CreateLogStream",
                "logs:PutLogEvents",
                "logs:AssociateKmsKey"
            ],
            "Resource": "arn:aws:logs:*:*:/aws-glue/*"
        },
        {
            "Sid": "GlueEC2NetworkAcess",
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeVpcEndpoints",
                "ec2:DescribeRouteTables",
                "ec2:CreateNetworkInterface",
                "ec2:DeleteNetworkInterface",				
                "ec2:DescribeNetworkInterfaces",
                "ec2:DescribeSecurityGroups",
                "ec2:DescribeSubnets",
                "ec2:DescribeVpcAttribute",
                "ec2:CreateTags",
                "ec2:DeleteTags"              
            ],
            "Resource": "*"
        }
    ]
}
```

Neste momento, é importante citar que este arquivo representa a *policy* IAM a ser associada a uma futura *role* IAM que, por sua vez, será vinculada aos jobs Glue para permitir que os mesmos tenham os acessos descritos na *policy*. Caso o leitor tenha interesse em modificar a policy acima fornecida, não há problemas. Desde que as modificações realizadas continuem gerantindo os acessos requisitados por esta proposta de solução.

Em continuidade a este processo, precisamos definir uma *trust policy* capaz de garantir que os jobs Glue são aptos a assumir a futura *role* IAM a ser criada. Para isso, navegue até o diretório `./infra/iam/trust` e crie um arquivo chamado `trust-glue.json` com o seguinte conteúdo:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "glue.amazonaws.com"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}
```

Com as definições dos arquivos JSON já realizadas, é possível então criar nosso arquivo Terraform com as declarações de criação dos elementos IAM. Para tal, altere o arquivo `./infra/iam.tf` com o seguinte contéudo:

```bash
/* -----------------------------------------------------------
ARQUIVO: iam.tf

Arquivo responsável por definir todas as declarações referentes
a criação de roles e policies IAM necessárias para que os
serviços implantados possam assumir as permissões exigidas
de execução. Neste arquivo, será possível encontrar códigos
Terraform que utilizam arquivos JSON para definição das
policies a serem criadas.
----------------------------------------------------------- */

# Criando policy IAM com acessos básicos de execução dos jobs Glue
resource "aws_iam_policy" "glue_jobs_policy" {
  name   = "paninitechlab-awslabs-glue-basic-access-policy"
  policy = file("../iam/policy/policy-glue-basic-access.json")
}

# Criando role IAM para execução dos jobs Glue
resource "aws_iam_role" "glue_jobs_role" {
  name               = "paninitechlab-awslabs-glue-execution-role"
  assume_role_policy = file("../iam/trust/trust-glue.json")

  managed_policy_arns = [
    aws_iam_policy.glue_jobs_policy.arn
  ]

  depends_on = [
    aws_iam_policy.glue_jobs_policy
  ]
}
```

Aqui, mais uma vez, caso o usuário já tenha interesse em ir analisando e validando as declarações, os comandos Terraform continuam válidos. Nesta etapa do processo, o usuário já tem em mãos as definições que garantem a criação de uma policy e uma role IAM a serem futuramente assumidas pelos jobs Glue.

Sinal verde para entrarmos nos detalhes de cada um dos jobs!

#### SoT de Itens

Bom, o primeiro job a ser definido é aquele responsável por consolidar dados específicos de itens de pedidos online registrados no nosso dataset BR-Ecommerce. Neste processo (e assim também para os demais), vamos definir a aplicação (código pyspark) e a infraestrutura (módulo terraglue) para que tudo possa ser detalhado da forma mais didática possível.

Todas as aplicações Spark definidas para os jobs Glue utilizam a biblioteca [sparksnake](https://sparksnake.readthedocs.io/en/latest/) que, por sua vez, fornece uma série de funções e métodos prontos que facilitam (e muito) a vida do desenvolvedor Spark, especialmente se este está implantando jobs Glue na AWS.

##### Aplicação

Iniciando pela aplicação, altere o arquivo `./app/src/sot_itens.py` e insira o seguinte conteúdo com toda a lógica em pyspark para criação da nossa SoT de Itens:

##### Infraestrutura

#### SoT de Pedidos

##### Aplicação

##### Infraestrutura

#### Spec E-commerce

##### Aplicação

##### Infraestrutura

### Orquestração com Step Functions

---

## Conclusão