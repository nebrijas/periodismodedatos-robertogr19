# ACTIVIDAD DIRIGIDA 2

Para explicar lo que hemos hecho en nuestro notebook de Jupyter escribiremos el código en bruto en este apartado. 

## LIBRERÍAS
En primer lugar importaremos las librerías. Es necesario para identificar con qué web queremos hacer el scrapping. 
Las dos librerías que importaremos serán **requests** y **BeautifulSoup**. La primera para identificar cómo queremos hacer el scrapping y la segunda para extraer la información en formato HTML o XML.

## VARIABLES
Copiamos la URL donde se encuentran los datos que necesitamos. A ella haremos la petición **request.get** para obtener todos los datos. En este punto le pediremos al código que nos avise cuando no nos permita hacer el scrapping.

## DATOS
Elegiremos las variables que queremos obtener. **Oros**, **platas**, **bronces** y **total medallas**. Para ello necesitaremos identificarlas en el HTML de la URL. Con la función **find_all()** las podremos encontrar fácilmente. 

## PREGUNTA
La escribiremos para conseguir la itneracción del usuario y que este sepa lo que le estamos mostrando. Si éste teclea **s** continuará el scrapping, si pulsa otra tecla no continuará.

## CÓDIGO EN BRUTO
from bs4 import BeautifulSoup
import requests
#Datos sobre los Juegos Olímpicos en 2020

respuesta=input('¿QUIERES CONOCER LOS 20 PAÍSES QUE HAN OBTENIDO MÁS MEDALLAS EN 2020?\n \n Si tu respuesta es Sí, presiona "s" \n')
if(respuesta == 's'):
  print('\nRESULTADOS DE LOS DATOS DE LOS JUEGOS OLÍMPICOS 2020\n')
  print ('PAÍSES')
  URL = "https://resultados.elpais.com/deportivos/juegos-olimpicos/medallero/"
  # Realizamos la petición a la web
  req = requests.get(URL)
  # Si el estatus code no es 200 no se puede leer la página
  if (req.status_code != 200):
    raise Exception("No se puede hacer Web Scraping en"+ URL)
  # Pasamos el contenido HTML de la web a un objeto BeautifulSoup()
  html = BeautifulSoup(req.text, "html.parser")
  # Obtenemos todos los divs donde están las entradas
  paises = html.find_all("th",{"class":"pais"})
  oros = html.find_all("td",{"class":"m_oro"})
  platas = html.find_all("td",{"class":"m_plata"})
  bronces = html.find_all("td",{"class":"m_bronce"})
  totales = html.find_all("td",{"class":"m_total"})
  for i in range (20):
    # Con el método "getText()" no nos devuelve el HTML
    print("%d. %s \nOro: %s Plata: %s Bronce: %s \n Total: %s \n " % (i+1, paises[i+1].text.strip(),oros[i].text.strip(),platas[i].text.strip(),bronces[i].text.strip(), totales[i].text.strip()))

else:
  print('Qué lástima, y...')
