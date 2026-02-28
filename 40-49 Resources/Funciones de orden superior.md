tags: [[Programación]] [[Programación Logica]]

*Una **función de orden superior** es aquella que toma otras funciones como parámetros o devuelve una función como resultado.*
### 1. Composición y Manipulación de Funciones
Estas funciones sirven para crear o modificar el comportamiento de otras funciones.
- **(.) Composición:** Une dos funciones. El resultado de la segunda función se pasa como parámetro a la primera. Es el equivalente matemático a $f(g(x))$.
    - `Ejemplo:` `(negate . abs) 5` -> El valor absoluto de 5 es 5, luego se niega. Resultado: `-5`.
- **flip:** Toma una función que acepta dos argumentos y devuelve la misma función pero con el orden de los argumentos invertidos.
    - `Ejemplo:` `flip (-) 10 2` -> En lugar de hacer 10 - 2, hace 2 - 10. Resultado: `-8`.
- **const:** Toma dos argumentos y siempre devuelve el primero, ignorando completamente el segundo.    
    - `Ejemplo:` `const 42 "hola"` -> Resultado: `42`.        
- **curry:** Convierte una función que espera un par (una tupla `(x, y)`) en una función que acepta dos argumentos separados `x y` (currificación).    
    - `Ejemplo:` `curry fst 1 2` -> La función `fst` saca el primer elemento de una tupla. `curry` le permite aceptar los números por separado. Resultado: `1`.        
- **uncurry:** El proceso inverso. Convierte una función de dos argumentos separados en una que espera una tupla.    
    - `Ejemplo:` `uncurry (+) (3, 4)` -> Pasa la tupla a la suma. Resultado: `7`.        
- **on:** (De la librería `Data.Function`). Toma una funció n binaria, una función unaria y dos valores. Aplica la función unaria a ambos valores y luego aplica la binaria a los resultados.   
    - `Ejemplo:` `((+) on length) "hola" "luz"` -> Calcula las longitudes (4 y 3) y luego las suma. Resultado: `7`.       
### 2. Transformación de Estructuras
- **map:** Aplica una función a cada uno de los elementos de una lista.
        - `Ejemplo:` `map (*2) [1, 2, 3]` -> Resultado: `[2, 4, 6]`.        
- **fmap:** Es una versión generalizada de `map`. Funciona no solo en listas, sino en cualquier estructura que sea un "Functor" (como el tipo `Maybe` o árboles).    
    - `Ejemplo:` `fmap (*2) (Just 5)` -> Resultado: `Just 10`.        
- **zipWith:** Toma una función y dos listas, y las combina aplicando la función elemento por elemento.    
    - `Ejemplo:` `zipWith (+) [1, 2, 3] [10, 20, 30]` -> Resultado: `[11, 22, 33]`.        
### 3. Filtrado y Extracción
- **filter:** Devuelve una lista solo con los elementos que cumplen una condición (predicado).
       - `Ejemplo:` `filter even [1, 2, 3, 4]` -> Filtra los pares. Resultado: `[2, 4]`.        
- **takeWhile:** Toma elementos del inicio de la lista _mientras_ la condición sea verdadera. Se detiene al primer falso.    
    - `Ejemplo:` `takeWhile (<3) [1, 2, 3, 1]` -> Resultado: `[1, 2]`. (Ignora el último 1 porque ya se detuvo en el 3).        
- **dropWhile:** Elimina elementos del inicio de la lista _mientras_ la condición sea verdadera y devuelve el resto.    
    - `Ejemplo:` `dropWhile (<3) [1, 2, 3, 1]` -> Resultado: `[3, 1]`.        
- **span:** Combina `takeWhile` y `dropWhile`. Devuelve una tupla con dos listas: los que cumplen la condición al inicio y el resto.    
    - `Ejemplo:` `span (<3) [1, 2, 3, 1]` -> Resultado: `([1, 2], [3, 1])`.        
- **break:** Es lo opuesto a `span`. Corta la lista en el momento en que la condición se vuelve _verdadera_.    
    - `Ejemplo:` `break (==3) [1, 2, 3, 4]` -> Resultado: `([1, 2], [3, 4])`.        

### 4. Plegado (Reducción) y Escaneo
Reducen una lista a un solo valor o muestran el proceso de reducción.
- **foldl:** Reduce la lista aplicando una función desde la **izquierda** hacia la derecha, usando un valor inicial o acumulador.    
    - `Ejemplo:` `foldl (-) 0 [1, 2, 3]` -> Hace `((0 - 1) - 2) - 3`. Resultado: `-6`.        
- **foldr:** Reduce la lista aplicando la función desde la **derecha** hacia la izquierda.    
    - `Ejemplo:` `foldr (-) 0 [1, 2, 3]` -> Hace `1 - (2 - (3 - 0))`. Resultado: `2`.        
- **scanl:** Hace lo mismo que `foldl`, pero en lugar de devolver solo el resultado final, devuelve una lista con todos los resultados intermedios.    
    - `Ejemplo:` `scanl (+) 0 [1, 2, 3]` -> Resultado: `[0, 1, 3, 6]`.        
- **scanr:** Hace lo mismo que `foldr`, devolviendo los pasos intermedios de derecha a izquierda.    
    - `Ejemplo:` `scanr (+) 0 [1, 2, 3]` -> Resultado: `[6, 5, 3, 0]`.        
### 5. Funciones utilitarias sobre listas
- **sum:** Suma todos los números de una lista.    
    - `Ejemplo:` `sum [1, 2, 3]` -> Resultado: `6`.        
- **product:** Multiplica todos los números de una lista.    
    - `Ejemplo:` `product [2, 3, 4]` -> Resultado: `24`.        
- **and:** Devuelve `True` solo si todos los elementos booleanos de la lista son verdaderos.    
    - `Ejemplo:` `and [True, True, False]` -> Resultado: `False`.        
- **or:** Devuelve `True` si al menos un elemento booleano de la lista es verdadero.    
    - `Ejemplo:` `or [False, True, False]` -> Resultado: `True`.        
- **maximum:** Devuelve el elemento de mayor valor en la lista.    
    - `Ejemplo:` `maximum [4, 9, 2]` -> Resultado: `9`.