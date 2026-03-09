# Telecom X Latam - Parte 2: Predicción de Churn (Cancelación de Clientes)

## 📌 Propósito del Proyecto
Este proyecto representa la segunda fase del análisis de datos para Telecom X Latam. Mientras que la primera parte se centró en la limpieza y tratamiento de los datos, el objetivo principal de esta fase es desarrollar un modelo predictivo capaz de anticipar qué clientes tienen mayor probabilidad de cancelar sus servicios (churn).

La empresa busca pasar de una postura reactiva a una proactiva. Al identificar a los clientes en riesgo antes de que tomen la decisión de irse, la gerencia puede implementar estrategias de retención focalizadas, optimizando así los recursos y mejorando el valor del ciclo de vida del cliente.

## ⚙️ Descripción del Proceso de Preparación de Datos
Antes de entrenar los algoritmos, los datos procesados en la Parte 1 fueron pre-preparados y en esta parte lo tratamos específicamente para el modelado de Machine Learning siguiendo estos pasos:

### Clasificación de Variables:

Categóricas: Variables como Método de pago, Tipo de contrato, Servicio de Internet, Género, etc.

Numéricas: Variables continuas como Cargo mensual, Cargo total y Antigüedad (Tenure).

### Normalización y Codificación:

Las variables categóricas fueron transformadas a un formato numérico comprensible por los modelos utilizando el modulo de pandas get_dummy.

Las variables numéricas con diferentes escalas fueron estandarizadas/normalizadas para evitar que variables con rangos más amplios dominaran el entrenamiento del modelo KNN.

### Separación de Datos (Train/Test Split):

El dataset se dividió en dos conjuntos: uno de entrenamiento (Train) para que el modelo aprenda los patrones, y uno de prueba (Test) para evaluar su rendimiento de manera objetiva con datos "inéditos".

### Tratamiento del Desbalanceo de Clases:

Dado que la tasa de churn natural era del ~25%, existía un desbalance respecto a la clase retenida. Se utilizó la librería imbalanced-learn ( técnicas SMOTE) para balancear los datos de entrenamiento y evitar que el modelo se sesgara hacia la clase mayoritaria (poque queriamos identificar a los que clientes que abandonaban).

## 🧠 Justificaciones para la Modelización
Para este desafío se optó por construir y evaluar modelos basados en árboles de decisión , dummy y knn, destacando el uso de Random Forest. Las decisiones clave incluyen:

Elección del Algoritmo Champion (Random Forest): Se eligió por su alta precisión, su robustez frente a valores atípicos y su capacidad para capturar relaciones no lineales complejas sin requerir una transformación exhaustiva de los datos.

Métricas de Evaluación: Más allá del Accuracy (Exactitud), el modelo se evaluó utilizando Recall (Sensibilidad) y F1-Score, ya que en problemas de Churn es más costoso no detectar a un cliente que se va (Falso Negativo) que predecir erróneamente que se irá (Falso Positivo).

## 📊 Insights y Resultados del Análisis Exploratorio (EDA)
### Durante el análisis y confirmados por la importancia de variables del modelo, se obtuvieron los siguientes hallazgos críticos:

La Antigüedad es clave: Existe una correlación negativa fuerte. Los clientes más nuevos (primeros 6 meses) presentan el mayor riesgo de abandono.

El peligro del "Mes a Mes": Los usuarios con contratos mensuales son la principal fuente de fuga. Los contratos a 1 o 2 años son el factor de retención más fuerte.

Alerta en Fibra Óptica: Sorprendentemente, los clientes con servicio de Fibra Óptica tienen una tasa de cancelación superior a los de servicio a internet DSL, lo que sugiere problemas de calidad técnica, intermitencia o insatisfacción con el precio.

## 🚀 **Instrucciones para Ejecutar el Cuaderno**
Para reproducir este análisis en tu máquina local o entorno en la nube, sigue estos pasos:

Requisitos Previos (Librerías)
Asegúrate de tener instalado Python 3.8+ y las siguientes dependencias. Puedes instalarlas ejecutando:

pip install pandas numpy scikit-learn matplotlib seaborn imbalanced-learn

Ejecución
Clona este repositorio o descarga los archivos.

Asegúrate de que el archivo de datos tratados (telecom_x_tratado.csv o similar) se encuentre en la ruta correcta (generalmente dentro de la carpeta data/ o en el mismo directorio si usas Google Colab).

Abre el cuaderno principal:

jupyter notebook notebooks/TelecomXLatamPrediccionDeChurn.ipynb

Ejecuta las celdas de forma secuencial. El cuaderno está diseñado para importar los datos, preprocesarlos, entrenar el modelo y finalmente imprimir las métricas de validación y las matrices de confusión.

******* 
Desarrollado como parte de la resolución del caso práctico Telecom X Latam - Cristian Aramayo.
