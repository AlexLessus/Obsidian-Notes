
## Resumen
La adopción de la Inteligencia Artificial Generativa (IAG) en Micro, Pequeñas y Medianas Empresas (MIPYMEs) enfrenta barreras significativas debido a los costos recurrentes de infraestructura en la nube y los riesgos asociados a la privacidad de los datos. Como alternativa, los Modelos de Lenguaje de Gran Escala (LLMs) de código abierto permiten una ejecución local segura, aunque su rendimiento sobre hardware convencional o heredado no está suficientemente documentado. Este artículo presenta un benchmarking exhaustivo para evaluar la viabilidad técnica de desplegar LLMs locales en estaciones de trabajo con recursos limitados (GPU con 4 GB de VRAM). Utilizando el motor de inferencia Ollama y formatos de cuantización GGUF, se analizó el rendimiento de arquitecturas compactas y de tamaño medio, incluyendo Llama 3.2 (3B), Phi-3.5 Mini (3.8B) y Mistral (7B). Mediante un script automatizado de telemetría, se midieron los tokens por segundo (TPS), el consumo de memoria unificada (RAM/VRAM) y el estrés térmico durante la resolución de tareas administrativas estándar. El análisis de los resultados determina el umbral de viabilidad operativa donde la cuantización evita el desbordamiento de memoria, proporcionando una guía técnica para que las organizaciones integren asistentes de IA garantizando la soberanía de sus datos sin requerir inversión en hardware de alto rendimiento.

**Palabras clave:** Benchmarking, Inteligencia Artificial Local, Cuantización, LLM, MIPYMEs.

---
## Abstract
The adoption of Generative Artificial Intelligence (GenAI) in Micro, Small, and Medium Enterprises (MSMEs) faces significant barriers due to recurring cloud infrastructure costs and data privacy risks. As an alternative, open-source Large Language Models (LLMs) allow for secure local execution, although their performance on conventional or legacy hardware is not sufficiently documented. This paper presents a comprehensive benchmark to evaluate the technical feasibility of deploying local LLMs on workstations with limited resources (4 GB VRAM GPU). Using the Ollama inference engine and GGUF quantization formats, the performance of compact and mid-sized architectures, including Llama 3.2 (3B), gemma3 (4b), Phi-3.5 Mini (3.8B), and Mistral (7B), was analyzed. Through an automated telemetry script, tokens per second (TPS), unified memory consumption (RAM/VRAM), and thermal stress were measured during the execution of standard administrative tasks. The analysis of the results determines the operational viability threshold where quantization prevents memory overflow, providing a technical guide for organizations to integrate AI assistants ensuring data sovereignty without requiring investment in high-performance hardware.

**Keywords:** Benchmarking, Local Artificial Intelligence, Quantization, LLM, MSMEs.

## 1. Introducción
La rápida evolución de la Inteligencia Artificial Generativa (IAG) ha redefinido los paradigmas de productividad y automatización en el entorno corporativo. A través de la implementación de Modelos de Lenguaje de Gran Escala (LLMs, por sus siglas en inglés), las organizaciones han logrado optimizar tareas administrativas, redactar correos electrónicos, clasificar información y generar resúmenes con una eficiencia sin precedentes. Sin embargo, el modelo de despliegue dominante se basa en Software como Servicio (SaaS) alojado en la nube comercial. Si bien este enfoque ofrece capacidades de cómputo masivas, presenta dos barreras críticas para las MIPYMEs: los elevados costos recurrentes por licencias de usuario y la pérdida de la soberanía de los datos [1, 2]. Para muchas de estas organizaciones, enviar información financiera, legal o confidencial a servidores externos representa un riesgo de privacidad inasumible.

