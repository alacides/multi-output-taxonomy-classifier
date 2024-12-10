# Indexação de Patentes

Aqui será descrito os passos a serem realizados para o uso da biblioteca SBERT utilizada para a criação de embeddings que são representações vetoriais de um dado, assim como um exemplo de seu uso.

## Requisitos
Ferramentas:
- [**Google Collab**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/Google%20Collab)
- [**SBERT**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/SBert)
- [**QDrant**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/QDrant)

Conjunto de dados:
- Para a criação do banco de dados vetorial será necessario tambem um conjunto de dados sobre patentes nesta aplicação utilizaremos o conjunto de dados criado por (LI et al., 2018) chamado USPTO-2M®, mais especificadamente o conjunto de patentes referentes ao ano de 2014 que deverá ser obtido atráves deste link: [**2014_USPTO**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/QDrant)
- Conjunto de dados contendo as subclasses existentes disponivel nesta pasta: **subclass_2025_with_description.h5** .

## Criação do banco de dados vetorial
1. Primeiramente o usuario deverá acessar o link do Google Collab [clicando aqui](https://colab.research.google.com) acessar sua conta e realizar o upload do arquivo **patent_taxonomy_indexing_v2.ipynb** encontrado nesta pasta.

2. No primeiro bloco você deve inserir os seguinte trecho de codigo que adicionara os prerequisitos para executarmos o SBERT no Google Collab:
![](https://github.com/alacides/multi-output-taxonomy-classifier/blob/main/resources/QDrant/Qdrant3.png?raw=true)
as
![](https://github.com/alacides/multi-output-taxonomy-classifier/blob/main/resources/QDrant/Qdrant3.png?raw=true)
as
![](https://github.com/alacides/multi-output-taxonomy-classifier/blob/main/resources/QDrant/Qdrant3.png?raw=true)
as
3.  No proximo bloco adicionaremos qual modelo pre-treinado do SBERT desejamos utilizar nesse caso foi selecionado **all-MiniLM-L6-v2** um modelo leve que gera um embeddings de 384 dimensões:
    ```python
    modelo = SentenceTransformer('all-MiniLM-L6-v2') #Loads the pre-trained SBERT model
    ```

4. No proximo bloco adicionaremos o texto que desejamos utilizar para criação do embeddings e então solicitamos a criação do embeddings que representa esse texto:
    ```python
    texto = 'Um texto simples para exemplificacao do uso de embeddings'
    embedding = modelo.encode(texto).tolist()
    print(embedding)
    ```
5. Agora execute todos o blocos de codigo, caso a execução tenha sido feita corretamente você devera ver um resultado semelhante ao apresentado abaixo em seu ultimo bloco de codigo:
    ```python
    [0.0023197680711746216, -0.012077988125383854, 0.005570219364017248, 0.003798567922785878, -0.008019999600946903, 0.06004340946674347, -0.005210468079894781, 0.05971264839172363, 0.021770309656858444, 0.007885130122303963, 0.02808375284075737, 0.0023287259973585606, 0.02754990942776203, 0.0362921878695488, -0.026183051988482475, 0.00019238902314100415, 0.06314578652381897, 0.08005636185407639, -0.03183247521519661, -0.004789372440427542, 0.034576598554849625, -0.017140667885541916, -0.06131031736731529, -0.0018636836903169751, -0.02196965366601944, 0.025016071274876595, -0.054140616208314896, 0.08863241225481033, 0.06350412219762802, -0.04341660812497139, -0.0064207459799945354, -0.0037565603852272034, 0.0619538389146328, 0.008120201528072357, -0.01242950651794672, 0.05303337052464485, 0.05133850499987602, -0.020509518682956696, -0.08026286214590073, 0.0351935513317585, -0.04334592819213867, 0.011951260268688202, -0.039756663143634796, 0.0938945785164833, -0.013216851279139519, -0.009407570585608482, -0.03779025375843048, 0.056759290397167206, -0.0674525797367096, 0.03094387985765934, -0.055512748658657074, -0.0407380610704422, -0.006284797564148903, -0.07864581048488617, -0.02283087745308876, ..., 0.03878243267536163, 0.0006215799949131906, 0.013311644084751606, 0.07326607406139374, -0.02463781088590622, 0.02428666688501835, -0.06385703384876251, -0.004637051373720169, 0.03229767456650734, -0.03583860024809837, -0.11583992093801498, -0.059407077729701996, 0.09580344706773758, 0.04341498762369156, -0.023342525586485863, -0.06666339933872223, 0.09658031910657883, 0.008316347375512123, 0.06480569392442703, -0.04221745580434799, -0.01158115454018116, 0.009670766070485115, -0.033449552953243256, -0.027999412268400192, 0.023085007444024086, -0.020378785207867622, -0.01921604759991169, 0.0031206337735056877, 0.03523070365190506, 0.037356436252593994, -0.042863182723522186, 0.029601309448480606, -0.006600270047783852, 0.14316487312316895, 0.059992190450429916, 0.0002204639749834314]
    ```

6. Caso possua um resultado similiar agora você está apto a começar a utilizar o SBERT e suas funções.