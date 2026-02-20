# Tipos de datos estructurados
## Cadenas
Los elementos están delimitados por comillas o apostrofes ”cadena” ’cadena’

Una cadena es inmutable (no se pueden modificar)
- Los elementos de cadena están indexados, el primer elemento tiene índice [0], el segundo elemento tiene índice [1], etc. 
- Para saber la cantidad de elementos que tiene una cadena se hace uso de la función len() tam=len(”cadena”) 
- Para acceder a un elemento determinado de la cadena se hace a través de su posición 
``` python
cad=”hoy es un día muy especial” 
uno=cad[8] 
rango=cad[0:4] 
algunos=cad[0:len(cad):2] 
ultimo=cad[-1]
#Permite obtener el reverso de la cadena 
cad[::-1]
```
### algunos métodos:
``` python
cad.upper() #regresa en mayúsculas la cadena 
cad.lower() #regresa en minúsculas la cadena 
cad.capitalize() # cambia la primera letra a mayúsculas 
cad.split(”subcadena”) #separa la cadena cada vez que encuentra el separador especificado y se guardan en una lista, por deficinicion es el espacio 
cad.split(”subcadena”, cantidad) #igual que el anterior, pero en este caso se le especifica la cantidad de veces que debe realizarse la operación, con -1 hace todas las separaciones, actúa como la primera versión 
cad.splitlines() #separa la cadena cada vez que encuentra un salto de línea 
cad.count("subcadena") #regresa las veces que se encuentra una subcadena 
cad.startswith("subcadena") #regresa True si la subcadena es igual a la parte inicial de la cadena 
cad.endswith("subcadena") #regresa True si la subcadena es igual a la parte final de la cadena 
cad.find("subcadena") # regresa la posición donde se encontró por primera vez la subcadena, -1 en caso contrario 
cad.index("subcadena") #regresa el valor del índice donde se encuentra la subcadena, error en caso contrario 
cad.rfind("subcadena") #igual que find(), solo que ahora busca de derecha a izquierda 
cad.rindex("subcadena") #igual que index(), solo que ahora busca de derecha a izquierda 
cad.isnumeric() #regresa True si la cadena es numérica 
cad.isdecimal() #regresa True si la cadena son números decimales 
cad.isdigit() #regresa True si la cadena son dígitos
cad.isalnum() #regresa True si la cadena es alfanumérica 
cad.isalpha() #regresa True si la cadena es conformada por caracteres alfabéticos 
cad.islower() #regresa True si la cadena es en minúsculas 
cad.isupper() #regresa True si la cadena es en mayúsculas 
cad.isprintable() #regresa True si la cadena está formada por caracteres imprimibles 
cad.isspace() #regresa True si la cadena son espacios solamente 
cad.encode("ascii") #regresa una cadena en bytes codificada al mapa de caracteres especificados, por definición es utf-8 b"asd"
cad.decode("ascii")#regresa una representación en bytes de la cadena a una cadena de acuerdo al mapa de caracteres especificado 
cad.center(cantidad de caracteres)#centra la cadena de acuerdo a la cantidad de caracteres indicados como base 
cad.center(cantidad de caracteres,”relleno”)#centra la cadena de acuerdo a la cantidad de caracteres indicados como base ”hola”.center(20,”*”), esto mismo aplica para los dos siguientes métodos. 
cad.ljust(cantidad de caracteres)#justifica a la izquierda la cadena de acuerdo a la cantidad de caracteres indicados como base 
cad.rjust(cantidad de caracteres)#justifica a la derecha la cadena de acuerdo a la cantidad de caracteres indicados como base 
cad.swapcase() #regresa una cadena, invierte los caracteres de mayúsculas a minúsculas y viceversa 
cad.replace(“subcadena", “nueva subcadena")#reemplaza una subcadena por otra subcadena 
cad.strip() # elimina los espacios de los extremos de la cadena 
cad.lstrip() # elimina los espacios del extremo izquierdo de la cadena 
cad.rstrip() # elimina los espacios del extremo derecho de la cadena

cad.partition(”separador”)# retorna una tupla de tres elementos: el bloque de caracteres anterior a la primera ocurrencia del separador, el separador mismo, y el bloque posterior 
cad.rpartition((”separador”) #similar al anterior, pero realizando la búsqueda de derecha a izquierda. 
"separador".join([lista de cadenas]) # debe ser llamado desde una cadena que actúa como separador para unir dentro de una misma cadena resultante los elementos de una lista 
cad.zfill(cantidad de caracteres) # completa el tamaño de la cadena con caracteres cero a la izquierda 

#Algunas funciones: 
len(cad) #regresa la cantidad de caracteres de la cadena
```

