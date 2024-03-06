<a href="/TraineeIQFC/site/home.html">Curso de Iniciação IQFC</a>

Momentum
======

Explicação do Fator
---------

O fator momentum tem como tese a expectativa de crescimento de um ativo em função de seu crescimento passado, como se dísessemos que um ativo que está em alta tende a continuar em alta, e um ativo que está em baixa tende a continuar em baixa.

Para evidenciar tal fator, vamos analisar o gráfico do último ano do ativo **PETR4**.

![PETR4](petr4.png)

A ideia que circunda o fator é de aproveitar os momentos de alta da ação, identificando seus momentos de crescimento e confiando na tese de que seguirão crescendo, de modo que se possa surfar nas ondas de valorização do ativo, tal qual evidenciado na imagem a seguir.

![PETR4](petr4_riscado.png)

Implementação em Python
---------

Para a aplicação em código do fator momentum a única base de dados necessária para análise será a base de dados **fechamento**, que contém o valor de fechamento de cada ativo em cada dia.

A ideia de tal aplicação de código é selecionar os ativos que mais valorizaram em determinado período de tempo passado pré definido para alocar o capital em tais ativos.

Primeiramente, defina o período de análise e o período de lookback, que é o período de tempo que será analisado para a definição do fator momentum. No caso a seguir, o período de lookback é de 3 meses.

```python
lookback = 3
dataInicio = pd.Timestamp(dt.date(2010, 1, 1))
dataAnalise = dataInicio - pd.DateOffset(months = lookback)
```

Segue abaixo um exemplo de aplicação do fator momentum em Python:
```python
momentum = fechamento[(fechamento["Data"] < dataInicio) & (fechamento["Data"] > dataAnalise)]
momentum = momentum.set_index('Data')
momentum = momentum.pct_change(fill_method=None).add(1).cumprod().add(-1)
momentum = momentum.iloc[-1]
momentum = momentum.sort_values(ascending = False)
momentum = momentum.iloc[:10]
```

A primeira linha do bloco de código é responsável por filtrar a base de dados para o momento de análise, ou seja, para o período de tempo que será analisado para a definição do fator momentum.
```python
momentum = fechamento[(fechamento["Data"] < dataInicio) & (fechamento["Data"] > dataAnalise)]
```

A segunda linha é responsável por definir o index da base de dados como a coluna de datas, de modo que possamos realizar operações com a base de dados de forma mais eficiente.
```python
momentum = momentum.set_index('Data')
```

A seguinte linha é a base para o cálculo do fator momentum, portanto, analisaremos ela mais a fundo:

```python
momentum = momentum.pct_change(fill_method=None).add(1).cumprod().add(-1)
```

- pct_change altera o database para que cada valor seja a variação percentual em relação ao valor anterior
- add(1) é necessário para que a variação percentual seja dada na ordem de grandeza correta para uso da função cumprod, exemplo:
    - Se a variação percentual for de 10%, o valor final será 1,1, sendo que pct_change retornaria 0,1
    - Se a variação percentual for de -10%, o valor final será 0,9, sendo que pct_change retornaria -0,1
- cumprod realiza o cálculo da variação percentual acumulada, acumulando o valor total no último dia do período
- add(-1) é necessário para que o valor final seja a variação percentual acumulada, e não o valor acumulado, exemplo:
    - Se a variação percentual for de 180%, o valor final será 1,8, sendo que cumprod retornaria 2,8
    - Se a variação percentual for de -180%, o valor final será -1,8, sendo que cumprod retornaria -0,8

A linha seguinte é responsável por selecionar apenas o último dia do período de análise, uma vez que nos interessa apenas a variação percentual total de nosso período de lookback.

Se selecionamos um lookback de 3 meses, somente nos interessa a variação percentual ao final dos 3 meses.

```python
momentum = momentum.iloc[-1]
```

A linha seguinte é responsável por ordenar os ativos de forma descrescente, conferindo os primeiros índices aos maiores valores de variação percentual acumulada.
```python
momentum = momentum.sort_values(ascending = False)
```

A linha seguinte é responsável por selecionar os 10 ativos com maior variação percentual acumulada para realizar a seleção final dos ativos.

Tal forma de seleção escolhendo apenas os 10 maiores valores é uma forma consideravelmente simples de se realizar a seleção, porém a fim de simplificar o entendimento do fator será realizada de tal forma.
```python
momentum = momentum.iloc[:10]
```

!!!Aviso
Tal bloco de código se aplica somente para uma iteração da base de dados, ou seja, para um único momento de análise. 

Para a realização efetiva do teste do fator momentum, é necessário que o bloco de código seja iterado para todo o dataset previsto.
!!!