Como respuesta a estas limitantes, el ecosistema de código abierto ha democratizado el acceso a LLMs altamente capaces que pueden ser ejecutados de manera local. No obstante, la barrera de entrada se ha desplazado del pago de suscripciones a la adquisición de infraestructura de hardware. En su estado nativo, la inferencia de un modelo promedio requiere aceleradores gráficos (GPUs) de gama alta con amplias capacidades de Memoria de Acceso Aleatorio de Video (VRAM), equipos que escapan al presupuesto de la mayoría de las MIPYMEs, cuya infraestructura tecnológica presenta bajos niveles de inversión y adopción de herramientas digitales avanzadas [2], lo que implica que la mayoría opera con equipos convencionales de recursos limitados.

Para mitigar este cuello de botella, la comunidad científica e ingenieril ha perfeccionado técnicas de compresión de modelos, destacando la cuantización de pesos. Esta técnica, popularizada a través de formatos como GGUF, permite reducir la precisión matemática de los parámetros del modelo —típicamente de punto flotante de 16 bits (FP16) a representaciones de 4 u 8 bits— disminuyendo drásticamente la huella de memoria requerida sin una degradación proporcional en la coherencia de las respuestas [3]. A pesar de estos avances teóricos, existe una brecha significativa en la literatura respecto a la evaluación empírica de estos modelos cuantizados operando bajo las severas restricciones térmicas y de memoria de equipos convencionales (por ejemplo, sistemas limitados a 4 GB de VRAM).

El presente artículo tiene como objetivo principal realizar un _benchmarking_ técnico para evaluar el rendimiento y viabilidad operativa de cuatro arquitecturas de LLMs de código abierto (Llama 3.2 de 3B, Gemma3 de 4b, Phi-3.5 Mini de 3.8B y Mistral de 7B parámetros) ejecutadas localmente en hardware de entrada. Mediante la captura automatizada de telemetría de hardware, se analiza la relación entre el nivel de cuantización, la velocidad de inferencia (tokens por segundo), el desbordamiento hacia la memoria unificada del sistema y el estrés térmico. Los resultados de este estudio buscan proporcionar una guía de referencia técnica para que las MIPYMEs puedan tomar decisiones informadas sobre la integración de asistentes de Inteligencia Artificial locales, maximizando la eficiencia de su infraestructura existente y garantizando la confidencialidad de su información.

## 2. Marco Teórico
#### 2.1 Arquitectura de los Modelos de Lenguaje y Consumo de Memoria
Los Modelos de Lenguaje de Gran Escala (LLMs) modernos se basan predominantemente en la arquitectura _Transformer_[4], la cual utiliza mecanismos de atención para procesar secuencias de texto y predecir el siguiente _token_ (fragmentos de palabras). El tamaño y la capacidad de razonamiento de estos modelos están definidos por su cantidad de parámetros (pesos y sesgos de la red neuronal).

En su estado nativo, los parámetros de un LLM se almacenan en un formato de precisión de punto flotante de 16 bits (FP16). Esto implica que un modelo de 7 mil millones de parámetros (7B), como Mistral, requiere matemáticamente alrededor de 14 GB de memoria solo para cargar los pesos, además de memoria adicional para el _KV Cache_ (la memoria dinámica que el modelo usa para recordar el contexto de la conversación actual) . Este requisito supera ampliamente las capacidades de la Memoria de Video (VRAM) de las tarjetas gráficas (GPUs) de gama de entrada, que típicamente oscilan entre los 4 GB y 8 GB.

#### 2.2 Cuantización y el Formato GGUF
Para cerrar la brecha entre los requisitos teóricos de los LLMs y el hardware convencional, se emplea la **cuantización**. Se trata de una técnica de compresión matemática que mapea los valores de los parámetros de alta precisión (16 bits) a representaciones de menor precisión, como enteros de 8 bits (INT8) o 4 bits (INT4).

