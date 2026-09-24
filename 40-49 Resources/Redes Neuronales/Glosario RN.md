Alexis De Jesus Perez Carmona
### 1. Elementos Básicos de la Neurona Artificial
- **Neurona Artificial (Nodo)**: Unidad computacional fundamental inspirada en las neuronas biológicas. Recibe señales numéricas, las procesa mediante transformaciones matemáticas y genera una respuesta o estado de activación hacia otras unidades.
- **Entradas(**$x_i$**)**: Valores o datos numéricos (binarios o continuos) introducidos en la neurona. Provienen del entorno externo o de las salidas de neuronas en capas anteriores.
- **Pesos Sinápticos (**$w_{ij}$**)**: Parámetros numéricos entrenables que miden la fuerza o intensidad de conexión entre una neurona presináptica y una postsináptica. Actúan como excitadores (si son positivos), inhibidores (si son negativos) o nulos (si valen cero) y representan la "memoria" almacenada por la red.
- **Sesgo (_Bias_ / \(b\))**: Término escalar independiente que se suma a la combinación ponderada de las entradas. Permite desplazar la función de activación a lo largo del eje para ajustar mejor el espacio de hipótesis.
- **Regla de Propagación (Suma Ponderada)**: Operación matemática que calcula el potencial de activación resultante de la neurona multiplicando cada entrada por su peso correspondiente y sumando el término de sesgo ($\sum w_i x_i + b$).
- **Función de Activación**: Operación matemática **no lineal** aplicada sobre el potencial resultante de la regla de propagación. Proporciona el estado de activación actual de la neurona y es esencial para permitir que la red aprenda relaciones geométricas y patrones complejos.

---

### 2. Estructura y Arquitectura de la Red
- **Capa de Entrada (_Input Layer_)**: Primera capa de la arquitectura encargada de recibir los datos brutos del problema sin realizar transformaciones pesadas sobre ellos.
- **Capas Ocultas (_Hidden Layers_)**: Capas intermedias ubicadas entre la entrada y la salida. Es donde se realiza la extracción jerárquica de características; las capas iniciales detectan patrones simples y las más profundas representan conceptos de alto nivel.
- **Capa de Salida (_Output Layer_)**: Capa final de la red encargada de entregar la predicción o resultado final del sistema (por ejemplo, probabilidades en un problema de clasificación o un valor escalar en regresión).
- **Capa Densa (_Fully Connected / Dense_)**: Tipo de capa en la que cada una de sus neuronas establece una conexión directa con todas y cada una de las neuronas de la capa anterior.
- **Profundidad (_Depth_)**: Número total de capas con parámetros entrenables que componen la red. Se considera "profundo" un modelo cuando cuenta con múltiples capas ocultas.

---

### 3. Proceso de Entrenamiento y Optimización
- **Paso Hacia Adelante (_Forward Pass_)**: Recorrido secuencial de los datos a través de la red, desde la capa de entrada pasando por las capas ocultas hasta calcular el resultado en la capa de salida.
- **Función de Pérdida / Costo (_Loss / Cost Function_)**: Ecuación matemática que evalúa el error o nivel de discrepancia entre la predicción generada por la red y el valor real esperado (_ground truth_).
- **Retropropagación (_Backpropagation_)**: Algoritmo fundamental que aplica la regla de la cadena del cálculo para viajar en sentido inverso (desde la salida hacia la entrada) y evaluar el gradiente del error respecto a cada peso y sesgo.
- **Gradiente (\(\nabla L\))**: Vector de derivadas parciales que indica la dirección y la magnitud exacta en que deben ajustarse los parámetros del modelo para minimizar el error de la función de pérdida.
- **Optimizador (_Optimizer_)**: Algoritmo numérico (como _SGD_, _Adam_ o _RMSprop_) que utiliza la información de los gradientes para actualizar iterativamente los pesos y sesgos de la red.
- **Tasa de Aprendizaje (_Learning Rate_)**: Hiperparámetro que define el tamaño del paso o la magnitud con la que el optimizador modifica los pesos en cada iteración de entrenamiento.
- **Época (_Epoch_) y Lote (_Batch_)**: Una **época** representa una pasada completa de todo el conjunto de entrenamiento a través del modelo. Un **lote (_mini-batch_)** es el subconjunto discreto de datos procesado en un paso individual de actualización.

---

### 4. Fenómenos de Aprendizaje y Evaluación
- **Sobreajuste (_Overfitting_)**: Condición no deseada en la que el modelo memoriza excesivamente el ruido o los detalles específicos del conjunto de entrenamiento, perdiendo la capacidad de generalizar a datos nuevos.
- **Subajuste (_Underfitting_)**: Situación en la cual la red no logra aprender ni siquiera la estructura básica de los datos de entrenamiento debido a falta de capacidad o entrenamiento insuficiente.
- **Regularización (ej. _Dropout_, _L2_)**: Conjunto de técnicas aplicadas durante el entrenamiento para restringir la complejidad de la red, previniendo el sobreajuste y mejorando la generalización.
- **Métricas de Evaluación**: Índices cuantitativos no necesariamente diferenciables (como _Accuracy_, _Precision_, _Recall_ y _F1-Score_) utilizados para medir el desempeño real del modelo.

---

### 5. Arquitecturas de Redes Neuronales
- **Redes Feedforward (FNN / MLP)**: Arquitecturas estáticas donde la información fluye en una sola dirección hacia adelante, sin bucles de realimentación.
- **Redes Convolucionales (CNN)**: Especializadas en el procesamiento de datos tipo cuadrícula (como imágenes) mediante operaciones de convolución para extraer características espaciales locales.
- **Redes Recurrentes (RNN / LSTM / GRU)**: Diseñadas para datos secuenciales o series temporales; utilizan bucles internos de realimentación para mantener un estado de memoria del contexto previo.
- **Transformers**: Arquitecturas modernas basadas en mecanismos de atención que capturan dependencias a largo plazo y procesan secuencias en paralelo, siendo el pilar de los modelos de lenguaje actual.
- **Autocodificadores (_Autoencoders_)**: Redes compuestas por un codificador y un decodificador entrenadas para comprimir los datos en una representación latente de menor dimensión y reconstruirlos posteriormente.
