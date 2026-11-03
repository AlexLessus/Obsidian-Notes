Una **Red Neuronal Recurrente (RNN)** es una arquitectura de aprendizaje profundo diseñada específicamente para procesar **datos secuenciales** (como texto, audio, señales biológicas o series temporales) en los que el orden y la dependencia temporal entre los elementos resultan fundamentales.

A diferencia de las redes tradicionales *feedforward* —que procesan cada entrada de manera independiente y sin memoria previa—, las RNN incorporan un **bucle o conexión de retroalimentación interna**. Esto les permite reutilizar la información calculada en pasos temporales previos y mantener una memoria del contexto histórico.

---
### 1. Características Principales
- **Estado Oculto (Hidden State / $h_t$)**: Actúa como la memoria interna del sistema. En cada paso de tiempo $t$, la red calcula un nuevo estado oculto combinando la entrada actual $x_t$ con el estado oculto previo $h_{t-1}$: $$h_t = \tanh(W \cdot x_t + U \cdot h_{t-1} + b)$$
* **Parámetros Compartidos en el Tiempo**: La red aplica las **mismas matrices de pesos** ($W$, $U$) y el mismo vector de sesgo ($b$) a lo largo de todos los pasos temporales de la secuencia.
* **Entrada de Forma Tridimensional**: En los marcos modernos, los datos se representan en tensores de rango 3 con la estructura `(batch_size, timesteps, features)`.
* **Sensibilidad al Orden Temporal**: Procesan la información paso a paso; alterar o invertir el orden de los elementos cambia por completo la representación interna resultante.
* **Entrenamiento mediante BPTT (*Backpropagation Through Time*)**: El cálculo de gradientes se realiza "desenrollando" (*unrolling*) la red a lo largo de los pasos temporales y aplicando la regla de la cadena.
* **Desafío de Dependencias a Largo Plazo**: Las RNN estándar sufren con secuencias extensas debido al fenómeno de **desvanecimiento o explosión del gradiente** (*vanishing/exploding gradients*).

---
### 2. Tipos de Redes Recurrentes

#### A. Por su Celda o Mecanismo de Memoria
1. **RNN Simple / Tradicional (Elman / Jordan)**: Utiliza una transformación lineal básica con función de activación ($tanh$) o sigmoide. Es eficiente para secuencias cortas, pero propensa al desvanecimiento del gradiente.
2. **LSTM (*Long Short-Term Memory*)**: Introducida por Hochreiter y Schmidhuber (1997). Introduce una celda de memoria interna (*cell state*) y un sistema de **puertas** (*gates*: olvido, entrada y salida) que regulan dinámicamente qué información conservar o descartar, permitiendo aprender dependencias a largo plazo.
3. **GRU (*Gated Recurrent Unit*)**: Introducida en 2014 por Cho et al.. Es una versión simplificada y computacionalmente más ligera del LSTM que fusiona estados y gestiona el flujo de información con dos puertas principales (*reset* y *update*).

#### B. Por su Topología y Flujo de Datos
* **Unidireccional**: Recorre la secuencia únicamente en orden cronológico ($t_1 \to t_n$).
* **Bidireccional (BiRNN / BiLSTM / BiGRU)**: Utiliza dos redes recurrentes en paralelo; una procesa la secuencia en orden cronológico y la otra en sentido inverso, concatenando o sumando sus representaciones para comprender el contexto pasado y futuro simultáneamente.
* **Apiladas (*Stacked RNN*)**: Múltiples capas recurrentes dispuestas en profundidad, donde la secuencia de salida de una capa intermedia sirve de entrada a la siguiente.
* **Secuencia a Secuencia (*Seq2Seq / Encoder-Decoder*)**: Una RNN codificadora comprime la secuencia de entrada en un vector de contexto, y una RNN decodificadora genera la secuencia de salida correspondiente.

---
### 3. Aplicaciones de las Redes Recurrentes
* **Procesamiento de Lenguaje Natural (PLN)**: Modelado de lenguaje, análisis de sentimientos, etiquetado de secuencias y corrección gramatical.
* **Traducción Automática**: Modelos *seq2seq* que mapean texto de un idioma de origen a uno de destino.
* **Reconocimiento y Síntesis de Voz**: Transcripción de señales acústicas a fonemas o texto (*Speech-to-Text*) y generación de voz.
* **Pronóstico de Series Temporales (*Time Series Forecasting*)**: Predicción meteorológica, consumo energético y evolución de precios financieros o transacciones.
* **Reconocimiento de Escritura Manuscrita**: Lectura y transcripción de texto manuscrito continuo.
* **Bioinformática y Medicina**: Detección de homología de proteínas, localización subcelular, decodificación neuroprotésica y análisis de vías clínicas.
---
### 4. Implementación y Programación
#### Implementación en TensorFlow / Keras
```python
import numpy as np
from tensorflow import keras
from tensorflow.keras import layers

# 1. Parámetros del problema
num_samples = 1000
timesteps = 10         # Pasos de tiempo en la secuencia
input_features = 4     # Características por paso
num_classes = 1

# 2. Generación de datos sintéticos (Tensor 3D: muestras, pasos, características)
X_train = np.random.random((num_samples, timesteps, input_features))
y_train = np.random.randint(0, 2, size=(num_samples, num_classes))

# 3. Construcción del modelo recurrente (Sequential API)
model = keras.Sequential([
    keras.Input(shape=(timesteps, input_features)),
    # Capa recurrente (se puede alternar entre SimpleRNN, LSTM o GRU)
    layers.SimpleRNN(units=32, return_sequences=False),
    # Capa de salida para clasificación binaria
    layers.Dense(units=1, activation="sigmoid")
])

# 4. Compilación del modelo
model.compile(
    optimizer="rmsprop",
    loss="binary_crossentropy",
    metrics=["accuracy"]
)

# 5. Entrenamiento
model.fit(X_train, y_train, epochs=5, batch_size=32, validation_split=0.2)
```

```
Epoch 1/5
25/25 ━━━━━━━━━━━━━━━━━━━━ 1s 16ms/step - accuracy: 0.5188 - loss: 0.6970 - val_accuracy: 0.4850 - val_loss: 0.7053
Epoch 2/5
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 6ms/step - accuracy: 0.5188 - loss: 0.6940 - val_accuracy: 0.4750 - val_loss: 0.7033
Epoch 3/5
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 6ms/step - accuracy: 0.5412 - loss: 0.6926 - val_accuracy: 0.4600 - val_loss: 0.7020
Epoch 4/5
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 7ms/step - accuracy: 0.5462 - loss: 0.6891 - val_accuracy: 0.5000 - val_loss: 0.7019
Epoch 5/5
25/25 ━━━━━━━━━━━━━━━━━━━━ 0s 6ms/step - accuracy: 0.5587 - loss: 0.6900 - val_accuracy: 0.4650 - val_loss: 0.6997

<keras.src.callbacks.history.History at 0x7df0cf42e7b0>
```
