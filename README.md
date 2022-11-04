# Data Science: Modelos de Classificação
Introdução aos Algoritmos de Classificação

## Algoritmo Naive Bayes (Teorema de Bayes)
O Teorema de Bayes(1701-1761) descreve a probabilidade de um evento, baseado em um conhecimenot a priori que esteja relacionado a um evento. 
É muito utilizado em Machine Learning para categorizar textos baseados nas frequências das palavras, por exemplo, na identificação de um SPAM.
Uma de suas aplicações é na Inferência Estatística (inferência bayesiana).

Naive: ingênuo -> o modelo desconsidera completamente a correlação entre as variáveis, tratando cada variável de maneira independente.

Equação do Teorema de Bayes: 
**P(A | B) = P(B | A) * P(A) / P(B)**, onde:
> **P(X)**: probabilidade de X
> 
> **P(X | Y)**: probabilidade de X condicional a Y(a posteriori)

> **Exemplo: Diagnóstico de doença após análise clínica.**
> 
> Amostra: 100 pessoas
> 
> Comprovação de doença: 20% da amostra
> 
> Receberam teste positivo(estando doente): 90% dos 20% = 0,18 
> 
> Receberam teste positivo(estando saudável): 30% dos 80% = 0,24

> Normalização dos dados: divisão de cada percentual pelo resultado da soma das duas probabilidades
> 
> 0,18 /(0,18 + 0,24) = 0,4285
> 
> 0,24 /(0,18 + 0,24) = 0,5714

> Pergunta: Se uma pessoa realizar o teste e receber o resultado positivo, qual a probabilidade dela possuir a doença?
> 
> Aproximadamente 43% de chance de estar doente.


### Utilização da base de dados preparada na branch manipulacao-dados
