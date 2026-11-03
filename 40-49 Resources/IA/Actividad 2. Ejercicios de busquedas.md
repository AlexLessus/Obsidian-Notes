**1. Conversión del Laberinto a Grafo**
Considerando los movimientos permitidos (arriba, abajo, izquierda, derecha) y las barreras representadas por líneas rojas (entre C-D, D-E, W-R, T-F), las adyacencias de cada nodo (costo = 1) quedan definidas así:
![[Pasted image 20261101182137.png]]
* **A:** B, C
* **B:** A, D
* **C:** A, K
* **D:** B, M
* **E:** N
* **G:** I, P
* **I:** G, Q, W
* **W:** I, K
* **K:** C, M, T, W
* **M:** D, F, K, N
* **N:** E, M
* **P:** G, Q
* **Q:** I, P, R
* **R:** Q, T
* **T:** K, R
* **F:** M

**2. Heurística (Distancia de Manhattan)**
Asignando coordenadas $(x, y)$ en la cuadrícula al estilo plano cartesiano, donde **F** está en $(5,4)$, la fórmula es $h(n) = \vert{}x - 5\vert{} + \vert{}y - 4\vert{}$.

* h(A) = 4
* h(B) = 3
* h(C) = 3
* h(D) = 2
* h(E) = 3
* h(G) = 5
* h(I) = 4
* h(W) = 3
* h(K) = 2
* h(M) = 1
* h(N) = 2
* h(P) = 4
* h(Q) = 3
* h(R) = 2
* h(T) = 1
* h(F) = 0

---

**3. Corridas de Escritorio**
### Primero en Anchura (BFS)

Estructura de datos: **Cola (FIFO)**. Se añaden los hijos al final.

| Estado Inicial | Estado Final | Estado Actual | Lista de estados abiertos (Cola) | Lista de estados cerrados      | Lista de hijos     |
| -------------- | ------------ | ------------- | -------------------------------- | ------------------------------ | ------------------ |
| I              | F            | I             | [G, Q, W]                        | [I]                            | G, Q, W            |
| I              | F            | G             | [Q, W, P]                        | [I, G]                         | P                  |
| I              | F            | Q             | [W, P, R]                        | [I, G, Q]                      | P (ignorado), R    |
| I              | F            | W             | [P, R, K]                        | [I, G, Q, W]                   | K                  |
| I              | F            | P             | [R, K]                           | [I, G, Q, W, P]                | Q (ignorado)       |
| I              | F            | R             | [K, T]                           | [I, G, Q, W, P, R]             | T                  |
| I              | F            | K             | [T, C, M]                        | [I, G, Q, W, P, R, K]          | C, M, T (ignorado) |
| I              | F            | T             | [C, M]                           | [I, G, Q, W, P, R, K, T]       | Ninguno nuevo      |
| I              | F            | C             | [M, A]                           | [I, G, Q, W, P, R, K, T, C]    | A                  |
| I              | F            | M             | [A, D, F, N]                     | [I, G, Q, W, P, R, K, T, C, M] | D, F, N            |
| I              | F            | A             | [D, F, N, B]                     | [..., C, M, A]                 | B                  |
| I              | F            | D             | [F, N, B]                        | [..., M, A, D]                 | B (ignorado)       |
| I              | F            | **F**         | **META**                         | **META**                       | **META**           |

### Primero en Profundidad (DFS)

Estructura de datos: **Pila (LIFO)**. Se añaden los hijos al principio.

| Estado Inicial | Estado Final | Estado Actual | Lista de estados abiertos (Pila) | Lista de estados cerrados | Lista de hijos |
| --- | --- | --- | --- | --- | --- |
| I | F | I | [G, Q, W] | [I] | G, Q, W |
| I | F | G | [P, Q, W] | [I, G] | P |
| I | F | P | [Q, W] | [I, G, P] | Q (ya en abiertos) |
| I | F | Q | [R, W] | [I, G, P, Q] | R |
| I | F | R | [T, W] | [I, G, P, Q, R] | T |
| I | F | T | [K, W] | [I, G, P, Q, R, T] | K |
| I | F | K | [C, M, W] | [I, G, P, Q, R, T, K] | C, M, W (ya en abiertos) |
| I | F | C | [A, M, W] | [..., T, K, C] | A |
| I | F | A | [B, M, W] | [..., K, C, A] | B |
| I | F | B | [D, M, W] | [..., C, A, B] | D |
| I | F | D | [M, W] | [..., A, B, D] | M (ya en abiertos) |
| I | F | M | [F, N, W] | [..., B, D, M] | F, N |
| I | F | **F** | **META** | **META** | **META** |

### Primero el Mejor (Best-First)

Estructura de datos: **Cola de Prioridad** basada exclusivamente en $h(n)$.

| Estado Inicial | Estado Final | Estado Actual | Lista de estados abiertos ordenados por $h(n)$ | Lista de estados cerrados | Lista de hijos |
| --- | --- | --- | --- | --- | --- |
| I | F | I(4) | [Q(3), W(3), G(5)] | [I] | G, Q, W |
| I | F | Q(3) | [R(2), W(3), P(4), G(5)] | [I, Q] | P, R |
| I | F | R(2) | [T(1), W(3), P(4), G(5)] | [I, Q, R] | T |
| I | F | T(1) | [K(2), W(3), P(4), G(5)] | [I, Q, R, T] | K |
| I | F | K(2) | [M(1), W(3), C(3), P(4), G(5)] | [I, Q, R, T, K] | C, M |
| I | F | M(1) | [F(0), D(2), N(2), W(3), C(3), P(4), G(5)] | [I, Q, R, T, K, M] | D, F, N |
| I | F | **F(0)** | **META** | **META** | **META** |

### Algoritmo A*

Estructura de datos: **Cola de Prioridad** basada en $f(n) = g(n) + h(n)$. $g(n)$ es el costo acumulado desde I.

| Estado Inicial | Estado Final | Estado Actual | Lista de estados abiertos ordenados por $f(n)$ | Lista de estados cerrados | Lista de hijos evaluados        |
| -------------- | ------------ | ------------- | ---------------------------------------------- | ------------------------- | ------------------------------- |
| I              | F            | I(f=4)        | [Q(4), W(4), G(6)]                             | [I]                       | G(6), Q(4), W(4)                |
| I              | F            | Q(f=4)        | [R(4), W(4), P(6), G(6)]                       | [I, Q]                    | P(6), R(4)                      |
| I              | F            | R(f=4)        | [T(4), W(4), P(6), G(6)]                       | [I, Q, R]                 | T(4)                            |
| I              | F            | T(f=4)        | [W(4), K(6), P(6), G(6)]                       | [I, Q, R, T]              | K(6) *(Costo g=4)*              |
| I              | F            | W(f=4)        | [K(4), P(6), G(6)]                             | [I, Q, R, T, W]           | **K(4)** *(Mejora costo a g=2)* |
| I              | F            | K(f=4)        | [M(4), C(6), P(6), G(6)]                       | [I, Q, R, T, W, K]        | C(6), M(4)                      |
| I              | F            | M(f=4)        | [F(4), D(6), N(6), C(6), P(6), G(6)]           | [..., W, K, M]            | D(6), F(4), N(6)                |
| I              | F            | **F(f=4)**    | **META**                                       | **META**                  | **META**                        |