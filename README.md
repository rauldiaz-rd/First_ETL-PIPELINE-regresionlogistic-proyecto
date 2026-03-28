# First_ETL-PIPELINE-regresionlogistic-proyecto
Este proyecto implementa un mini pipeline de ETL (Extract, Transform, Load) desarrollado en Google Colab, enfocado en el procesamiento, limpieza y análisis de datos.  El objetivo principal es acondicionar la base de datos e implementar un modelo de regresión logística, siguiendo buenas prácticas de ingeniería de datos.

## Objetivos
* Crear un pipeline para implementar ETL
* Construir un modelo de regresion logistica
* Evaluar el rendimiento con métricas robustas
* Mejorar el equilibrio entre precisión y recall

## Tecnologías utilizadas
* Python 
* Pandas
* NumPy
* Scikit-learn
* Matplotlib / Seaborn
* Google Colab

## Informe del proyecto
Las decisiones tomadas en base al analisis de datos fue eliminar duplicados porque eran registros repetidos, imputé nulos con mediana/moda y normalicé categorías (lowercase, trim) Convertí porcentajes y dinero a numérico corrigiendo simbolos y seleccionamos algunas features y se crearon usage_intensity, engagement_score, high_intent.
Preparación de datos (ETL)

### Carga y exploración de datos
* Importación de datasets
* Análisis exploratorio
* Identificación de valores nulos y atípicos

### Preprocesamiento
Se realizó la limpieza y transformación del dataset, incluyendo:
* Eliminación de valores nulos y duplicados
* Conversión de variables categóricas a formato numérico
* Creación de un conjunto de datos consistente para el modelado

### Selección de variables
Se excluyeron variables como identificadores únicos (user_id) y aquellas que generan fuga de información (selected_plan).

* Evaluación de variables relevantes
  Se seleccionaron variables relevantes para la predicción de conversión, priorizando:
  Variables de comportamiento del usuario (actividad, sesiones, uso de funcionalidades) 
  Variables de interacción (emails, visitas a planes, soporte)
 
* Features originales y derivadas
  Se generaron variables derivadas para mejorar la capacidad predictiva del modelo, tales como:
  Intensidad de uso Nivel de engagement 
  Indicadores de alta intención de compra
  Estas variables permiten capturar patrones no evidentes en los datos originales.

* Reducción de dimensionalidad

### Entrenamiento del modelo

El conjunto de datos se dividió en train/test/eval: 70/20/10
Entrenamiento (train)
Prueba (test)
Esto con el fin de evaluar la capacidad de generalización del modelo.

Modelado inicial
Se implementó un modelo de regresión logística utilizando la librería Scikit-learn, debido a:
Su interpretabilidad
Bajo costo computacional
Adecuación para problemas de clasificación binaria
Evaluación inicial

### Predicción de probabilidades:

```python
y_proba = model.predict_proba(X_test)[:,1]
```

### Evaluación inicial
El modelo fue evaluado mediante: Matriz de confusión Métricas como:
* Accuracy
* Precision
* Recall
* F1-score

<img width="539" height="455" alt="image" src="https://github.com/user-attachments/assets/f0f54233-b24d-42bd-8a96-c4eced8c5014" />

### Optimización del threshold
Se identificó: Alto recall (buena detección de positivos) Baja precisión (alto número de falsos positivos)
Ajuste inicial de threshold
En lugar de usar el valor por defecto (0.5), se ajusta el umbral para mejorar el rendimiento:

```python
y_pred = (y_proba > 0.6).astype(int)
```

### Evaluación del impacto:
Se modificó el umbral de clasificación (por defecto de 0.5 a 0.3 y 0.6) con el objetivo de incrementar la detección de usuarios que convierten, esto generó una mejora en recall y deterioro en precisión

### Resultados
El modelo inicial mostró capacidad para identificar patrones de conversión, pero presentó limitaciones en el equilibrio entre precisión y recall. Esto motivó la necesidad de optimizar el threshold y mejorar métricas como el F1-score en etapas posteriores.
* Mejora del F1-score tras ajuste de threshold
* Mejor equilibrio entre falsos positivos y falsos negativos
* Identificación del umbral óptimo para el problema

## Cómo ejecutar
1. Clonar repositorio con -> git clone https://github.com/tu-usuario/ml-lab2-modelo.git
2. Abrir en Google Colab
3. Ejecutar todas las celdas

Autor: Raul Diaz, 
Licencia: Uso académico
