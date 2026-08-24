# proyecto-rendimiento-estudiantes
Análisis y modelización del rendimiento académico de estudiantes
# Predicción del rendimiento académico de estudiantes

## Descripción del proyecto

Este proyecto analiza un conjunto de datos relacionado con el rendimiento académico de 1.000 estudiantes.

El objetivo es aplicar las diferentes fases de un proyecto de aprendizaje automático: análisis exploratorio, preprocesamiento, entrenamiento y validación de un modelo de regresión y entrenamiento y validación de un modelo de clasificación.

## Objetivos

El proyecto tiene dos variables objetivo:

- `nota_final`: variable continua entre 0 y 100 utilizada para regresión.
- `aprobado`: variable binaria utilizada para clasificación, donde 1 representa aprobado y 0 representa suspenso.

El modelo de regresión intenta predecir la nota final del estudiante.

El modelo de clasificación intenta predecir si el estudiante aprobará o suspenderá.

## Variables del conjunto de datos

- `horas_estudio_semanal`: horas de estudio semanales.
- `nota_anterior`: nota obtenida anteriormente.
- `tasa_asistencia`: porcentaje de asistencia a clase.
- `horas_sueno`: promedio diario de horas de sueño.
- `edad`: edad del estudiante.
- `nivel_dificultad`: dificultad percibida para el estudio.
- `tiene_tutor`: indica si el estudiante tiene tutor.
- `horario_estudio_preferido`: horario preferido para estudiar.
- `estilo_aprendizaje`: estilo de aprendizaje utilizado.
- `nota_final`: nota final del estudiante.
- `aprobado`: resultado académico binario.

## Fases del proyecto

### 1. Análisis exploratorio

Durante el análisis exploratorio se realizaron las siguientes tareas:

- Revisión de las dimensiones y estructura del dataset.
- Identificación de los tipos de datos.
- Comprobación de filas duplicadas.
- Identificación de valores ausentes.
- Estadísticas descriptivas.
- Análisis de variables numéricas y categóricas.
- Visualización de distribuciones.
- Detección de posibles valores atípicos.
- Matriz de correlación.
- Análisis de las relaciones con `nota_final` y `aprobado`.

El análisis mostró que las horas de estudio semanales, la nota anterior y la tasa de asistencia presentan una relación positiva con la nota final.

También se observó un desbalance en la variable `aprobado`, ya que la mayoría de los estudiantes pertenece a la clase de aprobados.

### 2. Preprocesamiento

Se realizaron las siguientes transformaciones:

- Eliminación de posibles duplicados.
- Imputación de los valores ausentes numéricos mediante la mediana.
- Tratamiento de los valores ausentes categóricos.
- Separación de variables predictoras y variables objetivo.
- Estandarización de variables numéricas.
- Codificación One-Hot de variables categóricas.
- Creación de pipelines para evitar fugas de información.

Para regresión se eliminó la variable `aprobado`, ya que deriva de la nota final.

Para clasificación se eliminó `nota_final`, porque determina directamente si el estudiante está aprobado.

## Modelo de regresión

Se utilizó un modelo de regresión lineal para predecir `nota_final`.

El conjunto de datos se dividió en un 80 % para entrenamiento y un 20 % para prueba.

Las métricas utilizadas fueron R², error absoluto medio (MAE) y raíz del error cuadrático medio (RMSE).

También se aplicó validación cruzada de cinco particiones y se analizaron gráficamente las predicciones y los residuos.

## Modelo de clasificación

Se utilizó un modelo de regresión logística para predecir `aprobado`.

La división entre entrenamiento y prueba se realizó de forma estratificada para mantener la proporción de estudiantes aprobados y suspendidos.

Debido al desbalance de las clases, se utilizó el parámetro `class_weight="balanced"`.

Las métricas utilizadas fueron:

- Accuracy.
- Precision.
- Recall.
- F1-score.
- ROC-AUC.
- Matriz de confusión.
- Curva ROC.

También se realizó una validación cruzada estratificada de cinco particiones.

## Estructura del repositorio

- `dataset_estudiantes.csv`: conjunto de datos original.
- `df_regresion_estudiantes.csv`: datos preparados para regresión.
- `df_clasificacion_estudiantes.csv`: datos preparados para clasificación.
- `01-EDA-Estudiantes.ipynb`: análisis exploratorio.
- `02-Preprocesamiento-Estudiantes.ipynb`: preprocesamiento.
- `03-Regresion-Estudiantes.ipynb`: modelo de regresión.
- `04-Clasificacion-Estudiantes.ipynb`: modelo de clasificación.
- `modelo_regresion_estudiantes.pkl`: modelo de regresión entrenado.
- `modelo_clasificacion_estudiantes.pkl`: modelo de clasificación entrenado.
- `README.md`: documentación del proyecto.

## Tecnologías utilizadas

- Python.
- Pandas.
- NumPy.
- Matplotlib.
- Seaborn.
- Scikit-learn.
- Google Colab.
- Joblib.

## Conclusiones

El proyecto ha permitido aplicar un flujo completo de aprendizaje automático sobre datos académicos.

El modelo de regresión permite estimar la nota final de los estudiantes, mientras que el modelo de clasificación permite identificar si un estudiante tiene probabilidades de aprobar o suspender.

Las horas de estudio, la nota anterior, la asistencia y la disponibilidad de tutor aparecen como factores relacionados con el rendimiento académico.

El uso de pipelines permite integrar el preprocesamiento y el modelado en un único proceso, reduciendo el riesgo de fuga de información y facilitando la utilización posterior de los modelos.
