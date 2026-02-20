Tags: [[Python]] 

- Para escribir comentarios se utiliza triple apostrofe o comillas si es de bloque y el símbolo de número si es de línea # 
- No se utiliza algún símbolo para indicar fin de la instrucción a diferencia de otros lenguajes como java o c que utilizan punto y coma (;) por mencionar algunos, en Python solo la instrucción se escribe en líneas diferentes y ya 
- Si se quieren poner varias instrucciones en una sola línea, éstas se separan con punto y coma (;) 
- Se utiliza la coma (,) para separar varios datos 
- Utilización de la indentación (4 espacios) para definir bloques de código en lugar de llaves u otro tipo de simbología. 
- No se hace uso de declaración de variables para asignar un tipo de dato en específico
- Para hacer uso de una variable en alguna instrucción dada debe tener asignado previamente su valor 
- Se utilizan dos puntos (:) para dar inicio de un bloque de instrucciones, después de los dos puntos ira de manera indentada el código perteneciente a ese bloque, el cual puede estar contenido en un ciclo, en una decisión, dentro de una función de un método, de una clase, entre otros tipos de sentencias
- Los identificadores pueden empezar con una letra o con guion bajo seguido de una letra, las letras pueden mayúsculas y minúsculas, y enseguida pueden ir dígitos. 
- Por convención los identificadores de clases inician con mayúsculas y el resto del identificador con minúsculas
- Los identificadores de las funciones y métodos inician con minúsculas. 
- Cuando un identificador dentro de una clase comienza con guion bajo se interpreta que es privado, y si comienza con dos guiones bajos es fuertemente privado, y si finaliza con dos guiones se interpreta que es un identificador especial definido en el lenguaje.
- Palabras reservadas van en minúsculas 
- Para conocer las palabras base del lenguaje en la consola interactiva escribimos help('keywords’) y nos da a conocer las palabras reservadas para la versión de Python que estamos trabajando, para la versión 3.12 son las siguientes
### Palabras reservadas
``` python
>>> help("keywords")

Here is a list of the Python keywords.  Enter any keyword to get more help.

False               class               from                or
None                continue            global              pass
True                def                 if                  raise
and                 del                 import              return
as                  elif                in                  try
assert              else                is                  while
async               except              lambda              with
await               finally             nonlocal            yield
break               for                 not
```


- Otra forma de conocer las palabras reservadas es importando el módulo keyword y después que se imprima la lista: 
	import keyword 
	print(keyword.kwlist) 
- Por lo general, el máximo de caracteres por línea es de 79 caracteres 
- Cuando la longitud de una línea sea mayor a la cantidad máxima permitida, o el formato de una línea de código sea muy extensa, se puede poner una diagonal invertida \ al final de la línea y contarla para seguir escribiéndola en una línea posterior. 
- La importación de módulos se hará siempre al inicio del programa, siguiendo el orden: - Módulos de la librería estándar - Módulos de terceros (otras librerías) - Módulos propios


## Variables
Se puede nombrar a las variables como se quiera, pero es importante saber que las mayúsculas y minúsculas son importantes. Las variables x y X son distintas. Lo mismo aplica para cualquier identificador. 

Por otro lado existen ciertas normas a la hora de nombrar variables: 
- El nombre no puede empezar por un número 
- No se permite el uso de guiones 
- Tampoco se permite el uso de espacios 
- Para el caso de las variables hay una variable especial que en algunos lenguajes de programación se conocen como variable anónima la cual se denota con el guión bajo _.
``` Python
# Definimos una variable x con una cadena 
x = "El valor de (a+b)*c es" 
# Podemos realizar múltiples asignaciones 
a, b, c = 4, 3, 2 
# Realizamos unas operaciones con 
a,b,c d = (a + b) * c 
# Definimos una variable booleana 
imprimir = True 
# Si imprimir, print() 
if imprimir: print(x, d) 

# Salida: 
El valor de (a+b)*c es 14
```

## Caracteres de escape 
/n – nueva línea 
/r – enter (retorno de carro) 
/’ – apostrofe o comilla simple 
/” - comillas 
// - barra invertida 
/t – tabulador horizontal 
/v – tabulador vertical 
/b - retroceso 
/f – salto de página 
/a - campana

### Listar elementos dentro de un modulo  dir()
``` Python
>>> dir(keyword)
['__all__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'iskeyword', 'issoftkeyword', 'kwlist', 'softkwlist']
```


## Entrada/salida de datos 
**Entrada de datos** 
variable = input('mensaje’) 

En ocasiones será necesario apoyarnos de funciones para convertir al dato deseado, sobre todo si el dato que se espera es numérico. Se puede trabajar de manera anidada. 

numero = int(input(”dame un numero”)) 

**Salida de datos** 
print (valor) print (”el valor de numero es: ”, numero) 

si son varios valores a imprimir, se separan con comas 

**Algunos formatos** 
print(f”mensaje {variable}, mensaje {variable}”) print(”mensaje {} mensaje {}”.format(var1,var2))

#### Formatos con print
``` Python
  

a = int(input("Dame el valor de a: "))

b = int(input("Dame el valor de b: "))

c = a + b

  

print(a, '+', b, '=', c, sep=" ")

print(f'{a} + {b} = {c}')

print('{1}+{0}={2}'.format(a,b,c))
```

``` python
a = 'queso'

b = 'jitomate'

# separa 10 espacios para a

print(f'{a:10} ---> {len(a):5d} ')

print(f'{b:10} ---> {len(b):5d} ')

  

# end reemplaza el final de la linea

print("a".rjust(10), end = "") # Justificación a la derecha

print("a".ljust(10)) # Justificación a la izquierda

print("a".center(10)) # Justificación centrada
```

--- 

``` python
>>> help(math.acos)
Help on built-in function acos in module math:

acos(x, /)
    Return the arc cosine (measured in radians) of x.

    The result is between 0 and pi.

#Para utilizar acos sin math.acos
>>> from math import acos
>>> help(acos)
Help on built-in function acos in module math:

acos(x, /)
    Return the arc cosine (measured in radians) of x.

    The result is between 0 and pi.



```

#### Operadores relacionales
``` Python
== igual a 
!= diferente a 
< menor que
> mayor que
<= menor o igual que
>= mayor o igual que 
```

#### Operador de igualdad
``` Python
is
3+4 is 3.5*2   #False

is not
```

#### Operador de membresía
``` Python
in
in not

x = [1,7,9,2,3]
4 in x    # False
7 in x    # True
```

#### Operadores lógicos
``` python
not   # !
and   # &&
or    # ||
```

#### Operadores a nivel de bits
``` python
&  # and
^  # xor
|  # or
-  # not
<< # desplazamiento a la izquierda
>> # desplazamiento a la derecha
```



## User input
``` Python
username = input('Enter your name:') 
age = input(int('Enter your age:'))
```
