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


### **2.3 Servicio SSH (Secure Shell)**
SSH es un servicio de **acceso remoto seguro** que permite administrar dispositivos de red y servidores mediante una conexión cifrada.

![[Pasted image 20260225073122.png]]

**¿Para qué se utiliza?**

- Administración remota de servidores.
- Configuración de switches y routers.
- Transferencia segura de archivos.
- Automatización mediante scripts.

**Ventajas**

- Comunicación cifrada.
- Autenticación fuerte.
- Sustituye a protocolos inseguros como Telnet.

**Desventajas**

- Requiere gestión adecuada de credenciales.
- Puede ser objetivo de ataques de fuerza bruta.
- Configuración incorrecta reduce su seguridad.

**Escenarios de uso comunes**

- Administración de servidores Linux.
- Gestión remota de infraestructura.
- Automatización de tareas de red.
- Operación de centros de datos.

### **2.4 Servicios FTP / TFTP / SFTP**

Servicios destinados a la **transferencia de archivos** entre dispositivos a través de una red.

- **FTP:** transferencia sin cifrado.
- **TFTP:** versión simple, sin autenticación.
- **SFTP:** transferencia segura sobre SSH.

![[Pasted image 20260225073106.png]]

**¿Para qué se utilizan?**
- Copia de archivos.
- Respaldo de configuraciones.
- Transferencia de firmware y software.

**Ventajas**
- Simplicidad.
- Amplio soporte en sistemas y dispositivos.
- SFTP ofrece seguridad elevada.

**Desventajas**
- FTP y TFTP no son seguros.
- Requieren controles de acceso.
- Pueden ser explotados si se exponen a Internet.

**Escenarios de uso comunes**
- Respaldo de configuraciones de red.
- Actualización de equipos.
- Transferencia interna de archivos.
- Laboratorios y entornos controlados.

### **2.5 Servicios HTTP / HTTPS**

Servicios que permiten la **publicación y acceso a contenido web**.

- **HTTP:** sin cifrado.
- **HTTPS:** cifrado mediante TLS.
![[Pasted image 20260225074305.png]]

**¿Para qué se utilizan?**
- Acceso a aplicaciones web.
- Interfaces gráficas de administración.
- Servicios web y APIs.

**Ventajas**
- Estándar universal.
- Fácil integración.
- HTTPS garantiza confidencialidad e integridad.

**Desventajas**
- HTTP no es seguro.
- Requiere certificados para HTTPS.
- Puede ser objetivo de ataques web.

**Escenarios de uso comunes**
- Portales institucionales.
- Paneles de administración.
- Aplicaciones empresariales.
- Servicios cloud

### **2.6 Servicio NFS (Network File System)**

NFS (Network File System) es un servicio de red que permite compartir sistemas de archivos a través de una red, de tal forma que los usuarios y aplicaciones pueden acceder a archivos remotos como si fueran locales.

![[Pasted image 20260225080426.png]]

**¿Para qué se utiliza NFS?**

NFS se utiliza principalmente para:
- Compartir directorios entre múltiples equipos.
- Centralizar información y recursos.
- Facilitar el acceso simultáneo a archivos.
- Evitar duplicación de datos en estaciones de trabajo.
- Proveer almacenamiento a servidores y aplicaciones.

En términos administrativos, NFS:
- Reduce la carga de mantenimiento.
- Simplifica respaldos.
- Permite un control más eficiente del acceso a la información.

**Ventajas**
- Transparencia para el usuario (archivos remotos se ven como locales).
- Centralización de la información.
- Fácil integración en entornos Linux/UNIX.
- Buen desempeño en redes locales.
- Ideal para entornos académicos y de laboratorio.

**Desventajas**
- Riesgos de seguridad si no se configura correctamente.
- Dependencia del servidor NFS.
- No es adecuado para redes públicas sin protección adicional.
- Control de acceso limitado en configuraciones básicas.

**Escenarios de uso comunes**
NFS se utiliza ampliamente en:
- Redes empresariales basadas en Linux.
- Laboratorios de cómputo universitarios.
- Clústeres de cómputo y HPC.
- Infraestructura virtualizada (VMware, Proxmox, KVM).
- Entornos on-premise y cloud privado.


### **2.7 Servicio de directorio (LDAP)** 
LDAP es un servicio que permite **centralizar la información de usuarios, grupos y recursos** en una red.
![[Pasted image 20260302073444.png]]

**¿Para qué se utiliza?**
- Autenticación centralizada.
- Control de acceso.
- Integración de servicios.

**Ventajas**
- Administración centralizada.
- Escalable. %%Puedes generar tantos usuarios como quieras, si se termina el espacio montas otro servidor%%
- Mejora la seguridad y control.

**Desventajas**
- Configuración compleja.
- Dependencia del servicio.
- Requiere planificación adecuada.

**Escenarios de uso comunes**
- Redes empresariales.
- Active Directory.
- Plataformas educativas.
- Infraestructura híbrida y cloud.

### **2.8 Servicio de correo electrónico (SMTP, POP, IMAP)**
Conjunto de servicios que permiten **enviar, recibir y almacenar correo electrónico**.
- **SMTP:** envío.
- **POP:** descarga local.
- **IMAP:** acceso remoto al buzón.

![[Pasted image 20260302080054.png]]

**¿Para qué se utiliza?**
- Comunicación institucional.
- Notificaciones automáticas.
- Alertas de sistemas.

**Ventajas**
- Medio de comunicación estándar.
- Integración con múltiples sistemas.
- IMAP permite acceso desde múltiples dispositivos.

**Desventajas**
- Objetivo de spam y phishing.
- Requiere medidas de seguridad.
- Administración compleja en servidores propios.

**Escenarios de uso comunes**
- Instituciones educativas.
- Empresas.
- Sistemas de monitoreo y alertas.

### **2.9 Servicio Proxy**
Un proxy es un servicio que **intermedia las comunicaciones** entre los usuarios y los servicios externos.

![[Pasted image 20260302080609.png]]

**¿Para qué se utiliza?**
- Controlar el acceso a Internet.
- Filtrar contenido.
- Mejorar el rendimiento mediante caché.

**Ventajas**
- Control y monitoreo.
- Mejora el desempeño.
- Apoyo a políticas de seguridad.

**Desventajas**- Punto único de falla.
- Configuración compleja.
- Puede afectar la experiencia del usuario.

**Escenarios de uso comunes**
- Redes escolares.
- Empresas.
- Control de navegación.
- Cumplimiento de políticas institucionales.