Aunque esta reducción introduce un margen de pérdida de información (aumento de la perplejidad), esquemas de cuantización avanzados como _K-Quants_ (ej. `Q4_K_M`) logran un equilibrio óptimo: reducen el tamaño del modelo en memoria en más de un 60% conservando casi intacta su capacidad de razonamiento y coherencia gramatical [5]. Para este estudio, resulta fundamental el formato **GGUF** (_GPT-Generated Unified Format_), el cual está diseñado específicamente para permitir la ejecución eficiente de modelos cuantizados y facilitar el fraccionamiento de la carga de trabajo entre el procesador (CPU) y la tarjeta gráfica (GPU).

#### 2.3 Inferencia Local y "GPU Offloading" (Descarga a la GPU)
El motor de inferencia Ollama, construido sobre la librería _llama.cpp_, permite ejecutar modelos GGUF en hardware no especializado. Su principal ventaja técnica en equipos de recursos limitados es el _GPU Offloading_ o descarga parcial de capas.

Cuando el tamaño de un modelo cuantizado (incluyendo su contexto) supera la capacidad física de la VRAM (por ejemplo, los 4 GB de una arquitectura legacy), el motor carga tantas capas neuronales como sea posible en la memoria ultrarrápida de la GPU, y relega el resto a la Memoria de Acceso Aleatorio (RAM) del sistema [6]. Este proceso permite que el modelo se ejecute, pero introduce un cuello de botella arquitectónico: el ancho de banda del bus PCIe. La velocidad de generación (tokens por segundo) disminuye drásticamente al depender de la transferencia constante de datos entre la RAM, el procesador y la tarjeta de video.

#### 2.4 Estrés Térmico y _Thermal Throttling_
Finalmente, en equipos portátiles y estaciones de trabajo convencionales, el rendimiento sostenido de la inferencia de IA está fuertemente condicionado por la disipación térmica. Cuando la CPU y la GPU operan a su máxima capacidad durante el cálculo de matrices, la temperatura del encapsulado aumenta rápidamente. Para evitar daños en los semiconductores, los sistemas implementan _Thermal Throttling_ (estrangulamiento térmico), reduciendo las frecuencias de reloj al alcanzar los límites operativos del procesador [7], una variable frecuentemente ignorada en benchmarks de servidores pero determinante en hardware de consumo. Esta mitigación provoca que la velocidad de inferencia fluctúe o decaiga en tareas de procesamiento prolongadas (como resumir textos largos), una variable que a menudo se ignora en benchmarks de servidores, pero que es vital en entornos reales de MIPYMEs.


## 3. Metodología
Para evaluar el impacto de la cuantización en la inferencia local sobre equipos de recursos limitados, se diseñó un experimento empírico de naturaleza cuantitativa. Se desarrolló un sistema de _benchmarking_ automatizado capaz de medir la velocidad de generación y la telemetría de hardware en tiempo real durante la resolución de tareas administrativas simuladas.
#### 3.1 Entorno de Pruebas (Hardware y Software)
El experimento se llevó a cabo en una estación de trabajo portátil representativa del hardware de gama de entrada común en el sector MIPYME. Las especificaciones del sistema son las siguientes:

- **CPU:** AMD Ryzen 5 4600H (Arquitectura Zen 2/3) con gráficos integrados desactivados para la prueba.    
- **Memoria RAM:** 16 GB de memoria unificada del sistema.    
- **GPU:** NVIDIA GeForce GTX 1050 con 4 GB de VRAM dedicada.    
- **Sistema Operativo:** **Ubuntu Linux** con controladores NVIDIA (v.535 o superior) y CUDA Toolkit 12.x para habilitar la aceleración por hardware. 
- **Motor de Inferencia:** Ollama, utilizando la API REST local expuesta en el puerto 11434.    

#### 3.2 Selección de Modelos
Se seleccionaron cuatro arquitecturas de LLMs de código abierto, priorizando modelos diseñados para eficiencia e instrucción (_instruct-tuned_). Para forzar distintos escenarios de consumo de memoria y descarga a GPU (_offloading_), se utilizaron las siguientes variantes cuantizadas en formato GGUF:

