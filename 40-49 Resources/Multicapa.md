#MachineLearning 

El calculo de pesos es del final al inicio

### La Arquitectura (Estructura)
Una red neuronal multicapa se compone de nodos (neuronas artificiales) organizados en al menos tres tipos de capas:

- **Capa de Entrada (Input Layer):** Recibe los datos crudos. Cada neurona aquí representa una característica (columna) de tu conjunto de datos. No hace cálculos, solo pasa la información a la siguiente capa.
    
- **Capas Ocultas (Hidden Layers):** Es aquí donde ocurre la "magia". Se llaman ocultas porque no interactúan directamente con los datos de entrada ni con el usuario final. Una red puede tener una (red superficial) o decenas de ellas (Deep Learning). Cada neurona en una capa oculta está conectada a todas las neuronas de la capa anterior y a todas las de la capa siguiente.
    
- **Capa de Salida (Output Layer):** Entrega el resultado final. Si es un problema de regresión (predecir un precio), será una sola neurona. Si es clasificación (reconocer si es un perro, gato o pájaro), tendrá varias neuronas que arrojan una probabilidad.

### El Flujo de Información (Forward Propagation)
Cuando los datos entran en la red, viajan hacia adelante capa por capa. En cada conexión entre neuronas ocurren tres operaciones matemáticas fundamentales:

1. **[[Pesos]] (Weights - $W$):** Cada conexión tiene un "peso" numérico. Representa la importancia de esa conexión. Si el peso es alto, la señal pasa con fuerza; si es cercano a cero, la señal se ignora.
    
2. **[[Sesgo]] (Bias - $b$):** Cada neurona tiene un valor adicional que se suma al resultado. Funciona de manera similar a la intersección en una regresión lineal, permitiendo desplazar la función de activación para que se ajuste mejor a los datos.
    
3. **Suma y Activación:** La neurona receptora toma los valores de entrada ($x$), los multiplica por sus pesos correspondientes ($W$), suma todos los resultados y le añade el sesgo ($b$). Matemáticamente: $z = Wx + b$.


**Keras**
