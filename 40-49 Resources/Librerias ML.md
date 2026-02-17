Tags: [[Machine Learning]] [[Aprendizaje Automático]]

## El Core: Manipulación y Cálculo Numérico
- **NumPy:** Es la librería fundamental. Permite el manejo de **tensores** (arrays multidimensionales) de forma extremadamente eficiente. En ML, casi todo se reduce a multiplicaciones de matrices, y NumPy lo hace a velocidad de C.

- **Pandas:** Introduce el concepto de `DataFrame`, que es como una tabla de base de datos o una hoja de Excel en memoria. Te permite limpiar, filtrar y transformar datos estructurados con facilidad.

- **SciPy:** Algoritmos matemáticos y estadísticos "crudos".
## Modelado y Algoritmos
- **Scikit-Learn:** Es la navaja suiza para el Aprendizaje Supervisado y No Supervisado. Incluye desde la **Regresión Lineal** hasta **Random Forest** y **K-Means**. Su gran ventaja es que tiene una API muy consistente: casi todo se resuelve con un `.fit()` (entrenar) y un `.predict()` (inferencia).

- **XGBoost / LightGBM:** Librerías especializadas en algoritmos de _Gradient Boosting_. Son las reinas en competencias de Ciencia de Datos cuando trabajamos con datos tabulares.


## Deep Learning - Redes neuronales
- **TensorFlow:** Desarrollado por Google. Es un framework de bajo nivel muy potente, ideal para producción y despliegue masivo.

- **Keras:** Es la API de alto nivel que corre sobre TensorFlow. Como ingeniero, la amarás porque es muy legible. Crear una red neuronal en Keras es como armar bloques de LEGO.

- **PyTorch:** El gran competidor (de Meta/Facebook). Es muy popular en investigación por su "grafo dinámico", lo que hace que el debugging sea más parecido a la programación imperativa tradicional que ya conoces.

## Visualización y Evaluación
- **Matplotlib:** La librería clásica para crear gráficas. Es un poco ruda pero te da control total sobre cada píxel.
    
- **Seaborn:** Construida sobre Matplotlib, pero orientada a visualización estadística. Genera mapas de calor y distribuciones con un código mucho más limpio.

