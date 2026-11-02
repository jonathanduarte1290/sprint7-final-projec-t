# sprint7-final-projec-t

Análisis Exploratorio de Datos y Segmentación de Usuarios - ConnectaTel

📄 Descripción del Proyecto

Este proyecto lleva a cabo un proceso integral de limpieza de datos, análisis exploratorio (EDA) y segmentación de clientes para la empresa de telecomunicaciones ConnectaTel.

El objetivo principal es transformar datos heterogéneos de consumo y perfiles demográficos en información estructurada que permita identificar patrones de uso, detectar clientes de alto valor (heavy users) y proponer recomendaciones comerciales estratégicas para la optimización de planes de servicio.

📊 Datasets Utilizados

El análisis se basa en tres conjuntos de datos principales:

users_latam.csv (users): Información demográfica y contractual de los clientes.

user_id: Identificador único del usuario.

age: Edad del usuario (contuvo valores sentinela como -999).

city: Ciudad de residencia (contuvo inconsistencias como ?).

plan: Plan contratado (surf, ultimate).

reg_date: Fecha de registro en el servicio.

usage.csv (usage): Registro detallado de eventos de consumo.

id: Identificador único del evento.

user_id: Identificador del usuario que realiza la transacción.

type: Tipo de servicio consumido (call, text, etc.).

duration: Duración de las llamadas en minutos.

length: Longitud/caracteres de los mensajes de texto.

date: Fecha en que ocurrió la transacción.

plans.csv (plans): Tabla de referencia con las especificaciones y tarifas de los planes ofrecidos.

🛠️ Etapas del Análisis

El proyecto sigue una metodología estructurada en las siguientes etapas:

Exploración Inicial y Diagnóstico de Sentinels:

Identificación y corrección de valores sentinela numéricos (-999 en age) y categóricos (? en city).

Diagnóstico de inconsistencias de formato e integridad en las identificaciones.

Saneamiento Temporal (Fechas Out-of-Range):

Conversión estricta a tipos de fecha (pd.to_datetime).

Corrección de fechas fuera de rango (>2024 o <2000) asignando NaT e imputando la fecha de registro a partir del primer consumo detectado.

Evaluación de Datos Faltantes (MAR):

Confirmación de patrones Missing At Random (MAR) en duration y length condicionados por el tipo de evento (type).

Conservación de los NaN para evitar distorsiones en las distribuciones reales de consumo.

Ingeniería de Características y Agregación:

Construcción de métricas agregadas por usuario: cant_mensajes, cant_llamadas y cant_minutos_llamada.

Creación de la tabla integrada user_profile.

Análisis Exploratorio de Datos (EDA) y Trata de Outliers:

Análisis visual de distribuciones e histográmas segmentados por tipo de plan (hue='plan').

Diagnóstico mediante Diagramas de Caja (Boxplots) y cálculo de rangos intercuartílicos (IQR).

Preservación deliberada de los outliers superiores al representar comportamiento real de usuarios intensivos (heavy users).

Segmentación de Usuarios:

Creación del segmento grupo_uso (Bajo uso, Uso medio, Alto uso).

Creación del segmento grupo_edad (Joven, Adulto, Adulto Mayor).

Evaluación cualitativa y cuantitativa de los segmentos por volumen de usuarios.

Conclusiones Ejecutivas y Recomendaciones:

Identificación de segmentos de alto valor y formulación de estrategias comerciales (migración de planes, upselling y diseño de nuevas ofertas).

🚀 Cómo Ejecutar el Notebook

Opción 1: Ejecución en Google Colab (Recomendado)

Sube el cuaderno interactivo (.ipynb) a tu cuenta de Google Drive o ábrelo directamente desde GitHub.

Abre el archivo en Google Colab.

Asegúrate de cargar los archivos .csv (users_latam.csv, usage.csv, plans.csv) en el entorno local de Colab o vincular la ruta correspondiente de tu Google Drive.

Ejecuta las celdas en orden secuencial (Entorno de ejecución > Ejecutar todas).

Opción 2: Ejecución Local en Jupyter Notebook / VS Code

Clona este repositorio en tu máquina local:

git clone https://github.com/tu-usuario/connectatel-eda-segmentation.git
cd connectatel-eda-segmentation


Instala las dependencias requeridas (se recomienda usar un entorno virtual):

pip install pandas numpy matplotlib seaborn


Inicia Jupyter Notebook o VS Code:

jupyter notebook


Abre el archivo del proyecto y ejecuta el análisis celda por celda.

🔄 Guía de Reproducción

Para replicar de forma exacta los resultados obtenidos en este estudio:

Estructura de Directorios: Asegúrate de colocar las fuentes de datos en la ruta esperada dentro del entorno de ejecución:

├── datasets/
│   ├── users_latam.csv
│   ├── usage.csv
│   └── plans.csv
├── notebook_proyecto.ipynb
└── README.md


Secuencia de Ejecución: Respeta el orden lineal del notebook. Las funciones de imputación y las variables calculadas en las celdas de saneamiento son requeridas en la fase de agregación (user_profile).

Versiones Recomendadas:

python >= 3.8

pandas >= 1.5.0

seaborn >= 0.12.0

matplotlib >= 3.5.0

✉️ Contacto y Contribuciones

Proyecto realizado como parte del programa de análisis de datos para telecomunicaciones. Si tienes dudas o sugerencias para mejorar el modelo de segmentación, siéntete libre de abrir un Issue o enviar un Pull Request.
