Tags: [[Python]] [[Sintaxis Python]]

# Selectivas - Condicionales
## if 
sintaxis: i
f condición: 
	instrucciones 
	instrucciones 

ejemplo: 
if num>100: 
	print (str(num)+" adios") 
	
if condición: 
	instrucciones 
	instrucciones 
else: 
	instrucciones 
	instrucciones

ejemplo: 
a=int(input("dame un numero ")) 
b=int(input("dame otro numero ")) 


## match
match algo similar al switch-case en otros lenguajes, uso a partir de la versión 3.10, se le conoce como compración de patrones 

``` python
match Sujeto: 
	case Patron1: Código si se cumple el Patron1 
	case Patron2: Código si se cumple el Patron2 
	case Patron3: Código si se cumple el Patron3 
	case ...
```

``` python
cdad=”GDL” 
match cdad: 
	case ”GZM”: ciudad=”Ciudad Guzmán” 
	case ”GDL”: ciudad=”Guadalajara” 
	case ”OCL”: ciudad=”Ocotlán” 
	case _: ciudad=”no definida” p
rint(ciudad)
```


---
# Estructuras de control y selección

## Iterativas: 
## while 
Sintaxis: 
inicialización 
while condición: 
	instrucciones
	instrucciones
cambio del valor de la variable de control

``` python
n=0 
while n<10: 
	print (n) 
	n+=1
```

## **break**
``` Python
while True: 
	num=int(input("-> ")) 
	if num>100: 
		print (str(num)+" adios") 
		break 
	else: 
		print (num)
		print("para terminar el valor debe ser mayor a 100")
```

## continue
omite la iteración actual y continua con la siguiente
``` python
n=0 
while n<15: 
	n+=1 
	if n%2==0: 
		continue 
	print(n)
```

## pass
se utiliza para cuando se desea que no se haga algo, que haga nada
```python
n=0 
while n<15:
	n+=1 
	if n%2==0: 
		pass 
	print(n)
```

# for … in

``` python
for x in secuencia: 
	print(x)
```

### range() 
función que permite generar un rango de valores y es muy utilizado en los ciclos for … in como contador

**range(n)** 
range(10) rango de valores del 0 al 9
ejemplo: 
``` python
for i in range(10): print(i)
```

**range(inferior, superior)** 
range(5, 10) rango de valores del 5 al 9
ejemplo: for
``` python
i in range(5,10): print(i)
```
**range (inferior, superior, salto)**
range(1,10,2) rango de valores 1,3,5,7,9

``` python
for i in range(1,10,2): 
	print(i)
```

---
# Módulos y funciones del lenguaje

Algunas funciones: 
```python
len(dato) #regresa la cantidad de caracteres de la cadena 
type(dato) #indica el tipo de dato 
dir(objeto) #muestra los elementos de un módulo 
help(objeto) #muestra información del elemento en cuestión 
del(secuencia) #borra un elemento de una secuencia mutable
```

Funciones para conversión de datos: 
``` python
int() 
int(numero, base) 
float() 
complex() 
str() 
bool() 
tuple() 
list() 
dict() 
set()
```

Más funciones:
``` python
bin() #representación binaria de un número entero 
oct() #representación octal de un número entero 
hex() #representación hexadecimal de un número entero 
abs() #valor absoluto de un valor numérico 
round() #redondear un valor 
divmod(a,b) #regresa una tupla con el resultado de la división y su residuo 
eval() #evalua una expresión contenida en una cadena y obtiene su resultado 
x=eval("12*2") 
y=eval('x/2') #x ya tiene un valor definido, en caso contrario marca error 
chr(i) # regresa una cadena de un caracter de acuerdo al valor numérico del argumento 
ord(caracter) #regresa el valor Unicode del caracter del argumento 
enumerate(secuencia, start=0) #retorna el elemento de la secuencia asociado a un valor numérico consecutivo 
vocales=”aeiou” 
for par in enumerate(vocales, 1): 
	print(par)
exec(código) #ejecuta el codigo 
codigo='x=input("dame un numero ")' 
exec(codigo)

max() #regresa el valor mayor de dos o más argumentos o secuencia 
min() #regresa el valor menor de dos o más argumentos o secuencia 
open() #crear o abrir achivos 
close() #cerrar el flujo de un archivo 
reversed(secuencia) #regresa una secuencia invertida 
sorted(secuencia) #ordena los datos
```

## Módulos
Un módulo se puede decir que es un programa de Python que contiene declaraciones, clases y funciones las cuales se pueden utilizar en otros programas (o módulo).
Se utilizará la palabra reservada import para indicar que vamos a importar ese módulo (o paquete, un paquete puede contenes varios módulos y paquetes) o funciones o clases contenidas en ese módulo.

``` python
import nombreMódulo 
import paquete.modulo
```
Para hacer uso de las funciones contenidas en éste, hacemos referencia al nombre del módulo ponemos un punto y después el nombre del recurso que necesitamos: modulo.funcion

Cuando importamos podemos indicar solo lo que queremos que se import de la manera siguiente:

``` python
from paquete import modulo 
from paquete import modulo as alias
#En esta opción podemos poner un alias a nuestro modulo para facilitar su referencia
from modulo import funcion
#En este último caso al hacer uso del recurso importado, no requerimos poner la referencia al momento de utilizarlo.
```
Para cualquiera de los casos, podemos importar más de un módulo de un paquete, o más de una funcion o clase de un módulo, para ello simplemente vamos separando con una coma la lista de recursos a importar.

## Módulos y funciones del lenguaje

```python
math # funciones matemáticas 
random # funciones números aleatorios 
datetime # ofrece clases para gestionar fechas y tiempos tanto de manera simple como compleja 
time # funciones manejo de tiempo 
sys # ofrece parametros y funciones del sistema os # provee funciones para interactuar con el sistema operativo 
shutil # tareas diarias de administración de archivos y directorios, este módulo provee una interfaz de más alto nivel que es más fácil de usar 
glob # provee una función para hacer listas de archivos a partir de búsquedas con comodines en directorios 
argparse # provee un mecanismo para procesar argumentos recibidos vía línea de comandos 
re # provee herramientas de expresiones regulares para un procesamiento avanzado de cadenas 
statistics # calcula propiedades de estadística básica (la media, mediana, varianza, etc) de datos numéricos 
array # provee un objeto array() (vector) que es como una lista que almacena sólo datos homogéneos y de una manera más compacta 
enum # soporte de enumeraciones 
pickle # serialización de objetos de Python 
io # herramientas principales para trabajar con streams 
turtle # gráficos con la tortuga 
socket # funciones para la creación y manejo de sockets 
threading # manejo de hilos
```
