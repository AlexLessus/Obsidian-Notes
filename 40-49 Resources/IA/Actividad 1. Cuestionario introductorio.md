#AI-u2
- **¿Qué se entiende por conocimiento?** El conocimiento es la comprensión, conciencia o familiaridad con hechos, información, descripciones o habilidades adquiridas a través de la experiencia, el aprendizaje o la educación

- **¿Qué tipos de conocimientos hay?** Se clasifica principalmente en: conocimiento explícito (fácil de articular, estructurar y documentar), tácito (basado en la intuición y la experiencia personal), declarativo (saber "qué" son los hechos) y procedimental (saber "cómo" ejecutar tareas)

- **¿Cuál de estos tipos de conocimientos pueden darse dentro de la inteligencia artificial (IA)?** En la IA se maneja predominantemente el conocimiento explícito, el declarativo y el procedimental, ya que pueden ser formalizados a través de algoritmos, estructuras lógicas y bases de datos.

- **Para la IA, ¿qué es el conocimiento?** Es información abstraída, estructurada y codificada formalmente de modo que un agente inteligente o sistema informático pueda almacenarla, procesarla y utilizarla para tomar decisiones, planificar o inferir conclusiones

- **¿Por qué es importante el conocimiento en la IA?** Porque permite que los agentes y sistemas transciendan el simple procesamiento mecánico de datos. El conocimiento proporciona el contexto y las reglas necesarias para el razonamiento estructurado, posibilitando la resolución de problemas complejos y el desarrollo de comportamientos racionales

- **En IA, ¿qué tipos de conocimientos existen?** Se reconocen diversos tipos: declarativo (afirmaciones y hechos), procedimental (secuencias de pasos y algoritmos), heurístico (reglas prácticas e intuiciones codificadas para acortar búsquedas y tomar decisiones eficientes) y metaconocimiento (conocimiento sobre cómo usar, estructurar o controlar el propio conocimiento)

- **¿Cómo podemos representar el conocimiento en la IA?** El conocimiento se representa mediante estructuras formales que asocian datos concretos con reglas lógicas, permitiendo conectar instancias específicas de problemas con sus soluciones matemáticas o deductivas

- **¿Qué tipos y/o técnicas se siguen para la representación del conocimiento?** Se utilizan técnicas formales como la lógica de predicados, las reglas de producción en formato IF...THEN, los árboles de decisión, las redes semánticas, los marcos (_frames_) y las ontologías. Además, en el aprendizaje automático, se emplean modelos conexionistas como las redes neuronales artificiales

- **¿Qué es un sistema basado en conocimientos (SBC)?** Es un programa informático diseñado para resolver problemas específicos utilizando una base estructurada de conocimientos humanos capturados y un motor de inferencia que evalúa dichos conocimientos frente a los datos de entrada

- **¿Qué es un sistema experto (SE)?** Es un programa informático inteligente que utiliza conocimiento y procedimientos de inferencia para resolver problemas que son lo suficientemente difíciles como para requerir una experiencia humana significativa para sus soluciones. El objetivo es emular la capacidad de toma de decisiones de un experto humano en su totalidad

- **¿Existe alguna diferencia entre un SE y un SBC?** Sí. Todos los sistemas expertos son sistemas basados en conocimientos, pero no todos los SBC son sistemas expertos. Un Sistema Experto está diseñado para igualar o superar el desempeño de un experto humano en un dominio altamente especializado y delimitado, mientras que un SBC es cualquier sistema que dependa de una base de conocimiento (como un sistema de clasificación simple) sin aspirar al nivel de competencia de un experto

- **Indicar la arquitectura de un SE o un SBC y a groso modo una explicación de cada uno de sus componentes:**     
    - **Base de Conocimientos:** Es el almacén que contiene los hechos y las reglas de producción (ej. IF...THEN) extraídas del dominio.
    - **Motor de Inferencia:** Es el procesador central que correlaciona los datos ingresados con las reglas de la base de conocimientos para inferir conclusiones o tomar decisiones.        
    - **Interfaz de Usuario:** El componente mediante el cual el usuario final introduce los datos del problema y recibe la solución o diagnóstico.
    - **Módulo de Explicación:** Subsistema que permite al programa detallar al usuario los pasos lógicos, respondiendo al "cómo" y "por qué" se llegó a una deducción.        
    - **Módulo de Adquisición de Conocimiento:** Interfaz orientada al ingeniero que permite actualizar, integrar y validar nuevas reglas dentro de la base de conocimientos.

