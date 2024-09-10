# Classificador multi-saída de patentes utilizando vetores densos e bancos de dados vetoriais com base na taxonomia

Estrutura da Proposta de Projeto

1. Título do Projeto
   - Nome claro e objetivo que reflita o escopo do projeto.

## 2. Introdução
   Este trabalho tem por objetivo a proposição e o desenvolvimento de um método voltado a classificação de patentes por meio da indexação semântica a partir da taxonomia utilizada no processo de rotulagem, ao invés de considerar patentes previamente classificadas visando reduzir a complexidade computacional do processo como um todo e, possivelmente, incrementar a acurácia da classificação
   
   ### Objetivo geral do projeto.

## 3. Motivação
   - Justificativa para o desenvolvimento do projeto.
   - Relevância do tema abordado e problemas que pretende resolver.
   - Potenciais impactos sociais, econômicos ou técnicos.
     
   Documentos de patentes contêm uma grande quantidade de informação na qual devem ser analisados e categorizados de forma a evitar violações de propriedade intelectual no desenvolvimento de novas patentes, com o propósito de auxiliar nesta tarefa e padronizar a classificação destas patentes a Organização Mundial de Propriedade Intelectual(do inglês World Intellectual Property Organization - WIPO) desenvolveu uma taxonomia padrão chamada de Classificação Internacional de Patentes(International Patent Classification - IPC) que contém cerca de de 80.000 categorias a quais cobrem todos tipos de tecnologias industriais.(Sofean, 2021)
   Tendo em vista a importância sobre as patentes (Ruijie et al, 2021) relata que existem diversas etapas as quais uma patente deve passar para sua aprovação sendo uma delas a tarefa de classificação de patentes a qual terá um destaque neste trabalho, sendo que esta tarefa é de um grau complexo e necessita de uma significante atenção do escritório de patentes, já que uma classificação correta de uma patente pode agilizar o processo de aplicação de uma patente.
   Atualmente com os avanços na área de inteligência artificial e processamento de linguagem natural(PLN) é observado que existe um crescente aumento no desenvolvimento de técnicas de como realizar a classificação de patentes, porém ainda se é necessário que haja intervenção humana no resultado destas técnicas além de que computacionalmente esta tarefa possui custo relativamente elevado (Lee e Hsiang, 2020).


## 4. Descrição da Proposta
   - Detalhamento da solução proposta (hardware, software ou ambos).
   - Principais funcionalidades que serão desenvolvidas.
   - Abordagem utilizada para implementação (ferramentas, plataformas, metodologias).

   Desenvolvimento de uma interface ao qual seja submetido um documento com titulo e texto seja possivel realizar sua classificação de acordo com a taxonomia IPC de forma correta.

## 5. Requisitos
   - Requisitos Funcionais:
     Classificação de documentos em forma de taxonomia IPC.
     Interface Grafica
     - Lista das funcionalidades essenciais que o sistema deverá oferecer.
   - Requisitos Não Funcionais:
     Acuracia
     UP-TO-DATE
     - Critérios de qualidade como desempenho, segurança, confiabilidade, manutenibilidade, etc.

