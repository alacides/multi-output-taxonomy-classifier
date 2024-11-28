
# Classificação multi-saída de patentes utilizando vetores densos e bancos de dados vetoriais
## 1. Introdução

Este trabalho tem por objetivo a proposição e o desenvolvimento de um método voltado a classificação de patentes por meio da indexação semântica a partir da taxonomia utilizada no processo de rotulagem, ao invés de considerar patentes previamente classificadas visando reduzir a complexidade computacional do processo como um todo e, possivelmente, incrementar a acurácia da classificação

### Diagrama de execução
![diagrama_de_execucao](https://github.com/alacides/multi-output-taxonomy-classifier/blob/main/resources/Concept%20map.png?raw=true)

### ETAPA 1: Coleta da Taxonomia e Pré-Processamento
A primeira etapa do método proposto consiste na coleta da taxonomia oficial do IPC(Classificação internacional de Patentes do inglês - International Patent Classification) disponível publicamente pela WIPO(Organização Mundial de Propriedade Intelectual do inglês - World Intellectual Property Organization), onde cada classificação é dividida em sua respectiva seção, classe, subclasse, grupo e subgrupo como representado na figura X, após esta coleta os dados obtidos da taxonomia são utilizados para a realização de uma busca em conjuntos de dados de patentes disponibilizadas pelo órgão USPTO(United States Patent and Trademark Office), para que cada uma das 653 subclasses presentes na taxonomia possuam um conjunto de patentes a qual possuam somente esta única subclasse como subclasse descritiva do contexto dela como exemplificado na figura X1 onde a patente demonstrada possui somente uma única subclasse atrelada a ela.

### ETAPA 2: Criação de embeddings utilizando LLM
Esta etapa envolve o uso de um modelo pré-treinado de NLP, também conhecido como LLM (Large Language Model). De forma simplificada, esses modelos geram, a partir de um token (como uma palavra), uma frase ou texto, resultando em um vetor denso, ou embedding. Embeddings oferecem uma representação semântica em um espaço n-dimensional, possibilitando a identificação de vetores semelhantes com base em um vetor de entrada. A dimensionalidade de um embedding varia de acordo com o LLM utilizado. Para este projeto, foi escolhido o modelo "all-MiniLM-L6-v2", principalmente por seu tamanho compacto em megabytes, menor número de dimensões geradas em comparação a outros modelos (384 dimensões) e desempenho eficaz em operações de similaridade vetorial, especialmente na similaridade de cosseno.
Utilizando-se dos dados coletados na etapa 1 foram criados com o auxílio do modelo de LLM "all-MiniLM-L6-v2” embeddings para os dados de cada uma destas respectivas etapas, e então foi feita a mediana destes respectivos embeddings para que o embedding resultante seja o mais adequado para a representação de determinada subclasse.(Adicionar exemplo de embedding)

### ETAPA 3: Formação da base de dados vetorial
Os embeddings então gerados na etapa anterior são armazenados em um banco de dados vetorial para que seja possível a realização de consulta dos mesmos sem que haja a necessidade da recriação dos embeddings a cada novo documento de patente que será classificado. Com esta base de dados vetorial a cada nova solicitação de consulta será retornado ao sistema a lista de embeddings previamente criados para realização da classificação e criação do ranking de recomendação nas etapas futuras.


### ETAPA 4: Solicitação de classificação
Esta etapa é caracterizada pela submissão de uma patente consistente de um título e seu respectivo conteúdo ao qual similarmente ao que foi realizado em etapas anteriores será transformado em um embedding conforme mostrado no exemplo na Etapa 2, para que esta patente possa ser enviada a etapa seguinte onde será possível ser realizada uma busca aproximada para que então seja ao final do processo obtenhamos uma lista de recomendação de subclasses para designada patente. 
### ETAPA 5: Análise e Classificação do Documento
Nesta etapa a patente submetida é transformada em um embeddings ao qual através de processo matemático é realizada comparações com os dados recuperados do banco de dados vetorial em busca da maior similaridade, sendo que essa similaridade caracteriza a semelhança entre as duas patentes sendo assim possível através deste fator descobrir com a subclasse se é mais condizente com o documento submetido e então através desse processo para cada embeddings de subclasse retornado do banco de dados vetorial teremos um valor de similaridade a qual será então organizado e exibido ao usuário na etapa subsequente.   

### ETAPA 6: Recomendação de Classes
Com o resultado obtido através da etapa anterior, será exibido para o usuário um ranking de forma decrescente indo das subclasses com a maior similaridade até as classes com menor similaridade como exibido na tabela X(criar tabela de um caso para explicação)

## 2. Materiais e métodos 

Esta seção descreve detalhadamente as ferramentas e processos utilizados no desenvolvindo do sistema de classificação multi-saída de patentes. 

### Caracterização do sistema

- [**Google Collab**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/Google%20Collab): Ferramenta utilizada para execução do codigos devido a capacidade de processamento.
- [**Python**](): Linguagem de programação utilizada para a criação da aplicação.
- [**SBERT**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/SBert): Modelos de Transformadores utilizados para a criação de embeddings.
- [**QDrant**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/QDrant): Ferramenta utilizada para armazenamento do banco de dados vetorial assim como a realização de busca por similaridade .

### 1. Criação do ambiente no Google Collab
1. **:**

2. **:**

### 2. Setup do banco de dados vetorial utilizando QDrant

### 3. Configurando arquivos com seu banco de dados vetorial

### 4. Criação dos embeddings no banco de dados vetorial

### 5. Testando banco de dados vetorial criado

### 6. Utilização da função de classificação de patentes