# **ANÁLISE, TRATAMENTO, AUTOMATIZAÇÃO E MACHINE LEARNING: GEOLOCALIZAÇÃO REGIÃO**  
## **Objetivo**  
- Localizar a região de cada pessoa com suas coordenadas dentro de um munícipio na utilização de funções relacionadas a dados geoespacias;
- A partir de localizada, construir um modelo de aprendizagem de máquina que realizará o mesmo próposito de prever a região;
- Separar os dados em uma amostra, usada na criação do modelo, e o restante para previsão da região pelo modelo;
- Empregar quatro variáveis preditivas criadas na conversão de latitude e longitude, destaque na utilização de algoritmo de clusterização agrupamento hierárquico;
- Testar em diferentes algoritmos de aprendizagem supervisionada de classificação e comparar o melhor para fazer a previsão da região nos dados que restaram.  
## **Informação**  
Base de dados: 185.005 linhas com 20% para elaborar o modelo de machine learning e os outros 80% para visualizar o desempenho do próprio modelo na rotulação do atributo-alvo região.  
## **INTRODUÇÃO**  
### **Conceito dados geoespaciais utilizados**  
#### **Ponto**  
Uma coordenada definida por latitude e longitude. Por exemplo a localização das pessoas que serão usadas no projeto.  

![Ponto](https://user-images.githubusercontent.com/111579476/196970550-1d1b62df-48e5-4370-9f1c-dea9a4d33fc7.png)  

Disponível em: https://www.slideshare.net/MdYousufGazi/introductory-gis  
#### **Polígono**  
São os pontos interligados com uma área delimitada por dentro, ou seja, fechados por dentro. Cada região que compõem o município pode ser expressa por um polígono e será essencial no objetivo do trabalho.

![Poligono](https://user-images.githubusercontent.com/111579476/196970893-096e611b-33f7-4887-8506-730b0ba17b9c.png)
 
Disponível em: https://www.slideshare.net/MdYousufGazi/introductory-gis 
#### **Line String**  
São os pontos interligados. No arquivo GeoJSON representa a cidade.

![Line_String](https://user-images.githubusercontent.com/111579476/196971610-e524a0e8-767e-4d19-bc97-d542e70c0de2.png)  
Disponível em: http://132.72.155.230:3838/js/geojson-1.html  
### **GIS (Sistemas de Informação Geográfica)**  
" Um sistema de informação geográfica (GIS) é um sistema que cria, gerencia, analisa e mapeia todos os tipos de dados. GIS conecta dados a um mapa, integrando dados de localização (onde as coisas estão) com todos os tipos de informações descritivas (como as coisas são lá). Isso fornece uma base para mapeamento e análise que é usada na ciência e em quase todos os setores. O GIS ajuda os usuários a entender padrões, relacionamentos e contexto geográfico. Os benefícios incluem melhor comunicação e eficiência, bem como melhor gestão e tomada de decisões."   
Disponível em: https://www.esri.com/pt-br/what-is-gis/overview  
Utilizou-se o conceito de Intersecção presente na nomenclatura do GIS que se baseia na entrada de tipos de geometria (ponto, polígonos, linhas) e a saída resulta na sobreposição desses objetos espacial, no contexto do projeto verificou se os pontos geográficos das pessoas estão dentro dos limites de um poígono da região A, B, C e assim por diante.  

<img width="355" alt="Intersect" src="https://user-images.githubusercontent.com/111579476/196972254-69472111-cf51-405e-92a5-b81eb1f6d9fa.png">  


Disponível em: https://pro.arcgis.com/en/pro-app/latest/tool-reference/analysis/intersect.htm  
## **Resultados**  
Baseado no arquivo [previsores_amostra.csv](https://github.com/guilhermehencus/geolocalizacao_ML/blob/master/Dataset_Prev_Alvo/previsores_amostra.csv) e [alvo_amostra.csv](https://github.com/guilhermehencus/geolocalizacao_ML/blob/master/Dataset_Prev_Alvo/alvo_amostra.csv), o melhor algoritmo para ser utlizado no modelo proposto é o Random Forest:  
  
**SVM = 90.25% (teste) e 90.32% (validação cruzada)**  
**Árvore de Decisão = 99.78% (teste) e 99.83% (validação cruzada)**  
**Random Forest = 99.85% (teste) e 99.88% (validação cruzada)**  
**XGboost = 99.77% (teste) e 99.85% (validação cruzada)**  
**LightGBM = 99.72% (teste) e 99.75% (validação cruzada)**  
**CatBoost =  99.73% (teste) e 99.66% (validação cruzada)**  
Escolhido o Random Forest, o algoritmo previu 97.10% corretamente no arquivo disponibilizado [previsores_populacao.csv](https://github.com/guilhermehencus/geolocalizacao_ML/blob/master/Dataset_Prev_Alvo/previsores_populacao.csv) e [alvo_populacao.csv](https://github.com/guilhermehencus/geolocalizacao_ML/blob/master/Dataset_Prev_Alvo/alvo_populacao.csv)