## 6. Diagrama de Comunicação
![Representação gráfica do fluxo de dados e da comunicação entre os componentes do sistema](https://media.discordapp.net/attachments/1112119484975681568/1283129612318281858/metodo.jpg?ex=66e1df12&is=66e08d92&hm=4bb5e6d884cdafe135d96658feab42fe866e858a2945a486c0804992aebbfca4&=&format=webp)
   Etapa 1: Coleta de dados das taxonomias do IPC para a base de dados.
Etapa 2: A base de dados é a taxonomia pesquisada anteriormente e realizar um processamento destes dados.
Etapa 3: Uso de um modelos de linguagem de grande porte para a geração dos embeddings
Etapa 4: Banco de dados gerados fixo que só precisa ser alterado caso a taxonomia do IPC mude.
Etapa 5: Patente de entrada
Etapa 6: Utilização de busca aproxima para classificação?
Etapa 7:  

A ser definido esta semana.
   
   - Representação gráfica do fluxo de dados e da comunicação entre os componentes do sistema (ex.: sensores, atuadores, servidores, dispositivos móveis).
   - Descrição breve de cada elemento e sua função.

     

## 7. Diagrama Elétrico (se houver)
   - Diagrama esquemático detalhado dos componentes eletrônicos utilizados no hardware.
   - Explicação de como cada componente se conecta e interage no sistema.

## 8. Revisão da Literatura


   A técnica apresentada no documento de (Choi et al., 2022) propõe o uso de modelos baseados em transformers e embeddings de grafos para representar informações sobre patentes em uma estrutura flexível, facilmente adaptável a diferentes conjuntos de dados. O método utiliza a arquitetura transformer para extrair recursos textuais dos resumos das patentes e o algoritmo Diff2Vec para capturar as relações entre as patentes. Esses recursos são combinados para criar um modelo de machine learning capaz de identificar tendências tecnológicas emergentes em tempo real. Treinado em um grande conjunto de dados de patentes, o modelo aprende a identificar padrões e relações, podendo ser atualizado conforme novas patentes são concedidas e o conhecimento evolui. As principais vantagens são a maior precisão na classificação de patentes, e a capacidade de adaptação a mudanças nas tendências tecnológicas.
	O framework HLSPC proposto por (Chen et al, 2022) visa melhorar a classificação de patentes ao explorar a correlação semântica hierárquica entre textos de patentes e descrições de rótulos correspondentes. Inicialmente, um módulo de aprendizado de representação de patentes é utilizado para capturar características semânticas através de incorporação de texto. Em seguida, um módulo de aprendizado de atenção de rótulo é desenvolvido para modelar a correlação semântica entre textos de patentes e descrições de rótulos hierárquicos, utilizando um mecanismo de atenção em várias camadas. Esse processo permite capturar associações semânticas eficazes, melhorando as predições de categorias de patentes em comparação com métodos convencionais. Experimentos extensivos em dois conjuntos de dados de patentes em inglês demonstraram que o modelo HLSPC supera vários métodos de linha de base de última geração.
	O artigo escrito por (Fang et al, 2021) propõe o framework Patent2Vec para classificação de patentes, utilizando uma abordagem inovadora baseada em múltiplas representações de grafos. São construídos três grafos de patentes considerando palavras-chave, inventores e cessionários(administrador?a tradução não é muito boa em portugues). O framework utiliza um processo de três etapas: aprimoramento de visualizações para capturar interações entre diferentes perspectivas, uma fusão multi-vista baseada em atenção para refinamento das representações e alinhamento de visualizações para modelar relações de dependência. O modelo é treinado com perda conjunta para otimização simultânea da classificação e alinhamento. Os experimentos mostraram que o Patent2Vec supera significativamente métodos de base, melhorando a precisão e na descrição da análise de patentes através da construção e análise de múltiplos grafos de metadados.
	(21) descreve em seu artigo que foram realizados ajustes e comparações entre os modelos de linguagem pré-treinados BERT, XLNet, RoBERTa e ELECTRA para o problema de classificação multi-rótulo de patentes sem simplificá-lo para problemas binários ou multi-classe demonstrando a superioridade desses modelos ao compará-los com outros modelos baseados em deep learning propostos para a classificação de patentes além de investigar o impacto do uso de diferentes embeddings de palavras nos modelos anteriores para melhorar o desempenho de classificação. O autor realizou experimentos em dois conjuntos de dados de patentes que indicam que o XLNet, com sua capacidade de modelar contexto bidirecional, apresenta o melhor desempenho e alcança um novo estado-da-arte na classificação de texto de patentes.
	A proposta de (Frerich et al, 2021) baseia-se na utilização de taxonomias IPC e CPC, que estruturam patentes como grafos de nós e arestas. A metodologia utilizada envolve a transformação desses grafos em vetores de características reais, usando algoritmos eficientes como o de Zhang-Shasha para calcular distâncias de edição de árvores. Quatro algoritmos de aprendizado de máquina foram empregados: SVM, KNN, Regressão Logística e Redes Neurais Artificiais. Esses algoritmos servem tanto como classificadores base quanto de fusão. Prototipagem e seleção de características são otimizadas por métodos específicos, visando criar vetores de características significativas para a classificação. O resultado obtido pelos autores mostra que classificadores baseados em taxonomia têm desempenho comparável aos melhores classificadores baseados em texto além de que a combinação de classificadores IPC e CPC usando técnicas de "stacking" superou o melhor desempenho dos classificadores baseados em texto, independentemente do idioma da patente e sugere que mais de 22 milhões de documentos adicionais, sem títulos ou resumos em inglês, podem ser incluídos em análises tecnológicas automatizadas. 
	(Pujari et al, 2022) propõem uma nova arquitetura que combina representações de transformadores baseados em redes neurais de vários campos textuais de documentos de patentes em embeddings enriquecendo o conjunto de dados USPTO-70k que contém somente títulos e resumos(abstract) com campos adicionais chamados de reivindicações(claims), descrição detalhada, breve sumário, e descrição figurativa, e utilizando-se de todos estes campos em um chamado meta-embedding, os autores mostram que essas informações complementares aumentaram significativamente o desempenho da classificação em relação a representações baseadas em tf-idf, e que ela se tornou particularmente eficaz para rótulos infrequentes, chegando a possuir um F1-macro melhor de 44%.
	Os autores (Lu et al, 2024) falam sobre a falta de modelos de classificação de patentes multilingual sendo que modelos tradicionais se fixam a modelos de um só idioma e com isto eles propõem um modelo de classificação de patentes multilinguístico (chinês, inglês e alemão) e multi-rótulos chamado XLM-R–CNN, que combina o modelo pré-treinado XLM-R com uma rede neural convolucional (CNN) para solucionar este problema, onde o XLM-R é utilizado para codificar os textos das patentes dos diferentes idiomas, enquanto a CNN extrai características relevantes para a classificação. Além disso, eles construíram um grande conjunto de dados multilíngues chamado XLPatent, que inclui patentes nesses três idiomas de forma que todos os idiomas tenham quase a mesma proporção entre si, e utilizando deste conjunto de dados eles demonstram que os resultados do XLM-R-CNN supera outros modelos como o mBERT e o XLM-R, em cinco de oito métricas avaliadas, tendo em destaque a precisão média de 94% e assim sendo eficaz para a categorização de patentes em um contexto multilinguístico.

   - Pesquisas e trabalhos relevantes já realizados sobre o tema.
   - Comparação entre a solução proposta e as soluções existentes.
   - Tecnologias, metodologias e ferramentas mais modernas utilizadas na área.

## 9. Metodologia de Desenvolvimento
   A ser definido esta semana
   
   - Detalhamento das etapas de desenvolvimento.
   - Ferramentas e tecnologias que serão utilizadas para implementação e testes.

## 10. Resultados Esperados
    - Descrição dos principais resultados esperados ao final do projeto.
    - Impacto no monitoramento, automação ou coleta de dados, caso seja relevante.
    - Possíveis melhorias ou benefícios proporcionados pela solução.

## 11. Conclusão
    - Resumo da proposta e considerações sobre a importância do projeto.
    - Expectativas futuras em relação à escalabilidade, melhorias ou aplicações futuras do projeto.

## 12. Referências
    - Citação das fontes utilizadas para revisão da literatura e pesquisa geral.

