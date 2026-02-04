

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