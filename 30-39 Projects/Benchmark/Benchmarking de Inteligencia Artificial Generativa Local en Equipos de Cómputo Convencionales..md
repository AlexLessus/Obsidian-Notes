
# Titulo tentativo
Benchmarking de Inteligencia Artificial Generativa Local en Equipos de Cómputo Convencionales.
Benchmarking Local Generative Artificial Intelligence on Conventional Computing Equipment.

opción 2:
Evaluación de Rendimiento de LLMs Cuantizados en Hardware de Entrada: Hacia la Adopción de IA Local en MIPYMEs.
    
Performance Evaluation of Quantized LLMs on Entry-Level Hardware: Towards Local AI Adoption in MSMEs.

## Resumen
La adopción de la Inteligencia Artificial Generativa (IAG) en Micro, Pequeñas y Medianas Empresas (MIPYMEs) enfrenta barreras significativas debido a los costos recurrentes de infraestructura en la nube y los riesgos asociados a la privacidad de los datos. Como alternativa, los Modelos de Lenguaje de Gran Escala (LLMs) de código abierto permiten una ejecución local segura, aunque su rendimiento sobre hardware convencional o heredado no está suficientemente documentado. Este artículo presenta un benchmarking exhaustivo para evaluar la viabilidad técnica de desplegar LLMs locales en estaciones de trabajo con recursos limitados (GPU con 4 GB de VRAM). Utilizando el motor de inferencia Ollama y formatos de cuantización GGUF, se analizó el rendimiento de arquitecturas compactas y de tamaño medio, incluyendo Llama 3.2 (3B), Phi-3.5 Mini (3.8B) y Mistral (7B). Mediante un script automatizado de telemetría, se midieron los tokens por segundo (TPS), el consumo de memoria unificada (RAM/VRAM) y el estrés térmico durante la resolución de tareas administrativas estándar. El análisis de los resultados determina el umbral de viabilidad operativa donde la cuantización evita el desbordamiento de memoria, proporcionando una guía técnica para que las organizaciones integren asistentes de IA garantizando la soberanía de sus datos sin requerir inversión en hardware de alto rendimiento.

**Palabras clave:** Benchmarking, Inteligencia Artificial Local, Cuantización, LLM, MIPYMEs.

---
## Abstract
The adoption of Generative Artificial Intelligence (GenAI) in Micro, Small, and Medium Enterprises (MSMEs) faces significant barriers due to recurring cloud infrastructure costs and data privacy risks. As an alternative, open-source Large Language Models (LLMs) allow for secure local execution, although their performance on conventional or legacy hardware is not sufficiently documented. This paper presents a comprehensive benchmark to evaluate the technical feasibility of deploying local LLMs on workstations with limited resources (4 GB VRAM GPU). Using the Ollama inference engine and GGUF quantization formats, the performance of compact and mid-sized architectures, including Llama 3.2 (3B), gemma3 (4b), Phi-3.5 Mini (3.8B), and Mistral (7B), was analyzed. Through an automated telemetry script, tokens per second (TPS), unified memory consumption (RAM/VRAM), and thermal stress were measured during the execution of standard administrative tasks. The analysis of the results determines the operational viability threshold where quantization prevents memory overflow, providing a technical guide for organizations to integrate AI assistants ensuring data sovereignty without requiring investment in high-performance hardware.

**Keywords:** Benchmarking, Local Artificial Intelligence, Quantization, LLM, MSMEs.

### 1. Introducción
La rápida evolución de la Inteligencia Artificial Generativa (IAG) ha redefinido los paradigmas de productividad y automatización en el entorno corporativo. A través de la implementación de Modelos de Lenguaje de Gran Escala (LLMs, por sus siglas en inglés), las organizaciones han logrado optimizar tareas administrativas, redactar correos electrónicos, clasificar información y generar resúmenes con una eficiencia sin precedentes. Sin embargo, el modelo de despliegue dominante se basa en Software como Servicio (SaaS) alojado en la nube comercial. Si bien este enfoque ofrece capacidades de cómputo masivas, presenta dos barreras críticas para las Micro, Pequeñas y Medianas Empresas (MIPYMEs): los elevados costos recurrentes por licencias de usuario y la pérdida de la soberanía de los datos [1]. Para muchas de estas organizaciones, enviar información financiera, legal o confidencial a servidores externos representa un riesgo de privacidad inasumible.

Como respuesta a estas limitantes, el ecosistema de código abierto ha democratizado el acceso a LLMs altamente capaces que pueden ser ejecutados de manera local. No obstante, la barrera de entrada se ha desplazado del pago de suscripciones a la adquisición de infraestructura de hardware. En su estado nativo, la inferencia de un modelo promedio requiere aceleradores gráficos (GPUs) de gama alta con amplias capacidades de Memoria de Acceso Aleatorio de Video (VRAM), equipos que escapan al presupuesto de la mayoría de las MIPYMEs, cuya infraestructura tecnológica suele estar compuesta por estaciones de trabajo convencionales y portátiles con hardware de generaciones anteriores o gamas de entrada [2].

