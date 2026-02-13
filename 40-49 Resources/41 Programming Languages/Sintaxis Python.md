Tags: [[Python]] 

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


### Palabras reservadas
``` 
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


### Listar elementos dentro de un modulo  dir()
``` Pyton
>>> dir(keyword)
['__all__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'iskeyword', 'issoftkeyword', 'kwlist', 'softkwlist']
```


```
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
