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

* Seleção de linhas:

```python
df["20130102":"20130104"]

Out:
                   A         B         C         D
2013-01-02  1.212112 -0.173215  0.119209 -1.044236
2013-01-03 -0.861849 -2.104569 -0.494929  1.071804
2013-01-04  0.721555 -0.706771 -1.039575  0.271860
```

Para selecionar linhas específicas de um dataframe, basta utilizar o index do intervalo de linhas desejadas entre colchetes.

Tais Index costumam ser valores inteiros, porém como no caso acima podem ser alterados para qualquer valor desejado, como datas.

Taletas seleções podem ser salvas em uma varíavel desejada para futuras manipulações.

* Loc:

```python
df.loc[:, ["A", "B"]]

Out: 
                   A         B
2013-01-01  0.469112 -0.282863
2013-01-02  1.212112 -0.173215
2013-01-03 -0.861849 -2.104569
2013-01-04  0.721555 -0.706771
2013-01-05 -0.424972  0.567020
2013-01-06 -0.673690  0.113648
```

Também é possível selecionar linhas específicas de apenas algumas colunas do dataframe, seguindo a notação acima de *linhas ,  colunas* e utilizando o método **loc**.

No caso acima estão sendo selecionadas todas as linhas das colunas A e B.

!!! note
Para selecionar todas as linhas de um dataframe, basta utilizar o operador **:**.
Caso queira selecionar todas as linhas até determinado index x, basta utilizar **:x**.
Caso queira selecionar todas as linhas a partir do index x, basta utilizar **x:**.
E para selecionar todas as linhas entre os index x e y, basta utilizar **x:y**.
!!!

Além disso o método **loc** permite a seleção de linhas específicas, podendo ser selecionadas tanto por index quanto por valores de colunas.

Para o seguinte dataframe:

```python
df = pd.DataFrame([[1, 2], [4, 5], [7, 8]],
                  index=['cobra', 'viper', 'sidewinder'],
                  columns=['max_speed', 'shield'])

Out:
            max_speed  shield
cobra               1       2
viper               4       5
sidewinder          7       8
```

```python
df.loc['viper']

Out:
max_speed    4
shield       5
```

No caso acima, a linha com index "viper" foi selecionada.

```python
df.loc[df['shield'] > 6, ['max_speed']]

            max_speed
sidewinder          7
```

Nesse caso entretanto, a seleção foi feita utilizando um operador boleano para um valor de uma coluna, além de selecionar apena uma das colunas, demonstrando a versatilidade do método **loc**.

* Iloc:

Semelhante ao método loc, o método **iloc** permite a seleção de linhas e colunas específicas de um dataframe, porém utilizando a posição das linhas e colunas ao invés de seus valores.

```python
df.iloc[3]

Out: 
A    0.721555
B   -0.706771
C   -1.039575
D    0.271860
```

O comando **iloc** também pode ser utilizado para seleção de colunas específicas como o método loc, porém utilizando também suas posições.

```python
df.iloc[[1, 2, 4], [0, 2]]
Out: 
                   A         C
2013-01-02  1.212112  0.119209
2013-01-03 -0.861849 -0.494929
2013-01-05 -0.424972  0.276232
```

Documentação
------------

O Pandas possuí uma imensa versatilidade de funções e métodos que podem ser utilizados para manipulação de dataframes e simplificação de processos.

Caso surjam duvidas sobre a utilização de algum método, escolha de argumentos ou a procura de um método específico, a documentação oficial do Pandas é uma ótima fonte de informações.

<a href="https://pandas.pydata.org/docs/index.html" target=”_blank”>Documentação Oficial</a>

Caso hajam dúvidas básicas quanto ao entendimento do Pandas recomenda-se o seguinte tutorial de 10 minutos no qual esse guia se inspirou:

<a href="https://pandas.pydata.org/pandas-docs/stable/user_guide/10min.html" target=”_blank”>10 Minutes to Pandas</a>

