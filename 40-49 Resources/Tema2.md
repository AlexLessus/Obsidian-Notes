### **Servicios de red**
Un **servicio de red** es un conjunto de procesos, protocolos y recursos que permiten a los usuarios y dispositivos **compartir información, recursos y funcionalidades** a través de una red de cómputo.

Desde el punto de vista del administrador de redes, los servicios de red:
- Son críticos para la operación diaria.
- Requieren configuración, monitoreo y mantenimiento continuo.
- Impactan directamente en disponibilidad, desempeño y seguridad.

Ejemplos comunes:
- Asignación de direcciones IP.
- Resolución de nombres.
- Acceso remoto seguro.
- Transferencia de archivos.
- Autenticación de usuarios.
### **2.1 Servicio DHCP (Dynamic Host Configuration Protocol)**
DHCP es un servicio de red que permite **asignar automáticamente direcciones IP y parámetros de red** a los dispositivos que se conectan a una red.

%%
	Se debe configurar correctamente, establecer un tiempo para refresco de ips segun su actividad, 
%%

**¿Para qué se utiliza?**
- Evitar la configuración manual de direcciones IP.
- Garantizar que los dispositivos obtengan:
- Dirección IP
- Máscara de red
- Puerta de enlace
- Servidores DNS

**Ventajas**
- Reduce errores de configuración.
- Facilita la administración en redes grandes.
- Permite reutilización eficiente de direcciones IP.
- Escalable y flexible.

**Desventajas**
- Dependencia del servidor DHCP.
- Riesgo de ataques si no está protegido (DHCP rogue).%%Si no se configura correctamente se muere la red, hay varios dhcp y pueden existir conflictos entre ellos%%
- Menor control individual si no se usan reservas.%%Reservas son ip reservadas, no se asignan con el dhcp %%

**Escenarios de uso comunes**
- Redes empresariales y campus.
- Redes Wi‑Fi.
- Laboratorios de cómputo.
- Entornos virtualizados y cloud.


### **2.2 Servicio DNS (Domain Name System)**
DNS es un servicio que permite **traducir nombres de dominio legibles por humanos** (ej. [www.tecnm.mx](http://www.tecnm.mx/)) en **direcciones IP** que utilizan los dispositivos de red.


**¿Para qué se utiliza?**
- Facilitar el acceso a servicios sin memorizar IPs.
- Localizar servidores y servicios en la red.
- Soportar servicios como correo, web y directorios.

**Ventajas**
- Simplifica el uso de la red.
- Permite cambios de IP sin afectar a los usuarios.
- Fundamental para prácticamente todos los servicios modernos.

**Desventajas**
- Punto crítico de falla si no hay redundancia.
- Objetivo frecuente de ataques (spoofing, poisoning).
- Requiere mantenimiento y actualización.

**Escenarios de uso comunes**
- Internet.
- Redes empresariales internas.
- Active Directory y servicios de autenticación.
- Infraestructura cloud y microservicios.


