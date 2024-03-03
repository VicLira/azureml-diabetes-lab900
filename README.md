# azureml-diabetes-lab900

## Criando um Workspace Azure ML

1. Cadastrei-me na plataforma [Azure Portal](https://portal.azure.com).
2. Selecionei o botão "+ Criar Recurso", escolhendo o recurso "Azure Machine Learning" e preenchendo os seguintes campos:

   - **Assinatura**: Minha assinatura (identificação pessoal na plataforma).
   - **Grupo de Recursos**: Criar ou selecionar um grupo de recursos.
   - **Nome**: Insira um nome único para o seu workspace.
   - **Região**: Selecione a região geográfica mais próxima.
   - **Conta de Armazenamento**: Anote a conta de armazenamento padrão que será criada para o seu workspace.
   - **Key Vault**: Anote o novo cofre de chaves que será criado por padrão para o seu workspace.
   - **Application Insights**: Anote a nova instância de insights de aplicativos que será criada por padrão para o seu workspace.
   - **Registro de Contêiner**: Nenhum (um será criado automaticamente na primeira vez que você implantar um modelo em um contêiner).
   
3. Selecione "Revisar + criar" e, em seguida, "Criar". Aguarde até que seu workspace seja criado (isso pode levar alguns minutos) e, em seguida, vá para o recurso implantado.

4. Selecione "Iniciar Studio" (ou abra uma nova aba do navegador e acesse https://ml.azure.com, e faça login no Azure Machine Learning Studio usando sua conta Microsoft). Feche quaisquer mensagens que forem exibidas.

5. No Azure Machine Learning Studio, você deverá ver seu workspace recém-criado. Caso contrário, selecione "Todos os workspaces" no menu à esquerda e, em seguida, escolha o workspace que acabou de ser criado.

## Usando automated machine learning para treinar um modelo

Para criar um trabalho de Automated ML com base no conjunto de dados fornecido, você pode seguir um processo semelhante ao descrito para o bike-rentals. Aqui está o passo a passo:

### Configurações Básicas:

- **Nome do Trabalho:** diabetes-prediction-automl
- **Nome do Experimento:** diabetes-prediction
- **Descrição:** Automated machine learning para previsão de diabetes
- **Tags:** Nenhuma

### Tipo de Tarefa e Dados:

- **Tipo de Tarefa:** Classificação
- **Conjunto de Dados:**
  - **Nome:** diabetes-data
  - **Descrição:** Dados históricos sobre pacientes com diabetes
  - **Tipo:** Tabular
  - **Fonte de Dados:** Carregar de um arquivo web
  - **Arquivo:** https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-fundamentals/main/data/ml/diabetes.csv

### Configurações de Tarefa:

- **Tipo de Tarefa:** Classificação
- **Conjunto de Dados:** diabetes-data
- **Coluna Alvo:** Diabetic (binário: 0 ou 1)
- **Configuração Adicional:**
  - **Métrica Primária:** AUC weighted
  - **Explicar o melhor modelo:** Não selecionado
  - **Usar todos os modelos suportados:** Não selecionado
  - **Modelos Permitidos:** Escolha os modelos que deseja testar. Por exemplo, RandomForest, LogisticRegression, SVM, etc.

### Limites:

- **Número Máximo de Tentativas:** 3
- **Número Máximo de Tentativas Concorrentes:** 3
- **Número Máximo de Nós:** 3
- **Limite de Pontuação da Métrica:** Defina um limite para terminar o trabalho quando uma métrica atinge um determinado valor.

### Validação e Teste:

- **Tipo de Validação:** Divisão de Treinamento-Validação
- **Percentual de Dados de Validação:** 10
- **Conjunto de Dados de Teste:** Nenhum

### Configuração de Computação:

- **Tipo de Computação:** Serverless
- **Tipo de Máquina Virtual:** CPU
- **Nível da Máquina Virtual:** Dedicado
- **Tamanho da Máquina Virtual:** Escolha um tamanho apropriado para suas necessidades.

### Submissão do Trabalho:

Após revisar todas as configurações, submeta o trabalho de Automated ML para iniciar o processo de treinamento.

Certifique-se de adaptar as configurações e os detalhes conforme necessário para atender aos requisitos específicos do conjunto de dados e aos objetivos do projeto de previsão de diabetes.

### Resultados:

![Resultados Da ](https://raw.githubusercontent.com/VicLira/azureml-diabetes-lab900/main/resultados.png))