1. **Llama 3.2 (3B):** Seleccionado por ser construido para adaptarse a dispositivos moviles y de borde, manteniendo un gran rendimiento.
2. **Phi-3.5 Mini (3.8B):** Evaluado en `Q4_K_M`, seleccionado por su alta densidad de razonamiento y diseño orientado a dispositivos de borde (_edge devices_).    
3. **Gemma 3 (4B):** El modelo más reciente de Google en la categoría _lightweight_, incluido para evaluar la eficiencia de la arquitectura de atención de última generación en tareas de oficina.
4. **Mistral (7B v0.3):** Evaluado en `Q4_K_M`, actuando como el modelo de estrés para forzar deliberadamente el desbordamiento de los 4 GB de VRAM hacia la memoria del sistema.

| Modelo       | Parámetros | Cuantización | Tamaño aprox. |
| ------------ | ---------- | ------------ | ------------- |
| Llama 3.2    | 3B         | Q4_K_M       | ~2 GB         |
| Phi-3.5 Mini | 3.8B       | Q4_K_M       | ~2.4 GB       |
| Gemma 3      | 4B         | Q4_K_M       | ~3 GB         |
| Mistral      | 7B         | Q4_K_M       | ~4.5 GB       |

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

## 4. Resultados y Discusión
El análisis empírico generó datos consistentes a través de las diversas iteraciones de pruebas de ofimática. A continuación, se desglosa el impacto de la arquitectura y la cuantización sobre las métricas de rendimiento, memoria y temperatura del sistema.

#### 4.1 Rendimiento de Inferencia (Tokens por Segundo)
La velocidad de generación es el indicador principal de usabilidad para un usuario final (MIPYME). Considerando que la velocidad de lectura humana promedio de 6 tokens por segundo (TPS)[8], los resultados demuestran que la mayoría de los modelos evaluados en formato GGUF superan este umbral en el hardware de prueba.

- **Llama 3.2 (3B):** Registró el mejor rendimiento general con un promedio de **22.62 TPS** sostenidos en todas las tareas, alcanzando picos de 23.32 TPS en tareas de clasificación corta.
- **Gemma 3 (4B) y Phi-3.5 (3.8B):** Presentaron un rendimiento estadísticamente similar en términos de velocidad, con **17.93 TPS** y **17.71 TPS** respectivamente.
- **Mistral (7B):** Como se anticipaba debido a su mayor número de parámetros, el rendimiento decayó significativamente a **9.18 TPS**. Aunque sigue siendo utilizable, la latencia en tareas largas (como la redacción de correos) reduce la interactividad del asistente.

#### 4.2 Consumo de Memoria y _GPU Offloading_
El análisis del consumo de Memoria Unificada (RAM) y Video (VRAM) valida la hipótesis sobre el cuello de botella de la arquitectura _legacy_ de 4 GB.

Durante las pruebas, todos los modelos lograron acomodar sus capas críticas en la GPU, registrando un uso de VRAM promedio estabilizado entre 2.3 GB y 2.6 GB. Sin embargo, la diferencia radicó en la dependencia de la memoria del sistema (RAM) para el _offloading_:

- **Eficiencia Óptima:** Llama 3.2 y Phi-3.5 demostraron una gestión eficiente, requiriendo un promedio de ~4.2 GB y ~4.5 GB de RAM respectivamente.
- **Anomalía de Memoria:** El modelo **Gemma 3 (4B)** exigió un promedio de 7.5 GB de RAM, con **picos de hasta 8.5 GB** de consumo en el sistema. Para una MIPYME con equipos de solo 8 GB de RAM totales, la elección de este modelo causaría un colapso del sistema operativo (Paging/Swap).
	Este comportamiento resulta contraintuitivo dado que Gemma 3 (4B) posee menos parámetros que Mistral (7B), modelo que registró un consumo de RAM considerablemente menor. Este hallazgo sugiere que el tamaño en parámetros no es el único determinante del consumo de memoria en tiempo de inferencia.
