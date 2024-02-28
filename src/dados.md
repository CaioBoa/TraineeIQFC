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