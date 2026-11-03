### 1. Ubicación del Estado Inicial y Estado Final (Meta)
- **Estado Inicial:** $$\begin{bmatrix} 1 & 4 & 3 \\ 7 & \text{\textvisiblespace} & 6 \\ 5 & 8 & 2 \end{bmatrix}$$ _(El espacio vacío_ $\text{\textvisiblespace}$ *se encuentra ubicado en el centro de la matriz)*[1].
- **Estado Final / Meta:** $$\begin{bmatrix} 1 & 2 & 3 \\ 8 & \text{\textvisiblespace} & 4 \\ 7 & 6 & 5 \end{bmatrix}$$ *(Las fichas numeradas quedan dispuestas secuencialmente alrededor del espacio vacío central)*[1].


---

### 2. Pasos y Procesos Desarrollados para la Solución

El desplazamiento del rompecabezas se modela moviendo las fichas contiguas hacia la posición vacía o, de manera equivalente, desplazando el espacio libre en las cuatro direcciones permitidas (**Arriba**, **Abajo**, **Izquierda**, **Derecha**). La secuencia de movimientos se desarrolla de la siguiente forma:
- **Estado Inicial:** $$\begin{bmatrix} 1 & 4 & 3 \\ 7 & \text{\textvisiblespace} & 6 \\ 5 & 8 & 2 \end{bmatrix}$$
- **Paso 1 (Mover hueco Abajo / subir la ficha 8):** $$\begin{bmatrix} 1 & 4 & 3 \\ 7 & 8 & 6 \\ 5 & \text{\textvisiblespace} & 2 \end{bmatrix}$$
- **Paso 2 (Mover hueco a la Derecha / deslizar la ficha 2 a la izquierda):** $$\begin{bmatrix} 1 & 4 & 3 \\ 7 & 8 & 6 \\ 5 & 2 & \text{\textvisiblespace} \end{bmatrix}$$
- **Paso 3 (Mover hueco Arriba / bajar la ficha 6):** $$\begin{bmatrix} 1 & 4 & 3 \\ 7 & 8 & \text{\textvisiblespace} \\ 5 & 2 & 6 \end{bmatrix}$$
- **Paso 4 (Mover hueco Arriba / bajar la ficha 3):** $$\begin{bmatrix} 1 & 4 & \text{\textvisiblespace} \\ 7 & 8 & 3 \\ 5 & 2 & 6 \end{bmatrix}$$
- **Paso 5 (Mover hueco a la Izquierda / deslizar la ficha 4 a la derecha):** $$\begin{bmatrix} 1 & \text{\textvisiblespace} & 4 \\ 7 & 8 & 3 \\ 5 & 2 & 6 \end{bmatrix}$$

---

### 3. Condiciones y Restricciones Generadas durante el Proceso

Durante la búsqueda de la solución dentro del espacio de estados, se deben respetar las siguientes condiciones lógicas e implícitas:

1. **Restricción de Vecindad Física (Movilidad):** Solo pueden deslizarse aquellas fichas que compartan una posición adyacente (horizontal o vertical) con el espacio vacío; están prohibidos los movimientos diagonales o saltos entre piezas.
2. **Límites del Tablero:** El espacio vacío y las fichas no pueden rebasar los márgenes de la matriz de \(3 \times 3\).
3. **Conservación de Elementos:** Se debe mantener en todo momento exactamente un espacio libre y 8 fichas numeradas sin duplicados.
4. **Restricción de No Ciclado:** Se evita revertir inmediatamente el movimiento realizado en el paso previo para no generar bucles infinitos en el proceso de búsqueda.

---

🧩 __¿Te gustaría que analicemos este problema aplicando algoritmos de búsqueda informada (como \(A^_\) con la heurística de distancia Manhattan) para evaluar el costo de los caminos en el árbol de búsqueda?_*