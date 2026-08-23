Actúa como un Arquitecto de Software Senior y Experto en Frontend UI/UX especializado en SvelteKit y Tailwind CSS. Quiero que me ayudes a estructurar e inicializar desde cero un portafolio web profesional de estilo estrictamente minimalista, sofisticado y corporativo. 

El objetivo principal de este portafolio es captar la atención de reclutadores e ingenieros de software senior en grandes empresas tecnológicas y consultoras de software de nivel internacional, destacando un perfil sólido en Desarrollo Full-Stack, Infraestructura/DevOps y Automatización con Inteligencia Artificial.

### 1. Especificaciones del Stack Tecnológico
* **Framework:** SvelteKit (última versión estable, usando routing basado en carpetas y archivos `+page.svelte`).
* **Estilos:** Tailwind CSS. Debe usar una paleta de colores estricta basada en la gama `slate` o `zinc` de Tailwind (fondos ultra limpios en modo claro y grises oscuros carbón en modo oscuro como `#121212`).
* **Tipografía:** Inter o Roboto (declarada globalmente, con excelente manejo del ritmo visual y el interlineado).
* **Gestión de Contenido:** El contenido de los proyectos debe ser dinámico, leyéndose localmente desde archivos Markdown (`.md`) con un bloque Frontmatter de metadatos mediante Vite `import.meta.glob` o Mdsvex.
* **Diseño UI/UX:** Enfoque en "Menos es más". Cero animaciones intrusivas, transiciones sutiles en estados hover (`transition-all duration-200`), uso estratégico del espacio en blanco (whitespace) y responsive absoluto (`mobile-first`).

### 2. Estructura de Páginas Requerida
* **Ruta Principal (`src/routes/+page.svelte`):** Una landing page corporativa limpia de una sola página que contenga de forma secuencial:
  1. **Hero Section:** Nombre, rol principal claro (ej: Full-Stack & Automation Engineer), llamada a la acción limpia para contactar por email y un botón prioritario para descargar el CV en PDF.
  2. **Sobre Mí:** Breve párrafo sobre el enfoque analítico, resolución de problemas y adaptabilidad técnica.
  3. **Experiencia Laboral / Proyectos de Consultoría:** Sección formal con formato cronológico.
  4. **Sección de Habilidades Técnicas:** Tarjetas o rejillas minimalistas organizadas por categorías de infraestructura, desarrollo y herramientas.
  5. **Grid de Proyectos:** Tarjetas elegantes que muestren los metadatos de los archivos `.md`.
* **Ruta Dinámica (`src/routes/proyectos/[slug]/+page.svelte` y `+page.js`):** La vista de detalle técnico para cada proyecto. Debe renderizar limpiamente el HTML generado por el Markdown, manteniendo la navegación fluida y continua de SvelteKit.

### 3. Estructura de Archivos del Proyecto
Genera el mapa de carpetas ideal para este proyecto, organizando el contenido de la siguiente manera:
* `src/lib/content/proyectos/` -> Aquí se guardarán los archivos `.md` de cada proyecto.
* `src/lib/components/` -> Componentes modulares y reutilizables (tarjetas de proyectos, botones corporativos, layout de navegación, toggle de dark mode).
* `src/routes/` -> Estructura de rutas limpias.

### 4. Entregables Esperados en tu Respuesta
Por favor, proporcióname:
1. El árbol de directorios recomendado para el proyecto SvelteKit.
2. La configuración base de `tailwind.config.js` adaptada al diseño corporativo y soporte nativo de Dark Mode.
3. El código de `src/routes/proyectos/[slug]/+page.js` (o `+page.server.js`) para cargar dinámicamente un archivo `.md` según el parámetro `slug`.
4. El componente Svelte de la tarjeta de proyecto (`ProjectCard.svelte`) estilizado con Tailwind CSS, optimizado para legibilidad, que reciba los metadatos del Markdown como props.
5. Un ejemplo estructurado de un archivo `.md` con Frontmatter rico en metadatos (título, descripción, rol, tags de tecnologías, urls de repositorios y demos).

Usa un tono puramente técnico, profesional y código optimizado listo para producción.