# Tuplas 
Los elementos están delimitados por un par de paréntesis y siguen un orden ``
``` python
tupla=(12,43,54,10)
```

- Una tupla es inmutables (no se pueden modificar) 
- Una tupla permite tener valores duplicados y de cualquier tipo 
	tupla=(1,4,2,5,2)
- Los elementos de tupla están indexados, el primer elemento tiene índice [0], el segundo elemento tiene índice [1], etc. 
- Para saber la cantidad de elementos que tiene una tupla se hace uso de la función len()
	tam=len(tupla)


Para acceder a un elemento determinado de la tupla se hace a través de su posición 
```Python
uno=tupla[0] 
rango=tupla[0:4] 
algunos=tupla[0:len(tupla):2
```
Algunas funciones:
``` python
tupla.count(elem)# regresa el numero de veces que se repite un elemento 
tupla.index(elem)# regresa la posición donde se encuentra el elemento, si no lo encuentra, regresa un error 
tupla.index(elem. posiciónIncial)# igual que el anterior, pero empieza a buscar a partir de la posición que se indica
```

Cuando creamos una tupla, el tipo de dato que dará el contenido de la tupla debe ser un valor iterable
``` python
#Tupla vacía: 
tupla=() 
#Tupla con un elemento: 
tupla=(2,) 
#Tupla varios elementos: 
tupla=12,54,75,"54“ 
a=199 
b="queso" 
d=(2,3) 
c={1,2,3} 
tupla=a,b,c,d #empaquetar 

#Convertir un tipo de dato a tupla, ejemplos: 
tuple("123") 
tuple([1,2,3]) 
tuple((1,2,3)) 
tuple({1,2,3}) 
tuple({"b":7,"c":8})

#Podemos obtener los datos de una tupla (desempaquetar): 
aa,cc,vv,bb=tupla 
(aa,cc,vv,bb)=tupla 
a,_,c,_=tupla
```

Para modificar los datos de una tupla, por lo general se hace una conversión a una lista, se agrega el elemento o se modifica dentro de la lista, y al final la lista se convierte de nuevo a tupla. 

Si lo que se quiere es agregar un nuevo elemento a la tupla, se puede hacer una suma de tuplas y guardar el resultado en la tupla base.


# Listas
Las listas son un tipo de dato que permite almacenar datos de cualquier tipo 
- Son mutables y dinámicas 
- Los elementos de una lista son delimitados por corchetes cuadrados y separados por comas 
- Para acceder a los valores de una lista lo hacemos igual que las cadenas y las listas
``` python
lista=[1,2,3,4,5,6,7] 
lista[1] 
lista[1:3]

```
Para crear una lista se requiere que los datos sean iterables al igual que las tuplas:
```python
#Lista vacía: 
lista=[] 
#Lista con un elemento: 
lista=[2] 
#Lista varios elementos: 
lista=[12,54,75,"54"]
a=199 
b="queso" 
d=(2,3) 
c={1,2,3} 
lista=[a,b,c,d] #empaquetar
```
Convertir un tipo de dato a listas, ejemplos:
``` python
list("123") 
list([1,2,3]) 
list((1,2,3)) 
list({1,2,3}) 
list({"b":7,"c":8}) 
#Se pueden anidar: 
lista=[[1,2,3],[4,5,6]] 
#Se pueden sumar: 
a=[1,2,3] 
b=[4,5,6] 
c=a+b
```

#### Algunos métodos
``` python
lista.append(valor) #agregar un elemento a la lista 
lista.insert(posición, valor)#agregar un elemento en una posición 
lista.extend(elementoIterable) #extender una lista 
lista.remove(valor)#borrar elemento 
lista.pop()#sacar el ultimo elemento de la lista 
lista.pop(posición) #sacar el elemento de la posición de la lista 
lista.reverse() #invierte el orden de los elementos de la lista 
lista.index(elemento) #regresa la posición o índice del elemento indicado
```

