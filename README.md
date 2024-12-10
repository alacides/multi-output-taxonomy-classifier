# Classificação multi-saída de patentes utilizando vetores densos e bancos de dados vetoriais
## 1. Introdução

Este trabalho tem por objetivo a proposição e o desenvolvimento de um método voltado a classificação de patentes por meio da indexação semântica a partir da taxonomia utilizada no processo de rotulagem, ao invés de considerar patentes previamente classificadas visando reduzir a complexidade computacional do processo como um todo e, possivelmente, incrementar a acurácia da classificação

## 2. Descrição da proposta

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
