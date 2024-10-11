# InnovaInvest
# COSECHAS 4,0 Agricultura Familiar Conectada: 
# Plataforma Web para Optimizar Cultivos con NDVI, NDMI y NDWI

# Integrantes del Grupo3

1. Omar Perez
2. Octavio Smith
3. Obed Acosta

## Casos de estudio
"Plataforma innovadora y accesible para agricultores familiares de la Cuenca del río Grande en el área Central de Panamá, basada en cálculos de los índices NDVI, NDMI y NDWI, que les permita mejorar la toma de decisiones y optimizar el manejo de cultivos mediante el monitoreo de la salud de las plantas y la disponibilidad de agua en sus terrenos agrícolas e identificar posibles zonas inundables en el la parcela seleccionada."

### Objetivo General

"Desarrollar una plataforma web innovadora y accesible para los agricultores familiares de la cuenca del Río Grande en Panamá, que integre datos de teledetección (NDVI, NDMI y NDWI) y pronósticos climáticos, facilitando la toma de decisiones informadas sobre el manejo de cultivos, monitoreo de la salud de las plantas, disponibilidad de agua, épocas de siembra y cosecha, y la identificación de zonas inundables, promoviendo una agricultura sostenible en respuesta al cambio climático."


### Objetivos Específicos

* Desarrollar una plataforma web intuitiva y accesible: Crear una plataforma digital de fácil uso que permita a los agricultores familiares acceder a información clave sobre sus cultivos y suelos, compatible con dispositivos como computadoras, tabletas y teléfonos móviles, con capacidad para trabajar en entornos de baja conectividad.
* Automatizar la integración de datos de teledetección: Implementar un sistema que descargue, procese y analice de manera automática los datos de satélites sobre las parcelas seleccionadas por los usuarios, utilizando índices NDVI (Índice de Vegetación de Diferencia Normalizada), NDMI( Índice de Humedad de Diferencia Normalizada) y NDWI (Índice de Diferencia de Agua Normalizada) para monitorear la salud de la vegetación y la humedad del suelo.
* Monitorear la salud de los cultivos en tiempo real: Proveer herramientas para el monitoreo continuo del estado de la cobertura vegetal de las parcelas, usando NDVI para evaluar el crecimiento de los cultivos y emitir alertas tempranas en caso de identificar problemas como estrés hídrico o baja calidad de la vegetación.
* Evaluar y pronosticar la disponibilidad de agua: Analizar las condiciones de humedad del suelo mediante NDWI y pronósticos climáticos, para informar a los agricultores sobre la disponibilidad de agua o inundación en sus parcelas.
* Delimitar áreas propensas a inundaciones: Definir zonas de riesgo de inundación basadas en análisis topográficos, ayudando a los agricultores a planificar mejor sus cultivos y evitar pérdidas debido a fenómenos climáticos extremos.
* Identificar estrés hídrico antes de que sea visible a simple vista. Este tipo de estrés ocurre cuando las plantas no tienen suficiente agua, lo que puede afectar negativamente su crecimiento y rendimiento. El monitoreo continuo con NDMI puede ayudar a detectar este problema y tomar medidas correctivas, como el riego.
* Ofrecer recomendaciones personalizadas sobre cultivos: Desarrollar un sistema de sugerencias basado en datos históricos y climáticos para orientar a los agricultores en la elección de cultivos adecuados, teniendo en cuenta la época del año, las condiciones del suelo y el clima pronosticado.
* Facilitar la planificación de siembras y cosechas: Implementar funciones para estimar el tiempo óptimo de siembra y cosecha basado en datos de crecimiento de los cultivos y las condiciones climáticas, mejorando la eficiencia de los ciclos de producción agrícola.
* Crear un espacio de interacción y colaboración: Establecer funciones de interacción social en la plataforma que permitan a los agricultores compartir experiencias, hacer preguntas y recibir asesoramiento de otros agricultores y expertos en agricultura.
* Almacenar y gestionar datos históricos: Desarrollar una base de datos que almacene datos históricos de los cultivos y las condiciones de las parcelas, permitiendo a los agricultores realizar análisis comparativos y optimizar su planificación agrícola a largo plazo.

## Población Meta
"La población meta principal son los agricultores familiares de la cuenca del río Grande, en la región central de Panamá. Estos agricultores dependen de pequeños terrenos y practican agricultura a pequeña escala, con recursos limitados y muchas veces sin acceso a tecnologías avanzadas. La plataforma está diseñada específicamente para ayudarles a mejorar la eficiencia de su producción, enfrentar los desafíos del cambio climático y tomar decisiones informadas sobre el manejo de sus cultivos y recursos hídricos."

## Componentes y Metodologías Generales.

### 1. Evaluación de Suelo y Recomendación de Cultivo
#### Objetivo: 
Antes de la siembra, evaluar la calidad del suelo de la parcela y, basándose en la época del año, datos históricos de cultivos en la zona y la información climática pronosticada, sugerir el cultivo más adecuado.
#### Metodología:
1. Base de datos de suelos y cultivos locales: Crea una base de datos con información detallada sobre las características del suelo en la zona (pH, nutrientes, capacidad de retención de agua, etc.) y los cultivos que se han sembrado exitosamente en la región. Esto se puede hacer a través de estudios previos o recopilando datos directamente de los agricultores.
2. Recomendaciones basadas en reglas: Configura reglas simples que comparen las características del suelo y el clima con las necesidades de cada cultivo. Por ejemplo, si la época es temporada seca y el suelo tiene buen drenaje, la plataforma puede sugerir un cultivo que necesite menos agua, como maíz o frijoles.
3. Pronóstico climático: Utiliza datos meteorológicos públicos para proporcionar información sobre las condiciones climáticas esperadas durante el ciclo de cultivo, y ajustar las recomendaciones según los cultivos más resistentes a las condiciones previstas.
#### Interfaz: 
Una vez que el agricultor seleccione su parcela en la plataforma, el sistema puede desplegar una lista de cultivos recomendados, junto con las razones detrás de cada recomendación.


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

