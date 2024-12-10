# Teste da Aplicação

Aqui será descrito os passos necessarios para a utilização do banco de dados vetorial criado anteriormente em [**Indexação de Patentes**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/indexing), para a realização de um teste para determinar a acuracia do mesmo, para realizar este teste utilizaremos o conjunto de patentes referente ao ano de 2015 extraido do conjunto de dados chamado USPTO-2M® criado por (LI et al., 2018). Os resultados serão apresentados por uma tabela de forma que as linhas representam até que classificação queremos que seja considerado e as colunas são a quantidade de documentos similiriares consultados para encontrar as subclasses.
## Requisitos
Ferramentas:
- [**Google Collab**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/Google%20Collab)
- [**SBERT**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/SBert)
- [**QDrant**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/QDrant)

Conjunto de dados:
- Conjunto de dados contendo as patentes do ano de 2015 disponivel nesta pasta: **2015_USPTO.json** .

## Realização do teste
1. Primeiramente o usuario deverá acessar o link do Google Collab [clicando aqui](https://colab.research.google.com) acessar sua conta e realizar o upload do arquivo **patent_taxonomy_testing_v2.ipynb** encontrado nesta pasta.

2. Com o documento aberto devemos inserir os conjuntos de dados necessarios para a criação do banco de dados vetorial seguindo os seguintes passos:<br>
    1. Clique na pasta para ver os arquivos do ambiente de trabalho do projeto.<br>![](https://github.com/alacides/multi-output-taxonomy-classifier/blob/main/resources/indexing/indexing1.png?raw=true)<br>
    2. Em seguida clique para enviar arquivos e selecione o arquivo: **2015_USPTO.json** .<br>![](https://github.com/alacides/multi-output-taxonomy-classifier/blob/main/resources/indexing/indexing2.png?raw=true)<br>
    3. Caso tenha feito corretamente os passos anterior voce deverá ver a seguinte situação:<br>![](https://github.com/alacides/multi-output-taxonomy-classifier/blob/main/resources/testing/indexing.png?raw=true)<br>
3. Agora execute todos os blocos de codigo em ordem sequencial e caso tenha feito tudo corretamente a saida de seu ultimo bloco de codigo deverá ser algo semelhante a:<br>
    ```
    A saída de streaming foi truncada nas últimas 5000 2 Subclasses
    Query id: 44962 - Patent No: US08970192 - Subclasses: G05F;H02M - Hits: 100
    Query id: 44963 - Patent No: US08970193 - Subclasses: G05F - Hits: 100
    Query id: 44964 - Patent No: US08970194 - Subclasses: G05F - Hits: 100
    Query id: 44965 - Patent No: US08970195 - Subclasses: G05F;H02M - Hits: 100
    Query id: 44966 - Patent No: US08970196 - Subclasses: H02M - Hits: 100
    Query id: 44967 - Patent No: US08970197 - Subclasses: G05F - Hits: 100
    Query id: 44968 - Patent No: US08970199 - Subclasses: H02M - Hits: 100
    ...
    ...
    ...
    k=10 - n=10 - Positive: 59033 - Negative: 37077 - Accuracy: 0.6142232858183332 
    k=10 - n=25 - Positive: 67741 - Negative: 28369 - Accuracy: 0.7048278014774737 
    k=10 - n=50 - Positive: 71177 - Negative: 24933 - Accuracy: 0.7405785037977317 
    k=10 - n=75 - Positive: 72308 - Negative: 23802 - Accuracy: 0.7523462698990739 
    k=10 - n=100 - Positive: 72716 - Negative: 23394 - Accuracy: 0.7565914056809905 
    Accuracy by k and n
    [[0.30146707 0.30731454 0.30421392 0.300874   0.29703465]
    [0.4230257  0.44481323 0.44677973 0.44391843 0.44075538]
    [0.48801373 0.52291125 0.53086047 0.52982    0.52716679]
    [0.53172407 0.57546561 0.58888773 0.59026116 0.58778483]
    [0.56463427 0.61277703 0.63191135 0.63453335 0.63358652]
    [0.58831547 0.63960046 0.6646967  0.668869   0.66881698]
    [0.60300697 0.66090937 0.69081261 0.69681615 0.6982416 ]
    [0.6103007  0.67865987 0.71072729 0.71967537 0.72142337]
    [0.61350536 0.69307044 0.72731245 0.73718656 0.74111955]
    [0.61422329 0.7048278  0.7405785  0.75234627 0.75659141]]
    ```

4. Destacando os dados obtidos na etapa anterior em uma tabela temos:<br>

    |       | 10 Documentos   | 25 Documentos   | 50 Documentos   | 75 Documentos   | 100 Documentos   |
    |-------|------------|------------|------------|------------|------------|
    | 1 Subclasse | 0.30146707 | 0.30731454 | 0.30421392 | 0.300874   | 0.29703465 |
    | 2 Subclasses | 0.4230257  | 0.44481323 | 0.44677973 | 0.44391843 | 0.44075538 |
    | 3 Subclasses | 0.48801373 | 0.52291125 | 0.53086047 | 0.52982    | 0.52716679 |
    | 4 Subclasses | 0.53172407 | 0.57546561 | 0.58888773 | 0.59026116 | 0.58778483 |
    | 5 Subclasses | 0.56463427 | 0.61277703 | 0.63191135 | 0.63453335 | 0.63358652 |
    | 6 Subclasses | 0.58831547 | 0.63960046 | 0.6646967  | 0.668869   | 0.66881698 |
    | 7 Subclasses | 0.60300697 | 0.66090937 | 0.69081261 | 0.69681615 | 0.6982416  |
    | 8 Subclasses | 0.6103007  | 0.67865987 | 0.71072729 | 0.71967537 | 0.72142337 |
    | 9 Subclasses | 0.61350536 | 0.69307044 | 0.72731245 | 0.73718656 | 0.74111955 |
    | 10 Subclasses| 0.61422329 | 0.7048278  | 0.7405785  | 0.75234627 | 0.75659141 |
<br>

5. Agora com o teste da aplicação realizada tambem podemos realizar a seguinte função:
- [**Classificação de Patentes**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/search): Dado um titulo e resumo de uma patente será realizada uma busca por similiriadade que retornará as subclasses mais recomendadas para esta patente em ordem decrescente.

## Bibliografia
LI, S. et al. DeepPatent: patent classification with convolutional neural networks and word embedding. Scientometrics,v. 117, p. 721–744, 2018. Disponível em: <https://link.springer.com/article/10.1007/s11192-018-2905-5>.
