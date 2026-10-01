Alexis De Jesus Perez Carmona
### 1. Definición de Agente Conversacional
Un **agente conversacional** es un sistema o programa de software diseñado para interactuar y mantener diálogos con usuarios humanos mediante el **procesamiento del lenguaje natural (PLN)**, respondiendo en formato de texto o voz. Su objetivo central es interpretar la intención del usuario y ofrecer respuestas coherentes y contextualizadas.

### 2. Aplicaciones de los Agentes Conversacionales
- **Atención y soporte al cliente:** Automatización de consultas, resolución de preguntas frecuentes y soporte técnico 24/7 en empresas.
- **Educación e investigación:** Tutoría personalizada, diálogos socráticos adaptativos y asistencia en la lectura o síntesis de documentos.
- **Entornos de salud:** Triaje inicial de síntomas, recordatorios de tratamiento y acompañamiento a pacientes.
- **Comercio electrónico:** Asesoramiento en ventas, recomendación de productos y gestión de pedidos.

---
### 3. Definición de un Asistente Virtual
Un **asistente virtual** es una entidad de software avanzada orientada a la **ejecución de tareas y servicios**. No solo mantiene una conversación, sino que integra herramientas externas, gestiona información del entorno del usuario (agenda, ubicación, preferencias) y ejecuta comandos de voz o texto para resolver problemas operativos.

### 4. Aplicaciones de los Asistentes Virtuales
- **Control de domótica e IoT:** Gestión de luces, persianas, electrodomésticos y dispositivos conectados en el hogar.
- **Gestión de productividad personal:** Creación de recordatorios, programación de eventos en el calendario, envío de mensajes y realización de llamadas.
- **Asistencia en el sector médico:** Transcripción de dictados clínicos en tiempo real y asistencia por voz desde la cama del paciente.
- **Navegación e información en tiempo real:** Consultas de tráfico, pronóstico del clima, reproducción de medios y búsquedas web inmediatas.

---

### 5. Definición de Chatbot
Un **chatbot** (o robot de plática) es una aplicación conversacional tradicionalmente estructurada sobre **reglas explícitas, árboles de decisión o patrones predefinidos** que provee respuestas automáticas e inmediatas a las entradas del usuario.

### 6. Aplicaciones de los Chatbots
- **Recepción automatizada de reclamos:** Gestión de quejas y canalización de tickets de servicio con reglas estructuradas.
- **Secciones de FAQ interactivas:** Respuestas rápidas a preguntas frecuentes en sitios web o aplicaciones móviles.
- **Captura inicial de datos (Leads):** Formularios conversacionales para recopilar datos de contacto de clientes potenciales.

---
### 7. Diferencia entre los Tres Agentes

|Criterio|Chatbot|Agente Conversacional|Asistente Virtual|
|:--|:--|:--|:--|
|**Complejidad**|Basado en reglas o scripts cerrados.|Basado en PLN o modelos de lenguaje (_LLM_) dinámicos.|Integración multimodal y orientada a la acción.|
|**Enfoque**|Responder consultas específicas y acotadas.|Mantener diálogos fluidos y razonar sobre contexto.|Ejecutar tareas, gestionar servicios y controlar herramientas.|
|**Ejemplo típico**|Bot de FAQ de un banco.|Asistente generativo de investigación o tutoría.|Siri, Alexa o Google Assistant.|

---
### 8. Proyectos Destacados en la Historia de la IA
- **ELIZA (1964–1966):** Creado por Joseph Weizenbaum en el MIT. Es considerado uno de los primeros programas en procesar lenguaje natural. Simulaba a un psicoterapeuta de la escuela de Carl Rogers mediante reglas de sustitución y coincidencia de patrones (_pattern matching_).
- **PARRY (1972):** Creado por Kenneth Colby en la Universidad de Stanford. Simulaba el comportamiento de un paciente con esquizofrenia paranoide y fue diseñado para someterse a variaciones del Test de Turing frente a psiquiatras evaluadores.
- **Dr. Abuse (1995):** Chatbot español desarrollado por Javier Sainz. Simulaba una personalidad irónica y sarcástica a través de heurísticas de análisis sintáctico y diccionarios de patrones.
- **Siri (2011):** Creado originalmente en 2007 dentro de SRI International e integrado comercialmente por Apple en 2011. Fue pionero en la asistencia virtual por voz masiva integrada en sistemas operativos móviles.
- **Watson (2011):** Desarrollado por IBM. Sistema de computación cognitiva que cobró fama mundial en 2011 al vencer a los campeones humanos en el concurso televisivo _Jeopardy!_, procesando lenguaje natural no estructurado y grandes bases de datos.
- **Cortana (2014):** Asistente virtual desarrollado por Microsoft para Windows y dispositivos móviles, enfocado en la gestión de tareas de productividad y búsquedas.
- **Alexa (2014):** Asistente virtual desarrollado por Amazon junto con los dispositivos Echo, especializado en control por voz de la domótica, música y comercio electrónico.

