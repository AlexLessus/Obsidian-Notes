#vision_artificial 
# Enseñando a ver a las computadoras

## Introducción
%% Presentarme junto con el tema de visión artificial %%
¿Cuantos de aquí desbloquean su teléfono con su cara?
¿Alguna vez han intentado engañarlo con una foto? o con un espejo?
¿Les funcionó?
Un coche tesla que se maneja solo... ¿creen que ven lo mismo que nosotros? 
%% Preguntas para despertar curiosidad, cuando respondan: %%
Eso es lo que vamos a ver hoy: **el superpoder de darle ojos a las maquinas**

## Desarrollo 
%%Se intentará explicar los componentes y las fases del proceso%%
### - Componentes
La visión artificial nació porque queríamos emular la visión humana en una computadora; nos inspiramos en nuestro propio cuerpo para crearla.
- Para los **ojos**, utilizamos cámaras.
- Para el **cerebro**, utilizamos un procesador.
- Y para la **capacidad de razonar**, utilizamos la programación y los algoritmos.
%% analogía de los sentidos %%

Las máquinas necesitan lo mismo que nosotros para ver. Por ejemplo: la luz. Si intentan tomar una foto en un lugar oscuro y sin flash, en la cámara no se distinguirá nada. Sin una buena iluminación, hasta la computadora más potente está "ciega".

### -Procesamiento
Si les enseño una foto de un perro y una de un gato, ¿en qué se fijarían ustedes para no confundirlos? ¿En las orejas? ¿En la forma de la nariz?

Eso es exactamente lo que le enseñamos a una computadora: a identificar **patrones**. Pero para que la computadora no se confunda, la imagen debe pasar por una "línea de producción":
%%Como se hace?%%

#### 1 Pre-procesamiento
Antes de darle la foto a la computadora es necesario prepararla para que pueda saber que hay en la foto
En pocas palabreas se aplican filtros a la imagen.

#### 2 Segmentación
Este es de los procesos más interesantes.

- **Detección de bordes:** La computadora dibuja los contornos de las cosas para saber dónde empieza y termina cada objeto.
- **Extracción de regiones:** Imaginen una foto de un campo de berries aquí en la región; la segmentación separa cada bolita roja del fondo verde para poder contarlas una por una de forma automática.

#### 3 Seguimiento
El _tracking_ es como seguir a un jugador en un partido de fútbol sin quitarle la vista de encima. Una cámara de seguridad puede seguir a una persona en movimiento o un sistema puede contar cuántos carros pasan por un semáforo en tiempo real.


## Conclusiones
Para lograr todo esto, usamos matemáticas, lógica y herramientas de programación como **OpenCV** o **Python**. Todo esto es lo que aprendemos aquí en la carrera de Sistemas.

La visión artificial se aplica en todo: desde ayudar a los agricultores de Ciudad Guzmán a identificar aguacates defectuosos o detectar plantas enfermas mediante drones, hasta en la medicina para detectar enfermedades de forma temprana.
## Despedida emotiva
"Muchos piensan que para crear tecnología de punta hay que irse a la NASA, pero la realidad es que aquí mismo, en el **ITCG**, estamos construyendo el futuro. Ustedes tienen el talento, solo necesitan las herramientas. No solo estudien una carrera, elijan una forma de cambiar el mundo. ¡Los esperamos en los pasillos del Tec!"%%Despedida con ayuda de Gemini, soy pésimo para escribir cosas emotivas%%
