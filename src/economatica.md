<a href="home.html">Curso de Iniciação IQFC</a>

Economatica
======

**Economatica** é a ferramenta que será utilizada para o download das bases de dados que utilizaremos em nossas estratégias.

Para utlização da mesma é necessário que se possua licença ativa, porém essa licença já foi adquirida pelo Insper para nosso uso e pode ser acessada quando logado na rede do Insper ou através de VPN, como será demonstrado ao final do tutorial.

Acesso e Login
------

1. Acesse o site do [Economatica](https://www.economatica.com/).

!!!
Lembre-se de estar logado na rede do Insper
!!!

2. Clique em *Login* no canto superior direito da tela.

3. Seleciona a opção *Plataforma Economatica*.

![](economatica1.png)

4. Insira seu email do Insper e clique em Login.

5. Aguarde a tela de carregamento. (Pode demorar um pouco)

Baixando um Banco de Dados
------

A título de exemplo iremos realizar o download de uma base de dados de ROE (Retorno sobre o Patrimônio Líquido) de empresas listadas na B3.

1. Caso não esteja com a seguinte janela aberta, clique em *abrir nova janela* no canto superior esquerdo.

![](economatica0.png)

2. Primeiramente é necessário selecionar os dados requisitados e para tal, clique em *Screening* na ala de *Ferramentas Básicas*.

3. Em tal janela escolheremos o tipo de ativo que desejamos analisar, no nosso caso iremos em *Todos os Ativos* e em seguida abriremos os dados da ala *Screenig sem Filtros* para selecionarmos todos os ativos e filtrarmos na mão. Caso se deseje futuramente acessar uma filtragem já pronta basta entrar na aba *Ações* e em seguida *Básico*.

4. Após selecionada iremos primeiramente realizar a filtragem por tipo de ativo, para acessarmos somente ações, portanto clique em *Criar Coluna*.

5. Na aba de criação de coluna iremos acessar os *dados cadastrais*, e em *principais itens* selecionar *Tipo de Ativo*, então clicar em *OK*.

6. Da mesma forma adicionaremos um filtro por bolsa/fonte, repetindo os mesmos passos em *dados cadastrais*, *Ações (bandeira do Brasil)* e *Bolsa/Fonte*. 

7. Agora com as colunas adicionadas aplicaremos nossos filtros. Para tal clique com o botão direito na coluna *Tipo de Ativo* e selecione *inserir filtro baseado nessa coluna*.

8. Na aba de filtros selecione na última posição da linha *Tipo de Ativo Igual* a opção *Ação* para que somente ações sejam selecionadas na base de dados.

9. Repita o mesmo processo para a coluna *Bolsa/Fonte* e selecione *America Latina - BRA Brasil - Bovespa*.

10. Com nossos filtros prontos, iremos buscar nossos dados de interesse, no caso o ROE. Para tal clique novamente em *abrir nova janela* com a tela de Screening ainda aberta e selecione *Matrixx*

11. Na tela de Matrixx, clique em *Criar Coluna* e selecione *Indicadores Financeiros* e procure por uma das variações de *ROE*.

12. Clique em *OK* 

13. Novamente na tela de Maatrix, agora com todos os dados selecionados clique no icone de *três listras* e seleciona *Exportar (XLS, XLSX, PDF, TXT, CSV, JSON)*.

14. Selecione as opções *CSV* (para um arquivo mais leve), *Salvar arquivo com nome* e escolher o nome desejado, *Para todos ativos da janela Screening*, *Todos ativos em um único ativo*

15. Confirme o download e aguarde o mesmo ser concluído (Pode demorar um pouco).

Acesso via VPN
------

Caso esteja fora da rede do Insper, é necessário o uso de uma VPN para acessar a Economatica. Para tal siga os seguintes passos:

