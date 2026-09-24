Alexis De Jesus Perez Carmona
### 1. Definición de Inteligencia Artificial Distribuida (IAD)
La **Inteligencia Artificial Distribuida (IAD o _DAI - Distributed Artificial Intelligence_)** es un subcampo de la Inteligencia Artificial que estudia el comportamiento colectivo e inteligente que surge de la cooperación de múltiples entidades autónomas computacionales denominadas **agentes**. Trata sobre el diseño y análisis de sistemas de IA conectados en red, analizando cómo un grupo de módulos distribuidos pueden dividir la carga de trabajo, compartir conocimientos sobre un problema y coordinar sus acciones para desarrollar soluciones conjuntas.

### 2. Enfoques o Campos de Estudio de la IAD
La IAD se divide principalmente en dos grandes ramas o enfoques de investigación:
1. **Resolución Distribuida de Problemas (_Distributed Problem Solving - DPS_)**: Se centra en dividir un problema global complejo entre varios nodos o módulos que cooperan estrechamente. En este enfoque, los agentes comparten un objetivo común prefijado y coordinan de forma estructurada la distribución del conocimiento y los datos.
2. **Sistemas Multiagente (_Multi-Agent Systems - MAS_)**: Se enfoca en el estudio del comportamiento emergente, la comunicación, la negociación y la coordinación entre múltiples agentes parcialmente autónomos que poseen visión local y pueden tener metas individuales o colectivas.

### 3. Definición de Agente
Un **agente** es un sistema informático o entidad física situado dentro de un entorno determinado, sobre el cual actúa de forma autónoma y flexible con el fin de cumplir con sus objetivos o metas preestablecidas. El agente percibe información de su ambiente mediante **sensores** y modifica dicho ambiente a través de **actuadores**.

### 4. Definición de un Agente de Software
Un **agente de software** (o _software agent_) es un programa o proceso informático equivalente a un proceso del sistema operativo que existe dentro de un contexto digital o sistema de red. Actúa de manera autónoma e interactiva realizando tareas en representación de un usuario o de otro sistema, comunicándose mediante protocolos interproceso.

### 5. Definición de un Agente Inteligente
Un **agente inteligente** es una entidad capaz de percibir su entorno, procesar la información mediante técnicas de IA y **tomar decisiones de forma autónoma** adaptándose a las variaciones del ambiente. No opera simplemente como un autómata rígido, sino que actúa con racionalidad, proactividad y capacidad de inferencia para maximizar su éxito o cumplir sus metas.

### 6. Clasificación o Tipos de Agentes en General
De forma general, los agentes se clasifican según la naturaleza de su soporte físico y medio de actuación:

- **Agentes Humanos**: Seres humanos o equipos que perciben el entorno a través de los sentidos biológicos y actúan mediante sus miembros físicos.
- **Agentes Robóticos / Físicos**: Robots, vehículos autónomos o dispositivos industriales equipados con cámaras, LiDAR o sensores físicos y motores/actuadores.
- **Agentes de Software / Virtuales**: Bots, agentes conversacionales, asistentes digitales o procesos de software que operan en sistemas operativos, redes o entornos web.

### 7. Clasificación o Tipos de Agentes según su Algoritmo y Arquitectura
Según la estructura interna de su programa de procesamiento y toma de decisiones, los agentes se clasifican en:

- **Agente Reactivo Simple**: Funciona bajo una regla rígida de condición-acción basada exclusivamente en la percepción actual. No guarda historial de percepciones ni realiza planeación a largo plazo.
- **Agente Basado en Modelos**: Mantiene un estado interno que le permite saber "cómo funciona y evoluciona el mundo" y qué efectos tendrán sus acciones, permitiéndole operar en entornos parcialmente observables.
- **Agente Basado en Metas (Deliberativo / Cognitivo)**: Incorpora descripciones de objetivos o metas explícitas. Evalúa posibles escenarios futuros mediante razonamiento lógico y planificación para elegir las acciones que lo lleven al estado deseado.
- **Agente Basado en Utilidad**: Utiliza una función de utilidad matemática que mide el grado de "satisfacción" o éxito en un estado determinado. Le permite tomar decisiones óptimas cuando existen múltiples metas en conflicto.
- **Agente de Aprendizaje**: Capaz de operar en entornos totalmente desconocidos. Se divide en cuatro elementos: _elemento de rendimiento_, _crítica_ (evalúa el éxito), _elemento de aprendizaje_ (realiza mejoras) y _generador de problemas_ (propone nuevas acciones exploratorias).
- **Agente Híbrido / EBDI**: Combina componentes reactivos para responder velozmente en tiempo real con componentes deliberativos o modelos emocionales/cognitivos (como el modelo BDI: _Beliefs, Desires, Intentions_).

