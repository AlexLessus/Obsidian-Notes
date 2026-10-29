 - El conocimiento importa 
 - Siempre buscan la solución óptima
 - La solución a parte de ser la respuesta debe ser la mejor respuesta
 - Siempre debemos de tener alguna medida del costo de obtener una solución. Este coste lo mediremos sobre el camino que nos llevará desde el edo Inicial hasta el final de un problema.
 - Supondremos que se puede plantear nuestra búsqueda como una búsqueda de un camino y que de alguna manera somos capaces de saber o estimar cual es la longitud de este. 
 - Por lo general tendremos un coste asociado a los operadores que nos permiten pasar de un edo a otro, por lo que el coste tendrá un papel fundamental en el cálculo del coste del camino.
 - No son sistemáticos, de manera que el orden de exploración no lo determina la estructura del criterio de búsqueda si no el criterio heurístico
 - Algunas búsquedas no son exhaustivas 
 - No siempre se garantiza encontrar la solución óptima, ni hallar la solución optima

### Algunos algoritmos
- Algoritmo voraz o primero el mejor avaricioso o greedy best first )
- Dijkstra
- Meramente Heurístico:
	-  A*
	- IDA*
	-  Primero el mejor recursivo (Recursive Best First)
	- A* con memoria limitada
- Búsqueda local
 - Branch & bound
 - Hill Climbing
 - Búsqueda tabú

### Algoritmo_busqueda_primero_el_mejor

inicio
edosAbiertos.insertar(edoInicial)
actual= edosAbiertos.primero( )
mientras no ( edos abiertos.vacia ( ) ) y no ( esFinal(actual)) hacer
edosAbiertos.borrar(primero)
edosCerrados.insertar(actual)
hijos=generarHijos(Actual)
hijos= tratar Repetidos(hijos,edosAbiertos,edosCerrados)
edosAbiertos.insertar(hijos)
edosAbiertos.actualizar( )
actual=edosAbiertosPrimero( )
FIN
Si esFinal(actual)
si si inicio
	edosAbiertos.borrarPrimero( )
	edosCerrados.insertar( actual )
	edosCerrados.recorrer( )
Fin
Si no imprimir "Solución no encontrada"
FIN
*GenerarHijos( )
 asignar c/ descendiente su coste (actual.valoracumulado+hijo.peso) y valor heuristico(hijo.coste+hijo.heuristico), este
último según sea el caso
*Actualizar ( )
ordenar los edos de manera ascendente
