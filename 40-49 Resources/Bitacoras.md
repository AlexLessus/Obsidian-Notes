#redes [[Administración de redes]]
El nombre bitácora está basado en los cuadernos de bitácora, cuadernos de viaje que se utilizaban en los barcos para relatar el desarrollo del viaje y que se guardaban en la bitácora.

El **logging** es el proceso mediante el cual los **sistemas, dispositivos y aplicaciones registran información sobre su funcionamiento**, actividades y eventos relevantes en archivos o bases de datos llamados **registros**.

Desde la perspectiva de la **administración de redes**, el logging es fundamental para:
- Monitorear el estado de los dispositivos.
- Detectar fallas y comportamientos anómalos.
- Investigar incidentes de seguridad.
- Analizar el desempeño de la red.
- Mantener evidencia histórica para auditorías.

En términos simples: **Si algo ocurre en la red, debe quedar registrado.**
Uno de los errores más comunes, es utilizar indistintamente los términos bitácora, log, evento y alerta. A continuación, se presentan sus diferencias claras.

### Bitácora
Una **bitácora** es el **conjunto organizado y cronológico de registros** que documentan la actividad de un sistema, dispositivo o red durante un periodo de tiempo.
>es un registro de TODO lo que sucede en nuestra red
**Características:**
- Tiene un enfoque histórico.
- Puede contener múltiples tipos de registros.
- Se utiliza para análisis posterior y auditoría.

**Ejemplo:** El archivo que almacena todos los accesos, errores y mensajes de un servidor durante un mes.
![[Pasted image 20260413072017.png]]

>Con la bitacora podemos registrar todo lo que pasa en la red, asi podemos identificar si la red se comporta como debería e identificar problemas

### **Log**
Un **log** es un **registro individual** o un **archivo de registros** que contiene información detallada sobre una acción o suceso específico.

**Características:**
- Es una unidad básica de información.
- Contiene datos como fecha, hora, origen y descripción.
- Puede almacenarse en archivos o sistemas centralizados.

**Ejemplo:** Un registro que indica que un usuario inició sesión exitosamente a las 10:35 hrs.
![[Pasted image 20260413072723.png]]
El log es mas especifico, solo tendrá información de un servicio en especial


### **Evento**
Un **evento** es un **suceso detectado por el sistema** que ocurre en un momento determinado y que puede o no ser relevante para el administrador.

**Características:**
- No todos los eventos son errores.
- Pueden ser informativos, de advertencia o críticos.
- Un evento genera uno o varios logs.

**Ejemplo:** El reinicio de un servicio o la conexión de un dispositivo a la red.
![[Pasted image 20260413073120.png]]
Cualquier cosa que suceda dentro de la red

### **Alerta**
Una **alerta** es una **notificación generada cuando un evento cumple una condición definida** que requiere atención del administrador.

**Características:**
- Es selectiva (no todo evento genera alerta).
- Puede enviarse por correo, SMS o panel de monitoreo.
- Está asociada a umbrales o reglas.

**Ejemplo:** Una notificación enviada cuando el uso de CPU supera el 90%.
![[Pasted image 20260413073504.png]]
Cuando sucede algo fuera de lo normal se envía una alerta

### **Relación entre bitácora, log, evento y alerta**
Para reforzar la comprensión, se presenta la relación jerárquica:

**Evento → Log → Bitácora → Alerta (si aplica)**

- Un **evento** ocurre.
- Se registra como **log**.
- Se almacena en una **bitácora**.
- Si cumple una regla, genera una **alerta**.

## **Clasificación de logs en la administración de redes**
Para facilitar su análisis y administración, los logs se clasifican según su naturaleza.
### **Logs de sistema**
Registran el funcionamiento interno del sistema operativo o dispositivo de red.

**Incluyen:**
- Arranque y apagado.
- Carga de servicios.
- Errores del sistema.

**Ejemplos:**
- Fallo al iniciar un servicio.
- Reinicio inesperado de un equipo.

**Uso administrativo:**
- Diagnóstico de fallas.
- Mantenimiento preventivo.

### **Logs de seguridad**
Registran eventos relacionados con el **control de acceso y protección de la red**.

**Incluyen:**
- Intentos de inicio de sesión.
- Accesos fallidos.
- Cambios de permisos.
- Detección de intrusiones.

**Ejemplos:**
- Intento fallido de acceso por SSH.
- Bloqueo por firewall.

**Uso administrativo:**
- Investigación de incidentes.
- Auditorías de seguridad.
- Cumplimiento normativo.

### **Logs de aplicación**
Registran eventos generados por **aplicaciones y [servicios de red](https://apps.cdguzman.tecnm.mx/itcg/mod/forum/view.php?id=105093 "Servicios de red")**.

**Incluyen:**
- Errores de aplicaciones.
- Accesos a servicios web.
- Consultas a bases de datos.

**Ejemplos:**
- Peticiones HTTP.
- Errores de un servidor DNS o DHCP.

**Uso administrativo:**
- Solución de problemas de servicios.
- Análisis de desempeño.
- Optimización de aplicaciones.

### **Relación con herramientas de monitoreo**
Las herramientas como **OpManager, Zabbix, Nagios o Splunk** no sustituyen el logging; lo **aprovechan**:

- Centralizan logs.
- Filtran eventos relevantes.
- Generan alertas automáticas.
- Presentan información de forma visual.