# Análisis de Evasión de Clientes - Telecom X

## Descripción del Proyecto

Este proyecto tiene como objetivo analizar los datos de clientes de Telecom X para comprender los factores que contribuyen a la evasión de clientes (churn). A través de la limpieza, transformación y análisis exploratorio de los datos, buscamos identificar patrones y obtener información valiosa que pueda ayudar a la empresa a desarrollar estrategias efectivas para reducir la pérdida de clientes.

## Estructura del Proyecto

El proyecto está organizado de la siguiente manera:

*   `TelecomX_Data.json`: Archivo de datos original en formato JSON.
*   `datos_limpios.csv`: Archivo CSV resultante después del proceso de limpieza y transformación de datos.
*   `notebook.ipynb`: Cuaderno de Jupyter (o Google Colab) que contiene el código para la extracción, limpieza, transformación y análisis exploratorio de los datos, así como la generación del informe final.
*   `README.md`: Este archivo, que proporciona una descripción general del proyecto.

## Requisitos y Dependencias

Para ejecutar este proyecto localmente, necesitarás tener instalado Python y las siguientes bibliotecas:

*   `pandas`: Para la manipulación y análisis de datos.
*   `requests`: Para la extracción de datos desde la URL (si no se descarga directamente).
*   `plotly`: Para la creación de visualizaciones interactivas.
*   `matplotlib`: Para la creación de visualizaciones estáticas (utilizado en el mapa de calor).
*   `seaborn`: Para la creación de visualizaciones estadísticas (utilizado en el mapa de calor).

## Acceso al Cuaderno de colab 

Puedes descaegae el notebook del proyecto desde github, y tambien visualizarlo en el siguente enlace en google colab https://colab.research.google.com/github/veterydaisy/TelecomX_LATAM_daisy/blob/main/TelecomX_LATAM.ipynb

## 📄 Informe Final del Análisis de Evasión de Clientes - Telecom X

## 1. Introducción

Telecom X, una empresa líder en el sector de las telecomunicaciones, se enfrenta a un desafío significativo: una alta tasa de evasión de clientes (churn). La pérdida de clientes no solo impacta los ingresos, sino que también afecta la estabilidad y el crecimiento a largo plazo de la empresa. Para abordar este problema, se ha llevado a cabo un análisis exhaustivo de los datos de los clientes con el objetivo de comprender los factores subyacentes que impulsan la evasión. Este informe detalla el proceso de análisis, los hallazgos clave y las recomendaciones estratégicas para ayudar a Telecom X a retener a sus clientes valiosos y reducir la tasa de abandono.

## 2. Limpieza y Tratamiento de Datos

La fase inicial del análisis implicó la importación y preparación del conjunto de datos. Los datos fueron obtenidos de una fuente JSON y cargados en un DataFrame de pandas para su manipulación.

Los pasos clave realizados durante la limpieza y el tratamiento de los datos incluyeron:

*   **Normalización del JSON:** Se utilizó `pd.json_normalize()` para aplanar la estructura anidada del JSON y convertirla en un DataFrame tabular.
*   **Exploración Inicial:** Se verificaron los tipos de datos (`df_normalizado.info()`) y se identificaron valores únicos en cada columna para comprender la naturaleza de las variables.
*   **Manejo de Valores Vacíos y Nulos:** Se identificaron y trataron los valores en blanco o vacíos, particularmente en las columnas 'Churn' y 'account.Charges.Total'. Las filas con valores vacíos en 'Churn' fueron eliminadas debido a su bajo porcentaje en comparación con el tamaño total del dataset. Los valores en blanco en 'account.Charges.Total' se convirtieron a nulos durante la transformación a tipo numérico y se manejaron posteriormente.
*   **Transformación de Tipos de Datos:** La columna 'account.Charges.Total' fue convertida a un tipo numérico (float) utilizando `pd.to_numeric` con `errors='coerce'` para manejar posibles valores no numéricos.
*   **Creación de Nuevas Variables:** Se creó la columna 'Cuentas_Diarias' calculando el cargo diario a partir del cargo mensual.
*   **Normalización de Nombres y Valores:** Se renombraron las columnas a español y se convirtieron a minúsculas para mayor claridad. Se tradujeron los valores categóricos relevantes al español (por ejemplo, 'Male' a 'Hombre', 'Yes' a 'Si').
*   **Reseteo del Índice:** Se reseteó el índice del DataFrame después de eliminar filas para asegurar una indexación continua.

Estos pasos de limpieza y preprocesamiento aseguraron que los datos estuvieran en un formato adecuado para el análisis exploratorio.

## 3. Análisis Exploratorio de Datos

En esta sección, presentamos los análisis exploratorios realizados para identificar patrones y relaciones entre las variables del conjunto de datos y el estado de evasión de los clientes. Se utilizaron diversas visualizaciones para ilustrar los hallazgos.

### 3.1 Distribución General de Clientes por Estado de Evasión

Comenzamos examinando la proporción general de clientes que han evadido la empresa.

