<a href="/TraineeIQFC/site/home.html">Curso de Iniciação IQFC</a>

Size
======

Explicação do Fator
---------

O fator size é fundalmentalmente a análise de um ativo em função de seu tamanho, ou seja, a análise de um ativo em função de seu valor de mercado. 

O fator de size possue essencialmente duas interpretações a priori:

* Empresas menores possuem mais espaço para crescer no mercado

Considerando essa abordagem pode se presumir que empresas menores tenderão a apresentar maior valorização, uma vez que possuem mais espaço para crescimento no mercado.

* Empresas maiores possuem maior estabilidade no mercado

Seguindo tal abordagem pode se presumir que empresas maiores apresentarão maior estabilidade no mercado, uma vez que já possuem uma posição consolidada no mercado e dificilmente apresentarão grandes flutuações, sendo boas empresas para investimentos a longo prazo e recebimento de dividendos.

Implementação em Python
---------

Para a aplicação em código do fator momentum a única base de dados necessária para análise será a base de dados **Valor de Mercado**, que contém o valor de mercado total da empresa, sendo ela a multiplicação do número de ações disponíveis pelo valor de cada ação.

Primeiramente, defina o período de análise e o período de lookback, que é o período de tempo que será analisado para a definição do fator size. No caso a seguir, o período de lookback é de 6 meses.

```python
lookback_size = 6
dataInicio = pd.Timestamp(dt.date(2023, 5, 4))
dataAnalise = data_inicial - pd.DateOffset(months = lookback_size)
```
Segue abaixo um exemplo de aplicação do fator size em Python:
```python
size = marketCap[(marketCap['Data'] < dataInicio) & (marketCap['Data'] >= dataAnalise)]
size = size.set_index('Data')
size = size.iloc[-1]
size = size.sort_values(by = lowvol.columns[0], ascending=True)
size = size.dropna()
size = size.iloc[:10]
```

A primeira linha do bloco de código é responsável por filtrar a base de dados para o momento de análise, ou seja, para o período de tempo que será analisado para a definição do fator size.
```python
size = marketCap[(marketCap['Data'] < data_inicial) & (marketCap['Data'] >= data_analise_size)]
```

A segunda linha é responsável por definir o index da base de dados como a coluna de datas, de modo que possamos realizar a seleção do último índice como sendo a última data.
```python
size = size.set_index('Data')
```

Como o fator size é a análise de um ativo em função de seu valor de mercado, a base de dados de *Valor de Mercado* já nos retorna o indíce necessário, portanto basta selecionar o valor de mercado do último dia do período de análise, sendo o mesmo o último index para o período analisado.
```python
size = size.iloc[-1]
```

Em sequência, ordenamos a base de dados em função do valor de mercado, de modo que possamos selecionar os ativos com maior e menor valor de mercado, no caso selecionamos os ativos com menor valor de mercado no topo.
```python
size = size.sort_values(by = lowvol.columns[0], ascending=True)
```

No próximo passo apagamos os valores nulos da base de dados, uma vez que não nos interessam para o fator e costumam ser valores antigos que atrapalham a análise.
```python
size = size.dropna()
```

A linha seguinte é responsável por selecionar os 10 ativos com maior valor de mercado para realizar a seleção final dos ativos, uma vez que esses se encontram no final da base de dados ordenada.

Tal forma de seleção escolhendo apenas os 10 maiores valores é uma forma consideravelmente simples de se realizar a seleção, porém a fim de simplificar o entendimento do fator será realizada de tal forma.
```python
size = size.iloc[:10]
```

!!!Aviso
Tal bloco de código se aplica somente para uma iteração da base de dados, ou seja, para um único momento de análise. 

Para a realização efetiva do teste do fator size, é necessário que o bloco de código seja iterado para todo o dataset previsto.
!!!





