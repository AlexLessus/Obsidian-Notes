tags: [[Vision Artificial]]
Alexis De Jesus Perez Carmona
- **¿Qué entiendes por procesamiento de imágenes?** 
Es el conjunto de técnicas y operaciones matemáticas aplicadas a una imagen digital con el objetivo de mejorar su calidad visual, restaurarla o extraer información útil para que un sistema (o un humano) pueda analizarla e interpretarla.    
- **¿Qué tareas o procesos se siguen en el procesamiento de imágenes?** 
Se realizan tareas de mejora (como ajustar contraste y brillo), restauración (eliminar defectos o ruido), segmentación (separar los objetos del fondo), extracción de características (medir formas, colores, texturas) y, finalmente, compresión para su almacenamiento.
- **¿Cuáles son las fases que componen al procesamiento de una imagen?**
    1. **Adquisición:** Capturar la imagen con un sensor (cámara).        
    2. **Preprocesamiento (Acondicionamiento):** Limpiar la imagen y prepararla (reducción de ruido, ajustes de iluminación).        
    3. **Segmentación:** Dividir la imagen en sus partes o regiones de interés.
    4. **Representación y Descripción:** Extraer las características matemáticas de esas regiones (ej. calcular el área o el contorno).        
    5. **Reconocimiento:** Clasificar el objeto basándose en sus características.
- **¿Qué se entiende por operaciones individuales de un pixel?** 
También llamadas operaciones puntuales. Son transformaciones donde el nuevo valor numérico (color o intensidad) de un píxel depende **únicamente** de su propio valor original, sin importar qué valores tengan los píxeles que lo rodean. Ejemplos: ajustar el brillo, invertir colores o aplicar un umbral.    
- **¿Qué se entiende con vecindad entre píxeles?** 
Es un concepto espacial que se refiere al grupo de píxeles que rodean o son adyacentes a un píxel central específico (generalmente se habla de vecindades de 4 u 8 píxeles). El análisis de la vecindad es fundamental para identificar bordes, texturas o aplicar filtros.
- **¿Qué se entiende por filtro y qué por convolución de una imagen?**
    - **Filtro (o Kernel):** Es una pequeña matriz matemática de valores fijos que define qué tipo de efecto se va a aplicar (ej. difuminar o buscar bordes).        
    - **Convolución:** Es la _operación matemática_ mediante la cual se desliza ese filtro sobre toda la imagen. Se multiplican los valores de los píxeles de una vecindad por los valores del filtro y se suman para calcular el nuevo valor del píxel central.
- **¿Qué se entiende por ruido en una imagen?** 
Son variaciones o alteraciones aleatorias e indeseadas en el brillo o color de los píxeles, que no representan la realidad de la escena fotografiada (como si tuviera "granulidad" o "nieve").   
- **¿Cómo o en qué momento se puede generar ruido en una imagen?** 
Se genera principalmente en la fase de **adquisición** (al tomar la foto con poca luz forzando el ISO del sensor, o por sobrecalentamiento de la cámara) o durante la **transmisión** electrónica de la señal.    
- **¿Qué tipos de ruidos se pueden dar en una imagen?** 
Los más comunes en visión artificial son:    
    - **Ruido Gaussiano:** Alteraciones sutiles distribuidas por toda la imagen.        
    - **Ruido de Sal y Pimienta:** Píxeles completamente blancos y negros esparcidos aleatoriamente.        
    - **Ruido Poisson (o fotónico):** Depende de la naturaleza estadística de las partículas de luz que llegan al sensor.        
- **¿Qué es la reducción de ruido en una imagen?** 
Es el proceso de aplicar algoritmos matemáticos (filtros espaciales) para minimizar o eliminar estos píxeles defectuosos, intentando conservar la mayor cantidad de detalles originales posibles.    
- **¿Qué se entiende por acondicionamiento de una imagen?** 
Es sinónimo de **preprocesamiento**. Significa preparar la imagen "cruda" apenas fue capturada para dejarla en condiciones óptimas antes de intentar analizarla. Incluye reducir el ruido, estandarizar el tamaño y normalizar la iluminación.    
- **¿Qué entenderías por suavizado de imágenes?** 
Es una técnica de filtrado que busca reducir las transiciones bruscas de intensidad entre píxeles, dando como resultado una imagen ligeramente difuminada o desenfocada (efecto "blur").    
- **¿Cómo crees que se llevaría a cabo el suavizado de imágenes?** 
Aplicando una convolución con un filtro espacial promediador (como el filtro de la Media, la Mediana o el Gaussiano). Lo que hace es que cada píxel adopte un valor que sea el promedio matemático de los píxeles de su vecindad.    
- **¿Qué propósito tendría el suavizado de imágenes?** 
Se utiliza principalmente para eliminar el ruido de alta frecuencia y ocultar pequeños detalles irrelevantes de la imagen. Esto evita que los algoritmos posteriores se confundan con la textura y se concentren en las formas generales.    
- **¿Qué entenderías por realzado de imágenes?** 
Es el proceso contrario al suavizado. Busca acentuar o resaltar detalles específicos, contrastes y transiciones bruscas para hacer que las características clave sean más nítidas.    
- **¿Cómo crees que se llevaría a cabo el realzado de imágenes?** 
Mediante la aplicación de filtros de "paso alto" (como el filtro Laplaciano, Sobel o Canny) que calculan derivadas espaciales para encontrar dónde hay cambios drásticos de color. También se logra ajustando el histograma de la imagen (ecualización).    
- **¿Qué propósito tendría el realzado de imágenes?** 
Facilitar la detección de bordes, líneas, contornos y texturas. Es un paso vital antes de la segmentación, ya que al resaltar los bordes, el sistema puede identificar exactamente dónde termina un objeto y dónde empieza el fondo.