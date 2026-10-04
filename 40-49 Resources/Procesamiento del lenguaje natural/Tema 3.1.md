**Las computadoras no procesan letras ni palabras, sino números y arreglos matriciales**.

La representación del texto es el puente que transforma secuencias de caracteres en vectores numéricos legibles por algoritmos de aprendizaje automático e inteligencia artificial.

A continuación, se detallan los **Modelos Básicos de Representación (Tema 3.1)**:

---

### **1. N-gramas**
Orden local


- **¿Qué son?:** Un **N-grama** es una secuencia continua de \(n\) palabras o tokens extraídos de un texto.
    - \(1\)-grama (**unigrama**): palabras individuales (ej. _"curso"_). Poco contexto, vocabulario simple
    - \(2\)-grama (**bigrama**): secuencias de dos palabras (ej. _"curso excelente"_). Expresiones frecuentes, mas dimensiones
    - \(3\)-grama (**trigrama**): secuencias de tres palabras (ej. _"el curso excelente"_). contexto mas especifico, mayor dispersión, requiere mas datos.
- **Como Modelo de Lenguaje:** Se utilizan para calcular la probabilidad de que una palabra aparezca dada una secuencia previa de palabras (\(P(w|h)\)). Se entrenan contando frecuencias en un corpus y calculando la Estimación de Máxima Verosimilitud (MLE).
- **Limitación:** Asumen una memoria local muy corta. Su número de parámetros crece de forma exponencial al aumentar el orden de \(n\), y sufren de escasez de datos (_sparsity_) ante palabras o combinaciones no vistas en el texto de entrenamiento.

Evaluan contexto

---
### **2. Cadenas de Markov (Markov Chains)**
Predecir deesde el estado anterior

La propiedad de Markov aproxima el futuro usando un historial limitado.

- **¿Qué son?:** Un modelo estocástico o probabilístico en el que la probabilidad de transición al siguiente estado (la siguiente palabra) depende **únicamente del estado actual o de un número finito de estados anteriores** (propiedad de Markov).
- **Relación con los N-gramas:** Los modelos de N-gramas son esencialmente **cadenas de Markov de orden \(N-1\)**. En lugar de considerar todo el historial del texto, la cadena de Markov simplifica el cálculo asumiendo que la siguiente palabra solo depende de las \(n-1\) palabras inmediatamente anteriores.

---

### **3. Vectores de Palabras Básicos (Bolsa de Palabras y Matrices)**

Antes de los _embeddings_ densos de aprendizaje profundo, el texto se representaba numéricamente mediante dos enfoques vectoriales básicos:

- **Vectores One-Hot:** Representación donde cada palabra es un vector del tamaño del vocabulario (\(|V|\)) que contiene un \(1\) en la posición correspondiente al índice de la palabra y \(0\) en todas las demás.
    - _Desventaja:_ Crea vectores gigantescos, diseminados e incapaces de medir la similitud semántica entre palabras.
- **Matriz Término-Documento (Term-Document Matrix):** Matriz donde las filas corresponden a palabras y las columnas a documentos. Cada celda registra la frecuencia con la que aparece una palabra en un documento determinado.
- **Matriz Término-Término (Word-Word Matrix / Co-occurrence):** Matriz de dimensión \(|V| \times |V|\) donde las celdas representan cuántas veces dos palabras coocurren dentro de una ventana de contexto de tamaño fijo.

---

### **4. TF-IDF (Term Frequency - Inverse Document Frequency)**
Sube el peso de terminos utiles en un documento y reduce

Las frecuencias puras de palabras en un documento no son la mejor medida de asociación semántica, ya que palabras muy comunes (_"el"_, _"de"_, _"bueno"_) aparecen masivamente en todos lados sin discriminar el tema real del texto.

El modelo **TF-IDF** resuelve esto multiplicando dos términos:

1. **Term Frequency (\(TF_{t,d}\)):** Mide la frecuencia local de la palabra \(t\) en el documento \(d\). Para evitar que una palabra que aparece 100 veces pese 100 veces más, se suele suavizar con una escala logarítmica: \(1 + \log_{10}(\text{count})\).
2. **Inverse Document Frequency (\(IDF_t\)):** Mide qué tan rara e informativa es la palabra en **todo el corpus**: \[IDF_t = \log_{10}\left(\frac{N}{df_t}\right)\] Donde \(N\) es el número total de documentos y \(df_t\) es en cuántos documentos aparece la palabra \(t\). Si una palabra aparece en todos los documentos (como _"de"_), su \(IDF\) se vuelve \(0\), anulando su impacto.
3. **Ponderación TF-IDF:** \(W_{t,d} = TF_{t,d} \times IDF_t\).

- **Uso:** Es el modelo vectorial clásico por excelencia (_baseline_) en Recuperación de Información (IR) y clasificación de texto tradicional mediante bibliotecas como `scikit-learn` o `Gensim`. La similitud entre documentos o consultas se calcula evaluando el **coseno del ángulo** entre sus vectores TF-IDF.

