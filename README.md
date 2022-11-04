# Data Science: Modelos de Classificação
Algoritmo: Árvore de Decisão

## Introdução
É um algoritmo de ML supervisionado, utilizado para classificação e regressão: previsão de categorias discretas e valores numéricos.
Estabelece nós de decisão que se relacionam por uma hierarquia (nó-raiz e nós-folha). O nó-raiz é uma das variáveis independentes da base de dados, enquanto o nó-folha é a classe ou valor a ser gerado como variável dependente. Nesse caso, como aqui estamos lidando com Modelos de Classificação, o nó-folha gerado será uma classe.
A base de uma Árvore de Decisão é a estrutura de dados Árvore.

## Conceito inicial
Subdivide progressivamente os dados em conjuntos cada vez menores e mais específicos, em relação aos atributos, até um tamanho suficiente para ser rotulado. O modelo deve ser treinado com dados previamente rotulados a serem aplicados a novos dados.
Uma árvore de decisão é composta por perguntas e respostas booleanas, realizando a classificação de acordo com o conjunto de respostas obtidas para essas perguntas.
É um dos métodos mais comuns para Aprendizado de Máquina.

- Exemplo de uma Árvore de Decisão

![image](https://user-images.githubusercontent.com/39681960/200064440-8731c79d-fd73-40ea-928f-2528fa8c89de.png)

## Características
Uma abordagem para encontrar a posição de cada nó é o Ganho de Informação e a Entropia: 
* desorganização e falta de uniformidade dos dados são diretamente proporcionais à Entropia.
* Ganho de Informação está diretamente relacionado à homogeneidade dos dados e, consequentemente, a diminuição da Entropia.

É uma boa opção para problemas de classificação e regressão. Pode ser aplicado antes de análises preditivas porque não sofre muita influência de dados faltantes, por exemplo. Lida bem com informações categóricas (nominais).







