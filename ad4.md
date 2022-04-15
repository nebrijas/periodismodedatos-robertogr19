### API Pandas Folium
- API
- Pandas
- Folium, mapas

## Instalar lebrerías


En primer lugar instalaremos la librería Pandas para poder tener las herramientas que nos van a permitir trabajar con los datos en los diferentes formatos que necesitamos: Excel, SQL, CSV y HDF5. Gracias a Pandas podremos filtrar fácilmente tablas de datos en función de nuestras necesidades


```python
!pip install pandas folium
```

    Requirement already satisfied: pandas in c:\programdata\anaconda3\lib\site-packages (1.2.4)
    Requirement already satisfied: folium in c:\programdata\anaconda3\lib\site-packages (0.12.1.post1)
    Requirement already satisfied: requests in c:\programdata\anaconda3\lib\site-packages (from folium) (2.25.1)
    Requirement already satisfied: jinja2>=2.9 in c:\programdata\anaconda3\lib\site-packages (from folium) (2.11.3)
    Requirement already satisfied: branca>=0.3.0 in c:\programdata\anaconda3\lib\site-packages (from folium) (0.4.2)
    Requirement already satisfied: numpy in c:\programdata\anaconda3\lib\site-packages (from folium) (1.20.1)
    Requirement already satisfied: MarkupSafe>=0.23 in c:\programdata\anaconda3\lib\site-packages (from jinja2>=2.9->folium) (1.1.1)
    Requirement already satisfied: python-dateutil>=2.7.3 in c:\programdata\anaconda3\lib\site-packages (from pandas) (2.8.1)
    Requirement already satisfied: pytz>=2017.3 in c:\programdata\anaconda3\lib\site-packages (from pandas) (2021.1)
    Requirement already satisfied: six>=1.5 in c:\programdata\anaconda3\lib\site-packages (from python-dateutil>=2.7.3->pandas) (1.15.0)
    Requirement already satisfied: certifi>=2017.4.17 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (2020.12.5)
    Requirement already satisfied: chardet<5,>=3.0.2 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (4.0.0)
    Requirement already satisfied: idna<3,>=2.5 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (2.10)
    Requirement already satisfied: urllib3<1.27,>=1.21.1 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (1.26.4)
    

## Configurar librerías

Deberemos importarlas para poder usarlas en nuestro Notebook. Lo haremos usando las siguientes funciones:


```python
import pandas as pd
import folium
```

## Variables

Las variasbles que vamos a usar son:

- url
- coords_zrgz
- mapa

En primer lugar usaremos la URL de la que queremos exportar los datos, los accidentes de tráfico en Zaragoza. Usaremos la librería Folium para generar el mapa y le indicaremos las coordenadas del sitio que queremos que nos muestre. 


```python
url = 'https://www.zaragoza.es/sede/servicio/transporte/accidentalidad-trafico/accidente.csv?rows=100'
coords_zrgz = [41.649693,-0.887712]
mapa = folium.Map(location=coords_zrgz)
```

Ahora llamamos al mapa, al que ya hemos dado valor en la función anterior


