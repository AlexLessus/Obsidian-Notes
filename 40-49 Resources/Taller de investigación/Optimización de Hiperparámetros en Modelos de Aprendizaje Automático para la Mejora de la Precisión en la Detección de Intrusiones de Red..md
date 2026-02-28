*Alexis De Jesus Perez Carmona*
# Antecedentes
#### **Contexto Global y Tecnológico**
Históricamente, los Sistemas de Detección de Intrusiones (IDS) se basaban en firmas (patrones conocidos), lo cual los hacía inútiles ante ataques nuevos o de "día cero". En años recientes (2020-2025), la literatura científica ha volcado su interés hacia el **Aprendizaje Automático (Machine Learning)** como la herramienta definitiva para identificar anomalías en el tráfico de red mediante el análisis de grandes volúmenes de datos.

#### **Evolución de la Investigación en Ciberseguridad**
Investigaciones actuales señalan que el uso de algoritmos como _Random Forest_, _XGBoost_ y _Redes Neuronales Convolucionales_ ha permitido alcanzar niveles de precisión superiores al 95% en la detección de ataques tipo DoS (Denegación de Servicio) e infiltraciones. Sin embargo, un reto persistente en la disciplina es la alta tasa de "falsos positivos", lo que motiva la necesidad de realizar investigaciones aplicadas que se centren en la **optimización de modelos** para entornos específicos.

#### **Motivación y Contexto Local**
El presente proyecto surge del interés personal por profundizar en el dominio del **Machine Learning** y el manejo de datos masivos, buscando aplicar los conocimientos adquiridos en la carrera de Ingeniería en Sistemas Computacionales para resolver problemas críticos de ciberseguridad.

A nivel institucional, el **Instituto Tecnológico de Ciudad Guzmán** cuenta con una red académica que soporta a miles de usuarios; no obstante, la falta de diagnósticos locales y herramientas personalizadas de monitoreo de red representa un área de oportunidad técnica. Esta investigación no solo busca consolidar habilidades profesionales en el desarrollo de IA, sino también proponer una base tecnológica que pueda ser integrada en la red de estudiantes de la institución para prevenir accesos no autorizados y garantizar la integridad de la información.

# Definición del Problema
A pesar del avance en las tecnologías de seguridad informática, las redes académicas como la del **Instituto Tecnológico de Ciudad Guzmán** enfrentan un incremento constante en intentos de intrusión y tráfico malicioso que comprometen la integridad de la información institucional. Los Sistemas de Detección de Intrusiones (IDS) tradicionales, basados en firmas estáticas, resultan insuficientes ante ataques dinámicos y de día cero.

Si bien el **Aprendizaje Automático (Machine Learning)** ha surgido como una solución prometedora, la mayoría de los modelos implementados carecen de una **optimización de hiperparámetros** específica para el contexto de redes académicas, lo que deriva en una alta tasa de falsos positivos y una baja precisión en la detección de ataques complejos como infiltraciones y botnets. Por lo tanto, el problema central radica en la falta de modelos de detección de intrusiones técnicamente optimizados que garanticen una alta eficiencia en la identificación de amenazas sin interrumpir el flujo legítimo de datos en una red estudiantil.

### **Pregunta de investigación:**
> ¿De qué manera la aplicación de técnicas de optimización de hiperparámetros en modelos de Aprendizaje Automático mejora la precisión y reduce los falsos positivos en la detección de intrusiones dentro de una infraestructura de red académica?

# Justificación
La presente investigación es de vital importancia debido a la creciente dependencia tecnológica en el ámbito educativo y la vulnerabilidad de los datos sensibles manejados en instituciones de nivel superior. La relevancia de este estudio se fundamenta en tres ejes principales:

