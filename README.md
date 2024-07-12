![image](https://github.com/user-attachments/assets/7d01830e-6d33-4dce-aa10-dd0168391332)


## Proyecto Individual nro 2 - Guillermo Gerbaldo



## TELECOMUNICACIONES

![image](https://github.com/user-attachments/assets/e6d45c51-1051-41ce-96ec-a9673e014142)


### Descripción de situación

Como Analista de Datos, se nos ha encomendado realizar un análisis exhaustivo del sistema de telecomunicaciones en Argentina, con un enfoque en la provisión de acceso a Internet. Nuestra tarea incluye los siguientes pasos:

Revisión de conjuntos de datos: Iniciaremos examinando diferentes conjuntos de datos relevantes.
Proceso ETL (Extracción, Transformación y Carga): Utilizaremos Visual Studio Code para extraer, transformar y cargar los datos, preparándolos para el análisis.
Análisis Exploratorio detallado (EDA): Realizaremos un análisis profundo para identificar patrones, tendencias y comportamientos en el sistema de telecomunicaciones.
Desarrollo de un dashboard interactivo: Finalmente, crearemos un dashboard interactivo utilizando Power BI para visualizar la información de manera efectiva.

### Revisión de conjuntos de datos
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

En esta etapa del desarrollo, nos focalizaremos en transformar los distintos conjuntos de datos, utilizando la herramienta Visual Studio Code (VSC), para obtener los dataframes finales que serán la fuente de datos desde donde obtendremos la información que nos permita entender y proyectar el funcionamiento y dinámica actual del sector de las telecomunicaciones en Argentina.

Aplicando la librería del lenguaje Python, PANDAS, cargamos de manera separada cada una de las pestañas de los archivos Excel en VSC para su transformación.
Durante el proceso de normalización de los datos, se encuentran y corrigen algunos caracteres especiales y formatos de celdas, para finalmente obtener cuatro (4) dataframes: **df_provincia**, **df_localidad**, **df_trimestre**, **df_partido** (








