<a href="/TraineeIQFC/site/home.html">Curso de Iniciação IQFC</a>

Python
======

Neste tutorial, vamos aprender os primeiros passos para começar a programar em Python. Percorremos assuntos básicos, como o que são e como declarar variáveis, operadores aritméticos, operadores de comparação, operadores lógicos, estruturas condicionais, estruturas de repetição, funções, strings, listas, tuplas, dicionários, conjuntos, e manipulação de arquivos.

!!!
    Para seguir este tutorial, você precisa ter o Python instalado em seu computador. Se você ainda não tem o Python instalado, siga o tutorial de [Interface de Desenvolvimento](/TraineeIQFC/site/interface.html).

## Variáveis

Variáveis são espaços na memória do computador que armazenam valores. Em Python, a declaração de variáveis é feita de forma simples, basta atribuir um valor a um nome. Por exemplo:

```python
x = 5
y = "Hello, World!"
```

Neste exemplo, *x* é uma variável do tipo inteiro, e *y* é uma variável do tipo string.

## Operadores Aritméticos

Os operadores aritméticos são utilizados para realizar operações matemáticas. Em Python, temos os seguintes operadores aritméticos:

| Operador | Descrição |
|----------|-----------|
| + +      | Adição    |
| -        | Subtração |
| *        | Multiplicação |
| /        | Divisão   |
| %        | Módulo    |
| **       | Exponenciação |
| //       | Divisão inteira |


??? Exemplo

    ```python
    x = 5
    y = 2

    print(x + y) # 7

    print(x - y) # 3

    print(x * y) # 10

    print(x / y) # 2.5

    print(x % y) # 1

    print(x ** y) # 25

    print(x // y) # 2
    ```

## Operadores de Comparação 

Os operadores de comparação são utilizados para comparar dois valores. Em Python, temos os seguintes operadores de comparação:

| Operador | Descrição |
|----------|-----------|
| ==       | Igual     |
| !=       | Diferente |
| >        | Maior     |
| <        | Menor     |
| >=       | Maior ou igual |
| <=       | Menor ou igual |

??? Exemplo

    ```python
    x = 5
    y = 2

    print(x == y) # False

    print(x != y) # True

    print(x > y) # True

    print(x < y) # False

    print(x >= y) # True

    print(x <= y) # False
    ```

## Operadores Lógicos

Os operadores lógicos são utilizados para combinar declarações condicionais. Em Python, temos os seguintes operadores lógicos:

| Operador | Descrição |
|----------|-----------|
| and      | Retorna True se ambas as declarações forem verdadeiras |
| or       | Retorna True se uma das declarações for verdadeira |
| not      | Inverte o resultado, retorna False se o resultado for verdadeiro |

??? Exemplo

    ```python
    x = 5
    y = 2

    print(x > 3 and x < 10) # True

    print(x > 3 or x < 4) # True

    print(not(x > 3 and x < 10)) # False
    ```

## Estruturas Condicionais

As estruturas condicionais são utilizadas para tomar decisões com base em diferentes condições. Em Python, temos a estrutura condicional *if*, que é utilizada para executar um bloco de código se a condição for verdadeira, e a estrutura condicional *else*, que é utilizada para executar um bloco de código se a condição for falsa.

??? Exemplo

    ```python
    x = 5
    y = 2

    if x > y:
        print("x é maior que y")
    else:
        print("x é menor ou igual a y")
    ```

Também temos a estrutura condicional *elif*, que é utilizada para executar um bloco de código se a primeira condição for falsa, e a condição do *elif* for verdadeira. 

??? Exemplo

    ```python
    x = 5
    y = 2

    if x > y:
        print("x é maior que y")
    elif x < y:
        print("x é menor que y")
    else:
        print("x é igual a y")
    ```

## Funções

Nos itens anteriores, vimos como utilizar estruturas condicionais e de repetição para executar um bloco de código. No entanto, se precisarmos executar o mesmo bloco de código em diferentes partes do programa, teremos que repetir o código. Para evitar a repetição de código, podemos utilizar funções. Em Python, uma função é definida utilizando a palavra-chave *def*, seguida pelo nome da função e os parâmetros entre parênteses. Por exemplo:

```python
def my_function():
    print("Hello, World!")
```

Neste exemplo, *my_function* é o nome da função, e o bloco de código que será executado está indentado abaixo da declaração da função. Para chamar a função, basta utilizar o nome da função seguido pelos parênteses. Por exemplo:

```python
my_function()
```

Funções podem receber parâmetros, que são valores que a função espera receber quando é chamada. Por exemplo:

```python
def my_function(x):
    print(x)

my_function("Hello, World!")
```

Neste exemplo, a função *my_function* recebe um parâmetro *x*, e imprime o valor de *x*.

??? Exercício de Fixação

    Crie uma função que receba dois números como parâmetros e retorne a soma dos dois números.

    ::: Gabarito

        ```python
        def soma(x, y):
            return x + y

        print(soma(5, 2)) # 7
        ```
::: Dica
    Para mais informações sobre funções, consulte a [documentação oficial](https://docs.python.org/3/tutorial/controlflow.html#defining-functions).

## Funções Nativas

Ainda nos itens anteriores, em alguns exemplos, utilizamos funções nativas do Python, como **print( )**, **len( )** e **range( )**. As funções nativas do Python são funções que já vêm com a linguagem, e estão disponíveis para serem utilizadas em qualquer programa. 

Disponibilizamos, a seguir, uma lista com algumas funções nativas do Python, se você quiser conhecer mais funções nativas, consulte a [documentação oficial](https://docs.python.org/3/library/functions.html).

::: Tabela de Funções Nativas
    | Função | Descrição |
    |--------|-----------|
    | abs( ) | Retorna o valor absoluto de um número |
    | all( ) | Retorna True se todos os itens de um iterável forem verdadeiros |
    | any( ) | Retorna True se algum item de um iterável for verdadeiro |
    | bin( ) | Converte um número inteiro em binário |
    | bool( ) | Retorna o valor booleano de um objeto |
    | chr( ) | Retorna um caractere correspondente ao código Unicode |
    | complex( ) | Retorna um número complexo |
    | dict( ) | Retorna um dicionário |
    | float( ) | Retorna um número de ponto flutuante |
    | hex( ) | Converte um número inteiro em hexadecimal |
    | int( ) | Retorna um número inteiro |
    | len( ) | Retorna o comprimento de um iterável |
    | list( ) | Retorna uma lista |
    | max( ) | Retorna o maior item de um iterável |
    | min( ) | Retorna o menor item de um iterável |
    | oct( ) | Converte um número inteiro em octal |
    | ord( ) | Retorna o código Unicode de um caractere |
    | pow( ) | Retorna o valor de x elevado à potência de y |
    | print( ) | Imprime um objeto |
    | range( ) | Retorna uma sequência de números |
    | round( ) | Retorna um número arredondado |
    | set( ) | Retorna um conjunto |
    | sorted( ) | Retorna uma lista ordenada |
    | str( ) | Retorna uma string |
    | sum( ) | Retorna a soma de todos os itens de um iterável |
    | tuple( ) | Retorna uma tupla |
    | type( ) | Retorna o tipo de um objeto |
    | zip( ) | Retorna um objeto zip |

## Strings

Strings são sequências de caracteres, e são utilizadas para representar texto em Python. Em Python, as strings são declaradas utilizando aspas simples ou duplas. Por exemplo:

```python
x = "Hello, World!"
y = 'Hello, World!'
```

Podemos utilizar diversas funções nativas do Python para manipular strings. Listamos algumas na tabela abaixo.

::: Tabela de Funções para Strings
                            
    | Função | Descrição |
    |--------|-----------|
    | capitalize( ) | Converte o primeiro caractere para maiúsculas |
    | casefold( ) | Converte a string para minúsculas |
    | count( ) | Retorna o número de vezes que um valor específico aparece na string |
    | find( ) | Retorna a posição da primeira ocorrência do valor especificado |
    | index( ) | Retorna a posição da primeira ocorrência do valor especificado |
    | isalnum( ) | Retorna True se todos os caracteres da string forem alfanuméricos |
    | isalpha( ) | Retorna True se todos os caracteres da string forem alfabéticos |
    | isdecimal( ) | Retorna True se todos os caracteres da string forem decimais |
    | isdigit( ) | Retorna True se todos os caracteres da string forem dígitos |
    | islower( ) | Retorna True se todos os caracteres da string estiverem em minúsculas |
    | isnumeric( ) | Retorna True se todos os caracteres da string forem numéricos |
    | isspace( ) | Retorna True se todos os caracteres da string forem espaços |
    | istitle( ) | Retorna True se a string estiver em formato de título |
    | isupper( ) | Retorna True se todos os caracteres da string estiverem em maiúsculas |
    | join( ) | Junta os elementos de uma lista em uma string |
    | len( ) | Retorna o comprimento da string |
    | lower( ) | Retorna a string em minúsculas |
    | lstrip( ) | Retorna uma versão da string com os espaços à esquerda removidos |
    | partition( ) | Retorna uma tupla onde a string é dividida em três partes |
    | replace( ) | Substitui uma string por outra |
    | rstrip( ) | Retorna uma versão da string com os espaços à direita removidos |
    | split( ) | Divide a string em substrings |
    | strip( ) | Retorna uma versão da string com os espaços removidos |
    | upper( ) | Retorna a string em maiúsculas |

??? Exemplo

    ```python
    x = "Hello, World!"

    print(len(x)) # 13

    print(x.lower()) # hello, world!

    print(x.upper()) # HELLO, WORLD!

    print(x.replace("H", "J")) # Jello, World!

    print(x.split(",")) # ['Hello', ' World!']
    ```

??? Exercício de Fixação

    Crie uma função que receba uma string como parâmetro e retorne a string em maiúsculas.

    ::: Gabarito

        ```python
        def maiusculas(x):
            return x.upper()

        print(maiusculas("hello, world!")) # HELLO, WORLD!
        ```

::: Dica
    Para mais informações sobre strings, consulte a [documentação oficial](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str).

## Listas

Listas são sequências ordenadas de itens, e são utilizadas para armazenar múltiplos itens em uma única variável. Em Python, as listas são declaradas utilizando colchetes. Por exemplo:

```python
fruits = ["apple", "banana", "cherry"]

nomes = ["João", "Maria", "José"]
```

Podemos utilizar diversas funções nativas do Python para manipular listas. Listamos algumas na tabela abaixo.

::: Tabela de Funções para Listas
    | Função | Descrição |
    |--------|-----------|
    | append( ) | Adiciona um elemento ao final da lista |
    | clear( ) | Remove todos os elementos da lista |
    | copy( ) | Retorna uma cópia da lista |
    | count( ) | Retorna o número de elementos com o valor especificado |
    | extend( ) | Adiciona os elementos de uma lista (ou qualquer iterável) ao final da lista |
    | index( ) | Retorna o índice do primeiro elemento com o valor especificado |
    | insert( ) | Adiciona um elemento em uma posição específica |
    | pop( ) | Remove o elemento na posição especificada |
    | remove( ) | Remove o primeiro item com o valor especificado |
    | reverse( ) | Inverte a ordem da lista |
    | sort( ) | Ordena a lista |

??? Exemplo

    ```python
    fruits = ["apple", "banana", "cherry"]

    fruits.append("orange") 
    # ["apple", "banana", "cherry", "orange"]

    fruits.clear() 
    # []

    fruits = ["apple", "banana", "cherry"]

    x = fruits.copy() 
    # ["apple", "banana", "cherry"]

    print(fruits.count("cherry")) 
    # 1

    fruits.extend(["orange", "lemon", "pineapple"]) 
    # ["apple", "banana", "cherry", "orange", "lemon", "pineapple"]

    print(fruits.index("banana")) 
    # 1

    fruits.insert(1, "grape") 
    # ["apple", "grape", "banana", "cherry", "orange", "lemon", "pineapple"]

    fruits.pop(2) 
    # ["apple", "grape", "cherry", "orange", "lemon", "pineapple"]

    fruits.remove("grape") 
    # ["apple", "cherry", "orange", "lemon", "pineapple"]

    fruits.reverse() 
    # ["pineapple", "lemon", "orange", "cherry", "apple"]

    fruits.sort() 
    # ["apple", "cherry", "lemon", "orange", "pineapple"]

    fruits.sort(reverse = True)
    # ["pineapple", "orange", "lemon", "cherry", "apple"]
    ```

??? Exercício de Fixação
    
        Crie uma função que receba uma lista de números como parâmetro e retorne a soma dos números.
    
        ::: Gabarito
    
            ```python
            def soma_lista(x):
                return sum(x)
    
            print(soma_lista([1, 2, 3, 4, 5])) # 15
            ```
::: Dica
    Para mais informações sobre listas, consulte a [documentação oficial](https://docs.python.org/3/tutorial/datastructures.html).

## Tuplas

Tuplas são sequências ordenadas de itens, e são utilizadas para armazenar múltiplos itens em uma única variável. Em Python, as tuplas são declaradas utilizando parênteses. Por exemplo:

```python
fruits = ("apple", "banana", "cherry")

nomes = ("João", "Maria", "José")
```

Apesar de serem muito semelhantes às listas, as tuplas têm uma diferença importante: as tuplas são imutáveis, ou seja, uma vez que uma tupla é criada, não é possível adicionar, remover ou alterar itens na tupla. 
E aí, surge a pergunta: "Por que utilizar tuplas se as listas são mais flexíveis?". A resposta é que, por serem imutáveis, as tuplas são mais rápidas que as listas, e ocupam menos espaço na memória.

Podemos utilizar diversas funções nativas do Python para manipular tuplas. Listamos algumas na tabela abaixo.

::: Tabela de Funções para Tuplas
    | Função | Descrição |
    |--------|-----------|
    | count( ) | Retorna o número de vezes que um valor específico aparece na tupla |
    | index( ) | Retorna o índice do primeiro item com o valor especificado |
    | len( ) | Retorna o comprimento da tupla |
    | max( ) | Retorna o maior item da tupla |
    | min( ) | Retorna o menor item da tupla |
    | sum( ) | Retorna a soma de todos os itens da tupla |
    | sorted( ) | Retorna uma lista ordenada com os itens da tupla |

??? Exemplo

    ```python
    fruits = ("apple", "banana", "cherry")

    print(fruits.count("cherry")) 
    # 1

    print(fruits.index("banana")) 
    # 1
    ```

??? Exercício de Fixação
    
        Crie uma função que receba uma tupla de números como parâmetro e retorne a soma dos números.
    
        ::: Gabarito
    
            ```python
            def soma_tupla(x):
                return sum(x)
    
            print(soma_tupla((1, 2, 3, 4, 5))) # 15
            ```
::: Dica
    Para mais informações sobre tuplas, consulte a [documentação oficial](https://docs.python.org/3/tutorial/datastructures.html#tuples-and-sequences).

## Dicionários

Dicionários são coleções desordenadas de itens, e são utilizados para armazenar pares de chave-valor. Em Python, os dicionários são declarados utilizando chaves. Por exemplo:

```python
person = {
    "name": "John",
    "age": 36,
    "country": "Norway"
}
```

Neste exemplo, *person* é um dicionário que contém três pares de chave-valor. A chave é o nome do item, e o valor é o conteúdo do item.

??? 
    No exemplo acima, quais são as chaves e os valores do dicionário *person*?

    ::: Gabarito
        As chaves do dicionário *person* são "name", "age" e "country", e os valores do dicionário *person* são "John", 36 e "Norway".

Esta é, quiçá, a estrutura de dados que mais se assemelha a um DataFrame, que usaremos muito aqui no IQFC. Por isso, é importante que você entenda bem como manipular dicionários.

Podemos utilizar diversas funções nativas do Python para manipular dicionários. Listamos algumas na tabela abaixo.

::: Tabela de Funções para Dicionários
    | Função | Descrição |
    |--------|-----------|
    | clear( ) | Remove todos os elementos do dicionário |
    | copy( ) | Retorna uma cópia do dicionário |
    | fromkeys( ) | Retorna um dicionário com as chaves e os valores especificados |
    | get( ) | Retorna o valor da chave especificada |
    | items( ) | Retorna uma lista contendo uma tupla para cada par chave-valor |
    | keys( ) | Retorna uma lista contendo as chaves do dicionário |
    | pop( ) | Remove o elemento com a chave especificada |
    | popitem( ) | Remove o último par chave-valor inserido |
    | setdefault( ) | Retorna o valor da chave especificada. Se a chave não existir, insere a chave com o valor especificado |
    | update( ) | Atualiza o dicionário com os pares chave-valor especificados |
    | values( ) | Retorna uma lista contendo os valores do dicionário |

??? Exercício 1

    Crie uma função que receba um dicionário como parâmetro e retorne uma lista contendo as chaves do dicionário.

        ::: Gabarito

            ```python
            def chaves(x):
                return list(x.keys())

            d = {"name": "John", "age": 36, "country": "Norway"}

            print(chaves(d)) # ['name', 'age', 'country']
            ```

??? Exercício 2

    Crie uma função que receba um dicionário como parâmetro e retorne uma lista contendo os valores do dicionário.

        ::: Gabarito

            ```python
            def valores(x):
                return list(x.values())

            d = {"name": "John", "age": 36, "country": "Norway"}

            print(valores(d)) # ['John', 36, 'Norway']
            ```

??? Exercício 3

    Crie uma função que receba um dicionário como parâmetro e retorne uma lista contendo as tuplas chave-valor do dicionário ordenada em ordem alfabética das chaves.

        ::: Gabarito

            ```python
            def itens(x):
                return sorted(list(x.items()))

            d = {"name": "John", "age": 36, "country": "Norway"}

            print(itens(d)) # [('age', 36), ('country', 'Norway'), ('name', 'John')]
            ```
## Estruturas de Repetição

As estruturas de repetição são utilizadas para executar um bloco de código várias vezes. Em Python, temos a estrutura de repetição *while*, que é utilizada para executar um bloco de código enquanto a condição for verdadeira e a estrutura de repetição *for*, que é utilizada para iterar sobre uma sequência de elementos.

* Exemplos de estrutura de repetição *while*:

    ```python
    i = 0
    while i < 6:
        print(i)
        i += 1
    ```

    O código acima irá imprimir os números de 0 a 5. 

    ```python
    fruits = ["apple", "banana", "cherry"]
    i = 0
    while i < len(fruits):
        print(fruits[i])
        i += 1
    ```

    O código acima irá imprimir os elementos da lista *fruits*.

* Exemplos de estrutura de repetição *for*:

    ```python
    for i in range(6):
        print(i)
    ```

    O código acima irá imprimir os números de 0 a 5.

    ```python
    fruits = ["apple", "banana", "cherry"]
    for x in fruits:
        print(x)
    ```

    O código acima irá imprimir os elementos da lista *fruits*.

??? Exercício 4
    
    Crie uma função que receba um número como parâmetro e imprima todos os números de 0 até o número.

        ::: Gabarito

            ```python
            def imprime_ate(x):
                for i in range(x):
                    print(i)

            imprime_ate(6)
            # 0
            # 1
            # 2
            # 3
            # 4
            # 5
            ```

??? Exercício 5

    Crie uma função que receba uma lista de nomes como parâmetro e imprima todos os nomes da lista.

        ::: Gabarito

            ```python
            def imprime_nomes(x):
                for nome in x:
                    print(nome)

            nomes = ["João", "Maria", "José"]

            imprime_nomes(nomes)
            # João
            # Maria
            # José
            ```

??? Exercício 6

    Crie uma função que receba um dicionário como parâmetro e imprima todos os pares chave-valor do dicionário.

        ::: Gabarito

            ```python
            def imprime_dicionario(x):
                for chave, valor in x.items():
                    print(chave, valor)

            d = {"name": "John", "age": 36, "country": "Norway"}

            imprime_dicionario(d)
            # name John
            # age 36
            # country Norway
            ```

??? Exercício 7

    Crie uma função que receba uma string como parâmetro e imprima cada caractere da string.

        ::: Gabarito

            ```python
            def imprime_caracteres(x):
                for caractere in x:
                    print(caractere)

            imprime_caracteres("Hello, World!")
            # H
            # e
            # l
            # l
            # o
            # ,
            #  
            # W
            # o
            # r
            # l
            # d
            # !
            ```

??? Exercício 8

    Crie uma função que receba um dicionário como parâmetro e imprima todos os valores do dicionário.

        ::: Gabarito

            ```python
            def imprime_valores(x):
                for valor in x.values():
                    print(valor)

            d = {"name": "John", "age": 36, "country": "Norway"}

            imprime_valores(d)
            # John
            # 36
            # Norway
            ```

## Conjuntos

Conjuntos são coleções desordenadas de itens, e são utilizados para armazenar múltiplos itens em uma única variável. Em Python, os conjuntos são declarados utilizando chaves. Por exemplo:

```python
fruits = {"apple", "banana", "cherry"}

nomes = {"João", "Maria", "José"}
```

Os conjuntos não permitem itens duplicados, ou seja, se tentarmos adicionar um item que já existe no conjunto, o item não será adicionado.
E, novamente, surge a pergunta: "Por que utilizar conjuntos se as listas são mais flexíveis?". A resposta é que, por não permitirem itens duplicados, os conjuntos são mais rápidos que as listas, e ocupam menos espaço na memória. E, então, surge outra pergunta: "Por que utilizar conjuntos se as tuplas são mais rápidas e ocupam menos espaço na memória?". A resposta é que os conjuntos são mais flexíveis que as tuplas, e permitem adicionar e remover itens.

Podemos utilizar diversas funções nativas do Python para manipular conjuntos. Listamos algumas na tabela abaixo.

::: Tabela de Funções para Conjuntos
    | Função | Descrição |
    |--------|-----------|
    | add( ) | Adiciona um item ao conjunto |
    | clear( ) | Remove todos os itens do conjunto |
    | copy( ) | Retorna uma cópia do conjunto |
    | difference( ) | Retorna um conjunto contendo a diferença entre dois ou mais conjuntos |
    | difference_update( ) | Remove os itens do conjunto que estão em outro conjunto |
    | discard( ) | Remove o item especificado |
    | intersection( ) | Retorna um conjunto contendo a interseção entre dois ou mais conjuntos |
    | intersection_update( ) | Remove os itens do conjunto que não estão em outro conjunto |
    | isdisjoint( ) | Retorna True se nenhum item do conjunto A estiver no conjunto B |
    | issubset( ) | Retorna True se todos os itens do conjunto A estiverem no conjunto B |
    | issuperset( ) | Retorna True se todos os itens do conjunto B estiverem no conjunto A |
    | pop( ) | Remove um item aleatório do conjunto |
    | remove( ) | Remove o item especificado |
    | symmetric_difference( ) | Retorna um conjunto contendo a diferença simétrica entre dois conjuntos |
    | symmetric_difference_update( ) | Insere a diferença simétrica entre dois conjuntos no conjunto |
    | union( ) | Retorna um conjunto contendo a união entre dois ou mais conjuntos |
    | update( ) | Insere os itens de um conjunto em outro conjunto |

??? Exercício 9

    Crie uma função que receba dois conjuntos como parâmetros e retorne a união entre os conjuntos.

        ::: Gabarito

            ```python
            def uniao(x, y):
                return x.union(y)

            a = {1, 2, 3}
            b = {4, 5, 6}

            print(uniao(a, b)) # {1, 2, 3, 4, 5, 6}
            ```
        
??? Exercício 10
    
        Crie uma função que receba dois conjuntos como parâmetros e retorne a interseção entre os conjuntos.
    
            ::: Gabarito
    
                ```python
                def intersecao(x, y):
                    return x.intersection(y)
    
                a = {1, 2, 3, 4, 5}
                b = {4, 5, 6, 7, 8}
    
                print(intersecao(a, b)) # {4, 5}
                ```

??? Exercício 11
    
        Crie uma função que receba dois conjuntos como parâmetros e retorne a diferença entre os conjuntos.
    
            ::: Gabarito
    
                ```python
                def diferenca(x, y):
                    return x.difference(y)
    
                a = {1, 2, 3, 4, 5}
                b = {4, 5, 6, 7, 8}
    
                print(diferenca(a, b)) # {1, 2, 3}
                ```
## Manipulação de Arquivos

A manipulação de arquivos é uma tarefa comum em programação. Em Python, podemos manipular arquivos utilizando funções nativas. Listamos algumas abaixo.

| Função | Descrição |
|--------|-----------|
| open( ) | Abre um arquivo |
| close( ) | Fecha um arquivo |
| read( ) | Lê o conteúdo de um arquivo |
| readline( ) | Lê a linha atual de um arquivo |
| readlines( ) | Lê todas as linhas de um arquivo |
| write( ) | Escreve no arquivo |
| append( ) | Adiciona ao arquivo |

??? Exemplo

    ```python
    f = open("demofile.txt", "r")
    print(f.read())
    f.close()
    ```

    O código acima irá abrir o arquivo *demofile.txt*, ler o conteúdo do arquivo e imprimir o conteúdo do arquivo.

    ```python
    f = open("demofile.txt", "a")
    f.write("Now the file has more content!")
    f.close()
    ```

    O código acima irá abrir o arquivo *demofile.txt*, adicionar o texto "Now the file has more content!" ao final do arquivo e fechar o arquivo.

Além das funções nativas, podemos utilizar o comando *with* para abrir e manipular arquivos. O comando *with* garante que o arquivo será fechado corretamente após a manipulação, por isso, é uma boa prática utilizá-lo.

??? Exemplo

    ```python
    with open("demofile.txt", "r") as f:
        print(f.read())
    ```

    O código acima irá abrir o arquivo *demofile.txt*, ler o conteúdo do arquivo e imprimir o conteúdo do arquivo, e garantir que o arquivo será fechado corretamente após a manipulação.

??? Exercício 12
    
        Crie um arquivo chamado *demofile.txt* e adicione o texto "Hello, World!" ao arquivo.
    
            ::: Gabarito
    
                ```python
                with open("demofile.txt", "w") as f:
                    f.write("Hello, World!")
                ```

??? Exercício 13
        
            Crie uma função que receba o nome de um arquivo como parâmetro e retorne o conteúdo do arquivo.
        
                ::: Gabarito
        
                    ```python
                    def le_arquivo(x):
                        with open(x, "r") as f:
                            return f.read()
    
                    print(le_arquivo("demofile.txt")) # Hello, World!
                    ```

## Comentários

Finalmente, mas não menos importante, vamos falar sobre comentários. Comentários são utilizados para explicar o código e torná-lo mais legível. Em Python, os comentários são iniciados com o caractere *#*. Por exemplo:

```python
# This is a comment
```

Comentários de várias linhas são iniciados e terminados com três aspas simples ou duplas. Por exemplo:

```python
"""
This is a comment
written in
more than just one line
"""
```

Pode parecer besteira, mas é muito importante que você comente o seu código. Isso vai te ajudar a entender o que você fez quando você voltar a olhar para o código depois de um tempo, e vai ajudar outras pessoas a entenderem o que você fez. No entanto, é importante que você não exagere nos comentários, pois comentários em excesso podem tornar o código mais difícil de ler.

## O que aprendemos?

    Neste tutorial, aprendemos os primeiros passos para começar a programar em Python. Percorremos assuntos básicos, como o que são e como declarar variáveis, operadores aritméticos, operadores de comparação, operadores lógicos, estruturas condicionais, estruturas de repetição, funções, strings, listas, tuplas, dicionários, conjuntos, e manipulação de arquivos.

    Além disso, aprendemos a utilizar funções nativas do Python, e a manipular arquivos.

    Por fim, aprendemos a utilizar comentários para explicar o código e torná-lo mais legível.

    Agora que você já sabe os primeiros passos para começar a programar em Python, está pronto para seguir para o próximo tutorial, onde vamos aprender a utilizar a principal biblioteca de Data Science em Python, o Pandas.

    Até lá!

![pandinha mt suav](panda.gif)
"""