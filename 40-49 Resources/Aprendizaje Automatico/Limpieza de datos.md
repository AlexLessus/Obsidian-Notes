Alexis De Jesus Perez Carmona
#MachineLearning 
### 1. ¿En qué consiste la limpieza de los datos?
La limpieza de datos (o _Data Cleaning_) es una fase crítica dentro del preprocesamiento. Consiste en identificar, corregir, reemplazar o eliminar registros que sean erróneos, incompletos, irrelevantes o que tengan un formato incorrecto dentro de un conjunto de datos (dataset) antes de alimentar a un modelo algorítmico. Básicamente, es auditar la base de datos para asegurar que la información sea coherente matemáticamente.

### 2. ¿Cuál es la finalidad de realizarla?
El objetivo principal es garantizar la calidad y adecuación de los datos para que los modelos de aprendizaje automático funcionen correctamente. En ingeniería de software y ciencia de datos existe la regla de oro **GIGO** (_Garbage In, Garbage Out_ o "Basura entra, basura sale"). Si entrenas un modelo algorítmico con datos defectuosos, sus predicciones o clasificaciones serán incorrectas, sin importar qué tan avanzada sea la arquitectura matemática que utilices. Una buena limpieza mejora la precisión del modelo y reduce los tiempos de procesamiento.

### 3. ¿Qué tipo de anomalías, defectos o ruido debemos limpiar?
Al extraer información de bases de datos o sensores, te encontrarás con defectos estructurales que arruinan el entrenamiento:

- **Datos faltantes (Missing values):** Celdas vacías o valores nulos (como un `NaN` o un `NULL` en SQL).
- **Valores atípicos (Outliers):** Puntos de datos que difieren drásticamente del resto de las observaciones (por ejemplo, registrar una temperatura ambiente de 180°C debido a un error del sensor).
- **Datos duplicados:** Filas idénticas repetidas que pueden sesgar el modelo dándole más peso matemático a una sola observación.
- **Inconsistencias de formato:** Diferentes formas de escribir lo mismo, como mezclar mayúsculas y minúsculas ("Guadalajara" vs "guadalajara"), o fechas en distintos formatos (DD/MM/AAAA vs MM/DD/AAAA).
- **Ruido estructural:** Caracteres especiales no deseados, etiquetas HTML coladas en texto plano o errores tipográficos.

### 4. ¿Cuál es el proceso que debemos de seguir para ello?
El proceso de limpieza se integra directamente con las técnicas que marca tu temario para acondicionar el dataset:
1. **Inspección inicial:** Cargar los datos (generalmente usando la librería Pandas) y ejecutar funciones exploratorias para detectar cuántos valores nulos o duplicados existen.
2. **Eliminación de duplicados y datos irrelevantes:** Borrar las filas idénticas y descartar columnas que no aportan valor predictivo (como el ID interno de un usuario).
3. **Manejo de datos faltantes:** Decidir si eliminar la fila completa que tiene el hueco, o rellenarla (imputación) usando el promedio, la mediana o un valor por defecto.
4. **Detección y tratamiento de valores atípicos:** Usar estadística (como el rango intercuartílico) para identificar los _outliers_ y decidir si se eliminan o se ajustan a un límite razonable.
5. **Estandarización y manejo de categóricos:** Convertir textos a formatos uniformes y transformar datos categóricos (como "Rojo", "Verde", "Azul") en valores numéricos que el algoritmo pueda procesar.
6. **Escalamiento y normalización:** Ajustar todas las variables numéricas a una escala común (por ejemplo, de 0 a 1) para que ninguna variable domine a otra solo por tener números más grandes.