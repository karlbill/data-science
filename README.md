# Data Science
Introdução às ferramentas básicas de Ciência de Dados.

## Preparação de um ambiente com o Colaboratory do Google (Google Colab):
1. Ter uma conta no Gmail
2. Acessar o link: https://colab.research.google.com/notebooks/welcome.ipynb

Observações:
  - Seu código é executado em uma máquina virtual, reciclada no fechamento de sua janela
  - Restauração do arquivo (notebook):
    - refazer o upload do arquivo .csv
    - executar o Runtime 
    - executar o Restart and Run all
    
Link para o arquivo compactado que será utilizado nas análises (Pandas) e visualizações (Seaborn):
https://files.grouplens.org/datasets/movielens/ml-latest.zip

## Iniciando a análise exploratória dos dados MovieLens (Grouplens)
1. Análise do arquivo ratings.csv
  - O arquivo ratings.csv, quando aberto diretamente, será exibido no Excel de maneira mal-formatada:
  ![image](https://user-images.githubusercontent.com/39681960/201909245-b4ea3244-62d5-427d-8333-7a7549379e3b.png)
  - Abra o Excel sem nenhum arquivo e vá até o menu Dados > Obter Dados > De Arquivo > De Text/CSV
    - Selecione o arquivo ratings.csv
    - Se a formatação apresentada estiver correta, simplesmente clique em Carregar
![image](https://user-images.githubusercontent.com/39681960/201909902-bc8d49b0-7395-4248-8eb2-46c76c4fa1f0.png)

Com as linhas e colunas melhor formatadas, vemos que o arquivo ratings.csv possui 4 variáveis: **userId**, **movieId**, **rating**, **timestamp**.

Existe uma biblioteca do Python para leitura de arquivos, como csv: a biblioteca **Pandas**
> Obs: como está sendo utilizado o ambiente virtual do Google Colab, para que o Pandas reconheça o arquivo a ser lido, é necessário fazer o upload do arquivo para a máquina virtual:
![image](https://user-images.githubusercontent.com/39681960/201932687-587ca7be-47ed-4fa0-8432-9ffb163cded2.png)

Feito o upload, basta importar o Pandas e utilizar o método read_csv para realizar a leitura do arquivo:
```
import pandas as pd
ratings = pd.read_csv("ratings.csv")
```
Nesse momento, temos a variável ratings que é do tipo DataFrame.
Para analisar as primeiras 5 linhas (por padrão) do DataFrame, utilize o método head(). E, para verificar a quantidade de linhas e colunas do arquivo, utilize o método shape:
```
ratings.head()
ratings.shape
```

Para alterar o nome das colunas do DataFrame, utilize o método columns:
```
ratings.columns = ["id_usuario","id_filme","avaliacao","horario"]
```

Vamos analisar uma das colunas de nosso DataFrame, a coluna de interesse avaliação:
```
ratings["avaliacao"]
```
Que também pode ser escrito, para maior fluência, da seguinte forma:
```
ratings.avaliacao
```
Ao executarmos o comando acima, estaremos lidando com um novo tipo de dado do Pandas: o tipo Series. Assim como o DataFrame, o tipo Series possui uma grande quantidade de métodos a serem utilizados. Por exemplo:
  - quais diferentes avaliações foram atribuídas aos filmes:
```
ratings["avaliacao"].unique()
```
![image](https://user-images.githubusercontent.com/39681960/201936884-b4ed009e-b26b-4fea-a020-fc54ebc251fe.png)
  - quantas vezes cada avaliação foi dada para todos os filmes (não faz muito sentido. Faria mais sentido para cada filme, separadamente.)
```
ratings["avaliacao"].value_counts()
```
  - qual a média de todas as avaliações feitas:
```
ratings["avaliacao"].mean()
```

Se quisermos analisar os dados através de um gráfico, podemos utilizar a função plot() do Pandas e definir o tipo de gráfico que queremos:
```
ratings.avaliacao.plot(kind='hist')
```
Dessa maneira, será plotado um gráfico Histograma com as avaliações distribuídas atráves do gráfico.
Além disso, temos diversas opções de medidas estatísticas que podem ser exploradas via Pandas, como a mediana:
```
ratings.avaliacao.median()
```
Se quisermos várias dessas medidas reunidas em um único comando, podemos utilizar o método describe:
```
ratings.avaliacao.describe()
```
![image](https://user-images.githubusercontent.com/39681960/201945021-721974bb-ca88-4884-ab6e-1d3cba73104c.png)
> Perceba que o método describe nos fornece os quartis de frequência de cada avaliação.

Podemos visualizar os quartis através de um gráfico estatístico próprio para esse tipo de divisão e melhor visualização da frequência de distribuição, o gráfico Boxplot. Para isso, vamos importar uma nova biblioteca do Python chamada Seaborn e chamar seu método boxplot:
```
import seaborn as sns
sns.boxplot(ratings.avaliacao)
```
 ![image](https://user-images.githubusercontent.com/39681960/201947398-f9cc640f-1d33-4b53-bb16-c02b101c46cc.png)
 
 Obs: existe um problema em relação à versão que o Google Colab nos fornece do Seaborn. Por se tratar de uma versão desatualizada e sem alguns métodos importantes, é importante que realizemos a atualização da versão para alguma superior ou igual à 0.9.0:
 ```
 !pip install seaborn==0.9.0
 ```
> É importante realizar o RESTART do notebook e a execução de todos os passos realizados para que o Google Colab possa atualizar de fato a versão.


## Explorando novo DataFrame 
1. Upload do arquivo movies.csv para a máquina virtual do Google Colab
2. Leitura do arquivo via método read_csv do Pandas
3. Alteração do nome das colunas: id_filme, titulo, genero
> Todos os passos acima já foram vistos anteriormente.

Nesse momento, queremos realizar uma consulta relacionada a algum dos filmes do arquivo. Por exemplo:
```
ratings.query("id_filme == 1")
```
> Com a query acima, estamos buscando todos os registros do DataFrame onde o ID do filme é 1: Toy Story.

Queremos, então, saber quais são as notas atribuídas ao filme 1 e, por fim, a média dessas notas, por exemplo:
```
ratings.query("id_filme == 1").nota.mean()
```
> Obtivemos que o filme Toy Story tem uma média de 3.92 em relação às suas avaliações.

Como precisamos generalizar essa consulta da média para todos os filmes do DataFrame, vamos agrupar os registros pelo ID de cada filme:
```
ratings.groupby("id_filme").mean()["avaliacao"]
```
> o final ["avaliacao"] significa que só precisamos da média das avaliações, para que seja tirada somente a média de interesse.
Que também poderia ser escrito:
```
ratings.groupby("id_filme").mean().avaliacao
```
Separamos essa média das avaliações de cada filme em uma nova série: media_por_filme:
```
media_por_filme = ratings.groupby("id_filme").mean().avaliacao
```

Visualizando graficamente as informações acima, através da biblioteca Pandas e Seaborn:
```
media_por_filme.plot(kind = 'hist')
```
![image](https://user-images.githubusercontent.com/39681960/202006836-db845087-92ee-4e40-b11b-50f3f0294683.png)

Se quisermos plotar o histograma pelo Seaborn:
```
sns.distplot(media_por_filme)
```
![image](https://user-images.githubusercontent.com/39681960/202006905-651b1de7-851b-4566-aa66-273051a85007.png)

> Há algumas diferenças entre os dois gráficos, por exemplo: o Histograma do Pandas é gerado com 10 barras para representação dos intervalos das médias; o histograma do Seaborn é gerado com 20 barras, porque o Seaborn provavelmente utilize um algoritmo diferente, que esteja considerando a Amplitude(A) dos dados para calcular a quantidade de classes (K) e a amplitude dessas classes (C).

Se quiséssemos que o Seaborn plotasse um gráfico com apenas 10 barras, como o Pandas plotou, bastaria informar a quantidade de bins a ser impresso:
```
sns.distplot(media_por_filme, bins=10)
```
Obs: ambas bibliotecas utilizam o Matplotlib.pyplot para a geração de seus gráficos, que seria a maneira mais baixo-nível de plotar um gráfico.
```
import matplotlib.pyplot as plt
plt.hist(media_por_filme)
```
Podemos adicionar um título ao nosso gráfico Histograma:
```
plt.title("Histograma das médias por filmes")
```

Como ambas bibliotecas estão utilizando o Matplotlib.pyplot no final das contas, é possível configurar os gráficos gerados por essas bibliotecas pelo pyplot:
```
plt.figure(figsize=(5,8))
sns.boxplot(y=media_por_filme)
```
> Nesse caso, geramos um gráfico do tipo Boxplot, no eixo vertical, e configurado com um tamanho de 5 u.m. na horizontal e 8 u.m. na vertical. E, no caso do Boxplot, se quisermos conferir os valores do gráfico, podemos utilizar o método describe() sobre o dataframe.

## Variáveis estatísticas
  - **Categóricas**:
    - **Nominal**: representam uma classificação onde não é possível atribuir uma hierarquia entre os dados classificados.
    > Exemplo: Gêneros de um filme 
    - **Ordinal**: representam uma classificação onde existe uma hierarquia entre os dados classificados.
    > Exemplo: Graus escolares (primeiro, segundo, terceiro grau)
  - **Quantitativas**:
    - **Contínuas**: em geral, valores não inteiros que podem ser agrupados em intervalos (Classes)
    > Exemplo: Consumo de energia
    - **Discretas**: não é possível ter 2.5 avaliações de um filme. Ou ele está avaliado ou não está.
    > Exemplo: Quantidade de avaliações de um filme 

## Importação de um novo arquivo csv de filmes
Link: https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata

Esse é um arquivo com muito mais variáveis do que o que estávamos analisando anteriormente: **budget**, **genres**, **homepage**, **id**, **keywords**, **original_language**, **original_title**, **overview**, **popularity**, **production_companies**, **production_countries**, **release_date**, **revenue**, **runtime**, **spoken_languages**, **status**, **tagline**, **title**, **vote_average**, **vote_count**

Vamos, primeiramente, verificar quais os diferentes idiomas de filmes que existem:
```
tmdb_movies.original_language.unique()
```
Vamos contar quantos filmes existem em cada língua:
```
tmdb_movies.original_language.value_counts()
```
![image](https://user-images.githubusercontent.com/39681960/202036731-d2e4bca0-a6aa-43dd-8289-b1e25dcce18b.png)
> Perceba que são apresentadas duas colunas visualmente mas, na verdade, o que temos é um tipo Series, ou seja, apenas uma coluna de valores que é a quantidade de filmes em determinada língua. A coluna que vemos, referente às diferentes línguas, na verdade, funciona como um índice.
```
tmdb_movies.original_language.value_counts().index
```
```
tmdb_movies.original_language.value_counts().values
```
Para transformar o objeto Series em um DataFrame, usamos o método to_frame():
```
tmdb_movies.original_language.value_counts().to_frame()
```
Para que o novo dataframe contenha duas colunas, utilizamos o método reset_index():
```
tmdb_movies.original_language.value_counts().to_frame().reset_index()
```

Os nomes das colunas, nesse caso, é dado automaticamente como index e original_language. Vamos criar uma variável para receber o dataframe e alterar o nome de suas colunas:
```
count_movie_language = tmdb_movies.original_language.value_counts().to_frame().reset_index()
count_movie_language.columns = ["lingua","quantidade_filmes"]
```
Vamos plotar um gráfico de barras para reproduzir visualmente as informações acima:
```
sns.barplot(x="lingua", y="quantidade_filmes", data = count_movie_language)
```
> Da maneira como foi feita a plotagem do gráfico, tivemos que executar vários passos para preparar o Dataframe para que pudesse ser plotado da maneira correta. 

O Seaborn fornece alguns tipos de gráficos que conseguem realizar a mesma função a partir de um único comando, como é o caso do gráfico catplot:
```
sns.catplot(x = 'original_language', kind='count', data = tmdb_movies)
```
> Perceba que utilizamos o Dataframe original, nem foi necessário preparar os dados. Apenas informamos que o tipo de catplot que queríamos era do tipo "count", ou seja, iria realizar a contagem de original_language no eixo y.

### Data Visualization
Faça com que o seu gráfico passe a mensagem clara que você deseja.
Obs: gráfico de pizza (em inglês, pie) só é encontrado no Matplotlib mas não é recomendada sua utilização.





