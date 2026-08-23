Alexis De Jesus Perez Carmona  22290827

1. Qué es la nube, qué características tiene y cómo funciona?
La **computación en la nube (Cloud Computing)** es el modelo que permite el acceso bajo demanda, y a través de internet, a un conjunto compartido de recursos de computación configurables (redes, servidores, almacenamiento, aplicaciones y servicios) con un mínimo esfuerzo de gestión o interacción con el proveedor.
**Características esenciales (según el NIST):**

- **Autoservicio bajo demanda:** Puedes adquirir capacidades de cómputo automáticamente sin intervención humana del proveedor.
- **Acceso amplio a la red:** Disponible desde cualquier dispositivo y ubicación.
- **Asignación común de recursos (Resource Pooling):** Los recursos del proveedor atienden a múltiples usuarios usando un modelo multi-inquilino (_multi-tenant_).
- **Elasticidad rápida:** Capacidad de escalar (crecer o reducir recursos) de forma automática y vertical/horizontal según la demanda.
- **Servicio medido:** Pagas exactamente por lo que consumes (como la luz o el agua).

**¿Cómo funciona?** Se basa fuertemente en la **virtualización**. Capas de software (hipervisores) dividen los recursos de servidores físicos reales en múltiples máquinas virtuales o contenedores aislados. Cuando subes tu API o base de datos, no la pones en una computadora física específica, sino en este ecosistema virtualizado gestionado por el proveedor.

2. Cuáles son los modelos de servicio que ofrece la nube y cuáles sus costos?
Los servicios en la nube se dividen tradicionalmente en tres capas conceptuales. A nivel de **costos**, la nube rompe el modelo tradicional de **CapEx** (Gasto de Capital: comprar servidores físicos caros por adelantado) y lo transforma en **OpEx** (Gasto Operativo: pagar una suscripción mensual o una tarifa por segundo/minuto de uso).

3. Qué características tiene IAAS, que tanto le implica al usuario implementarlo?
(Infrastructure as a Service)
	- **Características:** Se te proporciona acceso a recursos de infraestructura pura: servidores virtuales, espacio de almacenamiento, redes y sistemas operativos. Tú tienes el control total de la máquina virtual.
	- **Implicación para el usuario:** **Alta.** Eres responsable de instalar el sistema operativo (o parcharlo), configurar el firewall, instalar el entorno de ejecución (ej. Node.js, Docker), gestionar las bases de datos y asegurar el servidor contra ataques.

4. Qué características tiene PAAS, que tanto le implica al usuario implementarlo?
(Platform as a Service)
	- **Características:** El proveedor te da una plataforma con el entorno de ejecución listo. Ya incluye el sistema operativo, base de datos gestionada, servidores web y herramientas de desarrollo.
	- **Implicación para el usuario:** **Media-Baja.** Tú solo te preocupas por tirar código y desplegar tu aplicación. El proveedor se encarga del escalado, parches de seguridad del S.O. y alta disponibilidad. Es ideal para acelerar el desarrollo de tu Proyecto Integrador.

5. Qué características tiene SAAS, que tanto le implica al usuario implementarlo?
(Software as a Service)
	- **Características:** El software está completamente alojado y gestionado por el proveedor. Accedes a él directamente desde un navegador web o API.
	- **Implicación para el usuario:** **Mínima.** No programas nada a nivel de infraestructura ni código base; solo configuras opciones de usuario y consumes el servicio.
6. Describe los tipos de nubes: nube privada, nube pública, nube híbrida, nube de comunidad 
	- **Nube Pública:** Los recursos (servidores, almacenamiento) pertenecen a un proveedor externo y se comparten con otros "inquilinos" a través de internet. (Ej. AWS, Azure).
	- **Nube Privada:** La infraestructura es de uso exclusivo para una sola organización. Puede estar físicamente en el data center de la empresa (On-premise) o gestionada por un tercero, ofreciendo máximo control y seguridad.   
	- **Nube Híbrida:** Combina nubes públicas y privadas, enlazadas por tecnología que permite compartir datos y aplicaciones entre ellas. Por ejemplo: los datos sensibles de tus usuarios se quedan en tu nube privada por regulación, pero tu frontend procesa la carga masiva en la nube pública.	    
	- **Nube de Comunidad:** La infraestructura es compartida por diversas organizaciones que tienen intereses o misiones comunes (por ejemplo, requisitos de seguridad específicos, misiones de gobierno o instituciones educativas del TecNM).