- **Utilidad Técnica e Innovación:** El proyecto busca trascender el uso básico de algoritmos de clasificación mediante la implementación de **optimización Bayesiana**, lo cual representa una innovación y desarrollo tecnológico alineado con las competencias de la carrera de Ingeniería en Sistemas Computacionales.
- **Beneficio Institucional:** El resultado de esta investigación proporciona una base tecnológica que puede ser adaptada para fortalecer la seguridad de la red de estudiantes del **ITCG**, permitiendo una respuesta más ágil ante incidentes de ciberseguridad y protegiendo el ecosistema digital de la comunidad.

# Definición de Objetivos
El propósito de estos objetivos es transformar tu protocolo en un proyecto de **investigación aplicada o innovación tecnológica**.
#### **Objetivo General**
**Desarrollar** un sistema de detección de intrusiones de red basado en algoritmos de **Aprendizaje Automático (Machine Learning)**, optimizado mediante técnicas de **Búsqueda Bayesiana**, para mejorar la precisión en la identificación de tráfico malicioso y reducir la tasa de falsos positivos en entornos de redes académicas.

#### **Objetivos Específicos**
- **Analizar** y preprocesar el dataset **CIC-IDS2017** o similar, aplicando técnicas de limpieza y selección de características para identificar las variables más significativas en la detección de ataques.
- **Implementar** modelos de clasificación supervisada, tales como **Random Forest** y **XGBoost**, utilizando el lenguaje de programación **Python** y librerías especializadas en ciencia de datos.
- **Aplicar** métodos de **Optimización Bayesiana** para el ajuste fino de hiperparámetros, buscando maximizar el rendimiento del modelo frente a métodos de búsqueda tradicionales.
- **Evaluar** el desempeño del sistema mediante métricas estadísticas de **Precisión ($Precision$)**, **Exhaustividad ($Recall$)** y **Puntaje F1 ($F1\text{-}Score$)**, validando la eficacia del modelo optimizado.
- **Presentar** y defender los resultados obtenidos ante un sínodo académico, demostrando la viabilidad técnica y el alcance de la investigación en el contexto de la ciberseguridad institucional.

# **Hipótesis**
> "La implementación de un modelo de detección de intrusiones basado en **Random Forest** u **XGBoost**, optimizado mediante **Optimización Bayesiana**, permite alcanzar una precisión ($Accuracy$) superior al **95%** y una reducción significativa en los falsos positivos en comparación con modelos configurados con hiperparámetros por defecto".

# **Supuestos**
- **Disponibilidad de Datos:** Se asume que los datasets de tráfico de red seleccionados representan fielmente los patrones de ataque modernos y el tráfico legítimo de una red institucional.
- **Capacidad de Cómputo:** Se cuenta con los recursos de procesamiento necesarios (entornos locales o en la nube) para ejecutar los ciclos de entrenamiento y optimización requeridos por los algoritmos.
- **Relevancia Tecnológica:** El uso de herramientas de código abierto como **Scikit-learn** u **Optuna** proporciona un marco de validación robusto y reproducible para la investigación.
# Marco teórico
### 1. Sistemas de Detección de Intrusos (IDS)
Un IDS es una herramienta de seguridad que monitorea el tráfico de red en busca de actividades sospechosas o violaciones de políticas. En la actualidad, se clasifican principalmente en dos paradigmas:
- **Detección basada en firmas:** Identifica amenazas comparando el tráfico con una base de datos de patrones conocidos. Su limitación principal es la incapacidad de detectar ataques de "día cero" (amenazas nuevas).
- **Detección basada en anomalías:** Utiliza un perfil de comportamiento "normal" de la red y marca cualquier desviación significativa como una posible intrusión. Es aquí donde el **Aprendizaje Automático** cobra relevancia.

### 2. Machine Learning Aplicado a la Ciberseguridad
El aprendizaje automático permite a los sistemas "aprender" de los datos sin ser programados explícitamente para cada escenario. Para la detección de intrusos, se utilizan algoritmos de **Clasificación Supervisada**:

