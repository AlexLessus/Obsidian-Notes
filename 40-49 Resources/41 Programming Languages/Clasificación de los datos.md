Tags: [[Aprendizaje Automático]] 

## **Por el tipo de información**
Representan valores escalares o magnitudes.
### **Numérico**
- **Enteros:** Números sin parte decimal, positivos o negativos.    
    - **byte:** Ocupa 8 bits. Rango típico de $-128$ a $127$.        
    - **short:** Entero de 16 bits. Útil para ahorrar memoria en arreglos grandes.        
    - **integer:** El estándar de 32 bits para operaciones matemáticas generales.        
- **Flotantes:** Números con notación de punto decimal (mantisa y exponente).    
    - **float:** Precisión simple (32 bits). Ideal para gráficos o cuando la precisión no es crítica.  
    - **double:** Precisión doble (64 bits). El estándar para cálculos científicos.        
- **Complejos:** Datos que constan de una parte real y una imaginaria ($a + bi$).    

### **Texto**
Representación de glifos y lenguaje humano.
- **Caracteres:** Un solo símbolo (letra, dígito o signo) codificado usualmente en ASCII o Unicode.    
    - **numérico:** El dígito como símbolo (ej. `'5'`), no como valor matemático.        
    - **simbólico:** Signos de puntuación o caracteres especiales (ej. `$`, `@`).        
- **Cadenas:** (Strings) Una secuencia finita de caracteres. Es un objeto o puntero en muchos lenguajes.    

### **Booleano**
Representa lógica binaria: **True** (verdadero) o **False** (falso). Es la base del flujo de control en programación.

---
## **Por su estructura**
### **Estructurados**
Siguen un esquema rígido y predefinido, facilitando su búsqueda y análisis (ej. Bases de datos SQL).
- **Objetos:** Instancias que encapsulan estados (atributos) y comportamientos (métodos).    
- **Arreglos:** Colección de elementos del mismo tipo almacenados en posiciones contiguas de memoria.    
- **Tablas:** Organización bidimensional de datos.    
    - **Registros:** Una fila completa que representa una entidad única.        
    - **Campos:** Columnas que definen un atributo específico del registro.        
    - **Sub campos:** Divisiones internas de un campo (ej. "Fecha" dividido en día, mes, año).
- **Listas:** Conjunto de elementos enlazados; pueden ser simples, dobles o circulares.
- **Pilas:** Estructura LIFO (_Last In, First Out_). Como una pila de platos.
- **Colas:** Estructura FIFO (_First In, First Out_). Como una fila en el banco.
- **Arboles:** Estructura jerárquica no lineal con un nodo raíz y nodos hijos.
- **Grafos:** Conjunto de nodos (vértices) conectados por aristas, ideal para representar redes.

### **No Estructurados**
Datos que no tienen un formato interno identificable. Son masivos y difíciles de procesar sin herramientas de IA o Big Data (ej. PDFs, imágenes, audios, videos).
### **Semiestructurados**
No tienen una estructura de tabla rígida, pero contienen etiquetas o marcadores para separar elementos (ej. JSON, XML, HTML).

---
## **Por su origen**
### **Primarios**
Datos recolectados de primera mano por el investigador o sistema para un propósito específico (ej. lecturas de un sensor en tiempo real).

### **Secundarios**
Datos que ya existen y fueron recolectados por terceros para otros fines, pero que se reutilizan (ej. censos de población, bases de datos históricas).

---
## **Por su acceso**
### **Abiertos**
Datos que pueden ser utilizados, reutilizados y redistribuidos libremente por cualquier persona (ej. Open Data gubernamental).
### **Cerrados**
Datos protegidos por restricciones de seguridad, privacidad o propiedad intelectual. Solo usuarios autorizados pueden verlos (ej. historial clínico, datos bancarios).

---
## **Por su presentación o análisis**

### **Cuantitativos**
Datos que se pueden medir y expresar con números.
- **Discretos - Enteros:** Valores contables finitos.
    - **Número de control:** Identificador único (no existen medios números de control).
- **Continuos - Flotante:** Valores que pueden tomar cualquier número dentro de un intervalo.
    - **Altura:** Puede ser $1.75$ m, $1.752$ m, etc.

### **Cualitativos**
Describen cualidades o categorías.
- **Categóricos o Nominales:** Etiquetas sin un orden intrínseco (ej. Color de ojos, nacionalidad).
- **Ordinales:** Categorías que siguen una jerarquía o escala lógica (ej. Nivel de estudios: Licenciatura, Maestría, Doctorado).