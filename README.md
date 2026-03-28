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

## Flujo del proyecto

### Carga y exploración de datos
* Importación de datasets
* Análisis exploratorio (EDA)
* Identificación de valores nulos y atípicos

### Preprocesamiento
* Limpieza de datos
* Codificación de variables categóricas
* Escalado de variables (si aplica)
* Eliminación y/o combinación de duplicados

### Selección de variables
* Evaluación de variables relevantes
* Comparación entre features originales y derivadas
* Reducción de dimensionalidad

### Entrenamiento del modelo
* División train/test
* Entrenamiento de modelo de clasificación Logistic Regression
* Predicción de probabilidades:

```python
y_proba = model.predict_proba(X_test)[:,1]
```

### Evaluación inicial
* Accuracy
* Precision
* Recall
* F1-score

### Optimización del threshold
En lugar de usar el valor por defecto (0.5), se ajusta el umbral para mejorar el rendimiento:

```python
y_pred = (y_proba > 0.6).astype(int)
```

### Evaluación del impacto en:
  * Recall
  * Precision
  * F1-score

### Resultados
* Mejora del F1-score tras ajuste de threshold
* Mejor equilibrio entre falsos positivos y falsos negativos
* Identificación del umbral óptimo para el problema

## Cómo ejecutar
1. Clonar repositorio con -> git clone https://github.com/tu-usuario/ml-lab2-modelo.git
2. Abrir en Google Colab
3. Ejecutar todas las celdas

Autor: Raul Diaz
Licencia: Uso académico
