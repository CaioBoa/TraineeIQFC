<a href="/TraineeIQFC/site/home.html">Curso de Iniciação IQFC</a>

Low Volatility
==============

Explicação do Fator
-------------------

O fator *Low Volatitily (Low Vol)* pode ser interpretado como um fator defensivo, como o nome sugere, seu principal objetivo é diminuir a volatilidade da estratégia, tornando seus resultados mais previsíveis.

As principais abordagens para utilizar esse fator em suas estratégias são:

* Carteiras que o objetivo principal é o baixo risco e/ou baixa volatilidade, intuitivamente esse fator será útil nesse sentido.
* Além disso, pode ser utilizado em conjunto com outros fatores que tenham pouca correlação com ele, já que, de forma análoga, diminuirá os riscos das operações.
* Uma interpretação menos comum, seria para o caso contrário. Se você acreditar que os ativos com maior volatilidade terão mais rendimento em determinado universo, você pode utilizá-lo dessa forma.

Lembre-se que você pode adaptar o low-vol para outros usos conforme suas necessidades, mas durante essa capacitação, ele será interpretado principalmente como o desvio-padrão do retorno do ativo.

Implementação em Python
-----------------------

Nesse exemplo, utilizaremos o desvio-padrão do retorno do ativo, sinta-se livre para utilizar variância, assim como o desvio-padrão de outros indicadores conforme você sentir necessário. Há um medidor de desvio-padrão no economática, mas não recomendamos.

A única base de dados necessária para calcular esse desvio-padrão será a base de dados **fechamento**.

Primeiramente, defina o período de análise e o período de lookback, que é o período de tempo que será analisado para a definição do fator low vol. No caso a seguir, o período de lookback é de 1 mês.

```python
lookback_lowvol = 1
dataInicio = pd.Timestamp(dt.date(2007,1,1))
dataAnalise = dataInicio - pd.DateOffset(months = lookback)
```

Então aplica-se o seguinte bloco de cógido para decisão dos melhores ativos seguindo as regras definidas pelo fator de low vol. 

```python
lowvol = fechamento[(fechamento['Data'] < dataInicio) & (fechamento['Data'] >= dataAnalise)]
lowvol = lowvol.set_index('Data')
lowvol = lowvol.pct_change()
lowvol = lowvol.std()
lowvol = lowvol.dropna()
lowvol = lowvol.iloc[-1]
lowvol = lowvol.sort_values(by = lowvol.columns[0], ascending = True)
lowvol = lowvol.iloc[:10]
```

A primeira linha do bloco de código é responsável por filtrar a base de dados para o momento de análise, ou seja, para o período de tempo que será analisado para a definição do fator low vol.
```python
lowvol = fechamento[(fechamento['Data'] < data_inicial) & (fechamento['Data'] >= dataAnalise)]
```

A segunda linha é responsável por definir o index da base de dados como a coluna de datas, de modo que possamos realizar a seleção do último índice como sendo a última data.
```python
momentum = momentum.set_index('Data')
```

A seguinte linha de código é utilizada para alterar a apresentação dos valores de fechamento de valores inteiros para valores percentuais em relação a valores anteriores, de modo que se possa calcular o desvio-padrão do retorno de maneira simétrica para todos os ativos.
```python
lowvol = lowvol.pct_change()
```

Essa linha é a responsável pelo cálculo do desvio-padrão do retorno de cada ativo.
```python
lowvol = lowvol.std()
```
Para evitar possíveis falhas é interessante remover os valores nulos que podem ter resultado da operação anterior.
```python
lowvol = lowvol.dropna()
```

Seguindo, selecionamos apenas o último dia do período de análise, uma vez que nos interessa apenas o desvio-padrão do retorno de nosso período de lookback.
```python
lowvol = lowvol.iloc[-1]
```

A linha seguinte é responsável por ordenar os ativos de forma crescente, conferindo os primeiros índices aos menores valores de desvio-padrão do retorno.
```python
lowvol = lowvol.sort_values(by = lowvol.columns[0], ascending = True)
```

Tal forma de seleção escolhendo apenas os 10 menores valores é uma forma consideravelmente simples de se realizar a seleção, porém a fim de simplificar o entendimento do fator será realizada de tal forma.

Por fim selecionamos os 10 ativos com menor desvio-padrão do retorno, finalizando a aplicação de nossa estratégia.
```python
lowvol = lowvol.iloc[:10]
```

!!!Aviso
Tal bloco de código se aplica somente para uma iteração da base de dados, ou seja, para um único momento de análise. 

Para a realização efetiva do teste do fator size, é necessário que o bloco de código seja iterado para todo o dataset previsto.
!!!