#### Algunas funciones: 
```python
len(lista)#regreda el tamaño de la lista 
lista.sort() #ordena los datos de la lista 
lista.sort(reverse=True) #ordena en sentido invertido la lista 
lista.count(valor)#indica la cantidad de veces que se repite un valor 
del(lista[posicion]) #borra un elemento de la lista
```

##### Ejemplos de iteración:
``` python
lista = [5, 9, 10] 
for l in lista: 
	print(l) 

lista = [5, 9, 10] 
for i in range(len(lista)): 
	print(lista
	
lista = [5, 9, 10] 
for index, l in enumerate(lista): 
	print(index, l) 

lista1 = [5, 9, 10] 
lista2 = ["Jazz", "Rock", "Blues"] 
for l1, l2 in zip(lista1, lista2): 
	print(l1, l2)
```


#### Listas como arreglos
``` python
#una dimension 
ar=[1,2,3,4,5,6,7] 
for e in ar: 
	print(e) 
#otra forma 
for i in range(len(ar)): 
	print(ar[i])

#dos dimensiones 
ar2=[[1,2,3], #renglon 1 
	[4,5,6], #renglon 2 
	[7,8,9]] #renglon 3 
	
for i in ar2: 
	for j in i: 
		print(j,end=' ') 
	print() 
#otra forma 
for i in range(len(ar2)): 
	for j in range(len(ar2[i])): 
		print(ar2[i][j],end=' ') 
	print()


#tres dimensiones 
ar3=[[[1,2,3],[4,5,6],[7,8,9]], 
	[[10,11,12],[13,14,15],[16,17,18]]] 

for i in ar3: 
	for j in i: 
		for k in j: 
			print(k,end=' ') 
	print() 

#otra forma 
for i in range(len(ar3)): 
	for j in range(len(ar3[i])): 
		for k in range(len(ar3[i][j])): p
			rint(ar3[i][j][k],end=' ') 
	print()
```

### Lista de comprensión
``` python
lista=[] 
for x in range(1,11): 
	lista.append(x**3) 
print(lista) 

lista=[x**3 
for x in range(1,11)] 
	print(lista)
	
	
lista=[] 
for numero in range(0,11): 
if numero%2==0: 
lista.append(numero) 
print(lista) 

lista = [numero for numero in range(0,11) if numero % 2 == 0 ] 
print(lista)
```
##### Ejemplo de como pudiéramos diseñar una pila
``` python
#Agregar datos 
pila = [3,4,5] 
pila.append(6) 
pila.append(7) 
print(pila) 

#Sacar datos: 
opción 1: 
print(pila.pop()) 
print(pila) 

#opción 2: 
numero = pila.pop() 
print(numero)
```

##### Ejemplo de como crear una cola o fila
```  python
from collections import deque 

cola = deque() #se crea una cola o fila vacia 
print(cola)

#se agregan elementos a la cola inicialmente 
cola = deque(['Hector','Juan','Miguel']) 
print(cola) 

#agregar un elemento 
cola.append('Maria') 
cola.append('Arnaldo') 
print(cola) 

#sacar un elemento de la pila 
#opcion 1 
print(cola.popleft()) print(cola) 
#opcion 2 
elem=cola.popleft() print(elem)
```

---
# Conjuntos
son un tipo que permite almacenar varios elementos y acceder a ellos de una forma muy similar a las listas pero con ciertas diferencias

- Los elementos de un conjunto no pueden existir de manera duplicada 
- Los conjuntos son desordenados, lo que significa que no mantienen el orden de cuando son declarados. 
- Sus elementos deben ser inmutables

``` python
#Crear un conjunto: 
conjunto={1,3,6,2,7} 
conjunto=set{[2,1,4,5,6]} 
conjunto=set{”abcd”} 
conjunto=set((1,”a”,5,8)) 
conjunto=set({"a":7,"q":8}) 

#Union de dos conjuntos: 
a={1,2,3} 
b={2,3,4,6}
c=a|b #c=a.union(b) 
print(c)
```

