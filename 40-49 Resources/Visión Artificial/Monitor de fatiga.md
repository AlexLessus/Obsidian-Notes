Una herramienta de utilidad para automatizar el cuidado ergonómico durante largas sesiones de trabajo en la terminal.
- **El objetivo:** Crear un script de fondo que supervise tu postura y nivel de atención.
- **Cómo hacerlo:** Combinar _Pose Landmarker_ (para medir el ángulo de los hombros y el cuello) y _Face Mesh_ (para calcular el ratio de apertura de los ojos o la dirección de la mirada).
### 1. Preparación del Entorno

Estaremos trabajando con Python para facilitar el prototipado rápido. Solo necesitas instalar las librerías principales de procesamiento numérico y visión:

Bash

```
pip install mediapipe opencv-python numpy
```

### 2. La Lógica de Fatiga: Eye Aspect Ratio (EAR)

Para detectar si te estás quedando dormido, usaremos **Face Mesh** de MediaPipe. Esta solución nos da puntos exactos del contorno del ojo.

Para saber si el ojo está cerrado, utilizamos la relación de aspecto del ojo o **EAR**. Calculamos la distancia euclidiana entre los puntos verticales del ojo y la dividimos por la distancia horizontal:

$EAR = \frac{||p_2 - p_6|| + ||p_3 - p_5||}{2 ||p_1 - p_4||}$

Donde $p_1, ..., p_6$ son las coordenadas 2D de los puntos clave del ojo. Si tu $EAR$ cae por debajo de un umbral (por ejemplo, $0.2$) durante varios _frames_ consecutivos, significa que hay somnolencia o un "microsueño", y el sistema deberá lanzar una alerta.

### 3. La Lógica de Postura: Cálculo de Inclinación

Para la ergonomía, usaremos **Pose Landmarker**. Extraeremos las coordenadas $(x, y)$ de puntos anatómicos clave:

- Punto $0$ (Nariz)
- Puntos $11$ y $12$ (Hombro izquierdo y derecho)

Calcularemos el punto medio entre ambos hombros y, usando la función arco tangente (`numpy.arctan2`), obtendremos el ángulo que se forma entre la nariz y el eje de los hombros. Si la nariz se desplaza demasiado hacia adelante o hacia abajo (perdiendo el eje vertical), significa que estás "encorvado" hacia la pantalla.

