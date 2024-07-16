
## Proyecto Individual - Guillermo Gerbaldo



## TELECOMUNICACIONES

![image](https://github.com/user-attachments/assets/e6d45c51-1051-41ce-96ec-a9673e014142)




### Descripción de situación

Como Analista de Datos, se me ha encomendado realizar un análisis exhaustivo del sistema de telecomunicaciones en Argentina, con un enfoque en la provisión de acceso a Internet. 
Este trabajo incluye la definición de tres índices clave de rendimiento del negocio KPI (uno sugerido por el contratista), los cuales nos permitirán mostrar el progreso de la empresa o sus equipos de trabajo respecto de los objetivos empresariales más importantes, y acuar de manera flexible y rápida sobre las estrategias y procesos.

El desarrollo del trabajo consta de las siguientes etapas: 

Revisión de conjuntos de datos: Iniciaremos examinando diferentes conjuntos de datos relevantes.
Proceso ETL (Extracción, Transformación y Carga): Preparación y limpieza de los datos para el análisis exploratorio.
Análisis Exploratorio detallado (EDA): Realizaremos un análisis profundo para identificar patrones, tendencias y comportamientos en el sistema de telecomunicaciones.
Desarrollo de un dashboard interactivo: Creación de un dashboard interactivo para visualizar la información de manera efectiva.
Establecimiento de concludiones finales y sugerencias.

---------------------------------------------------------------------------------------------------

### Herramientas utlizadas

![image](https://github.com/user-attachments/assets/c8a0d16b-8282-4ce3-bf5d-752a90506db3)

![image](https://github.com/user-attachments/assets/bcc2a5b1-84f9-4f6e-8427-c5f4206d8b1e)


----------------------------------------------------------------------------------------------------


### Revisión de conjuntos de datos

![image](https://github.com/user-attachments/assets/50cb68f6-3c8a-4bb7-91c3-ca7e9e27fd7d)



Para comenzar con las tareas de análisis se nos brindan siete (7) dataset del Ente Nacional de Comunicaciones de Argentina (Enacom) en formato Excel:

1. Internet
2. Telefonía Móvil
3. Televisión
4. Telefonía Fija
5. Servicios Postales
6. Portabilidad
7. Mapa de conectividad

A continuación, se presenta una descripción detallada del contenido de los conjuntos de datos para definir los registros finales que se incluirán en el Análisis Exploratorio de Datos (EDA):

- **INTERNET DATASET:**
  Este conjunto de datos consta de quince (15) pestañas, organizadas en tres (3) niveles: por PROVINCIA, por TRIMESTRE y por LOCALIDAD. A continuación, se detallan los aspectos clave de la revisión realizada en cada nivel:
  
  - **Por PROVINCIA (df_provincia):** Se identificó información redundante relacionada con los datos de velocidad por provincia. Se optó por utilizar los registros con rangos de velocidad. Los siguientes atributos conforman este primer dataframe: Velocidad media de bajada.
      Banda ancha/Dial Up.
      Penetración por habitante.
      Penetración en hogares.
      Tipo de tecnología (ADSL, Fibra óptica, cablemódem, etc.).

  - **Por LOCALIDAD (df_localidad):** En este segundo dataframe, se seleccionaron los registros relacionados con el acceso a la tecnología por localidad y la velocidad sin rangos.
    
  - **Por TRIMESTRE (df_trimestre):** Para este tercer dataframe, se utilizaron los siguientes atributos:
      Velocidad media de bajada.
      Acceso por tecnología (ADSL, Fibra óptica, cablemódem, etc.).
      Banda ancha/Dial Up.
      Penetración total por habitantes/hogares.
      Velocidad por rangos.
      Ingresos por trimestre.
 

- **TELEFONÍA MÓVIL DATASET:**
  Este conjunto de datos contiene seis (6) pestañas co estructura nivel TRIMESTRE: SMS, Llamadas salientes, Minutos salientes, Ingresos, Penetración, Accesos.
  Para poder realizar algunas comparativas respecto des servicio de INTERNET, se utilizarán los campos SMS, Llamadas salientes e Ingresos, y se unirán al dataframe **df_trimestre**.

- **TELEVISIÓN DATASET:**
  Este conjunto de datos consta de cinco (5) pestañas, que incluyen información sobre el acceso a la televisión por provincia y en total, así como la penetración por provincia y en total. Sin embargo, nos centraremos exclusivamente en los datos de ingresos para realizar una comparativa de participación con respecto a otros servicios.

- **TELEFONÍA FIJA DATASET:**
   Similar al anterior, este conjunto de datos consta de cinco (5) pestañas, que incluyen información sobre el acceso a la telefonía fija por provincia y total (diferenciando las
  accesos entre HOGAR, COMERCIAL, GUBERNAMENTAL y o  tros.), así como la penetración por provincia y en total. Asimismo, nos centraremos exclusivamente en los datos de ingresos para realizar una comparativa de participación con respecto a otros servicios.

- **MAPA CONECTIVIDAD DATASET:**
   En este conjunto de datos se encuentramos información sobre el acceso a telefonia fija e Internet por tecnología (ADSL, Fibra óptica, cablemódem, etc.), además de su
  ubicación geométrica por localidad. Lo importaremos para realizar algún gráfico geaográfico (**df_partido**).

- En este estudio, no se considerarán los conjuntos de datos de **PORTABILIDAD** (relacionados con telefonía móvil y empresas prestadoras) ni los datos de **SERVICIOS POSTALES**. El enfoque de la investigación se centra en otros aspectos de la conectividad, como el acceso a Internet o la infraestructura tecnológica, por lo cual no es necesario incluir información sobre los mismos.”
  

### Proceso de ETL (Extracción, Transformación y Carga)

En esta etapa del desarrollo, nos focalizaremos en transformar los distintos conjuntos de datos, utilizando la herramienta **Visual Studio Code (VSC)**, para obtener las estructuras de datos finales (dataframes) que serán la fuente de datos desde donde obtendremos la información que nos permita entender y proyectar el funcionamiento y dinámica actual del sector de las telecomunicaciones en Argentina.

Iniciamos con el dataset de **internet**. Aplicando la librería del lenguaje Python, PANDAS, cargamos de manera separada cada una de las pestañas de los archivos Excel en VSC para su transformación.
Durante el proceso de normalización de los datos, se encuentran y corrigen algunos caracteres especiales y formatos de celdas, para finalmente obtener tres (3) dataframes, con distinta profundidad de información: **df_provincia**, **df_localidad**, **df_trimestre**, 

Luego se transformó el dataset de Mapa de Conectividades, en la estructura de datos **df_partido**, la cual se utilizó para realizar analisis visuales de mapas geolocalizados del territorio argentino.

De los dataset restantes sólo se extrajeron los registros de **ingreso** monetario para realizar un análisis económico comparativo entre los distintos servicios: Internet, Telefonía Móvil y servcios de TV. No fue considerado el dataset de telefonía fija para este proyecto. 

----------------------------------------------

### Análisis Exploratorio de datos (EDA)


Para iniciar el análisis exploratorio de datos, cargamos los datasets que se trabajaron en la etapa de ETL en la herramienta Visual Studio Code. Previamente, se importan las librerías de Python necesarias para la manipulación y visualización de los datos.
En primer lugar, realizamos una revisión de los tipos de datos y verificamos que concuerden con la información que se espera de cada dato. También comprobamos la existencia de valores anómalos o extremos (outliers), nulos o ceros. En este caso, observamos que el número de outliers es mínimo, por lo que consideramos que no afectarán significativamente las métricas del conjunto de datos. Por lo tanto, continuamos nuestro análisis utilizando los datos completos del dataset.

Realizamos un primer análisis de la evolución de accesos a internet de acuerdo a las distintas tecnologías. 

![image](https://github.com/user-attachments/assets/59c78118-6147-42d9-bf78-3926e9b6e77b)


Lo primero que observamos es el avance de las nuevas tecnologías, como el Cablemódem y la Fibra óptica. En consecuencia, se ha producido una caída en los accesos a tecnologías más antiguas, como el ADSL y la casi extinta Dial Up (conexión a través de la línea telefónica). Para el último trimestre de 2023, la Dial Up registra menos de 12 mil conexiones.

Al investigar las medidas tomadas en el país en referencia al mundo de las telecomunicaciones, encontramos que desde el año 2010 se viene elaborando un plan nacional de conexión a una red de fibra óptica para todo el territorio argentino, llamado Red Federal de Fibra Óptica (REFERO).

Durante la implementación de este plan, comenzaron a surgir las primeras conexiones a la red de fibra óptica entre los años 2013 y 2014. Luego, se produjo un importante avance entre los años 2018 y 2021, coincidiendo con el período de aislamiento social preventivo y obligatorio decretado por el gobierno nacional para proteger la salud pública durante la pandemia de Covid-19. Posteriormente, se observa un segundo incremento positivo en la tendencia de la curva a partir del año 2021, probablemente debido al despliegue continuo de la red en todo el territorio y a una mayor disponibilidad técnica para conectar hogares y ampliar las conexiones.

Además, el progreso tecnológico y la expansión de ambas tecnologías (cablemódem y fibra óptica) han contribuido al aumento de la velocidad promedio de descarga (medida en megabytes por segundo - Mbps), como se muestra en el siguiente gráfico:

![image](https://github.com/user-attachments/assets/a7aef370-b4e9-4ca0-98cb-18c9620293aa)


En el mismo se puede apreciar, el salto de la curva cuando se expanden en conjunto ambas tecnologias (cablemodem y fira óptica), pero a partir de 2022, la influencia de la fibra óptica en el crecimiento de la velocidad es significativo.

Posteriormente, analizamos la distribución de las distintas velocidades de conexión. En el gráfico correspondiente, se observa que para el año 2023, aunque se espera que las conexiones con velocidades superiores a 30 Mbps tengan una parte significativa del mercado, también es evidente que las velocidades más bajas aún ocupan una porción importante.

![image](https://github.com/user-attachments/assets/5251fb5f-1a61-4059-b5a9-3aaa0a2b19bc)


Esto nos permitiría considerar que, del mercado actual (recordemos que el mismo está en expansión) se podría trabajar en una mejora de calidad con los usuarios actualmente ya conectados, lo que generaría nuevos recursos economicos para la compañia. Pero, sigamos avanzando con nuestro análisis.

A continuación, vamos a enfocarnos en los ingresos por servicio, realizando una comparativa porcentual de la participación de los ingresos totales por servicio de internet, telefonia móvil y TV. 
En un primer análisis, evaluamos los ingresos con valores netos, pero los movimientos inflacionarios del país no proporcionaban una perspectiva comparativa adecuada. Por lo tanto, decidimos centrarnos en las medidas porcentuales. Es importante destacar que esperábamos resultados diferentes debido a la idea preconcebida de que las tecnologías emergentes, como los smart TVs conectados a Internet, reemplazarían el servicio de TV por cable tradicional. Además, la entrada de nuevos actores en el mercado, como Claro y Movistar, que ofrecían fibra óptica de alta velocidad pero no el servicio de TV por cable tradicional, también influyó en nuestras expectativas.


![image](https://github.com/user-attachments/assets/b2c713a5-e5fc-4cc2-a8b9-35958ecc60f5)


Sin embargo, al observar la gráfica, notamos que, aunque hay una disminución en las conexiones porcentuales del servicio de TV por cable, la tendencia no es lo suficientemente significativa como para centrarnos exclusivamente en este tema.