### Métodos
``` python
conjunto.add(elemento) # agregar un elemento 
conjunto.remove(elemento)#borrar elemento, si no existe marca error 
conjunto.discard(elemento)#borrar elemento, si no existe no marca error 
conjunto.pop() #saca el primer elemento del conjunto 
conjunto.clear()#elimina todos los elementos del conjunto 
conjunto=a.union(b)#unión de dos conjuntos 
conjunto=a.intersection(b)#intersección de dos conjuntos 
conjunto=a.difference(b)#regresa el subconjunto de los valores distintos de a con respecto a b 
conjunto= a.symmetric_difference(b)#regresa el subconjunto de los valores distintos de a y b 

a.issubset(b)#regresa True si a es un subconjunto de b 
a.issuperset(b) )#regresa True si a es un superconjunto de b 
a.isdisjoint(b) )#regresa True si a y b son conjuntos disjuntos

# Algunas funciones: 
len(conjunto) #tamaño del conjunto
```


---
# Diccionarios
Los diccionarios en Python son una estructura de datos que permite almacenar su contenido en forma de llave y valor.
Es una colección de elementos, donde cada uno tiene una llave key y un valor value. 

Algunas propiedades: 
- Son dinámicos, pueden crecer o decrecer, se pueden añadir o eliminar elementos. 
- Son indexados, los elementos del diccionario son accesibles a través de la clave (key) 
- Son anidados, un diccionario puede contener a otro diccionario en su campo valor (value)

``` python
# Crear un diccionario: 
d={key:valor, key:valor,..} 
d= {"Nomb": "Juan", "Edad": 20, "NC": 22290132, "sem":1} 

d = dict([('Nomb', ‘Juan’), ('Edad’, 20), (‘NC', 22290132),("sem",1)]) 
d = dict(nomb='juan', 
	edad=20, 
	nc=22290132, 
	sem=1)
```

``` python
#Acceder a un elemento: 
valor=d[key] 
v=d["Nomb"] 

#Modificar un valor: 
d[key]=nuevoValor
```

### Métodos

```python
Algunos métodos: d.get(key)#obtiene el valor 
d.get(key, 'No encontrado') #obtiene el valor, en caso de no encontrarse envia un mensaje 
d.clear()#limpia un diccionario 
d.items()#obtiene los elementos del diccionario 
d.keys()#obtiene una lista con las claves del diccionario 
d.values() #obtiene una lista con los valores del diccionario 
d.pop(key)#saca un elemento del diccionario, si no existe da error 
d.pop(key, -1) )#saca un elemento del diccionario, si no existe regresa el valor indicado, no da error 
d.popitem()#saca de manera aleatoria un item d1 = {'a': 1, 'b': 2} d2 = {'a': 0, 'd': 400} 
d1.update(d2)#actualiza los datos de un diccionario
```

#### Iterar un diccionario
```python
Iterar un diccionario: 
for x in d: 
	print(x)#solo imprime las claves 
	
for x in d: 
	print(d[x])#imprime el valor 
	
for x in d.values(): 
	print(x)#imprime los valores 
	
for k, v in d.items(): 
	print(k, v)#imprime ambos elementos
```

---
# Funciones
``` Python
def nombre_funcion(): 
	código 

def nombre_funcion(parametros): 
	código 

def nombre_funcion(parametros): 
	código 
	return valor_retorno 

def nombre_funcion(parametro=valor): 
	código

def nombre_funcion(*parametro): 
	código 

def nombre_funcion(**parametro): 
	código
```

Invocación 
``` python
nombre_funcion() 

x=nombre_funcion() #en caso de retornar valor 

nombre_funcion(argumentos) 

nombre_función(argumento=valor) 

nombre_función(conjunto de valores) 

Nombre_funcion(conjunto variables con asigancion de valor)
```

### Función lambda
lambda `parametros:operacion` 
``` python
#Función normal: 
def doble(num): 
	resultado = num*2 
	return resultado	
print(doble(2)) 
 
#Función lambda: 
resultado = lambda num:num*2 
print(resultado(2)) 

impar = lambda num: num%2 != 0 
print(impar(5))
```
