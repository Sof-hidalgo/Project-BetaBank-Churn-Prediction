# Project-BetaBank-Churn-Prediction

# 📌 Modelo para Identificar Clientes en Riesgo de Churn - Beta Bank

## 📝 Descripción:
El proyecto busca desarrollar un modelo de machine learning que prediga qué clientes de Beta Bank podrían abandonar el banco. Se trabajó con datos históricos de clientes, incluyendo información demográfica, comportamiento financiero y nivel de interacción con el banco.

## 🎯 Objetivo:
Crear un modelo predictivo efectivo que permita identificar clientes en riesgo de churn, optimizando la retención y reduciendo costos de adquisición de nuevos clientes.

### Descripción de los datos
Puedes encontrar los datos en el archivo Churn.csv.

### Características

- RowNumber: índice de cadena de datos
- CustomerId: identificador de cliente único
- Surname: apellido
- CreditScore: valor de crédito
- Geography: país de residencia
- Gender: sexo
- Age: edad
- Tenure: período durante el cual ha madurado el depósito a plazo fijo de un cliente (años)
- Balance: saldo de la cuenta
- NumOfProducts: número de productos bancarios utilizados por el cliente
- HasCrCard: el cliente tiene una tarjeta de crédito (1 - sí; 0 - no)
- IsActiveMember: actividad del cliente (1 - sí; 0 - no)
- EstimatedSalary: salario estimado
- Objetivo: Exited: El cliente se ha ido (1 - sí; 0 - no)

### Pasos del proyecto
- Descargar y preparar los datos.  Explicar el procedimiento.
- Examinar el equilibrio de clases. Entrenar el modelo sin tener en cuenta el desequilibrio. Describir brevemente los hallazgos.
- Mejorar la calidad del modelo. Utilizar al menos dos enfoques para corregir el desequilibrio de clases. Utilizar conjuntos de entrenamiento y validación para encontrar el mejor modelo y el mejor conjunto de parámetros. Entrenar diferentes modelos en los conjuntos de entrenamiento y validación. Encontrar el mejor. Describir brevemente tus hallazgos.
- Realizar la prueba final.

[Igualmente, en el archivo .ipynb se dejarán comentarios más específicos de cada paso.]

## 📈 Conclusiones Finales:
- Mejor Modelo: Random Forest con sobremuestreo obtuvo un F1-score de 0.639 y un AUC-ROC de 0.868, lo que demuestra una alta capacidad de clasificación.
- Impacto del Balanceo de Clases:
  - Sin balanceo, el F1-score máximo fue 0.6425.
  - Con sobremuestreo, se mantuvo en 0.639, mostrando que es una técnica efectiva para mejorar el equilibrio sin perder precisión.
  - El submuestreo, en cambio, redujo el F1-score a 0.536, lo que sugiere pérdida de información.
- Conclusión Final: El sobremuestreo resultó ser la mejor técnica para este caso, asegurando un mejor equilibrio entre precisión y recall, sin perder efectividad en la clasificación.

## 🛠 Skills Obtenidas:
- Machine Learning: Random Forest, Decision Trees y Regresión Logística.
- Preprocesamiento de Datos: Manejo de valores nulos, codificación categórica y normalización.
- Balanceo de Clases: Uso de técnicas de ajuste de pesos, sobremuestreo y submuestreo.
- Métricas de Evaluación: F1-score y AUC-ROC.
- Python: Extracción y análisis de datos.

## 🔍 Lecciones Aprendidas:
- La importancia de balancear las clases en datasets desbalanceados para evitar sesgos en el modelo.
- La métrica AUC-ROC es fundamental para evaluar modelos con clases desbalanceadas.
- La experimentación con diferentes técnicas de balanceo permite identificar la más efectiva según el contexto.