---
### 9. ¿En qué consiste el Chatbot A.L.I.C.E.?
**A.L.I.C.E. (_Artificial Linguistic Internet Computer Entity_)**, creado por Richard Wallace en **1995**, es un chatbot inspirado en el programa ELIZA. Utiliza el lenguaje **AIML** (_Artificial Intelligence Markup Language_), un formato XML especializado para codificar patrones de conversación mediante reglas de coincidencia de estímulo-respuesta. Ganó en tres ocasiones el célebre Premio Loebner de IA.

El hablar con ALICE no se sintió como hablar con un humano, al saber como  funciona sé que tipo de respuestas esperar y no se siente como un humano.

---
### 10. ChatGPT: Concepto, Funcionamiento y Características
- **Descripción y Fecha de Creación:** Sistema de IA conversacional generativa desarrollado por OpenAI y lanzado públicamente el **30 de noviembre de 2022**. Alcanzó los 100 millones de usuarios activos en apenas dos meses.
- **Funcionamiento:** Se basa en arquitecturas de **Transformador Generativo Preentrenado (GPT)** y modelos de lenguaje de gran tamaño (_LLMs_). Funciona de la siguiente manera:
    1. El _prompt_ (instrucción) ingresado se divide en **tokens**.
    2. El modelo analiza patrones estadísticos aprendidos durante su entrenamiento masivo para estimar la probabilidad de las palabras o frases siguientes.
    3. Convierte las predicciones en texto legible y lo filtra mediante **barandillas de seguridad (_guardrails_)** para evitar contenidos inapropiados.
- **Cómo entablar una conversación:** El usuario interactúa escribiendo _prompts_ (instrucciones o preguntas en lenguaje natural) en la interfaz gráfica de chat o mediante comandos de voz.
- **Servicios que ofrece:** Generación y resumen de textos, traducción multilingüe, asistencia y generación de código de programación, resolución de problemas lógicos y matemáticos, análisis de imágenes/visión artificial, y conexión con herramientas externas (_plugins_ / RAG).
- **Características de sus versiones recientes (Serie GPT-5 / GPT-5.4 en 2025–2026):**
    - **Integración de razonamiento y generación:** Unifica en una sola arquitectura la generación rápida y el razonamiento autónomo (_chain-of-thought_).
    - **Capacidades Multimodales y _Computer Use_:** Procesa texto, imágenes, audio e interactúa directamente con entornos de escritorio mediante captura de pantalla y control de periféricos.
    - **Ventana de Contexto Masiva:** Admite ventanas de contexto de hasta **1 millón de tokens**.
    - **Reducción drástica de alucinaciones:** Produce hasta un 33% menos de errores fácticos que versiones previas, ofreciendo mayor confiabilidad.

### 11. Akinator
La pasión inagotable de Akinator es intentar adivinar personajes haciendo preguntas.

Para jugar con él, piensa en un personaje, real o ficticio, y haz clic en el menú “jugar>personajes”

Entonces Akinator empezará a hacer preguntas que tendrás que responder de la forma más correcta posible. Después de unas preguntas, te dirá el personaje en el que estás pensando.

Akinator adivinó correctamente todos los personajes en los que pensé, es interesante. Parece que funciona filtrando poco a poco su base de datos de personajes según la pregunta, empieza con peguntas muy genéricas y después va haciendo preguntas mas especificas cuando quedan pocas opciones de personajes. 
Considero que no tiene inteligencia artificial, solo es un algoritmo que filtra entre sus personajes. 

### 12. AIML (Artificial Intelligence Markup Language)

#### **¿Qué es?**

**AIML** (_Artificial Intelligence Markup Language_) es un lenguaje de marcado basado en **XML** creado entre 1995 y 2001 por Richard Wallace y la comunidad de código abierto de A.L.I.C.E. (_Artificial Linguistic Internet Computer Entity_). Fue diseñado específicamente para facilitar el desarrollo, entrenamiento y estructuración de **agentes conversacionales y chatbots**.

#### **Estructura y hacia qué va encaminado**

- **Objetivo:** Está encaminado a la **coincidencia de patrones de texto** (_pattern matching_) y la reducción simbólica de lenguaje natural. Permite que un programa identifique estímulos textuales del usuario y seleccione la respuesta más adecuada según reglas predefinidas.
- **Estructura:** Sigue las reglas estándar de XML. Se compone de un documento raíz que encapsula múltiples **categorías**, donde cada categoría relaciona directamente un patrón de entrada (lo que dice el usuario) con una plantilla de salida (lo que responde el chatbot).