- **El Cuello de Botella del Bus:** En el caso de Mistral (7B), la telemetría reveló un uso promedio de la GPU de apenas **35.5%**, en contraste con el 56% de Llama 3.2. Esta caída en la utilización gráfica, combinada con un aumento en el uso del CPU (40.6%), demuestra matemáticamente el impacto del _GPU Offloading_: la tarjeta de video pasa la mayor parte del tiempo inactiva, esperando a que los datos del modelo se transfieran desde la RAM a través del bus PCIe.
    

#### 4.3 Comportamiento Térmico y Estrangulamiento (_Throttling_)
La viabilidad operativa en estaciones de trabajo portátiles está fuertemente limitada por la disipación térmica. La temperatura de la NVIDIA GTX 1050 se mantuvo estable y segura en un promedio de **~64 °C** para todos los modelos, evidenciando que el acelerador gráfico no fue llevado a su límite térmico en ningún momento.

Por el contrario, el procesador AMD Ryzen 5 experimentó cargas térmicas severas, alcanzando temperaturas operativas promedio de **91.9 °C** con Llama 3.2, y picos críticos de hasta **96.8 °C** sostenidos durante la ejecución de Phi-3.5. Estas temperaturas, cercanas al límite operativo del fabricante (105 °C), sugieren que en implementaciones prolongadas —como la indexación masiva de documentos— el sistema sufrirá inminentemente de _thermal throttling_ (estrangulamiento térmico), lo que degradará progresivamente los TPS reportados.

![[figura1_tps.png]]
>Figura 1. Velocidad de inferencia promedio. Las barras de error indican la desviación estándar entre las distintas tareas ofimáticas.

![[figura2_memoria.png]]
>Figura 2. Distribución de carga de memoria(Offloading)

![[figura3_temperatura.png]]
>Figura 3. Perfil Térmico promedio durante la inferencia

## 5. Discusión
Los resultados preliminares obtenidos permiten contrastar las hipótesis de trabajo con evidencia empírica directa y derivar implicaciones prácticas para el contexto MIPYME. A continuación se interpretan los hallazgos en función de las cuatro dimensiones analizadas: velocidad de inferencia, gestión de memoria, comportamiento térmico y viabilidad operativa.

#### 5.1 Viabilidad operativa: el umbral de interactividad como criterio funcional

El criterio de usabilidad adoptado en este estudio toma como referencia la velocidad de lectura humana promedio, estimada en 250 palabras por minuto según Rayner et al. [8], lo que equivale a aproximadamente 6 tokens por segundo al aplicar el factor de conversión palabras-token para el idioma español. Este umbral determina si un asistente de IA puede sostener una interacción fluida sin que la latencia de generación resulte perceptible para el usuario.

Bajo este criterio, los resultados son favorables para la mayoría de los modelos evaluados. Llama 3.2 (3B) registró el mayor rendimiento con 22.62 TPS promedio, superando el umbral de interactividad en aproximadamente 3.8 veces. Gemma 3 (4B) y Phi-3.5 Mini (3.8B) presentaron rendimientos estadísticamente similares, con 17.93 y 17.71 TPS respectivamente, ambos muy por encima del umbral. Estos resultados sugieren que los modelos compactos cuantizados en formato Q4_K_M son operativamente viables para tareas ofimáticas en hardware con 4 GB de VRAM, sin requerir inversión adicional en infraestructura de cómputo.

Mistral (7B), sin embargo, registró 9.18 TPS, lo que si bien supera el umbral mínimo, representa una reducción significativa respecto a los modelos compactos. En tareas de redacción extensa, donde la generación de respuestas largas amplifica el tiempo de espera, esta latencia puede comprometer la percepción de fluidez en escenarios de uso interactivo. Para organizaciones con recursos limitados donde la productividad por hora-empleado es un factor crítico, esta diferencia no es trivial.

#### 5.2 El cuello de botella arquitectónico del GPU Offloading

