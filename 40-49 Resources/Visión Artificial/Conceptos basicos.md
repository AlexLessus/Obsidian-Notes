Tags: [[Vision Artificial]] [[Conceptos]] 
### 1. Fundamentos Generales y Visión

- **Computación gráfica:** Campo que se encarga de la generación de imágenes sintéticas a partir de modelos matemáticos y geométricos de objetos. (El proceso inverso a la visión: _Datos $\to$ Imagen_).
 
- **Visión:** Proceso mediante el cual un organismo o máquina percibe el entorno a partir de la luz reflejada por los objetos.
 
- **Visión humana:** Proceso biológico y psicofísico complejo donde el ojo capta la luz y el cerebro interpreta las señales nerviosas para comprender el entorno.
 
- **Visión artificial:** Disciplina científica que busca simular la visión humana mediante computadoras, permitiendo adquirir, procesar, analizar y comprender imágenes del mundo real para producir información numérica o simbólica.
 
- **Sistema:** Conjunto de elementos interrelacionados que funcionan como un todo para lograr un objetivo común.
 
- **Sistema de visión:** Conjunto de hardware (cámaras, iluminación, procesador) y software diseñado para realizar tareas de visión artificial automáticamente.
 
- **Subsistema:** Parte o componente de un sistema mayor que tiene una función específica (ej. el subsistema de iluminación dentro de un sistema de visión).
 

### 2. Imágenes y Representación Digital

- **Imagen:** Representación visual de un objeto o escena. Matemáticamente, es una función $f(x,y)$ donde $x$ e $y$ son coordenadas espaciales y la amplitud $f$ es la intensidad.
 
- **Fotografía:** Imagen obtenida mediante la acción de la luz sobre una superficie sensible o un sensor electrónico.
 
- **Digitalización:** Proceso de convertir una señal analógica (continua) en una representación digital (discreta) mediante muestreo y cuantificación.
 
- **Pixel:** (Picture Element) La unidad mínima y elemental de una imagen digital. Representa un único punto de color o intensidad.
 
- **Resolución de una imagen:** Cantidad de detalle que tiene una imagen, generalmente medida por el número de píxeles (ancho $\times$ alto) o píxeles por pulgada (PPI).
 
- **Resolución espacial:** Capacidad de distinguir detalles finos en la imagen; depende de la densidad de píxeles.
 
- **Resolución temporal:** Frecuencia con la que se capturan imágenes en una secuencia (cuadros por segundo o FPS).
 
- **Señal analógica:** Señal continua en el tiempo y amplitud (ej. la luz que entra al lente).
 
- **Señal digital:** Señal discreta representada por números binarios (ej. el archivo JPG final).
 
- **Convertidor analógico-digital (ADC):** Dispositivo que transforma el voltaje continuo del sensor en valores numéricos digitales.
 
- **Convertidor digital-analógico (DAC):** Dispositivo que transforma datos digitales en señales continuas (ej. para mostrar la imagen en un monitor antiguo).
 
- **Vector:** En imágenes, puede referirse a un array unidimensional de datos o a una forma de representar gráficos mediante fórmulas geométricas en lugar de píxeles.
 
- **Matriz:** Arreglo bidimensional de números. Una imagen digital se representa computacionalmente como una matriz de valores.
 

### 3. Propiedades de la Imagen y Física

- **Luz:** Radiación electromagnética dentro del espectro visible capaz de ser detectada por el ojo humano o sensores ópticos.
 
- **Espectro:** Rango de frecuencias de la radiación electromagnética.
 
- **Cromático:** Relativo al color.
 
- **Fuente de luz o iluminación:** Dispositivo natural o artificial que emite luz para hacer visibles los objetos a la cámara.
 
- **Iluminación:** Técnica de aplicar luz a una escena para resaltar las características de interés y facilitar su captura.
 
- **Brillo:** Percepción subjetiva de la intensidad de la luz (luminancia) emitida o reflejada por un objeto.
 
- **Contraste:** Diferencia en intensidad de luz y color entre distintas partes de una imagen (ej. entre el objeto y el fondo).
 
- **Espacio de color:** Modelo matemático para describir colores mediante tuplas de números (ej. RGB, HSV, CIELAB).
 
- **Óptica:** Rama de la física que estudia el comportamiento de la luz; en visión, se refiere a las lentes utilizadas para enfocar la imagen en el sensor.
 
