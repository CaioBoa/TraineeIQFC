<a href="/TraineeIQFC/site/home.html">Curso de Iniciação IQFC</a>

Pandas
======

Pandas é uma biblioteca python de código aberto especializada em manipulação e análise de dados. O pandas oferece estruturas de dados e funções para manipulação de tabelas numéricas e séries temporais.

* O que é uma biblioteca?

Se lembra da ideia de funções? Imagine uma biblioteca como um conjunto de funções que você importa para seu código em uma única linha.

Não somente isso, através de uma biblioteca você pode acessar diferentes tipos previamente construídos de objetos com propriedades únicas, tal qual o dataset do pandas que veremos mais adiante, mas interprete como um novo tipo de lista ou dicionário com propriedades especiais.

Para adicionar uma biblioteca ao seu código, você deve importá-la. No caso do pandas, a importação é feita da seguinte forma:

```python
import pandas as pd
```

Aproveitando a oportunidade, é interessante também importar a biblioteca numpy, uma biblioteca de funções matemáticas que é popularmente utilizada em conjunto com o pandas e para muitas outras utilidades.

```python
import pandas as pd
```

Príncipios do Pandas
--------------------

O básico do pandas se resume a duas estruturas de dados novas especializadas em manipulação de dados: Series e DataFrames.

* Series: Uma lista unidimensional de dados com um índice associado.

A Series é a estrutura de dados básica do Pandas. Ela é uma lista unidimensional e sua manipulação é similar a uma lista comum do python, mas com algumas funcionalidades a mais.

Ao que se refere a manipulação de dados básica necessária para os projetos da entidade, o entendimento dessa estrutura não é de grande importância, mas é interessante saber que ela existe e que é a base para a estrutura de dados mais importante do Pandas.

Segue abaixo um exemplo de criação de uma série:

```python
s = pd.Series([1, 3, 5, 7, 6, 8])
```

* DataFrame: Uma tabela bidimensional de dados com índices associados.

Um dataframe é uma tabela de dados, similar a uma planilha do excel. Ela é a estrutura de dados mais importante do Pandas e é a que será mais utilizada em nossos projetos.

Um datafame é composto por séries, e por isso é importante ter entendimento da estrutura das mesmas e compreender suas diferenças perante as listas comuns do python.

A estrutura de um dataframe se resume a uma coluna de index e diversas colunas de valores, que correspondem a um index, tal qual uma tabela qualquer.

Segue abaixo um exemplo de criação de um dataframe:

```python
df2 = pd.DataFrame(
    {
        "A": 1.0,
        "B": pd.Timestamp("20130102"),
        "C": pd.Series(1, index=list(range(4)), dtype="float32"),
        "D": np.array([3] * 4, dtype="int32"),
        "E": pd.Categorical(["test", "train", "test", "train"]),
        "F": "foo",
    }
)
```

Por ser a estrutura principal de manipulação de dados da biblioteca o foco desse documento será na manipulação de dataframes.

Visualização de DataFrames
-------------------------

Em Pandas existem diversas formas de visualizar e manipular a visualização de um dataframe. E abaixo iremos ver algumas das mais importantes.

* head(x): Retorna as x primeiras linhas do dataframe.

```python
df.head()

Out: 
                   A         B         C         D
2013-01-01  0.469112 -0.282863 -1.509059 -1.135632
2013-01-02  1.212112 -0.173215  0.119209 -1.044236
2013-01-03 -0.861849 -2.104569 -0.494929  1.071804
2013-01-04  0.721555 -0.706771 -1.039575  0.271860
2013-01-05 -0.424972  0.567020  0.276232 -1.087401
```

Um dataframe pode ser muito grande e pesado para se carregar de maneira completa a cada mudança realizada, como é o caso de nossos datesets baixados, que contém milhares de dados para cada ação analisada.

No caso acima observamos apenas as 5 primeiras linhas do dataframe.

* tail(x): Retorna as x últimas linhas do dataframe.

```python
df.tail(3)

Out: 
                   A         B         C         D
2013-01-04  0.721555 -0.706771 -1.039575  0.271860
2013-01-05 -0.424972  0.567020  0.276232 -1.087401
2013-01-06 -0.673690  0.113648 -1.478427  0.524988
```

Essa função funciona exatamente como a função head, mas retorna as últimas linhas do dataframe.

Raramente essa função será utilizada, mas é interessante saber que ela existe.

* describe(): Retorna um resumo estatístico do dataframe.

```python
df.describe()
Out: 
              A         B         C         D
count  6.000000  6.000000  6.000000  6.000000
mean   0.073711 -0.431125 -0.687758 -0.233103
std    0.843157  0.922818  0.779887  0.973118
min   -0.861849 -2.104569 -1.509059 -1.135632
25%   -0.611510 -0.600794 -1.368714 -1.076610
50%    0.022070 -0.228039 -0.767252 -0.386188
75%    0.658444  0.041933 -0.034326  0.461706
max    1.212112  0.567020  0.276232  1.071804
```

Essa função retorna um resumo estatístico do dataframe, com informações como média, desvio padrão, mínimo, máximo e quartis.

* sort_index(): Ordena o dataframe pelo index.

```python
df.sort_index(axis=1, ascending=False)

Out: 
                   D         C         B         A
2013-01-01 -1.135632 -1.509059 -0.282863  0.469112
2013-01-02 -1.044236  0.119209 -0.173215  1.212112
2013-01-03  1.071804 -0.494929 -2.104569 -0.861849
2013-01-04  0.271860 -1.039575 -0.706771  0.721555
2013-01-05 -1.087401  0.276232  0.567020 -0.424972
2013-01-06  0.524988 -1.478427  0.113648 -0.673690
```

Essa função ordena o dataframe pelo index, que é a coluna de datas no caso do exemplo acima.

O argumento *axis* é utilizado para definir se a ordenação será feita pelas colunas ou pelas linhas, enquanto o argumento *ascending* é utilizado para definir se a ordenação será feita de forma crescente ou decrescente (seu valor padrão é **True**).

* sort_values(X): Ordena o dataframe por valores da coluna X.

```python
df.sort_values(by="B")
Out: 
                   A         B         C         D
2013-01-03 -0.861849 -2.104569 -0.494929  1.071804
2013-01-04  0.721555 -0.706771 -1.039575  0.271860
2013-01-01  0.469112 -0.282863 -1.509059 -1.135632
2013-01-02  1.212112 -0.173215  0.119209 -1.044236
2013-01-06 -0.673690  0.113648 -1.478427  0.524988
2013-01-05 -0.424972  0.567020  0.276232 -1.087401
```

Essa função ordena o dataframe pelos valores da coluna X, que no caso do exemplo acima é a coluna B.

Como o argumento *ascending* não está presente, a ordenação será feita de forma crescente.

Seleção de Dados 
-------------------------

Durante a manipulação de dados em Pandas é comum a necessidade de selecionar apenas uma parte do dataframe para realizar alguma operação. Abaixo veremos algumas das formas mais comuns de seleção de dados.

* Seleção de uma coluna:

```python
df["A"]

Out: 
2013-01-01    0.469112
2013-01-02    1.212112
2013-01-03   -0.861849
2013-01-04    0.721555
2013-01-05   -0.424972
2013-01-06   -0.673690
Freq: D, Name: A, dtype: float64
```

Para selecionar uma coluna específica de um dataframe, basta utilizar o nome da coluna entre colchetes.

Tal coluna pode ser salva em uma varíavel desejada para futuras manipulações.








