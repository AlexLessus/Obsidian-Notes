#MachineLearning #AI 

El **cerebro humano está hecho de unas 86 000 millones de neuronas.** Estas células están interconectadas y especializadas en la recepción de estímulos y en la conducción del impulso nervioso entre ellas. Cada neurona puede recibir el estímulo de otras 10 mil, con lo cual la cantidad de redes neuronales en el cerebro es enorme.

Se puede definir como un sistema que permite establecer una relación entre entradas y salidas inspiradas en el sistema nervioso y diferenciándose de la computación tradicional, ya que estos no utilizan una algoritmia secuencial. Las redes neuronales artificiales se comportan como un cerebro humano, en donde se procesa la información en paralelo, con la posibilidad de aprender y generalizar situaciones no incluidas en procesos de entrenamiento.

Las redes de neuronas artificiales son una herramienta atractiva para solucionar problemas de clasificación como el reconocimiento de caracteres manuscritos, el reconocimiento de palabras habladas, y el diagnóstico de diferentes enfermedades.


Neuronas de entrada
	Conectada a nuestros sentidos
Neuronas de trabajo
	Trabajan
Neuronas de salida
	Generan una salida


### Entrada y salida
Las entradas y salidas de una neurona pueden ser clasificadas en dos grandes grupos: Binarias o Continuas

Las Neuronas Binarias
- Solo admiten dos valores posibles
- Por lo general se utilizan dos alfabetos

Las Neuronas Continuas


### Pesos
El peso sináptico *wij* define la fuerza de una conexión sináptica entre dos neuronas, la neurona presináptica *i* y le neurona postsináptica *j*

Los pesos sinapticos pueden tomar valores positivos, negativos o cero.

En caso de una entrada positiva, un peso positivo actúa como exitador, un pesos negativo actúa como inhibidor.
En caso de cero, no existe comunicación entre el par de neuronas.


### Regla de propagación 
La regla de propagación determina el potencial resultante de la interacción de la neurona i con las N neuronas vecinas. La regla de propagación más simple y utilizada consiste en realizar una suma de las entradas ponderadas con sus pesos correspondientes:

![[Pasted image 20260922074410.png]]


### Función de activación 
La función de activación determina el estado de activación actual de la neurona en base al potencial resultante 𝑛𝑒𝑡𝑖 y al estado de activación anterior de la neurona 𝑎𝑖(𝑡 − 1). 

Por lo general, se omite el estado de activación anterior y solo se toma el valor actual resultante de la regla de propagación.

El estado de activación de la neurona para un determinado instante de tiempo t puede ser expresado de la siguientes maneras:

$a_i(t)=f(a_i(t-1),net_i(t))$ Si f a se toma en cuenta el estado anterior de activación 

$a_i(t)=f(net_i(t))$ No se toma en cuenta el estado anterior de activación

![[Pasted image 20260922074635.png]]

### Función de salida
La función de salida proporciona el valor de salida de la neurona, en base al estado de activación de la neurona

$y_i(t)=f(net_i(t))$

## Estructura de una red 
### Capa de entrada 
No realizan ningún proceso, sólo dejan pasar la información que se quiere manejar en la red. 

### Capas ocultas
Reciben las entradas y tienen la función de proporcionar un mejor aprendizaje. Pueden estar o no presentes en una red depende de la topología de la red. Una red puede ser monocapa o multicapa. 

### Capa de salida 
Se encargan de proporcionar la salida del sistema indicado, según su aprendizaje, una respuesta correcta o incorrecta

### Interconexiones entre las neuronas
Son las sinapsis de la red, estas tienen asociadas un peso sináptico, y son direccionales. 
Cuando la conexión se establece entre dos neuronas de una misma capa se conocen como conexiones laterales o conexiones intra-capa. 
Si la conexión se establece entre neuronas de distintas capas se la denomina conexión inter-capa. 
Si la conexión se produce en el sentido inverso al de entrada-salida la conexión se llama recurrente o realimentada.

## Clasificación de las redes neuronales 
### Por su topología: 
Neurona 
- Monocapa 
- Multicapa 
- Recurrente 

Por el tipo de aprendizaje: 
- Supervisado 
- No supervisado 
- Hibrido 

Por el tipo de representación de la información
- Discreta
- Continua
- Hibrida

Tipo de asociación entre las informaciones de entrada y salida 
- Redes heteroasociativas 
- Redes autoasociativas 

Tipo de conexión 
- Estática (Feedforward) 
- Dinámica (Feedback)

## Características 
#### Aprendizaje adaptativo: 
las redes neuronales, pueden comportarse en función de un entrenamiento con una serie de ejemplos ilustrativos. De esta forma, no es necesario elaborar un modelo a priori, ni establecer funciones probabilísticas. Una red neuronal artificial es adaptativa porque puede modificarse constantemente con el fin de adaptarse a nuevas condiciones de trabajo. 

#### Autoorganización: 
mientras que el aprendizaje es un proceso donde se modifica la información interna de la red neuronal artificial, la autoorganización consiste en la modificación de la red completa con el fin de llevar a cabo un objetivo específico.
Autoorganización significa generalización, de esta forma una red puede responder a datos o situaciones que no ha experimentado antes, pero que puede inferir sobre la base de su entrenamiento. Esta característica es muy útil sobre todo cuando la información de entrada es poco clara o se encuentra incompleta

#### Tolerancia a fallos: 
En la computación tradicional la pérdida de un fragmento pequeño de información puede acarrear comúnmente la inutilización del sistema. Las redes neuronales artificiales poseen una alta capacidad de tolerancia a fallos. 
Se entiende por ello que las redes pueden reconocer patrones de información con ruido, distorsión o incompletos, pero que, además, pueden seguir trabajando aunque se destruya parte de la red (con cierta degradación). 
La explicación de este fenómeno se encuentra en que mientras la computación tradicional almacena la información en espacios únicos, localizados y direccionables, las redes neuronales lo hacen de forma distribuida y con un alto grado de redundancia.

#### Operación en tiempo real: 
las redes neuronales artificiales, de todos los métodos existentes, son las más indicadas para el reconocimiento de patrones en tiempo real, debido a que trabajan en paralelo actualizando todas sus instancias simultáneamente. 
Es importante destacar que esta característica solo se aprecia cuando se implementan redes con hardware especialmente diseñados para el procesamiento paralelo. 

#### Fácil inserción en la tecnología existente: 
es relativamente sencillo obtener chips especializados para redes neuronales que mejoran su capacidad en ciertas tareas. Ello facilita la integración modular en los sistemas existentes.

## 

#### Self Organizing maps

#### Liquid state machines

#### Perceptron

#### Backpropagation

#### Feed forward

#### Hopefield Network 

#### Boltzmann machine 

#### Deep believe network
