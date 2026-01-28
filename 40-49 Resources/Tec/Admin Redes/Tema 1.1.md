### **Administración de redes.**

La administración de redes es un servicio que emplea una variedad de herramientas, aplicaciones y dispositivos para ayudar a los administradores de la red, en la configuración, supervisión y mantenimiento de la red.

El término administración de redes es definido como la suma total de todas las políticas, procedimientos que intervienen en la planeación, configuración, control, monitoreo de los elementos que conforman a una red con el fin de asegurar el eficiente y efectivo empleo de sus recursos. Lo cual se verá reflejado en la calidad de los servicios ofrecidos.
![[Pasted image 20260128000106.png]]

A partir de una buena administración de una red, se puede definir como una red eficiente, teniendo en cuenta los puntos que se encuentran dentro de esta unidad y que son:

- **Administración de la configuración.**
En este punto se administra la configuración de puerto, switches, entre cualquier equipo de hardware configurable, teniendo una configuración optima y necesaria para el uso de la red

- **Administración de fallas**
Cada falla debe de ser notificada, así mismo debe de tener una solución inmediata para evitar alguna inconsistencia en el desempeño de la red

- **Administración de contabilidad.**
En este punto se administran los recursos utilizados para la red.

- **Administración del desempeño.**
Se tiene que ver punto por punto de las funciones de la red, para que el desempeño de esta se eficiente y eficaz.

- **Administración de la seguridad.**
La seguridad es un punto elemental en una red, que no se debe tomar en segundo plano, ya que este punto puede perjudicar a daños severos para el desempeño de la red.

### 1.1 Administración de la configuración.

La **Administración de la Configuración** consiste en recopilar, almacenar, rastrear y controlar las configuraciones de todos los dispositivos y componentes de la red (hardware, software, parámetros), gestionando cambios, inventario y despliegue para asegurar que todo funcione correctamente y sea escalable.

El administrador de red debe conocer los objetivos de la red que administra. Bajo ese concepto debe configurar servicios y establecer políticas que afectarán a todos los usuarios. Algunas de las labores que sólo pueden hacerse como administrador de red son:

- Nombre de la cuenta que permite administrar un sistema Linux.
- Configurar los programas que se inician junto con el sistema.
- Administrar cuentas de usuarios.
- Administrar los programas y la documentación instalada.
- Configurar los programas y los dispositivos.
- Configurar la zona geográfica, fecha y hora.
- Administrar espacio en discos y mantener copias de respaldo.
- Configurar servicios que funcionarán en red.
- Solucionar problemas con dispositivos o programas. Labor que resulta en ocasiones la más dispendiosa, pero que se facilitará entre más aprenda del sistema y la red a su cargo.![[Pasted image 20260128000159.png]]
El administrador es el encargado de los aspectos de configuración de dispositivos de la red, como los archivos de configuración de dichos dispositivos y la administración del software, así como también el almacenamiento en un lugar que sea accesible por el personal autorizado.

Dentro de un administrador de redes, la configuración cumple con algunas de las siguientes actividades:

- **Recolección de datos sobre el estado de la red:** Para ello generalmente se emplean dos tipos de herramientas que funcionan de forma automática: las herramientas de autodescubrimiento (_auto-discovery_) y las herramientas de autotopología (_auto-mapping_). La primera lleva a cabo un sondeo periódico de la red para averiguar qué elementos están activos y con qué características; la segunda averigua de qué forma están interconectados los distintos elementos de la red. Toda esta información se representa gráficamente mediante un mapa topológico.
- **Cambio en la configuración de los recursos:** Cualquier cambio de configuración de recursos debe ser notificado al personal de uso final de red, para que este sea consciente del cambio y no perjudique los procesos en los que se efectúa la red.
- **Almacenamiento de los datos de configuración:** Todos los datos obtenidos han de ser almacenados para obtener el inventario de red.

Para realizar dichas labores, el administrador de red puede apoyarse en las siguientes herramientas de automatización:

- **Ansible:** Es una herramienta _agentless_ que permite gestionar dispositivos de red mediante módulos específicos para switches, routers y firewalls. Se basa en playbooks YAML ejecutados desde un nodo de control que gestionan inventarios, conectividad (SSH/NETCONF/RESTAPI) y configuración declarativa. Ideal para evitar la tarea manual de configuración, conservar el histórico de cambios y aplicar configuraciones consistentes.
- **Python + REST API (o Netmiko/NAPALM):** Permite automatizar tareas como extracción de CLI, configuración de interfaces, ACLs o QoS mediante scripts que utilizan librerías como _requests_, _Paramiko_, _Netmiko_ o _NAPALM_. Soporta control programático, lógica condicional, integración con inventarios y generación de reportes automáticos.