<img width="1248" height="495" alt="image" src="https://github.com/user-attachments/assets/f67d4d72-faa1-4814-93f1-73a28e3da614" />

### 3.2 Análisis de Evasión por Género

Analizamos la distribución de la evasión entre clientes masculinos y femeninos para determinar si existe alguna diferencia significativa basada en el género.

<img width="1276" height="470" alt="image" src="https://github.com/user-attachments/assets/ccc09874-7901-47da-a5c0-5601b1e34225" />

### 3.3 Análisis de Evasión por Edad (Adulto Mayor)

Aquí comparamos la tasa de evasión entre los clientes que son adultos mayores de 65 años y aquellos que no lo son.

<img width="1271" height="502" alt="image" src="https://github.com/user-attachments/assets/f9d4553e-161b-4c59-b4d5-ed873c9adceb" />

### 3.4 Análisis de Evasión por Relación (Pareja y Dependientes)

Exploramos si tener pareja o dependientes influye en la tasa de evasión de los clientes.

<img width="1242" height="478" alt="image" src="https://github.com/user-attachments/assets/00196674-a29c-4d88-a0e4-54040cc410a8" />

<img width="1238" height="492" alt="image" src="https://github.com/user-attachments/assets/85a5181e-a350-45af-b419-9617d3d39e0e" />

### 3.5 Análisis de Evasión por Antigüedad (Meses de Contrato)

Aquí exploramos cómo la duración del contrato de un cliente se relaciona con la probabilidad de que abandone la empresa.

<img width="1263" height="465" alt="image" src="https://github.com/user-attachments/assets/73523bf1-1e80-4a7a-9800-be21b397b09e" />

<img width="1242" height="483" alt="image" src="https://github.com/user-attachments/assets/c99c5067-4705-4390-b517-fb170a1291b0" />

<img width="1257" height="481" alt="image" src="https://github.com/user-attachments/assets/6c812ea8-25b1-4e8f-a24d-f738776ff941" />

### 3.6 Análisis de Evasión por Servicios Contratados

Exploramos la tasa de evasión para los diferentes servicios a los que están suscritos los clientes.

<img width="1260" height="491" alt="image" src="https://github.com/user-attachments/assets/1e8587cf-521b-4a9b-9e1c-bbcaa44e6c21" />

<img width="1248" height="477" alt="image" src="https://github.com/user-attachments/assets/199e9af8-dd89-40e5-9a25-0ded4339dc1e" />

<img width="1256" height="465" alt="image" src="https://github.com/user-attachments/assets/2e0fbcf2-ed95-41d3-a961-1c2a9d13c6cb" />

<img width="1251" height="484" alt="image" src="https://github.com/user-attachments/assets/f79f48c2-4b5f-4c7c-8797-fc307cf25209" />

<img width="1249" height="452" alt="image" src="https://github.com/user-attachments/assets/d5f2ccbd-04e9-443f-8539-6a8380d92667" />

<img width="1241" height="493" alt="image" src="https://github.com/user-attachments/assets/7cebca98-8904-4c4d-a6a6-47e0229dd273" />

<img width="1242" height="486" alt="image" src="https://github.com/user-attachments/assets/96f59d8c-8bdb-429e-95e9-cfaa4bc0ea73" />

<img width="1241" height="496" alt="image" src="https://github.com/user-attachments/assets/5534a9b9-7e76-4f4e-9374-cd9f3dcc22f5" />

<img width="1254" height="478" alt="image" src="https://github.com/user-attachments/assets/57dd549d-d131-4415-b07c-ec81028c1efe" />

<img width="1251" height="489" alt="image" src="https://github.com/user-attachments/assets/51790196-079d-4c54-a9ba-b2848a392026" />

### 3.7 Análisis de evasión por tipo de contrato:

La tasa de evasión entre los diferentes tipos de contrato.

<img width="1262" height="486" alt="image" src="https://github.com/user-attachments/assets/dfcb086e-c418-414e-9826-e0aa743126e2" />

### 3.8 Análisis de evasión por cargos:

Visualizar la relación entre los cargos mensuales y totales y la evasión.

<img width="1251" height="490" alt="image" src="https://github.com/user-attachments/assets/da37e95a-470e-4025-8a11-d738143f0de8" />

<img width="1244" height="471" alt="image" src="https://github.com/user-attachments/assets/971a9164-5dea-440a-a342-acba285be2d2" />

<img width="1241" height="498" alt="image" src="https://github.com/user-attachments/assets/2fa39f43-b3e8-41f1-a75f-2899834380cf" />

<img width="1269" height="512" alt="image" src="https://github.com/user-attachments/assets/238a600d-f7ff-494a-90fa-e872107b19a7" />

<img width="1233" height="497" alt="image" src="https://github.com/user-attachments/assets/aac7c78c-3458-497b-9ac9-e97e6ccef2a2" />

<img width="1251" height="502" alt="image" src="https://github.com/user-attachments/assets/956d7910-4569-4d52-b242-887e85c3c39f" />

### 3.9 Análisis de Evasión por Factura Online y Método de Pago

