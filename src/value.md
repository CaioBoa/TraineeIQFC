<a href="/TraineeIQFC/site/home.html">Curso de Iniciação IQFC</a>

Value
======

Explicação do Fator
-----------------

O fator value procura encontrar a diferença entre o preço e o valor de um ativo. Ou seja, procura por ativos que estejam pouco valorizados de acordo com um indicador selecionado, assim como o contrário, ativos que estejam muito valorizados de acordo com seu valor demonstrado.

Alguns indicadores que se encaixam nesses parâmetros são: lucro líquido, preço/lucro, EV/EBITDA, Preço/Valor Patrimonial etc.

Implementação em Python
-----------------

Nesse exemplo, utilizaremos Preço/Lucro como indicador de Value, vale ressaltar que esse indicador se trata do preço da ação, dividido pelo lucro da empresa POR AÇÃO, ou seja, a depender de quantas ações foram emitidas, esse indicador mudará.
Primeiramente, dimensiona-se a data inicial, a data final e o lookback da estratégia: 

```python
data_inicial = pd.Timestamp(dt.date(2007,1,1))
data_final = pd.Timestamp(dt.date(2023,8,31))

lookback_value = 3
```

Para esse indicador, queremos excluir as ações em que ele seja negativo, pois indica prejuízo e selecionar os menores preços/lucro. Isso, pois, as empresas que demonstrarem menores PLs, estão tendo mais lucro em relação ao preço da ação, demonstrando que é possível que haja um aumento no seu preço futuramente.

```python
data_analise_value = data_inicial - pd.DateOffset(months = lookback_value)
base_value = pl[(pl['Data'] < data_inicial) & (pl['Data'] >= data_analise_value)]
base_value = base_value.iloc[-1]
base_value = base_value[(base_value > 0)]
base_value = base_value.reset_index()
base_value = base_value.sort_values(by = base_value.columns[1], ascending = True)
```