El caso de Mistral (7B) ilustra con precisión el fenómeno de degradación de rendimiento derivado del GPU Offloading documentado en la literatura [6]. La telemetría registró un uso promedio de GPU de apenas 35.5%, en contraste con el 56% de Llama 3.2 (3B), acompañado de un incremento en el uso de CPU del 40.6%. Esta divergencia evidencia que la tarjeta gráfica, lejos de estar siendo aprovechada al máximo, permanece ociosa durante la mayor parte del tiempo de inferencia, esperando el trasvase de datos desde la RAM del sistema a través del bus PCIe.

Este cuello de botella es inherente a la arquitectura de los sistemas con VRAM reducida: cuando el tamaño del modelo cuantizado supera la capacidad física de la memoria de video, el motor de inferencia fracciona la carga neuronal entre GPU y RAM, introduciendo una latencia de transferencia constante que no existe en configuraciones donde el modelo cabe íntegramente en VRAM. La caída de velocidad de Mistral (7B) no es, por tanto, consecuencia de una limitación del modelo en sí, sino de una incompatibilidad estructural entre el tamaño del modelo y la capacidad del acelerador disponible.

Este hallazgo tiene implicaciones directas para la toma de decisiones en MIPYMEs: la selección de un modelo de 7B parámetros en hardware con 4 GB de VRAM no representa una solución óptima costo-beneficio, dado que el incremento en capacidad de razonamiento no se traduce en una mejora proporcional de la velocidad de interacción, sino en una penalización neta sobre la fluidez del asistente.

#### 5.3 Anomalía de consumo de memoria en arquitecturas de contexto extendido

El hallazgo más contraintuitivo del estudio es el comportamiento de Gemma 3 (4B) en cuanto a su consumo de RAM del sistema, que registró picos de hasta 8.5 GB a pesar de contar con menos parámetros que Mistral (7B), modelo que presentó un perfil de memoria considerablemente más contenido.

Esta aparente paradoja tiene una explicación arquitectónica documentada en el reporte técnico oficial del modelo. Gemma 3 implementa una ventana de contexto extendida de al menos 128,000 tokens, junto con modificaciones en la proporción de capas de atención local y global diseñadas específicamente para gestionar el KV-Cache, que tiende a crecer de manera explosiva en contextos largos [9]. Si bien estas modificaciones representan una ventaja significativa en escenarios de procesamiento de documentos extensos, su efecto secundario en hardware con RAM limitada es un incremento sustancial en el consumo de memoria del sistema durante la inferencia, independientemente del nivel de cuantización aplicado al modelo.

Este hallazgo establece una distinción metodológica importante: el número de parámetros de un modelo no es un predictor suficiente de su huella de memoria en tiempo de ejecución. El perfil real de consumo depende también de la arquitectura de atención, el tamaño de la ventana de contexto y la estrategia de gestión del KV-Cache implementada por el modelo. Para una MIPYME que opera con equipos de 8 GB de RAM total, la elección de Gemma 3 (4B) bajo carga de trabajo moderada podría derivar en saturación de la memoria virtual del sistema operativo (swapping), comprometiendo no solo el rendimiento del asistente, sino la estabilidad general del equipo.

#### 5.4 Estrés térmico como limitante operativa real en hardware portátil

A diferencia de los benchmarks realizados en servidores —donde la disipación térmica se gestiona mediante sistemas de refrigeración activa de alta capacidad— los resultados obtenidos en el equipo portátil de prueba revelan una limitación crítica que la literatura especializada suele ignorar: el estrangulamiento térmico como factor de degradación del rendimiento sostenido.

La temperatura de la GPU (NVIDIA GTX 1050) se mantuvo estable en un promedio de ~64°C durante todas las pruebas, indicando que el acelerador gráfico operó dentro de márgenes seguros y sin alcanzar sus límites térmicos. Sin embargo, el procesador AMD Ryzen 5 exhibió un comportamiento significativamente más preocupante, alcanzando temperaturas promedio de 91.9°C con Llama 3.2 y picos críticos sostenidos de 96.8°C durante la ejecución de Phi-3.5 Mini.