Finalmente, examinamos si el método de recepción de factura (online o no) y el método de pago están relacionados con la evasión.

<img width="1262" height="469" alt="image" src="https://github.com/user-attachments/assets/f4b95317-4a0d-452e-9534-7dedb4be2bd7" />

<img width="1238" height="494" alt="image" src="https://github.com/user-attachments/assets/a48791d2-0728-437d-8d52-368f737db2b7" />

## 4. Conclusiones e Insights

Basado en el análisis exploratorio de datos, se identificaron varios factores clave asociados con la evasión de clientes en Telecom X:

*   **Antigüedad del Cliente:** Los clientes nuevos (con pocos meses de contrato) tienen una probabilidad significativamente mayor de evadir. La tasa de evasión disminuye drásticamente a medida que aumenta la antigüedad.
*   **Servicio de Internet (Fibra Óptica):** Los clientes suscritos al servicio de Fibra Óptica presentan una tasa de evasión considerablemente más alta en comparación con aquellos con servicio DSL o sin servicio de internet. Esto podría estar relacionado con el costo, la calidad del servicio o las expectativas del cliente.
*   **Servicios Adicionales:** Los clientes que no tienen servicios adicionales (seguridad en línea, respaldo, protección de dispositivos, soporte técnico, streaming de TV y películas) tienden a evadir más. Esto sugiere que la adopción de servicios adicionales puede estar relacionada con una mayor lealtad o satisfacción.
*   **Tipo de Contrato:** Los contratos mes a mes están fuertemente asociados con una mayor tasa de evasión, lo que indica que los clientes con menor compromiso a largo plazo son más propensos a irse.
*   **Cargos (Mensuales y Totales):** Existe una tendencia a que los clientes con cargos mensuales y totales más altos tengan una mayor probabilidad de evasión. Esto podría estar vinculado al costo percibido del servicio, especialmente para los servicios de mayor precio como la Fibra Óptica.
*   **Método de Pago (Cheque Electrónico):** El uso del cheque electrónico como método de pago se asocia con una tasa de evasión más alta.
*   **Adulto Mayor:** Los clientes que son adultos mayores de 65 años también muestran una mayor tasa de evasión.

Estos insights sugieren que la evasión en Telecom X es un fenómeno complejo influenciado por una combinación de factores demográficos, de servicios y de facturación. La mayor vulnerabilidad se observa en clientes nuevos, aquellos con servicios de alta velocidad como Fibra Óptica, y aquellos con contratos flexibles o que utilizan métodos de pago específicos.

Comprender estos patrones es fundamental para desarrollar estrategias de retención dirigidas y efectivas que aborden las causas raíz de la evasión.

## 5. Recomendaciones

Con base en los hallazgos del análisis exploratorio, se proponen las siguientes recomendaciones estratégicas para ayudar a Telecom X a reducir la evasión de clientes:

*   **Programas de Incorporación y Retención Temprana:** Implementar programas de bienvenida proactivos y estrategias de retención dirigidas a los clientes en sus primeros meses de contrato. Esto podría incluir comunicación frecuente, soporte técnico prioritario y ofertas especiales después del primer mes.
*   **Optimización de la Oferta de Fibra Óptica:** Realizar una investigación más profunda sobre la experiencia del cliente con la Fibra Óptica. Evaluar la relación precio-valor, la estabilidad del servicio y la comunicación de beneficios para reducir la tasa de evasión en este segmento. Considerar programas de fidelización específicos para usuarios de Fibra Óptica.
*   **Incentivar la Adopción de Contratos a Largo Plazo:** Ofrecer descuentos significativos o beneficios adicionales a los clientes que opten por contratos de uno o dos años en lugar de contratos mes a mes. Comunicar claramente los beneficios de la estabilidad del servicio y los ahorros a largo plazo.
*   **Promoción de Servicios Adicionales:** Destacar el valor y los beneficios de los servicios adicionales (seguridad, respaldo, soporte técnico, streaming) para fomentar su adopción. Los clientes con más servicios tienden a tener una menor tasa de evasión, lo que sugiere que una oferta de servicios más completa puede aumentar la lealtad.
*   **Revisión del Proceso de Pago con Cheque Electrónico:** Investigar posibles puntos de fricción o insatisfacción asociados con el método de pago de cheque electrónico. Simplificar el proceso o promover métodos de pago alternativos más estables podría ayudar a reducir la evasión en este grupo.
*   **Estrategias de Retención para Adultos Mayores:** Desarrollar programas o servicios adaptados a las necesidades de los clientes adultos mayores, considerando posibles barreras tecnológicas o preferencias de comunicación.
*   **Análisis de Precios Competitivos:** Evaluar si los cargos mensuales y totales son competitivos en el mercado, especialmente para los servicios de alta velocidad. Un análisis de precios podría ayudar a identificar si el costo es un factor determinante en la decisión de evadir.

Estas recomendaciones buscan abordar los factores identificados como influyentes en la evasión de clientes y proporcionar un punto de partida para la implementación de estrategias de retención más efectivas en Telecom X.