#### **Etiquetas principales**

- `<aiml>`: Etiqueta raíz que delimita el inicio y fin del documento XML.
- `<category>`: Unidad fundamental de conocimiento que agrupa un patrón y una respuesta.
- `<pattern>`: Especifica la cadena de texto, pregunta o patrón de palabras clave que se espera recibir del usuario.
- `<template>`: Contiene la respuesta, instrucción o texto que el chatbot generará al coincidir el patrón.
- `<srai>` (_Symbolic Reduction / Substitution_): Permite redirigir un patrón a otra categoría (útil para gestionar sinónimos o simplificar frases complejas).
- `<star>`: Captura las palabras coincidentes con comodines (`*` o `_`) presentes en el `<pattern>`.
- `<set>` / `<get>`: Permite guardar y recuperar variables en la memoria del agente durante la sesión conversacional.
- `<random>` y `<li>`: Permiten definir una lista de respuestas alternativas para elegirlas de manera aleatoria y evitar la monotonía.

### 13. AML (Avatar Intelligence Markup Language / Avatar Markup Language)

#### **¿Qué es?**

**AML** (_Avatar Intelligence Markup Language_ / _Avatar Markup Language_) es un lenguaje de marcado basado en **XML** diseñado para la **especificación, control y sincronización de personajes o avatares virtuales 2D/3D**. A diferencia de los lenguajes puramente textuales, AML integra elementos de comportamiento gráfico, gestualidad, postura y expresiones faciales.

#### **Estructura y hacia qué va encaminado**
- **Objetivo:** Está encaminado a la **animación multimodal y la representación del lenguaje corporal** en interfaces humanas virtuales. Su propósito es coordinar simultáneamente la voz del avatar (mediante sintetizadores de texto a voz - TTS) con movimientos corporales, miradas, ademanes y emociones en una línea de tiempo gráfica.
- **Estructura:** Posee una estructura jerárquica y temporal basada en XML. Define contenedores para identificar el avatar objetivo y etiquetas hijas que declaran acciones que se ejecutan de manera secuencial o paralela (habla, sincronización labial, expresiones faciales y animaciones gestuales).

#### **Etiquetas principales**

- `<aml>` / `<avatar>`: Etiqueta raíz que encapsula la definición y el escenario del avatar interactivo.
- `<speech>` / `<say>`: Define el texto o fragmento de audio que el avatar debe sintetizar o pronunciar.
- `<gesture>` / `<animation>`: Especifica la animación o ademán físico que realizará el cuerpo del avatar (por ejemplo: saludar, señalar, encogerse de hombros).
- `<emotion>` / `<facial>`: Define el estado emocional o la gesticulación del rostro del avatar (alegría, sorpresa, empatía) junto con su grado de intensidad.
- `<wait>` / `<sync>`: Sincroniza la ejecución temporal de gestos con momentos clave de la alocución o establece pausas.


### 14. Programación Convencional vs. Programación Simbólica

|Criterio de Comparación|Programación Convencional (Procedimental / Algorítmica)|Programación Simbólica (IA Clásica / Basada en Conocimiento)|
|:--|:--|:--|
|**Enfoque de control y ejecución**|Especifica la secuencia lógica exacta paso a paso que la computadora debe seguir mediante código rígido e imperativo.|Separa explícitamente el conocimiento del motor de inferencia, permitiendo que el sistema determine de forma no rígida cómo alcanzar el objetivo.|
|**Representación del dominio**|Se centra en estructuras de datos cuantitativas o estáticas (arreglos, matrices, registros) estrechamente entrelazadas con las instrucciones.|Se centra en la abstracción explícita del conocimiento mediante formalismos lógicos, reglas (IF-THEN), marcos o redes semánticas.|
|**Tipo de operandos**|Diseñada principalmente para el procesamiento numérico y el cálculo masivo de datos.|Diseñada para la manipulación directa de símbolos, conceptos, listas y relaciones lógicas.|
|**Mecanismo de resolución**|Depende de la existencia previa de un algoritmo determinista e implícito diseñado por el programador.|Depende de métodos de inferencia lógica, deducción automática y búsqueda heurística.|
|**Modificabilidad y mantenimiento**|Modificar reglas de negocio requiere alterar y recompilar el código entrelazado del programa.|Es modular e incremental; se pueden añadir o editar hechos y reglas en la base de conocimientos sin modificar el motor de inferencia.|
|**Manejo de incertidumbre**|Asume que los datos son completos, exactos y deterministas; le cuesta manejar información parcial.|Puede representar y razonar sobre información incompleta, incierta o probabilística (p. ej., mediante lógica de predicados o factores de certeza).|
|**Explicabilidad**|No cuenta con un mecanismo intrínseco para explicar sus resultados al usuario.|Incorpora componentes explicativos que permiten trazar y comunicar las reglas o pasos lógicos seguidos.|

