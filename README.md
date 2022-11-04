# Data Science
Introdução às ferramentas básicas de Ciência de Dados.

## Utilização do Google Colab
Link: https://colab.research.google.com/?utm_source=scs-index
> Esta é uma opção para quem deseja fazer uso de um ambiente de desenvolvimento como o **Jupyter Notebook**, porém sem a necessidade de instalação.

**Obs: se estiver utilizando o **Google Colab** e precisar fazer o *upload* de um *Dataset*, esse arquivo deve ser colocado no *diretório content*.**

## Instalação do Anaconda no ambiente WSL2 (Ubuntu)
Referência: https://gist.github.com/kauffmanes/5e74916617f9993bc3479f401dfec7da

> 1. Repositório das versões do Anaconda: https://repo.continuum.io/archive
> 2. Rode o comando: wget https://repo.continuum.io/archive/[YOUR VERSION]
> 3. Instale o *Anaconda* via comando: $ bash Anaconda[YOUR VERSION].sh
> 4. Aperte *ENTER* para a licença ser apresentada, aperte *ENTER* até a última linha da licença e confirme a inclusão da pasta do Anaconda no *PATH* do sistema
> 5. Se já tiver o *VS Code* instalado, negue essa opção de instalação
> 6. Com o *Anaconda* instalado, feche o terminal e abra um novo. 
> 7. Digite o comando **which python** para que o sistema mostre o **caminho onde o Anaconda foi instalado**
> 8. Rode o *Jupyter Notebook* sem a opção automática de abrir o navegador, através do comando: **jupyter notebook --no-browser**
> 9. Abra o *Jupyter Notebook* através da *URL* que será apresentada no *terminal*

O Anaconda fornece muitas facilidades através de sua instalação, entre elas:
1. *Jupyter Notebook* como **IDE**
2. Centenas de bibliotecas como: **pandas, numpy, matplotlib.pyplot, seaborn, plotly.express** etc.

### Utilização de comandos do *terminal* através do *Jupyter Notebook*:
```
!pip install --upgrade pip
```
> O comando acima atualiza o *pip* para a última versão disponível. Isso deveria ser feito via *terminal* mas com a utilização do *símbolo de exclamação* (**!**) no início do comando, o *Jupyter Notebook* entende que se trata de um comando do *Sistema Operacional*.