- **Cámara:** Dispositivo transductor que convierte la energía luminosa en una señal eléctrica (imagen).
 
- **Modelo físico:** Representación matemática de cómo la luz interactúa con las superficies y llega al sensor.
 
- **Modelo fisiológico:** Estudio de cómo funciona el ojo humano y la percepción para inspirar algoritmos de visión.
 

### 4. Procesamiento de Imágenes

- **Procesamiento de una imagen:** Conjunto de técnicas aplicadas a una imagen digital para mejorar su calidad o extraer información.
 
- **Preprocesamiento:** Etapa inicial para acondicionar la imagen (reducir ruido, mejorar contraste) antes del análisis principal.
 
- **Ruido:** Variaciones aleatorias de brillo o color en la imagen no deseadas, producidas por el sensor o circuitos electrónicos.
 
- **Filtrar:** Aplicar una operación (como una máscara o kernel) para resaltar o suprimir características (ej. quitar ruido).
 
- **Suavizar:** Técnica de filtrado para reducir la nitidez y el ruido, difuminando la imagen (ej. filtro Gaussiano).
 
- **Realzar:** Mejorar detalles o bordes de una imagen para hacerlos más visibles.
 
- **Restaurar:** Intentar recuperar la imagen original a partir de una versión degradada o con ruido.
 
- **Compresión de una imagen:** Reducción del tamaño del archivo de imagen eliminando redundancia (con o sin pérdida de calidad).
 
- **Convolución:** Operación matemática fundamental en visión que combina dos funciones (la imagen y un filtro/kernel) para producir una tercera imagen transformada (ej. para detectar bordes).
 
- **Normalización:** Ajustar los valores de los píxeles a un rango estándar (ej. de 0 a 1) para facilitar el procesamiento.
 

### 5. Análisis y Reconocimiento de Patrones

- **Segmentación:** Proceso de dividir una imagen en partes o regiones significativas (ej. separar el grano de café del fondo).
 
- **Región:** Un grupo de píxeles conectados con propiedades similares.
 
- **Objeto:** Entidad física tangible representada en la imagen que se desea analizar.
 
- **Patrón:** Disposición específica de características que permite identificar una clase de objetos.
 
- **Reconocimiento de patrones:** Disciplina que se ocupa de la clasificación automática de objetos en categorías basadas en sus características.
 
- **Rasgo (Feature):** Característica distintiva de un objeto (ej. color, textura, forma).
 
- **Descriptor:** Representación numérica (vector) de los rasgos visuales de una imagen o región.
 
- **Extraer:** Obtener características cuantitativas (rasgos) de los objetos segmentados.
 
- **Etiqueta:** Identificador asignado a una región o imagen clasificada (ej. "Grano Tueste Medio").
 
- **Detectar:** Determinar la presencia y ubicación de un objeto en la imagen (¿Está ahí?).
 
- **Reconocer:** Identificar la categoría específica del objeto detectado (¿Qué es?).
 
- **Interpretar:** Asignar significado al conjunto de objetos reconocidos en el contexto de la escena.
 
- **Comprender:** Nivel más alto de visión; implica entender la escena y las relaciones entre objetos, similar a la cognición humana.
 
- **Analizar:** Descomponer la imagen en sus componentes para su estudio.
 

### 6. Aprendizaje y Video

- **Aprendizaje (Learning):** Proceso mediante el cual un sistema mejora su rendimiento a partir de datos o experiencia.
 
- **Aprendizaje automático (Machine Learning):** Subcampo de la IA donde las computadoras aprenden a reconocer patrones sin ser explícitamente programadas para cada regla.
 
- **Aprendizaje profundo (Deep Learning):** Técnica de aprendizaje automático basada en redes neuronales artificiales con múltiples capas, fundamental en la visión moderna.
 
- **Video:** Secuencia de imágenes mostradas en rápida sucesión para crear la ilusión de movimiento.
 
- **Estático:** Que no cambia con el tiempo (imagen fija).
 
- **Dinámico:** Que cambia con el tiempo (movimiento).
 
- **Tiempo real:** Procesamiento de datos a la misma velocidad (o mayor) a la que son capturados, permitiendo respuestas inmediatas.
 
- **Streaming:** Transmisión continua de datos de audio o video mientras se consumen.
 

