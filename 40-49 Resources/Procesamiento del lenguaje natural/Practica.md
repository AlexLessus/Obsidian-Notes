
``` python
corpus = [
 {"id": 1,
 "texto": "¡¡¡EXCELENTE curso de PLN!!! Aprendí muchísimo \U0001f60a\U0001f60a."},
 {"id": 2,
 "texto": "No me gustó la explicación de tokenización... fue confusa \U0001f615."},
 {"id": 3,
 "texto": "<p>Los profesores explicaron MUY bien.</p> ¡Gracias!"},
 {"id": 4,
 "texto": "Consulta el material en https://ejemplo.com/pln."},
 {"id": 5,
 "texto": "Tengo dudas; escriban a curso@ejemplo.com antes del 25/09/2026."},
 {"id": 6,
 "texto": "El taller cuesta $350.50 e incluye 3 sesiones."},
 {"id": 7,
 "texto": "Los alumnos estaban estudiando, estudiaron y estudiarán Python."},
 {"id": 8,
 "texto": "Las niñas llevaron libros y los niños llevaron libretas."},
 {"id": 9,
 "texto": "Ayer fui al laboratorio; el semestre pasado fui representante."},
 {"id": 10,
 "texto": "Este ejercicio es mejor; ahora comprendo mejor los ejemplos."},
 {"id": 11,
 "texto": "El archivo está listo: dámelo. Las actividades quedaron deshechas."},
 {"id": 12,
 "texto": "Holaaaa!!! El curso está muuuy bueno.\n\tQuiero otra sesión."},
 {"id": 13,
 "texto": "No estuvo mal, pero nunca explicaron las expresiones regulares."},
 {"id": 14,
 "texto": "La programación es útil. #AprenderPLN @curso_pln"},
 {"id": 15,
 "texto": "Sí entendí la práctica; si tengo dudas, preguntaré."},
 {"id": 16,
 "texto": "Excelente... otra vez no funciona el programa \U0001f644."},
]
```
### Actividad 2 Detectar y clasificar el ruido 
Subtema 2.2: ruido en el texto. 

Inspecciona los 16 documentos e identifica al menos ocho tipos de elementos que requieran revisión. Decide si deben conservarse, eliminarse o transformarse y justifica cada decisión.

| Elemento                                           | Ejemplo                                  | Decisión y justificación                                                                                                                                                                                                           |
| -------------------------------------------------- | ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Etiquetas                                          | \<p>...\<p>                              | Eliminar etiquetas y conservar su contenido                                                                                                                                                                                        |
| Espacios repetidos                                 | Tres    espacios                         | Reducir a un espacio.                                                                                                                                                                                                              |
| Emojis                                             | Sonrisa y ojos en blanco                 | Conservar o representar con etiquetas; aportan información.                                                                                                                                                                        |
| Negaciones                                         | no, nunca                                | Conservar para evitar cambios de sentido.                                                                                                                                                                                          |
| Alargamiento léxico                                | `Holaaaa`, `muuuy`                       | Transformar, Modifican artificialmente el vocabulario creando términos inexistentes. Debe hacerse de forma controlada para no afectar palabras válidas como _"leer"_ o _"acción"_                                                  |
| Direcciones web (URLs) y correos electrónicos      | www.cdguzman.tecnm.mx  curso@ejemplo.com | **Extraer primero y sustituir por etiqueta** (`_URL_`, `_EMAIL_`) o eliminar del texto de análisis                                                                                                                                 |
| Metadatos de redes sociales (Hashtags y Menciones) | `#AprenderPLN`, `@curso_pln`             | Extraer y transformar, El hashtag contiene tópicos de interés (`AprenderPLN`), mientras que la mención suele ser solo un identificador de destino                                                                                  |
| Puntuación enfática o repetida                     | !!!  ...                                 | Transformar, La repetición denota énfasis o duda, pero como tokens dificultan la lematización y aumentan la dispersión léxica innecesariamente.                                                                                    |
| Datos estructurados                                | 25/09/2026, $350.50                      | Extraer **previamente y transformar a tokens genéricos** (`_FECHA_`, `_MONEDA_`), Números específicos no generalizan temas; al agruparlos bajo una etiqueta homogénea se preserva el contexto semántico sin inflar el vocabulario. |
| Mayúsculas sostenidas                              | EXCELENTE, MUY                           | Transformar a minúsculas, Ayuda a unificar el vocabulario                                                                                                                                                                          |


### Actividad 3 
Extraer información con expresiones regulares
Subtema 2.7: expresiones regulares. 
Antes de limpiar, utiliza re.findall() o re.finditer() para extraer correos, direcciones web, fechas dd/mm/aaaa, cantidades monetarias con decimales, hashtags y menciones. Registra el identificador, el tipo y el valor encontrado.

``` python
import re

# Diccionario de patrones Regex requeridos
patrones = {
    # URL: Evita capturar signos de puntuación finales como '.', ',', ')' al terminar en [a-zA-Z0-9/]
    "URL": r"https?://[^\s/$.?#].[^\s]*[a-zA-Z0-9/]",
    # Correo: formato usuario@dominio.extension evitando capturar signos de puntuación adyacentes
    "Correo": r"[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+[a-zA-Z0-9]",
    # Fecha: Formato dd/mm/aaaa (dos dígitos / dos dígitos / cuatro dígitos)
    "Fecha": r"\b\d{2}/\d{2}/\d{4}\b",
    # Cantidad: Símbolo de moneda escapado (\$ o \$?), dígitos, punto y dos decimales
    "Cantidad": r"\$\d+(?:\.\d{2})",
    # Hashtag: Símbolo # seguido de caracteres alfanuméricos o guión bajo
    "Hashtag": r"#\w+",
    # Mención: Símbolo @ seguido de caracteres alfanuméricos o guión bajo
    "Mención": r"@\w+",
}

# Extracción de entidades sobre el corpus
resultados = []

for doc in corpus:
    doc_id = doc["id"]
    texto = doc["texto"]

    for tipo, patron in patrones.items():
        # Uso de re.finditer() para capturar coincidencias sin alterar el texto original
        coincidencias = re.finditer(patron, texto)
        for match in coincidencias:
            resultados.append(
                {"id": doc_id, "tipo": tipo, "valor": match.group()}
            )

# Mostrar resultados en formato de tabla
print(f"{'Documento':<12} | {'Tipo':<12} | {'Valor Extraído'}")
print("-" * 45)
for res in resultados:
    print(f"{res['id']:<12} | {res['tipo']:<12} | {res['valor']}")
```
