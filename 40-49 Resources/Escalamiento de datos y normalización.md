Alexis De Jesus Perez Carmona
### 1. ¿Qué es el Escalamiento y la Normalización?
En el aprendizaje automático, los conjuntos de datos suelen contener características (columnas) que varían drásticamente en sus magnitudes, unidades y rangos. Por ejemplo, una variable puede medir la edad (de 18 a 80 años) y otra el salario anual (de $10,000 a $150,000).

El **escalamiento** y la **normalización** son técnicas de preprocesamiento matemático que transforman los datos numéricos para que todas las variables operen en una escala similar, sin perder la información sobre las distancias o diferencias relativas entre los valores originales.

### 2. ¿Por qué es necesario llevarlo a cabo?
1. **Algoritmos basados en distancia:** Modelos como K-Vecinos Más Cercanos (KNN) o Máquinas de Vectores de Soporte (SVM) calculan la distancia euclidiana entre los puntos de datos. Si una variable tiene un rango de miles y otra de decimales, la variable de los miles dominará matemáticamente el modelo, haciendo que el algoritmo ignore casi por completo la variable pequeña.
2. **Optimización del Descenso de Gradiente:** Algoritmos como las Redes Neuronales y la Regresión Logística utilizan el descenso de gradiente para ajustar sus pesos. Si las variables tienen escalas muy diferentes, la función de costo se vuelve alargada, lo que hace que el modelo tarde muchísimo en converger (entrenar) o que nunca encuentre el punto óptimo.

---
### 3. Técnicas Principales (Cómo se lleva a cabo)
Aunque a veces los términos se usan como sinónimos, en la práctica y en librerías como _Scikit-Learn_, representan transformaciones matemáticas distintas:

#### A) Escalamiento Min-Max (Normalización)
Transforma los datos para que encajen exactamente en un rango predefinido, típicamente entre **0 y 1**. Es muy útil cuando no asumes que tus datos tienen una distribución normal (campana de Gauss) o cuando necesitas enmarcar los datos en márgenes estrictos (como procesar imágenes donde los píxeles van de 0 a 255).

La fórmula matemática que se aplica a cada valor es:

$$X_{scaled} = \frac{X - X_{min}}{X_{max} - X_{min}}$$

#### B) Estandarización (Z-Score Scaling)
A diferencia del Min-Max, la estandarización no limita los datos a un rango exacto. En su lugar, centra los datos para que tengan una **media ($\mu$) de 0** y una **desviación estándar ($\sigma$) de 1**. Es la técnica preferida para algoritmos como SVM, Regresión Logística y Redes Neuronales, ya que maneja mucho mejor los valores atípicos (_outliers_).

La fórmula matemática es:

$$X_{stand} = \frac{X - \mu}{\sigma}$$

---
### 4. Ejemplo Práctico
Imaginemos que estamos trabajando con los registros de extracción de una sesión de café V60. Tenemos dos variables: los **Gramos de café** (que varían poco, de 15 a 20) y el **Agua en mililitros** (que varía mucho, de 250 a 330).

Si alimentamos un modelo directamente con esto, el agua dominará completamente la ecuación. Aquí tienes cómo se soluciona en Python usando `pandas` y `scikit-learn`:
``` python
import pandas as pd
from sklearn.preprocessing import MinMaxScaler, StandardScaler

# 1. Nuestros datos originales (Gramos vs Mililitros)
datos = {
    'Gramos_Cafe': [15.0, 18.0, 20.0, 16.5, 19.0],
    'Agua_ml': [250.0, 300.0, 330.0, 275.0, 310.0]
}

df = pd.DataFrame(datos)
print("--- Datos Originales ---")
print(df)
print("\n")

# 2. Aplicando Escalamiento Min-Max (Rango 0 a 1)
min_max_scaler = MinMaxScaler()
df_minmax = pd.DataFrame(
    min_max_scaler.fit_transform(df), 
    columns=df.columns
)

print("--- Escalamiento Min-Max (0 a 1) ---")
print(df_minmax)
print("\n")

# 3. Aplicando Estandarización (Media 0, Desviación Estándar 1)
std_scaler = StandardScaler()
df_std = pd.DataFrame(
    std_scaler.fit_transform(df), 
    columns=df.columns
)

print("--- Estandarización (Z-Score) ---")
print(df_std)
```
![[Pasted image 20260403123503.png|421]]
![[Pasted image 20260403123513.png]]
![[Pasted image 20260403123521.png]]