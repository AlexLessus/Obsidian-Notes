Alexis De Jesus Perez Carmona
#AI #DeepLearning

---
**El aprendizaje profundo no existe de forma aislada; es una disciplina de confluencia científica altamente interdisciplinaria. Se nutre y recibe aportaciones fundamentales de diversas áreas del conocimiento humano.**

### 1. Matemáticas Aplicadas
Las matemáticas no son un mero complemento, sino el lenguaje y el motor formal que define las reglas del aprendizaje profundo.

- **Álgebra Lineal**: Aporta el concepto de **tensores** y la manipulación de espacios de alta dimensionalidad. Toda la información (imágenes, textos o sonidos) se vectoriza y procesa mediante multiplicaciones de matrices y transformaciones geométricas continuas dentro de la red.
- **Cálculo Vectorial**: Suministra la **regla de la cadena**, que es la base analítica detrás del algoritmo de retro propagación (_backpropagation_) para derivar funciones compuestas capa por capa.
- **Optimización Numérica**: Aporta algoritmos de descenso de gradiente (como el SGD o Adam) que determinan cómo deben ajustarse geométricamente los pesos para encontrar el punto mínimo de error.
- **Teoría de la Información**: Ayuda a definir formalmente la eficiencia con la que se transmite la información y a estructurar las funciones de pérdida que guían el aprendizaje.

### 2. Probabilidad y Estadística
El aprendizaje automático es, por definición, un campo profundamente emparentado con la estadística matemática.

- **Modelado del Ruido y la Incertidumbre**: Provee herramientas de inferencia y modelos probabilísticos para que las redes tomen decisiones ante entornos con variabilidad aleatoria.
- **Generalización Estadística**: Aporta la teoría matemática necesaria para verificar si un modelo de aproximación de funciones no solo "memoriza" el conjunto de entrenamiento, sino que logra una generalización estadística efectiva sobre datos nuevos y no vistos anteriormente.

### 3. Neurociencia y Ciencias Biológicas
La neurobiología y el estudio del cerebro humano constituyeron el impulso conceptual histórico del conexionismo.

- **Inspiración en Sistemas Distribuidos**: Aportó la idea fundamental de que la inteligencia puede emerger de una masa enorme de unidades de cómputo sumamente sencillas (neuronas artificiales) que cooperan a través de sus interconexiones ajustables.
- **Arquitecturas de Procesamiento Visual**: El estudio de la corteza visual de los mamíferos y de sus células complejas sirvió de base directa para el desarrollo de estructuras como el _Neocognitron_, que posteriormente evolucionó en las **Redes Neuronales Convolucionales (CNN)** modernas para el análisis de imágenes.
- _Nota de rigor_: Aunque la neurociencia es un motor de inspiración conceptual, el aprendizaje profundo moderno no busca simular fielmente el cerebro biológico, ya que nuestras redes artificiales operan bajo optimizaciones matemáticas (diferenciabilidad matemática continua y descenso de gradiente) que no reflejan el funcionamiento biológico real.

### 4. Ciencias de la Computación (e Ingeniería de Hardware y Software)
El aprendizaje profundo requiere transformar estas complejas construcciones matemáticas en código ejecutable de alto rendimiento, lo que lo convierte en una ciencia de ingeniería empírica.

- **Algoritmos y Estructuras de Datos**: Aporta el desarrollo de representaciones estructuradas avanzadas (como los grafos que definen el camino de las redes neuronales) y la optimización de los algoritmos de búsqueda y procesamiento.
- **Arquitectura de Computadoras y Cómputo Paralelo**: La computación en la nube y, en especial, el diseño de hardware paralelo masivo como las **unidades de procesamiento gráfico (GPUs)** y TPUs, transformaron operaciones que eran computacionalmente inviables hace 25 años en multiplicaciones matriciales ultrarrápidas, posibilitando el entrenamiento de modelos modernos con miles de millones de parámetros.

### 5. Inteligencia Artificial (IA)
Como disciplina marco de la informática, define el horizonte y los objetivos generales del sistema.
- **Estrategia y Clasificación**: Aporta el contexto histórico del reconocimiento de patrones, la definición del espacio de hipótesis y los marcos conceptuales sobre cómo construir agentes y sistemas capaces de aprender de la experiencia de manera autónoma para tomar decisiones complejas.


### Bibliografía:
*NotebookLM (lo utilizo para que procese los siguientes libros y algunos recursos de la plataforma)*
Chollet, F. (2021). _Deep Learning with Python_ (2nd ed.). Manning Publications.
Goodfellow, I., Bengio, Y., & Courville, A. (2016). _Deep Learning_. The MIT Press.
