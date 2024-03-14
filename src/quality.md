<a href="/TraineeIQFC/site/home.html">Curso de Iniciação IQFC</a>

Quality
======

Explicação do Fator
-------------------

O fator quality, como o nome sugere, tem o objetivo de mensurar a qualidade das empresas, sobre o previsto de que ativos com um bom funcionamento, investimentos e rendimentos, tendem a se valorizar ao longo do tempo.

No geral, ativos com indicadores altos de quality demonstram risco histórico menor que o do mercado e são considerados defensivos, ou seja, não são necessariamente cíclicos.

Alguns indicadores	 que podem ser utilizados para medir a qualidade do ativo são: ROE, ROA, ROIC, fluxo de caixa, alavancagem financeira etc.

Implementação em Python
-----------------------

Nesse exemplo, utilizaremos o ROE (Return on Equity), sinta-se livre para utilizar quaisquer outros indicadores ou combinações em suas estratégias.

Será utilizada a base de dados de ROE, encontrada no economática para esse exemplo, lembre-se de fazer o tratamento de seus dados corretamente antes de utilizar.

Primeiramente, será escolhido uma data final e inicial, assim como o lookback. Ao analisar os dados note como ROIC, ROE e ROA são os mesmos durante um trimestre inteiro, pela natureza do indicador, então lembre-se disso quando escolher seu lookback.

```python
data_inicial = pd.Timestamp(dt.date(2007,1,1))
data_final = pd.Timestamp(dt.date(2023,8,31))

lookback_quality = 3
```

Importante lembrar que esse exemplo foi feito na parte iterada do código do backtest. Nesse caso, estamos apenas filtrando os ROEs positivos e então ordenando-os em ordem decrescente, já que apenas os ativos com os maiores ROEs serão selecionados.

```python
data_analise_quality = data_inicial - pd.DateOffset(months = lookback_quality)
        base_quality = roe[(roe['Data'] < data_inicial) & (roe['Data'] >= data_analise_quality)]
        base_quality = base_quality.iloc[-1]
        base_quality = base_quality[(base_quality > 0)]
        base_quality = base_quality.reset_index()
        base_quality = base_quality.sort_values(by = base_quality.columns[1], ascending = False)
```

Outro exemplo útil, seria caso você tivesse montado seu próprio universo na iteração e quisesse calcular o fator apenas para ele (pode ser aplicado em outros fatores além do quality).

```python
data_analise_quality = data_inicial - pd.DateOffset(months = lookback_quality)
        base_quality = roe[(roe['Data'] < data_inicial) & (roe['Data'] >= data_analise_quality)]
        base_quality = base_quality.melt(id_vars = 'Data')
        base_quality = base_quality[base_quality['variable'].isin(ibx)]
        base_quality = base_quality.pivot_table(index = 'Data', values = 'value', columns = 'variable')
        base_quality = base_quality.iloc[-1]
        base_quality = base_quality[(base_quality > 0)]
        base_quality = base_quality.reset_index()
        base_quality = base_quality.sort_values(by = base_quality.columns[1], ascending = False)
```

Nesse caso, previamente foi calculado previamente o IBX100, e queria-se ver os maiores ROEs dentro desse universo. Logo, utiliza-se o código acima para filtrar os ativos pelo nome, selecionando apenas os que o ticker aparece na lista “ibx”.
