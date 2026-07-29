## 🏡 Predicción de Precios de Vivienda con Machine Learning
Proyecto de regresión que estima el precio de venta de una vivienda a partir de sus características estructurales, comparando un modelo lineal (Regresión Lineal) con uno basado en árboles (Random Forest).

#

### 🧠 Pregunta de negocio
¿Qué características de una vivienda explican mejor su precio, y qué tan bien puede automatizarse una estimación confiable sin recurrir a un tasador humano?

#

### 🗂️ Dataset
Ames Housing Dataset — ~1,460 registros de viviendas con variables estructurales (área habitable, calidad general, año de construcción, barrio, entre otras) junto con su precio de venta. Se seleccionaron 8 variables relevantes de las 81 disponibles en el dataset original.

#

### 🛠️ Herramientas
Python · Pandas · NumPy · Scikit-learn · Matplotlib · Seaborn

#

### 🔍 Proceso
- Análisis exploratorio de datos (EDA) y detección de outliers
- División train/test antes de cualquier transformación, para evitar fuga de información
- Preprocesamiento con `Pipeline` y `ColumnTransformer` (encoding y escalado ajustados solo con train)
- Transformación logarítmica del target (`log1p`) para corregir el sesgo de `SalePrice`
- Entrenamiento y comparación de dos modelos: Regresión Lineal y Random Forest
- Validación cruzada (5-fold) y análisis de residuos
- Explicabilidad del modelo: coeficientes (lineal) y feature importance (Random Forest)
- Función de predicción con validación de inputs

#

### 📈 Resultados
Los análisis muestran que la variable que más impulsa el precio de la vivienda es GrLivArea (área habitable), seguida de OverallQual (calidad general). Random Forest superó a la Regresión Lineal en las métricas de test, y tras controlar su complejidad (max_depth=10, min_samples_leaf=5) la brecha train-test se redujo notablemente, a un costo mínimo de desempeño — un trade-off favorable que se adopta como modelo final.

Ambos modelos siguen mostrando algo más de error en el segmento de viviendas de alto valor, dado que la mayoría de los datos se concentra en el rango de  100k– 350k, dejando menos ejemplos para que el modelo aprenda el comportamiento de las casas más caras.
Este proyecto pasó por una ronda de revisión técnica que corrigió un bug de flujo de datos (los outliers detectados no se eliminaban realmente antes de modelar), incorporó la transformación logarítmica del target, y migró el preprocesamiento a un `Pipeline` de scikit-learn para eliminar fuga de información en el encoding.

#

### Proyecto

[Proyecto](https://github.com/aacekm-7/Prediccion-Precio-Casas/blob/main/model_lr_rf.ipynb)
