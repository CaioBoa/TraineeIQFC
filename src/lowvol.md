<a href="/TraineeIQFC/site/home.html">Curso de Iniciação IQFC</a>

Low Volatility
==============

Explicação do Fator
-------------------

O fator Low Volatitily (Low Vol) pode ser interpretado como um fator defensivo, como o nome sugere, seu principal objetivo é diminuir a volatilidade da estratégia, tornando seus resultados mais previsíveis.

As principais abordagens para utilizar esse fator em suas estratégias são:

* Carteiras que o objetivo principal é o baixo risco e/ou baixa volatilidade, intuitivamente esse fator será útil nesse sentido.
* Além disso, pode ser utilizado em conjunto com outros fatores que tenham pouca correlação com ele, já que, de forma análoga, diminuirá os riscos das operações.
* Uma interpretação menos comum, seria para o caso contrário. Se você acreditar que os ativos com maior volatilidade terão mais rendimento em determinado universo, você pode utilizá-lo dessa forma.

Lembre-se que você pode adaptar o low-vol para outros usos conforme suas necessidades, mas durante essa capacitação, ele será interpretado principalmente como o desvio-padrão do retorno do ativo.

Implementação em Python
-----------------------

Nesse exemplo, utilizaremos o desvio-padrão do retorno do ativo, sinta-se livre para utilizar variância, assim como o desvio-padrão de outros indicadores conforme você sentir necessário. Há um medidor de desvio-padrão no economática, mas não recomendamos.
A única base de dados necessária para calcular esse desvio-padrão será os dados de fechamento. Logo, baseado em seu lookback, data inicial e final.

```python
data_inicial = pd.Timestamp(dt.date(2007,1,1))
data_final = pd.Timestamp(dt.date(2023,8,31))

lookback_lowvol = 1
```



Então calcula-se o desvio-padrão do período. Note que está sendo utilizado a base de dados do fechamento, que foi explicada como ser feita na aula “Tratamento de Dados”. 

```python
        data_analise_lowvol = data_inicial - pd.DateOffset(months = lookback_lowvol)
        base_lowvol = fechamento[(fechamento['Data'] < data_inicial) & (fechamento['Data'] >= data_analise_lowvol)]
        base_lowvol = base_lowvol.pct_change()
        base_lowvol = base_lowvol.std()
        base_lowvol = base_lowvol.dropna()
        base_lowvol = base_lowvol.reset_index()
        base_lowvol = base_lowvol.sort_values(by = base_lowvol.columns[1], ascending = True)
```
Importante notar que o caso demonstrado está sendo feito na parte iterada do backtest, dependendo da maneira que você preferir fazer esse código, pode calcular o desvio-padrão de todo o período e interpretá-lo de outra maneira no backtest. 
