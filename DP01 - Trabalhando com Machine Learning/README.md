<h1>
    <a href="https://www.dio.me/">
     <img align="center" width="60px" src="https://hermes.dio.me/lab_projects/badges/87d332d0-5198-4a2f-b159-38c8c2976954.png"></a>
    <span> Trabalhando com Machine Learning</span>
</h1>

## Criando modelo de previsão - Passo a passo

Para trabalhar no Azure Machine Learning é essencial que você possua um workspace e esta é a tarefa inicial, criar o seu workspace para assim poder criar o seu trabalho automatizado.

1. Entre no portal do Azure usando https://portal.azure.com suas credenciais da Microsoft.

2. Selecione + Criar um recurso , pesquise Machine Learning e crie um novo recurso do Azure Machine Learning com as seguintes configurações:
   - **Assinatura:** sua assinatura do Azure.
   - **Grupo de recursos:** Crie ou selecione um grupo de recursos.
   - **Nome:** Insira um nome exclusivo para seu espaço de trabalho.
   - **Região:** Selecione a região geográfica mais próxima.
   - **Conta de armazenamento:** observe a nova conta de armazenamento padrão que será criada para seu espaço de trabalho.
   - **Cofre de chaves:** Observe o novo cofre de chaves padrão que será criado para seu espaço de trabalho.
   - **Insights de aplicativo:** observe o novo recurso padrão de insights de aplicativo que será criado para seu espaço de trabalho.
   - **Registro de contêiner:** Nenhum ( um será criado automaticamente na primeira vez que você implantar um modelo em um contêiner ).

3. Selecione **Revisar + criar** e selecione **Criar** . Aguarde a criação do seu espaço de trabalho (pode demorar alguns minutos) e, em seguida, vá para o recurso implantado.

