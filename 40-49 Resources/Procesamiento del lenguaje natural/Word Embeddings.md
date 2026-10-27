### **Concepto Fundamental de Word Embeddings**
Los **word embeddings** (o _incrustaciones de palabras_) son representaciones numéricas de las palabras en forma de **vectores densos** de dimensión reducida (típicamente entre 50 y 1000 dimensiones). Se diferencian radicalmente de los modelos tradicionales (como la _Bolsa de Palabras_ o _TF-IDF_), los cuales generan **vectores esparcidos (_sparse_)** de longitud igual al tamaño del vocabulario ($|V|$) compuestos mayoritariamente por ceros.

- **Hipótesis Distribucional:** Se fundamentan en el principio lingüístico de J.R. Firth (1957) y Ludwig Wittgenstein (1953), según el cual el significado de una palabra se define por las palabras que suelen aparecer a su alrededor en el uso habitual del lenguaje. Dos palabras que comparten entornos contextualmente similares terminan ubicadas en posiciones cercanas dentro del espacio vectorial.
- **Ventajas frente a modelos esparcidos:** Al utilizar dimensiones continuas y densas, los clasificadores aprenden un número significativamente menor de parámetros, lo que ayuda a prevenir el sobreajuste (_overfitting_), mejora la capacidad de generalización y captura de forma efectiva la **sinonimia** y similitud semántica entre palabras.
- **Embeddings Estáticos vs. Contextuales:** Los modelos estáticos como **Word2Vec**, **GloVe** y **FastText** asignan un único vector fijo a cada palabra sin importar dónde aparezca. Por su parte, los modelos modernos basados en **Transformers** (como BERT) generan **embeddings contextuales**, calculando vectores dinámicos que cambian según la oración completa.

---

### **Fórmulas Matemáticas Clave**

#### **a) Similitud del Coseno (Cosine Similarity)**

Mide la cercanía semántica o alineación entre dos vectores de palabras $(v)$ y $(w)$ dividiendo su producto punto por el producto de sus normas L2 (longitudes vectoriales):

$$\text{cosine}(v, w) = \frac{v \cdot w}{\|v\| \|w\|} = \frac{\sum_{i=1}^{d} v_i w_i}{\sqrt{\sum_{i=1}^{d} v_i^2} \cdot \sqrt{\sum_{i=1}^{d} w_i^2}}$$
#### **b) Word2Vec (Skip-gram con Muestreo Negativo / SGNS)**
En el algoritmo Skip-gram, se calcula la probabilidad de que una palabra de contexto \(c\) aparezca realmente cerca de una palabra objetivo \(w\) aplicando la función sigmoide (\(\sigma\)) al producto punto de sus vectores:
$$P(+ \mid w, c) = \sigma(c \cdot w) = \frac{1}{1 + \exp(-c \cdot w)}$$
La función de pérdida ($L$) que el algoritmo minimiza mediante descenso de gradiente estocástico para un par positivo $(w, c_{\text{pos}})$ y ($k$) palabras de ruido o muestras negativas $c_{\text{neg}}$ es:
$$L = -\left[ \log \sigma(c_{\text{pos}} \cdot w) + \sum_{i=1}^{k} \log \sigma(-c_{\text{neg}_i} \cdot w) \right]$$
#### **c) Modelo del Paralelogramo (Analogías Vectoriales)**
Para resolver analogías de la forma _"a es a b como a* es a qué?"_($a : b :: a^* : b^*$), se calcula el vector objetivo $\hat{b}^*$ que minimiza la distancia al vector resultado:
$$\hat{b}^* = \arg\min_{x} \text{distance}\Big(x, \, b - a + a^*\Big)$$
---
### **Ejemplos Prácticos e Interpretación**
- **Álgebra Vectorial y Analogías Relacionales:** Gracias a la geometría del espacio vectorial, es posible realizar operaciones aritméticas directas entre conceptos. La ecuación de analogía más célebre deduce el concepto de realeza femenina: 
	$$\vec{V}_{\text{king}} - \vec{V}_{\text{man}} + \vec{V}_{\text{woman}} \approx \vec{V}_{\text{queen}}$$De manera similar, el modelo extrae relaciones geográficas (como $\vec{V}_{\text{Paris}} - \vec{V}_{\text{France}} + \vec{V}_{\text{Italy}} \approx \vec{V}_{\text{Rome}}$) o variaciones morfológicas (como comparativos y superlativos $\vec{V}_{\text{slower}} \to \vec{V}_{\text{slowest}}$).
    
- **Medición de Similitud Semántica:** Al evaluar la cercanía entre vectores, palabras del mismo dominio semántico (como _digital_ e _information_) producen un producto punto alto y un ángulo pequeño ($\text{cos} \approx 0.996$), mientras que conceptos no relacionados (como _cherry_ e _information_) obtienen valores cercanos a  ($0$ ($\text{cos} \approx 0.018$).
- **Manejo de Palabras Fuera de Vocabulario (_OOV_) en FastText:** A diferencia de Word2Vec, FastText descompone cada palabra en una bolsa de $n$-gramas de caracteres delimitados. Por ejemplo, para la palabra `<where>` con $n=3$, genera los sub-tokens `<wh`, `whe`, `her`, `ere`, `re>`. El vector final de la palabra es la suma de los vectores de sus subpalabras, lo que le permite construir representaciones numéricas incluso para términos desconocidos o con errores ortográficos.