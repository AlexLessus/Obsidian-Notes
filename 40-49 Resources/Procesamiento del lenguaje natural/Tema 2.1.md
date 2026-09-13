
### Corpus
Colección de documentos reunidos para un propósito
Ejemplo: 100 comentarios de estudiantes
### Documento
Una unidad de texto dentro del corpus
Ejemplo: un comentario
### Palabra
Unidad lingüística o función gramatical

### Token
Unidad que produce un tokenizador
Un token puede ser una palabra, un signo o parte de una palabra


#### Un corpus de 100 documentos tiene necesariamente 100 archivos?
**No, no necesariamente.** En Procesamiento del Lenguaje Natural (PLN) y Recuperación de Información, existe una diferencia clara entre la **unidad lógica (documento)** y la **unidad física de almacenamiento (archivo)**:

1. **Documento (Unidad Lógica/Semántica):** Es cada una de las instancias de texto independientes que componen el corpus según la tarea (por ejemplo, un tuit, una reseña de cliente, una noticia, un capítulo o una respuesta).
2. **Archivo (Unidad Física):** Es el contenedor en el sistema de archivos de tu computadora o servidor (como `.txt`, `.csv`, `.json`, `.parquet` o `.zip`).

**¿Cómo se relacionan en la práctica?**

- **1 archivo** $\rightarrow$ **100 documentos (Muy común):** Puedes tener un único archivo estructurado (por ejemplo, un dataset en formato `.csv`, `.jsonl` o `Pandas DataFrame`) que contiene 100 filas o registros. Para el modelo o algoritmo de PLN, ese único archivo físico contiene un corpus de **100 documentos**.
- **100 archivos** $\rightarrow$ **100 documentos:** Este es el caso tradicional en el que cada documento se guarda de forma independiente en su propio archivo de texto individual (por ejemplo, 100 archivos `.txt` en una carpeta).
- **Varios archivos** $\rightarrow$ **1 documento (o fragmentación):** En datasets masivos o procesamiento distribuido, un documento muy extenso (o un corpus) puede fragmentarse (_sharding_) en múltiples archivos comprimidos (como `.tar.gz` o `.json.gz`) para facilitar su lectura en memoria.


