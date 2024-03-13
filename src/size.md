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

Para a aplicação em código do fator momentum a única base de dados necessária para análise será a base de dados **Valor de Mercado**, que contém o valor de mercado de cada ativo em cada dia.

Primeiramente, defina o período de análise e o período de lookback, que é o período de tempo que será analisado para a definição do fator size. No caso a seguir, o período de lookback é de 6 meses.

```python
lookback_size = 6
data_inicial = pd.Timestamp(dt.date(2023, 5, 4))
data_analise_size = data_inicial - pd.DateOffset(months = lookback_size)
```
Em sequência será realizado o cálculo do valor size, 
```python
base_size = size[(size['Data'] < data_inicial) & (size['Data'] >= data_analise_size)]

base_size = base_size.set_index('Data')

base_size = base_size.iloc[-1]

base_size = base_size.reset_index()

base_size = base_size.sort_values(by = base_size.columns[1], ascending=True)

base_size = base_size.dropna()

base_size = base_size[base_size[2].isin(ibx)]

base_size.columns = ['Data', 'variable']
```