Tags: [[Aprendizaje Automático]] [[Python]]
- **Clasificación y Regresión**: El aprendizaje supervisado se divide en dos tipos principales: clasificación, que se utiliza para predecir en qué categoría cae una observación, y regresión, para predecir un valor continuo.
- **Preparación de Datos**: Se enfatizó la importancia de preparar tus datos antes de entrenar un modelo. Los datos deben estar libres de valores faltantes, en formato numérico y almacenados adecuadamente utilizando pandas DataFrames, Series o matrices de NumPy.
- **Flujo de Trabajo de scikit-learn**: Aprendiste el flujo de trabajo general para usar scikit-learn para construir un modelo de aprendizaje supervisado, que implica importar un modelo, ajustarlo a los datos y luego hacer predicciones. Por ejemplo:
``` python
from sklearn.neighbors import KNeighborsClassifier 
model = KNeighborsClassifier() 
model.fit(X, y) 
predictions = model.predict(X_new)
```
- **Clasificación Binaria**: Se puso un enfoque específico en la clasificación binaria, donde predices uno de dos posibles resultados, como si un correo electrónico es spam o no.

# KNN
- Usamos el algoritmo k-Nearest Neighbors (KNN) para predecir etiquetas de datos nuevos.
- KNN funciona mirando los vecinos más cercanos y votando por la etiqueta más común.
- Se entrena el modelo con datos etiquetados y luego se usa para predecir en datos sin etiquetas.
- Se construye un modelo KNN en Python usando scikit-learn y se aplican conceptos como la selección de vecinos y predicción.

Ejemplo de ajuste de datos para clasificador
``` Python
# Import KNeighborsClassifier
from sklearn.neighbors import KNeighborsClassifier

y = churn_df["churn"].values
X = churn_df[["account_length", "customer_service_calls"]].values

# Create a KNN classifier with 6 neighbors
knn = KNeighborsClassifier(n_neighbors=6)

# Fit the classifier to the data
knn.fit(X, y)
```


Ejemplo de Predecir KNN: k vecinos más cercanos
```Python
X_new = np.array([[30.0, 17.5],
                  [107.0, 24.1],
                  [213.0, 10.9]])

# Predict the labels for the X_new
y_pred = knn.predict(X_new)

# Print the predictions
print("Predictions: {}".format(y_pred))
```


# Medir el rendimiento del modelo
- La precisión (accuracy) mide qué porcentaje de predicciones son correctas.
- Para evaluar un modelo, se divide el conjunto de datos en entrenamiento y prueba.
- Se entrena el modelo con los datos de entrenamiento y se evalúa con los datos de prueba.
- Se usa `train_test_split` para hacer esta división, asegurando que las proporciones de las clases sean iguales en ambos conjuntos.
- Se ajusta un modelo, como KNN, y se calcula su precisión con `score`.
- Se puede analizar cómo cambia la precisión con diferentes valores de k para entender el equilibrio entre underfitting y overfitting.
--- 
## Accuracy - Precisión
Es una métrica que nos indica qué porcentaje de las predicciones del modelo son correctas.

Se calcula así:
```
Precisión = (Número de predicciones correctas) / (Total de predicciones)
```

Por ejemplo, si tienes 100 predicciones y 88 son correctas, la precisión será:
```
88 / 100 = 0.88 o 88%
```

En código, si usas un modelo en scikit-learn, puedes obtener la precisión con el método `.score()`, que recibe los datos de prueba y sus etiquetas:
``` python
accuracy = modelo.score(X_test, y_test)
```
Este método calcula automáticamente cuántas predicciones del modelo coinciden con las etiquetas reales y devuelve ese porcentaje.

>Es importante recordar que una alta precisión indica que el modelo predice bien en los datos que se usan para evaluarlo, pero no siempre significa que funcione igual de bien en datos nuevos, especialmente si el conjunto de datos es muy pequeño o tiene clases desbalanceadas.

