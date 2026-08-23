# Erosion y dilatación
Para detectar una persona u objeto suelen quedar huecos, entonces hay que rellenarlos para detectarlos bien.

``` python
# Erosión
img = cv2.erode(img, kernel, iteration=1)
# Dilatación
img = cv2.dilate(img, kernel, iteration=1)
```

> img: tiene que ser una imagen binaria, no funciona con imagenes a color
> iteration: Cuantas veces se aplicará, entre mas veces mas marcado se ve
> kernel: Matriz impar para aplicar, la mas comun es 5,5

erode es una operacion and
dilate es una operacion or

### Operaciones
- Apertura: desaparecen puntos sueltos
- Cierre: se rellenan huecos
- Gradiente diferencia entre dilatación y erosion
- Sombrero de copa: diferencian la imagen y la apertura
- Sombrero negro: diferencia entre la imagen de cierre y la imagen de entrada

``` python
cv2.morphology(img, cv2.MORPH_OPEN, kernel)
							 _CLOSE
							 _GRADIENT
							 _TOPHAT
							 _BLACKHAT
```

