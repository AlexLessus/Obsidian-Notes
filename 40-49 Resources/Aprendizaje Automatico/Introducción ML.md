Tags: [[Machine Learning]]
**1. ¿Qué se entiende por aprendizaje supervisado?** 
Es un paradigma del Machine Learning donde un algoritmo se entrena utilizando un conjunto de datos que ya contiene las respuestas correctas. 
Funciona bajo la lógica de un "profesor" (los datos) que supervisa al "alumno" (el modelo); el modelo hace predicciones y el profesor lo corrige hasta que el margen de error sea mínimo.

![[Pasted image 20260325215011.png]]

**2. Características que lo definen**
- **Requiere pares de entrada/salida:** Trabaja mapeando variables independientes ($X$) hacia una variable dependiente o resultado esperado ($Y$).
- **Fase de entrenamiento explícita:** El modelo aprende de ejemplos históricos antes de intentar predecir datos nuevos.
- **Medible:** Su rendimiento se puede evaluar matemáticamente contrastando sus predicciones con las respuestas reales que se ocultaron durante la prueba.

**3. Casos de uso y tipos de problemas** Se divide fundamentalmente en dos grandes familias de problemas matemáticos:
- **Clasificación:** Cuando la variable a predecir es categórica (ej. "Aprobado" o "Reprobado", "Gato" o "Perro").
- **Regresión:** Cuando la variable a predecir es un valor numérico continuo (ej. predecir el precio futuro del dólar o la temperatura de mañana).

**4. Principales algoritmos o técnicas**
- Regresión Lineal y Regresión Logística.
- Árboles de Decisión y Bosques Aleatorios (Random Forest).
- Máquinas de Vectores de Soporte (SVM).
- K-Vecinos más cercanos (KNN).
- Redes Neuronales Artificiales.
- Naive Bayes.

**5. Casos de uso reales**
- Filtros de spam en el correo electrónico.
- Predicción de precios de bienes raíces basándose en sus características (metros cuadrados, ubicación).
- Diagnóstico médico asistido (detectar tumores benignos o malignos a partir de historiales clínicos).

**6. Retos del aprendizaje supervisado**
- **Sobreajuste (Overfitting):** El modelo "memoriza" los datos de entrenamiento en lugar de aprender los patrones generales, fallando al ver datos nuevos.
- **Costo de preparación:** Requiere volúmenes masivos de datos perfectamente limpios y preparados.
- **Sesgo:** Si los datos históricos tienen prejuicios humanos, el algoritmo los replicará con precisión matemática.

**7. ¿Qué se entiende por datos etiquetados?** Son conjuntos de datos (texto, imágenes, audio o números) a los que se les ha asignado una o más "etiquetas" informativas que indican el resultado objetivo o la clase a la que pertenecen. Es decir, es la materia prima que contiene la "verdad absoluta" (Ground Truth) para que el algoritmo aprenda.

**8. Tipos de datos etiquetados**
- **Etiquetas categóricas/discretas:** Clases cerradas (ej. "Positivo", "Negativo", "Neutral" en un análisis de sentimientos).
- **Etiquetas continuas:** Valores numéricos exactos (ej. etiquetar una casa con el valor "$1,500,000").
- **Anotaciones espaciales:** Cajas delimitadoras (Bounding boxes) o máscaras de segmentación en imágenes para visión artificial (ej. encerrar en un cuadro dónde está el semáforo).

**9. Métodos para el etiquetado de datos**
- **Etiquetado manual interno:** Expertos de dominio (ej. médicos etiquetando radiografías) revisan los datos uno a uno.
- **Crowdsourcing:** Subcontratar la tarea a plataformas masivas (como Amazon Mechanical Turk) para etiquetado simple.
- **Semi-supervisado / Activo:** Un modelo básico etiqueta los datos más fáciles y un humano interviene solo en los casos donde el modelo tiene baja confianza
- **Etiquetado programático:** Usar scripts o reglas heurísticas simples para pre-etiquetar datos masivos automáticamente.

**10. Propósito de realizar dicho etiquetado** Proporcionar al algoritmo el objetivo matemático a alcanzar. Sin las etiquetas, el modelo no tendría forma de calcular su función de pérdida (la diferencia entre lo que predijo y lo que debió predecir) y, por ende, no podría ajustar sus pesos internos para "aprender".

**11. ¿Cómo funciona o se lleva a cabo el etiquetado?**
1. **Recopilación:** Se juntan los datos crudos (ej. 10,000 fotos de calles).
2. **Definición de reglas:** Se crea un manual estricto sobre cómo etiquetar (ej. "Solo etiquetar autos en movimiento, no estacionados").
3. **Anotación:** Humanos o software aplican las etiquetas mediante herramientas de interfaz gráfica.
4. **Control de Calidad (QA):** Un revisor verifica que las etiquetas sean consistentes para no introducir "ruido" al modelo.

**12. Ventajas del uso de datos etiquetados**
- Permiten entrenar modelos con altísima precisión para tareas específicas.
- Hacen que la validación del modelo sea transparente y matemáticamente demostrable mediante métricas exactas (Accuracy, F1-Score, Recall).

**13. Limitaciones**
- **Costo y tiempo:** Es el cuello de botella más grande en la IA. Etiquetar un millón de imágenes cuesta mucho dinero y horas de trabajo humano.
- **Errores humanos:** Si los anotadores se equivocan o no se ponen de acuerdo (subjetividad), el modelo aprenderá información contradictoria.

**14. Casos de uso de datos etiquetados**
- Entrenar el algoritmo de reconocimiento facial de tu celular (cientos de miles de fotos etiquetadas como "Tú" y "No tú").
- Sistemas de vehículos autónomos (millones de horas de video con peatones y señales de alto etiquetadas frame por frame).

---
- Bobadilla, J. (2020). _Machine Learning y Deep Learning: Usando Python, Scikit y Keras_ (1.ª ed.). RA-MA Editorial.
- Soria Olivas, E., Sánchez-Montañés Isla, M. A., & Gamero Cruz, R. (2023). _Sistemas de Aprendizaje Automático_ (1.ª ed.). RA-MA Editorial.
- Velasco Rebolledo, J. (2024). _Machine Learning: fundamentos, algoritmos y aplicaciones para los negocios, industria y finanzas_ (1.ª ed.). Ediciones Díaz de Santos.