Estas temperaturas son cercanas al límite operativo declarado por el fabricante y activan los mecanismos de estrangulamiento térmico descritos por Sulaiman [7], que regulan el entorno térmico reduciendo la frecuencia de reloj del procesador para prevenir daños en los semiconductores. El efecto observable de este mecanismo es una reducción progresiva de los TPS reportados en tareas de larga duración, lo que introduce una variable de degradación que no se manifiesta en pruebas cortas pero resulta relevante en implementaciones reales de uso continuo.

Para las MIPYMEs, esto implica que los benchmarks de velocidad de inferencia deben interpretarse como rendimiento de corto plazo, no como indicadores de velocidad sostenida. En escenarios de uso intensivo —como el procesamiento masivo de documentos, la indexación de archivos o sesiones de trabajo prolongadas— el rendimiento efectivo será menor al reportado en condiciones de prueba controladas. Las organizaciones que adopten esta tecnología deberán considerar estrategias de gestión térmica: pausas programadas entre solicitudes, optimización del entorno físico (ventilación adecuada del equipo) o la implementación de perfiles de energía que equilibren rendimiento y temperatura.

#### 5.5 Implicaciones para la adopción de IA local en MIPYMEs

La integración de los hallazgos anteriores permite articular una guía técnica concreta para organizaciones con infraestructura equivalente al hardware de prueba utilizado en este estudio.

Los modelos compactos en el rango de 3 a 4 mil millones de parámetros representan el punto de equilibrio óptimo entre velocidad de inferencia, consumo de memoria y estabilidad térmica para hardware con 4 GB de VRAM y 16 GB de RAM. Dentro de este rango, Llama 3.2 (3B) demostró la combinación más favorable de todos los indicadores evaluados.

La selección de modelos no debe fundamentarse exclusivamente en el conteo de parámetros, sino en el perfil de consumo de memoria en tiempo de ejecución sobre el hardware objetivo, dado que arquitecturas como la de Gemma 3 pueden exhibir comportamientos anómalos en equipos con recursos de RAM limitados.

Finalmente, el factor térmico constituye la limitante operativa más frecuentemente ignorada en la literatura pero más relevante en implementaciones reales. Su consideración es indispensable para garantizar la viabilidad a largo plazo de los asistentes de IA locales en el contexto de equipos portátiles convencionales.

## Conclusiones
La presente investigación evaluó la viabilidad técnica de ejecutar Modelos de Lenguaje de Gran Escala (LLMs) cuantizados en formato GGUF utilizando hardware de gama de entrada, un entorno representativo de la infraestructura tecnológica disponible en las Micro, Pequeñas y Medianas Empresas (MIPYMEs). A partir del análisis de telemetría, se concluye que la implementación de asistentes de Inteligencia Artificial locales y seguros es operativamente viable sin necesidad de inversiones en aceleradores gráficos de alto costo, siempre y cuando se realice una selección arquitectónica rigurosa.

