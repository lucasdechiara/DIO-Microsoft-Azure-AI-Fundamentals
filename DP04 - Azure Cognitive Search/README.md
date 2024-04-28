<h1>
    <a href="https://www.dio.me/">
     <img align="center" width="60px" src="https://hermes.dio.me/lab_projects/badges/619af8f8-d138-4e40-9d48-fec7b318e44d.png"></a>
    <span> 
Azure Cognitive Search: Utilizando AI Search para indexação e consulta de Dados</span>
</h1>

## Situação Problema:
Vamos imaginar que você trabalha para a Fourth Coffee, uma rede nacional de cafés. Você foi solicitado a ajudar a criar uma solução de mineração de conhecimento que facilite a busca de insights sobre as experiências dos clientes. Você decide criar um índice do Azure AI Search usando dados extraídos de avaliações de clientes.

## Desafio:
Criar uma pesquisa que funcione juntamente com um serviço de inteligência artificial para identificar palavras-chave, sentimentos, utilizando também o serviço de armazenamento do Azure, explorando um índice do Azure AI Search (UI).

Recursos utilizados:
- Azure AI Search
- Azure AI Services
- Azure Storage

[Documentação](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/11-ai-search.html)

## Passo 1: Criando recurso do Asure AI Search:     

<img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP04%20-%20Intelig%C3%AAncia%20de%20documentos%20e%20minera%C3%A7%C3%A3o%20de%20conhecimento/01%20-%20config%20da%20busca.gif" width=""/> ...  

## Passo 2: Criando recurso do Azure AI Services:      

<img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP04%20-%20Intelig%C3%AAncia%20de%20documentos%20e%20minera%C3%A7%C3%A3o%20de%20conhecimento/02%20-%20config%20do%20servi%C3%A7o%20de%20IA.gif" width=""/>
... 

## Passo 3: Criando o Storage:      

<img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP04%20-%20Intelig%C3%AAncia%20de%20documentos%20e%20minera%C3%A7%C3%A3o%20de%20conhecimento/03%20-%20Cria%C3%A7%C3%A3o%20do%20storage.gif" width=""/> 
... 
<img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP04%20-%20Intelig%C3%AAncia%20de%20documentos%20e%20minera%C3%A7%C3%A3o%20de%20conhecimento/04%20-%20deploy%20completo.png" width=""/> ... 

## Passo 4: Permitindo acesso anônimo ao Blob:      

Como nosso laboratório é apenas didático, para aprender os princípios da inteligência artificial com o Azure, precisamos permitir o acesso anônimo ao blob para simplificar e facilitar nossas implementações. Após criar o seu Storage, entre no mesmo e navegue até a guia SETTINGS > CONFIGURATION seguindo os passos abaixo:

<img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP04%20-%20Intelig%C3%AAncia%20de%20documentos%20e%20minera%C3%A7%C3%A3o%20de%20conhecimento/05%20-%20permitindo%20acesso%20anonimo%20de%20blob.gif" width=""/> ... 


## Passo 5: Criando o Container:      

Navegue até a guia DATA STORAGE > CONTAINERS, para criar o container dentro do storage e adicionar as pesquisas que serão analisadas pelo AI SERVICE.

<img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP04%20-%20Intelig%C3%AAncia%20de%20documentos%20e%20minera%C3%A7%C3%A3o%20de%20conhecimento/06%20-%20criando%20container.gif" width=""/> ...   
<img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP04%20-%20Intelig%C3%AAncia%20de%20documentos%20e%20minera%C3%A7%C3%A3o%20de%20conhecimento/07%20adicionando%20pesquisas%20ao%20container.gif" width=""/> ...  

## Passo 6: Importação e indexação dados para o AI SEARCH:      

Neste ponto você precisa linkar / importar os dados que você inseriu e configurou no seu STORAGE, volte para o AI SEARCH e siga os passos abaixo:

<img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP04%20-%20Intelig%C3%AAncia%20de%20documentos%20e%20minera%C3%A7%C3%A3o%20de%20conhecimento/08%20-%20importando%20os%20dados.gif" width=""/> ... 

Esta é a parte mais importante de todo o processo, assim como a Valéria explica na vídeo aula "Buscas cognitivas" do bootcamp, são muitos passos que que você precisa seguir a risca.

Ao seguir a [Documentação](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/11-ai-search.html) você chegará em INDEX DOCUMETS, o qual o gif acima mostra o início do processo.

## Passo 7: Consultando o índice:      

Feitas todas as configurações vamos voltar ao AZURE AI SERVICES, entrar no nosso serviço e através do SEARCH EXPLORER testar se tudo foi indexado e se a consulta esta funcionando, utilizando os comandos:

<img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP04%20-%20Intelig%C3%AAncia%20de%20documentos%20e%20minera%C3%A7%C3%A3o%20de%20conhecimento/11%20-%20testando%20a%20pesquisa.png" width=""/> ... 

No Search Explorer as consultas podem ser realizadas atraves da utilização de uma Query ou código JSON, conforme imagem abaixo.

<img align="right" src="https://github.com/lucasdechiara/DIO-Microsoft-Azure-AI-Fundamentals/blob/main/imagens/DP04%20-%20Intelig%C3%AAncia%20de%20documentos%20e%20minera%C3%A7%C3%A3o%20de%20conhecimento/searchJSON.png" width=""/> ... 

A consulta abaixo retorna todos os documentos no índice de pesquisa, incluindo uma contagem de todos os documentos no campo  **@odata.count**

**Query view**:
```
search=*&$count=true    (  verifica se a indexação esta funcionando e mostra os documentos )
```
**JSON view**:
```
{
    "search": "*",
    "count": true
}
```
<img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP04%20-%20Intelig%C3%AAncia%20de%20documentos%20e%20minera%C3%A7%C3%A3o%20de%20conhecimento/12%20-%20testando%20a%20pesquisa.png" width=""/> ... 

A consulta abaixo pesquisa todos os documentos no índice e filtra revisões com localização em Chicago. Você deveria ver 3 no **@odata.countcampo** campo:

**Query view**:
```
search=locations:'Chicago' ( Consulta as ocorrencias acontecidas em Chicado )
```
**JSON view**:
```
{
 "search": "locations:'Chicago'",
 "count": true
}
```
<img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP04%20-%20Intelig%C3%AAncia%20de%20documentos%20e%20minera%C3%A7%C3%A3o%20de%20conhecimento/13.png" width=""/> ... 

A consulta abaixo pesquisa todos os documentos no índice e filtra revisões com sentimento negativo. Você deveria ver 1 no **@odata.countcampo**

**Query view**:
```
search=sentiment:'negative' ( Consulta as ocorrencias com sentimento negativo )
```
**JSON view**:
```
{
 "search": "sentiment:'negative'",
 "count": true
}
```
<img align="right" src="https://raw.githubusercontent.com/alexklenio/DIO-Microsoft-Azure-AI-Fundamentals/main/imagens/DP04%20-%20Intelig%C3%AAncia%20de%20documentos%20e%20minera%C3%A7%C3%A3o%20de%20conhecimento/14.png" width=""/> ... 


## Observações finais:      

Um dos grandes problemas que as empresas tem é garantir a organização dos documentos e pesquisas rápidas através de ingestão de dados, assim neste laboratório foi avaliado quais recursos do Azure podem ser utilizados para extração dos dados de pesquisa de uma forma prática, enriquecimento da IA, como trabalhar os índices e consultar essas pesquisas futuramente.



