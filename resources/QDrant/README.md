# QDrant

Aqui será descrito os passos a serem realizados para o uso da ferramenta Google QDrant, assim como um exemplo de seu uso.

## Requisitos
- Conta QDrant
- Caso não possua uma conta [**clique aqui**](https://cloud.qdrant.io/login) e siga os passos para o registro antes de prosseguir.
- Google Collab, caso não possua/conheça [**clique aqui**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/Google%20Collab)

## Utilizando o QDrant
1. Nosso primeiro passo será a criação de um cluster gratuito oferecido pela QDrant.
<br>Ao acessar sua conta pela primeira vez você deverá encontrar algo semelhante a imagem a seguir:
![](https://github.com/alacides/multi-output-taxonomy-classifier/blob/main/resources/Google%20Collab/collab1.png?raw=true)
Primeiramente daremos um nome a este cluster no campo **Cluster Name**, e logo em seguida clique no botão **Create Free Cluster**.

2. Logo após ser solicitada a criação de seu cluster será solicitado que o usuario gera uma API KEY atráves do botão **Generate API Key** como exibido na imagem abaixo.
![](https://github.com/alacides/multi-output-taxonomy-classifier/blob/main/resources/Google%20Collab/collab1.png?raw=true)

3. O usuario após clicar no botão **Generate API Key** recebera sua chave de API do cluster criado como mostrado na imagem abaixo, **Preste muita atenção copie e cole essa key para um local seguro pois você não podera ve-lá ou requisita-la novamente**.
![](https://github.com/alacides/multi-output-taxonomy-classifier/blob/main/resources/Google%20Collab/Collab2.png?raw=true)
4. Agora com sua API Key iremos ao Google Collab realizar um teste de seu cluster criado. Crie um novo notebook no Google Collab com dois blocos de codigos no primeiro você deve inserir os seguinte trechos de codigo substituindo os campos **URL_CLUSTER, API_KEY e CLUSTER_NAME** com as informações de seu cluster respectivamente.
No primeiro bloco você deve inserir os seguinte trecho de codigo que adicionara os prerequisitos para executarmos o Qdrant no Google Collab:
    ```python
    !pip install qdrant_client
    from qdrant_client import QdrantClient
    from qdrant_client.models import Distance, VectorParams, PointStruct
    ```
    E no segundo bloco de codigo o seguinte codigo, que ira se conectar ao nosso cluster e após adicionara uma coleção de informações ao banco de dados vetorial e por fim realizará uma consulta no banco de dados:
    ```python
    client = QdrantClient(
        url="URL_CLUSTER", 
        api_key="API_KEY",
    )

    operation_info = client.upsert(
        collection_name="CLUSTER_NAME",
        wait=True,
        points=[PointStruct(id=1, vector=[0.05, 0.61, 0.76, 0.74], payload={"city": "Berlin"}),
            PointStruct(id=2, vector=[0.19, 0.81, 0.75, 0.11], payload={"city": "London"}),
            PointStruct(id=3, vector=[0.36, 0.55, 0.47, 0.94], payload={"city": "Moscow"}),
            PointStruct(id=4, vector=[0.18, 0.01, 0.85, 0.80], payload={"city": "New York"}),
            PointStruct(id=5, vector=[0.24, 0.18, 0.22, 0.44], payload={"city": "Beijing"}),
            PointStruct(id=6, vector=[0.35, 0.08, 0.11, 0.44], payload={"city": "Mumbai"}),
        ],
    )

    search_result = client.query_points(
        collection_name="CLUSTER_NAME",
        query=[0.2, 0.1, 0.9, 0.7],
        with_payload=False,
        limit=3
    ).points

    print(search_result)
    ```
5. Caso o codigo tenha executado corretamente o segundo bloco de codigo retornará ao usuario algo semelhante a seguinte imagem que nós dara uma lista de quais vectores são os mais similiares ao vetor pesquisado como mostrado abaixo.
    ```python
    [ScoredPoint(id=4, version=2, score=1.362, payload=None, vector=None, shard_key=None, order_value=None), 
    ScoredPoint(id=1, version=2, score=1.273, payload=None, vector=None, shard_key=None, order_value=None), 
    ScoredPoint(id=3, version=2, score=1.208, payload=None, vector=None, shard_key=None, order_value=None)]
    ```

6. Caso possua o mesmo resultado agora você está apto a começar a utilizar o QDrant e suas funções.