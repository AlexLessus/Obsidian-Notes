#PLN 
#### **1. Modelos de Secuencia a Secuencia (Seq2Seq / Encoder-Decoder)**

Los modelos de secuencia a secuencia están diseñados para tareas donde una secuencia de entrada se mapea a una secuencia de salida, siendo ambas de longitudes variables y sin un alineamiento directo palabra por palabra.
- **Arquitectura Clásica Basada en RNNs:** Tradicionalmente, se componían de dos redes recurrentes (como LSTMs):
    - **El Codificador (Encoder):** Procesa secuencialmente los tokens de entrada $x_{1:n}$ para comprimir su información en un vector de representación continua, habitualmente el último estado oculto de la red recurrentes ($h_n$), conocido como el **vector de contexto (**$c$**).
    - **El Decodificador (Decoder):** Toma el vector de contexto $c$ como su estado inicial ($h^d_0$) y genera de forma secuencial y autorregresiva los tokens de salida $y_{1:m}$ hasta emitir un token especial de fin de secuencia (`</s>` o `<EOS>`).
- **El Cuello de Botella de Información:** La mayor debilidad de este enfoque clásico es que toda la semántica de la secuencia de entrada debe comprimirse en un único vector de tamaño fijo. Para textos largos, el codificador es incapaz de retener la información inicial, lo que degrada drásticamente la calidad en el decodificador.
- **Mecanismos de Atención:** Introducido por Bahdanau et al. (2015), el mecanismo de atención resuelve el cuello de botella al permitir que el decodificador acceda a **todos** los estados ocultos intermedios del codificador ($h^e_{1:n}$) en lugar de limitarse al último. En cada paso de generación $i$, el decodificador calcula un puntaje de relevancia (mediante funciones como el producto punto o formas bilineales parametrizadas $W_s$) entre su estado oculto anterior ($h^d_{i-1}$) y cada estado del codificador ($h^e_j$). Estos puntajes se normalizan mediante una función **softmax** para obtener los pesos de atención ($\alpha_{ij}$), los cuales se usan para calcular un vector de contexto dinámico ($c_i$) como el promedio ponderado de los estados del codificador. Todo este proceso es completamente diferenciable, lo que permite que el modelo aprenda a "prestar atención" mediante entrenamiento de extremo a extremo (_end-to-end_).

#### **2. Arquitectura de los Transformadores (Transformers)**
Propuesto por Vaswani et al. (2017) en el célebre artículo _"Attention Is All You Need"_, el Transformer eliminó por completo la recurrencia secuencial, sustituyéndola enteramente por **mecanismos de autoatención (self-attention)** y redes lineales hacia adelante (_feed-forward_).

- **Procesamiento en Paralelo y Eficiencia:** A diferencia de las RNNs que procesan token por token de manera secuencial, el Transformer procesa **todos los tokens en paralelo** a través de sus bloques. Esto desbloqueó una enorme eficiencia computacional, permitiendo el entrenamiento en corpus exponencialmente más grandes al aprovechar el paralelismo del hardware.
- **Autoatención Bidireccional frente a Causal:**
    - **Autoatención Bidireccional (Encoder):** Permite que un token atienda a todos los demás tokens de la secuencia, tanto a su izquierda como a su derecha, generando representaciones profundamente contextualizadas.
    - **Autoatención Causal (Decoder):** Para tareas de generación, se debe evitar que el modelo "mire el futuro". Esto se logra mediante una **máscara causal** que establece los puntajes de atención de los tokens futuros en $-\infty$, de modo que la función softmax los reduzca a cero, limitando la atención exclusivamente a los tokens pasados y al actual.
- **Inyección de Posición:** Debido a que la operación de atención es equivariante ante permutaciones (no tiene noción inherente del orden secuencial), se deben sumar **embeddings posicionales** (ya sean sinusoidales absolutos o rotatorios relativos) a los embeddings de palabras antes de alimentar los bloques del Transformer.
- **Bloques del Transformer:** Cada capa o bloque consta de una subcapa de autoatención multi-cabezal (que proyecta linealmente las consultas $Q$, claves $K$ y valores $V$ en múltiples subespacios), una red **Feed-Forward de posición específica** (FFN, donde ocurre gran parte de la memorización del modelo), conexiones residuales (_skip connections_) y pasos de normalización de capa (_Layer Normalization_).

#### **3. Modelos Autorregresivos**
Son arquitecturas de tipo **solo decodificador (decoder-only)**, representadas predominantemente por la familia GPT (_Generative Pretrained Transformer_).

- **Objetivo de Entrenamiento (Causal Language Modeling):** Se entrenan de manera autosupervisada para estimar la probabilidad conjunta de una secuencia de tokens factorizándola mediante la regla de la cadena como un producto de probabilidades condicionales3132: $$P(y_1, y_2, \dots, y_t | \mathbf{x}) = \prod_{t=1}^{N} P(y_t | y_{<t}, \mathbf{x})$$ Es decir, el modelo predice el siguiente token condicionado estrictamente por la historia de tokens generados con anterioridad.
- **Estrategias de Decodificación (Decoding):** En tiempo de inferencia, el decodificador genera texto de forma iterativa y autoregresiva utilizando la distribución de probabilidad generada por la capa softmax de salida (Language Modeling Head). Entre los métodos de búsqueda y muestreo destacan:
    - _Búsqueda Codiciosa (Greedy Search):_ Selecciona en cada paso el token con mayor probabilidad (el _argmax_).
    - _Búsqueda de Haz (Beam Search):_ Mantiene un conjunto limitado de hipótesis más probables (haces) en paralelo, lo que resulta sumamente efectivo para traducción automática.
    - _Muestreo por Nucleo (Nucleus / Top-p Sampling) o Temperatura:_ Añade variabilidad y previene la degeneración repetitiva del texto al muestrear de un subconjunto dinámico de la distribución.
#### **4. Modelos Fundacionales (_Foundation Models_)**
Son modelos preentrenados a escala masiva que sirven como punto de partida común para ser adaptados a una gran variedad de tareas derivadas (_downstream_).

- **El Paradigma de Aprendizaje por Transferencia (_Transfer Learning_):** Consta de dos fases:
    1. **Preentrenamiento (Autosupervisado):** El modelo aprende propiedades generales del lenguaje a partir de corpus masivos sin etiquetar de internet. Por ejemplo, BERT se entrena mediante **Modelado de Lenguaje Enmascarado (MLM)** (adivinar palabras ocultas en medio del texto), mientras que GPT lo hace con **Modelado de Lenguaje Causal**.
    2. **Ajuste Fino (_Fine-Tuning_):** Se añade una capa de clasificación ligera sobre las representaciones contextuales del modelo preentrenado y se entrena con un conjunto de datos etiquetados mucho menor y específico de la tarea (como clasificación de sentimientos o NER).
- **Leyes de Escalamiento (_Scaling Laws_):** Investigaciones fundamentales (como Kaplan et al., 2020) demostraron que las capacidades de generalización y desempeño de estos modelos siguen una ley de potencias en relación directa con tres factores: el número de parámetros del modelo, el tamaño del dataset de entrenamiento y el presupuesto total de cómputo empleado.

