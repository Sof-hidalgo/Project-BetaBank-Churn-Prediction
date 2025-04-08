# 📌 Proyecto: Predicción de Fuga de Clientes (Churn) para Beta Bank

## 📝 Introducción

Beta Bank está experimentando una pérdida gradual de clientes (churn), lo cual representa un costo significativo, ya que adquirir nuevos clientes es más caro que retener a los existentes. Este proyecto se enfoca en desarrollar un modelo de Machine Learning capaz de predecir qué clientes tienen una alta probabilidad de abandonar el banco, permitiendo así implementar estrategias de retención proactivas.

## 🎯 Objetivo

El objetivo principal es construir y evaluar un modelo de clasificación que prediga eficazmente la fuga de clientes (`Exited` = 1) basado en sus características demográficas, de cuenta y comportamiento. Se busca maximizar la métrica F1-Score (objetivo > 0.59) y el área bajo la curva ROC (AUC-ROC), métricas clave para problemas con clases desbalanceadas.

## Metodología

1.  **Carga y Exploración Inicial:** Se cargó el dataset `Churn.csv` y se realizó una inspección inicial para entender la estructura, tipos de datos y valores nulos.
2.  **Preprocesamiento de Datos:**
    *   Renombrado de columnas a formato `snake_case`.
    *   Verificación y manejo de duplicados (no se encontraron).
    *   Imputación de valores nulos en la columna `tenure` utilizando la mediana.
    *   Identificación y separación de variables categóricas, numéricas y no informativas.
    *   Eliminación de columnas no relevantes (`surname`, `row_number`, `customer_id`).
    *   Codificación de variables categóricas (`geography`, `gender`) mediante One-Hot Encoding (`pd.get_dummies` con `drop_first=True`).
3.  **Análisis Exploratorio de Datos (EDA):**
    *   Se analizó la distribución de la variable objetivo (`exited`), confirmando un desbalance significativo (aprox. 20% churn).
    *   Se visualizaron las distribuciones de variables numéricas clave (`credit_score`, `age`, `balance`, etc.) y su relación con la variable `exited` mediante histogramas y boxplots.
    *   Se examinó la tasa de churn promedio para diferentes categorías de variables como `geography`, `gender`, `has_cr_card`, `is_active_member` y `num_of_products` usando gráficos de barras.
    *   Se generó una matriz de correlación para las variables numéricas.
4.  **Preparación para Modelado:**
    *   Escalado de características numéricas utilizando `StandardScaler` (ajustado sobre el conjunto de entrenamiento).
    *   División del dataset en conjuntos de Entrenamiento (60%), Validación (20%) y Prueba (20%) de forma estratificada.
5.  **Modelado y Evaluación:**
    *   Se entrenaron inicialmente modelos de Árbol de Decisión, Random Forest y Regresión Logística sin tratar explícitamente el desbalance (más allá de la evaluación inicial). Se optimizaron hiperparámetros básicos (ej. `max_depth` para DT, `n_estimators` para RF) usando el set de validación y la métrica F1.
    *   **Manejo del Desequilibrio:** Se aplicaron y compararon tres técnicas sobre los modelos (principalmente Random Forest, que mostró mejor potencial):
        *   Ajuste de Peso de Clases (`class_weight='balanced'`).
        *   Sobremuestreo (Upsampling) de la clase minoritaria.
        *   Submuestreo (Downsampling) de la clase mayoritaria.
    *   **Selección del Modelo Final:** El modelo Random Forest entrenado con **datos sobremuestreados** mostró el mejor rendimiento combinado de F1-Score y AUC-ROC en el conjunto de validación.
6.  **Evaluación Final:** Se evaluó el modelo seleccionado (Random Forest con Sobremuestreo) en el conjunto de prueba (datos no vistos). Se generaron gráficos de evaluación:
    *   Matriz de Confusión.
    *   Curva ROC.
    *   Curva Precision-Recall.
7.  **Análisis de Características:** Se extrajo y visualizó la importancia de las características según el modelo final para entender los factores clave del churn.

## 📈 Resultados

*   El modelo final (Random Forest con datos sobremuestreados) alcanzó un **F1-Score de 0.638** y un **AUC-ROC de 0.866** en el conjunto de prueba, superando el objetivo de F1 > 0.59.
*   El modelo demuestra una buena capacidad para identificar clientes en riesgo (buen Recall) y una excelente habilidad para distinguir entre las clases (alto AUC).
*   Las características más importantes para predecir el churn resultaron ser: `age`, `num_of_products`, `balance`, `credit_score`, `is_active_member`, y `geography_Germany`.

## 🔍 Conclusiones y Recomendaciones

El análisis y el modelo desarrollado proporcionan a Beta Bank una herramienta valiosa para identificar proactivamente a los clientes con riesgo de fuga. Se recomienda:

1.  Implementar el modelo para generar puntuaciones de riesgo periódicas.
2.  Utilizar estas puntuaciones y los factores clave (edad, productos, actividad, geografía) para segmentar clientes y aplicar estrategias de retención personalizadas (ofertas, seguimiento, mejoras de servicio).
3.  Monitorizar el rendimiento del modelo y reentrenarlo con datos frescos. Realizar pruebas A/B sobre las estrategias de retención.

## 🛠 Tecnologías Utilizadas

*   Python 3
*   Pandas
*   NumPy
*   Matplotlib
*   Seaborn
*   Scikit-learn
