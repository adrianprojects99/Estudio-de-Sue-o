# Estudio-de-Sueño

# Análisis de Datos de Patrones de Sueño y Estilo de Vida

##  Resumen del Proyecto

Este repositorio contiene la **Tarea 2** del curso de Inteligencia Artificial, que consiste en un análisis de datos exhaustivo (Exploratory Data Analysis - EDA) sobre un *dataset* de estilo de vida y patrones de sueño.

El objetivo principal de este análisis fue comprender los patrones subyacentes en la muestra, limpiar y transformar los datos, y, crucialmente, preparar un conjunto de datos final con una **variable objetivo binaria de estrés** para el futuro entrenamiento de un modelo de clasificación.

###  Dataset

* **Nombre:** Lifestyle and Sleep Patterns
* **Fuente:** [Kaggle](https://www.kaggle.com/datasets/minahilfatima12328/lifestyle-and-sleep-patterns)
* **Descripción:** Contiene información sobre hábitos de sueño, niveles de estrés, ejercicio, ocupación y otros indicadores de salud de un conjunto de individuos.

---

##  Metodología del Análisis de Datos

El análisis se estructuró en varias etapas de procesamiento y exploración, guiadas por la necesidad de asegurar la calidad del dato y la preparación para el modelado.

### 1. Exploración de Datos (EDA Inicial)

* **Análisis del Conjunto de Datos y Descripción:** Se revisó la estructura, tipos de datos y se obtuvo un resumen estadístico inicial del dataset.
* **Tratamiento de Valores Vacíos:** Se identificaron y gestionaron los valores nulos (NaN) para mantener la integridad del dataset. *(Se debe justificar si se imputaron, eliminaron o se mantuvieron, explicando el por qué de la decisión, por ejemplo: "Se eliminaron las filas con nulos debido a que representaban menos del 1% del total y su eliminación no sesgaba la muestra").*
* **Transformaciones Iniciales:** Se realizaron ajustes en tipos de datos o formatos de variables según fuera necesario.

### 2. Análisis Univariante

Se examinó la distribución de cada variable de forma aislada (categórica y numérica) para obtener una visión profunda de la muestra.

* **Deducciones Clave:** Se observó que:
    * *(Ejemplo de deducción para Estrés):* "El nivel de estrés mostró una alta concentración de valores entre 6 y 8, indicando que la mayoría de los pacientes de la muestra viven bajo niveles significativos de estrés."
    * *(Ejemplo de deducción para Sueño):* "Las horas de sueño por noche se concentran en un rango estrecho, siendo la media de [X] horas, con muy pocas desviaciones extremas."

### 3. Filtrado de Variables (Tratamiento de Outliers)

* **Método Aplicado:** Se implementó el filtrado de variables mediante **[Método utilizado, ej. Rango Intercuartílico (IQR) o límites de desviaciones estándar]** para identificar y eliminar *outliers* extremos.
* **Justificación:** *"(Ejemplo de justificación):* Este corte se realizó para mejorar la robustez del modelo de clasificación, asegurando que las anomalías extremas no distorsionen la media ni la varianza de los datos de entrenamiento."

### 4. Creación y Adaptación de la Variable Objetivo

Se creó una variable objetivo binaria a partir de la variable numérica `Nivel de Estrés` para la tarea de clasificación:

* **Variable Objetivo (`Nivel_Estres_Binario`):**
    * `ESTRES MODERADO`: Nivel de Estrés entre 3 y 6.
    * `ESTRESADO`: Nivel de Estrés de 7 en adelante.
* **Eliminación:** La variable numérica original `Nivel de Estrés` fue eliminada del dataset final.

### 5. Análisis Bivariante

Se graficó la **Variable Objetivo Binaria** contra todas las variables de insumo para determinar su relación.

* **Relaciones Clave:**
    * *(Ejemplo: Objetivo vs. Horas de Sueño):* "Existe una correlación visiblemente negativa: a menor cantidad de horas de sueño, la proporción de individuos en la categoría 'ESTRESADO' es significativamente mayor."
    * *(Ejemplo: Objetivo vs. Calidad del Sueño):* "La calidad del sueño muestra una fuerte relación inversa, donde las categorías de 'ESTRESADO' se concentran en calidades de sueño bajas (4-5)."

### 6. Matriz de Correlación

* **Análisis:** Se generó una matriz de correlación para evaluar las relaciones lineales entre las variables numéricas.
* **Redundancia:** Se identificaron y explicaron las **altas correlaciones positivas o negativas**. Se eligió una variable para eliminar (la que tuviera menos sentido según el contexto del negocio, por ejemplo, si `Horas de Ejercicio` y `Horas de Sueño` estuvieran muy correlacionadas).
* **Justificación de Eliminación:** *"(Ejemplo de justificación):* Se eliminó la variable [Variable Eliminada] porque estaba fuertemente correlacionada con [Otra Variable] y consideramos que esta última es la más relevante para el estudio de patrones de sueño."

### 7. División y Guardado del Dataset

* **Regla:** Se dividió el dataset en conjuntos de entrenamiento (`train.csv`) y prueba (`test.csv`) siguiendo la regla **80/20**.
* **Estratificación:** Se aplicó la **estratificación** a la variable objetivo (`Nivel_Estres_Binario`) para asegurar que la proporción de las clases de estrés fuera idéntica en ambos conjuntos, garantizando así un entrenamiento imparcial del modelo.
* **Archivos Generados:** El dataset final preprocesado y dividido se guardó en:
    * `data/train.csv`
    * `data/test.csv`

---

##  Cómo Ejecutar el Análisis

1.  Clonar el repositorio.
2.  Instalar las dependencias de Python (pandas, numpy, matplotlib, seaborn, scikit-learn).
3.  Abrir el *notebook* de análisis de datos (`EDA_Sleep_Patterns.ipynb` o similar).
4.  Ejecutar todas las celdas para replicar el preprocesamiento y la generación de los archivos `train.csv` y `test.csv`.