- **Lenguajes utilizados para la representación y manejo del conocimiento en la IA:** Los lenguajes más representativos orientados a la deducción, objetos y reglas son LISP, PROLOG y CLIPS.

- **¿Qué es la ingeniería del conocimiento?** Es la rama de la IA que aborda la teoría y los procesos necesarios para extraer, formalizar, estructurar e implementar el conocimiento de los expertos humanos dentro de un sistema computacional.    

- **¿Qué metodología sigue la ingeniería del conocimiento para diseñar un SE o SBC?**
    1. **Identificar la tarea:** El ingeniero debe delimitar el rango de preguntas que la base de conocimientos soportará y los hechos que estarán disponibles para cada caso específico.
    2. **Adquisición del conocimiento:** Extraer la información empírica y heurística del experto humano.
    3. **Codificar la descripción del problema:** Plasmar instancias específicas en el sistema utilizando la ontología definida y sentencias lógicas.
    4. **Plantear consultas:** Formular preguntas al procedimiento de inferencia y extraer las respuestas derivadas.

- **¿Qué roles existen dentro de la Ingeniería del conocimiento?** El experto del dominio (quien posee la experiencia heurística), el ingeniero del conocimiento (quien traduce ese saber a reglas formales) y el usuario (quien opera el sistema para resolver problemas diarios).

- **¿Qué es un ingeniero en conocimientos y qué funciones realizan?** Es el profesional de diseño de software especializado en IA encargado de construir la base de conocimiento. Sus funciones abarcan entrevistar exhaustivamente al experto humano, perfilar y delimitar la tarea del sistema, elegir la técnica de representación apropiada y redactar las reglas estructurales.

- **¿Qué es una ontología y qué pasos se siguen para su construcción?, dar un ejemplo:** Una ontología es una especificación formal, explícita y estructurada de los conceptos de un dominio y las interrelaciones que existen entre ellos._Pasos:_ 1) Determinar el dominio y el alcance. 2) Reutilizar ontologías ya existentes. 3) Enumerar los términos centrales. 4) Definir las clases y subclases jerárquicamente. 5) Establecer las propiedades de los conceptos. 6) Generar las instancias (objetos reales)._Ejemplo:_ En una ontología sobre automoción, "Vehículo" es la clase principal; "Automóvil" y "Motocicleta" son subclases. Se define una propiedad "tiene_componente" que vincula la subclase "Automóvil" con la instancia "Motor de Combustión".

- **¿Qué se entiende por razonamiento?** Es el proceso algorítmico o lógico que permite utilizar hechos conocidos y premisas almacenadas para evaluar situaciones, formular proyecciones deductivas y llegar a conclusiones que originalmente no estaban explícitas en el sistema.

- **¿Qué tipos de razonamientos existen y cuáles de estos son aplicables dentro de la IA?** Existen el razonamiento deductivo, inductivo, abductivo, basado en casos y probabilístico. Todos son aplicables en la IA: los sistemas expertos tradicionales utilizan principalmente deducción y abducción, mientras que disciplinas más recientes emplean la inducción, la probabilidad y redes neuronales para el aprendizaje automático (_Machine Learning_).

- **¿Qué se entiende por método de razonamiento?** Es la estrategia de procesamiento específica que utiliza el motor de inferencia para transitar a través de las reglas lógicas. Los métodos clásicos son el encadenamiento hacia adelante (_forward chaining_, donde se parte de los datos iniciales para alcanzar una conclusión final) y el encadenamiento hacia atrás (_backward chaining_, donde se asume una hipótesis y se rastrean las reglas hacia atrás para comprobar si los datos iniciales la sustentan).