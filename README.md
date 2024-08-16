# Estrutura de streaming utilizando o dataset de Tarifas de Táxi em Nova York

Este projeto utiliza um conjunto de dados de [táxi da cidade de Nova York](https://www.kaggle.com/competitions/new-york-city-taxi-fare-prediction/overview). O objetivo é propor um pipeline de streaming com o seguinte fluxo:
<p align="center">
<img src="https://github.com/liimaraafael/new-york-city-taxi-fare-prediction/blob/master/workflow.png" alt="workflow" width="900"/>
</p>

## Criação de eventos de streaming
O Flask-SSE será utilizado para criar um servidor de eventos de streaming a partir de um conjunto de dados csv. Esta parte da aplicação é responsável por gerar os eventos que serão consumidos pelo canal de streaming.

## Canal de streaming
O Kafka será utilizado como o sistema de mensagens distribuídas para lidar com o fluxo de eventos de streaming do servidor Flask-SSE, e devera atuar como um canal entre o produtor de eventos (Flask-SSE) e o consumidor de eventos (Spark).

## Consumo de eventos
A aplicação Spark deverá consumir os eventos de streaming do Kafka. Nesta parte será adicionada as funcionalidades de filtros de eventos por data e local da corrida.

## Armazenamento de dados
Os dados filtrados serão armazenados em formato Parquet utilizando o Hadoop Distributed File System (HDFS), o que será útil pensando em possíveis utilizações deste conjunto de dados.

## Orquestração do processamento
O Airflow fará todo o processo de orquestração dessa aplicação (coleta, processamento e armazenamento dos dados).

## Deploy da aplicação
O Docker Compose será utilizado para empacotar a aplicação e suas dependências em um contêiner isolado, o que deverá deixar o processo replicavel em qualquer ambiente com docker.
