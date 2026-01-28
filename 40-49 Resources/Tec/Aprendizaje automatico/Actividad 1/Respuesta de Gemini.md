### 1. Definiciones Fundamentales
**Inteligencia**
podemos definir la **inteligencia** en este contexto técnico como la conjunción de las siguientes capacidades:
1. **Aprendizaje y Reconocimiento de Patrones:** Es la capacidad de **reconocer e interpretar grandes volúmenes de datos** captados del entorno para identificar comportamientos o estructuras (patrones).
2. **Adaptabilidad:** Es la habilidad de un sistema para **adaptarse al medio** a partir de la información que procesa.
3. **Resolución de Problemas y Toma de Decisiones:** Es la facultad de utilizar el conocimiento adquirido para **aportar soluciones innovadoras a problemas complejos** y facilitar la **toma de decisiones** (clasificación, predicción u optimización).

**Inteligencia Humana**
Es la capacidad biológica y mental para adaptarse a entornos cambiantes, razonar de manera abstracta, comprender ideas complejas, aprender de la experiencia y resolver problemas mediante la creatividad y la consciencia. A diferencia de la máquina, incluye componentes emocionales y éticos intrínsecos.

**Inteligencia Artificial (IA)** 
Es la rama de la computación que busca diseñar sistemas capaces de realizar tareas que requerirían inteligencia si fueran hechas por un humano. El objetivo es que las computadoras puedan aprender a partir de patrones de datos, percibir su entorno y tomar decisiones para maximizar el éxito en una tarea dada.

**Diferencias en la Programación**

| **Característica** | **Programación de Sistemas Convencionales**       | **Programación de Sistemas Inteligentes (IA/ML)**        |
| ------------------ | ------------------------------------------------- | -------------------------------------------------------- |
| **Enfoque**        | Determinista (Algoritmos explícitos).             | Probabilístico y adaptativo.                             |
| **Flujo**          | Datos + Reglas = Respuestas.                      | Datos + Respuestas = Reglas (Modelos).                   |
| **Mantenimiento**  | Si los datos cambian, debes reescribir el código. | Si los datos cambian, el sistema se re-entrena y adapta. |
| **Rigidez**        | Sigue estrictamente el "If-Then-Else".            | Puede manejar ambigüedad y datos no vistos previamente.  |

**Capacidades de la Máquina**
- **¿Qué puede hacer?** Procesar grandes volúmenes de datos a velocidades sobrehumanas, reconocer patrones complejos (visión, voz), realizar tareas repetitivas sin fatiga, y hacer predicciones basadas en estadística histórica.
- **¿Qué (probablemente) nunca podrá hacer?** Sentir empatía genuina, tener consciencia de su propia existencia (qualia), ejercer un juicio moral subjetivo (no basado en reglas programadas) o tener creatividad con "intención" artística pura sin basarse en recombinación de datos existentes.    

---

### 2. Historia y Tipología de la IA

**Origen del nombre:**
Se acuña oficialmente en **1956**, durante la conferencia de Dartmouth, organizada por John McCarthy, Marvin Minsky, y otros pioneros.

**Tipos de Inteligencia Artificial**
- **IA Clásica:** Se refiere a los primeros enfoques basados en lógica formal y reglas explícitas. No "aprendía" de datos, sino que ejecutaba instrucciones lógicas predefinidas.
    
- **IA Simbólica (GOFAI):** Es parte de la IA clásica. Utiliza símbolos legibles por humanos y reglas lógicas para resolver problemas (ej. Sistemas Expertos). Es buena para razonamiento lógico pero mala para reconocer patrones difusos (como una cara).
    
- **IA Conexionista:** Se inspira en la biología (neuronas). No usa reglas explícitas, sino redes de nodos interconectados que ajustan sus pesos numéricos. Es la base del _Deep Learning_ actual.
    
- **IA Débil (Estrecha):** Es la que tenemos hoy. Sistemas diseñados para resolver **una** tarea específica muy bien (ej. jugar ajedrez o recomendar videos), pero inútiles fuera de ese dominio.
    
- **IA Fuerte (AGI - Inteligencia Artificial General):** Un sistema hipotético con la capacidad de entender, aprender y aplicar inteligencia a **cualquier** problema intelectual, igual o mejor que un humano. Aún no existe.
    
