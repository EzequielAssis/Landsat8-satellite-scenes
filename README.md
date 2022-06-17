# Landsat8-satellite-scenes
### Se você está buscando acessar cenas do landsat 8 de forma automatizada, o código acima pode te ajudar.

O código foi desenvolvido para solicitar especificamente indices de NDVI, mas pode ser alterado para buscar outras bandas especificas. O fluxo principal do código é o seguinte:
* Ler um shapefile da região de interesse e extrair seus limites (os mínimos e maximos de longitude e latitude).
* Acessar a [API da EROS](https://m2m.cr.usgs.gov/) e usar os limites do shapefile para descrever o Minimum bounding rectangle (MBR) e buscar todas as cenas que cobrem a região em um intervalo de tempo especificado. Há um loop nessa parte que foi usado para percorrer a região ao longo dos anos e encontrar a combinação de cenas com a menor cobertura de nuvem, mas o loop pode ser removido.
* A lista de cenas é passada para a [API da ESPA](https://espa.cr.usgs.gov/) que fará a requisição das cenas. A API da EROS também gera ordens de Download de cenas, mas a API da ESPA entrega indices espectrais (NDVI, EVI...).
* Quando todas as cenas forem processadas, o download poderá ser efetuado utilizando o script disponibilizado pela própria ESPA. Após o download de todas as cenas. O arquivo .tiff que contém a banda NDVI é extraído de cada cena baixada

Para ter acesso a API da EROS e da ESPA, é necessário [criar uma conta na USGS](https://ers.cr.usgs.gov/register).