```python
mapa
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><span style="color:#565656">Make this Notebook Trusted to load map: File -> Trust Notebook</span><iframe src="about:blank" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" data-html=%3C%21DOCTYPE%20html%3E%0A%3Chead%3E%20%20%20%20%0A%20%20%20%20%3Cmeta%20http-equiv%3D%22content-type%22%20content%3D%22text/html%3B%20charset%3DUTF-8%22%20/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%3Cscript%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20L_NO_TOUCH%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20L_DISABLE_3D%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%3C/script%3E%0A%20%20%20%20%0A%20%20%20%20%3Cstyle%3Ehtml%2C%20body%20%7Bwidth%3A%20100%25%3Bheight%3A%20100%25%3Bmargin%3A%200%3Bpadding%3A%200%3B%7D%3C/style%3E%0A%20%20%20%20%3Cstyle%3E%23map%20%7Bposition%3Aabsolute%3Btop%3A0%3Bbottom%3A0%3Bright%3A0%3Bleft%3A0%3B%7D%3C/style%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//code.jquery.com/jquery-1.12.4.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js%22%3E%3C/script%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css%22/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cmeta%20name%3D%22viewport%22%20content%3D%22width%3Ddevice-width%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20initial-scale%3D1.0%2C%20maximum-scale%3D1.0%2C%20user-scalable%3Dno%22%20/%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cstyle%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%23map_a1020f0e5935425f9d7a557e4cf1147a%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20position%3A%20relative%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20width%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20height%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20left%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20top%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%3C/style%3E%0A%20%20%20%20%20%20%20%20%0A%3C/head%3E%0A%3Cbody%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cdiv%20class%3D%22folium-map%22%20id%3D%22map_a1020f0e5935425f9d7a557e4cf1147a%22%20%3E%3C/div%3E%0A%20%20%20%20%20%20%20%20%0A%3C/body%3E%0A%3Cscript%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20map_a1020f0e5935425f9d7a557e4cf1147a%20%3D%20L.map%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22map_a1020f0e5935425f9d7a557e4cf1147a%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20center%3A%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20crs%3A%20L.CRS.EPSG3857%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoom%3A%2010%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoomControl%3A%20true%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20preferCanvas%3A%20false%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20tile_layer_e7b550414ec54ceb9a57bb2c56809579%20%3D%20L.tileLayer%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22https%3A//%7Bs%7D.tile.openstreetmap.org/%7Bz%7D/%7Bx%7D/%7By%7D.png%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22attribution%22%3A%20%22Data%20by%20%5Cu0026copy%3B%20%5Cu003ca%20href%3D%5C%22http%3A//openstreetmap.org%5C%22%5Cu003eOpenStreetMap%5Cu003c/a%5Cu003e%2C%20under%20%5Cu003ca%20href%3D%5C%22http%3A//www.openstreetmap.org/copyright%5C%22%5Cu003eODbL%5Cu003c/a%5Cu003e.%22%2C%20%22detectRetina%22%3A%20false%2C%20%22maxNativeZoom%22%3A%2018%2C%20%22maxZoom%22%3A%2018%2C%20%22minZoom%22%3A%200%2C%20%22noWrap%22%3A%20false%2C%20%22opacity%22%3A%201%2C%20%22subdomains%22%3A%20%22abc%22%2C%20%22tms%22%3A%20false%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a1020f0e5935425f9d7a557e4cf1147a%29%3B%0A%20%20%20%20%20%20%20%20%0A%3C/script%3E onload="this.contentDocument.open();this.contentDocument.write(    decodeURIComponent(this.getAttribute('data-html')));this.contentDocument.close();" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>



Vamos a crear un dataframe, que es como Python denomina a las tablas. Con la función delimiter, a la que llamaremos ;, para que la librería lea la función read csv. 


```python
df = pd.read_csv(url,delimiter=';')
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>year</th>
      <th>type</th>
      <th>accidentType</th>
      <th>firstAddress</th>
      <th>secondAddress</th>
      <th>geometry</th>
      <th>reason</th>
      <th>area</th>
      <th>creationDate</th>
      <th>daniosMateriales</th>
      <th>falloMecanico</th>
      <th>estadoPavimento</th>
      <th>tipoEstadoPavimento</th>
      <th>estadoAtmosfera</th>
      <th>tipoEstadoAtmosfera</th>
      <th>afectado</th>
      <th>vehiculo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>COSTA, JOAQUIN</td>
      <td>PERAL, ISAAC</td>
      <td>-0.8818527060979306,41.649027473051156</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>NaN</td>
      <td>2014-10-09T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>CADENA(MARQUES DE LA)</td>
      <td>NaN</td>
      <td>-0.8645810716721081,41.661585829868585</td>
      <td>DISTANCIA DE SEGURIDAD, no mantener</td>
      <td>2560.0</td>
      <td>2014-10-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>GOMEZ AVELLANEDA, G.</td>
      <td>CASTRO, R. (POETA)</td>
      <td>-0.887776415002892,41.666992622958105</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>2598.0</td>
      <td>2014-10-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLIS FRONTOLATERAL</td>
      <td>NaN</td>
      <td>MONZON</td>
      <td>GARCIA CONDOY, H.</td>
      <td>-0.8825260453930127,41.62957498750602</td>
      <td>CEDA EL PASO, no respetar prioridad de paso</td>
      <td>2555.0</td>
      <td>2014-10-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>RIOJA</td>
      <td>NAVARRA, AVENIDA DE</td>
      <td>-0.908314757720389,41.6562121210704</td>
      <td>PERDIDA del control por VELOCIDAD INADECUADA</td>
      <td>2554.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>95</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>OTRAS</td>
      <td>NaN</td>
      <td>MIRAL, DOMINGO</td>
      <td>NaN</td>
      <td>-0.8990662796872798,41.63977012001253</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>NaN</td>
      <td>2014-07-30T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>96</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>BUÑUEL,LUIS (PARQUE DEL AGUA)</td>
      <td>NaN</td>
      <td>-0.9072756956226459,41.670910841846876</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>2071.0</td>
      <td>2014-07-31T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>97</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>ALBAR, MANUEL GL.</td>
      <td>ILUSTRACION, AV. DE LA</td>
      <td>-0.9226018969034585,41.62757051008441</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>1969.0</td>
      <td>2014-07-25T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>98</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLIS FRONTOLATERAL</td>
      <td>NaN</td>
      <td>ECHEGARAY Y CABALLERO</td>
      <td>SAN VICENTE PAUL</td>
      <td>-0.8735234620830842,41.65507219335992</td>
      <td>SEMÁFORO, no respetar prioridad de paso</td>
      <td>1970.0</td>
      <td>2014-07-26T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>99</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>CESAR AUGUSTO, AVDA</td>
      <td>NaN</td>
      <td>-0.8869504077778204,41.65022964156985</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>1971.0</td>
      <td>2014-07-09T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
  </tbody>
</table>
<p>100 rows × 18 columns</p>
</div>



# Exploración de la tabla

Para conocer cuáles son los nombres de cada columna utilizaremos la función df.columns


```python
df.columns
```




    Index(['id', 'year', 'type', 'accidentType', 'firstAddress', 'secondAddress',
           'geometry', 'reason', 'area', 'creationDate', 'daniosMateriales',
           'falloMecanico', 'estadoPavimento', 'tipoEstadoPavimento',
           'estadoAtmosfera', 'tipoEstadoAtmosfera', 'afectado', 'vehiculo'],
          dtype='object')



Con esta función le pediremos que nos muestre los datos de la columna geometry


```python
df['geometry']
```




    0     -0.8818527060979306,41.649027473051156
    1     -0.8645810716721081,41.661585829868585
    2      -0.887776415002892,41.666992622958105
    3      -0.8825260453930127,41.62957498750602
    4        -0.908314757720389,41.6562121210704
                           ...                  
    95     -0.8990662796872798,41.63977012001253
    96    -0.9072756956226459,41.670910841846876
    97     -0.9226018969034585,41.62757051008441
    98     -0.8735234620830842,41.65507219335992
    99     -0.8869504077778204,41.65022964156985
    Name: geometry, Length: 100, dtype: object



Con esta función definiremos los tipos de datos que tiene nuestra tabla


```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 100 entries, 0 to 99
    Data columns (total 18 columns):
     #   Column               Non-Null Count  Dtype  
    ---  ------               --------------  -----  
     0   id                   100 non-null    object 
     1   year                 100 non-null    int64  
     2   type                 100 non-null    object 
     3   accidentType         0 non-null      float64
     4   firstAddress         100 non-null    object 
     5   secondAddress        48 non-null     object 
     6   geometry             100 non-null    object 
     7   reason               100 non-null    object 
     8   area                 79 non-null     float64
     9   creationDate         100 non-null    object 
     10  daniosMateriales     100 non-null    bool   
     11  falloMecanico        100 non-null    bool   
     12  estadoPavimento      100 non-null    object 
     13  tipoEstadoPavimento  0 non-null      float64
     14  estadoAtmosfera      100 non-null    object 
     15  tipoEstadoAtmosfera  0 non-null      float64
     16  afectado             44 non-null     object 
     17  vehiculo             100 non-null    object 
    dtypes: bool(2), float64(4), int64(1), object(11)
    memory usage: 12.8+ KB
    

Con la siguiente función conoceremos la información numérica


```python
df.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>accidentType</th>
      <th>area</th>
      <th>tipoEstadoPavimento</th>
      <th>tipoEstadoAtmosfera</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>100.000000</td>
      <td>0.0</td>
      <td>79.000000</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2013.590000</td>
      <td>NaN</td>
      <td>3341.569620</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.494311</td>
      <td>NaN</td>
      <td>1225.936991</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>min</th>
      <td>2013.000000</td>
      <td>NaN</td>
      <td>17.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2013.000000</td>
      <td>NaN</td>
      <td>2604.500000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>2014.000000</td>
      <td>NaN</td>
      <td>2659.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>2014.000000</td>
      <td>NaN</td>
      <td>4627.500000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>max</th>
      <td>2014.000000</td>
      <td>NaN</td>
      <td>4783.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