---
# División de datos
La división de datos para entrenamiento es un paso importante para evaluar cómo de bien puede generalizar un modelo a datos nuevos.

Primero, usamos la función `train_test_split` de `sklearn.model_selection`. Esta función toma nuestras características (X) y nuestras etiquetas (y) y las divide en dos conjuntos: uno para entrenar el modelo y otro para probarlo.

### Ejemplo Dividir datos
``` python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, random_state=42, stratify=y
)
```
- `test_size=0.3` significa que el 30% de los datos se usará para probar, y el 70% para entrenar.
- `random_state=42` asegura que la división sea la misma cada vez que corras el código, para reproducibilidad.
- `stratify=y` mantiene la misma proporción de clases en ambos conjuntos, lo cual es importante si tienes clases desbalanceadas.

De esta forma, el modelo se entrena con `X_train` y `y_train`, y luego se evalúa con `X_test` y `y_test`. Esto ayuda a entender cómo funcionará en datos que no ha visto antes.

# Entrenamiento
Para entrenar y evaluar un modelo en scikit-learn, seguimos estos pasos básicos:
1. **Entrenar el modelo:** usamos el método `.fit()` con los datos de entrenamiento (`X_train` y `y_train`). Esto ajusta el modelo a esos datos.    
2. **Evaluar el modelo:** usamos el método `.score()` con los datos de prueba (`X_test` y `y_test`). Esto calcula la precisión del modelo en datos que no ha visto durante el entrenamiento.

```python
from sklearn.neighbors import KNeighborsClassifier

# Crear el modelo
knn = KNeighborsClassifier(n_neighbors=5)

# Entrenar el modelo con los datos de entrenamiento
knn.fit(X_train, y_train)

# Evaluar el modelo con los datos de prueba
accuracy = knn.score(X_test, y_test)

print(f'Precisión en datos de prueba: {accuracy:.2f}')
```
- `fit()` ajusta el modelo a los datos de entrenamiento.
- `.score()` calcula qué tan bien predice en los datos de prueba.


Ejemplo de división entrenamiento/prueba + calculo de precisión 
```python
# Import the module
from sklearn.model_selection import train_test_split  

X = churn_df.drop("churn", axis=1).values
y = churn_df["churn"].values

# Split into training and test sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42, stratify=y)

knn = KNeighborsClassifier(n_neighbors=5)  

# Fit the classifier to the training data
knn.fit(X_train, y_train)  

# Print the accuracy
print(knn.score(X_test, y_test))
```
output
`<script.py> output: 0.8740629685157422`


# Sobreajuste e infra ajuste

```python
# Create neighbors
neighbors = np.arange(1, 13)
train_accuracies = {}
test_accuracies = {}  

for neighbor in neighbors:
    # Set up a KNN Classifier    
    knn = KNeighborsClassifier(n_neighbors=neighbor)
    
    # Fit the model
    knn.fit(X_train, y_train)
    
    # Compute accuracy
    train_accuracies[neighbor] = knn.score(X_train, y_train)
    test_accuracies[neighbor] = knn.score(X_test, y_test)

print(neighbors, '\n', train_accuracies, '\n', test_accuracies)
```



# Visualizar la complejidad del modelo
``` python
# Add a title
plt.title("KNN: Varying Number of Neighbors")

# Plot training accuracies
plt.plot(neighbors, train_accuracies.values(), label="Training Accuracy")
  
# Plot test accuracies (x,y)
plt.plot(neighbors, test_accuracies.values(), label="Testing Accuracy")
  
plt.legend()
plt.xlabel("Number of Neighbors")
plt.ylabel("Accuracy")
  
# Display the plot
plt.show()
```
Output
![[Pasted image 20260217234048.png]]






![[Pasted image 20260217231602.png]]

# Regresión
La regresión se usa para predecir valores continuos, como precios o niveles de glucosa.

