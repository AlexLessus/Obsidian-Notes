Tags: [[Aprendizaje Automático]] [[Etica de la IA]]

# ¿Qué técnicas o metodologías o tareas pudiéramos realizar para evitar que nuestros sistemas generados a traves del ML tuviera algún tipo de sesgo?

### 1. En la fase de Preparación de Datos
Es donde más impacto tendrás, ya que el sesgo suele venir de datos "sucios" o incompletos.
- **Limpieza de los datos:** Eliminar información errónea o corregir etiquetas mal asignadas que podrían enseñar al modelo asociaciones falsas.  
- **Manejo de datos faltantes**: Si a un grupo de personas le faltan datos sistemáticamente (ej. ingresos en cierta zona demográfica), simplemente "rellenar" esos huecos sin cuidado puede introducir un sesgo artificial. Debes decidir si imputar o eliminar con criterio estadístico.    
- **Detección y tratamiento de valores atípicos (outliers):** A veces, las minorías en un dataset aparecen como "outliers" matemáticos. Un mal tratamiento aquí podría hacer que tu modelo ignore completamente a estos grupos por considerarlos "ruido".
- **Selección de características:** Decidir qué variables entran al modelo. Aquí es vital la tarea humana de **no incluir** variables sensibles (como género o raza) si no son pertinentes, o detectar variables que actúan como "proxies" de estas.    
- **Manejo de datos categóricos:** Asegurar que todas las categorías estén bien representadas numéricamente para que el algoritmo no de peso arbitrario a una sobre otra.

### 2. En la fase de Modelado y Entrenamiento
- **Evaluación cruzada:** En lugar de entrenar con un solo bloque de datos (que podría estar sesgado por casualidad), rotas los datos para asegurar que el modelo funciona bien en _todos_ los subconjuntos de información.    
- **División de datos de prueba:** Garantizar que tu conjunto de prueba (test set) sea representativo de la realidad y no solo una copia del entrenamiento. Si entrenas con datos de "A" y pruebas con datos de "A", nunca verás el sesgo contra "B".

### 3. En la fase de Evaluación
- **Evaluación de métricas:** No basta con mirar la "precisión" (accuracy). Si tienes 90 hombres y 10 mujeres, un modelo que diga "siempre es hombre" tendrá 90% de acierto, pero será totalmente sesgado. Debes usar métricas que revelen estos desequilibrios (como la matriz de confusión o F1-score).

### 4. Desde la Ética
- **Análisis de Sesgo en los datos:** Es la tarea explícita de auditar tus fuentes antes de empezar. Preguntar: ¿Quién recolectó esto? ¿Falta algún grupo poblacional?    
- **Privacidad y uso responsable:** Asegurar que los datos se usen para el fin que fueron donados, evitando inferencias invasivas.