4. Selecione **Launch Studio** (ou abra uma nova guia do navegador e navegue até https://ml.azure.com e entre no Azure Machine Learning Studio usando sua conta da Microsoft). Feche todas as mensagens exibidas.

5. No estúdio Azure Machine Learning, você deverá ver seu espaço de trabalho recém-criado. Caso contrário, selecione **Todos os espaços de trabalho** no menu à esquerda e selecione o espaço de trabalho que você acabou de criar.

Depois que nosso workspace estiver pronto temos que entrar no ML studio para criar um "novo trabalho de ML automatizado", seguindo o [passo a passo da documentação do Learning](https://aka.ms/ai900-auto-ml) para melhor entendimento e para que tudo dê certo:

## Vamos criar um aprendizado de maquina para a previsão de aluguel de bicicletas:

1. No Azure Machine Learning Studio, veja a página Automated ML (em Authoring ).
 <img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP01%20-%20Machine%20Learning/01.png" width=""/>

2. Crie um novo trabalho de ML automatizado com as seguintes configurações, usando Next conforme necessário para avançar pela interface do usuário:

    **Configurações básicas:**
    - **Nome do trabalho:** mslearn-bike-automl *(sugestão)*
    - **Novo nome do experimento:** mslearn-bike-rental *(sugestão)*
    - **Descrição:** Aprendizado de máquina automatizado para previsão de aluguel de bicicletas
    - **Marcadores:** nenhum

    <img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP01%20-%20Machine%20Learning/02.png" width=""/>

   **Tipo de tarefa e dados:**
    - **Selecione o tipo de tarefa:** Regressão
    - **Selecionar conjunto de dados:** crie um novo conjunto de dados com as seguintes configurações

    <img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP01%20-%20Machine%20Learning/03.png" width=""/>    

    **Tipo de dados:**
    - **Nome:** aluguel de bicicletas *(sugestão)*
    - **Descrição:** dados históricos de aluguel de bicicletas *(sugestão)*
    - **Tipo:** Tabular

    **Fonte de dados:**
    - Selecione: **Dos arquivos da web**
    
    <img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP01%20-%20Machine%20Learning/04.png" width=""/>  
 
    **URL da Web:**
    - **URL da Web:** https://aka.ms/bike-rentals
    - **Ignorar validação de dados:** não selecionar

    <img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP01%20-%20Machine%20Learning/05.png" width=""/>
  
    **Configurações:**
    - **Formato de arquivo:** Delimitado
    - **Delimitador:** Vírgula
    - **Codificação:** UTF-8
    - **Cabeçalhos de coluna:** apenas o primeiro arquivo possui cabeçalhos
    - **Pular linhas:** Nenhum
    - **O conjunto de dados contém dados multilinhas:** não selecione

    **Esquema:**
    - Incluir todas as colunas exceto **Caminho**
    - Revise os tipos detectados automaticamente

   <img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP01%20-%20Machine%20Learning/07.png" width=""/>

    Selecione **Criar**. Após a criação do conjunto de dados, selecione o conjunto de dados de **aluguel de bicicletas** para continuar a enviar o trabalho de ML automatizado.
   
     <img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP01%20-%20Machine%20Learning/08.png" width=""/>
     
   **Configurações de tarefa:**
    - **Tipo de tarefa:** Regressão
    - **Conjunto de dados:** aluguel de bicicletas

    <img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP01%20-%20Machine%20Learning/09.png" width=""/>

    - **Coluna de destino:** Aluguéis (inteiro)

    <img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP01%20-%20Machine%20Learning/10.png" width=""/>

    - **Configurações adicionais:**
        - Métrica primária: raiz do erro quadrático médio normalizado
        - Explique o melhor modelo : Não selecionado
        - Usar todos os modelos suportados : Desmarcado . Você restringirá o trabalho para tentar apenas alguns algoritmos específicos.
        - Modelos permitidos : Selecione apenas RandomForest e LightGBM — normalmente você gostaria de tentar o máximo possível, mas cada modelo adicionado aumenta o tempo necessário para executar o trabalho.
    - **Limites:** expanda esta seção
        - Máximo de testes : 3
        - Máximo de testes simultâneos : 3
        - Máximo de nós : 3
        - Limite de pontuação da métrica : 0,085 *( para que, se um modelo atingir uma pontuação da métrica de erro quadrático médio normalizado de 0,085 ou menos, o trabalho termina. )*
        - Tempo limite : 15
        - Tempo limite de iteração : 15
        - Habilitar rescisão antecipada : selecionado

    <img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP01%20-%20Machine%20Learning/11.png" width=""/> 

    - **Validação e teste:**
        - Tipo de validação : divisão de validação de trem
        - Porcentagem de dados de validação : 10
        - Conjunto de dados de teste : Nenhum

    <img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP01%20-%20Machine%20Learning/12.png" width=""/> 
         
    **Calcular:**

    - **Selecione o tipo de computação:** sem servidor
    - **Tipo de máquina virtual:** CPU
    - **Camada de máquina virtual:** Dedicada
    - **Tamanho da máquina virtual:** Standard_DS3_V2*
    - **Número de instâncias:** 1
      
    <img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP01%20-%20Machine%20Learning/13.png" width=""/> 

3. Envie o trabalho de treinamento. Ele inicia automaticamente.

    <img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP01%20-%20Machine%20Learning/14.png" width=""/>
    
5. Espere o trabalho terminar. Pode demorar um pouco (~15min) – agora pode ser um bom momento para uma pausa para o café!


## Avalie o melhor modelo

Quando o trabalho automatizado de aprendizado de máquina for concluído, você poderá revisar o melhor modelo treinado.

1. Na guia Visão geral do trabalho automatizado de aprendizado de máquina, observe o melhor resumo do modelo.
2. Selecione o texto em Nome do algoritmo do melhor modelo para visualizar seus detalhes.
3. Selecione a guia Métricas e selecione os gráficos residuais e predito_true se eles ainda não estiverem selecionados.

## Implantar e testar o modelo

1. Na guia Modelo do melhor modelo treinado pelo seu trabalho automatizado de machine learning, selecione Implantar e use a opção de serviço Web para implantar o modelo com as seguintes configurações:
    - **Nome:** prever-aluguéis
    - **Descrição:** Prever aluguel de bicicletas
    - **Tipo de computação:** Instância de Contêiner do Azure
    - **Habilitar autenticação:** selecionado

2. Aguarde o início da implantação – isso pode levar alguns segundos. O status de implantação do endpoint de previsão de aluguel será indicado na parte principal da página como Running .

3. Aguarde até que o status da implantação mude para Succeeded . Isso pode levar de 5 a 10 minutos.

## Teste do modelo

Na página do modelo, cliquei na aba "Pontos de extremidade". Também é possível acessar pelo menu lateral em "Pontos de extremidade". Cliquei no ponto correspondente ao modelo gerado. Em seguida, acessei a aba "Testar".

Para o teste, utilizei o json abaixo:

1. No estúdio Azure Machine Learning, no menu esquerdo, selecione Endpoints e abra o ponto final em tempo real de previsão de alugueres .

2. Na página do endpoint em tempo real de previsão de aluguel, visualize a guia Teste .

3. No painel Dados de entrada para testar o endpoint , substitua o modelo JSON pelos seguintes dados de entrada:

``` JASON
 {
   "Inputs": { 
     "data": [
       {
         "day": 1,
         "mnth": 1,   
         "year": 2022,
         "season": 2,
         "holiday": 0,
         "weekday": 1,
         "workingday": 1,
         "weathersit": 2, 
         "temp": 0.3, 
         "atemp": 0.3,
         "hum": 0.3,
         "windspeed": 0.3 
       }
     ]    
   },   
   "GlobalParameters": 1.0
 }
```

4. Clique no botão Testar .

5. Revise os resultados do teste, que incluem um número previsto de aluguéis com base nos recursos de entrada - semelhante a este:

A previsão gerada foi: 361.95

<img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP01%20-%20Machine%20Learning/18.png" width=""/> 

## BOM TESTES!! :tada::tada::tada:
