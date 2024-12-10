# Classificação multi-saída de patentes utilizando vetores densos e bancos de dados vetoriais
## 1. Contextualização

Documentos de patentes contêm uma grande quantidade de informação na qual devem ser analisados e categorizados de forma a evitar violações de propriedade intelectual no desenvolvimento de novas patentes, com o propósito de auxiliar nesta tarefa e padronizar a classificação destas patentes a Organização Mundial de Propriedade Intelectual(do inglês World Intellectual Property Organization - WIPO) desenvolveu uma taxonomia padrão chamada de Classificação Internacional de Patentes(International Patent Classification - IPC) que contém cerca de de 80.000 categorias a quais cobrem todos tipos de tecnologias industriais.(Sofean, 2021)

Tendo em vista a importância sobre as patentes (Ruijie et al, 2021) relata que existem diversas etapas as quais uma patente deve passar para sua aprovação sendo uma delas a tarefa de classificação de patentes a qual é tratada nesta aplicação, sendo que esta tarefa é de um grau complexo com uma patente podendo ser classificada com mais de uma categoria dentre um grupo de cerca de 80.000 categorias sendo elas divididas em 8 seções em seu nível mais elevado, e então em 128 classes e 648 subclasses e nessas subclasses, com cerca de 7200 grupos principais e 72.000 subgrupos ao nível mais baixo sendo assim a atribuição correta destas categorias é de grande importância na tarefa de classificação de patentes.(Sofean, 2021)

Segundo (Choi. et al., 2022) a tarefa de classificação de patentes era exclusivamente realizada por humanos, porém esta é uma tarefa complexa muitas vezes requerendo que os avaliadores tenham um amplo conhecimento dos domínios técnicos e científicos sendo assim é de grande interesse o desenvolvimento de ferramentas para os auxiliá-los ou até mesmo que seja automatizada esta tarefa.

Atualmente com os avanços na área  de inteligência artificial e processamento de linguagem natural é visto que existe um crescente aumento no desenvolvimento de técnicas de como realizar a classificação de patentes, porém ainda se é necessário que haja intervenção humana no resultado destas técnicas além de que computacionalmente esta tarefa possui custo relativamente elevado (Lee e Hsiang, 2020).

## 2. Descrição da proposta

A proposta desenvolvida neste trabalho busca auxiliar a tarefa de classificação de patentes ao nivel de subclasse com um foco especifico na redução do custo computacional diminuindo drasticamente a quantidade de documentos necessarios utilizados em metodos tradicionais onde se é utilizado o conjunto de patentes chamado USPTO-2M® criado por (LI et al., 2018) em sua totalidade, onde se existem mais de 2 milhões de patentes. Para este trabalho foi utilizado parte do conjuntos de dados criado por (LI et al., 2018), mais especificadamente o conjunto de patentes do ano de 2014 onde se possuem 303.334 patentes para a criação da base de dados e o conjunto de patentes do ano de 2015 que possui 49.900 patentes como um conjunto de teste para a verificação da acuracia. 

A solução desenvolvida utiliza-se do conjunto de patentes do ano de 2014 criado por (LI et al., 2018) para criação embeddings ou seja uma representação vetorial para cada umas das subclasses existentes limitando-se a até 200 patentes para cada subclasse onde cada patente possuirá somente uma unica subclasse atrelada a seu documento afim de melhor criar uma representação vetorial unica para cada subclasse, esta representação então será armazenada em um banco de dados vetorial para que seja possivel realizar futuras consultas sem que haja a necessidade de recriar os embeddings novamente.

Para a criação do banco de dados vetorial que será a base deste projeto foi utilizado o serviço da empresa QDrant onde eles disponibilizam de forma gratuida a criação de um cluster onde se é possivel armazenar um banco de dados vetorial, alem de realizar busca por similiriadidade nos vetores armazenados.

