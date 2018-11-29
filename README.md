# <i>Finder de receitas da Vovó</i>
Projeto final da disciplina de Megadados - Insper 6º Semestre

<strong> Por Alexande Young, Jean Luca e Pedro de la Peña </strong>

### Introdução

   Todas as interações realizadas na rede geram informações que são trasnmitidas e armazenadas em diversos pontos da Internet. Alguns sites como o [Common Crawl](http://commoncrawl.org/) coletam informações públicas de páginas da web ao longo de um determinado período de tempo (na maioria dos casos isto ocorre mensalmente) e depois disponibilizam estas informações para download em seu site, para que qualquer um que esteja interessado possa realizar análises sobre os dados e encontrar soluções inteligentes para algum problema. Contudo, caso um usuário queira iterar sobre todos os dados, por mais poderosa que sua máquina seja, ele não conseguirá faze-lo localmente, pois os dados podem possuir mais de um petabyte de informação. Desta forma, para realizar análises e evitar a sobrecarga de uma máquina, é preciso utilizar várias máquinas operando em paralelo sobre os dados, fazendo com que a análise seja possível e relativamente mais rápida dependendo do número de máquinas utilizadas, suas configurações e o tamanho dos dados a serem analisados.

Para este e outros fins, existem sites que fornecem serviços de <i>public cloud</i>, onde um usuário pode executar máquinas virtuais dos mais diversos tipos e configurações em <i>clusters</i>, como é o caso da [Amazon](https://aws.amazon.com/).

### O projeto

O grupo pensou em ajudar suas vós, que não estão muito acostumadas com o ambiente da internet porém que adoram fazer receitas deliciosas durante o ano todo (com excessão do Natal quando resolvem colocar uva-passa em tudo). Sendo assim, desejou-se calcular quantos sites de receita existem na web Brasil (site pt-br) para que nossas vovós sempre tenham receitas gostosas para fazer. 

Inicialmente, foi carregado um fragmento do Crawl da Web Brasil (disponibilizado pelo professor) no Spark, que estava sendo rodado em uma máquina m4.xlarge como master e uma m4.large como worker.

![loading](loading)

Com o intuito de classificar sites automaticamente como "site de receita" e "outros", o grupo selecionou 100 amostras aleatórias do fragmento, porém que continham a palavra "receita" em algum ponto do site. A partir desses dados, o grupo analisou manualmente cada um desses 100 sites localmente em um [Jupyter Notebook](/manualfilter.ipynb), para confirmar quantos realmente eram de receita e quantos eram <i>falsos positivos</i>. A partir dessa análise, foram contados 53 sites de receita para 47 falsos positivos e uma máscara de bits foi gerada com base nessas informações.

![pythonnotebook](aa)

A partir da máscara de bits, foi treinada uma inteligencia artificial básica que decidia se um site era de receitas ou não com base em seu conteúdo. Foram ignoradas palavras com mais de 15 caracteres e também pequenas para não considerar palavras de conexão (e, a, um, ou, de). As primeiras 100 palavras do site foram consideradas para a análise, pois se o site é realmente de receitas, palavras chave relacionadas ao assunto estarão dispostas logo no começo da página. (explicar um pouco mais a fundo o algoritmo)

![spark1](aa)