Con esta función le pediremos que nos muestre los datos de la columna type con una descripción de valores únicos. Gracias a esta función sabremos cuáles son los valores únicos de nuestra tabla. 


```python
df['type'].unique()
```




    array(['SALIDA CALZADA', 'COLISIÓN ALCANCE', 'COLIS FRONTOLATERAL',
           'OTRAS', 'ATROPELLO', 'CAIDA SOBRE CALZADA', 'COLIS. MARCHA ATRÁS',
           'COLISIÓN LATERAL'], dtype=object)



Esta función nos dice qué tipo de dato es la primera celda de la columna geometry. Nos mostrará un str, o lo que es lo mismo, una cadena de caracteres. Con la función split le pediremos que nos separe las dos celdas de la columna geometry con una coma para diferenciar latitud y longitud.


```python
type(df['geometry'][0])
```




    str




```python
df['geometry'][0].split(',')
```




    ['-0.8818527060979306', '41.649027473051156']



A continuación crearemos un punto geográfico con los datos obtenidos al que llamaremos point.


```python
point = df['geometry'][0].split(',')
point
```




    ['-0.8818527060979306', '41.649027473051156']



Vamos a hacer un bucle para cada uno de los elementos de la columna geometry. En el primero separaremos las longitudes y en el segundo las latitudes


```python
longitudes = []
latitudes = []
```

Usando los siguientes códigos le pediremos que nos muestre las longitudes 


```python
for i in df['geometry']:
    punto_coord = i.split(',')
    longitudes += [float(punto_coord[1])]
longitudes
```




    [41.649027473051156,
     41.661585829868585,
     41.666992622958105,
     41.62957498750602,
     41.6562121210704,
     41.65949772773082,
     41.633353667694024,
     41.6390382112928,
     41.64083344974765,
     41.64904657717317,
     41.64322365075108,
     41.68753087470739,
     41.661646612715046,
     41.6454384961757,
     41.65543768899759,
     41.65180346604993,
     41.65233828238132,
     41.65040494617356,
     41.645335650478316,
     41.609992514227066,
     41.63379905763323,
     41.63275556609146,
     41.63808926467497,
     41.677487884305975,
     41.620591734015946,
     41.64931371437485,
     41.646890443474554,
     41.62404668544956,
     41.63964884250951,
     41.638477534601776,
     41.64332496247496,
     41.65260977469196,
     41.65248328671194,
     41.6474034449745,
     41.64926981833846,
     41.650740541708075,
     41.638807389014836,
     41.66374540604866,
     41.64886535549928,
     41.63265453864093,
     41.67281318904247,
     41.66895757951277,
     41.71496486522088,
     41.67007665525934,
     41.63484525009101,
     41.64060309287472,
     41.66210291413718,
     41.63348367532985,
     41.67593597602368,
     41.672106692157605,
     41.670796057267296,
     41.634304213138115,
     41.65154680743475,
     41.62152191885522,
     41.64737203882021,
     41.64583899054114,
     41.63444197353212,
     41.647668760113724,
     41.64713372980882,
     41.66759236644088,
     41.633156268397784,
     41.65815100896193,
     41.606852016162875,
     41.665547003703814,
     41.681817186609294,
     41.653142424569985,
     41.65471375662296,
     41.653113831884326,
     41.637370118574715,
     41.62307965046806,
     41.703559179288035,
     41.63800946128376,
     41.65509967011824,
     41.640231801283996,
     41.66399317788149,
     41.640202296609836,
     41.64045052143847,
     41.650342929846744,
     41.6515948922118,
     41.639588711692504,
     41.64547114097832,
     41.60941879505107,
     41.63594510671276,
     41.65806605032787,
     41.65124740456308,
     41.64919114164,
     41.68415187120862,
     41.64775005399505,
     41.647640923398896,
     41.64628513907135,
     41.646572275866276,
     41.64976600318248,
     41.653508476745046,
     41.647798885967035,
     41.64963422246641,
     41.63977012001253,
     41.670910841846876,
     41.62757051008441,
     41.65507219335992,
     41.65022964156985]



Y con este, las latitudes


```python
for i in df['geometry']:
    punto_coord = i.split(',')
    latitudes += [float(punto_coord[0])]
latitudes
```




    [-0.8818527060979306,
     -0.8645810716721081,
     -0.887776415002892,
     -0.8825260453930127,
     -0.908314757720389,
     -0.8691088511672924,
     -0.8880337913721866,
     -0.8708838775078237,
     -0.8970649943808023,
     -0.8718525605769747,
     -0.8964627561577849,
     -0.8778095796207178,
     -0.8812157329722801,
     -0.8762000299022707,
     -0.9089013552408617,
     -0.9004729973337304,
     -0.8917562993466011,
     -0.888856043735591,
     -0.8629911318784169,
     -0.8870207060655807,
     -0.8636325074780108,
     -0.8760724207544668,
     -0.9036852209830768,
     -0.8896980442453839,
     -0.9018264648858587,
     -0.9187726932212442,
     -0.8855988456901538,
     -0.887523212911549,
     -0.8863120908790753,
     -0.8689640327130923,
     -0.8900650666830714,
     -0.8918524618079099,
     -0.9104038365599549,
     -0.8850103896969528,
     -0.8734135018983006,
     -0.8593239531218387,
     -0.868891092151338,
     -0.9008107424460443,
     -0.9211220937948997,
     -0.9026681648170423,
     -0.8893162332922886,
     -0.8890866503471749,
     -0.8439506345833918,
     -0.8665477541801948,
     -0.8848493117953854,
     -0.9147014503640727,
     -0.9388159722509236,
     -0.9157439755527074,
     -0.8869959298557372,
     -0.876909940066992,
     -0.8816447317118501,
     -0.9072940747876611,
     -0.9297774953117621,
     -0.9260243926745974,
     -0.8747826613487039,
     -0.8808426934572774,
     -0.9244213411763852,
     -0.8837000032645412,
     -0.8949697510455706,
     -0.8586802458354249,
     -0.8824516125202209,
     -0.8857803278979575,
     -0.8901425582260953,
     -0.8853994844903159,
     -0.8988224291930889,
     -0.878399626737674,
     -0.9005718898973313,
     -0.8754417396680656,
     -0.8981774282134238,
     -0.9134005222660053,
     -0.9675955686913701,
     -0.8994494084124403,
     -0.9047634312813823,
     -0.8796660379583326,
     -0.8569442253224475,
     -0.8866382760165721,
     -0.9148179357831321,
     -0.91679280832361,
     -0.9831600853628304,
     -0.8805502979311851,
     -0.8834784288071386,
     -0.8907819329164345,
     -0.9129045578911849,
     -0.929341406599246,
     -0.9015144446496385,
     -0.8971281972974198,
     -0.8655422071013779,
     -0.9345679624034625,
     -0.9162444486972013,
     -0.9075234410781284,
     -0.8740118451885867,
     -0.8879390016835017,
     -0.8748263473540919,
     -0.893364249304231,
     -0.8793428209752854,
     -0.8990662796872798,
     -0.9072756956226459,
     -0.9226018969034585,
     -0.8735234620830842,
     -0.8869504077778204]



Con esta función crearemos un data frame de las coordenadas uniendo ambos puntos. 


```python
df_coord = pd.DataFrame({'long':longitudes,'lat':latitudes})
df_coord
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>long</th>
      <th>lat</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>41.649027</td>
      <td>-0.881853</td>
    </tr>
    <tr>
      <th>1</th>
      <td>41.661586</td>
      <td>-0.864581</td>
    </tr>
    <tr>
      <th>2</th>
      <td>41.666993</td>
      <td>-0.887776</td>
    </tr>
    <tr>
      <th>3</th>
      <td>41.629575</td>
      <td>-0.882526</td>
    </tr>
    <tr>
      <th>4</th>
      <td>41.656212</td>
      <td>-0.908315</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>95</th>
      <td>41.639770</td>
      <td>-0.899066</td>
    </tr>
    <tr>
      <th>96</th>
      <td>41.670911</td>
      <td>-0.907276</td>
    </tr>
    <tr>
      <th>97</th>
      <td>41.627571</td>
      <td>-0.922602</td>
    </tr>
    <tr>
      <th>98</th>
      <td>41.655072</td>
      <td>-0.873523</td>
    </tr>
    <tr>
      <th>99</th>
      <td>41.650230</td>
      <td>-0.886950</td>
    </tr>
  </tbody>
</table>
<p>100 rows × 2 columns</p>
</div>



Con la función concat, concatenaremos la columna type con la anterior tabla


```python
df_accidentes = pd.concat([df['type'],df_coord],axis=1) 
df_accidentes
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>type</th>
      <th>long</th>
      <th>lat</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>SALIDA CALZADA</td>
      <td>41.649027</td>
      <td>-0.881853</td>
    </tr>
    <tr>
      <th>1</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.661586</td>
      <td>-0.864581</td>
    </tr>
    <tr>
      <th>2</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.666993</td>
      <td>-0.887776</td>
    </tr>
    <tr>
      <th>3</th>
      <td>COLIS FRONTOLATERAL</td>
      <td>41.629575</td>
      <td>-0.882526</td>
    </tr>
    <tr>
      <th>4</th>
      <td>SALIDA CALZADA</td>
      <td>41.656212</td>
      <td>-0.908315</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>95</th>
      <td>OTRAS</td>
      <td>41.639770</td>
      <td>-0.899066</td>
    </tr>
    <tr>
      <th>96</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.670911</td>
      <td>-0.907276</td>
    </tr>
    <tr>
      <th>97</th>
      <td>SALIDA CALZADA</td>
      <td>41.627571</td>
      <td>-0.922602</td>
    </tr>
    <tr>
      <th>98</th>
      <td>COLIS FRONTOLATERAL</td>
      <td>41.655072</td>
      <td>-0.873523</td>
    </tr>
    <tr>
      <th>99</th>
      <td>SALIDA CALZADA</td>
      <td>41.650230</td>
      <td>-0.886950</td>
    </tr>
  </tbody>
</table>
<p>100 rows × 3 columns</p>
</div>



Ahora crearemos un mapa con un marcador. Utilizaremos la función marker, de folium. Llevará las coordenadas de Zaragoza y la información que queremos que se vea cuando hagamos click en el marcador. 