Para mitigar este cuello de botella, la comunidad científica e ingenieril ha perfeccionado técnicas de compresión de modelos, destacando la cuantización de pesos. Esta técnica, popularizada a través de formatos como GGUF, permite reducir la precisión matemática de los parámetros del modelo —típicamente de punto flotante de 16 bits (FP16) a representaciones de 4 u 8 bits— disminuyendo drásticamente la huella de memoria requerida sin una degradación proporcional en la coherencia de las respuestas [3]. A pesar de estos avances teóricos, existe una brecha significativa en la literatura respecto a la evaluación empírica de estos modelos cuantizados operando bajo las severas restricciones térmicas y de memoria de equipos convencionales (por ejemplo, sistemas limitados a 4 GB de VRAM).

El presente artículo tiene como objetivo principal realizar un _benchmarking_ técnico para evaluar el rendimiento y viabilidad operativa de tres arquitecturas de LLMs de código abierto (Llama 3.2 de 3B, Gemma3 de 4b, Phi-3.5 Mini de 3.8B y Mistral de 7B parámetros) ejecutadas localmente en hardware de entrada. Mediante la captura automatizada de telemetría de hardware, se analiza la relación entre el nivel de cuantización, la velocidad de inferencia (tokens por segundo), el desbordamiento hacia la memoria unificada del sistema y el estrés térmico. Los resultados de este estudio buscan proporcionar una guía de referencia técnica para que las MIPYMEs puedan tomar decisiones informadas sobre la integración de asistentes de Inteligencia Artificial locales, maximizando la eficiencia de su infraestructura existente y garantizando la confidencialidad de su información.

## 2. Marco Teórico
#### 2.1 Arquitectura de los Modelos de Lenguaje y Consumo de Memoria
Los Modelos de Lenguaje de Gran Escala (LLMs) modernos se basan predominantemente en la arquitectura _Transformer_, la cual utiliza mecanismos de atención para procesar secuencias de texto y predecir el siguiente _token_ (fragmentos de palabras). El tamaño y la capacidad de razonamiento de estos modelos están definidos por su cantidad de parámetros (pesos y sesgos de la red neuronal).

En su estado nativo, los parámetros de un LLM se almacenan en un formato de precisión de punto flotante de 16 bits (FP16). Esto implica que un modelo de 7 mil millones de parámetros (7B), como Mistral, requiere matemáticamente alrededor de 14 GB de memoria solo para cargar los pesos, además de memoria adicional para el _KV Cache_ (la memoria dinámica que el modelo usa para recordar el contexto de la conversación actual) [4]. Este requisito supera ampliamente las capacidades de la Memoria de Video (VRAM) de las tarjetas gráficas (GPUs) de gama de entrada, que típicamente oscilan entre los 4 GB y 8 GB.

#### 2.2 Cuantización y el Formato GGUF
Para cerrar la brecha entre los requisitos teóricos de los LLMs y el hardware convencional, se emplea la **cuantización**. Se trata de una técnica de compresión matemática que mapea los valores de los parámetros de alta precisión (16 bits) a representaciones de menor precisión, como enteros de 8 bits (INT8) o 4 bits (INT4).

Aunque esta reducción introduce un margen de pérdida de información (aumento de la perplejidad), esquemas de cuantización avanzados como _K-Quants_ (ej. `Q4_K_M`) logran un equilibrio óptimo: reducen el tamaño del modelo en memoria en más de un 60% conservando casi intacta su capacidad de razonamiento y coherencia gramatical [5]. Para este estudio, resulta fundamental el formato **GGUF** (_GPT-Generated Unified Format_), el cual está diseñado específicamente para permitir la ejecución eficiente de modelos cuantizados y facilitar el fraccionamiento de la carga de trabajo entre el procesador (CPU) y la tarjeta gráfica (GPU).

#### 2.3 Inferencia Local y "GPU Offloading" (Descarga a la GPU)
El motor de inferencia Ollama, construido sobre la librería _llama.cpp_, permite ejecutar modelos GGUF en hardware no especializado. Su principal ventaja técnica en equipos de recursos limitados es el _GPU Offloading_ o descarga parcial de capas.

Cuando el tamaño de un modelo cuantizado (incluyendo su contexto) supera la capacidad física de la VRAM (por ejemplo, los 4 GB de una arquitectura legacy), el motor carga tantas capas neuronales como sea posible en la memoria ultrarrápida de la GPU, y relega el resto a la Memoria de Acceso Aleatorio (RAM) del sistema [6]. Este proceso permite que el modelo se ejecute, pero introduce un cuello de botella arquitectónico: el ancho de banda del bus PCIe. La velocidad de generación (tokens por segundo) disminuye drásticamente al depender de la transferencia constante de datos entre la RAM, el procesador y la tarjeta de video.

