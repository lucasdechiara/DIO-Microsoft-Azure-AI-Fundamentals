<h1>
    <a href="https://www.dio.me/">
     <img align="center" width="60px" src="https://hermes.dio.me/lab_projects/badges/dc92e499-6ec6-4c82-af3f-00c40538ca80.png"></a>
    <span> 
Análise de Sentimentos com Language Studio </span>
</h1>

## Analyze sentiment and mine opinions
O Processamento de Linguagem Natural (PNL) é um ramo da IA ​​que lida com a linguagem escrita e falada. Você pode usar a PNL para construir soluções que extraiam significado semântico de texto ou fala, ou que formulem respostas significativas em linguagem natural.

O Azure AI Language Service inclui análise de texto e recursos de PNL. Isso inclui a identificação de frases-chave no texto e a classificação do texto com base no sentimento.

Neste exercício é explorado os recursos da linguagem Azure AI analisando uma crítica do filme Guerra Civil, feita por [MARCELO HESSEL em 18/04/2024 para o site Omelete](https://www.omelete.com.br/filmes/criticas/guerra-civil-filme-critica) verificando se as sentenças são em sua maioria positivas ou negativas.

## Após criar o recurso no [Portal do Azure](https://portal.azure.com) entre no [Language Studio](https://language.cognitive.azure.com)

## 01 - Dentro do Language Studio guia *"Classify test"* clique na opção *"Analyze sentiment and mine opinions"*:   
<img align="right" src="https://github.com/lucasdechiara/DIO-Microsoft-Azure-AI-Fundamentals/blob/main/imagens/DP03%20-%20An%C3%A1lise%20de%20sentimentos/01.png" width=""/> 

...
- 1.1 Em Selecionar idioma do texto.
- 1.2 Em Selecione seu recurso do Azure.
- 1.3 Digite seu próprio texto, carregue um arquivo ou use um dos textos de exemplo.

<img align="right" src="https://github.com/lucasdechiara/DIO-Microsoft-Azure-AI-Fundamentals/blob/main/imagens/DP03%20-%20An%C3%A1lise%20de%20sentimentos/02.png" width=""/> 

...
- 1.4 Marque a caixa para confirmar que a demonstração incorrerá em uso e poderá incorrer em custos e selecione Executar .

<img align="right" src="https://github.com/lucasdechiara/DIO-Microsoft-Azure-AI-Fundamentals/blob/main/imagens/DP03%20-%20An%C3%A1lise%20de%20sentimentos/03.png" width=""/>

...
- 1.5 Revise a saída. Observe que o documento é analisado quanto ao sentimento, assim como cada frase . Selecione Frase 1 para mostrar a análise de sentimento dessa frase.

<img align="right" src="https://github.com/lucasdechiara/DIO-Microsoft-Azure-AI-Fundamentals/blob/main/imagens/DP03%20-%20An%C3%A1lise%20de%20sentimentos/04.png" width=""/> 
  
...

## Considerações Finais  

O recurso do Language Studio para análise de sentimentos e extração de opiniões foi muito assertivo na avaliação, classificou o texto como:
- 86% negativo;
- 04% neutro;
- 09% positivo;
  
Coerente com a avaliação do site Omelete, onde o autor da crítica deu uma avaliação de 2 estrelas, em uma classificação de 0-5 para o filme, assim a análise de sentimentos pode ser considerada bem sucedida.

