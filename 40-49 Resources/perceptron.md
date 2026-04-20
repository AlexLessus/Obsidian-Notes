### Definición Teórica

El **perceptrón** es el modelo más simple de una red neuronal con alimentación hacia delante (_feed-forward_) de una sola capa. Fue propuesto originalmente por **Frank Rosenblatt** en 1958 y se inspira en el funcionamiento biológico de una neurona.

Desde una perspectiva de ingeniería, un perceptrón es un **clasificador lineal**. Esto significa que su objetivo es encontrar un **hiperplano** (una línea en 2D, un plano en 3D) que sea capaz de separar dos clases de datos.

n^2 al aumentar las salidas

### ¿Cómo funciona? (La analogía del "Compilador")
Si vienes de Java, piensa en el perceptrón como un método que recibe un arreglo de entradas y devuelve un resultado binario (0 o 1). El proceso tiene cuatro componentes clave:

1. **Entradas ($x_1, x_2, ..., x_n$):** Son los atributos de tus datos (features).
2. **Pesos ($w_1, w_2, ..., w_n$):** Representan la importancia de cada entrada. El entrenamiento del modelo consiste precisamente en ajustar estos valores (es como la fase de "compilación" donde ajustamos los parámetros para que el ejecutable funcione).
3. **Función de Suma:** El perceptrón calcula una suma ponderada de sus entradas: $\sum w_i x_i + umbral$.    
4. **Función de Activación (Escalón):** Si la suma supera un valor umbral, la neurona se "dispara" (devuelve 1); de lo contrario, devuelve 0.

