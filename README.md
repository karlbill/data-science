# Data Science
Algoritmo K-Nearest Neighboars (KNN)

## Introdução
Utilizado tanto em modelos de classificação quanto de regressão, esse algoritmo avalia a distância entre pontos para sua classificação.

## Características
1. Aprendizado baseado em Instâncias: instâncias brutas de treinamento são usadas para as previsões
2. Aprendizado preguiçoso: todo o fluxo ocorre apenas no momento da previsão. Não há aprendizado do modelo.
3. Não paramétrica: sem suposições acerca do problema.

## Como o algoritmo funciona
![image](https://user-images.githubusercontent.com/39681960/200093456-da5a711e-34c2-46e8-be22-7c460b2f5599.png)

Baseado na imagem acima, vemos um elemento não classificado em meio aos demais elementos já classificados em vermelhos e verdes. De acordo com o algoritmo KNN, precisamos avaliar a vizinha do elemento que queremos classificar de modo a identificar quais as classes mais próximas ao elemento. Assim, definimos a quantidade de elementos (K) que iremos analisar, por exemplo:
1. Se K = 3, o elemento será classificado como verde pois há dois elementos verdes e um vermelho mais próximos a ele;
2. Se k = 7, o elemento será classificado como vermelho pois agora há quatro elementos vermelhos e apenas três verdes mais próximos a ele.

### Overfitting x Underfitting
- Overfitting: desempenho excelente nos treinamentos mas ruim nos testes (desempenho ruim quando submetido a novos dados);
> Quando K é muito pequeno.
- Underfitting: desempenho ruim no treinamento de modo que os testes nem acontecem.
> Quando k é muito grande.

