
###  Perceptron simple
``` python
import numpy as np
from tensorflow import keras
from tensorflow.keras import layers

# 1. Crear el modelo secuencial
modelo = keras.Sequential()

# 2. Agregar una capa con 1 neurona y 1 variable de entrada (input_dim=1)
modelo.add(layers.Dense(units=1, input_shape=(1,)))

# 3. Compilar el modelo (definir optimizador y función de pérdida)
modelo.compile(optimizer='sgd', loss='mean_squared_error')

# 4. Datos de ejemplo (por ejemplo, y = 2 * x)
X = np.array([1.0, 2.0, 3.0, 4.0], dtype=float)
Y = np.array([2.0, 4.0, 6.0, 8.0], dtype=float)

# 5. Entrenar la neurona
modelo.fit(X, Y, epochs=500, verbose=0)

# 6. Probar la neurona con un nuevo valor (ej. ¿cuánto es 5.0?)
resultado = modelo.predict(np.array([5.0]))
print("Predicción para 5.0:", np.round(resultado))

```