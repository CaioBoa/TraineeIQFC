Momentum
======

Explicação do Fator
---------

O fator momentum tem como tese a expectativa de crescimento de um ativo em função de seu crescimento passado, como se dísessemos que um ativo que está em alta tende a continuar em alta, e um ativo que está em baixa tende a continuar em baixa.

Para evidenciar tal fator, vamos analisar o gráfico do último ano do ativo **PETR4**.

![PETR4](petr4.png)

A ideia que circunda o fator é de aproveitar os momentos de alta da ação, identificando seus momentos de crescimento e confiando na tese de que seguirão crescendo, de modo que se possa surfar nas ondas de crescimento do ativo, tal qual evidenciado na imagem a seguir.

![PETR4](petr4_riscado.png)

Implementação em Python
---------

A implementação em Python do fator requer apenas a base de dados de fechamento, uma vez que se baseia apenas nos valores anteriores para filtragem dos ativos.

Primeiramente realize a importação das bibliotecas necessárias.
```python
import pandas as pd
import numpy as np
import datetime as dt
```

Em sequência realize o tratamento da base de dados de fechamento. No caso a seguir observamos o tratamento da base de dados de fechamento baixada através do site Economatica.
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

Em seguida, defina seus valores de lookback e data de início. A definição de tais valores depende exclusivamente da estratégia utilizada.
```python
lookback = 3
dataInicio = pd.Timestamp(dt.date(2010, 1, 1))
dataAnalise = dataInicio - pd.DateOffset(months = lookback)
```

Por fim, realize o cálculo do fator momentum. No caso a seguir, o cálculo é realizado através da variação percentual acumulada dos últimos 3 meses.
```python
# Filtragem da base de dados para o momento de análise
momentum = fechamento[(fechamento["Data"] < dataInicio) & (fechamento["Data"] > dataAnalise)]
# Definindo index como Data para realização dos passos seguintes
momentum = momentum.set_index('Data')
# Cálculo da variação percentual acumulada dentro do período de análise
momentum = momentum.pct_change(fill_method=None).add(1).cumprod().add(-1)
# Selecionando apenas o último dia do período de análise, no qual haverá a variação percentual total do período
momentum = momentum.iloc[-1]
# Ordenando os valores de forma decrescente, de modo a selecionar os ativos com maior variação percentual no topo
momentum = momentum.sort_values(ascending = False)
# Selecionando os 10 ativos com maior variação percentual
momentum = momentum.iloc[:10]
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
