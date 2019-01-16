# Predicting_Default_Risk

## Resumo do projeto
Você é um agente de crédito em um pequeno banco novo (em operação há dois anos) que precisa de uma solução eficiente para classificar clientes novos entre aprovados e não aprovados para um empréstimo. Você utilizará uma série de modelos de classificação para descobrir o melhor modelo e fornecer ao seu gerente uma lista de clientes aptos a receber empréstimos.

## Passo 1: Entendimento de negócios e dados
Fornecer uma explicação das principais decisões que precisam ser feitas. (Limite de 250 palavras)

#### 1.	Que decisões precisam ser tomadas?

A decisão que precisa ser tomada neste problema de negócio é se aprovamos ou não um crédito para os novos clientes, ou seja, precisamos classificar os novos clientes em duas categorias, APROVADO ou NÃO APROVADO.

#### 2.	Que dados são necessários para informar essas decisões?

Precisamos ter os dados do passado para podermos treiná-los e aplicar o melhor modelo na base nova. Os dados do passado estão na planilha *credit-data-training.xlsx* e a planilhas que usaremos para aplicar o modelo é *customers-to-score*. Em ambas planilhas, precisaremos dos seguintes campos *Account-Balance, Age-years, Credit-Amount, Credit-Application-Result, Duration-of-Credit-Month, Instalment-per-cent,Length-of-current-employment, Most-valuable-available-asset, No-of-Credits-at-this-Bank, Payment-Status-of-Previous-Credit, Purpose, Type-of-Apartment and Value-Savings-Stocks*

#### 3.	Que tipo de modelo (Contínuo, Binário, Não-Binário, Time-Series) precisamos usar para ajudar a tomar essas decisões?

Para este problema, precisamos usar um Modelo Binário, sendo que a variável resposta é SIM ou NÃO para a aprovação do crédito ao cliente.

## Passo 2: Construindo o Conjunto de Treinamento

#### 1.	Em seu processo de limpeza, quais campos você removeu ou imputou? Por favor, justifique por que você removeu ou imputou esses campos. As visualizações são incentivadas.

Durante o processo de limpeza, os campos abaixo foram removidos do nosso data set.

*Concurrent-Credits, Occupation* - Ambos campos têm apenas 1 categoria como resultado.

*Guarantors, Foreign Workers, No. of Dependents* - Campos com baixa variabilidade.

*Phone Number* - Variável que não é necessária para a criação dos modelos, nenhuma importância.

*Duration in Current Address* - Campo com um índice alto de missing values, 69%.

Em relação a input de dados, achei necessário fazer a inclusão de informações no campo *Age*, visto que analisamos e percebemos um missing values de 2%. A premissa utilizada no input destes dados foi a *Mediana*, pois este indicador minimiza o efeito, se ussássemos *média*, de idades muito altas, como por exemplo >70 anos.

## Passo 3: Treinar seus Modelos de Classificação

Primeiro, crie suas amostras de Estimação e Validação, onde 70% de seu conjunto de dados deve ir para Estimativa e 30% de seu conjunto de dados inteiro deve ser reservado para Validação. Defina a Semente Aleatória como 1.

Crie todos os modelos a seguir: regressão logística, árvore de decisão (decision trees), modelo de floresta (forest model), e boosted model. 

Responda a estas perguntas para cada modelo criado:

#### 1.	Quais variáveis preditoras são significativas ou as mais importantes? Por favor, mostre os p-values ou gráficos de importância para todas as suas variáveis de previsão.

##### a. Logistic Regression + Step Wise

![lr_01](https://user-images.githubusercontent.com/34245933/51278921-0d104d00-19c3-11e9-82f9-e58d3cf64ae2.PNG)

##### b. Decision Tree

##### c. Forrest Model

##### d. Boosted Model


#### 2.	Valide seu modelo em relação ao conjunto de Validação. Qual foi a porcentagem geral de precisão? Mostre a matriz de confusão. Existe algum viés (bais) nas previsões do modelo?

## Step 4: Escrita

Decidir sobre o melhor modelo e pontuação de seus novos clientes. Para revisar a consistência, se Score_Creditworthy for maior que Score_NonCreditworthy, a pessoa deve ser rotulada como "Creditworthy"

#### 1.	Qual modelo você escolheu usar? Por favor, justifique sua decisão usando apenas as seguintes técnicas:

##### a. Precisão geral contra o seu conjunto de validação

##### b. Exatidão dentro dos segmentos "Creditworthy" e "Non-Creditworthy"

##### c. Gráfico ROC

##### d. Bias nas Matrizes de Confusão

Nota: Lembre-se de que seu chefe só se preocupa com a precisão das previsões para os segmentos Credityworth e Non-Creditworthy.

#### 2.	Quantos indivíduos são bons pagadores?

