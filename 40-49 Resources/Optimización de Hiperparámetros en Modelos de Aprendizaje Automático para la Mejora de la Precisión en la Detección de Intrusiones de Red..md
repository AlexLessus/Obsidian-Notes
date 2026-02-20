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

Si bien el **Aprendizaje Automático (Machine Learning)** ha surgido como una solución prometedora, ==la mayoría de los modelos implementados carecen de una **optimización de hiperparámetros** específica para el contexto de redes académicas,== lo que deriva en una alta tasa de falsos positivos y una baja precisión en la detección de ataques complejos como infiltraciones y botnets. Por lo tanto, el problema central radica en la falta de modelos de detección de intrusiones técnicamente optimizados que garanticen una alta eficiencia en la identificación de amenazas sin interrumpir el flujo legítimo de datos en una red estudiantil.

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
"La implementación de un modelo de detección de intrusiones basado en **Random Forest** u **XGBoost**, optimizado mediante **Optimización Bayesiana**, permite alcanzar una precisión ($Accuracy$) superior al **95%** y una reducción significativa en los falsos positivos en comparación con modelos configurados con hiperparámetros por defecto".

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

==Buscar==
- _"Bayesian Optimization for Network Intrusion Detection" (2021-2026).
- _"Machine Learning in Cybersecurity: A review of NIDS datasets"_.
- _"Handling imbalanced datasets in Intrusion Detection Systems"_.

