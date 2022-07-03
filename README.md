# Clustering-Spotify
Nesse projeto usei dados do serviço de streaming de áudio Spotify para estudar uma das técnicas que integra o sistema de recomendação: Clustering.

## O que é Clustering?


<center><img width="60%" src="https://i.imgur.com/S65Sk9c.jpg"></center>


**Clustering** é uma técnica de *Machine Learning*, pertencente à classe de Aprendizado Não-Supervisionado.
Basicamente, o que queremos fazer é agrupar conjuntos de dados semelhantes em um mesmo *Cluster*. Mas como isso acontece?
O algoritmo mais usado para esse tipo de atividade, que estudaremos aqui, é o [K-Means](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html). Esse algortimo calcula a distância dos pontos até os *Centroids*, que ficarão no centro (daí o nome) de cada Cluster.

## Como Saber Quantos Clusters Preciso Usar?


<center><img width="40%" src="https://github.com/rafaelnduarte/sigmoidal_data/blob/master/Elbow_Method.png?raw=true"></center>

É importante saber que o algoritmo não vai decidir sozinho quantos clusters usar. É trabalho do cientista de dados identificar a quantidade correta de clusters, e passar essa quantidade como parâmetro. Para identificar o melhor número de clusters para nossos dados, nós podemos utilizar, por exemplo, as seguintes métricas:

* Inspeção Visual dos Dados.
* Conhecimento previo sobre os dados/objetivos e um número pré-definidos de clusters.
* O *Elbow Method*, ou, em tradução livre, o "Método do Cotovelo". Esse método compara a distância média de cada ponto até o centro do cluster para diferentes números de clusters.

## Informações Importantes Sobre K-Means

O algoritmo K-Means trabalha com a distância entre os pontos, o que significa que ele é altamente sensível à escala dos dados. Por isso, é muito importante que, antes mesmo de descobrir quantos clusters vamos precisar, façamos uso de uma ferramenta como `StandardScaler` ou `MinMaxScaler` para que os dados estejam todos na mesma escala.

Essas duas técnicas de pré-processamento de dados nos retornam valores em uma escala que podemos usar, mas funcionam de maneiras diferentes.

O `StandardScaler` transforma os dados de forma a obter média 0 e desvio padrão 1.

O `MinMaxScaler` coloca todos os números em uma escala entre 0 e 1.

Efetivamente, o efeito que isso faz é trazer todos os pontos para mais perto uns dos outros. A título de curiosidade, essas técnicas também ajudam a diminuir o impacto de outliers em nossos dados.

## Outros Detalhes

Os *centroids* são colocados aleatoriamente nos dados, o que significa, especialmente se não tivermos o número certo de clusters, que cada vez que inicializarmos o algoritmo, teremos clusters diferentes. Veja um exemplo no gráfico abaixo.

## Como Funciona O Algoritmo do Spotify?

Primeiro de tudo, é importante reconhecer o tamanho do Spotify, e com isso, a complexidade de sua operação. Gigantes da mídia como o Spotify, Netflix, Amazon, têm times e times de Ciências de Dados, trabalhando em diferentes tipos de algoritmos e processos de recomendação que trabalham em conjunto.

<center><img width="80%" src="https://github.com/rafaelnduarte/sigmoidal_data/blob/master/spotify_clusters.png?raw=true"></center>

Ainda sobre sistemas de recomendação, precisamos entender os tipos de sistemas de recomendação, para entendermos onde o nosso projeto se encaixa.

* Collaborative Filtering - Comportamento de usuário.
* Content-Based Filtering - Baseado nas informações dos produtos.
* Hybrid Recommendation Systems - Combinação dos dois anteriores.

Com isso em mente, e com o que sabemos sobre o Spotify, temos noção que eles têm um sistema híbrido em funcionamento. Mas onde nosso projeto se encaixa?

> Aqui, vamos analisar as características das músicas, e agrupá-las de acordo com suas similaridades. Nossa análise, seria um dos passos para a criação de um sistema de recomendação do estilo *Content-Based Filtering*.

Agora que sabemos onde estamos pisando, vamos começar a andar!
