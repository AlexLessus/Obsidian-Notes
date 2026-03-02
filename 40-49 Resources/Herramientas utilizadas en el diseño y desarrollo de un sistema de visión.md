### Librerías Base de Visión Computacional
Estas son las herramientas fundamentales para el procesamiento tradicional de imágenes (filtrado, detección de bordes, transformaciones geométricas).
- **OpenCV (Open Source Computer Vision Library):** Es el estándar de oro absoluto en la industria. Está escrita en C++, pero tiene integraciones perfectas para Python y Java. Sirve para todo: desde calibrar una cámara hasta detección facial en tiempo real.
- **Scikit-Image:** Una librería de Python muy limpia y "pythónica", ideal para tareas científicas y preprocesamiento. Trabaja de la mano con **Numpy** y **SciPy**, herramientas que precisamente están contempladas en tu programa de Aprendizaje Automático.
- **Pillow (PIL):** Más básica, utilizada principalmente en Python para abrir, manipular (recortar, redimensionar) y guardar diferentes formatos de imagen.
### 2. Frameworks de Deep Learning (Para Visión Moderna)
Cuando el procesamiento clásico no es suficiente y necesitas que el sistema "aprenda" a reconocer objetos o clasificar imágenes complejas.
- **TensorFlow y Keras:** Desarrollados por Google. Son los más utilizados para construir Redes Neuronales Convolucionales (CNN) desde cero. Son parte oficial de las librerías de tu temario actual.
- **PyTorch:** Desarrollado por Meta (Facebook). Es el favorito actual en el ámbito de la investigación y está ganando muchísimo terreno en producción por ser más dinámico y fácil de depurar que TensorFlow.
- **YOLO (You Only Look Once):** Más que una librería, es una familia de modelos de detección de objetos en tiempo real. Es increíblemente rápido y es lo que usarías para, por ejemplo, contar coches en una autopista desde un video.
### 3. Herramientas para Desarrollo Móvil (Android/iOS)
Si el objetivo es llevar el sistema de visión a la cámara de un teléfono inteligente utilizando lenguajes nativos como Kotlin o Swift.
- **Google ML Kit:** Un SDK móvil brutal que ya trae modelos de visión de Google optimizados para ejecutarse localmente en el teléfono (lectura de códigos de barras, reconocimiento de texto, detección de rostros).    
- **MediaPipe:** También de Google, excelente para tareas como rastreo de manos (hand tracking), estimación de poses o mallas faciales en tiempo real directamente desde la cámara del celular.   
### 4. Herramientas para Hardware y Microcontroladores (Edge AI)
Para cuando necesitas integrar visión en sistemas electrónicos pequeños o de bajo consumo.
- **OpenMV:** Un ecosistema (software y hardware) programable en MicroPython, diseñado específicamente para hacer visión artificial en microcontroladores.
- **Edge Impulse:** Una plataforma de desarrollo que permite entrenar modelos de Machine Learning (incluyendo visión) y compilarlos en código C++ altamente optimizado para que corran en placas pequeñas como un Arduino.   
### 5. APIs en la Nube (Cloud Vision)
Si tu sistema tiene conexión a internet y prefieres delegar el procesamiento pesado a servidores externos.
- **Oracle Cloud Vision, Google Cloud Vision o AWS Rekognition:** Envías una imagen a través de una petición HTTP (API REST) y la nube te devuelve un archivo JSON con todo lo que detectó (marcas, caras, texto, objetos). Es la ruta más rápida si ya tienes experiencia montando servidores VPS y conectando servicios en la nube.