7. Qué implicaciones tecnológicas tiene la implementación de un modelo de servicios?    
	 - **Arquitectura:** Obliga a migrar de arquitecturas monolíticas a arquitecturas desacopladas, basadas en **Microservicios** o **Serverless**.    
	- **Interoperabilidad:** Necesidad estricta de diseñar **APIs RESTful** o GraphQL utilizando formatos estándar como **JSON** o **XML** para que los servicios web se comuniquen entre sí.    
	- **DevOps y CI/CD:** Implementación de pipelines automatizados para empaquetar tu código (por ejemplo, con **Docker**) y desplegarlo sin interrumpir el servicio.    
	- **Monitoreo y Loggin:** Al estar todo distribuido, requieres herramientas centralizadas para saber qué componente está fallando.    

8. Cuáles serían las implicaciones legales? 
9. Existe un marco normativo nacional para los servicios cloud, qué elementos incluye?
	- **Soberanía de Datos:** Leyes internacionales y locales exigen saber dónde están físicamente los servidores que almacenan la información de los usuarios.
	- **Marco Normativo en México:** Está regido principalmente por la **LFPDPPP** (_Ley Federal de Protección de Datos Personales en Posesión de los Particulares_).	    
	- **Elementos clave que incluye:**	    
	    - **Cómputo en la Nube (Artículo 52 del Reglamento):** El proveedor de nube debe garantizar políticas de privacidad equivalentes a la ley mexicana, no subcontratar sin consentimiento, y permitir la destrucción total de los datos si el cliente lo solicita.	        
	    - **Avisos de Privacidad:** Obliga a tu aplicación web a tener un consentimiento explícito de qué datos recabas y para qué.	        
	    - **Derechos ARCO:** Tu sistema debe programarse para permitir que un usuario pueda _Acceder, Rectificar, Cancelar u Oponerse_ al uso de sus datos.
10. Dentro del modelo IAAS , cuáles son los ejemplos más conocidos de las empresas que ofrecen estos servicios?
	Amazon EC2 (AWS), Google Compute Engine (GCP), Microsoft Azure VMs, DigitalOcean Droplets.
11. Dentro del modelo PAAS , cuáles son los ejemplos más conocidos de las empresas que ofrecen estos servicios?
	AWS Elastic Beanstalk, Heroku, Vercel / Netlify (para frontends modernos), Google App Engine, Azure App Services.
12. Dentro del modelo SAAS , cuáles son los ejemplos más conocidos de las empresas que ofrecen estos servicios?
	Microsoft 365, Google Workspace, Salesforce, GitHub, Slack.

13. Explora en DigitalOcean los servicios que ofrece, con la cuenta gratuita, qué proyectos puedes hacer? Genera un ejemplo.
	Servicios que ofrece gratis:
	- Crédito de bienvenida por tiempo limitado: DigitalOcean no tiene un plan gratuito permanente como GitHub o Vercel. En su lugar, ofrece un modelo de prueba (habitualmente un bono de $200 USD válidos por 60 días) al registrar una tarjeta de crédito o débito válida.
	- Acceso a infraestructura pura (IaaS): Durante la prueba, te permite crear Droplets (servidores virtuales privados con Linux, como Ubuntu), bases de datos gestionadas, balanceadores de carga y almacenamiento en bloques.
	Proyectos que puedes hacer (durante el periodo de prueba):
	- Arquitecturas de Servidor Completas: Configurar desde cero un servidor Linux real para montar un entorno de producción con bases de datos relacionales (MySQL, PostgreSQL) y servidores web como Nginx.
	- Entornos de Contenedores con Docker: Desplegar arquitecturas basadas en microservicios, metiendo tu base de datos, tu backend en Node.js y tus servicios de seguridad dentro de contenedores independientes aislados.
	- Proyectos de Programación del Lado del Servidor: APIs robustas y aplicaciones que requieran procesamiento continuo en segundo plano o que necesiten control absoluto sobre el sistema operativo (puertos, firewalls, variables de entorno), algo que el modelo serverless de Vercel no permite.
	Ejemplo:
		Landing page en Digital Ocean
		https://praxintesis.com/
		![[Pasted image 20260601165458.png]]
		Para este despliegue utilicé un droplet de digital ocean con ubuntu.
		Utilizo docker para correr el contendedor del proyecto y traefik para la configuración de https. hice toda la configuración desde la consola.


