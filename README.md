# Predicción de la carga de calefacción de edificios

Proyecto final de la Fase 4 de programación e inteligencia artificial,
centrado en Machine Learning clásico supervisado.

## Objetivo

Predecir la carga de calefacción de edificios simulados a partir
de ocho características físicas y arquitectónicas, comparando
varios modelos de regresión.

## Datos

Se utiliza el dataset Energy Efficiency de UCI Machine Learning
Repository, con 768 configuraciones simuladas, ocho variables
de entrada y dos objetivos numéricos.

Este proyecto utiliza únicamente la carga de calefacción
(`heating_load`) como objetivo.

Fuente:
Tsanas, A. y Xifara, A. (2012). Energy Efficiency [Dataset].
UCI Machine Learning Repository.
DOI: 10.24432/C51307.

## Modelos evaluados

- Regresión lineal.
- Ridge con escalado mediante un pipeline.
- Árbol de decisión.
- Random Forest.

## Metodología

- Revisión de datos, valores ausentes y duplicados.
- Exploración mediante histogramas y gráficos de dispersión.
- Separación de entrenamiento y prueba: 80 % y 20 %.
- Validación cruzada de cinco particiones sobre entrenamiento.
- Estudio de la profundidad del árbol y del parámetro alpha de Ridge.
- Comparación mediante MAE, RMSE y R².
- Análisis de residuos e importancia de las variables.

## Resultados

| Modelo | RMSE medio de validación cruzada | RMSE de prueba |
|---|---:|---:|
| Regresión lineal | 2,9292 | 3,0254 |
| Ridge ajustado | 2,9290 | 3,0264 |
| Árbol sin límite | 0,5801 | 0,6206 |
| Random Forest | 0,5110 | 0,4908 |

Random Forest fue seleccionado como modelo final. En el conjunto
de prueba obtuvo un MAE de 0,3547 y un R² de 0,9977.

En el experimento separado de profundidades, un árbol con profundidad
máxima 8 obtuvo un RMSE medio de validación cruzada de 0,5500.

## Cómo ejecutar el proyecto

1. Abrir `energy_efficiency_regression.ipynb` en Google Colab.
2. Obtener el archivo `ENB2012_data.xlsx` del dataset Energy Efficiency.
3. Ejecutar las celdas en orden.
4. Subir el archivo cuando lo solicite la celda de carga.

El notebook utiliza pandas, matplotlib y scikit-learn.
La lectura del archivo Excel requiere un motor compatible, como openpyxl.

## Limitaciones

- Los datos son simulados, no mediciones de edificios reales.
- Los resultados corresponden al dataset y a las particiones utilizadas.
- El conjunto de prueba se consultó durante una exploración inicial;
  esta limitación se documenta en el notebook.
- Las importancias de las variables no demuestran causalidad.
- El modelo no está validado para decisiones reales de ingeniería.

## Posibles mejoras

- Analizar con más detalle las variables categóricas.
- Evaluar la generalización a grupos de configuraciones diferentes.
- Repetir el análisis para la carga de refrigeración.