#### 2.4 Estrés Térmico y _Thermal Throttling_
Finalmente, en equipos portátiles y estaciones de trabajo convencionales, el rendimiento sostenido de la inferencia de IA está fuertemente condicionado por la disipación térmica. Cuando la CPU y la GPU operan a su máxima capacidad durante el cálculo de matrices, la temperatura del encapsulado aumenta rápidamente. Para evitar daños en los semiconductores, los sistemas implementan _Thermal Throttling_ (estrangulamiento térmico), reduciendo las frecuencias de reloj al alcanzar umbrales críticos (usualmente entre 80°C y 90°C) [7]. Esta mitigación provoca que la velocidad de inferencia fluctúe o decaiga en tareas de procesamiento prolongadas (como resumir textos largos), una variable que a menudo se ignora en benchmarks de servidores, pero que es vital en entornos reales de MIPYMEs.


## 3. Metodología
Para evaluar el impacto de la cuantización en la inferencia local sobre equipos de recursos limitados, se diseñó un experimento empírico de naturaleza cuantitativa. Se desarrolló un sistema de _benchmarking_ automatizado capaz de medir la velocidad de generación y la telemetría de hardware en tiempo real durante la resolución de tareas administrativas simuladas.
#### 3.1 Entorno de Pruebas (Hardware y Software)
El experimento se llevó a cabo en una estación de trabajo portátil representativa del hardware de gama de entrada común en el sector MIPYME. Las especificaciones del sistema son las siguientes:

- **CPU:** AMD Ryzen 5 (Arquitectura Zen 2/3) con gráficos integrados desactivados para la prueba.    
- **Memoria RAM:** 16 GB de memoria unificada del sistema.    
- **GPU:** NVIDIA GeForce GTX 1050 con 4 GB de VRAM dedicada.    
- **Sistema Operativo:** **Ubuntu Linux** con controladores NVIDIA (v.535 o superior) y CUDA Toolkit 12.x para habilitar la aceleración por hardware. 
- **Motor de Inferencia:** Ollama, utilizando la API REST local expuesta en el puerto 11434.    

#### 3.2 Selección de Modelos
Se seleccionaron tres arquitecturas de LLMs de código abierto, priorizando modelos diseñados para eficiencia e instrucción (_instruct-tuned_). Para forzar distintos escenarios de consumo de memoria y descarga a GPU (_offloading_), se utilizaron las siguientes variantes cuantizadas en formato GGUF:

1. **Llama 3.2 (3B):** Evaluado en dos niveles de cuantización (`Q4_K_M` y `Q8_0`) para establecer una línea base de comparación directa sobre cómo la compresión afecta el consumo de RAM frente a VRAM en un mismo modelo.    
2. **Phi-3.5 Mini (3.8B):** Evaluado en `Q4_K_M`, seleccionado por su alta densidad de razonamiento y diseño orientado a dispositivos de borde (_edge devices_).    
3. **Gemma 3 (4B):** El modelo más reciente de Google en la categoría _lightweight_, incluido para evaluar la eficiencia de la arquitectura de atención de última generación en tareas de oficina.
4. **Mistral (7B v0.3):** Evaluado en `Q4_K_M`, actuando como el modelo de estrés para forzar deliberadamente el desbordamiento de los 4 GB de VRAM hacia la memoria del sistema.
    

#### 3.3 Diseño del Experimento y Tareas de Oficina

Para garantizar la validez ecológica del estudio, se descartaron los _prompts_ sintéticos tradicionales en favor de cuatro escenarios prácticos de ofimática, definidos mediante una temperatura de generación de `0` (para asegurar la determinancia de la respuesta):

- **Redacción:** Generación de un correo electrónico formal de 150 palabras.    
- **Resumen:** Compresión de un texto técnico de 70 palabras a un máximo de 5 oraciones.    
- **Clasificación:** Categorización estructurada de 5 asuntos de correo electrónico en niveles de urgencia.    
- **FAQ:** Respuesta concisa (máximo 100 palabras) sobre la automatización empresarial.    

#### 3.4 Sistema de Captura de Telemetría
Para evitar que el proceso de monitoreo interfiriera con la inferencia del LLM, se desarrolló un _script_ en Python (`benchmark.py`) que ejecuta un hilo concurrente (`MetricsSampler`). La metodología de captura siguió estos protocolos:

1. **Muestreo Paralelo:** Durante la generación de cada respuesta, el hilo secundario interrogó los sensores de hardware cada 0.5 segundos utilizando las bibliotecas `psutil` (para CPU y RAM) y `pynvml` (interfaz directa con el controlador NVIDIA para VRAM, uso de núcleo y temperatura de la GPU).    
2. **Métricas de Rendimiento:** La velocidad del modelo se midió en Tokens por Segundo (TPS), calculada mediante la división del conteo total de tokens evaluados (`eval_count`) entre la duración de la evaluación en nanosegundos (`eval_duration`), datos extraídos de la respuesta JSON de la API de Ollama.    
3. **Control de Sesgos (Warmup y Repeticiones):** Para evitar el sesgo del "arranque en frío" (donde el primer _prompt_ tarda más debido a la carga del modelo en memoria), el _script_ ejecutó una iteración de calentamiento (`warmup_model`) ignorada en los datos finales. Posteriormente, cada tarea fue ejecutada 3 veces por modelo, registrando los promedios y picos de consumo de recursos para mitigar anomalías térmicas o procesos de fondo del sistema operativo.