De los datos empíricos obtenidos, se desprenden las siguientes conclusiones clave:
- **Viabilidad Operativa y Recomendación:** Las arquitecturas en el rango de los 3 mil millones de parámetros representan el punto de equilibrio óptimo para hardware con 4 GB de VRAM. **Llama 3.2 (3B)** se posiciona como la opción más robusta para entornos ofimáticos, entregando la mayor velocidad de inferencia (promedio de 22.6 TPS) con una gestión de memoria predecible que no satura los recursos del sistema.
- **El Límite del _GPU Offloading_:** La ejecución de modelos de 7 mil millones de parámetros, como **Mistral (7B)**, demuestra que aunque el motor Ollama es capaz de fraccionar la carga, la dependencia del bus PCIe para acceder a la RAM del sistema crea un cuello de botella severo. La caída de la velocidad a 9.1 TPS y la infrautilización de la GPU (35%) indican que, aunque el modelo es funcional, penaliza la interactividad en tiempo real.
- **Riesgos de Memoria en Arquitecturas Recientes:** El comportamiento anómalo de **Gemma 3 (4B)**, el cual exigió picos de hasta 8.5 GB de RAM del sistema, subraya que una menor cantidad de parámetros no garantiza automáticamente una baja huella de memoria. Para equipos limitados a 8 GB o 16 GB de RAM, este modelo representa un riesgo de colapso del sistema operativo por saturación de memoria virtual (_swapping_).
- **Limitantes Térmicas en Equipos Portátiles:** A diferencia de los servidores en la nube, el hardware de consumo es altamente susceptible al estrés térmico. El registro de temperaturas críticas (superiores a 95 °C) en el procesador durante la evaluación de modelos como **Phi-3.5** indica que las tareas de inferencia continua y masiva (ej. procesamiento por lotes de documentos) requerirán estrategias activas de enfriamiento o pausas programadas para evitar la degradación del rendimiento por _thermal throttling_.

En conclusión, la adopción de IA generativa de código abierto permite a las organizaciones mantener la **absoluta soberanía y privacidad de sus datos**. Para futuras líneas de investigación, se sugiere evaluar el impacto del tamaño de la ventana de contexto (_KV Cache_) en el desbordamiento de memoria, así como el uso de Unidades de Procesamiento Neuronal (NPUs) integradas en procesadores de nueva generación como alternativa a las GPUs convencionales.

## Referencias
[1] J. G. Córdova Rodríguez y R. Jiménez León, "Barreras que Frenan 
    la Adopción Tecnológica en la Mercadotecnia de las Pymes: Una 
    Revisión de la Literatura Contemporánea," Revista de Investigación 
    Académica sin Frontera, núm. 39, 2023. 
    doi: 10.46589/rdiasf.vi39.554
[2] E. Buenrostro Mercado, "Propuesta de adopción de tecnologías 
    asociadas a la industria 4.0 en las pymes mexicanas," 
    Entreciencias: Diálogos en la Sociedad del Conocimiento, 
    vol. 10, no. 24, pp. 1–19, 2022. 
    doi: 10.22201/enesl.20078064e.2022.24.81347
[3] T. Dettmers, M. Lewis, Y. Belkada y L. Zettlemoyer, "LLM.int8(): 8-bit Matrix Multiplication for Transformers at Scale," arXiv:2208.07339, 2022. 
[4] A. Vaswani et al., "Attention is all you need," Advances in Neural Information Processing Systems, vol. 30, 2017.
[5] E. Frantar, S. Ashkboos, T. Hoefler y D. Alistarh, "GPTQ: Accurate Post-Training Quantization for Generative Pre-trained Transformers," arXiv:2210.17323, 2022.
[6] G. Gerganov, llama.cpp [Software], GitHub, 2023. https://github.com/ggerganov/llama.cpp
[7] D. R. Sulaiman, "Microprocessors Thermal Challenges for Portable 
    and Embedded Systems Using Thermal Throttling Technique," 
    Procedia Computer Science, vol. 3, pp. 1023–1032, 2011. 
    doi: 10.1016/j.procs.2010.12.168
[8] Rayner, K., Schotter, E. R., Masson, M. E., Potter, M. C., & Treiman, R. (2016). _So Much to Read, So Little Time: How Do We Read, and Can Speed Reading Help?_ Psychological Science in the Public Interest, 17(1), 4–34. doi: 10.1177/1529100615623267
(agregar a pie de pagina
250 palabras/min ÷ 60 segundos = 4.16 palabras/segundo
4.16 ÷ 0.75 = ~5.5 tokens/segundo en inglés
4.16 ÷ 0.60 = ~6.9 tokens/segundo en español
)
[9] Gemma Team, Google DeepMind, "Gemma 3 Technical Report," 
    arXiv:2503.19786 [cs.CL], Mar. 2025. 
    [En línea]. Disponible: https://arxiv.org/abs/2503.19786