E caso jà esteja habituado com a manipulação de dados via Excel, o seguinte tutorial pode ser de grande ajuda:

<a href="https://pandas.pydata.org/docs/getting_started/comparison/comparison_with_spreadsheets.html#compare-with-spreadsheets" target=”_blank”>Comparison with spreadsheets</a>

Métodos Úteis Para Projetos da Entidade
---------------------------------------

Embora seja interessante que descubram os métodos e funções do Pandas utilizando da documentação oficial segue abaixo uma lista de métodos e funções que serão de grande utilidade para os projetos da entidade.

* read_csv(): Método utilizado para leitura de um arquivo .csv e transformação do mesmo em um dataframe, salvando o mesmo em uma variável x.

```python
x = pd.read_csv("nome_do_arquivo.csv")
```

* str_replace(): Método utilizado para substituição de strings em uma séries do panda em que o primeiro argumento é a string a ser substituída e o segundo argumento é a nova string.

```python
x["nome_da_coluna"] = x["nome_da_coluna"].str.replace("string_a_ser_substituida", "nova_string")
```

* strip(): Método utilizado para remoção de espaços em branco de uma série do panda.

```python
x["nome_da_coluna"] = x["nome_da_coluna"].str.strip()
```

* pd.to_datetime(): Método utilizado para transformação de varíaveis de uma série do panda em um formato de data.

```python
x["nome_da_coluna"] = pd.to_datetime(x["nome_da_coluna"])
```

* melt(): Método utilizado para transformação de um dataframe de formato *wide* para *long*, onde o argumento *id_vars* é a coluna que será mantida como identificador e as demais colunas serão transformadas em linhas.

Tal método será melhor compreendido na seção de tratamento de dados.

```python
x = x.melt(id_vars = "nome_da_coluna")
```

* pivot_table(): Método utilizado para transformação de um dataframe de formato *long* para *wide*, onde o argumento *values* é a coluna que será transformada em linhas, o argumento *index* é a coluna que será mantida como identificador e o argumento *columns* é a coluna que será transformada em colunas.

```python
x = pd.pivot_table(x, values = "nome_da_coluna", index = "nome_da_coluna", columns = "nome_da_coluna")
```

* pd.to_numeric(): Método utilizado para transformação de varíaveis de uma série do panda em varíaveis numéricas
```python
x["nome_da_coluna"] = pd.to_numeric(x["nome_da_coluna"])
```

* reset_index(): Método utilizado para resetar o index de um dataframe, gerando uma nova coluna de index com valores inteiros e transforamdno a antiga coluna de index em uma coluna comum.

```python
x = x.reset_index()
```

* pd.Timestamp(): Método utilizado para definição de uma varíavel de data a partir de um valor de data.

Para tal valor de data é necessário utilizar a função **dt.date** do python da biblioteca **datetime**.

```python
dataInicio = pd.Timestamp(dt.date(2010, 1, 1))
```

* Operador &

O operador & é utilizado para a realização de operações lógicas do tipo *and* em uma série do panda.

Caso utilizado como uma operação lógica entre dois dataframes, tal operador irá retornar os pontos de interseção entre os dois dataframes.

```python
x = x[(x["nome_da_coluna"] < dataInicio) & (x["nome_da_coluna"] > dataAnalise)]
```

* pct_change(): Método utilizado para transformação de uma série do panda em uma série de variação percentual em relação ao valor anterior.

```python
x = x.pct_change(fill_method=None)
```

* add(): Método utilizado para adição de um valor constante a todos os valores de uma série do panda.

```python
x = x.add(1)
```

* cumprod(): Método utilizado para transformação de uma série do panda em uma série de variação percentual acumulada.

Em resumo, tal método retorna o valor acumulado de todas as linhas anteriores a linha atual, de modo que o valor final é o valor acumulado de todas as linhas.

```python
x = x.cumprod()
```

* set_index(): Método utilizado para definição de uma coluna específica como index do dataframe.

```python
x = x.set_index('nome_da_coluna')
```




