### 1.2.1. Teoría Lingüística Básica: fonología, morfología, sintaxis, semántica, pragmática, diferencias entre lenguaje escrito y hablado. 
Para que un sistema computacional procese el lenguaje natural, debe ser capaz de modelar los diferentes niveles de organización o "capas" de la lingüística:

- **Fonología:** Estudia los sonidos de la lengua (fonemas) y sus patrones sistemáticos. En PLN, este nivel es la base para el desarrollo de tecnologías de **Reconocimiento de Voz** (convertir señales acústicas en texto) y de **Síntesis de Voz o TTS** (_Text-to-Speech_).
- **Morfología:** Analiza la estructura interna de las palabras y cómo se construyen a partir de unidades mínimas de significado (morfemas). Es fundamental para tareas de normalización y tokenización.
- **Sintaxis:** Estudia cómo se agrupan, ordenan y combinan las palabras para formar frases y oraciones con sentido y gramaticalmente válidas. Determina las jerarquías estructurales de una oración.
- **Semántica:** Se enfoca en el significado de las palabras individuales (semántica léxica) y en cómo sus combinaciones forman el significado de enunciados completos. En el PLN actual, esto se modela mediante representaciones vectoriales densas (_word embeddings_) que capturan similitud semántica en espacios geométricos.
- **Pragmática:** Analiza cómo el contexto externo y la intención del emisor influyen en la interpretación de los mensajes. Se asocia directamente con los **actos de habla** en sistemas conversacionales (ej. determinar si el usuario hace una pregunta o emite una orden) y con la **resolución de correferencias** (saber a qué elemento del mundo real se refieren pronombres como _él_ o _ella_).
- **Diferencias entre lenguaje escrito y hablado:**
    - El **lenguaje hablado** suele ser espontáneo, menos estructurado y está plagado de **disfluencias** (como fragmentos de palabras, repeticiones o muletillas del tipo _"eh"_ o _"um"_). Además, depende críticamente del diálogo interactivo y del tono de voz (prosodia).
    - El **lenguaje escrito** posee una estructura formal rígida y cuenta con elementos explícitos como signos de puntuación y uso de mayúsculas/minúsculas. Sin embargo, carece del contexto físico inmediato de la comunicación oral.

### 1.2.2. Partes del Lenguaje: Lexemas y Morfemas, clasificación, análisis de estructuras morfológicas. 
La morfología nos enseña cómo se configuran las palabras y de qué manera podemos procesarlas para simplificar el vocabulario que analiza un modelo.
- **Unidades clave:**
    - **Morfema:** Es la unidad mínima indivisible con significado en una lengua. Por ejemplo, en _"gatos"_, conviven dos morfemas: la raíz _"gat-"_ (significado de felino) y el sufijo _"-s"_ (significado de pluralidad).
    - **Lexema (o Lemma):** Es la forma base o de diccionario de una palabra (forma de citación). Por ejemplo, el lexema de _"dormir"_ unifica formas verbales flexionadas como _"duermes"_, _"durmió"_ o _"dormiremos"_.
    - **Forma de palabra (Wordform):** Es la palabra tal y como aparece escrita de forma concreta en el texto (ej. _"gatos"_, _"duermes"_).
- **Clasificación de Morfemas:**
    - **Raíz (Stem):** El morfema principal que aporta la carga del significado central de la palabra.
    - **Afijos (Affixes):** Morfemas secundarios que se unen a la raíz para añadir significados gramaticales o de derivación. Se clasifican según su posición: _prefijos_ (antes de la raíz), _sufijos_ (después) o _infijos_.
- **Análisis Morfológico en PLN:**
    - **Lematización (Lemmatization):** Proceso que utiliza diccionarios y reglas lingüísticas para identificar de manera precisa el lexema correcto de una palabra según su contexto. Es vital para idiomas morfológicamente complejos como el español.
    - **Stemming (Truncamiento):** Una alternativa mucho más rápida y heurística que simplemente recorta los afijos de las palabras para quedarse con una raíz aproximada (por ejemplo, mediante el algoritmo de Porter). Aunque es ágil, es menos preciso y puede cometer errores al agrupar palabras con significados distintos.
### 1.2.3. Sintaxis y Gramática. Estructura gramatical, árboles de derivación, reglas de producción en gramáticas formales.
En este nivel, se estudia cómo organizar y descomponer las oraciones para que la computadora entienda sus relaciones internas.
- **Estructura Gramatical y Clases de Palabras (POS):**
    - Las palabras se catalogan en **Partes de la Oración (Parts of Speech - POS)**. Se clasifican en **clases abiertas** (sustantivos, verbos, adjetivos y adverbios, que cambian y crecen constantemente) y **clases cerradas** (preposiciones, artículos, conjunciones y pronombres, que son fijos).
    - La sintaxis demuestra que las palabras no forman listas planas, sino que se agrupan en bloques jerárquicos llamados **constituyentes** (_constituents_). Por ejemplo, en _"el vuelo"_ se forma un Sintagma Nominal (NP).
- **Gramáticas Formales e Independientes del Contexto (CFG):**
	- La **Gramática Independiente del Contexto (CFG)** es el marco matemático estándar usado en lingüística computacional para modelar la sintaxis del lenguaje natural.
	- Se define formalmente por una 4-tupla $(N, \Sigma, R, S)$:
	    1. $N$: Símbolos **no terminales** (categorías abstractas como $S$ para oraciones, $NP$ para frases nominales, o $VP$ para frases verbales).
	    2. $\Sigma$: Símbolos **terminales** (las palabras reales de la lengua).
	    3. $R$: Conjunto de **reglas de producción** (de la forma $A \rightarrow \beta$, donde un no terminal se reescribe como otros símbolos, ej. $S \rightarrow NP \ VP$).
	    4. $S$: El **símbolo inicial**, que representa la oración completa.
- **Árboles de Derivación (Parse Trees):**
    - Son diagramas jerárquicos que muestran visualmente la estructura de una oración de acuerdo con las reglas de producción de la gramática. Ilustran cómo el nodo inicial $S$ domina de manera descendente a los constituyentes y a las palabras terminales.

- **Ambigüedad Sintáctica:**
    - Es uno de los grandes retos de la programación en PLN. Una misma secuencia de palabras puede producir múltiples árboles de derivación válidos. Un ejemplo clásico es la ambigüedad de adjunción de frases preposicionales (como en _"Disparé a un elefante en mis pijamas"_, donde no queda claro por pura estructura si el elefante vestía el pijama o el tirador lo hacía). Para resolver esto en la práctica, se utilizan parsers probabilísticos y algoritmos de programación dinámica como el **CKY**.