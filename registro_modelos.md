
# Registro de Modelos Probados y Técnicas Utilizadas

Este archivo contiene un seguimiento de los modelos y técnicas utilizadas hasta el momento para el análisis de datos en `C:\DB_Covid19Arg\csv_archivos_limpios`. Aquí se detallan los modelos probados, los resultados obtenidos y las técnicas que están en proceso o pendientes.

---

## Modelos Probados:

### 1. Random Forest (`modelo_random_forest.py`)
   - **Parámetros optimizados:** 
     - n_estimators: 300
     - max_depth: 30
     - min_samples_split: 5
     - min_samples_leaf: 2
     - bootstrap: True
   - **Exactitud del modelo optimizado:** 0.3503
   - **Observaciones:** El modelo obtuvo una precisión limitada debido al desbalance de clases.

### 2. Random Forest con SMOTE (`modelo_random_forest_smote.py`)
   - **Exactitud:** 0.5883
   - **Observaciones:** SMOTE fue aplicado para balancear las clases antes del ajuste del modelo.

### 3. XGBoost (`modelo_xgboost_optimizado.py`)
   - **Mejores hiperparámetros:**
     - subsample: 0.8
     - n_estimators: 200
     - max_depth: 6
     - learning_rate: 0.2
     - colsample_bytree: 1.0
   - **Exactitud del modelo:** 0.0088
   - **Observaciones:** El modelo no logró un buen rendimiento debido al fuerte desbalance en los datos.

### 4. Gradient Boosting (`modelo_gradient_boosting.py`)
   - **Estado:** En proceso
   - **Detalles del ajuste:**
     - Fitting 3 folds for each of 10 candidates, totalling 30 fits.
     - Diversas combinaciones de `learning_rate`, `max_depth`, `n_estimators`, y `subsample`.

---

## Técnicas y Modelos Pendientes:

### 1. SMOTE (Ajuste de parámetros)
   - **Descripción:** Ajustar los parámetros de SMOTE como `sampling_strategy` o `k_neighbors` para obtener un mejor equilibrio en los datos.
   - **Código:** `modelo_smote_ajustado.py`

### 2. ADASYN
   - **Descripción:** Probar el modelo con ADASYN para generar nuevas muestras en las clases minoritarias.
   - **Código:** `modelo_adasyn.py`

### 3. LightGBM y CatBoost
   - **Descripción:** Probar otros modelos como LightGBM y CatBoost para obtener comparaciones adicionales.
   - **Códigos:** `modelo_lightgbm.py` y `modelo_catboost.py`

### 4. Bayesian Optimization
   - **Descripción:** Optimización bayesiana para ajustar modelos y mejorar los resultados.
   - **Estado:** Pendiente.

---

Este archivo se actualizará conforme se obtengan más resultados y se ajusten los modelos en proceso.
