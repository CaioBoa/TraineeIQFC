<a href="/TraineeIQFC/site/home.html">Curso de Iniciação IQFC</a>

Value
======

Explicação do Fator
-----------------

O fator value procura encontrar a diferença entre o preço e o valor de um ativo. Ou seja, procura por ativos que estejam pouco valorizados de acordo com um indicador selecionado, assim como o contrário, ativos que estejam muito valorizados de acordo com seu valor demonstrado.

Alguns indicadores que se encaixam nesses parâmetros são: *lucro líquido*, *preço/lucro*, *EV/EBITDA*, *Preço/Valor Patrimonial* etc.

Implementação em Python
-----------------

Nesse exemplo, utilizaremos **Preço/Lucro** como indicador de Value, vale ressaltar que esse indicador se trata do preço da ação, dividido pelo lucro da empresa por ação.

Para a aplicação em código do fator value a única base de dados necessária para análise será a base de dados **Preço/Lucro**.

Primeiramente, dimensiona-se a data inicial, a data final e o lookback da estratégia: 

```python
lookback_value = 3
dataInicio = pd.Timestamp(dt.date(2007,1,1))
dataAnalise = dataInicio - pd.DateOffset(months = lookback_value)
```

Para o indicador *Preço/Lucro* é interessante excluir os valores negativos, uma vez que representam empresas com prejuízo, da mesma forma que queremos captar para nossa carteira os menores valores, uma vez que indicam baixo preço em relação ao lucro da empresa.

```python
value = pl[(pl['Data'] < dataInicio) & (pl['Data'] >= dataAnalise)]
value = value.set_index('Data')
value = value.iloc[-1]
value = value[(value > 0)]
value = value.sort_values(by = value.columns[0], ascending = True)
value = value.iloc[:10]
```

A primeira linha do bloco de código é responsável por filtrar a base de dados para o momento de análise, ou seja, para o período de tempo que será analisado para a definição do fator value.

```python
value = pl[(pl['Data'] < dataInicio) & (pl['Data'] >= dataAnalise)]
```

A segunda linha é responsável por definir o index da base de dados como a coluna de datas, de modo que possamos realizar a seleção do último índice como sendo a última data.

```python
value = value.set_index('Data')
```

A terceira linha é responsável por selecionar apenas o último valor de cada ativo, uma vez que somente nos interessa um valor por período de lookback.

```python
value = value.iloc[-1]
```

A quarta linha é responsável por selecionar apenas os valores positivos do indicador, uma vez que estamos interessados apenas nos ativos com value positivo.

```python
value = value[(value > 0)]
```

Em sequência, ordenamos a base de dados em função do indicador, de modo que possamos selecionar os ativos com menor value no topo.

```python
value = value.sort_values(by = value.columns[0], ascending = True)
```

Por fim, selecionamos os 10 ativos com menor value para realizar a seleção final dos ativos, uma vez que esses se encontram no topo da base de dados ordenada.

Tal forma de seleção escolhendo apenas os 10 menores valores é uma forma consideravelmente simples de se realizar a seleção, porém a fim de simplificar o entendimento do fator será realizada de tal forma.

```python
value = value.iloc[:10]
```

!!!Aviso
Tal bloco de código se aplica somente para uma iteração da base de dados, ou seja, para um único momento de análise. 

Para a realização efetiva do teste do fator value, é necessário que o bloco de código seja iterado para todo o dataset previsto.
!!!


