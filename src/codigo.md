<a href="/TraineeIQFC/site/home.html">Curso de Iniciação IQFC</a>

Estruturação do Código
======

Essa aula pode servir como uma prévia de como você pode estruturar seu código para a estratégia quantitativa que você irá desenvolver, servindo como uma primeira parte de um guia para o projeto final.

A estruturação do código é extremamente importante para que o mesmo seja de fácil compreensão e manutenção, e para que futuramente você possa reutilizar o mesmo código em outros projetos.

Recomenda-se que estruture seu projeto em um arquivo do tipo .ipynb, que é um arquivo do Jupyter Notebook, que permite a execução de código em Python de forma interativa, e a inserção de texto explicativo entre os códigos, de modo que você possa rodar cédula a cédula sem precisar carregar todos os dados a cada vez que for rodar o código.

Em suma, um código de estratégia quantitativa pode ser estruturado em 5 partes:

1. Importação de Bibliotecas
2. Leitura e Tratamento de Dados
3. Definição de Varíaveis
4. Backtest
5. Análise de Resultados

Importação de Bibliotecas
------

A primeira etapa do código é a importação das bibliotecas que serão utilizadas no projeto. A titulo de exemplo, um código básico pode ser estruturado da seguinte forma:

```python
import pandas as pd
import datetime as dt
import numpy as np
import quantstats as qs
```

É interessante reservar uma cédula única de seu arquivo para a importação de bibliotecas, de modo que você possa facilmente identificar quais bibliotecas estão sendo utilizadas em seu projeto.

Leitura e Tratamento de Dados
------

A segunda etapa do código é a importação e o tratamento dos dados que serão utilizados em sua estratégia. Para tal é interessante que você crie uma cédula única para leitura e tratamento de cada um dos bancos de dados utilizados, de modo que possa carrega-los separadamente.

O modelo para leitura e tratamento de dados pode ser encontrado na aula de Tratamento de Dados.

Definição de Varíaveis
------

A terceira etapa do cógido é a definição de variáveis importantes para sua estratégia.

Tais variáveis serão melhor abordadas na aula de Projeto Final, após o pleno entendimento dos fatores e da estruturação do projeto.

Backtest
------

Esse é o coração do seu projeto, onde você irá definir suas estratégias e realizar os backtests.

* Do que se trata uma Estratégia?

*Estratégias* serão os blocos de código correspondentes a aplicação de seus fatores para determinado período de tempo definido, resumidamente, estratégias são as regras que seu código seguirá para escolher os ativos a serem alocados.

As estratégias correspondem a apenas uma iteração do código, porém o mesmo terá de ser iterado diversas vezes para que se possa analisar o resultado real que sua estratégia teria em determinado período de tempo passado.

A cada iteração de tempo, sua estratégia será responsável por escolher os tickers a qual seu capital deve ser alocado.

* E o Backtest?

O *Backtest* se resume a um grande loop que atua no período de tempo de análise, no qual sua estratégia atuará escolhendo os ativos a serem alocados e simultaneamente o retorno acumulado de sua carteira hipotética será calculado.

Por conta disso, o backtest sempre necessitará da base de dados **Preço de Fechamento** para que se possa calcular o retorno acumulado de sua carteira hipotética.

A partir do backtest conseguimos analisar o resultado que nossa estratégia teria se utilizada em determinado período da história, como forma de validação da mesma.

Análise de Resultados
------

Por fim analisaremos os resultados obtidos em nosso backtest, e a partir disso poderemos validar ou não nossa estratégia.

Essa etapa do projeto se resume a extrair indicadores interessantes de desempenho que possam auxiliar na decisão de adesão ou não de sua estratégia. Para tal recomendamos o uso da biblioteca quantstats do Pyhton, que apresenta diversos indicadores de desempenho.

Esquema Ilustrativo de Estruturação
------

![Estruturação do Código](codigo.png)




