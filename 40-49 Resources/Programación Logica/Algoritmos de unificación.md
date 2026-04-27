Alexis De Jesus Perez Carmona
#ProgramaciónLogica
[[Programación Logica]]
### El Algoritmo de Robinson (1965)
Es el algoritmo clásico y pionero, propuesto por John Alan Robinson junto con el principio de resolución.

- **Cómo funciona:** Compara dos términos de izquierda a derecha. Cuando encuentra la primera diferencia (el "conjunto de desacuerdo"), intenta unificarlos asignando un valor a una variable. Si tiene éxito, aplica esa sustitución al resto de la expresión y repite el proceso hasta que no haya diferencias.    
- **Ventaja:** Es conceptualmente muy sencillo y la base de todos los demás.    
- **Desventaja:** En el peor de los casos, su complejidad de tiempo es exponencial. Es ineficiente para términos muy anidados.

### El Algoritmo de Martelli-Montanari (1982)
Es probablemente el algoritmo más estudiado hoy en día porque reformula la unificación como si fuera un **sistema de ecuaciones**.

- **Cómo funciona:** Toma los dos términos que se quieren unificar y crea una ecuación (Termino1 = Termino2). Luego, aplica repetidamente un conjunto de reglas de transformación hasta llegar a una solución (la sustitución) o a un fallo. Las reglas principales son:    
    - **Descomposición:** Si tienes `f(x) = f(a)`, lo simplifica a `x = a`.        
    - **Eliminación:** Si tienes `x = x`, simplemente lo borra porque no aporta información.      
    - **Asignación (Bind):** Si tienes `x = a`, asigna `a` a todas las demás instancias de `x`.       
    - **Choque (Conflict):** Si intentas igualar `f(x) = g(y)`, falla inmediatamente porque los functores son distintos.        
- **Ventaja:** Es muy eficiente, fácil de implementar y detiene los fallos rápidamente. Su complejidad es casi lineal.
### Algoritmos de Tiempo Lineal (Paterson-Wegman, 1978)
Para solucionar los problemas de lentitud de Robinson en casos extremos, se desarrollaron algoritmos de tiempo lineal.

- **Cómo funciona:** En lugar de tratar los términos como simples cadenas de texto o árboles básicos, utilizan estructuras de datos avanzadas como los **DAGs** (Grafos Acíclicos Dirigidos). Esto permite que, si una variable aparece varias veces, el algoritmo apunte al mismo nodo en la memoria en lugar de copiar el término completo, evitando redundancias.    
- **Ventaja:** Son matemáticamente los más rápidos (tiempo lineal $O(n)$).    
- **Desventaja:** La sobrecarga de gestionar los grafos en memoria los hace menos prácticos para casos sencillos, por lo que rara vez se usan en su forma pura en compiladores estándar.
--- 
Matemáticamente, un buen algoritmo de unificación debe incluir una regla llamada **"Occurs check"** (Prueba de ocurrencia). Esta regla verifica que no intentes unificar una variable con un término que ya contiene esa misma variable (por ejemplo, intentar unificar `X` con `padre(X)`). Si lo haces, crearías un bucle infinito (un árbol de tamaño infinito).

**Sin embargo, la mayoría de los compiladores de Prolog desactivan el "Occurs check" por defecto.** ¿Por qué? Porque hacer esa verificación en cada paso consume demasiado tiempo y memoria. Prolog sacrifica la pureza lógica en favor de la velocidad, asumiendo que el programador escribirá código que no genere esos bucles infinitos.