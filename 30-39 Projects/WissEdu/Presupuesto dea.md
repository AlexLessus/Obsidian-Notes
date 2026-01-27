
Version full

| **Módulo**              | **Descripción Técnica**                                                                                             | **Horas Est. (Equipo)** |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------- | ----------------------- |
| **1. Setup & DevOps**   | Configuración VPS, Docker, SSL, Dominio, Repositorio, Base de datos.                                                | 10 - 15 h               |
| **2. Auth & Usuarios**  | Login, Registro, Recuperar pass, Roles (Admin/Student), Seguridad JWT.                                              | 15 - 20 h               |
| **3. Landing & Lead**   | Diseño, Maquetado, Conexión API Newsletter (Mailchimp/Brevo).                                                       | 10 - 15 h               |
| **4. CMS (Admin)**      | CRUD Cursos, Módulos, Lecciones, Artículos (Rich Text), Subida de imágenes.                                         | 30 - 40 h               |
| **5. LMS (Estudiante)** | Dashboard, Lógica de "Curso Comprado" vs "No Comprado", Reproductor YouTube, Progreso.                              | 25 - 30 h               |
| **6. PAGOS (Nuevo)**    | Integración Stripe/PayPal. Checkout, Webhooks (para activar el curso automáticamente al pagar), Historial de pagos. | 20 - 25 h               |
| **Testing & Fixes**     | Pruebas de flujo completo, especialmente pagos y móviles.                                                           | 15 h                    |
| **TOTAL**               |                                                                                                                     | **125 - 160 Horas**     |

Version de lanzamiento

| **Módulo**              | **Descripción Técnica (Simplificada)**                                                                                                           | **Horas Est. (Equipo)** | **Cambios vs. Versión Full**                                                            |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------- | --------------------------------------------------------------------------------------- |
| **1. Setup & DevOps**   | Configuración VPS, Docker, SSL, Dominio, Repositorio, Base de datos.                                                                             | 12 - 15 h               | Se mantiene casi igual (es la base).                                                    |
| **2. Auth & Usuarios**  | Login, Registro, Recuperación básica. Roles: Admin y Estudiante.                                                                                 | 12 - 15 h               | Lógica estándar, sin cambios drásticos.                                                 |
| **3. Landing & Lead**   | Diseño y maquetado de Home. Botón de Newsletter que lleva a un link externo (ej. Google Forms o Mailchimp).                                      | 8 - 12 h                | Más rápido: sin integración de API de correos, solo links.                              |
| **4. CMS (Admin)**      | CRUD básico de Cursos/Artículos. **Funcionalidad clave:** Lista de usuarios con un "switch" para Activar/Desactivar acceso manualmente.          | 20 - 25 h               | **Reducción fuerte:** Sin reportes de ventas, ni facturación, ni gestión de reembolsos. |
| **5. LMS (Estudiante)** | Dashboard simple. Si el usuario está "Activo" ve el contenido; si no, ve una pantalla de "Cómo Pagar" (Instrucciones de transferencia/WhatsApp). | 15 - 20 h               | **Reducción:** Sin lógica de carrito de compras, ni webhooks de desbloqueo.             |
| **6. Testing & Fixes**  | Pruebas de flujo: Registro -> Admin activa -> Usuario entra. Despliegue final.                                                                   | 8 - 10 h                | Mucho más rápido al no tener que probar tarjetas de crédito falsas ni sandboxes.        |
| **TOTAL**               |                                                                                                                                                  | **75 - 97 Horas**       | **Ahorro de ~50 horas**                                                                 |
