## **_PROYECTO INDIVIDUAL 01 - DATA ENGINEER_**

---

## INTRODUCCIÓN

Hola!👋 Me llamo Nicolás Angel Lazarte, les presento mi proyecto individual de Machine Learning realizado durante el Bootcamp de Data Science de SoyHenry.  
El proyecto consiste en desarrollar un análisis en torno a un problema de clasificación de estadías cortas o largas en pacientes Hospitalizados. Dicho análisis conyeva realizar una serie de pasos tales como el entendimiento de los datos, análisis exploratorio, preprocesamiento y las etapas propias del modelo de Machine Learning. Se disponen de datos históricos de pacientes con la duración en días de su estadía y para el análisis se considera una hospitalización corta de 8 días o menos.

## Objetivo

Construir un modelo de Machine Learning optimizado que permita obtener buenas métricas de accuracy y recall. Se considera ésta última como prioritaria al querer predecir con mayor exhaustividad las estadías largas para el ingreso de pacientes.

## Directorios y archivos del repositorio

- [**Data:**](./Data/) Directorio donde se disponibilizan las fuentes de datos. Un archivo de _hospitalizaciones_train_ que se considera para el desarrollo del modelo y otro _hospitalizaciones_test_ que contiene datos nuevos sobre el cual el modelo debe realizar las predicciones correspondientes y comparado con los resultados reales otorgados por Henry
- [**Notebook Modelo:**](./PI02_Datathon_Hospitalizacion.ipynb) Notebook donde se desarrolla el proyecto de Machine Learning

## ETAPAS DEL PROYECTO

---

### **1) Comprensión de los datos y EDA**

En primer lugar se realiza un estudio de las fuente de datos disponibilizada en archivo `.csv` entendiendo cada una de las variables relativas al registro de cada paciente
Se hace una exploración de datos utilizando Pandas-Profiling para obtención de un reporte, pandas, matplotlib y seaborn para exploración de distribuciones, outliers, etc. Determino algunas observaciones necesarias para la selección de variables.

### **2) Preparación de los datos**

En esta etapa realizo el Feature Selection en base a ciertos criterios (correlación, tree-based selection, criterio propio), la división de los datos de entrenamiento (80%) y testeo (20%), y el conjunto de pasos de preprocesamiento de datos en el que incluyo `PipeLines` y `ColumnTransformer` para la unificación de todos los pasos de preprocesado.

### **3) Modelado**

En base a las variables seleccionadas y los datos preprocesados se seleccionan 5 modelos para entrenar en forma simultanea con los parámetros por defecto:

- Arbol de desición
- KNN
- Regresión logística
- SVM método lineal
- RandomForest

Se obtiene una tabla con los scores a considerar (accuracy en train-test y recall)

### **4) Evaluación y Validación**

En algunos modelos se genera overfitting (Tree y RandomForest) por la diferencia entre los accuracy de entrenamiento y testeo por lo que se decide entrenar y testear nuevamente los modelos reduciendo la dimensionalidad. Se decide quitar algunas variables que contienen outliers y otras que se seleccionaron previamente por criterio propio pero que no tienen correlación con el target.
Se general algunas alternativas, de las cuales se elige `DecisionTreeClasifier()` con la mínima cantidad de variables correlacionadas. Luego se valida con Cross validation

### **5) Optimización de Hiperparámetros**

### **6) Construcción Final del Pipeline**
