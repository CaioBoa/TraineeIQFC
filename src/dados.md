<a href="/TraineeIQFC/site/home.html">Curso de Iniciação IQFC</a>

Tratamento de Dados
======

Após realizar o download dos dados o primeiro passo para poder efetivamente utiliza-los em uma estratégia quantitativa é trata-los para tornar possível e mais simples a manipulação do dataset.

Esse é um processo extremamente repetitivo que envolve a limpeza, transformação e manipulação dos dados. Portanto, algo que futuramente poderá ser exportado para outros códigos e reutilizado.

!!!
Embora você possívelmente irá apenas copiar e colar o mesmo padrão de tratamento de dados em seus futuros projetos, é importante enteder o que está acontecendo em cada etapa do processo, para que você possa trabalhar futuramente com dados de outras fontes fora o economatica e resolver possíveis bugs que possam surgir.
!!!

Aplicação em Python
------

Segue abaixo uma possível aplicação de tratamento de dados em Python para a base de dados de fechamento baixada através do site Economatica.

```python
fechamento = pd.read_csv("fechamento.csv", delimiter=";")
fechamento.columns = fechamento.columns.str.replace("Fechamento\najust p/ prov\nEm moeda orig\n", "", regex = False)
fechamento["Data"] = pd.to_datetime(fechamento["Data"], format="%d/%m/%Y")
fechamento = fechamento.melt(id_vars =  "Data")
fechamento.value = fechamento.value.replace("-", np.nan)
fechamento.value = fechamento.value.str.replace(".", "")
fechamento.value = fechamento.value.str.replace(",", ".")
fechamento.value = pd.to_numeric(fechamento.value)
fechamento = pd.pivot_table(fechamento, values = "value", index = "Data", columns = "variable")
fechamento = fechamento.reset_index()
```

Pode parecer confuso a primeira vista, mas vamos analisar o código linha a linha para facilitar a compreensão.

```python
fechamento = pd.read_csv("fechamento.csv", delimiter=";")
```

Em tal linha o banco de dados *fechamento.csv* é lido e armazenado na varíavel *fechamento*, utilizando da string ";" como delimitador dos dados, pois é o padrão do arquivo baixado do site Economatica.

```python
fechamento.columns = fechamento.columns.str.replace("Fechamento\najust p/ prov\nEm moeda orig\n", "", regex = False)
```

Aqui é feita a substituição do nome das colunas, que por padrão vem com um texto desnecessário, por um nome mais limpo e fácil de trabalhar.

Essa substituição é feita utilizando a função *str.replace* do pandas, que substitui a string *"Fechamento\najust p/ prov\nEm moeda orig\n"* por um espaço em branco, e o parâmetro *regex = False* que indica que a string a ser substituída não é uma expressão regular, mas uma string literal.

```python
fechamento["Data"] = pd.to_datetime(fechamento["Data"], format="%d/%m/%Y")
```

Aqui é feita a conversão da coluna *Data* para o formato de data, utilizando a função *pd.to_datetime* do pandas, que recebe como parâmetro a coluna a ser convertida e o formato da data, no caso aplicando dia/mês/ano.

```python
fechamento = fechamento.melt(id_vars =  "Data")
```

Aqui é feita a transformação do banco de dados de formato *wide* para *long*, utilizando a função *melt* do pandas, que recebe como parâmetro a coluna que será mantida como identificador e as demais colunas serão transformadas em linhas.

A titulo de exemplo, esse é o head do dataframe antes da função melt:

![fechamento_wide](dados1.png)

E esse é o head do dataframe após a função melt:

![fechamento_long](dados2.png)

Percebe-se que as colunas representando tickers foram transformadas em linhas, de modo que existe agora uma linha para cada combinação de data e ticker, enquanto a coluna *value* representa o valor de fechamento ajustado para cada data e ticker.

```python
fechamento.value = fechamento.value.replace("-", np.nan)
```

Ao colocar todos os valores em uma única coluna é possível de maneira mais facilitada realizar sua manipulação, portanto iremos na coluna value, alterar todos os possíveis valores nulos para NaN, utilizando a função *replace* do pandas, possibilitando que cálculos possam ser realizados sem que haja erros.

```python
fechamento.value = fechamento.value.str.replace(".", "")
fechamento.value = fechamento.value.str.replace(",", ".")
```

Outra etapa importante é a substituição de vírgulas por pontos, e a remoção de pontos, pois o formato de número utilizado na base de dados importada é diferente do padrão reconhecido pelo python, e para que o pandas possa reconhecer os valores como números é necessário que estejam no formato correto.

```python
fechamento.value = pd.to_numeric(fechamento.value)
```

Finalizando os processamentos na coluna *value*, é feita a conversão dos valores para o formato numérico, utilizando a função *pd.to_numeric* do pandas, uma vez que como devem se recordar na aula de Python, existem diversos tipos de varíaveis e tal varíavel se encontra como uma string, necessitando ser transformada em um valor numérico para que possa ser utilizada em cálculos.

```python
fechamento = pd.pivot_table(fechamento, values = "value", index = "Data", columns = "variable")
```

Agora será revertida a alteração feita anteriormente pela função *melt*, transformando a base de dados de *long* para *wide*, utilizando a função *pivot_table* do pandas, que recebe como parâmetros: *values* para o valor que será utilizado para preencher a tabela, *index* para a coluna que será utilizada como identificador das linhas e *columns* para a coluna que será utilizada como identificador das colunas.

```python
fechamento = fechamento.reset_index()
```

Finalizando o processo, é feito o reset do index, para que a coluna *Data* volte a ser uma coluna normal, e não mais o index do dataframe, possibilitando a manipulação da mesma.

Esse é um exemplo de tratamento de dados, mas outras formas podem ser utilizadas a depender do banco de dados que você estiver trabalhando, e futuramente você poderá criar seu próprio padrão de tratamento de dados, que poderá ser reutilizado em futuros projetos.