- **IA Generativa:** Un subcampo (muy de moda) enfocado en modelos que pueden crear **nuevo** contenido (texto, imágenes, audio, código) similar a los datos de entrenamiento, en lugar de solo clasificar o predecir valores existentes.

**Diferencia: IA vs. IA Generativa**
La IA es el campo general (el "todo"). La IA Generativa es un subconjunto específico que se centra en la **creación** de datos nuevos. Una IA tradicional te dice "esto es una foto de un gato"; una IA Generativa "dibuja un gato nuevo que no existe".

**Ramas Principales**

1. **Machine Learning (Aprendizaje Automático):** El núcleo de tu materia.
    
2. **Visión Computacional:** Procesamiento de imágenes.
    
3. **Procesamiento de Lenguaje Natural (NLP):** Entender texto/voz.
    
4. **Robótica:** Interacción física.
    
5. **Sistemas Expertos:** Toma de decisiones basada en reglas.
    

Riesgos Éticos (Mencionados en tu temario )

- **Sesgo en los datos (Bias):** Si los datos históricos son racistas o sexistas, la IA lo será.
    
- **Privacidad:** Uso indebido de datos personales para entrenar modelos.
    
- **Caja Negra:** Falta de explicabilidad en cómo toma decisiones una red neuronal.
    
- **Desplazamiento laboral:** Automatización de empleos.
    

---

### 3. Análisis de Casos de Uso

Aquí tienes el desglose rápido para tu análisis:

| **Caso de Uso**                | **Rama Predominante**                         | **Beneficio Principal**                                               | **Riesgo Ético / Limitación**                                                                            |
| ------------------------------ | --------------------------------------------- | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Diagnóstico médico**         | Visión Computacional / ML Supervisado         | Detección temprana y precisa de anomalías que el ojo humano omite.    | Falsos negativos o responsabilidad legal en caso de error (¿quién tiene la culpa?).                      |
| **Vehículos autónomos**        | Visión, Robótica y Aprendizaje por Refuerzo   | Reducción de accidentes humanos y optimización de transporte.         | El "Dilema del tranvía" (decidir a quién salvar en accidente inevitable).                                |
| **ChatGPT en educación**       | NLP / IA Generativa                           | Tutoría personalizada 24/7 y acceso rápido a información.             | Alucinaciones (datos falsos) y pérdida de pensamiento crítico en alumnos.                                |
| **Robot industrial (Calidad)** | Visión Computacional / Detección de anomalías | Consistencia, velocidad y trabajo continuo (24/7).                    | Desplazamiento de mano de obra operativa.                                                                |
| **Sistemas de RRHH (Hiring)**  | NLP / Clasificación                           | Filtrado eficiente de miles de CVs para encontrar candidatos idóneos. | **Sesgo algorítmico:** puede discriminar por género o etnia si aprendió de patrones históricos sesgados. |

**Importancia de la IA hoy:** Facilita la toma de decisiones complejas, optimiza procesos industriales (Industria 4.0/5.0) y permite analizar volúmenes de datos inmanejables para el cerebro humano.

---

### 4. IA Verde (Green AI) y Relación con ML

**¿Qué es la IA Verde?**

Es una iniciativa para hacer que el desarrollo de la IA sea ambientalmente sostenible. Entrenar modelos grandes (como GPT) consume cantidades masivas de electricidad y agua (para enfriar servidores), generando una huella de carbono enorme.

**¿Qué hacer para lograrla?**

1. **Modelos más eficientes:** Crear algoritmos que requieran menos datos y cómputo ("TinyML").
    
2. **Reutilización:** Usar modelos pre-entrenados (Transfer Learning) en lugar de entrenar desde cero.
    
3. **Hardware optimizado:** Usar procesadores diseñados específicamente para IA (TPUs) que gasten menos energía.
    

**IA como antecedente al Aprendizaje Automático**
Es una relación de jerarquía, no solo de tiempo.

La **Inteligencia Artificial** es la ciencia general (nacida en los 50s). Dentro de ella, surgió el **Aprendizaje Automático (Machine Learning)** en los 80s/90s como la técnica donde _no_ programamos reglas, sino que dejamos que la máquina las aprenda. Luego, dentro del ML, surge el **Deep Learning** (2010s). Por tanto, la IA es el contenedor y el antecedente conceptual que permitió el desarrollo específico del ML que estudiarás en esta materia.