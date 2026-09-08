**1. Reconocimiento Automático de Voz (ASR - Automatic Speech Recognition)**

Consiste en mapear una señal acústica continua a una secuencia discreta de texto (grafemas o subpalabras).

- **Procesamiento de Características:** Las ondas sonoras se muestrean, cuantizan y transforman mediante análisis espectral en representaciones visuales de energía en función del tiempo, típicamente **espectrogramas log-Mel** calculados en ventanas de unos 10 ms.
- **Arquitecturas Principales:**
    - **Codificador-Decodificador con Atención (AED):** También conocido en aplicaciones de voz como _Listen, Attend and Spell (LAS)_. Debido a que la secuencia acústica es sumamente larga (cientos de frames para una palabra), requiere una etapa de **submuestreo o compresión** antes de alimentar al codificador. El decodificador genera las letras autorregresivamente asistido por capas de atención.
    - **Clasificación Temporal Conexiona (CTC):** Un enfoque basado en un modelo de codificador simple que predice directamente una etiqueta de carácter (o un token en blanco especial `[blank]`) para cada frame acústico individual de manera independiente. Posteriormente, una función de colapso elimina las repeticiones y los espacios en blanco (ej. `a-a--b-b` se convierte en `ab`). Es muy eficiente y apto para procesamiento en tiempo real (_streaming_), pero al asumir independencia condicional entre salidas, requiere acoplar externamente un modelo de lenguaje para mantener la coherencia lingüística.
- **Evaluación:** Se evalúa mediante la métrica **Tasa de Error de Palabras (WER - Word Error Rate)**, que calcula la distancia de edición (inserciones, eliminaciones y sustituciones) requerida para alinear la transcripción predicha con la de referencia.

**2. Traducción Automática (MT - Machine Translation)**
Se enfoca en traducir un enunciado de un idioma de origen a otro de destino, enfrentándose a divergencias tipográficas, léxicas y estructurales (por ejemplo, el orden de constituyentes SVO en español frente a SOV en japonés).

- **El Estándar Neuronal (NMT):** Implementa un Transformer completo de tipo **Codificador-Decodificador. El codificador procesa la frase de origen, mientras que el decodificador cuenta con una capa intermedia crítica denominada **atención cruzada (cross-attention)**. En esta capa, las consultas ($Q$) provienen del bloque del decodificador, mientras que las claves ($K$) y valores ($V$) se derivan directamente de las representaciones contextualizadas calculadas por el codificador. Esto permite al decodificador alinearse dinámicamente con cualquier segmento de la oración fuente al generar cada palabra.
- **Entrenamiento y Datos Sintéticos:** Requiere corpus paralelos alineados (_bitexts_). Cuando estos son escasos, se utiliza **retrotraducción (backtranslation)**: se entrena un modelo en sentido inverso para traducir corpus monolingües del idioma destino al origen, generando pares de entrenamiento sintéticos para robustecer el sistema final.
- **Evaluación Automática:** Además de la evaluación humana (adecuación y fluidez), se utilizan métricas computacionales basadas en el solapamiento de n-gramas de caracteres, como **chrF**, o basadas en proyecciones vectoriales profundas entrenadas para correlacionar con juicios humanos, como **COMET** o **BLEURT**.

**3. Análisis de Sentimientos**
Su propósito es extraer la orientación afectiva o polaridad (positiva, negativa o neutra) que un autor expresa hacia una entidad o tópico dentro de un texto63.

- **Enfoques Clásicos basados en Léxicos:** Utilizan diccionarios de afecto creados mediante etiquetado humano o semi-supervisado (como _EmoLex_ o _SentiWordNet_) para contabilizar palabras con carga emocional y aplicar heurísticas de polaridad mayoritaria.
- **Enfoque Neuronal Moderno (Clasificación de Secuencias):** Se utiliza un codificador bidireccional (como BERT). Durante el preprocesamiento, se antepone un token especial de clasificación (`[CLS]`) al texto. El vector de salida correspondiente a este token en la última capa ($h_{[CLS]}$) actúa como un resumen semántico de toda la secuencia gracias al libre flujo de la autoatención bidireccional. Este vector alimenta directamente a un clasificador lineal entrenado con entropía cruzada para predecir las etiquetas de sentimiento.
- **Enfoque por Prompts en LLMs:** En modelos autorregresivos modernos, la clasificación se reformula como una tarea de generación secuencial mediante el uso de plantillas de instrucciones (ej. _"Texto: [INPUT]. En resumen, la estadía fue: [PREDICCIÓN]"_), donde se evalúa la verosimilitud de que el modelo emita palabras clave como "excelente" o "mala".

**4. Resumen Automático de Texto**

Consiste en destilar un documento extenso en una versión condensada que conserve los hechos y puntos esenciales.

- **Métodos Extractivos:** Identifican y extraen directamente las oraciones más importantes del texto original sin alterar sus palabras. Algoritmos clásicos como **TextRank** modelan el documento como un grafo donde las oraciones son nodos y sus aristas representan similitud léxica, aplicando algoritmos de centralidad para seleccionar las frases clave.
- **Métodos Abstractivos:** Generan un texto completamente nuevo, fluido y coherente, lo que requiere capacidades avanzadas de comprensión y síntesis sintáctica. Se implementan mediante modelos codificador-decodificador masivos (como BART o T5). Modelos especializados como **PEGASUS** utilizan objetivos de preentrenamiento diseñados específicamente para esta tarea, como el enmascaramiento y reconstrucción de oraciones clave completas dentro de un párrafo en lugar de tokens individuales.
- **Evaluación:** Se mide mediante la suite métrica **ROUGE**, la cual evalúa el recobro y precisión de la coincidencia de n-gramas entre el resumen generado por la máquina y los resúmenes de referencia escritos por humanos.

**5. Chatbots y Sistemas de Diálogo**
Sistemas diseñados para mantener conversaciones estructuradas o informales con humanos81.

- **Estructuras del Diálogo Humano:** Se fundamentan en conceptos de pragmática como los **actos de habla / diálogo** (acciones que realizamos al hablar, ej. preguntar, prometer), la búsqueda de **terreno común (common ground)** mediante señales de entendimiento y la organización por turnos de palabra.
- **Evolución Arquitectural:**
    - _Sistemas basados en Reglas:_ Como **ELIZA** (1966), que dependía de un analizador sintáctico simple y coincidencia de patrones (_pattern matching_) para simular un terapeuta.
    - _Sistemas orientados a Tareas (Frame-based / GUS):_ Utilizan arquitecturas donde el diálogo consiste en llenar "ranuras" (_slots_) en un marco conceptual para completar una transacción (por ejemplo, agendar un vuelo especificando destino, fecha y aerolínea).
    - _Sistemas Neuronales Modernos:_ Chatbots conversacionales generales (como ChatGPT) que emplean decodificadores autorregresivos masivos entrenados en corpus de redes sociales organizados en hilos conversacionales estructurados como turnos de entrada y salida. Se refinan mediante alineación por preferencias utilizando técnicas de **Aprendizaje por Refuerzo a partir de Retroalimentación Humana (RLHF)** u optimización de preferencias directas (DPO) para asegurar que el agente sea útil, honesto y seguro.