### 8. Propiedades de los Agentes Inteligentes

Las propiedades fundamentales de un agente inteligente incluyen:
- **Conocimiento del entorno**: Capacidad de sensar e interactuar con el ambiente.
- **Autonomía**: Operación y toma de decisiones según su estado interno sin intervención humana directa.
- **Capacidad Inferencial**: Habilidad para deducir nueva información y trabajar sobre metas abstractas a partir de observaciones.
- **Reactividad**: Respuesta adecuada y oportuna a los estímulos del ambiente.
- **Proactividad**: Capacidad de tomar la iniciativa para alcanzar sus objetivos en lugar de limitarse a reaccionar a estímulos.
- **Sociabilidad**: Habilidad de interactuar, comunicarse y cooperar con otros agentes para resolver problemas.

### 9. Características de los Agentes
Entre sus características organizacionales y operativas destacan:
- **Visión local**: Ningún agente posee un conocimiento global completo de todo el sistema.
- **Descentralización**: El control y las decisiones están distribuidas sin depender de un único agente central.
- **Adaptabilidad**: Modificación del comportamiento basada en la experiencia y los cambios del entorno.
- **Racionalidad limitada**: Toma de decisiones informadas dentro de los límites de sus recursos computacionales y de datos.
- **Heterogeneidad**: Diferentes agentes pueden poseer distintas capacidades, arquitecturas u objetivos dentro del mismo sistema.

### 10. Definición de Agente Débil
El término **agente débil** (propuesto en la caracterización clásica de Wooldridge y Jennings) describe a un sistema de software que cumple únicamente con las cuatro propiedades operativas básicas de la programación orientada a agentes: **autonomía, habilidad social, reactividad y proactividad**.

### 11. Definición de Agente Fuerte
El término **agente fuerte** atribuye al sistema informático conceptos intencionales y cognitivos más complejos basados en la noción humana de la mente, tales como **creencias, deseos, intenciones (modelo BDI), conocimiento, compromisos y estados emocionales**.

### 12. Estructura o Arquitectura de un Agente
La estructura estándar de un agente se compone de:
1. **Sensores**: Interfaces que captan las percepciones del entorno.
2. **Estado Interno / Base de Conocimiento**: Almacén de reglas, modelos del mundo o datos históricos.
3. **Programa / Motor de Razonamiento**: Algoritmo que procesa las percepciones y selecciona la acción conveniente.
4. **Actuadores**: Interfaces que ejecutan las acciones físicas o digitales sobre el entorno.

### 13. Tipos de Arquitecturas de Agentes
- **Arquitecturas Reactivas**: Basadas en circuitos o tablas de reglas simples condición-acción.
- **Arquitecturas Deliberativas (Cognitivas)**: Basadas en la manipulación de lógica formal, bases de conocimiento y motores de inferencia.
- **Arquitecturas BDI (_Belief, Desire, Intention_)**: Organizadas en torno a las Creencias (lo que sabe del mundo), Deseos (sus metas) e Intenciones (los planes en ejecución).
- **Arquitecturas Híbridas**: Estructuradas en capas jerárquicas (por ejemplo, una capa reactiva inferior para tiempo real y una capa deliberativa superior para planificación).

### 14. ¿Cómo se construye un agente y qué consideraciones tomar en cuenta?
Para construir un agente es necesario:

1. **Especificar el entorno de trabajo** mediante la metodología **PEAS / REAS** (Rendimiento, Entorno, Actuadores, Sensores).
2. **Definir el nivel de autonomía y capacidad de procesamiento** de acuerdo con el hardware disponible.
3. **Elegir la arquitectura adecuada** (reactiva, deliberativa o híbrida) según los requerimientos de respuesta en tiempo real.
4. **Implementar los protocolos de comunicación y mecanismos de seguridad/tolerancia a fallos** si interactuará en red.

### 15. ¿Cómo se define el comportamiento de un agente?
Matemáticamente, el comportamiento de un agente se define mediante la **función del agente** ($f: P^* \to A$), la cual mapea cualquier secuencia histórica dada de percepciones ($P^*$) hacia una acción específica ($A$). En la práctica computacional, esta función abstracta se implementa a través del **programa del agente** ejecutándose sobre una arquitectura física.


