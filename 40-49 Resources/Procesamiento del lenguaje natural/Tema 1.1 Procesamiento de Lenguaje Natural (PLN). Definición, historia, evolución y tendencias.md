#PLN 

## Definición 
**PLN es el estudio y desarrollo de técnicas computacionales orientadas al procesamiento, análisis y generación automática del lenguaje humano**

Combina aspectos teóricos y prácticos de la **lingüística computacional**, el **aprendizaje automático (machine learning**) y la **inteligencia artificial** mediante el uso de modelos matemáticos y algoritmos de **aprendizaje profundo (**deep learning)**

---
El **Procesamiento del Lenguaje Natural (PLN)** —o NLP por sus siglas en inglés— es una rama de la inteligencia artificial enfocada en el estudio y desarrollo de técnicas computacionales que permiten la comprensión, el análisis y la generación automática del lenguaje humano. 
**Su propósito central** es cerrar la brecha entre la comunicación humana y el procesamiento digital, integrando aspectos teóricos de la lingüística computacional con el desarrollo práctico de modelos matemáticos, algoritmos de aprendizaje automático (machine learning) y aprendizaje profundo (deep learning).

De manera general, las tareas del PLN se dividen en dos campos principales:

1. **Comprensión del Lenguaje Natural (NLU):** Se refiere a las tareas donde el texto es la entrada y el sistema realiza algún tipo de análisis o clasificación. Un ejemplo común es el **Reconocimiento de Entidades Nombradas (NER)**, que consiste en detectar y extraer nombres de personas, lugares, organizaciones u otras categorías dentro de un texto.
2. **Generación del Lenguaje Natural (NLG):** Abarca aquellas tareas donde tanto la entrada como la salida consisten en texto. El ejemplo por excelencia es la **generación automática de resúmenes**, en la que un modelo procesa un texto largo para producir una síntesis fluida.

## **Historia y Evolución del PLN**
El desarrollo histórico de esta disciplina se ha consolidado en cuatro grandes fases reflejadas en la literatura:

- **La Era de Reglas y la Gramática Formal (Años 1940s - 1970s):**
    - La disciplina nació poco después del surgimiento de la computadora. En **1949**, Warren Weaver propuso formalmente los primeros enfoques de **Traducción Automática (MT)**.
    - En la década de **1950**, Stephen Kleene definió las primeras expresiones regulares y autómatas finitos, basándose en la neurona formal de McCulloch y Pitts de **1943**.
    - En **1966**, Joseph Weizenbaum diseñó **ELIZA**, uno de los primeros sistemas de diálogo basados en la coincidencia de patrones simples (_pattern-matching_).
    - Surgieron los primeros sistemas de respuesta a preguntas basados en bases de datos lógicas estructuradas, como **LUNAR (1972)**, para responder preguntas sobre la geología lunar.
- **La Era Estadística y Probabilística (Años 1980s - 2000s):**
    - Las limitaciones del diseño de reglas manuales llevaron a un cambio paradigmático hacia el modelado probabilístico de secuencias. Fred Jelinek y su equipo en **IBM Watson** acuñaron formalmente el término **"modelo de lenguaje" (Language Model)** en **1975** al aplicar modelos de **n-gramas** para calcular las probabilidades de secuencias de palabras en reconocimiento de voz.
    - En **1988**, Deerwester introdujo el **Análisis Semántico Latente (LSA)**, sentando las bases primitivas de los vectores de palabras o _embeddings_ al usar la descomposición de valores singulares para representar el significado semántico.
    - A finales de los 90, se aplicaron ampliamente clasificadores discriminativos como la **Regresión Logística** (conocida entonces como modelos de _máxima entropía_ o _MaxEnt_) para etiquetado gramatical (POS), análisis sintáctico y clasificación de texto.
- **La Era del Aprendizaje Profundo y Modelos de Secuencia (Años 2010s):**
    - A finales de la década de 2000, los trabajos de Collobert y Weston (2008, 2011) impulsaron el uso de redes neuronales profundas para realizar tareas de PLN **"desde cero" (****almost from scratch****)**, prescindiendo de características lingüísticas diseñadas a mano.
    - A partir de **2013**, la popularización de vectores densos preentrenados como **word2vec (Mikolov)** y **GloVe (Pennington)** revolucionó el campo al representar palabras en espacios vectoriales continuos donde la cercanía geométrica reflejaba similitud semántica.
    - Estos vectores se combinaron con redes neuronales recurrentes (**RNNs**) y de memoria a largo y corto plazo (**LSTMs**) para procesar secuencias de texto. Poco después, se introdujeron los marcos de trabajo de codificador-decodificador (_encoder-decoder_) con mecanismos de atención blanda para mejorar la traducción automática (Bahdanau et al., 2015).
- **La Era de los Transformers (2017 - Presente):**
    - En **2017**, investigadores de Google propusieron la arquitectura del **Transformer** en el famoso artículo _Attention Is All You Need_. Esta arquitectura eliminó por completo la recurrencia secuencial, sustituyéndola por la **autoatención** (_self-attention_), lo que posibilitó paralelizar el entrenamiento a gran escala y mejorar drásticamente la eficiencia de cómputo.
    - Esto catalizó el nacimiento del **aprendizaje por transferencia (Transfer Learning)** en PLN (ULMFiT en 2018), seguido rápidamente por el lanzamiento de **GPT** (OpenAI) y **BERT** (Google), modelos preentrenados de forma autosupervisada en corpus gigantescos de texto para luego ser ajustados con pocos datos a tareas específicas.


## **Tendencias Actuales en PLN**
1. **Leyes de Escalamiento (Scaling Laws):** Las investigaciones demuestran que incrementar masivamente la cantidad de datos y el tamaño de los parámetros de los modelos (como se vio de GPT-2 a GPT-3) mejora drásticamente sus capacidades de generalización.
2. **Modelos de Fundación y Multimodalidad:** El uso de tecnologías de Transformers se ha expandido del procesamiento de texto hacia otras disciplinas como la generación de imágenes, el audio, la visión computacional y la genética.
3. **Alineación e Instrucción (RLHF):** El uso del Aprendizaje por Refuerzo a partir de la Retroalimentación Humana (RLHF) permite alinear los modelos de lenguaje (como se hizo en InstructGPT o ChatGPT) para que sigan instrucciones directas de forma útil y segura.
4. **Democratización y Código Abierto:** El ecosistema de código abierto liderado por **Hugging Face** (biblioteca Transformers) y otras herramientas como **SpaCy** y **NLTK** facilita que estudiantes e industrias utilicen e implementen modelos de última generación de manera ágil y sencilla.