Por fim foi criado um prototipo onde inserido o titulo e o resumo de uma patente estas informações serão transformadas em um embeddings a qual serão comparados aos valores armazenados no banco de dados vetorial e então será retornado os documentos com a maior similiriadidade com a patente submetida e serão classificado de forma decrescente onde em primeiro lugar será a subclasse mais frequente e o ultimo colocado a subclasse menos frequente.

### Diagrama de Comunicação
![diagrama_de_execucao](https://github.com/alacides/multi-output-taxonomy-classifier/blob/main/resources/Concept%20map.png?raw=true)

## 3. Materiais e métodos 

Esta seção descreve detalhadamente as ferramentas e processos utilizados no desenvolvindo do sistema de classificação multi-saída de patentes. 

### Caracterização do sistema
Abaixo se encontra as ferramentas utilizadas para a criação da aplicação, o usuario pode clicar no nome da ferramenta para ser redirecionado a um exemplo explicando a utilização da ferramenta.

- **Python**: Linguagem de programação utilizada para a criação da aplicação no Google Collab devido a sua quantidade extensa de blibliotecas para manipulação de dados.
- [**Google Collab**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/Google%20Collab): Ferramenta utilizada para execução dos codigos devido a capacidade de processamento.
- [**SBERT**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/SBert): Modelos de Transformadores utilizados para a criação de embeddings.
- [**QDrant**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/resources/QDrant): Ferramenta utilizada para armazenamento do banco de dados vetorial assim como a realização de busca por similaridade.

## 4. Execução da Aplicação
1. Para a execução da aplicação primeiramente se é necessario a criação do banco de dados vetorial com os embeddings criados atráves da indexação de patentes. O passo a passo de como criar este banco de dados esta disponivel neste link: [**Indexação de Patentes**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/indexing).

2. **(Opcional porém recomendado)** Com o banco de dados vetorial criado podemos agora realizar um teste para verificação da acuracia da aplicação proposta. O passo a passo de como realizar este teste esta disponivel neste link: [**Teste da Aplicação**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/testing).

3. Após a criação do banco de dados vetorial podemos realizar consultas como a busca por similiaridade fornecendo um determinado titulo e resumo de uma patente, esta busca retornará uma lista de documentos onde cada documento terá a informação sobre a sua subclasse extraida e então será criado um ranking em ordem decrescente onde em primeiro lugar estará a subclasse mais comum até a subclasse menos comum e com base neste ranking podemos descobrir qual a subclasse recomendada para esta patente. O passo a passo de como realizar esta  esta disponivel neste link: [**Classificação de Patentes**](https://github.com/alacides/multi-output-taxonomy-classifier/tree/main/search).

## Bibliografia
LI, S. et al. **DeepPatent: patent classification with convolutional neural networks and word embedding.** Scientometrics,v. 117, p. 721–744, 2018. Disponível em: <https://link.springer.com/article/10.1007/s11192-018-2905-5>.

SOFEAN M. **Deep learning based pipeline with multichannel inputs for patent classification**, World Patent Information. v. 66, p. 102060, 2021, ISSN 0172-2190. Disponível em <https://doi.org/10.1016/j.wpi.2021.102060>.

RUIJIE Z. et al. **Patent text modeling strategy and its classification based on structural features.** World Patent Information, v. 67, p. 102084, 2021, ISSN 0172-2190. Disponível em <https://doi.org/10.1016/j.wpi.2021.102084>.

LEE J.; HSIANG J. **Patent classification by fine-tuning BERT language model.** World Patent Information, v. 61, p. 101965, 2020, ISSN 0172-2190. Disponível em <https://doi.org/10.1016/j.wpi.2020.101965>.

CHOI, S. et al. **Deep learning for patent landscaping using transformer and graph embedding**. Technological Forecasting and Social Change, v. 175, p. 121413, 2022, ISSN 0040-1625. Disponível em <https://doi.org/10.1016/j.techfore.2021.121413>.