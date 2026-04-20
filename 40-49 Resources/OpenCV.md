Tags [[Vision Artificial]]


## Funciones de suavizado
### Filtro2D
```python
dst = cv2.filter2D(src, ddepth, kernel[, dst[, anchor[, delta[, borderType]]]])
```
Parámetros:
•   src: Imagen de entrada (matriz NumPy), puede ser en escala de grises o en color.
•   ddepth: Profundidad deseada de la imagen de salida. Usa -1 para que tenga la misma profundidad que la imagen de entrada.
•   kernel: Núcleo (matriz) de filtrado, definido como un np.array (por ejemplo, de tipo np.float32).
•   dst: Imagen de salida (opcional).
•   anchor: Posición del ancla del kernel. Por defecto es (-1, -1), lo que significa que está centrado.
•   delta: Valor que se suma al resultado final (por defecto es 0).

•   borderType: Tipo de borde, como cv2.BORDER_DEFAULT, cv2.BORDER_CONSTANT, etc.
###  Blur
```python
cv2.blur(src, ksize, dst=None, anchor=(-1, -1), borderType=cv2.BORDER_DEFAULT)
```
Parámetros:
•   src: Imagen de entrada (matriz NumPy).
•   ksize: Tamaño del kernel de desenfoque, como una tupla (ancho, alto), por ejemplo (5, 5).
•   dst: (Opcional) Salida, imagen del mismo tamaño y tipo que src.
•   anchor: (Opcional) Punto de anclaje del kernel. Por defecto (-1, -1) significa que el centro del kernel se utiliza como ancla.
•   borderType: (Opcional) Tipo de borde usado para extrapolación, como cv2.BORDER_CONSTANT, cv2.BORDER_REFLECT, etc.
###  GaussianBlur
```python
cv2.GaussianBlur(src, ksize, sigmaX, dst=None, sigmaY=0, borderType=cv2.BORDER_DEFAULT)
```
Parámetros:
•   src: Imagen de entrada.
•   ksize: Tamaño del kernel, una tupla impar como (5, 5).
•   sigmaX: Desviación estándar en dirección X. Si es 0, se calcula automáticamente.
•   dst: (Opcional) Imagen de salida.
•   sigmaY: (Opcional) Desviación estándar en Y. Si es 0, se usa sigmaX.
•   borderType: (Opcional) Tipo de extrapolación de borde.

### medianBlur
```python
cv2.medianBlur(src, ksize)
```
Parámetros:
•   src: Imagen de entrada.
•   ksize: Tamaño del kernel (debe ser impar y mayor que 1). Por ejemplo: 3, 5, 7, etc.
### boxFilter
```python
cv2.boxFilter(src, ddepth, ksize, anchor=None, normalize=True, borderType=cv2.BORDER_DEFAULT)
```

Parámetros:
•   src: Imagen de entrada (debe ser de tipo numpy.ndarray).
•   ddepth: Profundidad de la imagen de salida. Si es -1, la imagen de salida tendrá la misma profundidad que la imagen de entrada.
•   ksize: Tamaño del kernel. Es una tupla (ancho, alto) que especifica las dimensiones del filtro de caja.
•   anchor: Punto de anclaje del kernel. Por defecto es (ksize[0]//2, ksize[1]//2).
•   normalize: Si es True, normaliza los valores del filtro, es decir, divide los elementos del kernel por su suma. Si es False, no se realiza la normalización. El valor predeterminado es True.
•   borderType: Tipo de borde que se usará. El valor predeterminado es cv2.BORDER_DEFAULT, pero puede ser modificado con opciones como cv2.BORDER_REPLICATE, cv2.BORDER_REFLECT, etc.
### bilateralFilter
	Permite definir si trabajamos con la imagen normalizada
