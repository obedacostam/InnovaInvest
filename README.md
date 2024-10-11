# InnovaInvest
# COSECHAS 4,0 Agricultura Familiar Conectada: 
# Plataforma Web para Optimizar Cultivos con NDVI y NDWI

# Integrantes del Grupo3

1. Omar Perez
2. Octavio Smith
3. Obed Acosta

## Casos de estudio

Cuenca del río Grande en el área Central de Panamá

### Objetivo General

"Desarrollar una plataforma web innovadora y accesible para agricultores familiares, basada en cálculos de los índices NDVI y NDWI, que les permita mejorar la toma de decisiones y optimizar el manejo de cultivos mediante el monitoreo de la salud de las plantas y la disponibilidad de agua en sus terrenos agrícolas ee identificar posibles zonas inundables en el area."


### Objetivos Específicos

* Desarrollar la plataforma web: Crear una plataforma en línea que sea intuitiva, fácil de usar y accesible desde diversos dispositivos    (como computadoras, tabletas y teléfonos móviles) para garantizar que los agricultores familiares puedan acceder a ella y utilizarla de manera efectiva.
*  Integrar datos de teledetección: Automatizar la descarga de datos de los satilites y delimitados por las parcelas que el usuario seleccione.
* Identificar la calidad de la cobertura vegetal
* Identificar las potencialidades de concentración de agua superficial
* Definir los principales usos de suelo
* Delimitación de áreas de inundación por influencia topográfica
* Establecer bases de datos de parcelas agrícolas
* Implementar alertas y notificaciones cuando se detecten cambios significativos en los índices NDVI y NDWI, señalando posibles situaciones de estrés hídrico o problemas en el crecimiento de los cultivos.
* Facilitar la interacción y colaboración al implementar funciones de interacción social en la plataforma para que los agricultores familiares puedan compartir experiencias, hacer preguntas y recibir asesoramiento de otros agricultores y expertos agrícolas.

## Metodología

### Planteamiento del problema

En la actualidad nuestros agricultores se enfrentan a retos nunca antes vistos, fenómenos climáticos extremos como sequias, inundaciones, Ciclones tropicales, degradación de la tierra, entre otros. Estos fenómenos naturales alteran en gran medida los valores nutricionales y químicos de los suelos en que los cultivos regularmente se desarrollan. 
Es por esto que se hace necesaria una herramienta que le permita al agricultor poder recibir alertas sobre las variaciones de las condiciones del suelo y poder monitorear de manera constante la salud de los cultivos y el comportamiento de los recursos hídricos existentes.
Nosotros proponemos una solución basada en una plataforma web innovadora y accesible que sea fácil de usar y que esté disponible para los agricultores, incluso aquellos con recursos limitados o acceso a Internet restringido, 
Por medio de esta herramienta, los agricultores se verán beneficiados con productos como la generación de alertas y notificaciones que los pongan sobre aviso cuando se detecten cambios significativos en los índices NDVI y NDWI, señalando posibles situaciones de estrés hídrico o problemas en el crecimiento de los cultivos.
Además, tendrán información sobre los riesgos existentes de áreas inundables y don esta información a la mano puedan decidir los lugares adecuados para sembrar sin caer en pérdidas de inversión.
Otro beneficio a obtener es que habilita la posibilidad de almacenar y visualizar datos históricos de los índices calculados y de esta manera hacer un análisis comparativo y comprender mejor las tendencias estacionales y anuales de estos índices.
Es importante mencionar que la información geoespacial estará disponible para el agricultor casi en tiempo real para el monitoreo adecuado de la salud de sus cultivos, 
Debemos apoyar de manera intencional al agricultor familiar ya que es un engranaje importante dentro de la economía de nuestros países.

## Procedimiento

1. Delimitacion de Zonas agricolas mediante el uso de mapa de cobertura boscosa y uso de suelo gestionando de información de carácter satelital del sitio de Copernicus y procesadas en QGIS 3.22

<img src="./docs/images/landcover.png" />

2. Calculamos el Índice Normalizado de Diferencia de Vegetación, utilizando codigos en Python

NDVI = (NIR-Red) / (NIR+Red)

NIR=  luz del infrarrojo cercano y 
Rojo= luz roja visible

Entre los valores de referencia de índice que se interpretarán calculando el NDVI, se encuentran los siguientes:

 | Min | Max  |         State               |
|------|------|-----------------------------|
| 0.1  | 0.2  | Suelo desnudo               |
| 0.2  |  1   |   Plantas                   |
| 0.5  | 0.5  | Vegetación densa y saludable|
| 0.2  | 0.5  | Vegetación dispersa         |

Valores negativos = Concentración de agua, estructuras artificiales y rocas entre otros.

<img src="./docs/images/NDVI.png" />

4. Cálculo de Índice de Agua de Diferencia Normalizada (NDWI), con la finalidad de identificar concentraciones de  agua sobre la superficie de la tierra.  Se aplicará la siguiente fórmula

NDWI = (Green – NIR)/(Green + NIR)

Green = luz de banda verde
NIR = luz del infrarrojo cercano

| Min | Max  |         State                        |
|------|-----|--------------------------------------|
| 0.2  | 1   | Superficie del agua                  |
| 0,0  | 0,2 |  Inundación, humedad                 |
|- 0,3 | 0,0 | Sequía moderada, superficies sin agua| 
| -1   | -0,3| Sequía, superficies sin agua         |




<img src="./docs/images/NDWI.png" />


5. Gestión de Modelo de Elevación Digital de 30 m, en el sitio de COPERNICUS 
(https://portal.opentopography.org/login), para calcular el Índice de Humedad del Terreno por el carácter topográfico


7. Gestión de Clasificación supervisada de imágenes Sentinel – 2 del 2021 a través del sitio 

https://viewer.esa-worldcover.org/worldcover/?language=en&bbox=-125.98451880201398,-64.41009987194155,91.3619876655554,17.92225321411891&overlay=false&bgLayer=OSM&date=2023-07-21&layer=WORLDCOVER_2021_MAP

8. Gestión de Datos de Carácter Climático
Otros sitios de referencia de Copernicus

https://emergency.copernicus.eu/

https://www.globalfloods.eu/glofas-forecasting/

https://viewer.esa-worldcover.org/worldcover/?language=en&bbox=-125.98451880201398,-64.41009987194155,91.3619876655554,17.92225321411891&overlay=false&bgLayer=OSM&date=2023-07-21&layer=WORLDCOVER_2021_MAP

https://edo.jrc.ec.europa.eu/tumbo/gdo/map/

