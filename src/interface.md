<a href="home.html">Curso de Iniciação IQFC</a>

Interface de Desenvolvimento
======

!!!
Esse tutorial foi pensado, principalmente, nos alunos de Administração e Economia do Insper, que, provavelmente, não tiveram contato prévio com o Visual Studio Code e um contato muito raso com o Python.
!!!

Neste tutorial, vamos aprender a instalar o Visual Studio Code e o Python, a configurar o ambiente de desenvolvimento para começar a programar em Python e a instalar os frameworks, bibliotecas e extensões necessárias para o andamento das aulas.

## Instalação do Visual Studio Code

!!! 
Se você já tem o Visual Studio Code instalado, você pode pular para a próxima seção.
!!!

O Visual Studio Code é um editor de código-fonte desenvolvido pela Microsoft, que pode ser utilizado para desenvolvimento de software em diversas linguagens, incluindo Python. O editor é gratuito e de código aberto, e possui diversas funcionalidades que facilitam o desenvolvimento de código, como realce de sintaxe, finalização de código, depuração, controle de versão, entre outros.

<div align="center">
    <img src="vscode.webp" alt="VScode icon" width="200"/>
</div>

Para instalar o Visual Studio Code, acesse o [site oficial](https://code.visualstudio.com/) e clique no botão de download. O site irá identificar automaticamente o sistema operacional que você está utilizando e oferecer o download da versão correta. Após o download, execute o instalador e siga as instruções para instalar o Visual Studio Code.

## Instalação do Python

!!! 
Se você já tem o Python instalado, você pode pular para a próxima seção.
!!!

O Python é uma linguagem de programação de alto nível, interpretada, de script, imperativa, orientada a objetos, funcional, de tipagem dinâmica e forte. É uma das linguagens mais populares para desenvolvimento de software, e é amplamente utilizada em diversas áreas, aqui, usaremos para análise de dados financeiros.

<div align="center">
    <img src="python.png" alt="Python icon" width="200"/>
</div>

Para instalar o Python, acesse o [site oficial](https://www.python.org/) e clique no botão de download. O site te oferecerá a versão mais recente do Python, e te dará diferentes opções de sistemas operacionais. Escolha a opção que corresponde ao seu sistema operacional e clique no link para baixar o instalador.

??? Exemplo
    Se você estiver utilizando Windows de 64 bits, você deve baixar a versão de 64 bits do Python. Você clicará no link ***Windows embeddable package (64-bit)*** e o download começará automaticamente.

## Configuração do ambiente de desenvolvimento

Após as instalações, abra o Visual Studio Code. A primeira vez que você abrir o editor, ele irá exibir uma tela de boas-vindas com algumas opções. Algo muito semelhante à tela seguir:

<div align="center">
    <img src="vscode_welcome.png" alt="VScode welcome" width="600"/>
</div>

Clique em ***"Open Folder..."*** ou ***"Abrir Pasta..."*** e selecione a pasta onde você deseja criar o seu projeto. Se você ainda não tem uma pasta para o seu projeto, crie uma nova pasta em um local de sua preferência e selecione essa pasta.

## Instalação de frameworks, bibliotecas e extensões

Para o andamento das aulas, utilizaremos alguns frameworks e bibliotecas que precisam ser instalados. Para isso, abra o terminal integrado do Visual Studio Code. Para abrir o terminal, clique em ***"Terminal"*** na barra de menu superior e depois em ***"New Terminal"***. O terminal será aberto na parte inferior do editor.

!!!
Se na barra de menu superior não aparecer a opção ***"Terminal"***, clique em ***"View"*** e depois em ***"Terminal"*** e siga os passos anteriores.
!!!

Sua tela deve estar parecida com a imagem a seguir:
![alt text](vs_terminal.png)

Dessa formma, conseguiremos instalar as bibliotecas necessárias para o andamento das aulas. No entanto, é possível que nem todos vocês estejam no mesmo sistema operacional, e, por isso, a instalação das bibliotecas pode variar. Antes precisamos checar se o Python foi instalado corretamente. Para isso, digite o seguinte comando no terminal e pressione ***Enter***:

```python
python --version
```

Se o Python foi instalado corretamente, o terminal irá exibir a versão do Python que foi instalada. 

??? Exemplo
    Se o Python foi instalado corretamente, o terminal irá exibir algo semelhante a:
    ```python
    Python 3.9.5
    ```
    Se o Python não foi instalado corretamente, o terminal irá exibir uma mensagem de erro.

Agora, vamos o instalar o gerenciador de pacotes do Python, o ***pip***. O ***pip*** é um sistema de gerenciamento de pacotes utilizado para instalar e gerenciar pacotes de software escritos em Python. Para instalar o ***pip***, digite o seguinte comando no terminal e pressione ***Enter***:

```python
python -m ensurepip --default-pip
```

Após a instalação do ***pip***, vamos instalar as bibliotecas necessárias para o andamento das aulas. Para isso, digite o seguinte comando no terminal e pressione ***Enter***:

```python
pip install pandas numpy matplotlib quantstats datetime notebook
```

Após a instalação das bibliotecas, vamos instalar as extensões necessárias para o andamento das aulas. Para isso, clique no ícone de extensões na barra lateral esquerda do editor (o ícone de extensões é representado por quatro quadrados sobrepostos) ou pressione ***Ctrl+Shift+X***. Na barra de pesquisa que aparecer, digite ***Python*** e pressione ***Enter***. A extensão ***Python***, desenvolvida pela Microsoft, deve aparecer como a primeira opção. Clique no botão ***"Install"*** para instalar a extensão.

Feito isso, faça o mesmo procedimento para instalar a extensão ***Jupyter***. Na barra de pesquisa, digite ***Jupyter*** e pressione ***Enter***. A extensão ***Jupyter***, desenvolvida pela Microsoft, deve aparecer como a primeira opção. Clique no botão ***"Install"*** para instalar a extensão.

Com isso, o ambiente de desenvolvimento está configurado e pronto para ser utilizado. Agora, você já pode começar a programar em Python e acompanhar as aulas do curso.

![gatin dboa](gatin_dboa.png)