- **Random Forest (Bosques Aleatorios):** Un conjunto de árboles de decisión que mejora la precisión y evita el sobreajuste (_overfitting_).
- **XGBoost (Extreme Gradient Boosting):** Algoritmo basado en árboles de decisión con aumento de gradiente, altamente eficiente para grandes volúmenes de datos como los registros de red.
- **Redes Neuronales Artificiales (ANN):** Modelos inspirados en la estructura biológica que pueden capturar relaciones no lineales complejas en el tráfico de datos.
### 3. Optimización de Hiperparámetros
Los **hiperparámetros** son configuraciones externas al modelo (como la profundidad de un árbol o la tasa de aprendizaje) que no se aprenden de los datos, sino que deben ser definidos antes del entrenamiento.

#### **Optimización Bayesiana**
A diferencia de la búsqueda exhaustiva (_Grid Search_), la optimización Bayesiana utiliza un modelo probabilístico para encontrar el conjunto óptimo de hiperparámetros de manera más eficiente, minimizando el costo computacional. Se basa en el **Teorema de Bayes** para actualizar la probabilidad de una hipótesis a medida que se obtienen más resultados de las pruebas.

### 4. Métricas de Evaluación de Modelos
Para validar la hipótesis y demostrar la eficiencia del sistema ante un sínodo, es indispensable el uso de métricas estadísticas de desempeño:

- **Exactitud (Accuracy):** Representa el porcentaje total de predicciones correctas. $$Accuracy = \frac{TP + TN}{TP + TN + FP + FN}$$
- **Precisión (Precision):** Indica cuántas de las intrusiones detectadas eran realmente ataques (minimizando falsos positivos).
- **F1-Score:** Es la media armónica entre la precisión y la sensibilidad (_Recall_), ideal para datasets de red donde las clases suelen estar desbalanceadas.$$F1 = 2 \cdot \frac{Precision \cdot Recall}{Precision + Recall}$$
# Metodología 
### Población o universo/muestra
- **Universo:** Está constituido por la totalidad de los registros de tráfico de red (instancias) contenidos en el dataset **CIC-IDS2017**, el cual comprende aproximadamente 2.8 millones de flujos de datos etiquetados.
- **Muestra:** Se utilizará un **muestreo aleatorio estratificado** para asegurar que la proporción de ataques y tráfico normal se mantenga en los subconjuntos.
	- **70% para Entrenamiento:** Utilizado para que el algoritmo aprenda los patrones de comportamiento.
	- **30% para Pruebas (Validación):** Utilizado para evaluar el desempeño del modelo con datos que nunca ha visto.

### Tipo de estudio
- **Investigación Aplicada:** Busca resolver un problema concreto de seguridad mediante tecnología existente.
- **Enfoque Cuantitativo:** Se basa en la medición numérica y el análisis estadístico de la precisión del modelo.
- **Diseño Experimental:** Se manipularán variables (hiperparámetros) para observar su efecto en la variable dependiente (precisión de detección).

### Descripción del instrumento
- **Hardware:** Estación de trabajo con capacidad de procesamiento gráfico (GPU) o uso de entornos de nube (Google Colab).
- **Software:** Lenguaje **Python**, librerías de manipulación de datos (**Pandas**, **NumPy**, **Mathplotlib**) y aprendizaje automático (**Scikit-learn**, **XGBoost**).
- **Optimizador:** El framework **Optuna** para la implementación de la búsqueda Bayesiana de hiperparámetros.    

### Procedimiento de recolección (Diseño del experimento)
1. **Adquisición de Datos:** Descarga y carga del dataset en el entorno de desarrollo.
2. **Limpieza y Preprocesamiento:** Manejo de valores nulos, eliminación de duplicados y normalización de escalas numéricas.    
3. **Selección de Características:** Aplicación de algoritmos para identificar las variables de red más influyentes en la detección de intrusos.   
4. **Ciclo de Optimización:** Ejecución de múltiples iteraciones donde el optimizador Bayesiano ajusta los parámetros del modelo para encontrar la configuración más eficiente.

