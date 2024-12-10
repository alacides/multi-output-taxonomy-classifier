# Indexação de Patentes

Aqui será descrito os passos necessarios para a criação do banco de dados vetorial que armazenará os embeddings criados a partir da informação de um conjunto de patentes de 2014 onde foram selecionadas até 200 patentes para cada determinada subclasse com essas patentes possuindo exclusivamente somente uma unica subclasse em vista de melhor representa-lá. 
## Requisitos
Ferramentas:
- [**Google Collab**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/Google%20Collab)
- [**SBERT**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/SBert)
- [**QDrant**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/QDrant)

Conjunto de dados:
- Para a criação do banco de dados vetorial será necessario tambem um conjunto de dados sobre patentes nesta aplicação utilizaremos o conjunto de dados criado por (LI et al., 2018) chamado USPTO-2M®, mais especificadamente o conjunto de patentes referentes ao ano de 2014 que deverá ser obtido atráves deste link: [**2014_USPTO**](https://drive.google.com/file/d/11Hz11k3hszJfDJbCFbGM0SEkBTLqGZQy/view?usp=sharing)
- Conjunto de dados contendo as subclasses existentes disponivel nesta pasta: **subclass_2025_with_description.h5** .

## Criação do banco de dados vetorial
1. Primeiramente o usuario deverá acessar o link do Google Collab [clicando aqui](https://colab.research.google.com) acessar sua conta e realizar o upload do arquivo **patent_taxonomy_indexing_v2.ipynb** encontrado nesta pasta.

2. Com o documento aberto devemos inserir os conjuntos de dados necessarios para a criação do banco de dados vetorial seguindo os seguintes passos:<br>
    1. Clique na pasta para ver os arquivos do ambiente de trabalho do projeto.<br>![](https://github.com/alacides/multi-output-taxonomy-classifier/blob/main/resources/indexing/indexing1.png?raw=true)<br>
    2. Em seguida clique para enviar arquivos e selecione os arquivos: **2014_USPTO** e **subclass_2025_with_description.h5** .<br>![](https://github.com/alacides/multi-output-taxonomy-classifier/blob/main/resources/indexing/indexing2.png?raw=true)<br>
    3. Caso tenha feito corretamente os passos anterior voce deverá ver a seguinte situação:<br>![](https://github.com/alacides/multi-output-taxonomy-classifier/blob/main/resources/indexing/indexing3.png?raw=true)<br>
3. Agora execute todos os blocos de codigo em ordem sequencial e caso tenha feito tudo corretamente a saida de seu ultimo bloco de codigo deverá ser algo semelhante a:<br>
```
110 patents were found for the subclass A01B.
-> 50 patent were indexed!!!
-> 100 patent were indexed!!!
75 patents were found for the subclass A01C.
-> 150 patent were indexed!!!
136 patents were found for the subclass A01D.
-> 200 patent were indexed!!!
-> 250 patent were indexed!!!
-> 300 patent were indexed!!!
37 patents were found for the subclass A01F.
-> 350 patent were indexed!!!
132 patents were found for the subclass A01G.
-> 400 patent were indexed!!!
...
3 patents were found for the subclass H05C.
23 patents were found for the subclass H05F.
-> 51800 patent were indexed!!!
107 patents were found for the subclass H05G.
-> 51850 patent were indexed!!!
-> 51900 patent were indexed!!!
70 patents were found for the subclass H05H.
-> 51950 patent were indexed!!!
200 patents were found for the subclass H05K.
-> 52000 patent were indexed!!!
-> 52050 patent were indexed!!!
-> 52100 patent were indexed!!!
-> 52150 patent were indexed!!!
2 patents were found for the subclass H10B.
2 patents were found for the subclass H10D.
2 patents were found for the subclass H10F.
-> 52200 patent were indexed!!!
2 patents were found for the subclass H10H.
2 patents were found for the subclass H10K.
2 patents were found for the subclass H10N.
2 patents were found for the subclass H99Z.
52209 patent subclasses were indexed!!!
Indexing was finished!!!
```

4. Agora com o banco de dados vetorial podemos realizar as seguintes funções desenvolvidas:
- [**Teste da Aplicação**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/testing): Teste automatizado para verificar a acuracia da aplicação desenvolvida.
- [**Classificação de Patentes**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/search): Dado um titulo e resumo de uma patente será realizada uma busca por similiriadade que retornará as subclasses mais recomendadas para esta patente em ordem decrescente.