### 16. Tipos de modelos para diseñar y construir un agente
- **Enfoque Formal o Clásico**: Basado en dotar al agente de representaciones formales del problema y motores de inferencia lógica.
- **Enfoque Constructivista / Emergente**: Diseña agentes individuales muy simples para que, mediante reglas de interacción locales, el sistema genere un comportamiento global complejo.
- **Modelado Orientado a Objetos / Extensión a Agentes (AOSE)**: Trata a los agentes como extensiones avanzadas de objetos de software con roles y capacidades de comunicación.

### 17. Tipos de Entornos de Trabajo
Los entornos donde operan los agentes se clasifican según las siguientes dimensiones:
- **Observabilidad**: Totalmente observable vs. Parcialmente observable.
- **Certidumbre**: Determinista vs. Estocástico.
- **Continuidad temporal**: Episódico vs. Secuencial.
- **Dinamismo**: Estático vs. Dinámico (y Semidinámico).
- **Discretización**: Discreto vs. Continuo.
- **Concurrencia**: Agente único vs. Multiagente.

### 18. Aplicaciones de los Agentes
- Automoción y conducción autónoma.
- Robótica colaborativa e industrial (Industria 4.0/5.0).
- Asistentes digitales y monitoreo de salud/telemedicina.
- Mercados digitales y comercio electrónico automatizado.
- Gráficos por computadora y simulación de multitudes en cine/videojuegos.

### 19. Plataformas de Desarrollo de Agentes
Entre los marcos de trabajo (_frameworks_) y plataformas más extendidas para el desarrollo de agentes destacan: **JADE**, **MADKiT**, **NetLogo**, **CORMAS**, **AgentTool** y **Janus**.

### 20. ¿Qué es un Modelo Basado en Agentes (ABM) y sus componentes?
Un **Modelo Basado en Agentes (_Agent-Based Model - ABM_)** es una simulación computacional para analizar fenómenos complejos mediante múltiples agentes autónomos que interactúan en un entorno compartido. Sus componentes son:

1. **Los Agentes**: Entidades autónomas con atributos, estados y reglas de comportamiento.
2. **El Entorno**: El espacio (físico o abstracto) donde habitan y se desplazan los agentes.
3. **Las Reglas e Interacciones**: Protocolos que rigen la comunicación y las relaciones entre agentes.

### 21. Metodologías Orientadas al Desarrollo de Agentes (AOSE)
Pertenecientes a la Ingeniería de Software Orientada a Agentes (_AOSE_), destacan:

- **GAIA**: Análisis basado en roles e interacciones organizacionales.
- **MaSE (_Multiagent Software Engineering_)**: Propone agentes como extensiones de objetos.
- **INGENIAS / MESSAGE**: Herramientas para modelado y generación de código.
- **Mas-CommonKADS**: Extiende el modelado del conocimiento a sistemas multiagente.
- **Vocales (_Voyelles_)**: Analiza el sistema desde cuatro ejes: Agente, Entorno, Interacción y Organización.
- **ADELFE**: Orientada al diseño de sistemas cooperativos.

### 22. Definición de DAML, AUML, JADE-FIPA y CommonKADS
- **DAML (_DARPA Agent Markup Language_)**: Lenguaje en XML/RDF creado para la Web Semántica que permite a los agentes interpretar ontologías y razonar sobre el conocimiento web.
- **AUML (_Agent UML_)**: Extensión de la notación UML (diseñada por James Odell) para especificar diagramas de secuencia de interacción y protocolos entre agentes.
- **JADE-FIPA**: **JADE** (_Java Agent Development Framework_) es una plataforma en Java que implementa los estándares internacionales de la **FIPA** (_Foundation for Intelligent Physical Agents_), incluyendo directorio de agentes (páginas blancas), directorio de servicios (páginas amarillas), transporte de mensajes y lenguaje **ACL**.
- **CommonKADS / Mas-CommonKADS**: Metodología estándar de ingeniería del conocimiento adaptada para el desarrollo de sistemas expertos y agentes inteligentes mediante especificación de protocolos.

### 23. Concepto de Sistemas MultiAgente (SMA / MAS)
Un **Sistema Multiagente** es una red descentralizada de múltiples agentes autónomos que interactúan entre sí dentro de un entorno compartido. Al colaborar, negociar o competir, el sistema es capaz de resolver problemas complejos que sobrepasan las capacidades individuales de cada agente.