### Procedimiento de manejo estadístico de la información
- **Métricas de Desempeño:** Cálculo de la **Matriz de Confusión**, exactitud, precisión, sensibilidad y el **Puntaje F1** ($F1 = 2 \cdot \frac{Precision \cdot Recall}{Precision + Recall}$).
- **Análisis Comparativo:** Realizar una comparación de los resultados obtenidos contra los esperados (modelos sin optimizar) para validar la mejora en la detección.


# Cronograma
| **Fase / Unidad**                | **Actividad Principal**                                       | **Mes** | **Entregable Esperado**             |
| -------------------------------- | ------------------------------------------------------------- | ------- | ----------------------------------- |
| I. Evaluación y Complementación  | Análisis FODA y revisión del protocolo inicial.               | Marzo   | Protocolo actualizado y aprobado.   |
|                                  | Desarrollo del Marco Teórico.                                 | Marzo   | Marco conceptual y referencial.     |
|                                  | Definición y operacionalización de variables.                 | Marzo   | Tabla de variables e indicadores.   |
| II. Desarrollo de la Metodología | Diseño y validación de instrumentos (Scripts de ML).          | Marzo   | Código base y dataset preprocesado. |
|                                  | Ejecución de experimentos y Optimización Bayesiana.           | Abril   | Logs de entrenamiento y resultados. |
|                                  | Recolección, tratamiento y análisis estadístico de datos.     | Mayo    | Gráficas de desempeño y métricas.   |
| III. Presentación del Informe    | Elaboración del reporte de investigación (estructura formal). | Mayo    | Informe final de investigación.     |
|                                  | Preparación de material audiovisual para la defensa.          | Junio   | Presentación de diapositivas.       |
|                                  | Presentación oral y defensa ante el sínodo.                   | Junio   | Acta de evaluación y cierre.        |

# Presupuesto
Al ser un proyecto de software basado en **Machine Learning**, la inversión principal es en infraestructura de cómputo y servicios de red.

| **Concepto**          | **Descripción**                                      | **Cantidad** | **Costo Estimado (MXN)** |
| --------------------- | ---------------------------------------------------- | ------------ | ------------------------ |
| **Hardware**          | Computadora portátil (Procesador Ryzen 5, 16GB RAM). | 1            | $18,000.00 (Propio)      |
| **Servicios de Nube** | Google Colab Pro (para entrenamiento intensivo).     | 4 meses      | $800.00                  |
| **Conectividad**      | Servicio de internet de banda ancha (50 Mbps).       | 4 meses      | $2,000.00                |
| **Software**          | Licencias de software y librerías (Open Source).     | N/A          | $0.00                    |
| **Papelería**         | Impresión de reportes y materiales de apoyo.         | Global       | $500.00                  |
| **TOTAL**             |                                                      |              | **$21,300.00**           |

# Fuentes consultadas
- **Ahmad, Z., et al. (2021).** _Network intrusion detection system: A systematic study of machine learning and deep learning approaches_. IEEE Access. [Enfoque en métricas de desempeño].
- **Akter, M., et al. (2023).** _A Comprehensive Analysis of the CIC-IDS2017 Dataset for Network Intrusion Detection_. Journal of Cybersecurity and Privacy. [Base para la selección del dataset].
- **Akiba, T., et al. (2019/2021).** _Optuna: A Next-generation Hyperparameter Optimization Framework_. Proceedings of the 25th ACM SIGKDD. [Documentación técnica para la Optimización Bayesiana].
- **Hernández Sampieri, R., & Mendoza, C. (2020).** _Metodología de la investigación: las rutas cuantitativa, cualitativa y mixta_. McGraw-Hill. [Base metodológica para el tipo de estudio].
- **Tecnológico Nacional de México. (2016).** _Programa de estudio de la asignatura: Taller de investigación II (Clave ACA-0910)_. Dirección de Docencia e Innovación Educativa.    
- **Sharafaldin, I., et al. (2022).** _Toward Generating a New Intrusion Detection Dataset and Intrusion Traffic Characterization_. University of New Brunswick (CIC). [Referencia directa del dataset a utilizar].