```python
marcador = folium.Marker(coords_zrgz, popup="¡Hola, Zaragoza!")
mapa = mapa.add_child(marcador)
mapa
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><span style="color:#565656">Make this Notebook Trusted to load map: File -> Trust Notebook</span><iframe src="about:blank" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" data-html=%3C%21DOCTYPE%20html%3E%0A%3Chead%3E%20%20%20%20%0A%20%20%20%20%3Cmeta%20http-equiv%3D%22content-type%22%20content%3D%22text/html%3B%20charset%3DUTF-8%22%20/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%3Cscript%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20L_NO_TOUCH%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20L_DISABLE_3D%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%3C/script%3E%0A%20%20%20%20%0A%20%20%20%20%3Cstyle%3Ehtml%2C%20body%20%7Bwidth%3A%20100%25%3Bheight%3A%20100%25%3Bmargin%3A%200%3Bpadding%3A%200%3B%7D%3C/style%3E%0A%20%20%20%20%3Cstyle%3E%23map%20%7Bposition%3Aabsolute%3Btop%3A0%3Bbottom%3A0%3Bright%3A0%3Bleft%3A0%3B%7D%3C/style%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//code.jquery.com/jquery-1.12.4.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js%22%3E%3C/script%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css%22/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cmeta%20name%3D%22viewport%22%20content%3D%22width%3Ddevice-width%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20initial-scale%3D1.0%2C%20maximum-scale%3D1.0%2C%20user-scalable%3Dno%22%20/%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cstyle%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%23map_a1020f0e5935425f9d7a557e4cf1147a%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20position%3A%20relative%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20width%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20height%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20left%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20top%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%3C/style%3E%0A%20%20%20%20%20%20%20%20%0A%3C/head%3E%0A%3Cbody%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cdiv%20class%3D%22folium-map%22%20id%3D%22map_a1020f0e5935425f9d7a557e4cf1147a%22%20%3E%3C/div%3E%0A%20%20%20%20%20%20%20%20%0A%3C/body%3E%0A%3Cscript%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20map_a1020f0e5935425f9d7a557e4cf1147a%20%3D%20L.map%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22map_a1020f0e5935425f9d7a557e4cf1147a%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20center%3A%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20crs%3A%20L.CRS.EPSG3857%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoom%3A%2010%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoomControl%3A%20true%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20preferCanvas%3A%20false%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20tile_layer_e7b550414ec54ceb9a57bb2c56809579%20%3D%20L.tileLayer%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22https%3A//%7Bs%7D.tile.openstreetmap.org/%7Bz%7D/%7Bx%7D/%7By%7D.png%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22attribution%22%3A%20%22Data%20by%20%5Cu0026copy%3B%20%5Cu003ca%20href%3D%5C%22http%3A//openstreetmap.org%5C%22%5Cu003eOpenStreetMap%5Cu003c/a%5Cu003e%2C%20under%20%5Cu003ca%20href%3D%5C%22http%3A//www.openstreetmap.org/copyright%5C%22%5Cu003eODbL%5Cu003c/a%5Cu003e.%22%2C%20%22detectRetina%22%3A%20false%2C%20%22maxNativeZoom%22%3A%2018%2C%20%22maxZoom%22%3A%2018%2C%20%22minZoom%22%3A%200%2C%20%22noWrap%22%3A%20false%2C%20%22opacity%22%3A%201%2C%20%22subdomains%22%3A%20%22abc%22%2C%20%22tms%22%3A%20false%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a1020f0e5935425f9d7a557e4cf1147a%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_72c03b4b585d4d179b80737f8322a835%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_a1020f0e5935425f9d7a557e4cf1147a%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_9159d7e41f424b9a85cc2ceb7568cb69%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_9770ec6a9e6f484d9f6cdce89b387b2e%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_9770ec6a9e6f484d9f6cdce89b387b2e%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3E%C2%A1Hola%2C%20Zaragoza%21%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_9159d7e41f424b9a85cc2ceb7568cb69.setContent%28html_9770ec6a9e6f484d9f6cdce89b387b2e%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_72c03b4b585d4d179b80737f8322a835.bindPopup%28popup_9159d7e41f424b9a85cc2ceb7568cb69%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%3C/script%3E onload="this.contentDocument.open();this.contentDocument.write(    decodeURIComponent(this.getAttribute('data-html')));this.contentDocument.close();" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>



Con el siguiente bucle crearemos un mapa con cada uno de los puntos de nuestra tabla. Importamos los datos de la url, marcamos las coordenadas y le pedimos que nos muestre los datos que nos interesa. 


```python
url = 'https://www.zaragoza.es/sede/servicio/transporte/accidentalidad-trafico/accidente.csv?rows=20'
coord = [41.64,-0.88]
mapa = folium.Map(location=coord)
df = pd.read_csv(url,delimiter=';')
longitudes = []
for i in df['geometry']:
    longlat = i.split(',')
    longitudes += [float(longlat[0])]
latitudes = []
for i in df['geometry']:
    longlat = i.split(',')
    latitudes += [float(longlat[1])]
df_coord = pd.DataFrame({'long':longitudes, 'lat':latitudes})
df_tipo = pd.concat([df['type'],df_coord],axis=1)
for index, fila in df_tipo.iterrows():
    marcador = folium.Marker([fila['lat'],fila['long']],popup=fila['type'])
    mapa.add_child(marcador)
