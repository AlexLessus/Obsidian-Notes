#MachineLearning [[Aprendizaje Automático]]
Una matriz de confusión, también conocida como matriz del error, es una herramienta visual en forma de cuadrícula que se utiliza para evaluar el desempeño de un modelo de clasificación en el aprendizaje automático supervisado

Su **objetivo principal es resumir y describir** la distribución de las predicciones hechas por el modelo frente a los valores reales, mostrando claramente la cantidad de aciertos y errores cometidos por el algoritmo

En el contexto de un clasificador binario (que clasifica los datos en dos categorías, por ejemplo, 0 y 1, o "enfermo" y "sano"), la matriz se divide en cuatro cuadrantes fundamentales:

- **Verdadero Positivo (VP):** Casos en los que el modelo predijo correctamente la salida como positiva.
- **Verdadero Negativo (VN):** Casos en los que el modelo predijo correctamente la salida como negativa.
- **Falso Positivo (FP) o Error de Tipo I:** Casos en los que el modelo se equivocó al predecir la salida como positiva cuando el valor real era negativo.
- **Falso Negativo (FN) o Error de Tipo II:** Casos en los que el modelo se equivocó al predecir la salida como negativa cuando el valor real era positivo.

Para considerar que un clasificador funciona adecuadamente, los valores ubicados en la diagonal que conforman los aciertos (Verdaderos Positivos y Verdaderos Negativos) deben ser altos. Además, los resultados presentados en esta matriz sirven como base fundamental para calcular otras métricas importantes de evaluación, tales como la exactitud, la precisión, la sensibilidad y la especificidad del modelo.
