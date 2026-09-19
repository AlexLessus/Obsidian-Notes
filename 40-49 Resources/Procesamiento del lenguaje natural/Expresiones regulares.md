

## Definiciones
En su jerarquia de gramaticas, Chomsky caracteriza los lenguajes regulares como aquiellos generados por las gramaticas mas restrictivas. 

## 1. Fundamentos y Evolución de las Expresiones Regulares (Regex)
Una expresion regular es una notación formal que permite describir un conjunto de cadenas mediante patrones construidos con caracteres y operadores.

En el ecosistema de la ingeniería de software moderna, las expresiones regulares (o _regex_) trascienden la mera búsqueda de cadenas de texto para consolidarse como una infraestructura lógica crítica. Actúan como patrones algebraicos que permiten describir la geometría de los datos no estructurados, permitiendo una automatización determinista en el tratamiento de la información que resulta vital para la estabilidad de sistemas distribuidos y flujos de datos masivos.

Desde una perspectiva histórica, el concepto se origina en 1951 con el matemático **Stephen Cole Kleene**, quien formalizó los "lenguajes regulares" dentro de la teoría de autómatas. Sin embargo, la transición hacia la operatividad práctica fue liderada por **Ken Thompson** en los laboratorios Bell. Thompson no solo implementó la notación de Kleene en el editor _ed_, sino que, buscando la máxima eficiencia arquitectónica, diseñó un sistema de compilación _Just-In-Time_ (JIT) para el IBM 7094, convirtiendo las regex directamente en código máquina. Este hito dio origen en 1973 a **grep** (_Global Regular Expression Print_), estableciendo un paradigma de procesamiento que hoy es el núcleo de la manipulación de texto en sistemas Linux y motores de búsqueda modernos.

Esta evolución, que comenzó en la matemática pura y maduró en la necesidad operativa de Unix, ha derivado en una diversificación de dialectos técnicos que exigen una comprensión profunda de su compatibilidad y rendimiento.

## 2. Taxonomía de Dialectos: BRE, ERE y PCRE

La elección del estándar (dialecto) no es un detalle cosmético; es una decisión de diseño que impacta directamente en la portabilidad y la eficiencia del procesamiento. Un arquitecto de sistemas debe considerar que no todos los motores interpretan los metacaracteres de la misma forma, lo que puede generar fallos críticos en entornos de producción.

- **BRE (Basic Regular Expressions):** El estándar POSIX original. Es el dialecto por defecto en herramientas clásicas como `sed` y `grep`. Se caracteriza por su verbosidad, ya que metacaracteres como `+`, `?` o las llaves `{}` se interpretan como literales a menos que se escapen con una barra invertida (`\+`, `\?`, `\{`).
- **ERE (Extended Regular Expressions):** Una evolución que simplifica la sintaxis, permitiendo que los cuantificadores y la agrupación operen sin escapado previo (utilizado en `grep -E`, `awk` y `bash`). Es el dialecto de equilibrio recomendado para la administración de sistemas, aunque presenta limitaciones: por ejemplo, la versión `mawk` (común en Debian) no soporta el cuantificador de llaves `{n,m}`.
- **PCRE (Perl Compatible Regular Expressions):** El estándar _de facto_ en lenguajes modernos (Python, JavaScript, PHP). Aunque no es un estándar POSIX, es el más potente al incluir funcionalidades avanzadas como _lookarounds_, cuantificadores perezosos (_lazy_) y soporte para Unicode.

**Advertencia de Compatibilidad:** Es un error común asumir que clases como `\d` (dígitos) o `\s` (espacios) son universales. Herramientas estándar de Linux como `grep` y `sed` **no** las soportan nativamente bajo ERE o BRE; requieren el uso de rangos POSIX como `[0-9]` o clases con nombre como `[[:space:]]`.

## 3. Intersección Estratégica: Regex en el Procesamiento del Lenguaje Natural (PLN)

En el ámbito de la Lingüística Computacional, las regex representan la primera línea de defensa en la limpieza y preprocesamiento de datos para modelos de lenguaje. Antes de que un modelo de [[aprendizaje profundo]] pueda procesar semántica, el texto debe ser normalizado y tokenizado para eliminar el ruido técnico.

Las regex facilitan dos procesos esenciales en PLN:

1. **Tokenización y Segmentación:** Identificación de límites de palabra (`\b`) y segmentación de oraciones en unidades léxicas procesables.
2. **Normalización Multilingüe:** El uso de clases de caracteres Unicode (como `\p{L}` para cualquier letra en cualquier alfabeto) es superior a los rangos `[a-z]`, que ignoran tildes, eñes y caracteres no latinos.

Para el procesamiento de datos globales, es imperativo el uso del **flag Unicode (**`**u**`**)**. Este flag permite al motor manejar correctamente **pares sustitutos** y caracteres fuera del Plano Multilingüe Básico (como emojis o alfabetos antiguos), evitando que un carácter de 4 bytes sea interpretado erróneamente como dos caracteres distintos, lo que corrompería la integridad de la normalización.

## 4. Guía Maestra de Construcción: Caracteres y Metacaracteres

La construcción de patrones requiere distinguir entre la sintaxis BRE (donde el escape activa el poder del carácter) y ERE/PCRE (donde el escape desactiva el poder para buscar el literal).

|   |   |   |   |
|---|---|---|---|
|Elemento|Descripción Técnica|ERE / PCRE|BRE (Literal vs Operador)|
|**Anclas**|Posicionan el patrón en la línea o palabra.|`^` (inicio), `$` (fin), `\b`|`^`, `$`, `\<`, `\>`|
|**Cuantificadores**|Frecuencia de ocurrencia.|`+`, `?`, `{n,m}`|`\+`, `\?`, `\{n,m\}`|
|**Clases**|Conjuntos de caracteres.|`.` (comodín), `[a-z]`|`.` (comodín), `[a-z]`|
|**Atajos**|Clases predefinidas (PCRE/Pipes).|`\d`, `\w`, `\s`|_No soportados (usar_ `_[0-9]_`_, etc.)_|
|**Lógica**|Flujo y agrupación.|`\|` (OR), `()` (grupo)|`\|`, `\(\)`|

_Nota: La simple memorización es insuficiente sin comprender que el motor consume caracteres de izquierda a derecha, afectando el rendimiento según la complejidad del patrón._

## 5. Mecánicas Avanzadas: Cuantificadores "Greedy" vs. "Lazy" y Lookarounds

El control de la voracidad del motor es fundamental para evitar capturas accidentales y mejorar el rendimiento.

### Voracidad (Greedy vs. Lazy)

Por defecto, los cuantificadores son **Greedy** (codiciosos): intentan capturar la mayor cantidad de texto posible. En un archivo `access.log` con la estructura `usuario:x:1000`, la regex `.*:` capturará `usuario:x:` (el tramo más largo hasta el último dos puntos). Para capturar solo el primer campo, se debe usar el modo **Lazy** (perezoso) en PCRE con `.*?`, o recurrir a clases negadas en ERE: `[^:]*:`.

### Lookarounds (Vistazos Contextuales)

Son mecanismos de validación que no "consumen" caracteres del puntero de búsqueda:

- **Lookahead Positivo (**`**(?=...)**`**):** Valida que lo que sigue coincide con el patrón. Ejemplo: `\d+(?=\s*miles)` capturará "5" en "5 miles", pero no en "5 kilometers".
- **Lookbehind Positivo (**`**(?<=...)**`**):** Valida lo que precede. Ejemplo: `(?<=\$)\d+` capturará "100" solo si tiene el símbolo de moneda delante.

## 6. Casos de Uso Profesionales y Validación de Datos

En producción, las regex deben integrarse en scripts de automatización y validación de integridad.

### Patrones de Validación Estructural

- **Emails:** El estándar profesional sugiere una **estrategia de doble validación**. Una regex para la estructura general y otra para verificar la longitud del TLD (ej. `/^.+@.+\.[a-z]{2,4}$/i`), evitando falsos positivos como `root@localhost`.
- **Identificadores (NIF/NIE/CIF):** Es vital entender que la regex solo valida la **estructura** (ej. `/^[0-9]{8}[A-Z]$/`). La validez real del documento depende de un cálculo matemático posterior sobre el dígito de control, una lógica que la regex no puede (ni debe) ejecutar por sí sola.

### Integración en Bash y Linux

Desde Bash 3.0, podemos usar el operador `=~` para validación directa sin invocar subshells:

```bash
if [[ "$ip" =~ ^[0-9]{1,3}(\.[0-9]{1,3}){3}$ ]]; then
    # El array BASH_REMATCH[0] contiene la coincidencia completa
    echo "IP válida detectada"
fi
```

