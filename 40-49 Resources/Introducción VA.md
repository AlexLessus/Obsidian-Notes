Tags: [[Vision Artificial]]
### 1. Relación: Visión Artificial e Inteligencia Artificial
La **Visión Artificial (VA)** es una subdisciplina o rama de la **Inteligencia Artificial (IA)**.
- **Vínculo:** Mientras que la IA es el campo general que busca dotar a las máquinas de capacidades cognitivas (razonamiento, aprendizaje, percepción), la Visión Artificial es el "ojo" de esa inteligencia.    
- La IA proporciona los algoritmos de aprendizaje (como redes neuronales) que permiten a la VA no solo "ver" píxeles, sino "entender" qué significan. Sin IA, un sistema de visión solo procesaría imágenes (brillo, contraste) sin interpretar el contenido.    
### 2. Relación: Visión Artificial y Reconocimiento de Patrones
El **Reconocimiento de Patrones (RP)** es el núcleo matemático y algorítmico que utiliza la Visión Artificial para funcionar.
- **Vínculo:** La VA se encarga de adquirir y procesar la imagen, pero utiliza las técnicas de RP para clasificar lo que ve.
- Por ejemplo: La VA captura la foto de un grano de café y lo limpia de ruido; el RP analiza su forma y color para decir "es un grano tipo Arábica". La VA es el vehículo y el RP es el motor de clasificación.

### 3. Sentidos relacionados con el Reconocimiento de Patrones
Aunque solemos asociarlo a la vista, el reconocimiento de patrones es una capacidad cognitiva que involucra todos los sentidos para identificar regularidades en el entorno:
- **Vista:** Reconocimiento de rostros, letras, formas, objetos.
- **Oído:** Reconocimiento de melodías, voz, lenguaje hablado.    
- **Tacto:** Identificación de texturas (suave, rugoso) o formas sin mirar.
- **Olfato/Gusto:** Identificación de alimentos en mal estado o ingredientes específicos.

### 4. Analogía: Sensores de IA vs. Sentidos Humanos

| **Sentido Humano** | **Órgano Biológico**    | **Sensor en IA / Robótica**                     | **Función (Patrón a detectar)**                  |
| ------------------ | ----------------------- | ----------------------------------------------- | ------------------------------------------------ |
| **Vista**          | Ojos (Retina)           | Cámaras (Sensores CCD/CMOS), LiDAR              | Luz, color, profundidad, movimiento.             |
| **Oído**           | Oídos (Cóclea)          | Micrófonos, Sensores ultrasónicos               | Ondas sonoras, frecuencias, voz.                 |
| **Tacto**          | Piel (Nervios)          | Sensores de presión, piezoresistivos, térmicos  | Textura, temperatura, contacto físico.           |
| **Olfato**         | Nariz (Bulbo olfatorio) | Narices electrónicas (Sensores de gas)          | Composición química del aire (gases).            |
| **Gusto**          | Lengua (Papilas)        | Lenguas electrónicas (Sensores electroquímicos) | Composición química de líquidos (pH, salinidad). |
| **Propiocepción**  | Oído interno / Músculos | Acelerómetros, Giroscopios (IMU)                | Equilibrio, orientación y aceleración.           |

### 5. Estados Mentales y Reconocimiento de Patrones
Desde la psicología cognitiva, el reconocimiento de patrones involucra varios procesos o "estados" mentales:
- **Atención:** Enfocar los recursos cognitivos en el estímulo (filtrar el ruido).
- **Percepción:** La interpretación inicial de la señal sensorial.    
- **Memoria (Corto y Largo Plazo):** Comparar el estímulo actual con "plantillas" o experiencias almacenadas previamente.    
- **Aprendizaje:** La capacidad de actualizar los modelos mentales cuando un patrón cambia o aparece uno nuevo.    
- **Toma de Decisiones:** El estado final donde se concluye qué es el objeto (clasificación).    

### 6. Analogía: Ser Humano vs. IA en Reconocimiento de Patrones

| **Característica** | **Ser Humano**                                                                       | **Inteligencia Artificial**                                                       |
| ------------------ | ------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------- |
| **Aprendizaje**    | Aprende con **pocos ejemplos** (puedes ver un animal una vez y reconocerlo siempre). | Requiere **miles de ejemplos** (Big Data) para entrenar un modelo robusto.        |
| **Generalización** | Alta capacidad de generalizar (reconoce una silla aunque sea de diseño extraño).     | Le cuesta generalizar si el objeto es muy diferente a sus datos de entrenamiento. |
| **Contexto**       | Usa el **sentido común** y el contexto para resolver ambigüedades.                   | Carece de sentido común; se basa estrictamente en probabilidades estadísticas.    |
| **Cansancio**      | Se fatiga y pierde precisión con tareas repetitivas.                                 | Mantiene la misma precisión **indefinidamente** (ideal para industria).           |

### 7. Fases del Reconocimiento de Patrones
Según la literatura clásica (como Bishop o Duda & Hart), las fases son:
1. **Adquisición de datos:** Captura de la señal física mediante un sensor.
2. **Preprocesamiento:** Limpieza de la señal (eliminar ruido) para facilitar el análisis.
3. **Extracción de características:** Obtener los datos numéricos clave que definen al objeto (ej. "redondez", "brillo medio") y descartar información irrelevante.
4. **Selección de características:** Elegir solo las características más discriminantes para reducir la complejidad.    
5. **Clasificación (Toma de decisiones):** Asignar el objeto a una categoría específica (Clase A o Clase B) usando un modelo matemático.

### 8. Fases que hereda la Visión Artificial
La Visión Artificial adapta las fases anteriores específicamente l dominio de las imágenes.
1. **Adquisición de imagen:** (Heredada de Adquisición) Obtención de la imagen digital mediante cámaras e iluminación adecuada.    
2. **Preprocesamiento:** (Heredada de Preprocesamiento) Mejora de la imagen: filtrado de ruido, ajuste de contraste, corrección gamma.
3. **Segmentación:** (Fase crítica en VA) Separar los objetos de interés del fondo. Esto es vital para aislar el patrón antes de medirlo.    
4. **Representación y Descripción:** (Heredada de Extracción de características) Convertir la región segmentada en datos (vectores, descriptores de forma/textura).
5. **Reconocimiento e Interpretación:** (Heredada de Clasificación) Usar algoritmos (como redes neuronales o clasificadores estadísticos) para identificar el objeto y darle sentido en la escena.    

### Fuentes de Información Consultadas:
- **Domínguez, T. (2021).** _Visión Artificial. Aplicaciones prácticas con OpenCV._ 
- **Pajares, G. (2002).** _Visión por Computador._ 
- **Wikipedia / Enciclopedias técnicas:** Artículos sobre "Reconocimiento de patrones (psicología)" y "Visión Artificial" para las analogías sensoriales.
- **Artículos de Divulgación (AWS, UnitX):** Para las definiciones modernas de Industria 4.0 y relación IA-VA.

--- 

## Observaciones y comentarios
Me parece muy interesante como se relacionan directamente la visión artificial y la IA, sin IA no existiría la VA. Creo que lo mencioné en alguna otra actividad en la parte de conclusiones, me pregunto si al alcanzar la singularidad tecnológica, las computadoras desarrollarán alguna otra forma de aprender de su entorno, tal vez con campos electromagnéticos o algo incluso que ellas mismas desarrollen algún sentido completamente nuevo. Que miedo