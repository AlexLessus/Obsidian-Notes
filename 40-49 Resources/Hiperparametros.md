Tags: [[Aprendizaje Automático]]

## **Parámetros** 
Son **variables internas del modelo** que se obtienen automáticamente a partir de los datos durante el entrenamiento del algoritmo. 

En el ejemplo, son los coeficientes que definen la orientación de la línea recta de separación Estos valores no se pueden controlar directamente.

%% se pueden obtener a traves de los datos%%

## **Hiper-parámetros**: 
Son **variables externas al modelo** que deben ser definidas manualmente por el programador antes del entrenamiento del algoritmo. 

 El desempeño del modelo depende directamente de la elección de estos.
 
%%Tu los ajustas para buscar la mejor configuración%%

# Ajuste de Hiper-parámetros
Dado que no hay una fórmula mágica, se usa un enfoque de ==prueba y error==, probando diferentes combinaciones de hiper-parámetros para encontrar el conjunto que ofrezca el mejor desempeño.

## Grid search - Búsqueda Exhaustiva
Este método prueba _todas_ las combinaciones posibles de hiper-parámetros. 
La ventaja es que garantiza encontrar la mejor combinación, pero su desventaja es que requiere mucho tiempo y recursos computacionales en modelos complejos o con muchos datos.

## Random Search - Búsqueda aleatoria
A diferencia del Grid Search, este método selecciona una _muestra aleatoria_ de combinaciones de hiper-parámetros. 
Su ventaja es que es más rápido y requiere menos recursos, pero no garantiza encontrar la combinación ideal, ya que no prueba todas las posibilidades.