La tríada de Linux complementa este flujo: `grep` para filtrado, `sed` para transformaciones _in-place_ y `awk` para extracción de campos y cálculos aritméticos.

## 7. Buenas Prácticas y Conclusiones Técnicas

Para garantizar la seguridad y el rendimiento de los patrones en entornos profesionales, siga este protocolo:

1. **Seguridad en el Shell:** Use siempre comillas simples (`'`) para evitar que el shell expanda caracteres antes de que lleguen a la herramienta.
2. **Protección de Literales:** Al validar extensiones o IPs, escape el punto (`\.`). De lo contrario, `archivo.txt` coincidirá con `archivoXtxt`.
3. **Prevención de Inyecciones:** Use los delimitadores `\Q` y `\E` (en PCRE) para tratar bloques de texto como literales absolutos, protegiendo al motor de caracteres maliciosos.
4. **Validación No Destructiva:** Antes de un `sed -i`, verifique con `grep --color` para visualizar exactamente qué caracteres serán modificados.

Las expresiones regulares, décadas después de Thompson y Kleene, siguen siendo insustituibles. Su capacidad para operar en la base misma de la información —el texto— las convierte en una herramienta obligatoria tanto para la administración forense de sistemas como para la ingeniería de datos en la era de la Inteligencia Artificial. El dominio de las regex no es solo una habilidad de codificación; es una competencia de arquitectura de datos.

## Simbolos en [[python]]
#python 
### **1. Metacaracteres y Comodines Básicos**

|Símbolo|Descripción|Ejemplo en Python|Coincidencia de ejemplo|
|:--|:--|:--|:--|
|`.`|Coincide con **cualquier carácter** excepto un salto de línea (`\n`).|`r"c.sa"`|`"casa"`, `"cosa"`, `"c1sa"`|
|`\`|**Carácter de escape**: quita el significado especial a un metacarácter o activa una secuencia especial.|`r"archivo\.txt"`|`"archivo.txt"` (evalúa el punto literal)|
|`\|`|**Alternación (OR)**: coincide con el patrón a la izquierda o a la derecha.|`r"gato\|

---

### **2. Clases y Secuencias Especiales de Caracteres**

|Símbolo|Descripción|Equivalencia / Significado|Ejemplo coincidente|
|:--|:--|:--|:--|
|`[...]`|**Clase de caracteres**: coincide con un único carácter de los indicados.|`r"[aeiou]"`|Cualquier vocal minúscula|
|`[^...]`|**Clase negada**: coincide con un único carácter que **NO** esté en la lista.|`r"[^0-9]"`|Cualquier carácter no numérico|
|`[a-z]`|**Rango**: coincide con cualquier carácter entre los límites indicados.|`r"[A-Z]"`|Cualquier letra mayúscula|
|`\d` / `\D`|**Dígito / No dígito**.|`` / `[^0-9]`|`"123"` / `"abc"`|
|`\w` / `\W`|**Carácter de palabra / No palabra** (letras, dígitos y `_`).|`[a-zA-Z0-9_]` / `[^a-zA-Z0-9_]`|`"hello_1"` / `"!@#"`|
|`\s` / `\S`|**Espacio en blanco / No espacio** (espacios, `\t`, `\n`, `\r`).|`[ \t\n\r\f\v]` / `[^ \t\n\r\f\v]`|Espacios y tabulaciones / texto|

---

### **3. Cuantificadores (Repetición)**

|Símbolo|Frecuencia|Modo|Ejemplo en Python|
|:--|:--|:--|:--|
|`*`|**0 o más** repeticiones.|Codicioso (_greedy_)|`r"a*"` \(\rightarrow\) `""`, `"a"`, `"aaa"`|
|`+`|**1 o más** repeticiones.|Codicioso (_greedy_)|`r"b+"` \(\rightarrow\) `"b"`, `"bbb"`|
|`?`|**0 o 1** repetición (opcional).|Codicioso (_greedy_)|`r"colou?r"` \(\rightarrow\) `"color"`, `"colour"`|
|`{n}`|Exactamente **n** repeticiones.|Exacto|`r"\d{4}"` \(\rightarrow\) `"2026"`|
|`{n,m}`|Entre **n** y **m** repeticiones.|Codicioso (_greedy_)|`r"\d{2,4}"` \(\rightarrow\) `"12"`, `"1234"`|
|`{n,}`|Al menos **n** repeticiones.|Codicioso (_greedy_)|`r"\d{2,}"` \(\rightarrow\) dos o más dígitos|
|`*?`, `+?`, `??`|**Cuantificadores perezosos (_lazy_)**: buscan la menor cantidad de caracteres.|Perezoso (_non-greedy_)|`r"<.*?>"` \(\rightarrow\) captura `<b>` en `<b>Hola</b>`|

