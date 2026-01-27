![[Pasted image 20260119203209.png]]
### 1. El Problema: La "Amnesia" de Android

Imagina que estás llenando un formulario largo en tu App. De repente, giras el celular para verlo en horizontal.

- **Sin ViewModel:** Android destruye tu pantalla (Activity) y la vuelve a crear para ajustarse al nuevo tamaño. En ese proceso, **¡se borran todos los datos que escribiste!** Es como si tuvieras memoria de pez.
    
- **Con ViewModel:** La pantalla se destruye, pero el ViewModel se queda vivo en una "burbuja" segura. Cuando la pantalla vuelve a nacer, le pregunta al ViewModel: _"¿Qué estaba haciendo?"_ y el ViewModel le devuelve todos los datos intactos.
    

### 2. ¿Qué hace exactamente?

El ViewModel tiene dos responsabilidades clave:

#### A. Es el "Guardián de los Datos" (Sobrevive a la rotación)

Evita que tengas que volver a cargar datos de internet o de la base de datos cada vez que el usuario gira el celular o cambia el modo oscuro/claro.

#### B. Separa la Lógica de la Vista

- **La Activity (Vista)** solo debe preocuparse por **mostrar cosas** (pintar colores, mostrar textos, detectar clics).
    
- **El ViewModel** se preocupa por la **lógica** (validar si el email es correcto, llamar a la base de datos, sumar el carrito de compras).
    

> **Regla de Oro:** El ViewModel NUNCA debe tener referencias a elementos visuales (como `TextView`, `Button` o `Context`). Si lo hace, causará fugas de memoria. El ViewModel no sabe cómo se ve la pantalla, solo sabe qué datos tiene.