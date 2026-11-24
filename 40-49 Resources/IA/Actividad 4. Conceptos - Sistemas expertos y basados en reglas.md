### 1. Sistema Experto (SE)
Un **sistema experto** es un programa informático inteligente diseñado para resolver problemas complejos dentro de un dominio altamente especializado y acotado, emulando la capacidad de decisión y la competencia de un experto humano en esa materia. Su arquitectura se caracteriza por la separación explicita e independiente entre la **base de conocimientos** y el **motor de inferencia**.

### 2. Sistema de Producción (SP)
Es un modelo o arquitectura de procesamiento simbólico (popularizado por Emil Post, Newell y Simon) compuesto por tres elementos esenciales: la memoria de trabajo (_working memory_), la memoria de producción (conjunto de reglas) y un procesador cognitivo o mecanismo de control. Opera continuamente en un ciclo de **reconocimiento-acción** o **situación-acción**.

### 3. Sistema Basado en Reglas (SBR)
Es el tipo de sistema de producción o sistema experto más difundido, donde el conocimiento del dominio se representa de forma modular mediante un conjunto de **reglas condicionales**.

### 4. Regla
Es la unidad modular fundamental de conocimiento (un _"chunk"_ de conocimiento) en un SBR. Posee una estructura lógica compuesta por un **antecedente/premisa** (LHS) y un **consecuente/acción** (RHS): 
$$\text{SI } \langle \text{condición/patrón} \rangle \text{ ENTONCES } \langle \text{acción/conclusión} \rangle$$
### 5. Hecho
Es una afirmación, dato o pieza de información atómica que describe el estado actual de las cosas o del problema en un momento determinado. Los hechos sirven de estímulo para activar los antecedentes de las reglas.

### 6. Base de Conocimientos (BC)
Es el componente central y almacén estático del sistema experto que contiene todo el conocimiento declarativo, formal, asociativo e intuitivo (heurísticas) extraído de los expertos del dominio.

### 7. Base de Hechos (Memoria de Trabajo / _Working Memory_)
Es la memoria global de corto plazo del sistema donde se almacenan dinámicamente los datos de entrada proporcionados por el usuario, así como los **hechos e inferencias intermedias** derivados durante la sesión de resolución del problema.

### 8. Motor de Inferencia
Es el procesador o motor computacional que evalúa el estado de la memoria de trabajo contra las reglas de la base de conocimientos, determina qué reglas satisfacen sus condiciones, resuelve conflictos de prioridad y ejecuta las acciones correspondientes para generar nuevas conclusiones.

### 9. Encadenamiento hacia Adelante (_Forward Chaining_)
Es un método de inferencia **guiado por datos** (_data-driven_ o _bottom-up_). Comienza a partir de los hechos conocidos en la memoria de trabajo y aplica las reglas cuyas premisas se cumplen, agregando progresivamente nuevas conclusiones a la memoria hasta alcanzar un objetivo o punto fijo.

### 10. Encadenamiento hacia Atrás (_Backward Chaining_)
Es un método de inferencia **guiado por metas** (_goal-driven_ o _top-down_). Comienza proponiendo una hipótesis u objetivo a probar y trabaja en sentido inverso, buscando las reglas cuyos consecuentes satisfagan dicha meta y convirtiendo sus antecedentes en submetas a verificar.

### 11. Algoritmo Rete
Es un algoritmo de **equiparación rápida de patrones** desarrollado por Charles Forgy en 1979. Preprocesa el conjunto de reglas para construir una red de flujo de datos que almacena los emparejamientos parciales entre ciclos de ejecución, evitando la reevaluación exhaustiva e ineficiente de todas las reglas contra todos los hechos.

### 12. Equiparación (_Pattern Matching_)
Es el proceso mediante el cual el motor de inferencia compara los hechos presentes en la memoria de trabajo con los patrones o condiciones del antecedente (LHS) de las reglas para determinar cuáles se satisfacen y pueden activarse.

### 13. Inferencia
Es el proceso lógico-computacional mediante el cual el motor aplica reglas y estrategias de razonamiento a los hechos existentes para derivar y sintetizar **nuevas conclusiones o decisiones** que no estaban explícitamente registradas en el sistema.

### 14. Regla de Producción
Es la denominación formal de una regla condicional de tipo _condición-acción_ dentro de un sistema de producción, especificando la transformación o cambio de estado que debe sufrir la memoria de trabajo al cumplirse un patrón determinado.

### 15. Red de Inferencia
Es una estructura estática en forma de grafo en la que los nodos representan evidencias e hipótesis (intermedias o finales) y los arcos representan las relaciones lógicas, reglas o ponderaciones de verosimilitud que propagan la información a través del sistema.

### 16. Encadenamiento Mixto

Es una estrategia de razonamiento híbrida que combina el **encadenamiento hacia adelante** (para procesar datos e inferir consecuencias automáticas a medida que llegan) con el **encadenamiento hacia atrás** (para verificar subobjetivos o solicitar datos específicos al usuario solo cuando son requeridos).

### 17. Tareas de un Sistema Experto

Un sistema experto se diseña para realizar las siguientes tareas principales en su dominio:

- **Diagnóstico:** Inferir fallas o causas subyacentes a partir de síntomas observados.
- **Planificación:** Diseñar secuencias de acciones para lograr un objetivo.
- **Control y Monitoreo:** Regular procesos continuos y comparar datos observados contra patrones esperados.
- **Configuración:** Ensamblar correctamente los componentes de un sistema complejo.
- **Interpretación:** Explicar y analizar datos u observaciones.
- **Pronóstico / Predicción:** Estimar los resultados o la evolución futura de una situación.
- **Instrucción / Tutoría:** Guiar interactivamente el aprendizaje de un estudiante.
- **Prescripción / Remedio:** Proponer tratamientos o soluciones a un problema diagnosticado.