---

### **4. Anclas y Límites de Posición (Aserciones de Ancho Cero)**

| Símbolo | Descripción                                         | Ejemplo en Python | Comportamiento                                       |
| :------ | :-------------------------------------------------- | :---------------- | :--------------------------------------------------- |
| `^`     | **Inicio de línea/cadena**.                         | `r"^Inicio"`      | Valida si el texto empieza por `"Inicio"`            |
| `$`     | **Fin de línea/cadena**.                            | `r"Fin$"`         | Valida si el texto termina en `"Fin"`                |
| `\A`    | **Inicio absoluto** de la cadena (ignora `re.M`).   | `r"\ATexto"`      | Coincide solo al principio de todo el string         |
| `\Z`    | **Fin absoluto** de la cadena.                      | `r"Texto\Z"`      | Coincide solo al final de todo el string             |
| `\b`    | **Límite de palabra** (frontera entre `\w` y `\W`). | `r"\bgato\b"`     | Coincide con `"gato"`, ignora `"gatos"` o `"gatuno"` |
| `\B`    | **No límite de palabra**.                           | `r"\Bsol\B"`      | Coincide dentro de palabras como `"parasol"`         |

---

### **5. Agrupación, Captura y Referencias**

|Sintaxis|Descripción|Uso práctico en Python|
|:--|:--|:--|
|`(...)`|**Grupo de captura**: agrupa subexpresiones y las guarda en memoria por índice (`1`, `2`...).|`m = re.search(r"(\w+)-(\d+)", s)` \(\rightarrow\) `m.group(1)`|
|`(?:...)`|**Grupo de no captura**: agrupa sin guardar en memoria para optimizar.|`r"(?:http\|
|`(?P<nombre>...)`|**Grupo de captura con nombre** exclusivo de Python / PCRE.|`m.group('nombre')` o `m.groupdict()`|
|`\1`, `\2`|**Referencia anterior (_backreference_)** por número dentro de la RegEx.|`r"\b(\w+)\s+\1\b"` (detecta palabras duplicadas)|
|`(?P=nombre)`|**Referencia anterior por nombre**.|`r"\b(?P<word>\w+)\s+(?P=word)\b"`|

---

### **6. Aserciones de Inspección (_Lookarounds_)**

|Sintaxis|Nombre|Descripción|
|:--|:--|:--|
|`(?=...)`|**Lookahead positivo**|Comprueba si el patrón siguiente coincide **sin consumir texto**.|
|`(?!...)`|**Lookahead negativo**|Comprueba si el patrón siguiente **NO** coincide.|
|`(?<=...)`|**Lookbehind positivo**|Comprueba si el patrón anterior coincide sin incluirlo en el resultado.|
|`(?<!...)`|**Lookbehind negativo**|Comprueba si el patrón anterior **NO** coincide.|

---

### **7. Banderas de Compilación (`flags` en `re.compile`)**

|Bandera (Nombre corto / Largo)|Efecto principal|
|:--|:--|
|`re.I` / `re.IGNORECASE`|Iguala mayúsculas y minúsculas al buscar.|
|`re.M` / `re.MULTILINE`|Permite que `^` y `$` coincidan en cada salto de línea de un texto.|
|`re.S` / `re.DOTALL`|Hace que el comodín punto `.` coincida también con saltos de línea `\n`.|
|`re.X` / `re.VERBOSE`|Permite escribir expresiones multilínea, ignorar espacios libres e incluir comentarios con `#`.|
|`re.A` / `re.ASCII`|Restringe las clases `\w`, `\d`, `\s` estrictamente al conjunto ASCII en cadenas Unicode.|

💡 **Nota clave para Python:** Para evitar la _"plaga de la barra invertida"_ (_backslash plague_), se recomienda definir siempre las expresiones regulares utilizando **cadenas crudas** (anteponiendo la letra `r` antes de las comillas, como `r"\d+\s+\w+"`). De lo contrario, el intérprete de Python procesará las barras invertidas antes de entregárselas al módulo `re`.

