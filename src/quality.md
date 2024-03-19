<a href="/TraineeIQFC/site/home.html">Curso de Iniciação IQFC</a>

Quality
======

Explicação do Fator
-------------------

O fator *Quality*, como o nome sugere, tem o objetivo de mensurar a qualidade das empresas, sobre o previsto de que ativos com um bom funcionamento, investimentos e rendimentos, tendem a se valorizar ao longo do tempo.

No geral, ativos com indicadores altos de quality demonstram risco histórico menor que o do mercado e são considerados defensivos, ou seja, não são necessariamente cíclicos.

Alguns indicadores que podem ser utilizados para medir a qualidade do ativo são: *ROE*, *ROA*, *ROIC*, *fluxo de caixa*, *alavancagem financeira* etc.

Implementação em Python
-----------------------

Nesse exemplo, utilizaremos o **ROE (Return on Equity)**, sinta-se livre para utilizar quaisquer outros indicadores ou combinações em suas estratégias.

Será utilizada a base de dados de ROE, encontrada no economática para esse exemplo, lembre-se de fazer o tratamento de seus dados corretamente antes de utilizar.

Primeiramente, será escolhido uma data final e inicial, assim como o lookback. Ao analisar os dados note como ROIC, ROE e ROA são os mesmos durante um trimestre inteiro, pela natureza do indicador, então lembre-se disso quando escolher seu lookback.

```python
lookback_quality = 3
dataInicio = pd.Timestamp(dt.date(2007,1,1))
dataAnalise = dataInicio - pd.DateOffset(months = lookback_quality)
```

Importante lembrar que esse exemplo foi feito na parte iterada do código do backtest. Nesse caso, estamos apenas filtrando os ROEs positivos e então ordenando-os em ordem decrescente, uma vez que o indicador já esta pronto e não precisa ser tratado.

```python
quality = roe[(roe['Data'] < dataInicio) & (roe['Data'] >= dataAnalise)]
quality = quality.set_index('Data')
quality = quality.iloc[-1]
quality = quality[(quality > 0)]
quality = quality.sort_values(by = lowvol.columns[0], ascending = False)
quality = quality.iloc[:10]
```

A primeira linha do bloco de código é responsável por filtrar a base de dados para o momento de análise, ou seja, para o período de tempo que será analisado para a definição do fator quality.

```python
quality = roe[(roe['Data'] < dataInicio) & (roe['Data'] >= dataAnalise)]
```

A segunda linha é responsável por definir o index da base de dados como a coluna de datas, de modo que possamos realizar a seleção do último índice como sendo a última data.

```python
quality = quality.set_index('Data')
```

A terceira linha é responsável por selecionar apenas o último valor de cada ativo, uma vez que o indicador é o mesmo durante um trimestre inteiro e nos interessa apenas um valor por trimestre.

```python
quality = quality.iloc[-1]
```

A quarta linha é responsável por selecionar apenas os valores positivos do indicador, uma vez que estamos interessados apenas nos ativos com qualidade alta.

```python
quality = quality[(quality > 0)]
```

Em sequência, ordenamos a base de dados em função do indicador, de modo que possamos selecionar os ativos com maior qualidade no topo.

```python       
quality = quality.sort_values(by = lowvol.columns[0], ascending = False)
```

Por fim, selecionamos os 10 ativos com maior qualidade para realizar a seleção final dos ativos, uma vez que esses se encontram no topo da base de dados ordenada.

Tal forma de seleção escolhendo apenas os 10 maiores valores é uma forma consideravelmente simples de se realizar a seleção, porém a fim de simplificar o entendimento do fator será realizada de tal forma.

```python
quality = quality.iloc[:10]
```

!!!Aviso
Tal bloco de código se aplica somente para uma iteração da base de dados, ou seja, para um único momento de análise. 

Para a realização efetiva do teste do fator quality, é necessário que o bloco de código seja iterado para todo o dataset previsto.
!!!




