Alexis De Jesus Perez Carmona
# **Actividad 1.- Diseño metodológico del proyecto**
### Descripción Metodológica
La presente investigación adopta un enfoque **cuantitativo** con un diseño **experimental** y de **investigación aplicada**. El procedimiento se divide en cuatro fases técnicas que aseguran la replicabilidad del experimento:

1. **Fase de Adquisición y Limpieza:** Se utilizará el dataset benchmark **CIC-IDS2017**, el cual contiene flujos de red etiquetados. Se realizará un preprocesamiento para manejar valores nulos y eliminar registros duplicados.
2. **Fase de Ingeniería de Características:** Se aplicarán algoritmos de selección para identificar las variables de red más influyentes, reduciendo la dimensionalidad y el ruido del modelo.
3. **Fase de Optimización de Hiperparámetros:** Es el núcleo del proyecto. Se implementará una búsqueda mediante **Optimización Bayesiana** utilizando el framework **Optuna**. A diferencia de una búsqueda aleatoria, este método utiliza un modelo probabilístico para encontrar la configuración óptima de los algoritmos **Random Forest** y **XGBoost** en el menor número de iteraciones posible.
4. **Fase de Evaluación:** Se someterá al modelo optimizado a una prueba de validación con el 30% del dataset original (datos no vistos) para calcular métricas de desempeño.
### Tabla de Variables
La operacionalización de las variables permite medir el impacto de la optimización en la seguridad de la red.

| **Tipo de Variable** | **Nombre de la Variable**      | **Definición Conceptual**                                                                                         | **Indicador (Métrica)**                                          |
| -------------------- | ------------------------------ | ----------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| **Independiente**    | **Hiperparámetros del modelo** | Configuraciones externas al algoritmo que definen su estructura (ej. profundidad del árbol, tasa de aprendizaje). | Valores configurados en el script de entrenamiento (int, float). |
| **Dependiente**      | **Rendimiento de detección**   | Capacidad del sistema para clasificar correctamente el tráfico malicioso y el normal.                             | $Accuracy$, $Precision$, $Recall$ y $F1\text{-}Score$.           |
| **Control**          | **Dataset de referencia**      | Fuente de datos estandarizada para garantizar que los resultados sean comparables.                                | Dataset **CIC-IDS2017**.                                         |
### Instrumento Diseñado
**Descripción del Instrumento:**
Se trata de un pipeline de software automatizado que consta de los siguientes módulos:
- **Módulo de Ingesta:** Carga de datos masivos mediante la librería **Pandas**.

- **Módulo de Clasificación:** Motores de aprendizaje basados en **Scikit-learn** y **XGBoost**.

- **Módulo de Medición (El instrumento de recolección):** Un script de validación que genera la **Matriz de Confusión**. Este módulo captura los Verdaderos Positivos ($TP$), Falsos Positivos ($FP$), Verdaderos Negativos ($TN$) y Falsos Negativos ($FN$) para calcular el éxito del modelo mediante la fórmula del **Puntaje F1**:    $$F1 = 2 \cdot \frac{Precision \cdot Recall}{Precision + Recall}$$
# **Actividad 2.-** **Procedimiento metodológico y plan de ejecución**

### Población y Muestra
- **Población (Universo):** Está constituida por la totalidad de los registros de tráfico de red (instancias) contenidos en el dataset benchmark **CIC-IDS2017**, el cual comprende aproximadamente 2.8 millones de flujos de datos etiquetados con diversas categorías de tráfico normal y malicioso.    
- **Muestra:** Se utilizará un **muestreo aleatorio estratificado** para asegurar la representatividad de todas las clases de ataques en los subconjuntos.
    - **Subconjunto de Entrenamiento (70%):** Utilizado para que el algoritmo aprenda los patrones y correlaciones de las amenazas.        
    - **Subconjunto de Prueba (30%):** Reservado para evaluar el desempeño final del modelo con datos no vistos previamente, permitiendo validar la hipótesis de investigación.

### Procedimiento Metodológico
- **Adquisición de Datos:** Se realizará la descarga y carga del dataset **CIC-IDS2017** en el entorno de desarrollo (Google Colab/Local), verificando la integridad de los archivos CSV.
- **Limpieza y Preprocesamiento:** Se aplicarán técnicas de manejo de valores nulos, eliminación de duplicados y normalización de escalas numéricas para asegurar que las variables tengan el mismo peso en el modelo.
- **Selección de Características (Feature Selection):** Se utilizarán algoritmos para identificar las variables de red más influyentes, optimizando el tiempo de procesamiento y mejorando la capacidad predictiva.
- **Ciclo de Optimización y Entrenamiento:** Se implementará la búsqueda mediante **Optimización Bayesiana** (framework **Optuna**) para ajustar los hiperparámetros de los algoritmos **Random Forest** y **XGBoost**.
- **Evaluación Estadística:** Se someterá al modelo a pruebas de validación para calcular la **Matriz de Confusión** y obtener métricas de **Precisión**, **Exhaustividad** y el **Puntaje F1**.
- **Análisis Comparativo:** Se realizará un contraste entre los resultados obtenidos con el modelo optimizado frente a un modelo base (sin optimización) para cuantificar la mejora en la detección.

### Cronograma de ejecución

| **Fase / Unidad**                | **Actividad Principal**                                       | **Mes** | **Entregable Esperado**             |
| -------------------------------- | ------------------------------------------------------------- | ------- | ----------------------------------- |
| I. Evaluación y Complementación  | Análisis FODA y revisión del protocolo inicial.               | Marzo   | Protocolo actualizado y aprobado.   |
|                                  | Desarrollo del Marco Teórico.                                 | Marzo   | Marco conceptual y referencial.     |
|                                  | Definición y operacionalización de variables.                 | Marzo   | Tabla de variables e indicadores.   |
| II. Desarrollo de la Metodología | Diseño y validación de instrumentos (Scripts de ML).          | Marzo   | Código base y dataset preprocesado. |
|                                  | Ejecución de experimentos y Optimización Bayesiana.           | Abril   | Logs de entrenamiento y resultados. |
|                                  | Recolección, tratamiento y análisis estadístico de datos.     | Mayo    | Gráficas de desempeño y métricas.   |
| III. Presentación del Informe    | Elaboración del reporte de investigación (estructura formal). | Mayo    | Informe final de investigación.     |
|                                  | Preparación de material audiovisual para la defensa.          | Junio   | Presentación de diapositivas.       |
|                                  | Presentación oral y defensa ante el sínodo.                   | Junio   | Acta de evaluación y cierre.        |
