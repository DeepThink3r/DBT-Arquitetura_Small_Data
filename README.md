# Utilizando DBT como o T do ETL

* [Descrição do Projeto](#descrição-do-projeto)
* [Tecnologias Utilizadas](#tecnologias-utilizadas)
* [Configurando a Arquitetura](#configurando-a-arquitetura)
* * [Docker](#docker)
  * [Subindo os Banco de Dados](#subindo-os-banco-de-dados)
  * [Docker Network](#docker-network)
  * [Airbyte](#airbyte)
  * [Schemas](#Schemas)
  * [Modelos](#Modelos)
  * [Orquestração](#orquestração)
* [Conclusão](#conclusão)

# Descrição do Projeto

Esse projeto tem como objetivo a utilização de tecnologias modern data stack(MDS) da disciplina de engenharia de dados do curso de especialização em Analise de Big Data - Data Engineering do LABDATA FIA para a construção de pipelines que atendam tanto demandas de small data quanto Big Data. Aqui iremos desenhar toda uma arquitetura onde a ênfase é uma ferramenta sensacional para intusiastas de transformações com SQL. 

O Data Build Tool surgiu pela necessidade de tornar o processo de transformação e carga de dados menos moroso e mais aderente ao controle de versionamento, CI/CD,data lineage e qualidade de dados para as equipes de dados.

Mesmo com o íntuito do estudo ser voltado para o DBT, maior parte do tempo foi investido para a criação da infraestrutura para preparar a integração do DBT na arquitetura e a orquestração dos scripts .sql também referênciados como modelos.

Esse é apenas o início de uma jornada de estudo orientado à projetos. Bem vindo ao meu primeiro projeto no github! \

![image](https://github.com/user-attachments/assets/c47e439c-68db-44f3-9828-60e08eecea88)


# Tecnologias Utilizadas \


* Docker
* Sql Server
* Airbyte
* Postgres
* DBT
* Airflow


# Configurando a Arquitetura

Antes de começar a configurar, é necessário que tenhamos o docker instalado em nossas máquinas. Segue abaixo o guia de instalação do docker de acordo com o seu sistema operacional(OS): \

## Docker
https://docs.docker.com/engine/install/

## Subindo os Bancos de Dados

Para subir a imagem mssql no docker, segui as orientações da própria Microsoft. A escolha desse RDBMS foi devido a fácilidade popular os dados utilizando os arquivos .bak da AdventureWorks. Eu escolhi subir a imagem diretamente via terminal com os seguintes comandos abaixo: \

``docker run -d --name mssql_awdb --hostname awdb -p 1433:1433 \ 
`--network ambiente_dev \
`-e "ACCEPT_EULA=Y" \
`-e "MSSQL_SA_PASSWORD=sqlserver" \
-v mssql-db:/var/lib/mssql \``