### 24. Composición de un Sistema Multiagente
Un SMA está compuesto por:
1. **Un conjunto de Agentes** (autónomos e interactivos).
2. **Un Entorno compartido**.
3. **Un Middleware o Plataforma de Agentes** que gobierna el acceso a los recursos.
4. **Protocolos de Comunicación y Lenguajes** (como FIPA-ACL o KQML).
5. **Estructuras de Organización y Coordinación**.

### 25. Aplicaciones de los Sistemas Multiagente
- Simulación de tráfico urbano y redes inteligentes de transporte.
- Modelado epidemiológico de propagación de enfermedades.
- Coordinación de enjambres de drones y robótica colaborativa.
- Diagnóstico distribuido de fallas en redes de telecomunicaciones.
- Gestión de logística, cadenas de suministro y mercados digitales.

### 26. ¿Qué es REAS y para qué se utiliza?
**REAS** es un marco de especificación de entornos de trabajo para agentes (variante de la sigla PEAS en inglés). Corresponde a: **R**endimiento (medida de éxito), **E**ntorno, **A**ctuadores y **S**ensores. Se utiliza en las fases iniciales del diseño para formalizar los requisitos operacionales antes de construir la arquitectura del agente.

### 27. Descripción Detallada de los Entornos de Trabajo

|Par de Entornos|Descripción y Diferencia Clave|Ejemplo Representativo|
|:--|:--|:--|
|**Totalmente Observable vs. Parcialmente Observable**|En el **totalmente observable**, los sensores captan todo el estado relevante del entorno. En el **parcialmente observable**, existe visión limitada o ruido en los sensores.|Un juego de ajedrez es totalmente observable; conducir un taxi o una aspiradora con un solo sensor es parcialmente observable.|
|**Determinista vs. Estocástico**|En el **determinista**, el siguiente estado está completamente determinado por el estado actual y la acción realizada. En el **estocástico**, existe incertidumbre sobre el resultado.|El ajedrez es determinista; la conducción en tráfico real es estocástica.|
|**Episódico vs. Secuencial**|En el **episódico**, cada experiencia se divide en etapas independientes donde las acciones pasadas no afectan las futuras. En el **secuencial**, cada decisión afecta las decisiones futuras.|Un robot clasificador de partes es episódico; el ajedrez es secuencial.|
|**Estático vs. Dinámico**|En el **estático**, el entorno no cambia mientras el agente deliberatorio decide. En el **dinámico**, el ambiente cambia constantemente con el paso del tiempo.|Resolver un crucigrama es estático; conducir en carretera es dinámico.|
|**Discreto vs. Continuo**|En el **discreto**, existe un número finito de estados, percepciones y acciones. En el **continuo**, los estados o variables son infinitos/flotantes.|El ajedrez es discreto; el pilotaje de un vehículo es continuo.|
|**Agente Único vs. Multiagente**|En **agente único**, el agente opera solo en el entorno sin otras entidades inteligentes. En **multiagente**, interactúa con dos o más agentes.|Un solitario/crucigrama es agente único; un juego de póquer o el tráfico vehicular es multiagente.|

---
### 28. Comentarios y Conclusiones
La **Inteligencia Artificial Distribuida** y los **Sistemas Multiagente** representan un cambio de paradigma crucial frente al cómputo centralizado tradicional. Al descentralizar la toma de decisiones en múltiples entidades autónomas pero coordinadas, los sistemas adquieren **escalabilidad, alta resiliencia a fallos y capacidad de adaptación** ante entornos dinámicos e inciertos. Esta arquitectura es la piedra angular de las transformaciones actuales en la **Industria 4.0/5.0**, la Internet de las Cosas (IoT) y la robótica colaborativa.

### 29. Fuentes de donde se obtuvo la información
1. **"Sistema multiagente - Wikipedia, la enciclopedia libre"** (Coordinación distribuida, características, FIPA, AOSE, entornos).
2. **"https://ri.uaemex.mx/bitstream/handle/20.500.11799/63881/secme-35486.pdf"** (Presentación institucional sobre Tipos de Agentes y Entornos de IA, Dr. Héctor Rafael Orozco Aguirre, UAEM).
3. **"Guía didáctica de conceptos de IA"** (Resumen de jerarquía de IA, Agentes de IA y Generativa).
4. **"AprendizajeProfundo_TIA_2025.pdf"** (Programa académico de Ingeniería en Sistemas, Instituto Tecnológico de Ciudad Guzmán).
5. **"Top Deep Learning Frameworks in 2026: A Practical Guide"** (Ecosistema actual de orquestación de agentes con PyTorch).