14. Explora en Vercel cuáles servicios ofrece, con la cuenta gratuita que tipo de proyectos puedes hacer? Genera un ejemplo.
	 Servicios que ofrece gratis (Plan Hobby):
	- **Despliegue automático (CI/CD Global):** Cada vez que haces un git push a tu repositorio de GitHub, Vercel compila y publica tu aplicación automáticamente en segundos.	    
	- **Hosting Frontend Optimizado:** Alojamiento de alto rendimiento en una red de distribución de contenidos (CDN) global, lo que hace que tus páginas carguen instantáneamente.	    
	- **Serverless Functions:** Permite ejecutar código del lado del servidor (Node.js, Go, Python) en formato API sin necesidad de configurar o mantener un servidor real.	    
	- **Certificados SSL automáticos:** Tu sitio web contará con el protocolo seguro https:// por defecto y soporte para dominios personalizados sin costo.
	 Proyectos que puedes hacer:
	- **Aplicaciones de una sola página (SPAs):** Desplegar frontends modernos e interactivos construidos con **React, Angular, Vue o svelte**.
	- **Aplicaciones Full-Stack Ligeras:** Proyectos creados en frameworks modernos como **Next.js o Astro**, donde el frontend y las APIs del servidor conviven en el mismo entorno gracias a las Serverless Functions.
	- **Consumo de APIs externas:** Páginas interactivas que se conectan a bases de datos en la nube (como MongoDB Atlas) para mostrar información en tiempo real, como un tablero de control o un sistema de clima
	Ejemplo:
		https://praxintesis-landing-page.vercel.app/
		Para hacer este despliegue solo entre al dashboard de vercel, conecté mi cuenta de github y seleccioné el repositorio con el proyecto
		![[Pasted image 20260601170154.png]]
		
15. Explora en Github cuáles servicios ofrece, con la cuenta gratuita que tipo de proyectos puedes hacer? Genera un ejemplo.
	Servicios que ofrece gratis:
	- **Repositorios públicos y privados ilimitados:** Espacio en la nube para alojar y gestionar el código fuente de tus proyectos usando Git.	    
	- **GitHub Actions:** Automatización de flujos de trabajo (CI/CD) con hasta 2,000 minutos al mes para compilar y probar tu código de forma automática.	    
	- **GitHub Pages:** Servicio de hosting estático gratuito directamente desde un repositorio para publicar archivos HTML, CSS y JavaScript.	    
	- **GitHub Issues y Projects:** Herramientas de gestión de proyectos y seguimiento de bugs usando metodologías ágiles (tableros Kanban) ideales para organizar el avance de tu Proyecto Integrador.
	Proyectos que puedes hacer:
	- **Portafolios web estáticos y landing pages:** Subiendo tus prácticas de HTML y CSS usando GitHub Pages.    
	- **Control de versiones de sistemas complejos:** Guardar el código de aplicaciones completas (como el backend en Node.js o Python) de forma segura y colaborativa con tus compañeros de equipo.    
	- **Automatización de pruebas básicas:** Validar que tus scripts no tengan errores de sintaxis antes de subirlos a producción mediante Actions.
	Ejemplo:
		https://alexlessus.github.io/quasar-simulador-productividad/#/
		[Calculadora/](https://alexlessus.github.io/Calculadora/ "https://alexlessus.github.io/Calculadora/")
		[tablasDeMultiplicar/](https://alexlessus.github.io/TablasDeMultiplicar/ "https://alexlessus.github.io/TablasDeMultiplicar/")
		[Areas/](https://alexlessus.github.io/Areas/ "https://alexlessus.github.io/Areas/")
		He estado utilizando bastante github para publicar los proyectos que he estado haciendo, es bastante sencillo 
		![[Pasted image 20260601170443.png]]


