# Predicting_Default_Risk

## Resumo do projeto
Você é um agente de crédito em um pequeno banco novo (em operação há dois anos) que precisa de uma solução eficiente para classificar clientes novos entre aprovados e não aprovados para um empréstimo. Você utilizará uma série de modelos de classificação para descobrir o melhor modelo e fornecer ao seu gerente uma lista de clientes aptos a receber empréstimos.

## Passo 1: Entendimento de negócios e dados
Fornecer uma explicação das principais decisões que precisam ser feitas. (Limite de 250 palavras)
Decisões chave:
Responda estas perguntas

1.	Que decisões precisam ser tomadas?

A decisão que precisa ser tomada neste problema de negócio é se aprovamos ou não um crédito para os novos clientes, ou seja, precisamos classificar os novos clientes em duas categorias, APROVADO ou NÃO APROVADO.

2.	Que dados são necessários para informar essas decisões?



3.	Que tipo de modelo (Contínuo, Binário, Não-Binário, Time-Series) precisamos usar para ajudar a tomar essas decisões?

Para este problema, precisamos usar um Modelo Binário, sendo que a variável resposta é SIM ou NÃO para a aprovação.

## Passo 2: Construindo o Conjunto de Treinamento

Construa seu conjunto de treinamento dado os dados fornecidos a você. Os dados foram limpos para você já assim você não deve precisar converter quaisquer campos de dados para os tipos de dados apropriados.

Aqui estão algumas diretrizes para ajudar a orientar sua limpeza de dados:

●	Para campos de dados numéricos, existem campos que se correlacionam entre si? A correlação deve ser de pelo menos 0,70 para ser considerada "alta".

●	Existem dados em falta para cada um dos campos de dados? Campos com muitos dados em falta devem ser removidos

●	Existem apenas alguns valores em um subconjunto de seu campo de dados? O campo de dados parece muito uniforme (há apenas um valor para todo o campo?). Isso é chamado de "baixa variabilidade" e você deve remover os campos que têm baixa variabilidade. Consulte a seção "Dicas" para encontrar exemplos de campos de dados com baixa variabilidade.

●	Seu conjunto de dados limpos deve ter 13 colunas onde a média de  Age Years  deve ser 36 (arredondado para cima)

Nota: Por uma questão de consistência no processo de limpeza de dados, impute dados usando a média de todo o campo de dados em vez de remover alguns pontos de dados. (Limite de 100 palavras)

Nota: Para alunos que usam software diferente do Alteryx, por favor, formate cada variável como:




Para alcançar resultados consistentes os revisores esperam.

Responda esta pergunta:

1.	Em seu processo de limpeza, quais campos você removeu ou imputou? Por favor, justifique por que você removeu ou imputou esses campos. As visualizações são incentivadas.

## Passo 3: Treinar seus Modelos de Classificação

Primeiro, crie suas amostras de Estimação e Validação, onde 70% de seu conjunto de dados deve ir para Estimativa e 30% de seu conjunto de dados inteiro deve ser reservado para Validação. Defina a Semente Aleatória como 1.

Crie todos os modelos a seguir: regressão logística, árvore de decisão (decision trees), modelo de floresta (forest model), e boosted model. 

Responda a estas perguntas para cada modelo criado:

1.	Quais variáveis preditoras são significativas ou as mais importantes? Por favor, mostre os p-values ou gráficos de importância para todas as suas variáveis de previsão.

2.	Valide seu modelo em relação ao conjunto de Validação. Qual foi a porcentagem geral de precisão? Mostre a matriz de confusão. Existe algum viés (bais) nas previsões do modelo?

Você deve ter quatro conjuntos de perguntas respondidas. (Limite de 500 palavras)


## Step 4: Escrita

Decidir sobre o melhor modelo e pontuação de seus novos clientes. Para revisar a consistência, se Score_Creditworthy for maior que Score_NonCreditworthy, a pessoa deve ser rotulada como "Creditworthy"

Escreva um breve relatório sobre como você criou o seu modelo de classificação e anote quantos dos novos clientes se qualificariam para um empréstimo. (Limite de 250 palavras)

Responda estas perguntas:

1.	Qual modelo você escolheu usar? Por favor, justifique sua decisão usando apenas as seguintes técnicas:
a.	Precisão geral contra o seu conjunto de validação
b.	Exatidão dentro dos segmentos "Creditworthy" e "Non-Creditworthy"
c.	Gráfico ROC
d.	Bias nas Matrizes de Confusão

Nota: Lembre-se de que seu chefe só se preocupa com a precisão das previsões para os segmentos Credityworth e Non-Creditworthy.

2.	Quantos indivíduos são bons pagadores?
