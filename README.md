# ChallengeTelecomX2
# 📉 Predicción de Abandono de Clientes (Customer Churn Prediction)

## 📖 Descripción del Proyecto
Este proyecto de Machine Learning tiene como objetivo predecir la probabilidad de que un cliente cancele su servicio (Churn) utilizando datos históricos de suscripción, facturación y características demográficas. 

El enfoque principal no es solo lograr una alta exactitud predictiva, sino **optimizar la métrica de Sensibilidad (Recall)** para identificar la mayor cantidad posible de clientes en riesgo de fuga y extraer *insights* accionables para el equipo de retención.

## 🛠️ Tecnologías Utilizadas
* **Lenguaje:** Python 3.x
* **Manipulación y Análisis de Datos:** `pandas`, `numpy`
* **Visualización:** `matplotlib`, `seaborn`
* **Machine Learning:** `scikit-learn` (Random Forest, K-Nearest Neighbors, GridSearchCV)
* **Manejo de Clases Desbalanceadas:** `imbalanced-learn` (SMOTE, RandomUnderSampler, Pipeline)

## ⚙️ Metodología y Flujo de Trabajo

1. **Análisis Exploratorio de Datos (EDA):** Análisis bivariado para encontrar patrones visuales entre las características del cliente y la tasa de cancelación.
2. **Preprocesamiento:** * Codificación de variables categóricas (One-Hot Encoding).
   * Estandarización de variables numéricas (`StandardScaler`).
3. **Manejo de Desbalanceo de Clases (Pipeline Híbrido):**
   * Implementación de una arquitectura estricta para evitar *Data Leakage*.
   * Generación de datos sintéticos para la clase minoritaria (`SMOTE`).
   * Submuestreo de la clase mayoritaria (`RandomUnderSampler`).
4. **Modelado y Optimización:**
   * Entrenamiento de modelos K-Nearest Neighbors (basado en distancias) y Random Forest (basado en reglas lógicas).
   * Búsqueda exhaustiva de hiperparámetros con `GridSearchCV` optimizando la métrica de `Recall`.
5. **Evaluación de Modelos:** Comparación mediante Matrices de Confusión, F1-Score y Curva ROC-AUC.
6. **Interpretabilidad:** Extracción de la "Importancia de Variables" (Reducción de Impureza de Gini y Permutación) para entender los detonantes matemáticos de la cancelación.

## 📊 Resultados Clave e Insights de Negocio

El modelo **Random Forest** demostró ser el algoritmo superior, logrando el mejor equilibrio entre detectar bajas reales y minimizar los falsos positivos. El análisis de importancia de variables reveló los siguientes *insights* críticos:

* **El Blindaje del Contrato:** La antigüedad (`Antiguedad_Meses`) y poseer un contrato a largo plazo (`Tipo_Contrato_Two year`) son los mayores protectores contra la cancelación. Los contratos "Mes a mes" presentan alta volatilidad.
* **El Problema de la Fibra Óptica:** El servicio de internet de fibra óptica (`Servicio_Internet_Fiber optic`) apareció como un fuerte predictor de abandono, sugiriendo una posible brecha entre el precio pagado y la calidad percibida del servicio o fallas técnicas recurrentes.
* **Fricción en Pagos:** Los métodos de pago manuales, como el cheque electrónico (`Metodo_Pago_Electronic check`), incrementan drásticamente el churn pasivo en comparación con los pagos automatizados.
