Tags: [[Vision Artificial]]

- Patron natural
- Variables fisicas

Existen múltiples tipos de modelos y enfoques para las tareas de visión artificial, pero el siguiente ejemplo hipotético ilustra un flujo de trabajo común:

1. Recopilación de datos
2. Preprocesamiento
3. Selección de modelo
4. Entrenamiento de modelos


### Etapas generales
- Diseño de un localizador de objetos
- Selección de rasgos
- Diseño del clasificador
- Entrenamiento del clasificador
	- Selecciona el tipo de entrenamient(supervisado, no supervisado, ...)
- Evaluación de su rendimiento


- Mundo circundante
	- Señal analogica
- Captura de imagen
	- Imagen digital
- Pre-tratamiento o pre-procesamiento
	- Imagen tratada
- Segmentación
	- Imagen con regiones segmentada
- Representación
	- objetos representados en forma mas adecuada para procesamiento
- Extracción d rasgos y caracteristicas
	- Descriptores del objeto(vector)
- Detección, reconocimiento, clasificación
- Resultado e interpretación



Adquisición
PreProcesamiento
Segmentcación


### Recopilación de datos

El primer paso es recopilar los datos visuales necesarios. Los hospitales generan enormes volúmenes de radiografías de tórax, que pueden utilizar para entrenar un [algoritmo](https://www.ibm.com/mx-es/think/topics/machine-learning-algorithms) de visión artificial. Dado que el objetivo es que el algoritmo clasifique si una imagen de radiografía representa neumonía o no, los hospitales deberán compilar un [conjunto de datos](https://www.ibm.com/mx-es/think/topics/dataset) de radiografías de tórax y [etiquetar](https://www.ibm.com/mx-es/think/topics/data-labeling) o anotar correctamente cada exploración como normal o que signifique neumonía.

Para otros casos de uso, las imágenes y los videos pueden provenir de fuentes como cámaras y sensores. [Los conjuntos de datos](https://www.ibm.com/mx-es/think/topics/dataset) como COCO, ImageNet y Open Images proporcionan grandes colecciones de imágenes anotadas.

### Preprocesamiento

Un [modelo de IA](https://www.ibm.com/mx-es/think/topics/ai-model) es tan bueno como los datos utilizados para entrenarlo, lo que hace que los datos de alta calidad sean cruciales para la visión artificial. El preprocesamiento puede ayudar a mejorar la [calidad de los datos](https://www.ibm.com/mx-es/think/topics/data-quality) a través de [la limpieza de datos](https://www.ibm.com/mx-es/think/topics/data-cleaning) y mejoras, como ajustar el brillo o el contraste para dar nitidez a las imágenes, así como cambiar el tamaño y suavizar.

Los conjuntos de datos también deben ser lo suficientemente grandes y diversos para que [los algoritmos](https://www.ibm.com/mx-es/think/topics/machine-learning-algorithms) de visión artificial produzcan resultados precisos. [La generación de datos sintéticos](https://www.ibm.com/mx-es/think/insights/synthetic-data-generation) y el [aumento de datos](https://www.ibm.com/mx-es/think/topics/data-augmentation) pueden ayudar a ampliar el tamaño y la diversidad de los conjuntos de datos. Por ejemplo, los hospitales pueden utilizar transformaciones geométricas, como rotar las imágenes de radiografías de tórax hacia la izquierda o hacia la derecha o invertir las imágenes para aumentar sus datos.


### Selección de modelo

[Seleccionar el modelo de machine learning adecuado](https://www.ibm.com/mx-es/think/topics/model-selection) es crucial para optimizar la eficiencia y el rendimiento. Las [redes neuronales convolucionales (CNN)](https://www.ibm.com/mx-es/think/topics/convolutional-neural-networks) siguen siendo el principal modelo de [aprendizaje profundo](https://www.ibm.com/mx-es/think/topics/deep-learning) para las tareas de procesamiento de imágenes, mientras que las [redes neuronales recurrentes (RNN)](https://www.ibm.com/mx-es/think/topics/recurrent-neural-networks) son especialmente adecuadas para procesar datos secuenciales, como fotogramas de video.

Sin embargo, los avances en IA están impulsando un cambio hacia [modelos transformadores](https://www.ibm.com/mx-es/think/topics/transformer-model). Por ejemplo, un transformador de visión (ViT) aplica elementos de un [modelo de lenguaje](https://www.ibm.com/mx-es/think/topics/large-language-models) basado en transformadores a la visión artificial. Los ViT procesan una imagen en parches y los tratan como secuencias, de forma similar a los tokens en un transformador de lenguaje. Luego, el transformador de visión implementa un mecanismo de [autoatención](https://www.ibm.com/mx-es/think/topics/self-attention) en estos parches para crear una representación basada en transformadores de la imagen de entrada. Los ViT a menudo igualan o superan el rendimiento de las CNN en tareas de visión artificial, como la clasificación de imágenes.

### Entrenamiento de modelos

Una vez que se ha elegido un modelo, sigue [el entrenamiento del modelo.](https://www.ibm.com/mx-es/think/topics/model-training) La etapa de entrenamiento implica ejecutar el modelo en [datos de entrenamiento](https://www.ibm.com/mx-es/think/topics/training-data) específicos para una tarea de visión artificial, medir el rendimiento frente a [la verdad fundamental](https://www.ibm.com/mx-es/think/topics/ground-truth) y optimizar [los parámetros](https://www.ibm.com/mx-es/think/topics/model-parameters) para mejorar el rendimiento a lo largo del tiempo.

## Tareas de visión artificial
Los algoritmos de [visión artificial](https://developer.ibm.com/articles/introduction-computer-vision/) se pueden entrenar en una amplia gama de tareas, algunas de las cuales incluyen:

- Reconocimiento de imágenes
- Clasificación de imágenes
- Detección de objetos
- Segmentación de imágenes
- Seguimiento de objetos
- Comprensión de la escena
- Reconocimiento facial
- Estimación de poses
- Reconocimiento óptico de caracteres
- Generación de imágenes
- Inspección visual


## Herramientas de visión artificial
Existen muchas herramientas para crear aplicaciones de visión artificial, lo que ayuda a agilizar el proceso de desarrollo. Algunas herramientas populares incluyen:

- keras
- OpenCV
- Scikit-image
- TensorFlow
- Torchvision