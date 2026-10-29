Alexis De Jesus Perez Carmona


### Plataforma/herramienta/lenguaje de programación utilizado: 
Python

### Agente conversacional
### Tipo de preguntas o acciones que hay que indicarle al agente para que realice su tarea y nos otorgue el servicio, o tipo de preguntas que podemos realizarle:
Responde preguntas sobre la carrera de sistemas. Identifica patrones como Que es, De que trata y con esto identifica la posible respuesta

### Guía de cómo realizar su ejecución o activación según sea el caso
####  Cómo ejecutarlo
1. Guarda el código en un archivo llamado `agente_sistemas.py`.
2. Abre tu terminal o consola de comandos.    
3. Ejecuta el script con el comando: `python agente_sistemas.py`.    
4. Comienza a escribir preguntas como _"¿Cuáles son las materias?"_ o _"¿Es muy difícil la carrera?"_.
### Código
``` python
import re

def obtener_respuesta(mensaje):
    mensaje = mensaje.lower()
    
    # Diccionario de intenciones (patrones) y sus respuestas
    respuestas = {
        r".*(que es|de que trata|que es).*": "La carrera de Sistemas Computacionales se enfoca en el diseño, desarrollo y mantenimiento de software, hardware y redes. Es la base de la tecnología moderna.",
        r".*(materias|asignaturas|que se estudia|plan de estudios).*": "Llevarás materias como Programación (C++, Java, Python), Bases de Datos, Redes, Matemáticas Discretas, Inteligencia Artificial y Arquitectura de Computadoras.",
        r".*(trabajo|campo laboral|donde puedo trabajar|empleo).*": "El campo laboral es inmenso. Puedes ser Desarrollador de Software, Científico de Datos, Administrador de Servidores, Experto en Ciberseguridad o Líder de Proyectos TI.",
        r".*(difícil|complicado|pesado).*": "Tiene su nivel de exigencia, sobre todo en matemáticas y lógica, pero si disfrutas resolver problemas y la tecnología, se vuelve una carrera muy gratificante.",
        r".*(hola|saludos|buenos).*": "¡Hola! Soy tu asistente virtual sobre la carrera de Sistemas Computacionales. ¿Qué te gustaría saber sobre esta ingeniería?",
        r".*(adiós|bye|hasta luego).*": "¡Hasta luego! Si tienes más dudas sobre programación o la carrera, aquí estaré."
    }
    
    # Busca la primera coincidencia en los patrones
    for patron, respuesta in respuestas.items():
        if re.search(patron, mensaje):
            return respuesta
            
    # Respuesta por defecto si no reconoce la intención
    return "No estoy seguro de entender eso. Puedes preguntarme sobre qué trata la carrera, las materias que se llevan o el campo laboral."

def iniciar_chat():
    print("🤖 Asistente de Sistemas Computacionales")
    print("¡Hola! Pregúntame lo que quieras sobre la carrera. (Escribe 'salir' para terminar)\n")
    
    while True:
        entrada = input("Tú: ")
        if entrada.lower() in ['salir', 'exit', 'quit', 'adiós', 'adios']:
            print("🤖 Asistente: ¡Mucho éxito en tu camino como ingeniero! Nos vemos.")
            break
        
        respuesta = obtener_respuesta(entrada)
        print(f"🤖 Asistente: {respuesta}\n")

if __name__ == "__main__":
    iniciar_chat()
	
```

### Capturas de pantallas
![[Pasted image 20261020231455.png]]

![[Pasted image 20261020231642.png|700]]![[Pasted image 20261020231746.png]]