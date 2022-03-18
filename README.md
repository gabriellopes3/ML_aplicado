# Machine Learning Aplicado ao Mercado Financeiro
O seguinte projeto tem como objetivo construir um modelo de Machine Learning aplicado a dados contábeis e financeiros com o propósito de montar uma carteira de ações rentável montada pelo modelo. Para isso, foram utilizados dados fornecidos em: https://www.youtube.com/watch?v=wz5_MOWYias, principal referência do projeto. 



# Divisão do Projeto
O trabalho foi separado em diversas etapas, baseado na metodologia CRISP-DM com um rigor científico e métodos experimentais, mas sem abrir mão da visão de negócio e objetivo final de agregar valor e resolver um problema com uma solução de Machine Learning robusta. Dentre essas divisões do projeto, vale a pena destacar:
### Tratamento dos dados
Etapa onde os dados foram importados de fontes diversas para o ambiente de trabalho utilizado (Jupyter Lab), concatenado e tratados, com os principais problemas encontrados em bases de dados reais, como por exemplo, valores faltantes, colunas duplicadas, datas bagunçadas, etc.

![df_print](https://user-images.githubusercontent.com/83516816/159029032-16e9c9d2-b7fc-4144-8464-ee0a6c3e7ae9.png)

### Análise Exploratória Individual
Onde foram definidas funções com o intúito de automatizar uma análise estatística dos principais indicadores de cada empresa individualmente, além de gerar comparações entre as mesmas. Essa etapa é importante para o caso de algum técnico querer um relatório individualizado acerca de uma empresa específica ao longo do tempo, comparar duas companhias ou até mesmo de comparar os retornos de uma companhia com o índice Bovespa.

#### Relatório Individual: 

![graficos1](https://user-images.githubusercontent.com/83516816/159033913-c7f35baa-44c4-4556-b501-102b9f2ae3bc.png)

#### Comparativo de Retornos:
![graficos2](https://user-images.githubusercontent.com/83516816/159033915-e921b3fc-97ac-4aba-b6a6-4a06d9b2575a.png)

### Preparação Dos Dados
Nessa etapa é onde deixaremos os dados degustáveis para serem consumidos por um algorítmo de ML. aqui iremos, além de juntar todos os dados em um único DataFrame, fazer alguns tratamentos neles, como por exemplo:
- Transformar os dados em variações: Para o nosso problema é mais importante saber as variações percentuais do que as variações nominais em dados contábeis, afinal, o mesmo valor nominal que pode ser desastroso para uma empresa grande, pode ser excelente para outra de menor porte. Transformar os dados em variações irá ajudar nosso modelo a identificar melhores padrões.
- Criação de rótulos (o "gabarito"): Para o aprendizado supervisionado, precisamos de variáveis explicativas (X) e uma variável alvo (y). Em problemas de classificação, o y assume valores de classe que são ocasionados em docorrência de algumas características das variáveis preditoras. Para podermos modelar este problema, precisamos criar essa classe de forma que faça sentido e siga algumas regras, atribuindo um valor onde era vantajoso comprar uma ação, e outro valor quando era melhor vendê-la, preparando assim os dados para serem modelados em um problema de classificação com as técnicas adequadas.

### Análise Exploratória na Base Completa
Essa parte é importante para entender a peculiaridades dos dados após os mesmos terem sido tratados e agrupados em um único DataFrame. Por se tratarem de dados contábeis, um problema bastante previsível é o de alta multicolinearidade. Embora algorítmos de árvore sejam robustos contra esse problema, colocar dados altamente correlacionados a ponto de serem redundantes em um modelo é contraprodutivo, pois aumenta a complexidade do mesmo sem nenhum ganho de valor agregado. Portanto, é necessário analisar e tratar essa questão. 

### Aplicando Técnincas de Machine Learning 
Aqui é onde iremos finalmente fazzer o grande experimento do projeto, onde testaremos uma lista de modelos de classificação, tendo como baseline um modelo "Dummy" e avaliaremos cada um com uma validação cruzada de 5 folds e utilizando a Precision como principal métrica de avaliação, mas avaliando também outras métricas como possíveis critérios de desempate e para ter outras perspectivas acerca do modelo avaliado. 

![modelos](https://user-images.githubusercontent.com/83516816/159055376-cf307fcf-0836-4667-8a93-d7bcdb597b66.png)

Após escolhido o modelo, iremos aprimorá-lo fazendo seu Hyperparameter Fine Tuning, técninca utilizada para encontrar as melhores combinações de hiperparâmetros.

![plot_convergence](https://user-images.githubusercontent.com/83516816/159056827-69361b3b-c987-426a-9d69-476357c6e606.png)

Após definido o melhor modelo com os melhores hiperparâmetros, iremos partir para as Features,utilizando todo o poder do Scikit-learn para encontrar o número ideal de Features e testando as combinações na prática, criando um verdadeiro experimento de Machine Learning e Feature Selection a fim de chegar no melhor resultado possível.

### Testando a Solução e Traduzindo o Resultado Para Métricas de Negócio
No fim do projeto, realizamos o teste da solução no último trimestre, que não foi utilizado para treinar e nem validar o modelo, atingindo um retorno (lucro) de 5,2% sobre o capital invesstido, contrastando com o retorno negativo de -2,24%.