``` python
# Cargar el dataset y mostrar las primeras filas
import pandas as pd
data = pd.read_csv('health_data.csv')
print(data.head())

# Separar las características y la variable objetivo
X = data.drop('blood_glucose', axis=1)
y = data['blood_glucose'].values

# Seleccionar solo la característica de IMC
X_bmi = X.iloc[:, 3].values

# Asegurar que X_bmi tenga la forma correcta (2D)
import numpy as np
X_bmi = X_bmi.reshape(-1, 1)

# Visualizar la relación
import matplotlib.pyplot as plt
plt.scatter(X_bmi, y)
plt.xlabel('Índice de Masa Corporal (IMC)')
plt.ylabel('Niveles de glucosa en sangre')
plt.show()

# Crear y ajustar el modelo de regresión lineal
from sklearn.linear_model import LinearRegression
reg = LinearRegression()
reg.fit(X_bmi, y)

# Hacer predicciones
predicciones = reg.predict(X_bmi)

# Graficar la línea de regresión
plt.scatter(X_bmi, y)
plt.plot(X_bmi, predicciones, color='black')
plt.xlabel('Índice de Masa Corporal (IMC)')
plt.ylabel('Niveles de glucosa en sangre')
plt.show()

```



## **Ajustar una línea a los datos (regresión simple):**
Consiste en encontrar la mejor línea recta que pase cerca de los datos, usando métodos como `np.polyfit`. La línea se define por su pendiente y su intercepto.
``` python
import numpy as np
import matplotlib.pyplot as plt

# Datos de ejemplo
x = np.array([1, 2, 3, 4, 5])
y = np.array([2, 4, 5, 4, 5])

# Ajustar una línea usando numpy
coef = np.polyfit(x, y, 1)  # grado 1 para línea recta
a, b = coef
print(f"Pendiente (a): {a}, Intercepto (b): {b}")

# Graficar
plt.scatter(x, y)
plt.plot(x, a*x + b, color='red')
plt.show()
```

## Función de pérdida: suma de residuos al cuadrado (RSS):
Es la suma de los cuadrados de las diferencias entre los valores observados y los predichos por la línea. Minimizar esta suma ayuda a encontrar la mejor línea ajustada a los datos.
```python
# Residuales
residuals = y - (a * x + b)

# RSS
rss = np.sum(residuals ** 2)
print(f"RSS: {rss}")
```

## Regresión lineal múltiple con scikit-learn:
Cuando tienes varias características, puedes usar `LinearRegression` para ajustar un modelo que predice la variable objetivo en función de todas esas características.
``` python
from sklearn.linear_model import LinearRegression
import numpy as np

# Datos ejemplo con varias características
X = np.array([[1, 2], [2, 1], [3, 4], [4, 3], [5, 5]])
y = np.array([3, 3, 7, 7, 10])

# Crear y ajustar el modelo
model = LinearRegression()
model.fit(X, y)

# Coeficientes
print("Coeficientes:", model.coef_)
print("Intercepción:", model.intercept_)

# Predicciones
y_pred = model.predict(X)
```

## Evaluar el modelo con R-cuadrado y RMSE:
Se usan métricas como R-cuadrado para medir qué porcentaje de la variación en los datos explica el modelo, y RMSE para entender el error promedio en las predicciones.
```python
from sklearn.metrics import mean_squared_error

# R-cuadrado
r2 = model.score(X, y)
print(f"R-cuadrado: {r2}")

# RMSE
rmse = np.sqrt(mean_squared_error(y, y_pred))
print(f"RMSE: {rmse}")
```
## Rendimiento de la regresión
``` python
# Import root_mean_squared_error
from sklearn.metrics import root_mean_squared_error

# Compute R-squared
r_squared = reg.score(X_test, y_test)

# Compute RMSE
rmse = root_mean_squared_error(y_test, y_pred)

# Print the metrics
print("R^2: {}".format(r_squared))
print("RMSE: {}".format(rmse))
```
