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

#### 2.	Valide seu modelo em relação ao conjunto de Validação. Qual foi a porcentagem geral de precisão? Mostre a matriz de confusão. Existe algum viés (bais) nas previsões do modelo?

### a. Logistic Regression + Step Wise

* Considerando que a variável *Credit-Application-Result* é nossa variável target, podemos dizer que as variáveis *Account-Balance, Purpose e Credit-Amount* são as variáives preditoras com maior significância, isso pois como vemos na Figura 1 estas variáveis tem p-valor inferior à 0.05.

* O nosso modelo tem uma acurácia boa, de 76.0%, conforme Figura 2. Enquanto temos uma acurácia ainda maior para *Creditworthy* de 87.62%, porém encontramos que o resultado para *Non-Creditworthy* pode estar enviesado, pois o resultado é muito baixo, apenas 48.89%.

![lr_01](https://user-images.githubusercontent.com/34245933/51278921-0d104d00-19c3-11e9-82f9-e58d3cf64ae2.PNG)

*Figura 1: Report Logistic Regression*

![lr_02](https://user-images.githubusercontent.com/34245933/51280270-62019280-19c6-11e9-9410-109640337f03.PNG)

*Figura 2: Model Comparison Report for Stepwise Logistic Regression*

### b. Decision Tree

* Considerando que a variável *Credit-Application-Result* é nossa variável target, podemos dizer que as variáveis *Account-Balance, Value-Saving-Stocks e Duration-of-Credit-Month* são as variáives preditoras com maior significância, isso pois como vemos na Figura 3 estas variáveis estão como mais importantes na *Variável Importância*.

* O nosso modelo tem uma acurácia boa, de 79.1% (melhor que o modelo anterior), conforme Figura 4. Para as variáveis *Creditworthy e Non-Creditworthy* temos o mesmo cenário do modelo anterior, uma alta acurácia para *Creditworthy*, de 86.67% e baixa para *Non-Creditworthy*, de apenas 46.67%. Portanto, também podemos enviesar a variável *Non-Creditworthy*.

![dt_01](https://user-images.githubusercontent.com/34245933/51281191-d5a49f00-19c8-11e9-9528-0f1d18fc6881.PNG)

*Figura 3: Decision Tree, Variable Importance and Confusion Matrix*

![dt_02](https://user-images.githubusercontent.com/34245933/51281233-f40a9a80-19c8-11e9-9b54-c52c3c08032f.PNG)

*Figura 4: Model Comparison Report for Decision Tree*

### c. Forest Model

* Considerando que a variável *Credit-Application-Result* é nossa variável target, podemos dizer que as variáveis *Credit-Amount, Age-Years e Duration-of-Credit-Month* são as variáives preditoras com maior significância, isso pois como vemos na Figura 5 estas variáveis estão como mais importantes no gráfico de *Variable Importance Plot*.

* Este modelo mostra uma acurácia geral maior que todos os outros modelos até aqui analisados, de 80.0% conforme Figura 5. Como um alta acurácia para *Creditworthy*, de 96.19% e novamente baixa para *Non-Creditworthy*, de apenas 42.22%. Portanto, também temos enviesamento da variável *Non-Creditworthy*.

![fm_01](https://user-images.githubusercontent.com/34245933/51282204-9cb9f980-19cb-11e9-843f-2b3276a93619.png)

*Figura 5: Percentage Error for Different Number of Trees and Variable Importance Plot*

![fm_02](https://user-images.githubusercontent.com/34245933/51282268-c96e1100-19cb-11e9-8f46-b7b8c16ceb1e.png)

*Figura 6: Model Comparison Report for Forest Model*

### d. Boosted Model

* Considerando que a variável *Credit-Application-Result* é nossa variável target, podemos dizer que as variáveis *Account-Balance, Credit-Amount e Payment-Status-of-Previous-Credit* são as variáives preditoras com maior significância, isso pois como vemos na Figura 7 estas variáveis estão como mais importantes no gráfico de *Variable Importance Plot*.

* Este modelo tem uma acurácia geral de 78.67%, conforme Figura 8. Como um alta acurácia para *Creditworthy*, de 96.16% e novamente baixa para *Non-Creditworthy*, de apenas 37.78%. Também temos enviesamento da variável *Non-Creditworthy*.

![bm_01](https://user-images.githubusercontent.com/34245933/51282301-e1459500-19cb-11e9-847a-b0dec436118b.PNG)

*Figura 7: Variable Importance Plot for Boosted Model*

![bm_02](https://user-images.githubusercontent.com/34245933/51282325-f3bfce80-19cb-11e9-8b91-0ef91f49e1a5.PNG)

*Figura 8: Model Comparison Report for Boosted Model*

## Step 4: Escrita

Decidir sobre o melhor modelo e pontuação de seus novos clientes. Para revisar a consistência, se Score_Creditworthy for maior que Score_NonCreditworthy, a pessoa deve ser rotulada como "Creditworthy"

#### 1.	Qual modelo você escolheu usar? Por favor, justifique sua decisão usando apenas as seguintes técnicas:

O modelo escolhido como melhor fit nos dados disponíveis foi o modelo de *Forest Model* pois conta com uma maior acurácia em relação aos outros modelos, conforme podemos ver na Figura 9.

##### a. Precisão geral contra o seu conjunto de validação

![mc_01](https://user-images.githubusercontent.com/34245933/51283525-99c10800-19cf-11e9-83dd-b81f7f06b31c.png)

*Figura 9: Model Comparison Report for all 4 classification models*

A precisão geral foi a maior em comparação com os outros modelos, de 80.0%.

##### b. Exatidão dentro dos segmentos "Creditworthy" e "Non-Creditworthy"

O segmento *Creditworthy* também conta com uma alta acurácia no modelo *Forest Model* de 96.16%, maior em comparação com os outros modelo. Enquanto o segmento *Non-Creditworthy* não demonstra muita acurácia, apenas de 42.22% porém um dos maiores em relação aos outros modelos.

##### c. Gráfico ROC

![mc_02](https://user-images.githubusercontent.com/34245933/51283506-8c0b8280-19cf-11e9-8819-44cc750e9599.png)

*Figura 10: ROC curve for all 4 classification models*

##### d. Bias nas Matrizes de Confusão

Analisando as matrizes de confusão, percebemos que a variável *Creditworthy* ficou bem alinhada com a modelagem, quase em sua maioria o modelo acertou. Enquanto tivemos uma acurácia menor para *Non-Creditworthy* porém podemos mesmo assim considerar que o modelo não tem um bias significativo.

#### 2.	Quantos indivíduos são bons pagadores?

Por fim, analisando após aplicarmos o nosso modelo na base de novos customers, vimos que **408** pessoas estão aptas a receber o empréstimo do nosso banco, sendo que o critério de seleção foi de pessoas com Score >=50% seriam consideradas como *Creditworthy*.

## Alteryx Flow

![alteryx flow](https://user-images.githubusercontent.com/34245933/51284262-13f28c00-19d2-11e9-8545-73aaa7b7d315.PNG)