---

### 15. Cómputo Tradicional vs. Cómputo de Inteligencia Artificial

|Criterio de Comparación|Cómputo Tradicional|Cómputo de Inteligencia Artificial (Simbólica y Subsimbólica)|
|:--|:--|:--|
|**Paradigma de procesamiento**|Puramente algorítmico e instructivo: ejecuta instrucciones predefinidas sobre entradas conocidas.|Cognitivo y declarativo/orientado a datos: abarca desde razonamiento simbólico hasta el aprendizaje automático (_Machine Learning_ y _Deep Learning_).|
|**Capacidad de aprendizaje**|Carece de autoaprendizaje; su comportamiento es fijo y requiere reprogramación humana para adaptarse a casos nuevos.|Aprende patrones de manera autónoma a partir de datos previos (_data-driven_) o se adapta refinando sus parámetros sin estar explícitamente programada.|
|**Resolución de problemas**|Orientado a problemas bien estructurados con soluciones algorítmicas exactas (p. ej., nóminas, bases de datos).|Orientado a problemas no estructurados, complejos, no lineales o con alta incertidumbre (visión, lenguaje natural, diagnóstico).|
|**Flexibilidad y toma de decisiones**|Aplica reglas estáticas fijadas _a priori_ de manera mecánica y repetitiva.|Exhibe comportamiento adaptativo y racional, eligiendo la mejor acción posible para un objetivo basándose en sus percepciones y datos.|
|**Naturaleza del programa**|El programador especifica el código completo y los pasos algorítmicos exactos.|El sistema genera el modelo o la inferencia analizando masas de datos o manipulando reglas de conocimiento.|
|**Arquitectura de hardware**|Se ejecuta de forma predominantemente secuencial sobre procesadores generales (CPU).|Requiere y aprovecha el procesamiento masivamente en paralelo mediante arquitecturas avanzadas como GPUs o chips neuromórficos.|

---

### 16. Cerebro Humano vs. Computadora

| Criterio de Comparación             | Cerebro Humano                                                                                                                                   | Computadora / Supercomputadora                                                                                                                          |
| :---------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Unidades de procesamiento**       | Aproximadamente **\(10^{11}\) neuronas biológicas** en el sistema nervioso.                                                                      | Desde **4 CPUs** en ordenadores personales hasta **\(10^4\) CPUs / billones de transistores** en supercomputadoras.                                     |
| **Conexiones e interconexión**      | Cerca de **\(10^{14}\) a \(10^{15}\) sinapsis**, formando una red densamente interconectada.                                                     | Almacenamiento organizado en memorias RAM (\(10^{11}\) a \(10^{14}\) bits) y discos magnéticos o de estado sólido.                                      |
| **Velocidad de ciclo (Frecuencia)** | Tiempo de ciclo lento: aprox. **\(10^{-3}\) segundos** (milisegundos) por impulso nervioso.                                                      | Tiempo de ciclo extremadamente rápido: **\(10^{-9}\) segundos** (nanosegundos / GHz).                                                                   |
| **Modo de procesamiento**           | Procesamiento masivamente **paralelo, distribuido y biológicamente adaptable**.                                                                  | Procesamiento predominantemente **secuencial, guiado por reloj y de altísima velocidad**.                                                               |
| **Mapeo y recuperación de memoria** | Memoria **difusa y dispersa** que funciona por **asociación** de conceptos e ideas.                                                              | Memoria **localizada** que funciona por **referencia directa/dirección física** de almacenamiento.                                                      |
| **Tolerancia a fallos**             | Alta tolerancia a fallos: si parte de la red neuronal se daña, sufre una degradación suave sin pérdida catastrófica inmediata de la información. | Nula tolerancia a errores de hardware: un error o corrupción en direcciones de memoria específicas provoca fallos del sistema o resultados incorrectos. |
| **Dimensión cognitiva y emocional** | Inevitablemente condicionado por la **inteligencia emocional, conciencia, sentido común, contexto cultural, sueños y pasiones**.                 | Opera de manera **aséptica mediante procesos numéricos y estadísticos**, sin conciencia, emociones, ni comprensión del sentido de las cosas.            |
### 17 Conclusiones 
Es interesante como han evolucionado los chatbots desde ALICE a la actualizad con LLM con los que puedes tener una conversación como si fuera  un humano sobre cualquier tema, es curioso como incluso hay personas que le han desarrollado afecto hacia alguna IA.