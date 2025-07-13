# TelecomX_LATAM-_PARTE_2

#  Telecom X - Predicción de Cancelación de Clientes (Churn)

Este proyecto forma parte del desafío de Ciencia de Datos y Machine Learning de Alura LATAM. El objetivo fue predecir qué clientes de una empresa de telecomunicaciones tienen mayor probabilidad de cancelar el servicio, utilizando técnicas de aprendizaje supervisado.

---

##  Datos

Se utilizó el archivo `datos_tratados.csv`, el cual ya contenía datos limpios y preprocesados, con las siguientes características:

- 7043 registros
- Variables numéricas, binarias y categóricas
- Variable objetivo: `baja_cliente` (0 = activo, 1 = cancelado)

---

## Etapas del Proyecto

### 1.  Análisis de Desbalance de Clases

- Se identificó un desbalance entre clases: solo el 26% de los clientes estaban marcados como cancelados.
- Se aplicó **SMOTE (Synthetic Minority Oversampling Technique)** para balancear la clase minoritaria en el conjunto de entrenamiento.

### 2.  Preprocesamiento

- **Eliminación de columnas irrelevantes**, como identificadores o variables redundantes.
- **Codificación de variables categóricas** mediante `pd.get_dummies()`.
- **Conversión de booleanos a enteros**.
- **Estandarización** de variables numéricas para modelos sensibles a la escala (`StandardScaler`).

### 3.  Análisis de Correlación

- Se utilizó una matriz de correlación para:
  - Identificar variables fuertemente relacionadas con `baja_cliente`.
  - Detectar casos de posible multicolinealidad (moderada) entre variables financieras.

### 4.  División del Dataset

- Conjunto de entrenamiento: 80%
- Conjunto de prueba: 20%

---

##  Modelos Entrenados

Se entrenaron dos modelos con enfoques complementarios:

| Modelo              | Escalado | Accuracy | Precisión | Recall | F1-score |
|---------------------|----------|----------|-----------|--------|----------|
| Regresión Logística | Sí       | 0.7381   | 0.5046    | 0.7273 | 0.5958   |
| Random Forest       | No       | 0.7559   | 0.5355    | 0.6043 | 0.5678   |

- La **Regresión Logística** destacó por su *recall*, ideal para no perder clientes en riesgo.
- El **Random Forest** fue más equilibrado en todas las métricas, ideal para decisiones generales de negocio.

---

## Análisis de Importancia de Variables

### Regresión Logística

Variables con mayor impacto negativo en cancelación (es decir, retienen al cliente):

- `tipo_contrato_two year`
- `tipo_contrato_one year`
- `gasto_total_cliente`
- `metodo_pago_credit card (automatic)`

Variables que aumentan la probabilidad de cancelación:

- `cuentas_diarias`
- `total_mensual_servicios`

### Random Forest

Variables más importantes para la predicción:

- `gasto_total_cliente`
- `total_mensual_servicios`
- `cuentas_diarias`
- `tipo_contrato_two year`
- `tipo_contrato_one year`

---

##  Conclusiones Estratégicas

- Los contratos de largo plazo y mayor gasto acumulado están relacionados con mayor retención.
- Clientes con pagos mensuales altos o mucha actividad diaria podrían estar más insatisfechos.
- Promover el uso de **métodos automáticos de pago** mejora la permanencia del cliente.

---

##  Herramientas Utilizadas

- Python (Google Colab)
- pandas, numpy, seaborn, matplotlib
- scikit-learn
- imbalanced-learn (SMOTE)

---

##  Autor

Mariana Espíndola  
Desarrollado en el marco del programa de formación en Ciencia de Datos y Machine Learning de Alura LATAM 