mapa
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><span style="color:#565656">Make this Notebook Trusted to load map: File -> Trust Notebook</span><iframe src="about:blank" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" data-html=%3C%21DOCTYPE%20html%3E%0A%3Chead%3E%20%20%20%20%0A%20%20%20%20%3Cmeta%20http-equiv%3D%22content-type%22%20content%3D%22text/html%3B%20charset%3DUTF-8%22%20/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%3Cscript%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20L_NO_TOUCH%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20L_DISABLE_3D%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%3C/script%3E%0A%20%20%20%20%0A%20%20%20%20%3Cstyle%3Ehtml%2C%20body%20%7Bwidth%3A%20100%25%3Bheight%3A%20100%25%3Bmargin%3A%200%3Bpadding%3A%200%3B%7D%3C/style%3E%0A%20%20%20%20%3Cstyle%3E%23map%20%7Bposition%3Aabsolute%3Btop%3A0%3Bbottom%3A0%3Bright%3A0%3Bleft%3A0%3B%7D%3C/style%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//code.jquery.com/jquery-1.12.4.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js%22%3E%3C/script%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css%22/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cmeta%20name%3D%22viewport%22%20content%3D%22width%3Ddevice-width%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20initial-scale%3D1.0%2C%20maximum-scale%3D1.0%2C%20user-scalable%3Dno%22%20/%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cstyle%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%23map_96612fdd4b174c22b677585d57f26fed%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20position%3A%20relative%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20width%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20height%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20left%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20top%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%3C/style%3E%0A%20%20%20%20%20%20%20%20%0A%3C/head%3E%0A%3Cbody%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cdiv%20class%3D%22folium-map%22%20id%3D%22map_96612fdd4b174c22b677585d57f26fed%22%20%3E%3C/div%3E%0A%20%20%20%20%20%20%20%20%0A%3C/body%3E%0A%3Cscript%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20map_96612fdd4b174c22b677585d57f26fed%20%3D%20L.map%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22map_96612fdd4b174c22b677585d57f26fed%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20center%3A%20%5B41.64%2C%20-0.88%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20crs%3A%20L.CRS.EPSG3857%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoom%3A%2010%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoomControl%3A%20true%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20preferCanvas%3A%20false%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20tile_layer_7fbbccc788ca4884af8347315c791f53%20%3D%20L.tileLayer%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22https%3A//%7Bs%7D.tile.openstreetmap.org/%7Bz%7D/%7Bx%7D/%7By%7D.png%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22attribution%22%3A%20%22Data%20by%20%5Cu0026copy%3B%20%5Cu003ca%20href%3D%5C%22http%3A//openstreetmap.org%5C%22%5Cu003eOpenStreetMap%5Cu003c/a%5Cu003e%2C%20under%20%5Cu003ca%20href%3D%5C%22http%3A//www.openstreetmap.org/copyright%5C%22%5Cu003eODbL%5Cu003c/a%5Cu003e.%22%2C%20%22detectRetina%22%3A%20false%2C%20%22maxNativeZoom%22%3A%2018%2C%20%22maxZoom%22%3A%2018%2C%20%22minZoom%22%3A%200%2C%20%22noWrap%22%3A%20false%2C%20%22opacity%22%3A%201%2C%20%22subdomains%22%3A%20%22abc%22%2C%20%22tms%22%3A%20false%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_16bb4c1db0544f4e9319755227200296%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.649027473051156%2C%20-0.8818527060979306%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_e9f82b2d0acd4bfab7961eb89eed5aa6%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_28883a1f945c44469a9f35c57025de7d%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_28883a1f945c44469a9f35c57025de7d%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_e9f82b2d0acd4bfab7961eb89eed5aa6.setContent%28html_28883a1f945c44469a9f35c57025de7d%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_16bb4c1db0544f4e9319755227200296.bindPopup%28popup_e9f82b2d0acd4bfab7961eb89eed5aa6%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_b3410f2bb4a24e7dac32a3f36e136628%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.661585829868585%2C%20-0.8645810716721081%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_3408adc1fb2f4cf498d5bc4322d66584%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_87435ed788014793bd97571a3ba81701%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_87435ed788014793bd97571a3ba81701%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_3408adc1fb2f4cf498d5bc4322d66584.setContent%28html_87435ed788014793bd97571a3ba81701%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_b3410f2bb4a24e7dac32a3f36e136628.bindPopup%28popup_3408adc1fb2f4cf498d5bc4322d66584%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_bdb7215d2b62444796d519dde2e4af3f%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.666992622958105%2C%20-0.887776415002892%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_b3b790a07d6045a0a3d2668e5c2e8652%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_0ade015c7f844a2998c9db79a7e519f5%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_0ade015c7f844a2998c9db79a7e519f5%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_b3b790a07d6045a0a3d2668e5c2e8652.setContent%28html_0ade015c7f844a2998c9db79a7e519f5%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_bdb7215d2b62444796d519dde2e4af3f.bindPopup%28popup_b3b790a07d6045a0a3d2668e5c2e8652%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_7b784add3ae24859846d9d7cb36aad8e%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.62957498750602%2C%20-0.8825260453930127%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_a30cae273319446a9512bf324017b815%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_5542318da16c4cc59f4336b34d1cffd2%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_5542318da16c4cc59f4336b34d1cffd2%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS%20FRONTOLATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_a30cae273319446a9512bf324017b815.setContent%28html_5542318da16c4cc59f4336b34d1cffd2%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_7b784add3ae24859846d9d7cb36aad8e.bindPopup%28popup_a30cae273319446a9512bf324017b815%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_8322c58a428842d78e189079dc2fd980%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.6562121210704%2C%20-0.908314757720389%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_1d871b4ed7ba44f4989b5d9a548929d5%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_d4dd588d55c442a08d90a759c3ffd452%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_d4dd588d55c442a08d90a759c3ffd452%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_1d871b4ed7ba44f4989b5d9a548929d5.setContent%28html_d4dd588d55c442a08d90a759c3ffd452%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_8322c58a428842d78e189079dc2fd980.bindPopup%28popup_1d871b4ed7ba44f4989b5d9a548929d5%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_abf6475a880049b8945e5cdcc69ff79c%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.65949772773082%2C%20-0.8691088511672924%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_ad7372aab6e44901a5f9d584ed3ebe6f%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_609ef02f9a52456381fad744e53cd4b6%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_609ef02f9a52456381fad744e53cd4b6%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_ad7372aab6e44901a5f9d584ed3ebe6f.setContent%28html_609ef02f9a52456381fad744e53cd4b6%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_abf6475a880049b8945e5cdcc69ff79c.bindPopup%28popup_ad7372aab6e44901a5f9d584ed3ebe6f%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_c7a8852d659f42aba251f3672cd7fda7%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.633353667694024%2C%20-0.8880337913721866%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_ee44e53c7027458585dddfe04dac4ff5%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_fd966121ff65495eacc922909cb737e3%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_fd966121ff65495eacc922909cb737e3%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_ee44e53c7027458585dddfe04dac4ff5.setContent%28html_fd966121ff65495eacc922909cb737e3%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_c7a8852d659f42aba251f3672cd7fda7.bindPopup%28popup_ee44e53c7027458585dddfe04dac4ff5%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_c04050ef6bb24a24b99bce8ffb8ac84d%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.6390382112928%2C%20-0.8708838775078237%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_8e54d791f9024e0cb2509c3f3599c9ec%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_47fdffb18ce344a78b7ab25a5840353e%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_47fdffb18ce344a78b7ab25a5840353e%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECAIDA%20SOBRE%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_8e54d791f9024e0cb2509c3f3599c9ec.setContent%28html_47fdffb18ce344a78b7ab25a5840353e%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_c04050ef6bb24a24b99bce8ffb8ac84d.bindPopup%28popup_8e54d791f9024e0cb2509c3f3599c9ec%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_630253893de34d11aece3630985ead8d%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.64083344974765%2C%20-0.8970649943808023%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_f94ad1c055bc4cf2986fe83ed14f0f0a%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_31f0931196a54646bd984f94c671a6a6%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_31f0931196a54646bd984f94c671a6a6%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS.%20MARCHA%20ATR%C3%81S%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_f94ad1c055bc4cf2986fe83ed14f0f0a.setContent%28html_31f0931196a54646bd984f94c671a6a6%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_630253893de34d11aece3630985ead8d.bindPopup%28popup_f94ad1c055bc4cf2986fe83ed14f0f0a%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_fd77d0fb548946d9a885d546e88cdcd9%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.64904657717317%2C%20-0.8718525605769747%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_072d5e9406ed4077b50f353c606022db%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_8aa797a53e5b4d68a2b26f5a2ee97a9c%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_8aa797a53e5b4d68a2b26f5a2ee97a9c%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20LATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_072d5e9406ed4077b50f353c606022db.setContent%28html_8aa797a53e5b4d68a2b26f5a2ee97a9c%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_fd77d0fb548946d9a885d546e88cdcd9.bindPopup%28popup_072d5e9406ed4077b50f353c606022db%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_76c4f8602d86434d97e9cc7fc13cdb52%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.64322365075108%2C%20-0.8964627561577849%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_d99036bb21ae4acebe165348e5443ce7%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_0f9f62d6bb2044088d4d8ac7ff7cce41%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_0f9f62d6bb2044088d4d8ac7ff7cce41%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_d99036bb21ae4acebe165348e5443ce7.setContent%28html_0f9f62d6bb2044088d4d8ac7ff7cce41%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_76c4f8602d86434d97e9cc7fc13cdb52.bindPopup%28popup_d99036bb21ae4acebe165348e5443ce7%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_6571a8f46d6640509539c00fbbee5bd9%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.68753087470739%2C%20-0.8778095796207178%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_80ff62fe161e43ed83d74b57f53b55fc%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_18808b70de43485aa6ba9181a948210b%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_18808b70de43485aa6ba9181a948210b%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_80ff62fe161e43ed83d74b57f53b55fc.setContent%28html_18808b70de43485aa6ba9181a948210b%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_6571a8f46d6640509539c00fbbee5bd9.bindPopup%28popup_80ff62fe161e43ed83d74b57f53b55fc%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_68c4f55c43b145709d085502bb467c39%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.661646612715046%2C%20-0.8812157329722801%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_c2549242d7004fe884ab14c88536f50e%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_701738dc15e14f5caf7a0ecc372dc547%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_701738dc15e14f5caf7a0ecc372dc547%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_c2549242d7004fe884ab14c88536f50e.setContent%28html_701738dc15e14f5caf7a0ecc372dc547%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_68c4f55c43b145709d085502bb467c39.bindPopup%28popup_c2549242d7004fe884ab14c88536f50e%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_b739ea9f209348eeaea91a9b0bd3a7e2%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.6454384961757%2C%20-0.8762000299022707%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_5303ddff3ce64621b5582d057efad58b%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_9ef7cdf4301c432c93bb195a387165bb%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_9ef7cdf4301c432c93bb195a387165bb%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_5303ddff3ce64621b5582d057efad58b.setContent%28html_9ef7cdf4301c432c93bb195a387165bb%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_b739ea9f209348eeaea91a9b0bd3a7e2.bindPopup%28popup_5303ddff3ce64621b5582d057efad58b%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_39e924f4b3914082a9bc0e9829df7050%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.65543768899759%2C%20-0.9089013552408617%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_a8e27c0f637c46d6bb0a8a539cfb744a%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_decc56b3b71e41f99c17a04d05ee6a38%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_decc56b3b71e41f99c17a04d05ee6a38%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_a8e27c0f637c46d6bb0a8a539cfb744a.setContent%28html_decc56b3b71e41f99c17a04d05ee6a38%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_39e924f4b3914082a9bc0e9829df7050.bindPopup%28popup_a8e27c0f637c46d6bb0a8a539cfb744a%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_e653b82fb69e461586fa365ea85e5972%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.65180346604993%2C%20-0.9004729973337304%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_eef8936586af4d65b8f89a48d2891fba%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_9039d2714aa74c16ace1af5a7489b6ae%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_9039d2714aa74c16ace1af5a7489b6ae%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_eef8936586af4d65b8f89a48d2891fba.setContent%28html_9039d2714aa74c16ace1af5a7489b6ae%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_e653b82fb69e461586fa365ea85e5972.bindPopup%28popup_eef8936586af4d65b8f89a48d2891fba%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_0793723e3ea64f9eb37aaef07aee84b4%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.65233828238132%2C%20-0.8917562993466011%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_f8d8c04b0ceb4baa807cbd67acaaad5e%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_cf3ea5f7ad0048a9914924a1426d1088%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_cf3ea5f7ad0048a9914924a1426d1088%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_f8d8c04b0ceb4baa807cbd67acaaad5e.setContent%28html_cf3ea5f7ad0048a9914924a1426d1088%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_0793723e3ea64f9eb37aaef07aee84b4.bindPopup%28popup_f8d8c04b0ceb4baa807cbd67acaaad5e%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_2894d612424849b6bd97fca02eb27250%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.65040494617356%2C%20-0.888856043735591%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_e4beb237331f4fd6b42eb01dc8102d3d%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_9a9558ece6b44447b26cbc7fdbdfce36%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_9a9558ece6b44447b26cbc7fdbdfce36%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_e4beb237331f4fd6b42eb01dc8102d3d.setContent%28html_9a9558ece6b44447b26cbc7fdbdfce36%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_2894d612424849b6bd97fca02eb27250.bindPopup%28popup_e4beb237331f4fd6b42eb01dc8102d3d%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_2dc7937fd6b24f0685ef698cbc9f5124%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.645335650478316%2C%20-0.8629911318784169%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_7f625ca52f054b59a6f120dd2da1516a%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_aa8ffc5377fe4e47bf440cd161d694b6%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_aa8ffc5377fe4e47bf440cd161d694b6%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_7f625ca52f054b59a6f120dd2da1516a.setContent%28html_aa8ffc5377fe4e47bf440cd161d694b6%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_2dc7937fd6b24f0685ef698cbc9f5124.bindPopup%28popup_7f625ca52f054b59a6f120dd2da1516a%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_680fd452864d46b586dcef8b789df8a9%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.609992514227066%2C%20-0.8870207060655807%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_96612fdd4b174c22b677585d57f26fed%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_f6020c7a42554abeba9a79df07066356%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_a2ba9cf6b6e14e42a543dca95b4b7c34%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_a2ba9cf6b6e14e42a543dca95b4b7c34%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_f6020c7a42554abeba9a79df07066356.setContent%28html_a2ba9cf6b6e14e42a543dca95b4b7c34%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_680fd452864d46b586dcef8b789df8a9.bindPopup%28popup_f6020c7a42554abeba9a79df07066356%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%3C/script%3E onload="this.contentDocument.open();this.contentDocument.write(    decodeURIComponent(this.getAttribute('data-html')));this.contentDocument.close();" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>



