# Predicción del Nivel de PIB utilizando Datos del Banco Mundial

## 1. Introducción y Propósito del Proyecto
El nivel de riqueza de un país, medido a través del Producto Interno Bruto (PIB), es un indicador fundamental para entender el bienestar económico. Sin embargo, el PIB no aumenta de forma aislada; es el resultado de la interacción de múltiples factores como el acceso a la educación, la salud de la población, el crecimiento demográfico y la estabilidad macroeconómica.

**El objetivo central de este proyecto** es desarrollar un modelo capaz de clasificar el nivel económico de distintos países basándose en indicadores sociales y demográficos. Este análisis permite identificar qué variables tienen mayor peso en la prosperidad de una nación y validar si estos factores son suficientes para predecir el estatus económico global.

---

## 2. Desarrollo de las Etapas

### Etapa 1: Análisis Descriptivo e Imputación de Datos
La primera fase se centra en garantizar que la información sea confiable y representativa. Trabajar con datos globales implica enfrentar problemas de información incompleta.

* **Revisión General:** Se identifica el número total de países, los años de estudio y las variables disponibles para asegurar una base de datos robusta.
* **Tratamiento de Datos Faltantes (NA):** * **Justificación del 15%:** Si a una variable le falta más del 15% de su información, se elimina. Esto se hace porque intentar completar tantos datos faltantes introduciría errores (sesgos) que afectarían la precisión del modelo.
    * **Imputación:** Si el faltante es menor al 15%, se utilizan métodos estadísticos para rellenar los huecos, evitando así perder filas completas de países que aportan valor al análisis.
* **Estadísticas y Outliers:** Se generan tablas descriptivas (media, mediana, desviación estándar) y se identifican valores atípicos. Esto es clave para distinguir entre países con comportamientos económicos únicos y posibles errores de registro.
* **Visualización del PIB:** Se analiza la distribución de nuestra variable objetivo mediante histogramas y mapas. Esto permite entender visualmente la brecha de ingresos entre las diferentes regiones del mundo.



### Etapa 2: Reducción de Dimensionalidad con PCA
En economía, muchas variables están relacionadas (por ejemplo, la esperanza de vida suele subir con el nivel educativo). Esto genera redundancia en los datos, lo que confunde a los modelos predictivos.

* **¿Por qué usar PCA?** El Análisis de Componentes Principales nos permite "resumir" muchas variables en un grupo pequeño de componentes principales. Estos nuevos componentes mantienen la información esencial pero eliminan la repetición.
* **Estandarización:** Como las variables usan escalas distintas (ej. población en millones vs. tasas de interés en porcentaje), es obligatorio normalizarlas para que todas tengan la misma importancia al inicio.
* **Varianza Explicada (70% - 90%):** Se busca reducir el número de variables pero conservando entre el 70% y el 90% de la información original. Esto simplifica el modelo y lo hace más eficiente sin sacrificar calidad.



### Etapa 3: Modelación con Algoritmos de Clasificación
Etapa Final: Implementación y Comparación de Modelos de Clasificación

En esta etapa final del proyecto se procede a la implementación de modelos de clasificación, con el propósito de evaluar el efecto de la reducción de dimensionalidad sobre el desempeño predictivo y la estructura del problema. Las fases de proyecto son las siguientes:

En primer lugar, se construyen dos modelos de clasificación utilizando el conjunto de datos original, es decir, considerando la totalidad de las variables explicativas sin aplicar técnicas de reducción de dimensionalidad. Esta aproximación permite establecer una línea base (baseline) para el análisis comparativo posterior.
Posteriormente, se desarrollan los mismos modelos de clasificación empleando como variables de entrada las componentes principales obtenidas en la etapa de reducción de dimensionalidad mediante PCA. De esta forma, se evalúa si la representación reducida de los datos logra preservar información relevante para la tarea de clasificación.
Ambos enfoques se implementan bajo condiciones metodológicas comparables, manteniendo criterios consistentes de partición de datos y métricas de evaluación. El desempeño de los modelos se analiza mediante indicadores adecuados al problema de clasificación, permitiendo contrastar los resultados obtenidos con datos originales y con datos reducidos.

Finalmente, se realiza un análisis comparativo de los resultados, discutiendo las ventajas y limitaciones de cada enfoque, así como el impacto del uso de PCA en términos de desempeño, interpretabilidad y complejidad del modelo. Esta etapa cierra el proyecto integrando los aprendizajes obtenidos a lo largo de las fases previas y fundamentando las decisiones analíticas adoptadas.


## 3. Origen de los Datos y Entorno de Trabajo

Para la realización de este proyecto, se han definido los siguientes parámetros técnicos:

* **Base de Datos:** Se utiliza la **API oficial del Banco Mundial**, la cual permite extraer indicadores actualizados directamente de sus servidores. Esta herramienta facilita el acceso a series temporales de diversos países de manera dinámica y organizada.
* **Versión de la API:** Se emplea específicamente el paquete `wbgapi` en su **versión 1.0.2**, la cual incluye mejoras para la integración de datos con estructuras de análisis modernas.
* **Entorno de Trabajo:** Todo el desarrollo, desde la extracción hasta el modelado, se realiza bajo el lenguaje de programación **Python**, utilizando sus herramientas estándar para el tratamiento de datos científicos.
