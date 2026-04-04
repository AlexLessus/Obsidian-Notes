# Sistema de visión para el acceso de vehículos al estacionamiento del acceso 2 del ITCG

Alexis De Jesus Perez Carmona
## Problemática
Siempre ha sido un problema controlar el acceso de automóviles al estacionamiento exclusivo para el personal del ITCG (Acceso 2), por lo que les solicitan, basado en su gran experiencia en el diseño de sistemas de visión, que diseñen una solución basada en un sistema de visión (SVA) precisamente. Dentro de las capacidades que debe de tener el sistema, es identificar si es del personal o no el automóvil que trata de entrar al estacionamiento, si lo es dar acceso a éste, pero en caso de que no, deberá dirigirlo a cualquiera de los otros tres accesos. También deberá de darle a conocer de acuerdo a las dimensiones del automóvil cuál de las dos áreas es la más indicada para ello (carro grande a la derecha y carro chico mediando a la izquierda). 

--- 
## Propuesta
### **Escenario**
El Sistema de Visión Artificial (SVA) se desplegará en el Acceso 2 del ITCG, aprovechando la infraestructura existente. La cámara se instalará en la caseta de vigilancia actual, con un ángulo frontal apuntando directamente al área de detención de los vehículos, justo antes de la pluma de acceso. El sistema reemplazará o complementará el uso de tarjetas RFID, automatizando la entrada mediante la lectura de matrículas.

### Componentes de Hardware y Software
- **Hardware:**
    - **Cámara IP:** TP-Link Tapo C325WB (seleccionada por su capacidad de visión nocturna a color, fundamental para evitar el deslumbramiento en las placas reflectantes).        
    - **Unidad de Procesamiento Central:** Raspberry Pi 4 (8GB RAM) o Raspberry Pi 5. Funcionará como cerebro del sistema, procesando el video, alojando la base de datos y controlando los actuadores.        
    - **Actuadores y Periféricos:** Módulo de relevadores (conectado a los pines GPIO de la Raspberry Pi) para la apertura de la pluma, y una pantalla LED exterior con comunicación serial/I2C.        
- **Software:**    
    - **Lenguaje:** Python.        
    - **Librerías de Visión:** OpenCV (manejo del flujo RTSP y preprocesamiento) y EasyOCR o Tesseract para la extracción de texto.        
    - **Base de Datos:** SQLite o PostgreSQL de forma local. Para mantener el entorno ordenado y fácilmente replicable, la base de datos y los scripts de Python pueden ejecutarse dentro de contenedores de Docker en la misma Raspberry Pi.

### Arquitectura del sistema de visión
El sistema sigue una arquitectura de procesamiento en el borde (_Edge Computing_). 
La cámara transmite un flujo de video constante (RTSP) a la red local. La Raspberry Pi captura este flujo y procesa los fotogramas localmente, asegurando que el sistema siga funcionando incluso si hay caídas en el servicio de internet del campus. Al procesar todo en el mismo dispositivo, la latencia desde que el auto se detiene hasta que la pluma se abre se reduce a 1 o 2 segundos.

### Módulos de la Implementación
- **Módulo de Captura (Video Streaming):** Se encarga de leer el protocolo RTSP de la cámara Tapo. Extrae fotogramas a una tasa baja (ej. 2-3 FPS) para no saturar la memoria de la Raspberry Pi.    
- **Módulo de Procesamiento (ALPR):** Aplica filtros de contraste mediante OpenCV para resaltar los caracteres de la matrícula y utiliza un modelo ligero de Reconocimiento Óptico de Caracteres para convertir la imagen a una cadena de texto.    
- **Módulo de Validación Lógica:** Toma la cadena de texto y ejecuta una consulta SQL en la base de datos local. Verifica si la matrícula pertenece a un miembro del personal activo y recupera la dimensión del vehículo registrado.    
- **Módulo de Control I/O:** Basado en la respuesta de la base de datos, utiliza los pines GPIO de la Raspberry Pi para mandar la señal de cierre de circuito al relevador de la pluma y transmite el texto correspondiente ("Izquierda" o "Derecha") a la pantalla LED.

### Algoritmo y Proceso de Uso
1. El vehículo llega al Acceso 2 y se posiciona frente a la pluma.
2. El script en la Raspberry Pi detecta la matrícula en el flujo de video y extrae el texto (ej. JAL-123).
3. Se realiza la consulta en la base de datos local de vehículos autorizados.
4. **Validación Negativa:** Si la placa no existe en el registro, la pluma se mantiene abajo. La pantalla LED muestra: "Acceso Denegado - Diríjase a accesos 1, 3 o 4".
5. **Validación Positiva:** Si la placa existe, se lee el tamaño del auto.
6. La Raspberry Pi envía un pulso alto (HIGH) al relevador, abriendo la pluma.
7. Simultáneamente, la pantalla LED muestra un mensaje de bienvenida y la instrucción direccional: "Auto Grande - Estacione a la DERECHA" o "Auto Chico/Mediano - Estacione a la IZQUIERDA".
### Diagrama de Flujo:
![[Diagrama en blanco.png]]