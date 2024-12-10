# Classificação de Patentes

Aqui será descrito os passos necessarios para a utilização do banco de dados vetorial criado anteriormente em [**Indexação de Patentes**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/indexing), para a realização da classificação de uma patente, com base no resultado apresentado na fase de testes da aplicação: [**Teste da Aplicação**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/testing) foi selecionado os valores de até 10 subclasses recomendadas extraidas de um numero de 50 documentos.
## Requisitos
Ferramentas:
- [**Google Collab**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/Google%20Collab)
- [**SBERT**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/SBert)
- [**QDrant**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/QDrant)
- Criação do banco dados vetorial anteriormente criado em [**Indexação de Patentes**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/indexing)
## Realização da Classificação
1. Primeiramente o usuario deverá acessar o link do Google Collab [clicando aqui](https://colab.research.google.com) acessar sua conta e realizar o upload do arquivo **patent_taxonomy_searching_v2_case.ipynb** encontrado nesta pasta.

2. Com o codigo aberto o usuario deve procurar o seguinte trecho do codigo para inserir o titulo e o resumo da patente que deseja clasificar como mostrado na imagem abaixo<br>
    ![](https://github.com/alacides/multi-output-taxonomy-classifier/blob/main/resources/search/search1.png?raw=true)
A patente selecionada para este exemplo foi a seguinte:

    |   Numero da Patente    | US08926299   | 
    |-----------------|------------|
    | Titulo | Pump device | 
    | Resumo | The invention has a housing a pump section formed of a drive gear unit and a driven gear unit a main flow channel through which oil pressure is applied to the driven gear unit in a discharge volume reduction direction a first branching flow channel through which oil pressure that assists oil pressure from the main flow channel is applied a second branching flow channel through which oil pressure is applied to the driven gear unit in a discharge increase direction a first flow channel control section a second flow channel control section and a spring that elastically urges the driven gear unit in a discharge increase direction the first flow channel control section and the second flow channel control section can perform switching control in accordance with each increase or decrease of engine revolutions and in pressure  | 
    | Subclasse | F04C |
3. Agora execute todos os blocos de codigo em ordem sequencial e caso tenha feito tudo corretamente a saida de seu ultimo bloco de codigo deverá ser algo semelhante a:<br>
    ```
    Index name:  tcc-alacides
    {'F04B': 19, 'F04C': 8, 'F04D': 5, 'F04F': 3, 'F15B': 2, 'A61M': 2, 'G05D': 1, 'F16H': 1, 'F16B': 1, 'F03B': 1}
    ```

4. Destacando os dados obtidos na etapa anterior em uma tabela alem de realizar uma pequena analise temos a seguinte classificação:<br>
    | Ranking | Subclasse   | Frequencia   | Relevancia   |
    |-------|------------|------------|------------|
    | 1 | F04B | 18 | 0.36 |
    | 2 | F04C  | 8 | 0.16 |
    | 3 | F04D | 5 | 0.10 |
    | 4 | F04F | 3 | 0.06 |
    | 5 | F15B | 2 | 0.04 |
    | 6 | A61M | 2 | 0.04  |
    | 7 | G05D | 1 | 0.02 |
    | 8 | F16H | 1 | 0.02| 
    | 9 | F16B | 1 | 0.02 |
    | 10| F03B | 1  | 0.02  |

    Analisando os dados obtidos vemos que a subclasse correta (**F04C**) para aquela patente acabou ficando em segundo colocado. Outro ponto importante a se notar que os quatro primeiro colocados são da mesma classe **F04** o que faz sentido pois compartilham varias caracteristicas e vale ressaltar que o banco de dados vetorial é desbalanceado como neste caso a subclasse **F04C** possui apenas 41 documentos atrelados a ela porem as subclasses **F04B** e **F04D** possuem o limite estabelecido de 200 documentos durante a criação o banco de dados vetorial.

<br>