Por último, intentaremos que nos muestre un mapa con otras coordenadas. En este caso, pondremos el marcador en las del Estadio Santiago Bernabéu. Utilizaremos el siguiente bucle para ello. Con la función Marker nos situará el marcador allí y con la función Icon podremos cambiar el color del marcador. 


```python
coord = [40.4494478,-3.6893706]
mapa = folium.Map (location=coord, tiles='Stamen Terrain')
marcador = folium.Marker (coord, icon=folium.Icon(color="green"))
mapa = mapa.add_child (marcador)
mapa
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><span style="color:#565656">Make this Notebook Trusted to load map: File -> Trust Notebook</span><iframe src="about:blank" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" data-html=%3C%21DOCTYPE%20html%3E%0A%3Chead%3E%20%20%20%20%0A%20%20%20%20%3Cmeta%20http-equiv%3D%22content-type%22%20content%3D%22text/html%3B%20charset%3DUTF-8%22%20/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%3Cscript%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20L_NO_TOUCH%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20L_DISABLE_3D%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%3C/script%3E%0A%20%20%20%20%0A%20%20%20%20%3Cstyle%3Ehtml%2C%20body%20%7Bwidth%3A%20100%25%3Bheight%3A%20100%25%3Bmargin%3A%200%3Bpadding%3A%200%3B%7D%3C/style%3E%0A%20%20%20%20%3Cstyle%3E%23map%20%7Bposition%3Aabsolute%3Btop%3A0%3Bbottom%3A0%3Bright%3A0%3Bleft%3A0%3B%7D%3C/style%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//code.jquery.com/jquery-1.12.4.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js%22%3E%3C/script%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css%22/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cmeta%20name%3D%22viewport%22%20content%3D%22width%3Ddevice-width%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20initial-scale%3D1.0%2C%20maximum-scale%3D1.0%2C%20user-scalable%3Dno%22%20/%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cstyle%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%23map_0f11a0fd2816415ebd68e6798a23aad9%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20position%3A%20relative%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20width%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20height%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20left%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20top%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%3C/style%3E%0A%20%20%20%20%20%20%20%20%0A%3C/head%3E%0A%3Cbody%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cdiv%20class%3D%22folium-map%22%20id%3D%22map_0f11a0fd2816415ebd68e6798a23aad9%22%20%3E%3C/div%3E%0A%20%20%20%20%20%20%20%20%0A%3C/body%3E%0A%3Cscript%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20map_0f11a0fd2816415ebd68e6798a23aad9%20%3D%20L.map%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22map_0f11a0fd2816415ebd68e6798a23aad9%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20center%3A%20%5B40.4494478%2C%20-3.6893706%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20crs%3A%20L.CRS.EPSG3857%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoom%3A%2010%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoomControl%3A%20true%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20preferCanvas%3A%20false%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20tile_layer_0928cc9be2fa4a3b95172a15607006e3%20%3D%20L.tileLayer%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22https%3A//stamen-tiles-%7Bs%7D.a.ssl.fastly.net/terrain/%7Bz%7D/%7Bx%7D/%7By%7D.jpg%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22attribution%22%3A%20%22Map%20tiles%20by%20%5Cu003ca%20href%3D%5C%22http%3A//stamen.com%5C%22%5Cu003eStamen%20Design%5Cu003c/a%5Cu003e%2C%20under%20%5Cu003ca%20href%3D%5C%22http%3A//creativecommons.org/licenses/by/3.0%5C%22%5Cu003eCC%20BY%203.0%5Cu003c/a%5Cu003e.%20Data%20by%20%5Cu0026copy%3B%20%5Cu003ca%20href%3D%5C%22http%3A//openstreetmap.org%5C%22%5Cu003eOpenStreetMap%5Cu003c/a%5Cu003e%2C%20under%20%5Cu003ca%20href%3D%5C%22http%3A//creativecommons.org/licenses/by-sa/3.0%5C%22%5Cu003eCC%20BY%20SA%5Cu003c/a%5Cu003e.%22%2C%20%22detectRetina%22%3A%20false%2C%20%22maxNativeZoom%22%3A%2018%2C%20%22maxZoom%22%3A%2018%2C%20%22minZoom%22%3A%200%2C%20%22noWrap%22%3A%20false%2C%20%22opacity%22%3A%201%2C%20%22subdomains%22%3A%20%22abc%22%2C%20%22tms%22%3A%20false%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_0f11a0fd2816415ebd68e6798a23aad9%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_59a19472c0034e11830578d24cbc8d72%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B40.4494478%2C%20-3.6893706%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_0f11a0fd2816415ebd68e6798a23aad9%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20icon_b10d976f6eb1485f8abc10c7efefe870%20%3D%20L.AwesomeMarkers.icon%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22extraClasses%22%3A%20%22fa-rotate-0%22%2C%20%22icon%22%3A%20%22info-sign%22%2C%20%22iconColor%22%3A%20%22white%22%2C%20%22markerColor%22%3A%20%22green%22%2C%20%22prefix%22%3A%20%22glyphicon%22%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20marker_59a19472c0034e11830578d24cbc8d72.setIcon%28icon_b10d976f6eb1485f8abc10c7efefe870%29%3B%0A%20%20%20%20%20%20%20%20%0A%3C/script%3E onload="this.contentDocument.open();this.contentDocument.write(    decodeURIComponent(this.getAttribute('data-html')));this.contentDocument.close();" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>


