Tags [[Vision Artificial]]
Que es?


### Preprocesamiento
Es lo primero que haremos con la imagen, para prepararla para procesarla


### Adecuación de una imagen
Adecuar la imagen, con cambios de tamaño, colores, etc. para que sea adecuada para la tarea que se hará


## Ruido
Imperfecciones
Todo aquello que no forme parte de la imagen se le considera ruido

Sal y pimienta
La imagen tiene puntitos, que son blancos y negros

Algoritmos de suavizado
Se utilizan para procesar imágenes y eliminar el ruido
### Denoising de imágenes en OpenCV
OpenCV proporciona cuatro variaciones de esta técnica.
```python 
cv2.fastNlMeansDenoising () # funciona con una sola imagen en escala de grises
cv2.fastNlMeansDenoisingColored () # funciona con una imagen en color. 
cv2.fastNlMeansDenoisingMulti () # funciona con la secuencia de imágenes capturadas en un corto periodo de tiempo (imágenes en escala de grises) 
cv2.fastNlSignificaDenoisingColoredMulti () # igual que arriba, pero para imágenes en color.
```
#### cv2.fastNlSignificaDenoisingColored ()
Como se mencionó anteriormente, se utiliza para eliminar el ruido de las imágenes en color. (El ruido se espera que sea gaussiano). Vea el ejemplo a continuación:
```python
import numpy as np import cv2 from matplotlib import pyplot as plt img = cv2.imread('fastNlMeansDenoising.jpg') dst = cv2.fastNlMeansDenoisingColored(img,None,10,10,7,21) plt.subplot(121),plt.imshow(img) plt.subplot(122),plt.imshow(dst) plt.show()
```
![[Pasted image 20260414100332.png]]

## Segmentación



## Representación y descripción
